# Risk A5: Security Misconfiguration

## Key Concepts

Security control is an information safegaurd or countermeasure designed to protect the confidentiality, integrity and availability of data.

Misconfiguration introduces security vulnerabilities, configuration has not been hardened

## Definition

Failing to implement the necessary controls to secure the configuration of your application

- Application is missing the necessary security hardening
- Default accounts are still active
- Unnecesary features are installed and enabled

## Examples

Configuration of Apache Structs

```xml
<global-forwards>
    <forward name="sign-in" path="Sign-in.jsp" />
</global-forwards>
```

Good Example

```xml
<global-forwards>
    <forward name="sign-in" path="/Sign-in.jsp" />
</global-forwards>
```

## Challenges

- A Small configuration change can introduce vulnerabilites
- People do not read the manual
- Know enough to understand the deployment environment and frameworks you use

## Protection Strategies

### VARKAS

- Verify Configuration
- Assume insecure
- Read existing guides
- Know your frameworks and libraries
- Apply security settings avaliable to you
- Study to enough enough
