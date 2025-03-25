# Tarefa Prática - aula 03 - 24/03/2025

## 1. Permitir que o usuário selecione a quantidade de produtos
  - **Disponibilidade:** Implementar um sistema de backup e replicação de servidores para garantir que a funcionalidade de seleção de produtos esteja disponível mesmo durante falhas de servidor.
  - **Testabilidade:** Criar testes unitários e de integração para verificar se a quantidade de produtos selecionada é corretamente registrada no sistema. Também devem ser feitos testes de interface para garantir que o comportamento do front-end seja adequado.
  - **Usabilidade:** Realizar testes de usabilidade com usuários reais para avaliar a facilidade de uso da interface de seleção de produtos.  
## 2. O usuário pode cancelar o pedido
  - **Disponibilidade:**  Implementação de um sistema de microsserviços onde o serviço de cancelamento é isolado para garantir que ele continue funcional mesmo que outras partes do sistema estejam com problemas.
  - **Testabilidade:** Criar cenários de teste que incluam diferentes estágios de processamento do pedido (durante a preparação e antes de sair para entrega) para garantir que o cancelamento seja possível em todos esses estágios.
  - **Usabilidade:** Fornecer uma explicação clara sobre as implicações do cancelamento (exemplo: política de reembolso).  
## 3. O usuário pode rastrear seu pedido durante a entrega
  - **Disponibilidade:** Garantir que o serviço de rastreamento seja altamente disponível, utilizando APIs de mapas e serviços de rastreamento que sejam escaláveis e com alta confiabilidade.
  - **Testabilidade:** Criar testes de integração para verificar se a localização do pedido é corretamente atualizada no mapa.
  - **Usabilidade:** A interface de rastreamento deve ser simples e intuitiva, com visualizações claras da localização do pedido e do progresso da entrega.
## 4. A empresa deve poder escolher entre entregadores particulares ou da plataforma
- **Disponibilidade:** Utilizar um sistema de fila para garantir que a escolha entre entregadores particulares ou da plataforma esteja sempre disponível, mesmo durante picos de demanda.
- **Testabilidade:** Desenvolver testes de integração entre o sistema de pedidos e o serviço de gerenciamento de entregadores, garantindo que a escolha do tipo de entregador seja corretamente refletida na execução do pedido.
- **Usabilidade:** Oferecer uma interface simples e clara para que a empresa selecione entre entregadores da plataforma ou particulares, com informações visuais claras sobre as opções.  
## 5. O usuário deve ser capaz de salvar métodos de pagamento
- **Disponibilidade:** Implementar técnicas de persistência como backup regular de dados de pagamento para evitar perda de informações em caso de falha
- **Testabilidade:** Criar testes de integração para garantir que os métodos de pagamento sejam corretamente salvos, recuperados e utilizados no processo de pagamento.
- **Usabilidade:** Oferecer ao usuário uma interface simples para gerenciar os métodos de pagamento, com visualização clara dos métodos salvos e possibilidade de adicionar, editar ou remover métodos.
