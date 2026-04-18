# Infraestrutura e Deployments

### Guia de Repetidores Solares
Um repetidor solar eficiente em Santa Catarina precisa considerar nossa alta umidade e a frequência de dias nublados. 

* **Componentes Recomendados:** Painel Solar (10W+) -> Controlador de Carga (MPPT preferencialmente) -> Bateria LiFePO4 -> RAK4631 (devido ao baixo consumo do nRF52840).
* **Dica de Ouro:** Sempre instale o rádio o mais próximo possível da antena. Em frequências de 915MHz, cada metro de cabo coaxial comum resulta em uma perda significativa de sinal. Use cabos de baixa perda (como LMR-240 ou superior) se a distância for inevitável.

---

### Classificação de Nós
A escolha correta do papel (*role*) do seu nó é fundamental para o desempenho de toda a malha catarinense.

* **CLIENT:** É o modo padrão. Use para o seu rádio pessoal, celular ou nó móvel. Ele participa da rede, repete mensagens, mas prioriza o próprio tráfego.
* **CLIENT_BASE:** Use para nós fixos em casa ou no escritório que não estão em pontos extremamente altos. Ele se comporta como um cliente, mas prioriza o tráfego de mensagens para nós favoritos.
* **CLIENT_MUTE:** Use para enviar e receber mensagens normalmente, porém ele não vai repetir mensagens recebidas. Útil para economizar bateria ou reduzir o tráfego em áreas já saturadas.
* **ROUTER:** Destinado a nós em locais de altíssima visada e pontos estratégicos.

!!! warning "Observação Importante"
    Antes de configurar seu nó como **ROUTER**, consulte a comunidade. Um nó do tipo Router instalado em um local inadequado ou com configuração errada pode causar colisões de pacotes e degradar a performance de toda a rede regional em vez de ajudar.

---

### Locais Estratégicos
A rede SC Mesh já conta com infraestrutura dedicada nos seguintes pontos:

* **Morro dos Muller - Antônio Carlos:** Cobertura estratégica para a região metropolitana e áreas rurais adjacentes.

### Tem um ótimo local para uma repetidora?
Se você tem acesso a um topo de morro, prédio alto ou torre com boa visada, entre em contato com a comunidade! Nós ajudamos a avaliar a viabilidade técnica, o impacto na rede e os melhores equipamentos para o local.