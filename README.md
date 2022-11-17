## NODE EXPRESS TS TEMPLATE

## Qual a função desse Repositório ?

1. Esse repositório é um template de API com NodeJs

## Sumário

[Tecnologias](#tecnologias)

[Como instalar](#como-instalar)

[Como utilizar](#como-utilizar)

[Diretorios](#diretorios)

[Detalhes](#detalhes)

[Projeto](#projeto)

## Tecnologias

1. NodeJs

2. Mongo

3. Jest

4. Express

5. Typescript

6. Babel

7. Supertest

## Como instalar

1. npm i

## Como utilizar

1. npm run start para inicializar a API

2. npm run test para rodar os testes

## Diretorios

1. mocks - Aqui temos mocks/stubs para os testes do serviço principal

2. models - Aqui temos o modelo do banco feito com Mongoose

3. repositories - Aqui foram armazenados códigos de interação com o banco de dados

4. services - Aqui estão as funções principais do script

5. controllers - Aqui temos o controle de fluxo e tratamento de erros https

6. routes - Aqui temos as rotas da aplicação

7. utils - Aqui encontram-se bibiliotecas/helpers

8. factories - Aqui serão realizadas as instâncias e a DI das classes do core

## Projeto

1. O Projeto em questão será uma API de duas entidades, com uma pasta especifica para
   cada entidade.

2. As entidades devem seguir o conceito de arquitetura em camadas, proposta durante o curso e enumerada no tópico `Diretórios`

3. Serão permitidas instalações de bibiliotecas de terceiros, fora as que já se encontram no `package.json`, dese que justificadas durante a apresentação do projeto

4. Critérios gerais de aceite:

ORM/Banco de dados

- Será obrigatório o uso da Mongoose para criação das Schemas e Models

Rotas

- É obrgatório o uso do Express

Testes de Integração

- O projeto deverá conter pelo menos um teste de Integração para cada Enpoint do
  domínio associado a respectiva entidade, verificando ao menos o StatusCode da response
  (Não será cobrado criação de ecossistema para teste de Integração)

Teste Unitários

- A camada de Repositórios deve conter pelo menos 1 teste unitário por Método/Função
- A camada de serviços deverá conter 1 teste unitário para retornos de sucesso
  e um teste para cada cenário de exceção
- A camada de controllers deve possuir um teste unitário para cada captura de exceção
  do serviço e um teste de resposta de sucesso
- Funções de validação ou Função de mensagem de erro. Todas deverão possuir arquivos de teste unitário

Documentação no Postman/Insomnia

- Todos os endpoints deverão estar documentados e exportados em formato link JSON
  do postman/insomnia
- Deverá ser possível rodar a API local e verificar cada execução de request com
  a documentação assim como os testes de integração com supertest/jest

Retorno das Rotas

- GetAll -> Toda a collection
- GetById -> Apenas o identificado
- Update -> Apenas o editado
- Create -> Apenas o criado

Extras/Opcionais

- Interfacear o Core da aplicação(Models, Repos, Service, Controller)
  \*(pesquisas sobre inversão de controle/inversão de dependência)
- Realizar o processo de DI com abstrações ao invés de detalhes
  É a letra D do Solid

5. Entidades e critérios de aceitação específico

Resenhas

- Cada acervo de Resenhas deverá conter um:

-> Título da Resenha de no máximo 24 caracteres (String) - Obrigatório - Único

-> Resenha: Texto de no máximo 200 caracteres (String[]) - Obrigatório

-> Data de criação: Formato de Data a sua escolha (new Date) - Obrigatório

-> Data de edição: Array com todas as datas de modificação (new Date[]) - Obrigatório

-> Nota do Autor: Um número de 1 a 5 (Number) - Obrigatório

- Essa API deverá ser capaz de interagir com uma lista(collection) de Resenhas do MONGODB

- Deverá ser possível: Criar, Editar, Listar, Listar por ID

- Não deverá ser possível apagar uma resenha
  rigatório - Único

- As edições devem ser acumuladas no Array de Resenhas e as datas no Array de datas,
  dessa maneira elas não irão se sobreescrever e serão correspondentes por index

- Os campos editaveis do Documento são: Resenhas(Apenas) e suas respectivas Datas

Livros

- Os Livros devem possuir

->Título: Texto de no máximo 24 caracteres(Esse título é diferente do título
da resenha em si) (String) - Obrigatório

-> Data de criação: Formato de Data a sua escolha (new Date) - Obrigatório

-> Idiomas disponíveis: Texto de no máximo 18 caracteres por String (String[]) - Obrigatório

-> Status: Campo booleano que indica se o livro é comercializado/Existe (boolean) - Obrigatório

-> Resenha: ID de uma Document de Resenha (ObjectId) - Opcional - Único

-> Autor: Texto de no máximo 24 caracteres (String) - Obrigatório - Único

- Essa API deverá ser capaz de interagir com uma lista de Livros do MONGODB

- Deverá ser possível: Criar, Editar, Listar, Listar por ID

- Não deverá ser possível apagar um livro

- Deverá possível alterar apenas o Status, os Idiomas disponíveis do livro e
  o ID do Documento de Resenhas referentes ao Livro

- A Listagem por ID deverá trazer todos dados da Resenha do respectivo livro caso
  ela exista. Caso não exista retorna o Documento em sua estrutura normal
  -> aqui deverá ser feito um aggregate/populate

- Na funcionalidade de Listar, deverá ser possível fazer uma consulta com Query Params
  por autor