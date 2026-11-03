# Lacrei Saúde Docs

Projeto de documentação técnica da plataforma Lacrei Saúde. A documentação é escrita em Markdown, fica na pasta `docs/` e é compilada com o MkDocs.

## Executar localmente

> **Pré-requisito:** ter Python instalado.

1. Clone o repositório e entre na pasta do projeto.
2. Crie e ative um ambiente virtual:

   No Linux:

   ```bash
   python3 -m venv .venv
   source .venv/bin/activate
   ```

   No Windows (PowerShell):

   ```powershell
   python -m venv .venv
   .venv\Scripts\Activate.ps1
   ```

3. Instale as dependências:

   ```bash
   pip install -r requirements.txt
   ```

4. Inicie o servidor local:

   ```bash
   mkdocs serve
   ```

5. Acesse <http://127.0.0.1:8000> no navegador. O servidor atualiza a página automaticamente quando os arquivos da documentação são alterados.

## Compilar o site

Para gerar os arquivos estáticos em `site/`, execute:

```bash
mkdocs build
```
