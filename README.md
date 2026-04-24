# Desafio Backend Frameworks

## Sobre o projeto

A ideia aqui foi construir dois back-ends diferentes usando dois frameworks bem conhecidos: Node.js com Express e Java com Spring Boot. Mas o mais legal é que os dois seguem a mesma organização em camadas (aquele padrão MVC que a gente estuda). Ou seja, cada um tem suas pastas separadas por responsabilidade, o que deixa o código mais fácil de entender e mexer depois.

## Como organizei cada projeto

### Node.js / Express

No projeto com Node, eu dividi assim:

- **models:** aqui ficam os "formatos" dos dados que a aplicação usa. Por exemplo, o que é um usuário? Tem nome, e-mail, ID...
- **controllers:** é onde as requisições chegam e as respostas são preparadas. Quem manda buscar os dados e retorna pro cliente.
- **routes:** as rotas mesmo, tipo `/api/users`, que o cliente chama pra acessar cada funcionalidade.

### Java / Spring Boot

Já no Spring, a lógica é parecida, mas tem uma camadinha a mais:

- **models:** mesma coisa, representa os dados do sistema.
- **controllers:** também recebe as chamadas HTTP.
- **services:** aqui é diferente. No Spring, eu separei as regras de negócio (a lógica mais importante) em uma camada própria, o que deixa o controller mais enxuto.

## Comparando os dois frameworks na prática

**Configuração inicial:**

Olha, o Express é bem mais rápido pra começar. Você roda `npm init`, instala o pacote, e em poucos minutos já tem um servidor rodando. O Spring Boot não é difícil, mas tem mais passos: você precisa baixar o projeto no Initializr, configurar dependências, esperar o Maven baixar tudo... é mais "robusto", mas também mais demorado.

**Quantidade de código (verbosidade):**

Com Node.js você escreve beeem menos pra ter uma API simples. JavaScript é mais solto, dinâmico. Já o Java exige mais linhas: você precisa criar getters, setters, colocar anotações, definir tipos... Mas, pra falar a verdade, isso também ajuda a organizar melhor quando o projeto cresce.

**Gerenciamento de dependências:**

No Node, é tudo no `package.json` com npm (ou yarn). No Spring, usamos Maven, então as dependências ficam no `pom.xml`. Os dois fazem a mesma coisa, só que de jeitos diferentes.

## Como a comunicação acontece entre as camadas

Vou explicar com um exemplo real:

1. O usuário acessa `http://localhost:3000/api/users`.
2. A **rota** (routes) percebe que alguém chamou esse endereço e direciona pro **controller** certo.
3. O **controller** entende o que precisa ser feito. Se tiver regra de negócio, chama o **service** (no Spring). Se for só buscar dados, chama direto o **model**.
4. O **model** representa os dados (por exemplo, uma lista de usuários).
5. O controller pega esses dados e devolve uma resposta JSON bonitinha pro cliente.

Essa separação toda ajuda bastante na hora de dar manutenção. Você sabe exatamente onde mexer: problema de regra de negócio? Vai no service. Erro na resposta? Olha o controller. Rota que não funciona? Verifica as routes.

## 
Pra fechar...

O que esse desafio mostrou na prática é que **a arquitetura importa mais que o framework**. Tanto no Express quanto no Spring Boot, consegui organizar o código em camadas separadas. Cada um tem seus pontos fortes e fracos, mas no fim os dois servem muito bem pra construir APIs organizadas e que não viram uma bagunça com o tempo.

Se fosse resumir:

- **Express:** mais rápido, menos código, bom pra começar ou projetos menores.
- **Spring Boot:** mais estruturado, mais código, ideal pra sistemas grandes e times grandes.

Mas os dois funcionam.
