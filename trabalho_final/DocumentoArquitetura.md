# Proposta Arquitetural para Sistema de Monitoramento e Automação Agrícola

## Estilo Arquitetural Adotado

- **Arquitetura em Camadas**  
  O sistema será estruturado em camadas bem definidas, garantindo separação de responsabilidades e facilitando a manutenção e evolução do sistema.

- **Padrão Arquitetural: MVC (Model-View-Controller)**  
  Utilização do padrão MVC para organizar os componentes de software:  
  - **Model**: Representação das entidades de domínio, incluindo sensores, dados meteorológicos e parâmetros do solo.  
  - **View**: Interfaces para interação com o usuário, incluindo dashboards, notificações e recomendações.  
  - **Controller**: Coordenação das interações entre Model e View, bem como processamento das regras de negócio.

---

## Modelo de Representação Arquitetural: Modelo C4

Optamos pelo uso do **Modelo C4** para representar visualmente os diferentes níveis de abstração do sistema. O Modelo C4 compreende quatro níveis:

1. **Contexto**: visão geral do sistema e suas interações externas.  
2. **Contêineres**: componentes executáveis e suas relações.  
3. **Componentes**: divisão dos contêineres em componentes internos.  
4. **Código**: visão detalhada do código-fonte (opcional nesta proposta).

---

## Requisitos Funcionais Prioritários

| ID | Descrição | Prioridade |
| --- | --- | --- |
| 1 | O sistema deve adaptar a irrigação do solo com base em previsões meteorológicas (umidade, chuva, seca). | ALTA |
| 2 | Rede de sensores de solo com comunicação sem fio que colete dados em tempo real sobre umidade, temperatura, pH e nutrientes em diferentes zonas da plantação, permitindo irrigação e fertilização automatizadas e personalizadas para cada microárea da lavoura. | ALTA |
| 3 | O sistema deve permitir que pragas ou outros problemas nas plantações sejam identificados e um alerta seja gerado aos usuários. | ALTA |
| 4 | O sistema deve fornecer recomendações de plantio com base em análises de solo. | ALTA |
| 5 | O sistema deve analisar as condições do solo e do clima para prever o melhor momento para a colheita. | ALTA |

---

## Visão Geral da Arquitetura

### 🎯 **Camadas Arquiteturais**

1. **Camada de Apresentação (View)**  
   - Interface Web/Mobile para exibir dashboards, alertas, relatórios e recomendações.
   - Notificações em tempo real para os usuários.

2. **Camada de Controle (Controller)**  
   - Orquestra as operações do sistema: coleta de dados, análises, envio de comandos para automação.  
   - Coordena comunicação com APIs de previsão meteorológica.

3. **Camada de Negócio (Model)**  
   - Modelos de dados para representar sensores, plantações, clima, solo e ações automatizadas.  
   - Processamento de dados para gerar recomendações, alertas e decisões de irrigação.

4. **Camada de Persistência**  
   - Banco de dados para armazenar dados históricos de sensores, previsões climáticas, diagnósticos e ações realizadas.  
   - Eventualmente, uso de banco NoSQL para dados de sensores e SQL para dados relacionais.

5. **Camada de Infraestrutura**  
   - Rede de sensores IoT com comunicação sem fio (LoRa, Zigbee, Wi-Fi).  
   - Gateways de borda para pré-processamento e envio de dados à nuvem ou sistema central.  
   - Integração com serviços externos de previsão meteorológica.

---

## Aplicação do Modelo C4

### **1. Diagrama de Contexto**  
- Usuários (agricultores, técnicos) interagem com o sistema via interfaces.  
- Sensores de solo e clima enviam dados ao sistema.  
- Integração com APIs meteorológicas.  
- Sistema emite comandos de automação para irrigação/fertilização.

### **2. Diagrama de Contêineres**  
- **Frontend**: Interface Web/Mobile.  
- **Backend**: Serviços de controle e processamento de dados.  
- **Banco de Dados**: Armazenamento estruturado e não estruturado.  
- **Gateways IoT**: Coleta e pré-processamento de dados dos sensores.

### **3. Diagrama de Componentes**  
- **Módulo de Coleta de Dados**: integração com sensores e APIs.  
- **Módulo de Processamento Analítico**: previsão de colheita, detecção de pragas, recomendação de plantio.  
- **Módulo de Automação**: acionamento de irrigação e fertilização.  
- **Módulo de Notificações**: envio de alertas aos usuários.  
- **Módulo de Relatórios**: geração de relatórios e dashboards.

---

## Considerações Arquiteturais

- **Escalabilidade**: o sistema deve suportar expansão da rede de sensores.  
- **Resiliência**: tolerância a falhas na comunicação dos sensores e nas integrações com APIs.  
- **Segurança**: garantir proteção de dados e autenticação nos acessos.  
- **Manutenibilidade**: uso de arquitetura em camadas e padrão MVC facilita evolução e manutenção.  
- **Tempo Real**: análise e resposta rápidas a eventos críticos como pragas ou variações climáticas.

---

## Escolha de Tecnologias

### 🛠️ Camada de Infraestrutura (IoT e Redes)

**Tecnologias:**
- Sensores de umidade, temperatura, pH e nutrientes: `Decagon 5TE`, `Adafruit STEMMA Soil Sensor`.
- Sensores de imagem: `Raspberry Pi Camera`, `OpenMV Cam`.
- Comunicação sem fio: `LoRaWAN` (baixo consumo, longo alcance).
- Protocolo de comunicação: `MQTT` (leve, ideal para IoT).
- Gateways: `Raspberry Pi` ou `ESP32` para pré-processamento local.

**Justificativa:**  
Comunicação eficiente em ambientes rurais, com suporte a grandes distâncias e baixo consumo de energia. MQTT simplifica a troca de mensagens entre sensores e sistema central.

---

### 🛠️ Camada de Persistência (Banco de Dados)

**Tecnologias:**
- **MongoDB:** para armazenar dados não estruturados (sensores, imagens, logs).
- **PostgreSQL:** para armazenar dados relacionais (usuários, recomendações, histórico).
- **PostGIS:** para consultas geoespaciais.

**Justificativa:**  
Flexibilidade para dados heterogêneos, robustez e recursos geoespaciais fundamentais para sistemas agrícolas.

---

### 🛠️ Camada de Negócio (Model)

**Tecnologias:**
- Linguagem: `Python`
- Bibliotecas:  
  - `scikit-learn`: modelagem preditiva.  
  - `TensorFlow` ou `PyTorch`: visão computacional (detecção de pragas).  
  - `pandas` e `NumPy`: análise e manipulação de dados.
- Sistema de Regras: `Drools` ou lógica via backend.

**Justificativa:**  
Ecossistema rico em ferramentas de Data Science, ideal para análises preditivas e automação agrícola.

---

### 🛠️ Camada de Controle (Controller)

**Tecnologias:**
- Backend: `FastAPI` (Python) — rápido, assíncrono, documentação automática.
- Orquestração: `Celery` + `RabbitMQ` — tarefas assíncronas (ex.: coleta periódica, análises).
- Automação: integração via `Modbus` ou APIs de controladores de irrigação.

**Justificativa:**  
FastAPI oferece desempenho elevado para aplicações modernas. Celery possibilita execução de processos assíncronos de forma escalável.

---

### 🛠️ Camada de Apresentação (View)

**Tecnologias:**
- Frontend: `ReactJS`
- Visualizações: `D3.js` ou `Chart.js` para gráficos; `Leaflet` ou `Mapbox` para mapas.
- Mobile: `React Native` para app multiplataforma.

**Justificativa:**  
Ecossistema unificado, desenvolvimento ágil de interfaces ricas e responsivas, suporte a notificações push para alertas.

---

### 🛠️ Integração com Serviços Externos

**Tecnologias:**
- APIs meteorológicas: `OpenWeatherMap` ou `Meteostat`.
- Middleware: `Apache Kafka` (opcional) para processamento de dados em tempo real.

**Justificativa:**  
APIs são essenciais para previsões meteorológicas precisas. Kafka é indicado para sistemas com grande volume de dados.

---

### 🛠️ Segurança

**Tecnologias:**
- Autenticação: `OAuth 2.0` + `JWT`
- Criptografia: `TLS/SSL`
- Gerenciamento de Identidades: `Keycloak` ou `Auth0`

**Justificativa:**  
Garantia de segurança e privacidade, essencial para proteger dados sensíveis e garantir a integridade das operações.

---

### 🛠️ DevOps e Deployment

**Tecnologias:**
- Containerização: `Docker`
- Orquestração: `Kubernetes (K8s)` ou `Docker Swarm`
- CI/CD: `GitHub Actions` ou `GitLab CI`
- Monitoramento: `Prometheus` + `Grafana`
- Cloud Provider: `AWS`, `GCP` ou `Azure` (com suporte a IoT Core).

**Justificativa:**  
Facilita a escalabilidade, automação do deploy e observabilidade completa do sistema.

---

## ✅ Resumo: Tecnologias Alocadas por Camada

| Camada                         | Tecnologias                                                      |
| ------------------------------ | ---------------------------------------------------------------- |
| Infraestrutura                 | Sensores IoT, LoRaWAN, MQTT, Gateways ESP32/RPi                  |
| Persistência                   | MongoDB, PostgreSQL, PostGIS                                     |
| Negócio (Model)                | Python, scikit-learn, TensorFlow/PyTorch, pandas                 |
| Controle (Controller)          | FastAPI, Celery, RabbitMQ, Modbus                                |
| Apresentação (View)            | ReactJS, React Native, D3.js, Leaflet                            |
| Integração e Comunicação       | OpenWeatherMap, Kafka (opcional)                                 |
| Segurança                      | OAuth 2.0, JWT, TLS/SSL, Keycloak                                |
| DevOps e Deployment            | Docker, Kubernetes, GitHub Actions, Prometheus, AWS/GCP/Azure    |

---

