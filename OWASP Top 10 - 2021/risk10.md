# Risk A10: Server-Side Request Forgery

## Key Concepts

Server Side refers to programs and operation that run on the server like an API on the backend

Request forgery is when you craft a web request that appears legitimate but contains malicious input

Cross-Site Request Forgery (CSRF) an attack that forces the user to execute unwanted actions while authenticated to your web application

One-Click attack sending a malicious URL to an authenticated uer that performs an action they do not approve or know about

## Definition

Forcing a server to make a request to an unexpected resources

- Loss of data
- Privellege escalation
- Often affects microservices or N-tiered applications

## Examples

Bad Example

```javascript
addToPage(String url) {
    if (Validator.isValidURL(url)) {
        return fetchContent(url);
    }
}
```

Good Example

```javascript
addToPage(String url) {
    if (Validator.isValidURL(url)) {
        if (Domain.isOurs(url)) {
            return fetchContent(url);
        }
    }
}
```

## Challenges

Traditional code and dynamic scanning tools truggle to accurately identify Server-Side Request Forgery

## Protection Strategies

### VEST

- Validate the origin of URLs and IPs when there are parameters
- Ensure authentication and access control
- Setup URL encoding for untrusted parameters
- Test and limit service network access
