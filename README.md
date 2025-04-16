# Integrantes

- Alexandre Basílio da Silva Júnior - 119110494 
- Marcos Aurélio Pinheiro Leal      - 124110974 

# Vídeo de Demonstração
Para uma explicação detalhada do funcionamento do sistema e uma demonstração da simulação,
[Vídeo de Demonstração do Funcionamento](https://youtu.be/f8zDNdk1tXs)

# Descrição do Projeto

**Descrição do Projeto de Modelagem de Sistema de Manufatura com Redes de Petri Coloridas**  

Este projeto tem como objetivo modelar um sistema de manufatura composto por quatro células idênticas, utilizando Redes de Petri Coloridas (CPN) no CPN Tools. Cada célula opera de forma autônoma, mas integrada ao sistema maior, seguindo um fluxo de produção pré-definido que envolve depósitos, máquinas e robôs responsáveis pelo transporte de itens.  

Cada célula é composta por um depósito de entrada, um depósito de saída, três máquinas (M1, M2 e M3) e três robôs (R1, R2 e R3). As máquinas possuem seus próprios depósitos de entrada e saída, com capacidade máxima de quatro itens cada. Os robôs atuam de forma coordenada para transportar os itens entre os depósitos, seguindo duas rotas de produção distintas: Rota i e Rota j.  

O fluxo inicia quando os itens chegam ao depósito de entrada da célula. O Robô 1 (R1) é responsável por levar esses itens para o depósito de entrada da Máquina 1 (M1). Após o processamento em M1, o Robô 2 (R2) transporta os itens para os depósitos de entrada das Máquinas 2 (M2) ou 3 (M3), dependendo da rota escolhida (i ou j). Finalmente, o Robô 3 (R3) coleta os itens processados nos depósitos de saída de M2 ou M3 e os encaminha para o depósito de saída da célula, concluindo o ciclo.  

![image](https://github.com/user-attachments/assets/8ef2f181-0255-4942-b300-787930ecaf4c)

## Modelagem do sistema

### **Modelagem do Sistema**  

#### **1. Componentes do Sistema**  
O sistema consiste em:  
- **Buffer de Entrada**
- **Esteiras de Entrada/Saída**:  
  - `Entrada Esteira_0x` (recebe itens brutos)  
  - `Saida Esteira_0x` (envia itens processados)  
  - Onde x Representa (1,2 ou 3)
  - 
- **Máquinas**:  
  - `Maquina_01`, `Maquina_02`, `Maquina_03` (com depósitos internos de entrada/saída)
  - 
- **Robôs**:  
  - `Robo_01`: Transporta da `Entrada Esteira 01` para `Maquina_01`.  
  - `Robo_02`: Transporta da `Saida da Esteira 01  ` para `Maquina_02` ou `Maquina_03`.  
  - `Robo_03`: Transporta para `Saida Esteira 02` ou `Saida Esteira 03` para ***Buffer de Saida***.  


#### **2. Tokens de Controle**  
| **Token**  | **Local**               | **Função**                                  |  
|------------|-------------------------|--------------------------------------------|  
| **False**  | `Entrada_Esteira_0x`    | Contabiliza itens **entrando no sistema**. |  
| **True**   | `Saida_Esteira_0x`      | Contabiliza itens **saindo do sistema**.   |  

**Regras**:  
- Cada token `False` na entrada representa um item disponível para processamento.  
- Cada token `True` na saída confirma que um item foi concluído.  
- **Exemplo**:  
  - Se `Entrada_Esteira_01` tem `3 False` → 3 itens aguardando processamento.  
  - Se `Saida_Esteira_01` tem `2 True` → 2 itens finais produzidos.  


#### **4. Controle de Capacidade**  
- **Máximo de 4 itens** em qualquer esteira/depósito.  
- **Exemplo de Bloqueio**:  
  - Se `Saida_Esteira_01` tem `4 True` → Sistema para até liberar espaço.  



### Componetes das células

### Descrição dos Componentes de Cada Célula de Manufatura

Cada célula de manufatura descrita no documento possui os seguintes componentes:

1. **Depósitos:**
   - **Depósito de entrada da célula:** Local onde os itens são recebidos para serem processados na célula.
   - **Depósito de saída da célula:** Local onde os itens processados são armazenados após passarem por todas as etapas de produção.
   - **Depósito de entrada de cada máquina:** Cada uma das três máquinas possui um depósito de entrada onde os itens são colocados antes do processamento.
   - **Depósito de saída de cada máquina:** Cada máquina possui um depósito de saída onde os itens são armazenados após o processamento. Cada depósito de máquina tem capacidade máxima de 4 itens.

2. **Máquinas:**
   - **Máquina 1:** Processa itens recebidos do depósito de entrada da célula, transportados pelo Robô 1.
   - **Máquina 2:** Recebe itens do depósito de saída da Máquina 1, transportados pelo Robô 2, e os processa.
   - **Máquina 3:** Também recebe itens do depósito de saída da Máquina 1, transportados pelo Robô 2, e os processa. As Máquinas 2 e 3 operam em paralelo.

3. **Robôs:**
   - **Robô 1:** Responsável por transportar itens do depósito de entrada da célula para o depósito de entrada da Máquina 1.
   - **Robô 2:** Transporta itens do depósito de saída da Máquina 1 para os depósitos de entrada das Máquinas 2 e 3, seguindo as rotas de produção definidas (Rota i e Rota j).
   - **Robô 3:** Transporta itens dos depósitos de saída das Máquinas 2 e 3 para o depósito de saída da célula.

4. **Rotas de Produção:**
   - **Rota i e Rota j:** São as duas rotas de produção que definem o fluxo de itens entre as máquinas. O Robô 2 distribui os itens para as Máquinas 2 e 3 conforme essas rotas.


### Fluxo de Operação:
1. Os itens entram no **depósito de entrada da célula**.
2. O **Robô 1** transporta os itens para o **depósito de entrada da Máquina 1**.
3. A **Máquina 1** processa os itens e os envia para seu **depósito de saída**.
4. O **Robô 2** pega os itens do depósito de saída da Máquina 1 e os distribui para os **depósitos de entrada das Máquinas 2 e 3**, seguindo as rotas i e j.
5. As **Máquinas 2 e 3** processam os itens e os enviam para seus respectivos **depósitos de saída**.
6. O **Robô 3** coleta os itens dos depósitos de saída das Máquinas 2 e 3 e os transporta para o **depósito de saída da célula**, concluindo o ciclo.



![Foto01](https://github.com/user-attachments/assets/d2e40b22-6a9d-4179-9f64-0f14bd544974)

| Célula 1  | Célula 1 | 
|----------|----------|
| ![example](img/![Captura de tela 2025-04-16 052016](https://github.com/user-attachments/assets/5a3b589f-4334-4582-83f3-8150bff9360e)
![Captura de tela 2025-04-16 052051](https://github.com/user-attachments/assets/4c3d4e70-8fd3-4921-9020-b069b28f4c1b)
) | ![example](img/maquina_2.png) | 
