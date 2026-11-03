# Configuração do ambiente de desenvolvimento

Este guia reúne os passos para preparar o ambiente Linux com as tecnologias usadas no desenvolvimento da **Lacrei Saúde**.

## Tecnologias usadas pela plataforma

### Front-end

- Next.js e TypeScript
- Styled-Components
- Marsha Design System e referências de design no Figma

### Back-end

- Python, Django e Django REST Framework
- Poetry para gerenciamento de dependências Python
- PostgreSQL
- Docker e Docker Compose

## Passo a passo de configuração

1. Obter os acessos necessários
2. Instalar as ferramentas
3. Preparar os repositórios
4. Iniciar os serviços e as aplicações

## 1. Obter os acessos necessários

Antes de começar, você precisará de acesso aos repositórios do projeto e às contas e recursos da **Lacrei Saúde**: repositórios, Figma, pacote do Marsha Design System, registros de contêineres e serviços de desenvolvimento.

> ❓ **Requer revisão**
>
> Listar acessos necessários e como solicitar o acesso. Listar também, se houver, as preferências de configuração e versões mínimas dos packages utilizados.
>
> - Permissões de acesso aos repositórios
> - Requisitos de ambiente (distro, versão do Node, IDE, etc.)
> - Acesso aos protótipos do Figma
> - Acesso a documentos internos

## 2. Instalar as ferramentas

### Node.js e gerenciador de pacotes

O **Next.js** requer **Node.js**. Use a versão declarada pelo projeto; um gerenciador de versões, como [Node Version Manager - nvm](https://github.com/nvm-sh/nvm), facilita alternar versões sem alterar a instalação do sistema.

**Versão do Node.js:** XX.XX.XX

> ❓ **Requer revisão:** versão exata do Node.js e do gerenciador de pacotes (npm, pnpm ou Yarn) a ser usada. Confirmar com a equipe.

### Python e Poetry

Instale o Python:

```bash
sudo apt install -y python3 python3-venv pipx
pipx ensurepath
```

Instale o Poetry e confira a versão:

```bash
pipx install poetry
poetry --version
```

Na pasta do back-end, instale as dependências definidas pelo projeto:

```bash
poetry install
```

### PostgreSQL (Docker Compose)

O banco de dados usado pelo projeto é o PostgreSQL, executado em contêineres Docker por meio do Docker Compose.

Instale o **Docker Engine** e o plugin **Docker Compose** seguindo as instruções oficiais para sua distribuição:

- [Docker Engine](https://docs.docker.com/engine/install/)
- [Docker Compose](https://docs.docker.com/compose/install/linux/)

Valide a instalação:

```bash
docker --version
docker compose version
```

## 3. Preparar os repositórios

Clone os repositórios usando as URLs fornecidas pela equipe. Os exemplos abaixo são ilustrativos:

> ❓ **Requer revisão:** obter URLs dos repositórios e substituir. Detalhar se front-end e back-end estão em repositórios separados ou no mesmo repositório.

```bash
git clone <url-do-repositorio>
```

### Variáveis de ambiente

> ❓ **Requer revisão:** aqui a documentação assume que o projeto contém um `.env.example` com as variáveis de ambiente necessárias.

Crie um arquivo de configurações `.env` a partir do exemplo abaixo:

> ❓ **Requer revisão:** inserir aqui a estrutura do arquivo `.env.example` com as variáveis de ambiente necessárias para o projeto.

Obtenha as credenciais de desenvolvimento com a equipe e substitua os valores nas variáveis de ambiente no arquivo `.env`.

> **Atenção!** Lembre-se de nunca commitar o arquivo `.env` com credenciais reais. Ele deve ser mantido localmente e ignorado pelo Git.

## 4. Iniciar os serviços e as aplicações

> ❓ **Requer revisão:** validar se o projeto usa de fato `docker-compose.yml`, porta do front-end, porta do back-end, porta do banco de dados e se há instruções específicas para iniciar os serviços.

### Docker Compose (quando fornecido)

No diretório que contém o arquivo `docker-compose.yml`, confira primeiro os serviços e as instruções do projeto. Em seguida, inicie os serviços:

```bash
docker compose up -d
docker compose ps
```

Para acompanhar os logs:

```bash
docker compose logs -f
```

Para encerrar:

```bash
docker compose down
```

### Front-end

Entre no diretório do Next.js e execute o front-end em ambiente de desenvolvimento:

```bash
npm run dev
```

No navegador, acesse a interface em: http://localhost:3000

Agora siga para a seção de **Back-end** para iniciar o servidor Django e validar a comunicação entre front-end e back-end.

### Back-end

Entre no diretório do Django e inicie o servidor de desenvolvimento:

```bash
poetry run python manage.py check
poetry run python manage.py migrate
poetry run python manage.py runserver
```

Caso queira conferir se o servidor está funcionando, acesse a URL do Django no navegador: http://localhost:8000

> ❓ **Requer revisão:** incluir aqui algum comando de API de health check, se houver, para validar a comunicação entre front-end e back-end.

## 5. Design System e Figma

- Solicite acesso ao arquivo ou projeto de Figma usado pela equipe.
- Consulte as orientações do repositório para instalar e importar o **Marsha Design System**.
- Sempre use os componentes e tokens oficiais. Caso precise recriar estilos localmente, solicite a criação de novos tokens ou componentes à equipe responsável.
- Não inclua arquivos, fontes ou outros recursos do Figma no repositório sem verificar as permissões e o fluxo de contribuição.

## 6. Verificação rápida

Ao final, confirme que:

- As versões de Node.js e Python correspondem às exigidas pelos projetos.
- As dependências foram instaladas a partir dos lockfiles existentes.
- PostgreSQL ou o serviço de banco no Docker está disponível e acessível pela aplicação.
- O Django passa em `manage.py check` e inicia sem erro de configuração.
- O front-end inicia sem erro e consegue acessar os serviços necessários.
- Arquivos com credenciais locais não aparecem entre as alterações do Git.

Para revisar alterações locais:

```bash
git status --short
```

## Problemas comuns

> ❓ **Requer revisão:** listar aqui possíveis problemas e soluções, como erros de dependências, conflitos de versão, problemas de permissão, etc. Buscar com a equipe de desenvolvimento para compilar uma lista de problemas conhecidos e suas soluções.
