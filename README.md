# Sumário

## Usuário

- [Criar Usuário](#criar-usuario)
- [Buscar Usuários](#buscar-usuarios)
- [Buscar Usuário por ID](#buscar-usuario-por-id)
- [Atualizar Usuário](#atualizar-usuario)
- [Apagar Usuário](#apagar-usuario)
- [Alugar Livro](#alugar-livro)
- [Devolver Livro](#devolver-livro)

## Livro

- [Criar Livro](#criar-livro)
- [Buscar Livros](#buscar-livros)
- [Buscar Livro por ID](#buscar-livro-por-id)
- [Atualizar Livro](#atualizar-livro)
- [Apagar Livro](#apagar-livro)

# USUARIO

- `rented` é a lista de livros alugados

## CRIAR USUARIO

REQUEST

`POST` /users

```json
{
  "name": ""
}
```

RESPONSE

```json
{
  "id": 0,
  "name": "",
  "rented": []
}
```

## BUSCAR USUARIOS

REQUEST

`GET` /users

RESPONSE

```json
[
  {
    "id": 0,
    "name": "",
    "rented": []
  }
]
```

## BUSCAR USUARIO POR ID

REQUEST

`GET` /users/:id

RESPONSE

```json
{
  "id": 0,
  "name": "",
  "rented": []
}
```

## ATUALIZAR USUARIO

REQUEST

`PUT` /users/:id

```json
{
  "name": ""
}
```

RESPONSE

```json
{
  "id": 0,
  "name": "",
  "rented": []
}
```

## APAGAR USUARIO

REQUEST

`DELETE` /users/:id

RESPONSE

Status 200 OK

## ALUGAR LIVRO

- Em caso de sucesso atualiar `status` do livro para `RENTED`
- Nao permitir alugar um livro ja alugado

REQUEST

`POST` /users/:id/rent-book

```json
{
  "bookId": 0
}
```

RESPONSE

```json
{
  "id": 0,
  "name": "",
  "rented": [
    {
      "id": 0,
      "title": ""
    }
  ]
}
```

## DEVOLVER LIVRO

- Em caso de sucesso atualiar `status` do livro para `AVAIBLE`
- Nao permitir devoler um livro nao alugado
- Nao permitir devolver um livro que este usuario nao tenha alugado

REQUEST

`POST` /users/:id/return-book

```json
{
  "bookId": 0
}
```

RESPONSE

```json
{
  "id": 0,
  "name": "",
  "rented": []
}
```

# LIVRO

- `status` nao pode ser nulo
- `status` pode ser apenas `RENTED` ou `AVAIBLE`

## CRIAR LIVRO

- cria um livro com `status` deve ser automaticamente colocado como `AVAIBLE`

REQUEST

`POST` /books

```json
{
  "title": ""
}
```

RESPONSE

```json
{
  "id": 0
}
```

## BUSCAR LIVROS

- parametro `status` nao é obrigatorio
- se o parametro `status` for nulo buscar todos os livros
- se o parametro `status` deve aceitar apenas `RENTED` ou `AVAIBLE`
- se o parametro `status` for `RENTED` buscar os livros com status `RENTED`
- se o parametro `status` for `AVAIBLE` buscar os livros com status `AVAIBLE`

REQUEST

`GET` /books?status=RENTED | AVAIBLE

RESPONSE

```json
[
  {
    "id": 0,
    "title": "",
    "status": "RENTED | AVAIBLE"
  }
]
```

## BUSCAR LIVRO POR ID

REQUEST

`GET` /books/:id

RESPONSE

```json
{
  "id": 0,
  "title": "",
  "status": "RENTED | AVAIBLE"
}
```

## ATUALIZAR LIVRO

REQUEST

`PUT` /books/:id

```json
{
  "title": ""
}
```

RESPONSE

```json
{
  "id": 0,
  "title": "",
  "status": "RENTED | AVAIBLE"
}
```

## APAGAR LIVRO

REQUEST

`DELETE` /books/:id

RESPONSE

Status 200 OK
