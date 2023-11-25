---
github: https://github.com/cisco/node-jose
linguagem: Javascript
---
[[Teste RSA SHA-256]]
[[Teste RSA SHA-256]]
```js

var fixtures = {
  "4_1.rsa_v15_signature": cloneDeep(require("jose-cookbook/jws/4_1.rsa_v15_signature.json")),
  "4_2.rsa-pss_signature": cloneDeep(require("jose-cookbook/jws/4_2.rsa-pss_signature.json")),
  "4_3.ecdsa_signature": cloneDeep(require("jose-cookbook/jws/4_3.ecdsa_signature.json")),
  "4_4.hmac-sha2_integrity_protection": cloneDeep(require("jose-cookbook/jws/4_4.hmac-sha2_integrity_protection.json"))
};
 // signing
      if (fixture.reproducible) {
        it("signs to a compact JWS", function() {
          var options = {
            compact: true,
            protect: "*"
          };

          var signer = JWS.createSign(options, input.key);
          return signer.final(input.payload, "utf8").
            then(function(result) {
              assert.deepEqual(result, output.compact);
            });
        });
        it("signs to a general JSON JWS", function() {
          var options = {
            compact: false,
            protect: "*"
          };

          var signer = JWS.createSign(options, input.key);
          return signer.final(input.payload, "utf8").
            then(function(result) {
              assert.deepEqual(result, output.json);
            });
        });
        it("signs to a flattened JSON JWS", function() {
          var options = {
            format: "flattened",
            protect: "*"
          };

          var signer = JWS.createSign(options, input.key);
          return signer.final(input.payload, "utf8").
            then(function(result) {
              assert.deepEqual(result, output.json_flat);
            });
        });
      }


```

