#artigo

A análise das bibliotecas JWT baseia-se nos padrões estabelecidos pelo grupo de padrões Javascript Object Signing and Encryption (jose), que define as diretrizes para o uso do JWT na internet. Dentro desses padrões, a RFC-7519 - JSON Web Token (JWT) especifica o formato do token, enquanto a RFC-7515 - JSON Web Signature (JWS) define a assinatura do token, garantindo a integridade da operação. Assim, os métodos para a geração de assinaturas tornam-se o ponto central da autenticação via JWT.

A RFC-7519 abrange os algoritmos para a geração de tokens, incluindo:

| alg Param | Digital Signature or MAC      | Implementation |
|-----------|-------------------------------|----------------|
| HS256     | [[HMAC SHA-256]]            | Required       |
| HS384     | HMAC using SHA-384            | Optional       |
| HS512     | HMAC using SHA-512            | Optional       |
| RS256     | [[RSA SHA-256]] using  SHA-256     | Recommended    |
| RS384     | RSASSA-PKCS1-v1_5 using  SHA-384      | Optional       |
| RS512     | RSASSA-PKCS1-v1_5 using  SHA-512    | Optional       |
| ES256     | ECDSA using P-256 and SHA-256 | Recommended    |
| ES384     | ECDSA using P-384 and SHA-384 | Optional       |
| ES512     | ECDSA using P-521 and SHA-512 | Optional       |
| PS256     | RSASSA-PSS using SHA-256 and   MGF1 with SHA-256 | Optional       |
| PS384     | RSASSA-PSS using SHA-384 and  MGF1 with SHA-384 | Optional       |
| PS512     | RSASSA-PSS using SHA-512 and   MGF1 with SHA-512 | Optional       |
| none      | No digital signature or MAC  performed | Optional       

Nesse trabalho iremos analisar se a biblioteca implementa o algoritimo obrigatório HS256 e também os 2 algoritmos recomentados RS256 
e EC256

Para analisarmos as bibliotecas JWT  usamos os criterios abaixo:


### Pesos atribuídos 
| **    | Propriedade                                                 | Peso | Ponto máximo obtido |
|-------|-------------------------------------------------------------|------|---------------------|
| A1    | Algoritmos geradores de assinatura cobertos                 | 5    | 15                  |
| A2    | Cobertura de Testes para Algoritmos geradores de assinatura | 5    | 15                  |
| B3    | Download Semanais                                           | 3    | 9                   |
| B4    | Quantidade de Contribuidores                                | 3    | 9                   |
| B5    | Estrelas no Github                                          | 3    | 9                   |
| B6    | Idade do projeto                                            | 3    | 9                   |
| C7    | Vulnerabilidades resolvidas                                 | 2    | 6                   |
| C8    | Problemas Levantados e resolvidos pela comunidade           | 2    | 6                   |
| D8    | Commits no ultimo anos                                      | 1    | 3                   |
| D9    | Quantidade de commits totais                                | 1    | 3                   |
| TOTAL |                                                             |      | 84                  |


A abordagem adotada para a análise das bibliotecas que implementam o JWT nas linguagens Python e JavaScript foi estruturada em quatro categorias distintas, cada uma atribuída a um conjunto específico de atributos. Cada categoria recebeu um peso correspondente, baseado em seu impacto perceptível pelos usuários da biblioteca, variando de A, com um peso de 5, a D, com um peso de 1. A pontuação máxima que uma biblioteca poderia alcançar em cada categoria seria de 15 pontos ou 3 pontos por atributo.
A Categoria A focaliza a implementação das criptografias obrigatórias e recomendadas pela biblioteca, bem como a presença de testes associados a cada uma dessas implementações, sendo atribuído um peso de 5. Por outro lado, a Categoria B, com peso 3, aborda o impacto na comunidade, considerando parâmetros como o número de downloads semanais, estrelas no GitHub, idade do projeto e quantidade de contribuidores.
A Categoria C, com peso 2, direciona-se a fatores que podem gerar impressões equivocadas sobre as bibliotecas, como problemas resolvidos levantados pela comunidade e vulnerabilidades resolvidas. Esta categoria busca fornecer uma visão abrangente, reconhecendo que bibliotecas mais recentes podem resolver um maior percentual de problemas, embora possam também conter vulnerabilidades já solucionadas em bibliotecas mais estabelecidas.
Na última Categoria D, atribuída com um peso de 1 ponto, são considerados fatores gerais do projeto, como o número total de commits e os commits realizados no último ano. Estes elementos, embora possam indicar uma biblioteca mais ativa, são interpretados com cautela, pois os commits podem variar significativamente em termos de complexidade e extensão.
A combinação ponderada dessas categorias visa proporcionar uma avaliação abrangente e equilibrada das bibliotecas, oferecendo uma percepções valiosa sobre a sua adequação e confiabilidade.


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
|    | Python     | [[jwcrypto]] | 309.800                      |  388              |
|    | Javascript | [[node-jose]] | 296.150                      |  671              |

dowloads
jsonwebtoken - 9
jose - 6
node-jose - 3

estrelas
jsonwebtoken - 9
jose - 6
node-jose - 3


### Cobertura
| ** | Lib              | HS256 | RS256 | ES256 |
|----|------------------|-------|-------|-------|
|    | [[pyjwt]]        | v     | v     | v     |
|    | [[jsonwebtoken]] | v     | v     | v     |
|    | [[jose]]         | v     | v     | v     |
|    | [[jwcrypto]]     | v     | v     | v     |
|    | [[python-jose]]  | v     | v     | v     |
|    | [[node-jose]]    | v     | v     | v     |

#### Testes 

| ** | Lib              | HS256 | RS256 | ES256 |
|----|------------------|-------|-------|-------|
|    | [[pyjwt]]        | v     | v     | v     |
|    | [[jsonwebtoken]] | v     | v     | v     |
|    | [[jose]]         | v     | v     | v     |
|    | [[jwcrypto]]     | v     | v     | v     |
|    | [[python-jose]]  | v     | v     | v     |
|    | [[node-jose]]    | v     | v     | v     |


### Vulnerabilidades  Resolvidas 
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

| **  | Lib              | Data da criação |
| --- | ---------------- | --------------- |
|     | [[jwcrypto]]     | 04/03/2015      |
|     | [[jose]]         | 06/11/2018      |
|     | [[node-jose]]    | 10/09/2015      |
|     | [[python-jose]]  | 20/04/2015      |
|     | [[pyjwt]]        | 24/02/2011      |
|     | [[jsonwebtoken]] | 30/07/2013      |

#### Commits totais

| **  | Lib              | Quantidade de commits |
| --- | ---------------- | --------------------- |
|     | [[jwcrypto]]     | 307                   |
|     | [[jose]]         | 1375                  |
|     | [[node-jose]]    | 275                   |
|     | [[python-jose]]  | 657                   |
|     | [[pyjwt]]        | 813                   |
|     | [[jsonwebtoken]] | 449                   |
```
#### Filtros
- ``tag:#lib  OR tag:#teste`` - Relação Lib x Test Alg  

```


### Javascript

|              |     |     |     |     |     |     |     |     |     |     |     |
| ------------ | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|              | B3  | B4  | A1  | A2  | C7  | B4  | C8  | D8  | B6  | D9  | TOTAL    |
| jsonwebtoken | 9   | 9   | 15  | 15  | 4   | 9   | 6   | 2   | 9   | 2   | 80    |
| jose         | 6   | 6   | 15  | 15  | 6   | 3   | 4   | 3   | 3   | 3   | 64    |
| node-jose    | 3   | 3   | 15  | 15  | 2   | 6   | 2   | 1   | 6   | 1   | 54    |


### Python
|             |    |    |    |    |    |    |    |    |    |    |    |
|-------------|----|----|----|----|----|----|----|----|----|----|----|
|             | B3 | B4 | A1 | A2 | C7 | B4 | C8 | D8 | B6 | D9 | TOTAL   |
| pyjwt       | 9  | 9  | 15 | 15 | 6  | 9  | 6  | 3  | 9  | 2  | 83 |
| python-jose | 6  | 6  | 15 | 15 | 2  | 6  | 2  | 1  | 3  | 3  | 59 |
| jwcrypto    | 3  | 3  | 15 | 15 | 4  | 3  | 4  | 2  | 6  | 1  | 56 |


Aqui vemos uma diferença ainda gritante entre o primeiro colocado de todas as categorias e os demais, a pyjwt perde somente para commits anuais, isso pode ser devido ao fato 
da lib ser a biblioteca mais antiga analisada e não precisar de grandes ajustes com o passar do tempo. Nesse sentido, a biblioteca pyjwt é a bilbioteca para assinatura de token JWT em python mais estável para se adotar em um projeto
### links 
- https://www.youtube.com/watch?v=bpB0pEro9qY

