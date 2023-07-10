# Risk A4: Insecure Design

## Key Concepts

Architecturral flaws:
- Flaws of Omission, ignoring a threat or security requirement, such as storing a password in a file
- Flaws of Commission, Bad design such as using client-side authentication
- Flaw of Realization, Design is good but errors exist in the implementations

Secure Design Patterns:
- Patterns of privellege separation

Reference Architectures:
- These are templates to combine secure design patterns into a secure architecture

## Definition

The collection of security flaws within the web application that cannot be attributed to or fixed by implementation.

## Examples

User access modle based on the zones of trust from which the user is connection to our web application

Bad Example
```
userAccess() {
    if (user.isAuthorized("USER")) {
     // authorize user indepent zone
    }
}
```

Good Example
```
userAccess() {
    if (user.isConnectionFromZone(Zone.SemiTrusted)) {
     // authorize user based on zone
    }
}
```

## Challenges

Not enough time is givent ot architecture and design. Security design patterns are incorrectly customized. Reference architectures are not updated for latest frameworks.

## Protection Strategies

### DADGUM

- Deny by principle, based on policy
- Apply known reference architectures
- Design using privellege separation
- Generate security requirements to counter threats
- Use known secure design patterns
- Manage protocols and restrict permissions