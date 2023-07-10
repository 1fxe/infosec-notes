# Risk A9: Security Logging and Moniting Failures

## Key Concepts

Event logging provides a standard and centralized way of recording important software events. Records events from various sources and stored them, typically, in a signel collection called an event log

Event Monitoring, process of collecting, analyzing and signaling event occurrences, the process of collecting events in our event log. Analyzed in the future

Security logging and monitoring, logging the events that can impat the confidentiality, integrity or availability of out software, not a specific risk, helps us with incidents

## Definition

Having auditable events, warnings and errors within our web application or API, which are not adequately logged.

- Agree on a security centric logging standard
- Security teams need to monitor logs for suspicious activity
- Proper logging infastructure

## Examples

Bad Example

```java
if (!user.hasAccess("ADMIN_ACCOUNT")) {
    // queitly deny access
}
```

Good Example

```java
if (!user.hasAccess("ADMIN_ACCOUNT")) {
    // deny and access log
    log.event(Event.SECURITY, Event.CRITICAL, "User attempted to access admin action without permission");
}
```

## Challenges

Developers are unware of the security alerts they need to log

- Appropriate alerting thresholds and response escalation processes are not in place

Incident respose/security operations teams do not know enough about thow the application is working and what should be logged

- Think what actions are imporant
- We forgot how suspicous activity should be logged

## Protection Strategies

### BEST

- Build a secure logging infrastrucutre for collection and storage of long term logs
- Ensure all authentication a nd a ccess controls are logged
- Standardise machine readable formats for incident reports
- Test incident response based on logging events
