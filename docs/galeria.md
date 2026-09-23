# Galeria de Setups

Setups reais da comunidade SC Mesh — de gambiarra elegante a engenharia de morro. Serve para inspirar, comparar e mostrar que não tem fórmula única.

!!! tip "Quer aparecer aqui?"
    Mande foto do seu nó para a [comunidade no WhatsApp](https://chat.whatsapp.com/Hn19DdrY6460uGn0EkYwlQ) ou abra um [PR](contribuindo.md) com a imagem em `docs/img/galeria/` e a descrição abaixo. **Nunca poste fotos com o QR code de canal privado visível.**

## 📐 Padrão de submissão

Cada setup deve incluir:

- **Foto** (boa iluminação, foco no setup, não na pessoa).
- **Operador** (nome ou indicativo, sem dados pessoais).
- **Cidade/Bairro** (sem endereço completo).
- **Hardware:** rádio, antena, energia, case.
- **Role:** CLIENT, CLIENT_MUTE ou ROUTER.
- **Custo aproximado** (opcional).
- **O que aprendeu** ou faria diferente.

Modelo:

```markdown
### <Cidade> — <descrição curta>

**Operador:** Fulano (FSB1)
**Hardware:** RAK4631 + antena 8 dBi N-fêmea + case IP66 + painel 10 W + bateria LiFePO4 6 Ah.
**Role:** ROUTER
**Custo:** ~R$ 1.400
**Aprendizado:** O cabo coaxial estava longo demais (5 m) — mudei rádio para topo do mastro num case menor e SNR melhorou 4 dB.

![Vista do setup](img/galeria/cidade-fulano.jpg)
```

## 🏠 Setups domésticos

### Florianópolis - Mini node Frankenstein ("Frankenodinho")

* **Operador:** Carlos M.
* **Hardware:** Seeed Xiao ESP32S3+Wio SX1262, Antena 5dBi, sensor BMP280, bateria 18650.
* **Role:** CLIENT_BASE
* **Custo:** R$80 (node) + R$5 (placa fenolite ilhada) + R$??? (fiação e parafusos reusados)
* **Aprendizado:** O Xiao ESP32S3 tem um carregador de bateria integrado e ele é muito devagar; melhor usar um TP4056 no projeto. Melhor também usar um estojo pronto para a bateria.

Inspirado no [Franken-Mesh](https://github.com/atoughram/Franken-Mesh/) , construí esse projeto dimensionado para uma placa de fenolite perfurada de 10x15cm, para deixar ligado em casa. O Xiao ESP32S3 tem uma boa especificação no microcontrolador mas a potência do rádio deixa a desejar.

![Conjunto montado em placa perfurada](img/galeria/mini-frankenode/01.jpeg)

![Estojo do node](img/galeria/mini-frankenode/02.jpeg)

![Node montado no estojo](img/galeria/mini-frankenode/03.jpeg)

## 🏔️ Repetidoras em ponto alto

*Em construção. Seja o primeiro a contribuir.*

## ☀️ Sistemas solares

### Florianópolis - Sinalizador Náutico Solar

* **Operador:** Carlos M.
* **Hardware:** Seeed Xiao nRF52850+Wio SX1262, Antena 5dBi, sensor BH1750, circuito TP4056+bateria 18650 e painel solar.
* **Role:** CLIENT
* **Custo:** R$188 (dispositivo e sinalizador) + R$100 (outros materiais que eu já possuía)
* **Aprendizado:** Pelo dimensionamento (baixo) dos paineis, ele precisa ter no mínimo 4 horas de exposição solar direta diária para manter a bateria com o Xiao em modo de economia de energia. Visada é tudo para um node com baixa potência como esse.

Eu tinha visto o [projeto de um node no instructables](https://www.instructables.com/Meshtastic-Solar-Buoy/) reusando um sinalizador náutico. Ele vem vedado contra todos os elementos e é difícil de abrir, mas dentro traz três painéis solares ligados em série (5v) e uma bateria 18650 com terminais soldados. [Montei o meu](https://www.reddit.com/r/meshtastic/comments/1wjzb1v/so_i_made_that_solar_beacon_node/) fazendo uns ajustes no circuito de carregamento e usando um sensor de luminosidade, além de algumas impressões para fixação e vedação.

![Imagem com vista do setup](img/galeria/sinalizador-nautico/01.jpeg)

## 🥾 Setups portáteis

*Em construção. Seja o primeiro a contribuir.*

## 🛠️ Cases e soluções criativas

Aqui caem as soluções "fora da caixa" que outras pessoas podem copiar:

- **Antena improvisada** que funcionou.
- **Case 3D** com `.stl` aberto.
- **Suporte de mastro** caseiro.
- **Integração inusitada** (drone, balão, barco, mochila com painel solar embutido).

*Em construção.*

## ⚠️ O que evitar nas fotos

- **QR codes de canais privados** (mesmo de canto da imagem).
- **Endereços completos** ou placas de rua.
- **Documentos pessoais** ou identificação.
- **Crianças** sem consentimento dos responsáveis.
- **Senhas** visíveis em telas.
- Use editor de imagem para borrar essas partes antes de submeter.

## 📜 Licença das imagens

Ao submeter foto, você confirma que:

- É a autora ou tem permissão de uso.
- Aceita que a imagem seja publicada sob a mesma licença do site.
- Pessoas reconhecíveis na foto (se houver) consentiram em aparecer.

Para remover uma foto sua já publicada, abra issue ou avise no grupo.
