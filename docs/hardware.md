# Guia de Hardware

A escolha do hardware depende do seu objetivo na rede: você quer um dispositivo para levar na mochila, um nó fixo para sua casa ou um repetidor solar para o topo de um morro?

| Dispositivo | Prós | Contras | Uso Recomendado |
| :--- | :--- | :--- | :--- |
| **Heltec V3** | Barato, tela OLED integrada e muito popular. | Consumo de energia alto (ESP32). | Nós fixos ligados na tomada. |
| **RAK WisBlock** | Consumo baixíssimo, modular (nRF52840). | Preço mais elevado no kit completo. | **Repetidores Solares** (O padrão ouro). |
| **Lilygo T-Beam** | GPS integrado, suporte nativo para bateria 18650. | Grande, pesado e esquenta consideravelmente. | Uso móvel em veículos ou mochilas. |
| **Seeed XIAO S3 Mesh** | Ultra-compacto, processador potente e discreto. | Antena original limitada, requer montagem cuidadosa. | **EDC (Every Day Carry)** e dispositivos vestíveis. |
| **Seeed Wio Pro** | Construção industrial, alta confiabilidade e robusto. | Investimento inicial maior. | Estações base e infraestrutura crítica. |
| **Elecrow ThinkNode M5** | Design limpo, excelente para sensores e telemetria. | Menor disponibilidade no mercado nacional. | Monitoramento ambiental e agrofloresta. |

### Antenas
A antena que vem com o rádio geralmente é básica ("duck antenna"). Para expandir o alcance da sua estação no SC Mesh:

* **Urbano:** Antenas de **3dBi a 5dBi**. Antenas de menor ganho costumam ter um padrão de radiação mais "redondo", o que ajuda a refletir o sinal em prédios e obstáculos.
* **Rural/Morro:** Antenas Colineares de **8dBi a 12dBi**. Elas achatam o sinal no horizonte, ideal para cobrir longas distâncias onde há visada direta (Line of Sight).

Marcas recomendadas:  
**GIZONT** e **Ziisor**

### Cases e Energia
Para que a rede seja resiliente, precisamos de nós que aguentem as condições climáticas de Santa Catarina:

* **Proteção:** Para nós externos, use caixas herméticas com certificação **IP66** ou superior para proteger contra nossa alta umidade e chuvas.
* **Sistemas Solares:** Recomendamos painéis de pelo menos **5W a 10W** e baterias de boa qualidade (como LiFePO4 para maior durabilidade) para garantir que o nó não desligue após dois dias nublados.