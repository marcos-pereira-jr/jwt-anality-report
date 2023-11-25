---
github: https://github.com/mpdavis/python-jose
linguagem: Python
---
#lib
algoritmos suportados: https://python-jose.readthedocs.io/en/latest/jws/index.html#supported-algorithms
Foi baseada no pyjwt
Dependências:
	- [[pyrsa]]

[[Teste RSA SHA-256]]
```python
def test_to_dict(self):  
    passphrase = "The quick brown fox jumps over the lazy dog"  
    encoded = "VGhlIHF1aWNrIGJyb3duIGZveCBqdW1wcyBvdmVyIHRoZSBsYXp5IGRvZw"  
    key = HMACKey(passphrase, ALGORITHMS.HS256)  
  
    as_dict = key.to_dict()  
    assert "alg" in as_dict  
    assert as_dict["alg"] == ALGORITHMS.HS256  
  
    assert "kty" in as_dict  
    assert as_dict["kty"] == "oct"  
  
    assert "k" in as_dict  
    assert as_dict["k"] == encoded  
  
    # as_dict should be serializable to JSON  
    json.dumps(as_dict)
```