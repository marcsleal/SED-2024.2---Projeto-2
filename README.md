# Integrantes

- Alexandre Basílio da Silva Júnior - 119110494 
- Marcos Aurélio Pinheiro Leal      - 124110974 

# Vídeo de Demonstração
Para uma explicação detalhada do funcionamento do sistema e uma demonstração da simulação,
[Vídeo de Demonstração do Funcionamento](https://youtu.be/f8zDNdk1tXs)

# Modelagem de um sistema de manufatura com quatro células
## Descrição do Projeto

Este projeto tem o objetivo de desenvololver um sistema de manufatura contendo quantro células de manufatura onde cada uma possui um depósito de entrada, um depósito de saída, três máquinas e três robôs.

### Problema Resolvido

O problema central deste projeto é a coordenação de múltiplos robôs autônomos em um ambiente compartilhado, onde eles precisam acessar o Buffer de Entrada para retirar insumos e entregá-los às máquinas de processamentos:

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
