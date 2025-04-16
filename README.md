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


## Modelagem do sistema

O fluxo mostra que os itens são roteados para diferentes células, processados e depois enviados para um buffer de saída. As células são etapas paralelas dentro da fábrica, ou seja, o processo pode acontecer simultaneamente em várias células, dependendo da lógica de roteamento.

![image](https://github.com/user-attachments/assets/8ef2f181-0255-4942-b300-787930ecaf4c)

### Componetes das células

```
As 4 células possuem a mesma composição e funcionamento, sendo os seus componetes:

Robô 1: Transporta os itens do depósito da célula para a máquina 1.
Robô 2: Transporta os itens da máquina 1 para a máquinha 2 e para a máquina 3.
Robô 3: Transporta os itens da máquina 2 e máquina 3 para o depósito de sáida da célula.

Máquina 1: Processa os itens do tipo i e tipo j.
Máquina 2: Processa os itens do tipo i.
Máquina 3: Processa os itens do tipo j.

Sendo possivel os depósitos de cada máquina armazenarem no máximo 4 itens.
```

| Célula 1  | Célula 1 | 
|----------|----------|
| ![example](img/![Captura de tela 2025-04-16 052016](https://github.com/user-attachments/assets/5a3b589f-4334-4582-83f3-8150bff9360e)
![Captura de tela 2025-04-16 052051](https://github.com/user-attachments/assets/4c3d4e70-8fd3-4921-9020-b069b28f4c1b)
) | ![example](img/maquina_2.png) | 
