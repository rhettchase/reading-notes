# Class-15 Reading Notes: Authentication

source: [What is OAuth](https://www.csoonline.com/article/3216404/what-is-oauth-how-the-open-authorization-framework-works.html)

1. **What is OAuth?**

   OAuth, which stands for Open Authorization, is an open-standard authorization protocol/framework. It defines how unrelated servers and services can allow authenticated access to their assets without sharing the initial, related, single logon credential. OAuth enables secure, third-party, user-agent, delegated authorization, allowing users to access resources across different services without sharing their login credentials.

2. **Give an example of what using OAuth would look like.**

   A common example of OAuth is when a user logs into a website and is given the option to log in using credentials from another website or service. For instance, when logging into a website, you might see options like "Log in with Google" or "Log in with Facebook." Clicking on such an option initiates an OAuth flow. The user is redirected to the authentication provider (Google or Facebook), authenticates there, and then the original website gains access on behalf of the user.

3. **How does OAuth work? What are the steps that it takes to authenticate the user?**

   The OAuth process involves several steps:

   - The user initiates a transaction that requires access to another site or service.
   - The initiating site connects to the second site using OAuth, providing the user's verified identity.
   - The second site generates a one-time token and a one-time secret unique to the transaction.
   - The first site gives this token and secret to the user's client software.
   - The client's software presents the request token and secret to their authorization provider.
   - If not already authenticated, the client may be asked to authenticate, then approves the authorization transaction to the second website.
   - The user approves a specific transaction type at the first website.
   - The user is given an approved access token.
   - The user gives the approved access token to the first website.
   - The first website gives the access token to the second website as proof of authentication.
   - The second website lets the first website access their site on behalf of the user.

   OAuth focuses on authorization rather than authentication. It allows users to give limited access to their resources to another website or service without sharing their primary credentials.

4. **What is OpenID?**

   OpenID is another technology related to authentication, often mentioned alongside OAuth. While OAuth is about authorization, OpenID is specifically about authentication. OpenID is designed for humans logging into machines, providing a single sign-in solution for users across multiple websites. It allows users to use a single set of credentials to log in to different websites, vouching for their identity. OpenID 2.0 initially struggled with adoption but gained traction when OpenID Connect was released in 2014. OpenID Connect reinvented OpenID as an authentication layer for OAuth, complementing each other in many implementations.

source: [Authorization and Authentication flows](https://auth0.com/docs/flows), chatGPT

1. **What is the difference between authorization and authentication?**

   - **Authentication:** The process of verifying the identity of a user, system, or entity. It involves validating provided credentials (such as username/password or other authentication factors) against a known set of data.
   - **Authorization:** The process of granting or denying access to specific resources or actions based on the authenticated user's permissions. Once a user is authenticated, authorization determines what actions or resources they are allowed to access.

2. **What is Authorization Code Flow?**
   - The Authorization Code Flow is a method used in OAuth 2.0 for obtaining access tokens. It is suitable for server-side applications where the source code is not exposed to the public. The flow involves exchanging an authorization code for a token, providing a more secure way to obtain access.
3. **What is Authorization Code Flow with Proof Key for Code Exchange (PKCE)?**
   - Authorization Code Flow with Proof Key for Code Exchange (PKCE) is an extension of the Authorization Code Flow, designed to enhance security in scenarios like mobile and native applications. PKCE helps mitigate security risks by ensuring that the authorization code cannot be intercepted during the authorization process.
4. **What is Implicit Flow with Form Post?**
   - Implicit Flow with Form Post is an alternative to the Authorization Code Flow, primarily intended for Public Clients or applications that cannot securely store client secrets. This flow, while no longer considered best practice for accessing access tokens, is suitable for scenarios where an application only requires an ID token for user authentication. The use of Form Post response mode streamlines the workflow.
5. **What is Client Credentials Flow?**
   - Client Credentials Flow is a flow within OAuth 2.0 designed for machine-to-machine (M2M) applications. In this scenario, the application itself is authenticated and authorized, rather than a user. Typical user-based authentication methods like usernames/passwords are not applicable. Instead, M2M apps use the Client Credentials Flow, where the system authenticates and authorizes the application.
6. **What is Device Authorization Flow?**
   - Device Authorization Flow is used for input-constrained devices that connect to the internet. In this flow, the device prompts the user to go to a link on another device (computer or smartphone) to authorize it. This approach is particularly useful for devices that lack an easy way to enter text directly. The Device Authorization Flow is suitable for mobile/native applications.
7. **What is Resource Owner Password Flow?**
   - Resource Owner Password Flow is a less recommended method where highly-trusted applications request users to provide credentials (username and password) directly, usually through an interactive form. This flow should only be used when other redirect-based flows, like the Authorization Code Flow, cannot be employed. It is considered less secure because it involves handling user credentials directly.
