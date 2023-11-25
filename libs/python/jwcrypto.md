---
github: https://github.com/latchset/jwcrypto
doc: https://jwcrypto.readthedocs.io/en/latest/
---
#lib 

Dependências: 
	- [[cryptography]]

[[Teste HMAC SHA-256]]
```python
A1_signature = \
    [116, 24, 223, 180, 151, 153, 224, 37, 79, 250, 96, 125, 216, 173,
     187, 186, 22, 212, 37, 77, 105, 214, 191, 240, 91, 88, 5, 88, 83,
     132, 141, 121]
A1_example = {'key': SymmetricKeys['keys'][1],
              'alg': 'HS256',
              'protected': bytes(bytearray(A1_protected)).decode('utf-8'),
              'payload': bytes(bytearray(A1_payload)),
              'signature': bytes(bytearray(A1_signature))}

class TestJWS(unittest.TestCase):
    def check_sign(self, test):
        s = jws.JWSCore(test['alg'],
                        jwk.JWK(**test['key']),
                        test['protected'],
                        test['payload'],
                        test.get('allowed_algs', None))
        sig = s.sign()
        decsig = base64url_decode(sig['signature'])
        s.verify(decsig)
        # ECDSA signatures are always different every time
        # they are generated unlike RSA or symmetric ones
        if test['key']['kty'] != 'EC':
            self.assertEqual(decsig, test['signature'])
        else:
            # Check we can verify the test signature independently
            # this is so that we can test the ECDSA against a known
            # good signature
            s.verify(test['signature'])
```



[[Teste RSA SHA-256]]

```python
# RFC 7515 - A.2
[[RFC-7515 - JSON Web Signature (JWS)]]
A2_protected = \
    [123, 34, 97, 108, 103, 34, 58, 34, 82, 83, 50, 53, 54, 34, 125]
A2_payload = A1_payload
A2_key = \
    {"kty": "RSA",
     "n": "ofgWCuLjybRlzo0tZWJjNiuSfb4p4fAkd_wWJcyQoTbji9k0l8W26mPddx"
          "HmfHQp-Vaw-4qPCJrcS2mJPMEzP1Pt0Bm4d4QlL-yRT-SFd2lZS-pCgNMs"
          "D1W_YpRPEwOWvG6b32690r2jZ47soMZo9wGzjb_7OMg0LOL-bSf63kpaSH"
          "SXndS5z5rexMdbBYUsLA9e-KXBdQOS-UTo7WTBEMa2R2CapHg665xsmtdV"
          "MTBQY4uDZlxvb3qCo5ZwKh9kG4LT6_I5IhlJH7aGhyxXFvUK-DWNmoudF8"
          "NAco9_h9iaGNj8q2ethFkMLs91kzk2PAcDTW9gb54h4FRWyuXpoQ",
     "e": "AQAB",
     "d": "Eq5xpGnNCivDflJsRQBXHx1hdR1k6Ulwe2JZD50LpXyWPEAeP88vLNO97I"
          "jlA7_GQ5sLKMgvfTeXZx9SE-7YwVol2NXOoAJe46sui395IW_GO-pWJ1O0"
          "BkTGoVEn2bKVRUCgu-GjBVaYLU6f3l9kJfFNS3E0QbVdxzubSu3Mkqzjkn"
          "439X0M_V51gfpRLI9JYanrC4D4qAdGcopV_0ZHHzQlBjudU2QvXt4ehNYT"
          "CBr6XCLQUShb1juUO1ZdiYoFaFQT5Tw8bGUl_x_jTj3ccPDVZFD9pIuhLh"
          "BOneufuBiB4cS98l2SR_RQyGWSeWjnczT0QU91p1DhOVRuOopznQ",
     "p": "4BzEEOtIpmVdVEZNCqS7baC4crd0pqnRH_5IB3jw3bcxGn6QLvnEtfdUdi"
          "YrqBdss1l58BQ3KhooKeQTa9AB0Hw_Py5PJdTJNPY8cQn7ouZ2KKDcmnPG"
          "BY5t7yLc1QlQ5xHdwW1VhvKn-nXqhJTBgIPgtldC-KDV5z-y2XDwGUc",
     "q": "uQPEfgmVtjL0Uyyx88GZFF1fOunH3-7cepKmtH4pxhtCoHqpWmT8YAmZxa"
          "ewHgHAjLYsp1ZSe7zFYHj7C6ul7TjeLQeZD_YwD66t62wDmpe_HlB-TnBA"
          "-njbglfIsRLtXlnDzQkv5dTltRJ11BKBBypeeF6689rjcJIDEz9RWdc",
     "dp": "BwKfV3Akq5_MFZDFZCnW-wzl-CCo83WoZvnLQwCTeDv8uzluRSnm71I3Q"
           "CLdhrqE2e9YkxvuxdBfpT_PI7Yz-FOKnu1R6HsJeDCjn12Sk3vmAktV2zb"
           "34MCdy7cpdTh_YVr7tss2u6vneTwrA86rZtu5Mbr1C1XsmvkxHQAdYo0",
     "dq": "h_96-mK1R_7glhsum81dZxjTnYynPbZpHziZjeeHcXYsXaaMwkOlODsWa"
           "7I9xXDoRwbKgB719rrmI2oKr6N3Do9U0ajaHF-NKJnwgjMd2w9cjz3_-ky"
           "NlxAr2v4IKhGNpmM5iIgOS1VZnOZ68m6_pbLBSp3nssTdlqvd0tIiTHU",
     "qi": "IYd7DHOhrWvxkwPQsRM2tOgrjbcrfvtQJipd-DlcxyVuuM9sQLdgjVk2o"
           "y26F0EmpScGLq2MowX7fhd_QJQ3ydy5cY7YIBi87w93IKLEdfnbJtoOPLU"
           "W0ITrJReOgo1cq9SbsxYawBgfp_gh6A5603k2-ZQwVK0JKSHuLFkuQ3U"}
           
A2_example = {'key': A2_key,
              'alg': 'RS256',
              'protected': bytes(bytearray(A2_protected)).decode('utf-8'),
              'payload': bytes(bytearray(A2_payload)),
              'signature': bytes(bytearray(A2_signature))}
              
class TestJWS(unittest.TestCase):
    def check_sign(self, test):
        s = jws.JWSCore(test['alg'],
                        jwk.JWK(**test['key']),
                        test['protected'],
                        test['payload'],
                        test.get('allowed_algs', None))
        sig = s.sign()
        decsig = base64url_decode(sig['signature'])
        s.verify(decsig)
        # ECDSA signatures are always different every time
        # they are generated unlike RSA or symmetric ones
        if test['key']['kty'] != 'EC':
            self.assertEqual(decsig, test['signature'])
        else:
            # Check we can verify the test signature independently
            # this is so that we can test the ECDSA against a known
            # good signature
            s.verify(test['signature'])
```