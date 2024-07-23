# 1. Visão Geral

Este documento descreve o design arquitetônico e os componentes principais da Plataforma de Gestão de Tarefas. O objetivo é fornecer uma visão clara da estrutura do sistema, dos fluxos de dados e das decisões de design que guiam o desenvolvimento.

# 2. Arquitetura do Sistema

A plataforma é baseada em uma arquitetura de microserviços, onde cada serviço é responsável por uma funcionalidade específica. Isso facilita a escalabilidade, a manutenção e a evolução contínua do sistema.

## 2.1. Componentes Principais

**Gateway API:** Roteia as solicitações do cliente para os microserviços apropriados.<br>
**Auth Service:** Gerencia a autenticação e autorização dos usuários.<br>
**User Service:** Gerencia as informações dos usuários.<br>
**Task Service:** Gerencia as tarefas e os fluxos de trabalho.<br>
**Notification Service:** Envia notificações aos usuários.<br>
**Report Service:** Gera relatórios e análises de dados.<br>

## 2.2. Diagrama de Arquitetura

Em andamento

# 3. Design de Componentes

## 3.1. Gateway API

**Tecnologia:** PHP, Laravel<br>
**Responsabilidades:**
    Roteamento de solicitações para os microserviços.<br>
    Balanceamento de carga e controle de taxa de solicitação.<br>
    Implementação de segurança, como CORS e verificação de tokens JWT.<br>

## 3.2. Auth Service

**Tecnologia:** PHP, Laravel, JWT<br>
**Responsabilidades:**
        Gerenciamento de usuários (login, registro, logout).<br>
        Emissão e verificação de tokens JWT.<br>
        Gerenciamento de roles e permissões.<br>

## 3.3. User Service

**Tecnologia:** PHP, Laravel, MariaDB<br>
**Responsabilidades:**
        CRUD de informações dos usuários.<br>
        Gerenciamento de perfis de usuários.<br>
        Integração com o Auth Service para validação de usuários.<br>

## 3.4. Task Service

**Tecnologia:** PHP, Laravel, MariaDB
**Responsabilidades:**
        CRUD de tarefas.<br>
        Gerenciamento de estados e prioridades das tarefas.<br>
        Implementação de funcionalidades de colaboração em tarefas.<br>

## 3.5. Notification Service

**Tecnologia:** PHP, Laravel, Redis (para filas)<br>
**Responsabilidades:**
        Envio de notificações em tempo real e por e-mail.<br>
        Gerenciamento de preferências de notificação dos usuários.<br>
        Integração com outros serviços para eventos de notificação.<br>

## 3.6. Report Service

**Tecnologia:** PHP, Laravel, MariaDB<br>
**Responsabilidades:**
        Geração de relatórios baseados em dados de tarefas e usuários.<br>
        Exportação de relatórios em formatos diferentes (PDF, CSV).<br>
        Implementação de gráficos e visualizações de dados.<br>

# 4. Fluxos de Dados

## 4.1. Fluxo de Autenticação

O usuário envia uma solicitação de login para o Auth Service.<br>
O Auth Service valida as credenciais e emite um token JWT.<br>
O token JWT é enviado de volta ao cliente.<br>
O cliente inclui o token JWT em todas as solicitações subsequentes.<br>
Os microserviços validam o token JWT antes de processar as solicitações.<br>

## 4.2. Fluxo de Criação de Tarefa

O usuário envia uma solicitação para criar uma tarefa para o Task Service.<br>
O Task Service valida a solicitação e cria a tarefa no banco de dados.<br>
O Task Service envia uma notificação para o Notification Service.<br>
O Notification Service envia uma notificação ao usuário.<br>

# 5. Decisões de Design

## 5.1. Escolha da Arquitetura de Microserviços

Justificativa: A arquitetura de microserviços permite uma escalabilidade mais fácil e uma melhor separação de responsabilidades, facilitando a manutenção e a evolução do sistema.

## 5.2. Uso de MariaDB

Justificativa: MariaDB é escolhido pela sua confiabilidade, performance e compatibilidade com MySQL, facilitando a integração com aplicações existentes.

## 5.3. Autenticação com JWT

Justificativa: Tokens JWT são leves e permitem uma autenticação segura e eficiente, sem a necessidade de manter o estado do servidor.

# 6. Considerações Finais

Este design é uma base sólida para o desenvolvimento da Plataforma de Gestão de Tarefas. No entanto, a flexibilidade e a adaptação contínua são essenciais à medida que o projeto evolui e novas necessidades surgem.

Se tiver dúvidas ou sugestões, sinta-se à vontade para contribuir e discutir no repositório do projeto.
