# Risk A8: Software and Integrity Failure

## Key Concepts

Software Integrity Verification

- Trust but verify
- Verifying the inclusion of functionality from untrusted software sources

Continuous Intefration

- Automated tasks, merging developers code

Continuois Delivery

- Untrusted software libraries

## Definition

Having software code that does not prevent the inclusion of functionality from untrusted sources

- Know sources of code you trust
- Parsing data relating to software loaded during runtime
- Deserialzing untrusted data

## Examples

Auto update functionality with hardcoded http url

Bad example

```javascript
Update() {
    const data = download("https://<url>/update.sh")
    exec(data)
}
```

Good Example

```javascript
Update() {
    const data = download("https://<url>/update.sh")
    verifyHash(data, "some-hash")
    verifyGitContent(data)
    exec(data)
}
```

## Challenges

Many software solutions/components auto-update ewithout sufficient integrity checks

- Attackers target software update

Software integrity problems are hard to detect

- Security teams are not involved

## Protection Strategies

### LEVAN

- Learn enough cryptograhpy to verify the integrity of downloads
- Ensure all third party software are updated
- Verify thirdy party software
- Apply and use digital Signatures
- Note what software sources you trust
