# Risk A2: Cryptographic Failures

## Key Concepts

Cryptography is the art and science of keeping messages secure.

Encryption is the algorithm for transforming messages (such as plaintext) into secure messages (cipher text) most often used with a key.

Cryptanalysis is the art and science of breaking encrypted messages.

## Definition

The use of weak, deprecated or incorrect cryptographic algorithms can lead to the compromise of sensitive data.

## Examples

Sensitve data transmitted in clear text.

Secret key ors keys which can be predicted.

Use of older encryption algorithms.

### Weak
Algorithms we have found ways to civumevent the security they provide

### Deprecated
Outdated algorithms which were designed in the 70s and 80s. Computing power has increased and these algorithms are no longer secure.

Bad Example
```
Cipher cipher = 
Cipher.getInstance("DES/CBC/NoPadding"); # DES created in early 90s
Cipher.getInstance("DESede/CBC/PKCS5Padding"); 
Cipher.getInstance("AES/ECB/PKCS5Padding");
```

Good Example
```
Cipher cipher = 
Cipher.getInstance("AES/GCM/NoPadding"); # Advanced Encryption Standard created early 2000s, Galois Counter Mode nire secure than CBCs
```

## Challenges

Crypto knowledge is rare, difficult to learn and hard to verify the security that crypto security provides. Requires senior and sophisticated developer resources.

## Protection Strategies

### MUSIC

- Manage keys and secrets properly
- Use up to date and strong cryptographic algorithms, protocols and key sizes
- Sensitive data requires more protection so classify them correctly
- Instrument encryption for data at rest and in transit
- Configure cryptoghraphic algorithms well
