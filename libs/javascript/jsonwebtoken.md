---
github: https://github.com/auth0/node-jsonwebtoken
linguagem: Javascript
---
#lib

Dependencias: 
	- [[node-jws]]


[[Teste RSA SHA-256]]
```js
describe('verify', function() {
  const pub = fs.readFileSync(path.join(__dirname, 'pub.pem'));
  const priv = fs.readFileSync(path.join(__dirname, 'priv.pem'));

  it('should first assume JSON claim set', function (done) {
    const header = { alg: 'RS256' };
    const payload = { iat: Math.floor(Date.now() / 1000 ) };

    const signed = jws.sign({
      header: header,
      payload: payload,
      secret: priv,
      encoding: 'utf8'
    });

    jwt.verify(signed, pub, {typ: 'JWT'}, function(err, p) {
      assert.isNull(err);
      assert.deepEqual(p, payload);
      done();
    });
  });
```


[[Teste HMAC SHA-256 - Invalid Signature]]
```js
	
  it('should not be able to verify unsigned token', function () {
    const header = { alg: 'none' };
    const payload = { iat: Math.floor(Date.now() / 1000 ) };

    const signed = jws.sign({
      header: header,
      payload: payload,
      secret: 'secret',
      encoding: 'utf8'
    });

    expect(function () {
      jwt.verify(signed, 'secret', {typ: 'JWT'});
    }).to.throw(JsonWebTokenError, /jwt signature is required/);
  });
```  
  