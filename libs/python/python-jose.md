---
github: https://github.com/mpdavis/python-jose
linguagem: Python
---
#lib
algoritmos suportados: https://python-jose.readthedocs.io/en/latest/jws/index.html#supported-algorithms
Foi baseada no pyjwt
Dependências:
	- [[pyrsa]]

[[Teste ECDSA  SHA-256]]
```python
   def test_verify(self):
        key = ECKey(private_key, ALGORITHMS.ES256)
        msg = b"test"
        signature = key.sign(msg)
        public_key = key.public_key()

        assert bool(public_key.verify(msg, signature))
        assert not bool(public_key.verify(msg, b"not a signature"))
```


[[Teste HMAC SHA-256]]
```python
class TestHMACAlgorithm:
    def test_non_string_key(self):
        with pytest.raises(JOSEError):
            HMACKey(object(), ALGORITHMS.HS256)

    def test_RSA_key(self):
        key = "-----BEGIN PUBLIC KEY-----"
        with pytest.raises(JOSEError):
            HMACKey(key, ALGORITHMS.HS256)

        key = "-----BEGIN RSA PUBLIC KEY-----"
        with pytest.raises(JOSEError):
            HMACKey(key, ALGORITHMS.HS256)

        key = "-----BEGIN CERTIFICATE-----"
        with pytest.raises(JOSEError):
            HMACKey(key, ALGORITHMS.HS256)

        key = "ssh-rsa"
        with pytest.raises(JOSEError):
            HMACKey(key, ALGORITHMS.HS256)

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