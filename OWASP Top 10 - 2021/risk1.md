# Risk A1: Broken Access Control

## Key Concepts

Access control is the proces which you disallow access. Features or data require a permission to access.

Authorization is the process of verifying that the user has the permission to access the requested resource.

## Definition

Broken access control is when a user is able to act outside of their permissions, access of unauthorized data or functionality. Violation of the Principle of Least Privilege. Only give the permissions necessary for users to perform their job.

## Examples

Bad Example
```python
def adminReport(param):
    if param == "user":
        return "You are an admin"
    else:
        return "You are not an admin"
```

Good Example
```python
def adminReport(param):
    if param == "admin":
        return "You are an admin"
    else:
        return "You are not an admin"
```

## Challenges

Frameworks do not procide detailed access control functionality. Developers must implement their own access control. It is also difficult to test access control due to automated tools not aware of custom access control. 

## Protection Strategies

### DEBAR

- Design access control so all requests must be authorized
- Enforce access by acticity and only for valid work flow paths
- Build a centralized access control mechanism
- Assign permissions to users in the context of data
- Refused access by defauly, fail securely