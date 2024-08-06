# Research on Question Flow Logic Options

## Custom Rule Engine

Overview:
Develop a custom rule engine that evaluates conditions and determines the next step. This is ideal for applications with highly dynamic and complex decision logic.

Implementation:

- Rules: Define rules as classes or functions that evaluate the response and decide the next question.
- Engine: Iterate over the rules to find the applicable one for each step

```python
class Rule:
    def __init__(self, question_id, condition, next_question_id):
        self.question_id = question_id
        self.condition = condition
        self.next_question_id = next_question_id

    def applies(self, current_question_id, response):
        return self.question_id == current_question_id and self.condition(response)

rules = [
    Rule(1, lambda r: r == "Yes", 2),
    Rule(1, lambda r: r == "No", None),
    Rule(2, lambda r: r == "Banana", 4),
    Rule(2, lambda r: r == "Apple", 5),
]

def get_next_question(current_question_id: int, response: str) -> Optional[int]:
    for rule in rules:
        if rule.applies(current_question_id, response):
            return rule.next_question_id
    return None

```
## Database-driven Workflow

Overview:
Store question flow logic in a database, allowing dynamic changes without altering the code. This is useful for applications where workflows need frequent updates or customization.

Implementation:

Tables: Create tables to define questions, responses, and rules (that dictate next questions based on responses).
Logic: Fetch the next question based on the current question ID and response from the database.

Implementing the Workflow
Backend Logic
Fetching the Next Question:

- When a response is submitted, query the Rules table for rules associated with the current question.
- Evaluate each rule to see if its condition is met.
- If a condition is met, fetch the next question using next_question_id.
- If no conditions are met, return the associated message or default message.

Updating the Database:

- Insert the user's response into the Answers table.
- Track the progress of each user through the questionnaire by storing a session or user ID with each response.

Example schema:
```sql
CREATE TABLE questions (
    id SERIAL PRIMARY KEY,
    text TEXT,
    options JSONB
);

CREATE TABLE question_flows (
    question_id INT,
    response TEXT,
    next_question_id INT,
    PRIMARY KEY (question_id, response)
);
```

Query Rules Table:

```python
def get_rules_for_question(db: Session, question_id: int):
    return db.query(Rule).filter(Rule.question_id == question_id).all()

def get_question(db: Session, question_id: int):
    return db.query(Question).filter(Question.id == question_id).first()

```

Evaluate Conditions:
```python
def evaluate_rules(response: str, rules: List[Rule]):
    for rule in rules:
        if eval(rule.condition):  # Using eval for simplicity; ensure this is safe
            return rule.next_question_id or rule.message
    return "No valid rule found"

```

Fetching Next Question:

```python
def get_next_question(db: Session, current_question_id: int, response: str) -> Optional[int]:
    result = db.query(QuestionFlow).filter_by(
        question_id=current_question_id,
        response=response
    ).first()
    return result.next_question_id if result else None

```

## Configuration Files

Overview:
Use JSON or YAML configuration files to define question flows. This allows non-developers to update workflows without touching the code.

Implementation:

- Config Files: Store question flow in files like question_flow.json or question_flow.yaml.
- Parser: Load and parse these files at application startup.

JSON Config File Example
```json
{
    "1": {
        "Yes": 2,
        "No": "You're not eligible"
    },
    "2": {
        "Banana": 4,
        "Apple": 5,
        "default": "You're not eligible"
    }
}

```

Loading and using Config Example:

```python
import json

with open('question_flow.json') as f:
    QUESTION_FLOW = json.load(f)

def get_next_question(current_question_id: int, response: str) -> Union[int, str]:
    question_mapping = QUESTION_FLOW.get(str(current_question_id), {})
    return question_mapping.get(response, question_mapping.get("default", "No further questions"))

```

API Endpoints to fetch questions and process responses

```python
@app.get("/questions/{question_id}")
async def get_question(question_id: int):
    question = next((q for q in QUESTION_FLOW if q['id'] == question_id), None)
    if not question:
        raise HTTPException(status_code=404, detail="Question not found")
    return question

@app.post("/next-question/")
async def next_question(answer: dict):
    result = evaluate_rules(answer['question_id'], answer['response'])
    return result

```
