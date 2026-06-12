# 🚀 Portfólio: SmartWholesale AI (NextMind Solutions)

> **Aviso:** Este repositório documenta um cenário hipotético desenvolvido como parte de um trabalho acadêmico. Todas as empresas, dados e processos descritos (NextMind Solutions e Atacadão Norte Distribuidora) são fictícios e criados para fins de estudo em Arquitetura de Sistemas, Inteligência Artificial e Migração de Legado.

## 👥 Equipe de Consultoria (NextMind Solutions)
* **Domingos Alves**
* **Isabella Alvarenga**
* **Isac Leal**
* **Lucas Alves**
* **Paulo Octavio**
* **Wesly Santos**

---

## 🎯 1. O Desafio de Negócio

A **Atacadão Norte Distribuidora** atua no fornecimento de alimentos e produtos de higiene. O grande gargalo da empresa era a sua infraestrutura tecnológica: um sistema monolítico implantado há mais de 15 anos. 

**Principais Dores Identificadas:**
- **Inconsistência de Dados:** O estoque físico raramente batia com o digital.
- **Morosidade Operacional:** A extração e consolidação de relatórios de vendas eram feitas de forma manual, consumindo horas da equipe.
- **Experiência do Cliente Prejudicada:** Vendedores precisavam navegar por múltiplas telas lentas para concluir um pedido, atrasando o atendimento.

## 💡 2. A Solução: SmartWholesale AI

Para resolver esses gargalos sem descaracterizar a força de vendas humana, a NextMind Solutions projetou o **SmartWholesale AI**. O foco principal desta arquitetura é a **Sinergia Colaborativa entre Humanos e Inteligência Artificial**.

- **O que a IA faz:** Assume o trabalho pesado. Ela automatiza consultas de estoque no banco de dados, analisa o histórico de compras em tempo real, faz sugestões preditivas de reposição para clientes recorrentes e emite alertas de inventário.
- **O que o Humano faz:** Assume o trabalho de valor. Com as informações já mastigadas e filtradas pela IA, a equipe comercial foca em fechar negociações complexas, gerenciar exceções e fidelizar o cliente.

---

## 🛠️ 3. Engenharia de Migração: Adoção do `spec-kit`

A etapa mais crítica do projeto não foi apenas implementar a IA, mas **migrar as regras de negócio do sistema antigo para uma arquitetura moderna**. Para isso, evitamos a reescrita manual massiva e adotamos o **[spec-kit](https://github.com/github/spec-kit)**, uma ferramenta open-source do GitHub baseada em *Spec-Driven Development* (Desenvolvimento Orientado a Especificações).

### O que é o Spec-Kit?
O `spec-kit` permite que arquitetos de software definam intenções, regras de negócio e padrões arquiteturais em Markdown puro. A partir dessa documentação, agentes de IA (como o GitHub Copilot Workspace ou agentes CLI) geram o planejamento e o código final.

### 🔄 Como utilizamos o Spec-Kit na Prática (Fluxo de Migração):

#### Passo 1: Definição da Constituição (`constitution.md`)
O primeiro passo foi ensinar à IA quais seriam as "leis" do nosso novo sistema. Criamos um arquivo de constituição no repositório definindo:
- **Stack Tecnológico:** C# / .NET 10 para o backend, React para o frontend.
- **Padrões de Arquitetura:** Uso estrito de *Clean Architecture* e *Domain-Driven Design* (DDD).
- **Regras de Qualidade:** Obrigatoriedade de testes unitários (xUnit) com cobertura mínima de 80%.

#### Passo 2: Especificação das Regras (`specify`)
Extraímos as lógicas do código legado (ex: cálculos de impostos, fluxo de baixa de estoque) e redigimos documentos descritivos na pasta `.spec/`. Em vez de codar a nova rota de API, escrevemos:
> *"A rota de atualização de estoque deve receber o ID do produto e a quantidade. Deve deduzir do inventário e disparar um evento via RabbitMQ caso o saldo caia abaixo do estoque mínimo."*

#### Passo 3: Planejamento Assistido (`plan`)
Ao rodar o CLI do `spec-kit`, a IA consumiu nossa constituição e nossas especificações, gerando um plano arquitetural. Ela propôs a criação das interfaces, os *controllers* e os modelos de banco de dados. **Nossa equipe humana revisou e aprovou o plano antes de qualquer código ser gerado.**

#### Passo 4: Implementação (`implement`)
Com o plano aprovado, o `spec-kit` orquestrou a geração de todo o *boilerplate* e do código estrutural limpo, aderente à `.NET 10`. O esforço da nossa equipe passou a ser o de revisão profunda (*Code Review*) em vez de digitação braçal.

---

## 📈 4. Resultados e Impacto do Projeto

1. **Eficiência em Relatórios:** Tempo de geração caiu de 4 horas (processo manual) para apenas **30 minutos** em painéis automatizados.
2. **Precisão de Estoque:** Redução drástica dos erros de inventário e das perdas por validade.
3. **Tempo de Resposta:** O atendimento inicial aos clientes foi acelerado em **80%**, dado que a IA compila o histórico e as sugestões antes mesmo de o vendedor iniciar a chamada.
4. **Transformação Cultural:** Os colaboradores deixaram de ser "operadores de sistema" e passaram a ser estrategistas de vendas.

O projeto prova que a modernização de legados, aliada à Inteligência Artificial Assistiva, é o caminho mais seguro e rentável para a transformação digital corporativa.
