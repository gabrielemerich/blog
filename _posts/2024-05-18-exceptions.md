---
title: TITLE
date: 2023-11-13 11:00:00
categories: [TOP_CATEGORIE, SUB_CATEGORIE]
tags: [arch] # TAG names should always be lowercase
---

# O que é arquitetura

Organização fundamental de um sistema em seus componentes, responsabilidades e relacionamentos.

# Clean Code

Regra dos escoteiros: deixe a área do acampamento mais limpa do que você a encontrou.
Boas práticas:

- Complexidade ciclomática: métrica utilizada para medir a complexidade de um código, quando maior, mais complexo. Ex: if's alinhados
- Classe não contem verbos methodos sim (de preferência no infinitivo)
- extraia trechos em métodos privados
  -evite muitos parâmetros
  -leitura linear, cronológica, ler de cima para baixo sem confusão
  -boa identação

Comentários:

- um código que requer comentário, precisa ser reescrito
- não deixe trechos de código comentados

-Quando devo comentar um código

- licenças direitos autorais, versões etc..
- necessidade de explicar uma regra de negócio interna

Tratamento de erros:

- Não utilizar muitos try/catch e sim tratar excessões em um ponto centralizado/global.

# Design Patterns

Padrões de código para solução de problemas conhecidos.

Familias
Creational Patterns (Criacional) -> Meios de criação de um objeto, como será instanciado.
Structural Patterns (Estrutural) -> Composição de objetos por herenças e interfaces para diferentes funcionalidades
Behavioral Patterns (Comportamental) -> Tratam interações e comunicações entre objetos além da divisão de responsabilidades

www.dofactory.com

Creational Patterns:

- Abstract Factory
- Factory Method
- Singleton = economizar alocação de memória, alocar a instancia apenas uma vez na memória.

Structural Patterns:

- Adapter = A ideia do Adapter é quando você precisa adicionar ou modificar comportamentos a uma implementação que não pode mudar de contrato e o contrato não pode ser modificado em essencia.
  -Facade = Ponte com o mundo externo e a modelagem da sua aplicação. (exemplo integração com paypal)
  -Composite

Behavioral Patterns:
-Command
-Strategy
-Observer = notifcações

Termos:
cross cutting (atravessar cortando) = é a caixa de ferramentas da aplicação, pode atender todas as camadas
Patternite = Evite querer usar o design patterns só por usar, entenda a necessidade.

# ESTILOS ARQUITETURAIS

-Monolitica

- Microservice
- Arquitetura em camadas
  -REST
- Hexagonal Architecture "Ports & Adapters"

# PADRÕES ARQUITETURAIS

São semelhantes aos design patterns.
São usados de acordo com os estilos arquiteturais, exemplo:

- MVC
- SQRS : seperar leituras e escritas de dados, alterações (commands) leituras (queries). Quando possui uma alta demanda de dados, consumo, é legal utilizar.
- Event Sourcing: Manter/Salvar o estado anterior de uma entidade (tabela de logs)

# 3-Tier Architecture

Presentation Layer (front), Application Layer (back), DataLayer(Banco de dados)

# Clean Architecture

É um conceito de boas práticas assim como clean-code.

# Onion Architecture

É um estilo arquitetonico, onde as dependencias ocorrem de dentro para foram, sempre a partir do núcleo.

# DDD

Modelagem guiada pelo domínio do negócio.

Implementação:

- Entender o negócio
- Extrair linguagem ubíqua: Vocabulário, nome especificos relacionados ao negócio. Compartilhada por todas as partes envolvidas no projeto
- Modelagem estratégica: Extratir a linguagem ubíqua, é possível ter uma visão do negócio e segregar o domínio em partes.
  Modelagem de negócio: um produto assume seu papel em diversas áreas, já na modelagem de dominio, o produto assumento um papel dependendo do contexto onde se encontra.
- Definir a Arquitetura: pensar em tecnologia
- Modelagem tática: Modelar classes, serviços, objetos etc... Modelagem

* Camada de anticorrupção: Camada para impedir que a linguagem ubiqua de outras peças sejam impactadas, pode ser uma facade.

# Arquiteturas Evolutivas

Evolua aos poucos, não aplique complexidade desnecessária. Menos esforço mais resultados, sem otimização precoce.

# Tipos de Complexidade

Acidental: Causada pela abordagem escolhida para resolver o problema.
Essencial: Complexidade que se propõe a resolver. Problemas complexos se resolve com soluções complexas.

# Conway's Law

qualquer empresa que projeta um sistema, produz um projeto cuja a estrutura é uma cópia da forma com que a empresa se comunica (estrutura da empresa).

# Agilidade e Manifesto Ágil

-individuos e interações, mais que processos e ferramentas
-software em funcionamento, mais que documentação abrangente.

# DRY, KISS e YAGNI

Dry: (Dont repeat yourself), representação unica, não ambigua. Ex: string nome = "Edu" (ambiguidade). Correto: var nome = "Edu"
KISS: (Keep it simples), stupid Complexidade desnecessária deve ser descartada.
YAGNI: Não adicionar funcionalidades até que elas sejam realmente necessárias/requiridas.

# Evolução arquitetural

monolitos > distribuidos (segregado) > microserviços (granularizado)

# DDD vs 3 camadas

são coisas diferentes, ddd é uma filosofia de como orientar ou estruturar sua aplicação de acordo com o negócio.

# DDD

DDD é uma abordagem/modelagem com foco na complexidade da aplicação, onde é possível facilitar a implementação de complexas regras

- Toda arquitetura é design, mas nem todo design é arquitetura.
- Criar uma modelagem com base no negócio
  Pontos chaves:

  - ubiquituos language
  - bounded context = contexto delimitado
  - context map = mapa de contextos aqui acontece a modelagem estragética
  - história de usuário = ações que uma determinada funcionalidade tem, exemplo: Cadastro de usuário => o usuário poderá também editar o cadastro, excluir e etc.
  - tipos de dominio: core ou principal, auxiliar e genérico.
    -modelo de negócio: mundo real, a aplicação pode acabar caindo no big ball of mud, caso não seja aplicado o DDD
    -modelo de dominio: apresentado através do DDD

  Upstream vs Downstream = Contextos Upstream influenciam contextos Downstream, alguma mudança no requisito por exemplo.
  Camada anticorrupção = Garante que sua aplicação não seja corrompida.

  Tipos de relacionamento: Conformist -> Downstream dependem de Upstream, sem negociação

  - Costumer/Supplier: Oportunidade de levantar preoucapações e abordar alguma solução (com negociação)
    -Partner: Dependencia mutua entre dois contextos
    -Shared Kernel (Núcleo Compartilhado): modelo compartilhado, não pode ser alterado sem consultar os times que dependem dele.
    -Anti corruption Layer: Camada adicional dando ao contexto downstream uma interface fixa e independente do que acontece no upstream.

# Estilos e padrões arquiteturais

Spaghetti = Código macarronico, copiar e colar
Lasagna = Arquitetura em camadas
Ravioli = pequenos pedaços com responsabilidades diferentes (microserviços)

Transaction Script Pattern = realizar ações diretamente da camada de apresentação (webforms, mvc, etc...)
Table module pattern = Um módulo por tabela do banco de dados, a aplicação é orientada pelas tabelas do banco.
Domain Model Pattern = Abordagem do DDD. É agnostico ou ignorante, não sabe como o dominio deve ser persistido num repository por exemplo. Bons padrões para escrever um bom domínio.

Camada de aplicação = Orquestra ações disparadas pela apresentação (user cases), formata dados para a apresentação. Ela é dependente dos casos de uso (DTOS, Application Services)

Camada de domínio = Independe dos casos de uso, indepente da camada de aplicação (está voltado para o negócio). Contém (domain model, domain services, entidades)
Modelo Anêmico = Contém apenas propriedades (get, set)

# Modelagem Tática

- Escrever classes de domínio
- Domain services = repositories and external services (gateways de pagamento e etc)
  -Domain models = entities, factories, value types, aggregates etc..

- Value objects: São imutáveis, mais preciso que tipos primitivos. Atributos não ficam soltos em uma classe, agregam valor a uma entidade, não são persistidos no banco de dados. Quando você tem uma classe por exemplo, que representa algo. Exemplo:
  public string CPF;
  public Cpf Cpf;

-Entities: Possui estados e comportamentos, possui identidade, é exclusiva para o objeto mapeado, não faz persistencia no banco.

-Agregações: Pedido (raiz de agregação) > ItemPedido(Agregação). A raiz de agregação gerencia todo o processo. Utilizar um único repositório por agregação.

# CQRS

Commands = Representam uma intenção de mudança no estado de uma entidade, representam uma intenção de negócio
Queries = Forma de obter dados
CommandStack = Parte que trabalha com os comandos
QueryStack = Parte que trablaha com a Leitura

Teorema cap: Como manter o dado consistente? O teorema CAP aplica um tipo de lógica semelhante a sistemas distribuídos, a saber, que um sistema distribuído pode entregar apenas duas das três características desejadas: consistência, disponibilidade e tolerância de partição (tolerancia a falhas)

SAGAS: É um pattern arquitetural, fluxo continuo baseado em eventos Exemplo: Iniciar compra > selecionar produtos > Pagar > Saga concluida
Iniciar compra > selecionar produtos > Pagamento negado > A saga deve voltar cancelando a compra
