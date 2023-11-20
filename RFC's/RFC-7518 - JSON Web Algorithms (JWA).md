---
link: https://www.rfc-editor.org/rfc/rfc7518
---
#RFC

!!!ERRADO!! https://www.youtube.com/watch?v=bpB0pEro9qY
Define qual são os algoritmos mínimos que devem ser cobertos pelas libs:


| alg Param | Digital Signature or MAC      | Implementation |
|-----------|-------------------------------|----------------|
| HS256     | [[HMAC SHA-256]]            | Required       |
| HS384     | HMAC using SHA-384            | Optional       |
| HS512     | HMAC using SHA-512            | Optional       |
| RS256     | [[RSA SHA-256]] using  SHA-256     | Recommended    |
| RS384     | RSASSA-PKCS1-v1_5 using  SHA-384      | Optional       |
| RS512     | RSASSA-PKCS1-v1_5 using  SHA-512    | Optional       |
| ES256     | ECDSA using P-256 and SHA-256 | Recommended    |
| ES384     | ECDSA using P-384 and SHA-384 | Optional       |
| ES512     | ECDSA using P-521 and SHA-512 | Optional       |
| PS256     | RSASSA-PSS using SHA-256 and   MGF1 with SHA-256 | Optional       |
| PS384     | RSASSA-PSS using SHA-384 and  MGF1 with SHA-384 | Optional       |
| PS512     | RSASSA-PSS using SHA-512 and   MGF1 with SHA-512 | Optional       |
| none      | No digital signature or MAC  performed | Optional       |


   