# Ferramentas e Recursos

Catálogo de software, hardware e links úteis que a comunidade SC Mesh usa no dia a dia.

## 🔗 Links oficiais

- [Site oficial Meshtastic](https://meshtastic.org/)
- [Firmware Meshtastic no GitHub](https://github.com/meshtastic/firmware)
- [Meshtastic Site Planner](https://site.meshtastic.org/)
- [Cálculo de visada — Scadacore](https://www.scadacore.com/tools/rf-path/rf-line-of-sight/)
- [Cálculo de visada — HeyWhatsThat](https://www.heywhatsthat.com/)

## 📱 Apps oficiais Meshtastic

| Plataforma | Link | Observação |
| :--- | :--- | :--- |
| Android | [Play Store](https://play.google.com/store/apps/details?id=com.geeksville.mesh) | O mais maduro. |
| iOS | [App Store](https://apps.apple.com/us/app/meshtastic/id1586432531) | Funciona bem, algumas configs avançadas só via CLI. |
| Web Client | [client.meshtastic.org](https://client.meshtastic.org/) | Conecta via serial USB no Chrome/Edge. |
| Desktop (CLI) | [meshtastic/python](https://github.com/meshtastic/python) | `pip install meshtastic`. |

### Meshtastic Python CLI

Indispensável para automação, exportar/importar configs, debug profundo:

```bash
pip install meshtastic
meshtastic --info                  # status geral
meshtastic --export-config > cfg.yaml
meshtastic --configure cfg.yaml    # aplica config YAML
meshtastic --listen                # imprime tráfego em tempo real
meshtastic --sendtext "Olá" --ch-index 0
```

Docs: [meshtastic.org/docs/software/python](https://meshtastic.org/docs/software/python/).

### Meshtastic Flasher

[flasher.meshtastic.org](https://flasher.meshtastic.org/) — flasheia firmware via Chrome/Edge (Web Serial API). Sem necessidade de instalar drivers manualmente na maioria dos casos.

## 🗺️ Mapas e monitoramento

| Ferramenta | Link | Observação |
| :--- | :--- | :--- |
| MeshMap | [meshmap.net](https://meshmap.net/) | Mapa global, depende de MQTT. |
| Plataforma Meshtastic Brasil | [platform.meshbrasil.com](https://platform.meshbrasil.com/) | Foco no Brasil, também depende de MQTT. |
| MeshSense | [affirmatech.com/meshsense](https://affirmatech.com/meshsense/) | App desktop para monitorar nós vizinhos com gráficos. |
| PotatoMesh | [potatomesh.net](https://potatomesh.net/) (referência) | Dashboard open-source de rede regional. |
| MeshMonitor | [meshmonitor.org](https://meshmonitor.org/) | Ferramenta para monitoramento e automação da sua rede mesh. |
| Mesh Mapper | [meshtastic.world](https://meshtastic.world/#) | Mapeamento e monitoramento da rede mesh. |
| AI Responder | [LN4CY/ai-responder](https://github.com/LN4CY/ai-responder) | Integração de IA à sua rede mesh. |

> Muitos nós da SC Mesh optam por **não** enviar a MQTT para preservar o caráter off-grid. Por isso, nem tudo aparece nesses mapas.

## 📐 Planejamento de RF e cobertura

Ver [Infraestrutura — Ferramentas para escolher o ponto alto](infraestrutura.md#ferramentas-para-escolher-o-ponto-alto) para o uso detalhado de cada ferramenta:

- [Google Earth Pro](https://www.google.com/earth/versions/)
- [HeyWhatsThat](https://www.heywhatsthat.com/)
- [Ubiquiti airLink](https://link.ui.com/)
- [Radio Mobile (VE2DBE)](https://www.ve2dbe.com/english1.html)
- [CloudRF](https://cloudrf.com/)
- [RadioPlanner 3.0](https://www.wireless-planning.com/radioplanner)
- [QGIS](https://qgis.org/) + dados SRTM/ALOS

## 🛠️ Hardware auxiliar

| Ferramenta | Para que serve | Faixa de preço |
| :--- | :--- | :--- |
| **NanoVNA V2** | Medir VSWR, impedância e perda de cabos/antenas | R$ 250–600 |
| **Multímetro** | Medir tensão e corrente em setup solar | R$ 40–200 |
| **USB Power Meter** (ex.: UM25C) | Medir consumo real do rádio | R$ 100–300 |
| **RTL-SDR** | Monitorar espectro, caçar interferência | R$ 150–400 |
| **Gerador de sinal / analisador** | Uso profissional em oficina | R$ 2.000+ |

## 🤖 Automação e integrações (referência)

Projetos criados pela comunidade Meshtastic global. Cite as integrações com cuidado — geralmente dependem de MQTT:

- **Meshtastic-MQTT-JSON** — ponte JSON para Home Assistant e similares.
- **meshtasticd** — daemon Linux para usar um Raspberry Pi como nó.
- **Meshtastic-matrix-relay** — ponte para Matrix.
- **Home Assistant** — sensores + botões ligados ao nó.
- **Grafana + InfluxDB** — dashboards de telemetria.

!!! warning "Pense antes de conectar à internet"
    Qualquer ponte entre Meshtastic e internet expõe metadados e, dependendo, conteúdo. Isole em canal privado, não em `LongFast`.

## 🔬 Ferramentas locais da SC Mesh

A comunidade tem desenvolvido utilitários próprios:

- **Gvatanto CLI** — ferramenta de linha de comando para automação, segurança e auditoria de nós Meshtastic e OSINT. *(em desenvolvimento, acompanhe o grupo)*.
- **Scripts de monitoramento** — alertas via Telegram quando um repetidor fica offline.

Contribuições bem-vindas — envie pela comunidade ou PR no [repositório](https://github.com/scmesh/scmesh.github.io).

## 📚 Literatura e referência rápida

- [Meshtastic Docs oficiais](https://meshtastic.org/docs/) — fonte primária.
- [Semtech LoRa Calculator](https://www.semtech.com/design-support/lora-calculator) — airtime e link budget.
- [Antennas for Meshtastic — relatórios comunitários](https://github.com/meshtastic/antenna-reports).
- [Meshtastic Discord e Discourse](https://meshtastic.org/docs/community/) — tirar dúvidas avançadas.
