#teste 
Testes para [[HMAC SHA-256]]


Exemplo:
```python
def test_hmac_jwk_should_parse_and_verify(self):  
    algo = HMACAlgorithm(HMACAlgorithm.SHA256)  
  
    with open(key_path("jwk_hmac.json")) as keyfile:  
        key = algo.from_jwk(keyfile.read())  
  
    signature = algo.sign(b"Hello World!", key)  
    assert algo.verify(b"Hello World!", key, signature)
```