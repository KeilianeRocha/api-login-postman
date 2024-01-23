<h1 align="center"> API Login </h1>
<p align="right">

#### Criado: 23 de janeiro de 2024 10:50
 Aula: Qa.Coders Academy
Tipo: Tutorial

[Postman.com/docs:](https://learning.postman.com/docs/introduction/overview/)

<img loading="lazy" src="http://img.shields.io/static/v1?label=STATUS&message=EM%20ANDAMENTO"/>
</p>

# Aqui estão os passos que fiz pra criar esse teste de API no Postman

### **Passo 01/Post**

- Baixei o Postman,
- Configurei,
- Fiz login(pois ja tinha conta criada),
- Criei um ´WORKSPACE´, add nome,
- Criei uma ´COLLECTION´ add nome,
- Criei uma ´REQUEST´ add nome,
    - Selecionei o ´MÉTODO´, (nesse caso era ´POST´)
    - Coloquei a ´URL´,
    - Coloquei o ´ENDPOINT´,
    - Coloquei o ´BODY´,
    
    ```json
    { 
    	"Key": "Value"
    }
    ```
    
    - Adicionei as informações no ´BODY´ de acordo com a regra de negócio,
    - Apertei ´SEND´,
- Retornou ´STATUSCODE 200 - OK´, o ´Usuário´ efetuou o ´Login´ com sucesso,
- Gerou um ´TOKEN´,
Validei ⇒

```markdown
STATUSCODE,
NOME,
TOKEN
```

### Passo 02/Variável de Ambiente

- Criei uma ´VARIAVEL DE AMBIENTE´ local => add nome do ambiente [Qa],
- Importei a ´VARIAVEL´ => {{variavel}} + ´ENDPOINT´

### Passo 03/ Pre-req

- Criei funções para os campos:

```markdown
FirstaName, 
LastName,
mail
```

- Declarei as variaveis:

```markdown
FirstName, 
LastName,
mail
```

- Para o email, usei um hash ({{$guid}}) dessa forma, conseguir gerar vários emails, com uma massa
de dados (nome) pequena, sem retornar erro (email já cadastrado). Ver documentação do postman ⇒

[Use predefined variables to return values | Postman Learning Center](https://learning.postman.com/docs/writing-scripts/script-references/variables-list/)

- Concatenei as variaveis:

```markdown
FirstaName e LastName,
FirstName e mail
```

- Digitei o comando pro Postman setar essas variaveis no ´ENVIRONMENT´ local,
- Importei as ´VARIAVEIS´ => {{variavel}} para os campos do ´BODY´,

```json
{ 
	"Key": "{{variable}}"
}
```

- Criei a ´VARIAVEL´ ´GLOBAL´ para o ´PASSWORD´ => add nome, coloquei mascára {{variavel}},
- Declarei a ´VARIAVEL´ para os campos do ´BODY´

### Passo 04/ Teste de Validação

- Na aba ´TESTE´ usei um modelo ´Snippets´,
- Validei o ´STATUSCODE´, o teste passou,
- Capturei o ´TOKEN´

```jsx
console.log(Json.parse(responseBody).token)
```

- Criei uma ´VARIAVEL´ ´TOKEN´
- Validei a lógica, usando o ´RUNNER´, teste de execução de massa
- Coloquei a msg ´FullName´ no environment ´GLOBAL´

  
