#teste 
Testes para [[HMAC SHA-256]]

Exemplo:
```python
def test_hmac_jwt_should_return_false_if_signature_invalid(self):  
    algo = HMACAlgorithm(HMACAlgorithm.SHA256)  
  
    with open(key_path("jwk_hmac.json")) as keyfile:  
        key = algo.from_jwk(keyfile.read())  
  
    signature = algo.sign(b"Hello World!", key)  
    assert not algo.verify(b"Hello World!",  base64url_decode("hJtXIZ2uSN5kbQfbtTNWbpdmhkV8FJG-Onbc6mxCcY1"), signature)
```