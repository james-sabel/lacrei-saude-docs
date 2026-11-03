# Consultar perfil profissional - Contrato da API

> ❓ **Requer revisão:** os endpoints descritos abaixo são exemplos ilustrativos (mock). Não foram disponibilizados contratos reais da API para consulta. Também é preciso validar o método de autenticação e autorização, como tokens JWT, OAuth2, etc. A documentação abaixo é apenas uma referência inicial para o desenvolvimento do front-end.

**Endpoints:**

- Autenticação e autorização _(❓ carece de detalhes)_
- [Buscar profissional](#buscar-profissional) - `/api/v1/professionals/{id}`
- [Consultar lista de profissionais](#consultar-lista-de-profissionais) - `/api/v1/professionals`

---

## Buscar profissional

Buscar informações detalhadas de uma pessoa profissional de saúde pelo seu identificador único.

```http
GET /api/v1/professionals/{id}
```

### Parâmetros

| Campo | Tipo | Obrigatório | Descrição | Exemplo |
|---------|---------|---------|---------|---------|
| `id` | integer | Sim | Identificador da pessoa profissional de saúde | `123` |

Exemplo:

```http
GET /api/v1/professionals/123
Accept: application/json
```

### Respostas

#### Sucesso

Cadastro da pessoa profissional foi encontrado.

```http
200 OK
```

```json
{
  "id": 123,
  "full_name": "Dra. Ana Souza",
  "specialty": "Cardiologia",
  "city": "São Paulo",
  "bio": "Especialista em cardiologia clínica.",
  "rating": 4.8
}
```

#### Erros

Cadastro da pessoa profissional não foi encontrado.

```http
404 Not Found
```

```json
{
  "error": "Professional not found"
}
```

---

Erro interno do servidor.

```http
500 Internal Server Error
```

```json
{
  "error": "Internal server error"
}
```

## Consultar lista de profissionais

Buscar uma lista de pessoas profissionais de saúde disponíveis na plataforma, com suporte a filtros e paginação.

```http
GET /api/v1/professionals
```

### Parâmetros

| Campo | Tipo | Obrigatório | Descrição | Exemplo |
| --------- | --------- | --------- | --------- | --------- |
| `specialty` | string | Não | Especialidade da pessoa profissional | `cardiology` |
| `city` | string | Não | Cidade da pessoa profissional | `sao-paulo` |
| `page` | integer | Não | Número da página | `1` |

Exemplo:

```http
GET /api/v1/professionals?specialty=cardiology&city=sao-paulo&page=1
Accept: application/json
```

### Respostas

#### Sucesso

Lista de profissionais foi encontrada.

```http
200 OK
```

```json
{
  "results": [
    {
      "id": 123,
      "full_name": "Dra. Ana Souza",
      "specialty": "Cardiologia"
    }
  ]
}
```

#### Erros

Cadastro da pessoa profissional não foi encontrado.

```http
404 Not Found
``` 

```json
{
  "error": "No professionals found"
}
```
