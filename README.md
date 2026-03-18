# pipeline-labs

Este repositório reúne exemplos de GitHub Actions usados em treinamento prático.

## Roteiro de aprendizado - Labs 01 a 11

Os primeiros 11 labs cobrem conceitos fundamentais de GitHub Actions. Recomenda-se rodar em ordem.

### Lab 01 - Estrutura de Diretórios e Arquivos

Arquivo: `.github/workflows/lab-01.yml`

Objetivo:

- Entender a estrutura de um workflow do GitHub Actions.
- Conhecer os 3 elementos obrigatórios: `name`, `on` e `jobs`.
- Usar variáveis de ambiente e contexto do GitHub.

O que o workflow faz:

1. Executa em `push` na branch `main` ou manualmente.
2. Lista a estrutura do diretório `.github/workflows/`.
3. Exibe os elementos obrigatórios do workflow.
4. Demonstra acesso a variáveis de ambiente e contexto.

Conceitos-chave:

- `name`: Nome visível nas interfaces.
- `on`: Define quando o workflow executa.
- `jobs`: Lista de trabalhos (units of work).
- `steps`: Passos executados dentro de um job.
- `uses` vs `run`: ações pré-construídas vs comandos shell.

### Lab 02 - Schedule Trigger Workflow

Arquivo: `.github/workflows/lab-02.yml`

Objetivo:

- Agendar workflows para rodar em horários específicos.
- Usar sintaxe cron para triggers periódicos.

O que o workflow faz:

1. Executa automaticamente em horários programados (cron).
2. Exibe informações sobre quando foi disparado.
3. Simula um relatório diário automatizado.

Conceitos-chave:

- `on.schedule`: Define triggers periódicos.
- Sintaxe cron: como agendar tarefas (dia, hora, minuto, etc.).
- Contexto `github.event`: acesso a metadados do evento.

### Lab 03 - Push Trigger Workflow

Arquivo: `.github/workflows/lab-03.yml`

Objetivo:

- Disparar workflows automaticamente em push.
- Filtrar por branch específica.

O que o workflow faz:

1. Dispara quando há push na branch `main`.
2. Mostra informações do evento de push.
3. Lista arquivos modificados.

Conceitos-chave:

- `on.push`: Dispara em modificações.
- Filtering: limitar por branch ou caminho.
- Contexto `github.event.head_commit`: acesso a detalhes do commit.

### Lab 04 - Issue Trigger Workflow

Arquivo: `.github/workflows/lab-04.yml`

Objetivo:

- Disparar workflows em eventos de issue.
- Demonstrar automação baseada em repositório.

O que o workflow faz:

1. Executa quando uma issue é aberta.
2. Busca informações da issue via contexto.
3. Simula comentário automático.

Conceitos-chave:

- `on.issues`: Dispara em eventos de issue.
- `permissions`: Define o que o workflow pode fazer no repositório.
- Contexto `github.event.issue`: acesso aos dados da issue.

### Lab 05 - Jobs Paralelos

Arquivo: `.github/workflows/lab-05.yml`

Objetivo:

- Executar múltiplos jobs simultaneamente.
- Entender a diferença entre jobs paralelos e sequenciais.

O que o workflow faz:

1. Cria 3 jobs que rodam em paralelo: análise, testes, build.
2. Cada job executa etapas diferentes.
3. Demonstra upload de artefatos.

Conceitos-chave:

- Jobs paralelos por padrão.
- `needs`: Criar dependências entre jobs (caso desejado).
- `artifacts`: Transferir dados entre jobs.

### Lab 06 - Matrix Strategy

Arquivo: `.github/workflows/lab-06.yml`

Objetivo:

- Executar testes em múltiplas versões de linguagens/SO simultaneamente.
- Reduzir duplicação de código com matrix.

O que o workflow faz:

1. Roda testes em múltiplas versões de Node.js e sistems operacionais.
2. Combina variáveis via `matrix`.
3. Demonstra acesso aos valores da matriz dentro do job.

Conceitos-chave:

- `strategy.matrix`: Define múltiplas combinações.
- `matrix.*`: Acesso aos valores da combinação atual.
- Economia de YAML e reutilização lógica.

### Lab 07 - Steps Condicionais

Arquivo: `.github/workflows/lab-07.yml`

Objetivo:

- Executar etapas condicionalmente.
- Depender de eventos, branches ou status anterior.

O que o workflow faz:

1. Executa steps diferentes conforme o evento.
2. Deploy apenas em branches específicas.
3. Mostra uso de `failure()` e `always()`.

Conceitos-chave:

- `if`: Condicional na etapa.
- `github.event_name`: Tipo de evento.
- `github.ref`: Branch ou tag.
- `failure()`, `success()`, `always()`: Status anteriores.

### Lab 08 - Demonstração de Variáveis de Ambiente

Arquivo: `.github/workflows/lab-08.yml`

Objetivo:

- Entender os 3 níveis de variáveis: workflow, job e step.
- Usar variáveis para reutilizar valores.

O que o workflow faz:

1. Define variáveis em nível de workflow.
2. Define variáveis em nível de job.
3. Define variáveis em nível de step.
4. Exibe e usa essas variáveis em comandos.

Conceitos-chave:

- `env` em workflow, job e step.
- Escopo e override de variáveis.
- Acesso via `${{ env.NOME }}` ou `$NOME` em shell.

### Lab 09 - Demo GitHub Secrets

Arquivo: `.github/workflows/lab-09.yml`

Objetivo:

- Guardar dados sensíveis de forma segura.
- Entender a diferença entre `secrets` e `variables`.

O que o workflow faz:

1. Usa secrets em variáveis de ambiente.
2. Simula conexão com API e banco de dados.
3. Mostra que o GitHub mascara automaticamente valores.

Conceitos-chave:

- `secrets.*`: Acesso a dados sensíveis.
- Mascaramento automático nos logs.
- Indisponibilidade em forks.
- Escrita no repositório → Configurações → Secrets.

### Lab 10 - Deploy Multi-Ambientes

Arquivo: `.github/workflows/lab-10.yml`

Objetivo:

- Separar configurações por ambiente.
- Usar `environment` para controlar deploy.

O que o workflow faz:

1. Define scripts de deploy para dev, staging e production.
2. Usa `environment` para separar contexto.
3. Garante sequência: dev → staging → production.

Conceitos-chave:

- `environment`: Agrupamento lógico com variáveis/secrets próprios.
- `needs`: Criar chains de jobs.
- Variáveis diferentes por environment.
- Potencial para aprovações manuais.

### Lab 11 - Contextos e Expressões

Arquivo: `.github/workflows/lab-11.yml`

Objetivo:

- Dominar os contextos disponíveis no GitHub Actions.
- Usar expressões e funções para lógica dinâmica.

O que o workflow faz:

1. Exibe contextosgithub` e `runner`.
2. Demonstra `outputs` entre steps e entre jobs.
3. Usa expressões com `contains()`, `startsWith()`, `endsWith()`, `format()`.
4. Conecta tudo em lógica condicional complexa.

Conceitos-chave:

- Contextos: `github`, `runner`, `env`, `job`, `steps`.
- Outputs de steps com `steps.ID.outputs.NOME`.
- Expressões com `${{ }}`.
- Funções: `contains()`, `startsWith()`, `endsWith()`, `format()`, `toJSON()`.
- Acesso a `needs.JOB.outputs.NOME` de jobs anteriores.

---

## Ciclo Avançado - Labs 12 a 14

Os labs 12, 13 e 14 mostram um padrão mais restrito para acesso a segredos usando OIDC com cofres externos.

Ideia central:

- O GitHub Actions não guarda a credencial final do provedor.
- O workflow recebe um token OIDC temporário do GitHub.
- AWS, GCP ou Azure validam esse token e decidem se liberam ou não o acesso ao segredo.
- Os identificadores usados nesses labs foram tratados como `secrets` para reduzir exposição de contexto.

### Lab 12 - AWS Secrets Manager com OIDC

Arquivo: `.github/workflows/lab-12.yml`

Objetivo:

- Autenticar na AWS sem access key estática.
- Assumir uma role via OIDC.
- Ler um segredo do AWS Secrets Manager.

O que o workflow faz:

1. Executa manualmente via `workflow_dispatch`.
2. Só roda quando disparado na branch `main`.
3. Usa o environment `lab12-aws-prod`.
4. Assume a role informada em `LAB12_AWS_ROLE_TO_ASSUME`.
5. Busca o segredo definido em `LAB12_AWS_SECRET_ID`.
6. Mantém o valor fora dos logs.

Secrets esperadas no GitHub:

- `LAB12_AWS_REGION`
- `LAB12_AWS_ROLE_TO_ASSUME`
- `LAB12_AWS_SECRET_ID`

Restrição recomendada na AWS:

- Limitar a trust policy da role ao repositório correto.
- Exigir `sub` do token OIDC compatível com o environment `lab12-aws-prod`.
- Permitir leitura apenas do segredo necessário.

### Lab 13 - GCP Secret Manager com OIDC

Arquivo: `.github/workflows/lab-13.yml`

Objetivo:

- Autenticar no Google Cloud sem chave JSON estática.
- Trocar o token OIDC por credenciais temporárias.
- Ler um segredo do Secret Manager.

O que o workflow faz:

1. Executa manualmente via `workflow_dispatch`.
2. Só roda quando disparado na branch `main`.
3. Usa o environment `lab13-gcp-prod`.
4. Autentica usando Workload Identity Federation.
5. Busca o segredo definido em `LAB13_GCP_SECRET_NAME`.
6. Mantém o valor fora dos logs.

Secrets esperadas no GitHub:

- `LAB13_GCP_PROJECT_ID`
- `LAB13_GCP_WORKLOAD_IDENTITY_PROVIDER`
- `LAB13_GCP_SERVICE_ACCOUNT`
- `LAB13_GCP_SECRET_NAME`

Restrição recomendada no GCP:

- Limitar a federação ao repositório correto.
- Restringir a condição para o subject do environment `lab13-gcp-prod`.
- Dar à service account apenas permissão de leitura do segredo necessário.

### Lab 14 - Azure Key Vault com OIDC

Arquivo: `.github/workflows/lab-14.yml`

Objetivo:

- Autenticar na Azure sem client secret estático.
- Trocar o token OIDC por autenticação federada.
- Ler um segredo do Azure Key Vault.

O que o workflow faz:

1. Executa manualmente via `workflow_dispatch`.
2. Só roda quando disparado na branch `main`.
3. Usa o environment `lab14-azure-prod`.
4. Entra na Azure com federated credentials.
5. Busca o segredo definido em `LAB14_AZURE_SECRET_NAME`.
6. Mantém o valor fora dos logs.

Secrets esperadas no GitHub:

- `LAB14_AZURE_CLIENT_ID`
- `LAB14_AZURE_TENANT_ID`
- `LAB14_AZURE_SUBSCRIPTION_ID`
- `LAB14_AZURE_KEYVAULT_NAME`
- `LAB14_AZURE_SECRET_NAME`

Restrição recomendada na Azure:

- Criar federated credential específica para o repositório.
- Amarrar o subject ao environment `lab14-azure-prod`.
- Dar ao principal apenas permissão de leitura no segredo necessário do Key Vault.

## Por que estes labs estão mais restritos

Os três labs seguem o mesmo desenho de segurança inicial:

- `workflow_dispatch` para evitar execução automática desnecessária.
- `if: github.ref == 'refs/heads/main'` para limitar a execução à branch principal.
- `environment` exclusivo por lab para separar contexto e permitir proteções adicionais.
- `permissions` mínimas com `id-token: write` e `contents: read`.
- Uso de `secrets` no GitHub até para identificadores, seguindo um modelo conservador.

## Importante para o treinamento

Esses labs mostram o passo inicial de um desenho seguro, mas não tornam o acesso impossível para qualquer novo workflow do mesmo repositório.

O acesso real continua dependendo principalmente de duas camadas:

1. Configuração do GitHub:

- repositório onde os secrets estão disponíveis
- environment usado pelo job
- regras e aprovações do environment

2. Política no provedor cloud:

- trust policy na AWS
- workload identity conditions no GCP
- federated credentials na Azure

Se a política do provedor estiver ampla demais, outro workflow do mesmo repositório ainda pode conseguir acesso.

## Leitura recomendada antes de executar

Antes de rodar os labs 12, 13 e 14, a pessoa deve entender estas três ideias:

1. OIDC evita credencial estática no GitHub.
2. `Environment` ajuda a separar contexto, mas não é uma barreira absoluta sozinho.
3. O controle mais forte está no provedor de nuvem, não apenas no YAML.
