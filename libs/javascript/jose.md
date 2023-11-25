---
github: https://github.com/panva/jose
linguagem: Javascript
---
#lib 

[[Teste RSA SHA-256 Parse And Verify]]
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


[[Teste HMAC SHA-256 - Invalid Signature]]
```js
test('incorrect hmac signature lengths', async (t) => {
  const jwt = await new SignJWT(t.context.payload)
    .setProtectedHeader({ alg: 'HS256' })
    .sign(t.context.secret)

  await t.throwsAsync(jwtVerify(jwt.slice(0, -3), t.context.secret), {
    code: 'ERR_JWS_SIGNATURE_VERIFICATION_FAILED',
    message: 'signature verification failed',
  })
})
```