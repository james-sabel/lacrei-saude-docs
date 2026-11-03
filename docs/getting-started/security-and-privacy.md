# Segurança e Privacidade

Esta documentação registra práticas gerais de segurança e privacidade aplicáveis ao uso e desenvolvimento da plataforma **Lacrei Saúde**.

## Dados pessoais

Considerando o contexto de saúde, as informações manipuladas podem conter dados pessoais e dados sensíveis.

- Toda documentação deve utilizar exemplos fictícios.
- Ambientes de desenvolvimento e teste devem utilizar dados fictícios.

## Credenciais

- Não publicar tokens.
- Não publicar chaves de acesso.
- Não publicar credenciais de ambientes.
- Não armazenar segredos nos repositórios do Git.

## Proteção de dados

Recomenda-se:

- Uso de HTTPS em todas as comunicações.
- Criptografia dos dados em trânsito.
- Controle de acesso baseado em perfis.
- Registro de auditoria quando aplicável.
- Princípio do menor privilégio.

## LGPD

> ❓ **Requer revisão:** classificação oficial dos dados tratados pela plataforma conforme LGPD (sensíveis, pessoais, não sensíveis, política de exclusão).

Dados pessoais devem ser tratados de acordo com a Lei Geral de Proteção de Dados (LGPD).

Princípios relevantes:

- **Finalidade** - para que o dado é usado?
- **Necessidade** - o dado é realmente necessário?
- **Segurança** - como o dado é protegido?
- **Transparência** - quais dados são coletados?
- **Responsabilização** - quem é responsável pelo dado?

**O princípio básico é: se o dado não é necessário, não deve ser coletado.**

## Monitoramento

> ❓ **Requer revisão:** política de retenção de logs.

- Evitar exposição de dados sensíveis em logs (Sentry e AWS CloudWatch).
- Sanitizar informações pessoais antes do envio para sistemas de monitoramento.
