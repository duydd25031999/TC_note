## Concept

- A web security vulnerability that allows an attacker to induce users to perform actions that they do not intend to perform.
    - change the email address on their account
    - change their password
    - make a funds transfer.
- It allows an attacker to partly circumvent the same origin policy, which is designed to prevent different websites from interfering with each other.

## How to work

- For a CSRF attack to be possible, 3 key conditions must be in place:

### **A relevant action**

- There is an action within the application that the attacker has a reason to induce.
- This might be a privileged action (such as modifying permissions for other users) or any action on user-specific data (such as changing the user's own password).

### **Cookie-based session handling**

- Performing the action involves issuing one or more HTTP requests, and the application relies solely on session cookies to identify the user who has made the requests.
- There is no other mechanism in place for tracking sessions or validating user requests.

### **No unpredictable request parameters**

- The requests that perform the action do not contain any parameters whose values the attacker cannot determine or guess.
    - For example, when causing a user to change their password, the function is not vulnerable if an attacker needs to know the value of the existing password.

## **Preventing CSRF attacks**

- The most robust way to defend against CSRF attacks is to include a `CSRF_token` within relevant requests.
- Unpredictable with high entropy, as for session tokens in general.
- Tied to the user's session.
    - Only validate in 1 session.
- Strictly validated in every case before the relevant action is executed.

---