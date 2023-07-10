# Risk A7: Identification and Authentication Failures

## Key Concepts

Digital Identity, a set of attributes that relate to a person or organisation: username, age, password

Identification, sharing or showing attributes relating to your identity

Authentication confirming the identity of a user, identity presented is being confirmed

## Definition

Being able to perform successful attacks that disclose identity attributes on the system or web application in use.

Authentication controls being subverted or bypassed

- Such as forget password processes
- Weak or misconfigured identity attributes
  - Low password complexity
  - Despite logout, sessions are not made invalid

## Examples

Bad Example

```java
if (user.equals(username)) {
    if (pass.equals(password)) {
        response.set("Invalid password"); // Not good attacker knows valid username
    } else {
        response.authriseUser(user);s
    }
}
```

Good Example

```java
if (user.equals(username) && pass.equals(password)) {
    response.authriseUser(user);s
} else {
    response.set("Invalid username or password");
}
```

## Challenges

The most difficult point to secure for any web application is the point of interation with the user

- Flexibility for users
- Credential stuffing
- Brute force attacks

## Protection Strategies

### FEMALE

- Force strong credentials
- Ensure user registration and recovery are hardened
- Manage authentication sessions and tokens
- Alert on attacks such as bruteforce
- Limit failed login attempts
- Enable multi factor authentication
