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
| **  | Lib              | Moderada | Gravidade Alta |
| --- | ---------------- | -------- | -------------- |
|     | [[jose]]         | 5        | 0              |
|     | [[jsonwebtoken]] | 4        | 0              |
|     | [[jwcrypto]]     | 1        | 0              |
|     | [[node-jose]]    | 0        | 1              |
|     | [[python-jose]]  | 0        | 0              |
|     | [[pyjwt]]        | 0        | 1              |

### Contribuidores 
| **  | Lib              | Quantidade |
| --- | ---------------- | ---------- |
|     | [[pyjwt]]        | 100        |
|     | [[jsonwebtoken]] | 86         |
|     | [[python-jose]]  | 39         |
|     | [[node-jose]]    | 32         |
|     | [[jwcrypto]]     | 32         |
|     | [[jose]]         | 31         |


### Problemas levantados pela comunidade

| **  | Lib              | Levantados | Resolvidos | Percentual resolvidos |
| --- | ---------------- | ---------- | ---------- | --------------------- |
|     | [[jose]]         | 128        | 128        | 100%                  |
|     | [[python-jose]]  | 145        | 77         | 53%                   |
|     | [[node-jose]]    | 173        | 120        | 69%                   |
|     | [[jsonwebtoken]] | 619        | 511        | 82%                   |
|     | [[jwcrypto]]     | 141        | 134        | 95%                   |
|     | [[pyjwt]]        | 414        | 400        | 96%                   |


### Commits no ultimo ano

Dados de Semanais: 26/11/2023 - 19/11/2023 
Dados mensais 26/11/2023 - 27/10/2023
Dados anuais 26/11/2023 - 26/11/2023

| **  | Lib              | Ultima Semana | Ultimo Mês | Ultimo ano |
| --- | ---------------- | ------------- | ---------- | ---------- |
|     | [[jose]]         | 2             | 17         | 246        |
|     | [[pyjwt]]        | 0             | 1          | 49         |
|     | [[jwcrypto]]     | 0             | 0          | 10         |
|     | [[jsonwebtoken]] | 0             | 0          | 10         |
|     | [[python-jose]]  | 0             | 0          | 7          |
|     | [[node-jose]]    | 0             | 0          | 4          |



#### Data de criação do Repositório 

| **  | Lib              | Data da criação | Quantidade de commits |
| --- | ---------------- | --------------- | --------------------- |
|     | [[jwcrypto]]     | 04/03/2015      | 307                   |
|     | [[jose]]         | 06/11/2018      | 1375                  |
|     | [[node-jose]]    | 10/09/2015      | 275                   |
|     | [[python-jose]]  | 20/04/2015      | 657                   |
|     | [[pyjwt]]        | 24/02/2011      | 813                   |
|     | [[jsonwebtoken]] | 30/07/2013      | 449                   |

```
#### Filtros
- ``tag:#lib  OR tag:#teste`` - Relação Lib x Test Alg  

```

### links 
- https://www.youtube.com/watch?v=bpB0pEro9qY

