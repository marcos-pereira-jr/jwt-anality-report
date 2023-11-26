#artigo


JWT é um padrão definida pela [[RFC-7519 - JSON Web Token (JWT)]] que especifica o formato e estrutura do token JWT, além disso ele especifica que o [[RFC-7515 - JSON Web Signature (JWS)]]  é responsável pela **integridade** e o [[RFC - 7516 - JSON Web Encryption (JWE)]] é responsável pela **privacidade**, todas essas especificações e algumas outras estão compiladas no [[Javascript Object Signing and Encryption (jose)]]



Características a serem analisadas 

|    |                          |                                                                                                                     |
|----|--------------------------|---------------------------------------------------------------------------------------------------------------------|
|    | Requisito                | Descrição                                                                                                           |
|    | Características          | Analisar o objetivo para qual a biblioteca foi feito, recomendações de uso, versões que estavam com erros críticos. |
|    | [[Capacidades]]              | Criptografias suportadas                                                                                            |
|    | Alcance                  | Número de downloads e projetos vinculados                                                                           |
|    | [[Identificadores de teste]] | Criaremos uma tabela que identifica testes cruciais que devem estar presente no código fonte                        |
|    | Segurança                | Quantos CVE estão abertos ou permaneceram aberto muito tempo na biblioteca                                          |
|    | Suporte da comunidade    | Quantidade de commits anuais, contribuidores, quantidades de questões levantadas e resolvidas                       |


##### Número de download semanal 

| ** | Linguagem  | Lib                | Número de downloads semanais | Estrelas no github |
|----|------------|--------------------|------------------------------|--------------------|
|    | Python     | [[pyjwt]]          | 29.403.798                       |  4.749             |
|    | Javascript | [[jsonwebtoken]]       | 14.411.984                   | 17.083             | 
|    | Javascript | [[jose]]               | 6.508.721                    |  4.104             | 
|    | Javascript |~~[[jwt-decode]]~~      | 5.564.026                    |  2.963             |
|    | Python     | [[python-jose]]        | 1.617.849                    |  1.391                 |
|    | Python     | ~~[[flask-jwt-extended]]~~ | 928.715                      |  1.461              |
|    | Python     | [[jwcrypto]] | ?                      |  ?              |
|    | Javascript | [[node-jose]] | ?                      |  ?              |

### Cobertura
| ** | Lib              | HS256 | RS256 | ES256 |
|----|------------------|-------|-------|-------|
|    | [[pyjwt]]        | v     | v     | v     |
|    | [[jsonwebtoken]] | v     | v     | v     |
|    | [[jose]]         | v     | v     | f     |
|    | [[jwcrypto]]     | v     | v     | v     |
|    | [[python-jose]]  | v     | v     | v     |
|    | [[node-jose]]    | v     | v     | v     |

#### Testes

| ** | Lib              | HS256 | RS256 | ES256 |
|----|------------------|-------|-------|-------|
|    | [[pyjwt]]        | v     | v     | v     |
|    | [[jsonwebtoken]] | v     | v     | v     |
|    | [[jose]]         | v     | v     | f     |
|    | [[jwcrypto]]     | v     | v     | v     |
|    | [[python-jose]]  | v     | v     | v     |
|    | [[node-jose]]    | v     | v     | v     |


### Vulnerabilidades 
| ** | Lib              | Moderada |  Gravidade Alta |
|----|------------------|-------|-------|
|    | [[pyjwt]]        | 0     | 1     | 
|    | [[jsonwebtoken]] | 4     | 0     | 
|    | [[jose]]         | 5     | 0     | 
|    | [[jwcrypto]]     | 1     | 0     | 
|    | [[python-jose]]  | 0     | 0     | 
|    | [[node-jose]]    | 0     | 1     |

### Contribuidores 
| ** | Lib              | Quantidade |
|----|------------------|-------|
|    | [[pyjwt]]        | 100   | 
|    | [[jsonwebtoken]] | 86    |
|    | [[jose]]         | 31    | 
|    | [[jwcrypto]]     | 32    |
|    | [[python-jose]]  | 39    |
|    | [[node-jose]]    | 32    |


### Problemas levantados pela comunidade

| **  | Lib              | Levantados | Resolvidos | Percentual resolvidos |
| --- | ---------------- | ---------- | ---------- | --------------------- |
|     | [[pyjwt]]        | 414        | 400        |    96%                  |
|     | [[jsonwebtoken]] | 619        | 511        |  82%                     |
|     | [[jose]]         | 128        | 128        |  100%                     |
|     | [[jwcrypto]]     | 141        | 134        |  95%                     |
|     | [[python-jose]]  | 145        | 77         |  53%                      |
|     | [[node-jose]]    | 173        | 120        |  69%                     |


### Commits no ultimo ano


```
#### Filtros
- ``tag:#lib  OR tag:#teste`` - Relação Lib x Test Alg  

```

### links 
- https://www.youtube.com/watch?v=bpB0pEro9qY

