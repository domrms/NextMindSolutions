# 🚀 Portfólio Expandido: SmartWholesale AI (NextMind Solutions)

> **Aviso:** Este repositório documenta um cenário corporativo e técnico avançado desenvolvido como parte de um estudo de caso arquitetural de nível acadêmico e profissional. Todas as empresas, dados de desempenho e processos descritos (NextMind Solutions e Atacadão Norte Distribuidora) foram estruturados para fins de modelagem em Arquitetura de Sistemas, Inteligência Artificial Assistiva e Migração de Sistemas Legados.

---

## 👥 Equipe de Consultoria (NextMind Solutions)
* **Domingos Alves Ramos Neto** — Engenheiro de Software Backend & Especialista em Cloud Computing
* **Isabella Alvarenga** — Arquiteta de Soluções e Engenheira de Prompt
* **Isac Leal** — Analista de Negócios e Engenheiro de Dados
* **Lucas Alves** — Engenheiro DevOps e Especialista em Infraestrutura
* **Paulo Octavio** — Engenheiro de Software Fullstack
* **Wesly Santos** — Especialista em QA e Automação de Testes

---

## 🎯 1. O Desafio de Negócio e o Contexto do Legado

### 1.1 O Cenário da Atacadão Norte Distribuidora
A **Atacadão Norte Distribuidora** é uma empresa consolidada no setor de cadeia de suprimentos (*supply chain*), atuando massivamente no fornecimento de alimentos não perecíveis, produtos perecíveis e materiais de higiene e limpeza para milhares de pequenos e médios varejistas. Com uma operação logística que funciona 24/7, a eficiência operacional e a precisão do estoque são os pilares de sustentabilidade financeira da companhia.

### 1.2 A Anatomia do Monolito Legado
O grande gargalo que impedia a expansão de mercado da distribuidora era a sua infraestrutura de software: um sistema monolítico acoplado, implantado há mais de 15 anos. Características técnicas do ecossistema antigo:
* **Persistência Centralizada e Bloqueios de Tabela:** Banco de dados relacional sobrecarregado com *Stored Procedures* extensas executando regras de negócio diretamente na camada de dados, gerando frequentes *deadlocks* durante os horários de pico de vendas.
* **Falta de Modularidade:** Alterações na lógica de cálculo tributário de uma categoria de produto frequentemente quebravam o fluxo de checkout ou a emissão de notas fiscais (NF-e).
* **Ausência de Pipeline de CI/CD e Testes:** Implantações manuais via FTP/Cópia de binários, com cobertura zero de testes automatizados, resultando em alta taxa de regressão de bugs.

### 1.3 As Principais Dores Operacionais e Impactos Financeiros
* **Inconsistência Crítica de Dados:** Devido a falhas de concorrência e conciliação assíncrona, o estoque físico raramente correspondia ao saldo digital. Isso resultava em duas situações críticas: a venda de produtos inexistentes (gerando quebra de contrato e insatisfação) e o encalhe de mercadorias esquecidas no galpão.
* **Morosidade Operacional e Latência Analítica:** A extração e consolidação de relatórios de fechamento de vendas e projeção de demanda eram executadas manualmente por analistas através de *queries* pesadas. O processo demorava cerca de 4 horas, imobilizando o time de BI e entregando dados já defasados à diretoria.
* **Atrito na Experiência do Cliente e da Força de Vendas:** Os vendedores em campo e o time de telemarketing precisavam navegar por múltiplas telas lentas, com interfaces baseadas em terminal (CUI) ou formulários de desktop antigos, elevando o tempo médio de atendimento (TMA) e reduzindo a taxa de conversão de leads.

---

## 💡 2. A Solução: SmartWholesale AI

Para solucionar os gargalos operacionais sem desumanizar o atendimento comercial — que é o grande diferencial competitivo da distribuidora —, a NextMind Solutions projetou e arquitetou o **SmartWholesale AI**. Esta solução redefine a dinâmica de trabalho adotando o princípio da **Sinergia Colaborativa entre Humanos e Inteligência Artificial**.

+------------------------------------------------------------------------+
|                          SMARTWHOLESALE AI                             |
+------------------------------------------------------------------------+
|                                                                        |
|  +--------------------------------+    +----------------------------+  |
|  |     TRABALHO PESADO (IA)       |    | TRABALHO DE VALOR (HUMANO) |  |
|  +--------------------------------+    +----------------------------+  |
|  | * Consultas automáticas de     |    | * Negociações complexas e  |  |
|  |   estoque e conciliação.       |===>|   fechamento de contratos. |  |
|  | * Análise preditiva de compras |    | * Gestão de exceções e     |  |
|  |   em tempo real (Insights).    |    |   pedidos especiais.       |  |
|  | * Emissão de alertas ativos    |    | * Relacionamento consultivo|  |
|  |   de quebra de inventário.     |    |   e fidelização de clientes|  |
|  +--------------------------------+    +----------------------------+  |
|                                                                        |
+------------------------------------------------------------------------+

### 2.1 Divisão de Responsabilidades na Arquitetura Inteligente

* **O papel da Inteligência Artificial (Automação Cognitiva):**
  A IA assume todo o trabalho repetitivo, exaustivo e de alto processamento matemático. Ela monitora o banco de dados de inventário de forma reativa através de eventos, analisa o histórico de compras dos clientes recorrentes em milissegundos utilizando modelos preditivos e sugere a quantidade exata de reposição. Além disso, gera alertas proativos quando um item de alta rotatividade atinge o ponto de pedido crítico.
* **O papel do Profissional Humano (Decisão Estratégica):**
  Com os dados agregados, analisados e estruturados pela IA em painéis intuitivos, o vendedor elimina o tempo gasto procurando informações no sistema. Ele assume o papel de consultor de negócios, utilizando os insights gerados pela IA para fechar negociações complexas, gerenciar exceções logísticas (como entregas prioritárias) e construir relacionamentos de longo prazo com os clientes.

---

## 🛠️ 3. Engenharia de Migração: O Paradigma Spec-Driven Development com `spec-kit`

O maior desafio técnico do projeto não residia na criação da IA isoladamente, mas sim na extração segura de 15 anos de regras de negócio obscuras contidas no monolito para uma arquitetura moderna, escalável e baseada em nuvem. Para mitigar o risco de falha associado à reescrita manual de código (*Big Bang Rewrite*), a equipe implementou o **[spec-kit](https://github.com/github/spec-kit)**, uma ferramenta open-source desenvolvida sob o conceito de **Spec-Driven Development (SDD)**.

### 3.1 O que é Spec-Driven Development (SDD)?
O desenvolvimento orientado a especificações inverte o fluxo tradicional da engenharia de software. Durante décadas, o código fonte foi considerado o elemento supremo; as especificações funcionais e os diagramas eram apenas artefatos temporários, abandonados e desatualizados assim que a codificação real iniciava. 

No **SDD**, a especificação escrita em linguagem natural estruturada (Markdown) torna-se o artefato central e executável. A especificação não serve apenas para documentar, mas sim para **direcionar pipelines automatizados de IA que geram, validam e implementam a aplicação final**. O código passa a ser um derivado direto e automatizado da especificação.

### 🔄 3.2 O Fluxo de Migração Prático do Projeto

O processo de modernização do ecossistema da Atacadão Norte foi segmentado em quatro fases utilizando a CLI do `spec-kit`:

#### Passo 1: Definição da Constituição (`constitution.md`)
Alinhamos o time técnico para estabelecer as diretrizes permanentes de arquitetura e qualidade. Criamos a "Constituição do Projeto", um arquivo Markdown central que rege o comportamento de geração da IA:
* **Stack Alvo:** Backend robusto em C# utilizando as capacidades de alta performance do **.NET 10** e frontend responsivo em React.
* **Padrões de Projeto:** Aplicação rigorosa de *Clean Architecture* para separação de conceitos e *Domain-Driven Design (DDD)* para blindar o domínio de negócio contra acoplamentos de infraestrutura.
* **Métricas de Qualidade:** Obrigatoriedade de criação de testes unitários utilizando o framework `xUnit` e bibliotecas de asserção, exigindo cobertura mínima de **80%** das linhas de código de negócio.

#### Passo 2: Especificação das Regras (`specify`)
Realizamos sessões de engenharia reversa no monolito legado. Toda regra extraída (como as fórmulas complexas de partilha de ICMS e o fluxo transacional de baixa de estoque) foi traduzida em arquivos descritivos no diretório `.spec/`. Em vez de escrever diretamente as rotas e regras em C#, documentamos a intenção de forma técnica e declarativa:
> *"A rota de atualização de estoque deve aceitar requisições HTTP PUT contendo o ID do Produto e a Quantidade movimentada. Deve validar a consistência do saldo em banco de dados distribuído, persistir a alteração e, caso o saldo resulte em um valor abaixo do estoque de segurança cadastrado, disparar um evento de integração assíncrono via RabbitMQ para o microsserviço de compras."*

#### Passo 3: Planejamento Assistido (`plan`)
Ao acionar o motor do `spec-kit`, a IA interpretou de forma holística a nossa constituição global e as especificações de negócio isoladas. O sistema gerou um plano técnico detalhado contendo a proposta de contratos de interfaces, os modelos de domínio, mapeamento de tabelas no PostgreSQL e controladores de API. **A equipe técnica atuou como uma banca avaliadora, revisando, refinando e aprovando o plano arquitetural antes da escrita de qualquer linha de código produtivo.**

#### Passo 4: Implementação Automatizada (`implement`)
Com o plano técnico validado, o `spec-kit` orquestrou agentes de IA para codificar as estruturas base de código, injeção de dependências, entidades e os testes correspondentes em .NET 10. O papel do time de desenvolvimento transicionou de "digitadores de código repetitivo" para **revisores de código de alto nível (Code Review)**, focando em segurança, concorrência e validação de regras críticas.

---

## 📈 4. Resultados, Métricas e Impacto do Projeto

A reengenharia de software orientada pelo `spec-kit` e a implantação do SmartWholesale AI trouxeram retornos expressivos sobre o investimento (ROI):

1. **Otimização Analítica drástica:** O tempo de consolidação e geração de relatórios gerenciais complexos despencou de **4 horas manuais para apenas 30 minutos** processados nativamente em dashboards analíticos em tempo real.
2. **Exatidão e Integridade de Inventário:** Mitigação quase total das divergências entre o estoque físico e o sistema digital, reduzindo prejuízos por perda de validade de mercadorias perecíveis em armazém.
3. **Redução Acentuada no Tempo de Atendimento (TMA):** O tempo de resposta para fechamento e validação de pedidos complexos de clientes foi reduzido em **80%**, permitindo que a força de vendas atenda um portfólio significativamente maior de clientes por dia.
4. **Evolução da Cultura Técnica e de Negócio:** Os desenvolvedores passaram a focar na modelagem precisa de regras de negócio em Markdown em vez de perder tempo configurando códigos repetitivos de infraestrutura (*boilerplate*), enquanto o time de vendas se transformou de operadores de sistema em estrategistas comerciais.

---

## 📖 5. Guia Técnico: Instalação e Utilização do `spec-kit`

Para reproduzir a metodologia de desenvolvimento adotada no projeto SmartWholesale AI, siga o guia passo a passo detalhado abaixo para configurar o ecossistema do `spec-kit`.

### ⚙️ 5.1 Pré-requisitos
A ferramenta de linha de comando do `spec-kit` (Specify CLI) utiliza o gerenciador de pacotes e ambientes Python **`uv`** para garantir execuções rápidas e isoladas.

Certifique-se de ter o `uv` instalado em seu sistema operacional antes de prosseguir. Se não tiver, instale-o utilizando o comando oficial do instalador:
* **Linux/macOS:** `curl -LsSf https://astral.sh/uv/install.sh | sh`
* **Windows (PowerShell):** `powershell -c "irm https://astral.sh/uv/install.ps1 | iex"`

### 📥 5.2 Instalação da CLI do Specify (`specify-cli`)
Execute o comando abaixo para instalar globalmente a ferramenta de linha de comando utilizando o repositório oficial do GitHub. Certifique-se de substituir `vX.Y.Z` pela tag da versão estável mais recente disponível na aba de Releases do projeto:

```bash
uv tool install specify-cli --from git+[https://github.com/github/spec-kit.git@vX.Y.Z](https://github.com/github/spec-kit.git@vX.Y.Z)
```

### 📁 5.3 Inicialização de um Novo Projeto
Navegue até o diretório onde deseja criar a estrutura e execute o comando de inicialização informando o nome do projeto e a integração desejada (ex: GitHub Copilot):

```bash
specify init meu-projeto-smartwholesale --integration copilot
cd meu-projeto-smartwholesale
```

### 🔄 5.4 Comandos de Auto-Gerenciamento e Atualização
A CLI possui comandos integrados para verificar a existência de atualizações ou gerenciar versões instaladas localmente sem impactar outros ambientes do sistema:

# Executa uma checagem em modo leitura para verificar se há uma versão mais recente (não altera arquivos)
specify self check

# Pré-visualiza as ações que seriam executadas em um upgrade, sem aplicar as mudanças em disco
specify self upgrade --dry-run

# Executa a atualização automática no local para a última versão estável lançada
specify self upgrade

# Força a instalação ou realiza o downgrade/upgrade fixando uma tag específica do repositório
specify self upgrade --tag vX.Y.Z

Nota técnica: O comando specify self upgrade detecta automaticamente se a instalação original foi feita via uv tool ou pipx, executando a reconfiguração de forma transparente sob o capô. Caso precise limitar o tempo de execução do subprocesso do instalador em conexões lentas, você pode configurar a variável de ambiente SPECIFY_UPGRADE_TIMEOUT_SECS com o limite desejado em segundos.

### 🚀 5.5 Ciclo de Desenvolvimento Prático (Passo a Passo)
Uma vez que o projeto está inicializado, a interação com o motor do spec-kit ocorre diretamente por meio de agentes de codificação ou via comandos especializados da CLI. Veja como executar as etapas do ciclo completo:

Passo 1: Estabelecer os Princípios de Engenharia (constitution)
Abra a sua ferramenta de IA de preferência ou utilize os comandos integrados da CLI para criar as leis fundamentais do projeto. O comando criará as diretrizes de qualidade, performance e testes:

/speckit.constitution Criar princípios focados em qualidade de código .NET 10, padrões de teste xUnit com 80% de cobertura, arquitetura DDD e consistência de performance de APIs.
Passo 2: Redigir as Especificações Funcionais (specify)
Descreva o comportamento funcional e o valor de negócio do caso de uso que deseja construir, focando exclusivamente no o que a funcionalidade deve fazer e no porquê, sem se prender à codificação pura:

```bash
/speckit.specify Construir um módulo de gerenciamento de estoque que controle a entrada e saída de insumos. O sistema deve emitir um alerta visual na tela caso o saldo do item atinja o estoque mínimo e deve impedir movimentações de saída que resultem em saldo negativo.
Passo 3: Criar o Plano Técnico de Implementação (plan)
Nesta etapa, instrua o assistente técnico informando os detalhes da pilha de tecnologia e escolhas estruturais de software para que ele elabore o plano arquitetural:

```

```bash
/speckit.plan A aplicação backend deve utilizar .NET 10 Web API estruturada com Clean Architecture. O mapeamento objeto-relacional deve ser feito via Entity Framework Core apontando para um banco de dados relacional PostgreSQL local. Nenhuma persistência externa ou em nuvem deve ser configurada nesta fase.
Passo 4: Decompor o Plano em Tarefas Técnicas (tasks)
Com o plano técnico aprovado, solicite ao motor que quebre a arquitetura desenhada em tarefas granulares, sequenciais e acionáveis para o time ou para o agente automatizado:

```

```bash
/speckit.tasks
Passo 5: Executar a Implementação de Código (implement)
Com a lista de tarefas devidamente estruturada e validada pelos arquitetos humanos, ordene a geração automatizada de código para implementar a funcionalidade de forma limpa e em total conformidade com a Constituição do projeto:

```

```bash
/speckit.implement
```

## 🎯 6. Conclusão
O ecossistema SmartWholesale AI demonstra de forma empírica que a modernização de sistemas legados de missão crítica não precisa ser um processo traumático ou propenso a falhas catastróficas. Ao adotar o Spec-Driven Development por meio do spec-kit, a consultoria NextMind Solutions conseguiu criar uma ponte robusta entre as regras de negócio de 15 anos e os padrões arquiteturais de ponta do .NET 10. A automação cognitiva liberou o elemento humano para focar no que realmente gera valor: a estratégia comercial e a excelência operacional.
