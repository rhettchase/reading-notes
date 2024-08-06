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
## Database-drive Workflow

Overview:
Store question flow logic in a database, allowing dynamic changes without altering the code. This is useful for applications where workflows need frequent updates or customization.

Implementation:

Tables: Create tables to define questions, responses, and next questions.
Logic: Fetch the next question based on the current question ID and response from the database.

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
