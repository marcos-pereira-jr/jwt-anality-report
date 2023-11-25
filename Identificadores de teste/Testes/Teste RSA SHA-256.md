#teste 
Teste para [[RSA SHA-256]]

```python
@crypto_required  
def test_ec_jwk_public_and_private_keys_should_parse_and_verify(self):  
    tests = {  
        "P-256": ECAlgorithm.SHA256,  
        "P-384": ECAlgorithm.SHA384,  
        "P-521": ECAlgorithm.SHA512,  
        "secp256k1": ECAlgorithm.SHA256,  
    }  
    for curve, hash in tests.items():  
        algo = ECAlgorithm(hash)  
  
        with open(key_path(f"jwk_ec_pub_{curve}.json")) as keyfile:  
            pub_key = cast(EllipticCurvePublicKey, algo.from_jwk(keyfile.read()))  
  
        with open(key_path(f"jwk_ec_key_{curve}.json")) as keyfile:  
            priv_key = cast(EllipticCurvePrivateKey, algo.from_jwk(keyfile.read()))  
  
        signature = algo.sign(b"Hello World!", priv_key)  
        assert algo.verify(b"Hello World!", pub_key, signature)
```