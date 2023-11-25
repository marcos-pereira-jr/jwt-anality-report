---
github: https://github.com/jpadilla/pyjwt
linguagem: Python
---
#lib

algoritmos suportados: https://pyjwt.readthedocs.io/en/stable/algorithms.html

Dependências: 
	- [[cryptography]]
#### Testes suportados 
[[Teste RSA SHA-256]]
```python
   @crypto_required
    def test_rsa_jwk_public_and_private_keys_should_parse_and_verify(self):
        algo = RSAAlgorithm(RSAAlgorithm.SHA256)

        with open(key_path("jwk_rsa_pub.json")) as keyfile:
            pub_key = cast(RSAPublicKey, algo.from_jwk(keyfile.read()))

        with open(key_path("jwk_rsa_key.json")) as keyfile:
            priv_key = cast(RSAPrivateKey, algo.from_jwk(keyfile.read()))

        signature = algo.sign(b"Hello World!", priv_key)
        assert algo.verify(b"Hello World!", pub_key, signature)
```


[[Teste HMAC SHA-256]]
```python
   def test_hmac_verify_should_return_true_for_test_vector(self):
        """
        This test verifies that HMAC verification works with a known good
        signature and key.

        Reference: https://tools.ietf.org/html/rfc7520#section-4.4
        """
        signing_input = (
            b"eyJhbGciOiJIUzI1NiIsImtpZCI6IjAxOGMwYWU1LTRkOWItNDcxYi1iZmQ2LWVlZ"
            b"jMxNGJjNzAzNyJ9.SXTigJlzIGEgZGFuZ2Vyb3VzIGJ1c2luZXNzLCBGcm9kbywgZ"
            b"29pbmcgb3V0IHlvdXIgZG9vci4gWW91IHN0ZXAgb250byB0aGUgcm9hZCwgYW5kIG"
            b"lmIHlvdSBkb24ndCBrZWVwIHlvdXIgZmVldCwgdGhlcmXigJlzIG5vIGtub3dpbmc"
            b"gd2hlcmUgeW91IG1pZ2h0IGJlIHN3ZXB0IG9mZiB0by4"
        )

        signature = base64url_decode(b"s0h6KThzkfBBBkLspW1h84VsJZFTsPPqMDA7g1Md7p0")

        algo = HMACAlgorithm(HMACAlgorithm.SHA256)
        key = algo.prepare_key(load_hmac_key())

        result = algo.verify(signing_input, key, signature)
        assert result

```