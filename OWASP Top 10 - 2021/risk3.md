# Risk A3: Injection

## Key Concepts

Protocol is a set of ruls for exchanging information. Protcol Encapsulation is when one set of rules is wrapped into another

New Malicious Commands are added to an application

## Definition

Injection is an instance where an attacker can supply untrusted data to a web application that can be processed as a command or query. This can lead to data loss or corruption, lack of accountability, or denial of access.

SQL and LDAP injection
Command Injection
Object Query Language Injection

## Examples

Bad Example
```
SqlCommand objCommand = new SqlCommand(
    "SELECT id, name FROM user_table WHERE
    username = '" + Reques(Username) + "' AND password = '" + Request(Password) + "'"
);
```

Good Example
Use a parameterized query
```
SqlCommand objCommand = new SqlCommand(
    "SELECT id, name FROM user_table WHERE
    username = @username AND password = @password"
);
```

## Challenges

Building web applications involves many layers and protocols, insufficient user input validation, and lack of security awareness.

## Protection Strategies

### VECUS

- Validate untrusted
- Encode data
- Configure databases using least privilege principle
- Use safe APIS for protocol queries
- Sanitize data
