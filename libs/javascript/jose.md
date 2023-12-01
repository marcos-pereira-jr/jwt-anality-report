---
github: https://github.com/panva/jose
linguagem: Javascript
---
#lib 

[[Teste HMAC SHA-256]]
```js
test('SignJWT', async (t) => {
  const jwt = await new SignJWT(t.context.payload)
    .setProtectedHeader({ alg: 'HS256' })
    .sign(t.context.secret)
  t.is(
    jwt,
    'eyJhbGciOiJIUzI1NiJ9.eyJ1cm46ZXhhbXBsZTpjbGFpbSI6dHJ1ZX0.yPnOE--rxp3rJaYy0iZaW2Vswvus05G6_ZBdXqIdjGo',
  )
})
```


[[Teste RSA SHA-256]]
```js
async function testRSAsig(t, alg) {
  const message = `${alg} requires key modulusLength to be 2048 bits or larger`
  const keyBad = t.context.rsa2040
  const keyOk = t.context.rsa2048
  await t.throwsAsync(
    new FlattenedSign(t.context.payload)
      .setProtectedHeader({ alg })
      .sign(await importJWK(keyBad, alg)),
    { instanceOf: TypeError, message },
  )

  const jws = await new FlattenedSign(t.context.payload)
    .setProtectedHeader({ alg })
    .sign(await importJWK(keyOk, alg))

  await t.throwsAsync(flattenedVerify(jws, await importJWK(pubjwk(keyBad), alg)), {
    instanceOf: TypeError,
    message,
  })
}
```

[[Teste ECDSA  SHA-256]]
```javascript
async function testECDSASigEncoding(t, alg) {
  let { privateKey, publicKey } = await generateKeyPair(alg, { extractable: true })

  const jws = await new FlattenedSign(t.context.payload)
    .setProtectedHeader({ alg })
    .sign(privateKey)

  const derEncodedSignature = base64url.encode(
    crypto.sign(`sha${alg.slice(2, 5)}`, Buffer.from('foo'), await exportPKCS8(privateKey)),
  )

  await t.throwsAsync(flattenedVerify({ ...jws, signature: derEncodedSignature }, publicKey), {
    message: 'signature verification failed',
    code: 'ERR_JWS_SIGNATURE_VERIFICATION_FAILED',
  })
}
```

