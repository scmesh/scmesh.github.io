# Vaquinhas e Financiamento

A SC Mesh é mantida por voluntários. Não temos sede, CNPJ, mensalidade nem patrocínio formal. Cada nó é pago e operado por alguém. Quando o local é estratégico mas o operador não tem como bancar sozinho, organizamos uma **vaquinha** — um financiamento coletivo aberto para custear o hardware.

## 🤝 Como funciona

Vaquinha não é caridade nem investimento — é um **rateio entre interessados** numa repetidora que beneficia todos os nós ao redor. Quem contribui tem voz no projeto e direito a transparência total.

### Princípios

1. **Necessidade comprovada.** A repetidora resolve um gap real (visada, cobertura, redundância) que está documentado em [Infraestrutura](infraestrutura.md).
2. **Operador definido** antes de abrir a vaquinha. Sem padrinho local, não levanta.
3. **BOM público** — lista de itens, fornecedor sugerido, custo, antes do PIX.
4. **Prestação de contas** — ao final, o operador publica nota fiscal/recibo, fotos da instalação e endereço/coordenada do nó na lista de [Pontos ativos](infraestrutura.md#pontos-ativos).
5. **Sem lucro.** O que sobrar volta para a próxima vaquinha ou compra de peça reserva, com aviso público.

## 💸 Vaquinhas em andamento

*Quando houver, aparecem aqui com link para a página específica de cada uma.*

| Projeto | Meta | Arrecadado | Status |
| :--- | ---: | ---: | :--- |
| *(nenhuma ativa)* | — | — | — |

## 📋 Como propor uma vaquinha

Se você tem acesso a um ponto alto e quer levantar uma repetidora comunitária:

1. **Valide o ponto** com a comunidade — é mesmo estratégico? Há visada para outros nós? Veja os [critérios](infraestrutura.md#criterios-para-um-bom-ponto-alto).
2. **Conseguir autorização formal** do proprietário (e-mail, contrato simples ou termo). Sem permissão escrita, não começa.
3. **Monte o BOM** — use o [Kit DIY de Repetidora Solar](hardware.md#kit-diy-repetidora-solar) como base; ajuste para o seu caso.
4. **Estime a meta** com 10–15 % de folga (frete, peça quebrada, ferragem).
5. **Apresente no [WhatsApp](https://chat.whatsapp.com/Hn19DdrY6460uGn0EkYwlQ)** — formato sugerido:
    - Local + foto da vista a partir do ponto.
    - Quem opera (você).
    - Quem cobre (cidades/bairros que vão ganhar sinal).
    - BOM com link e preço.
    - Meta R$ XXX, prazo Y semanas.
    - PIX (chave do operador, NÃO chave de terceiro).
6. **Atualize o grupo** semanalmente com valor arrecadado.
7. **Ao instalar**, publique fotos, vídeo do nó funcionando, primeiro pacote recebido por outro vizinho da rede.

## 🧾 Prestação de contas

Toda vaquinha encerrada deve ter uma página em `docs/financiamento/<cidade>-<ponto>.md` com:

- **BOM final** com nota fiscal/recibo de cada item.
- **Foto da instalação** (case montado, antena no mastro, painel solar, vista geral).
- **Coordenadas** do nó.
- **Configuração Meshtastic** aplicada (preset, role, hop limit).
- **Saldo final** — sobrou? para onde foi?
- **Contato do operador** atual.

Modelo de prestação:

```markdown
# Vaquinha — Morro da Tromba (Blumenau)

## Resumo
- Operador: Fulano da Silva (FSB1)
- Coordenadas: -26.91, -49.06
- Meta: R$ 1.500
- Arrecadado: R$ 1.620
- Custo final: R$ 1.587
- Saldo: R$ 33 → fundo de reserva da próxima vaquinha

## BOM
| Item | Fornecedor | Valor |
| ... |

## Fotos
![Vista do mastro](img/...)
...
```

## 🔍 Cuidados e transparência

- **Sempre PIX direto para o operador**, nunca chave de terceiro.
- **Comprovantes digitais** disponíveis a quem contribuir.
- **Sem reembolso garantido** se a instalação não der certo (ex.: dono retirou autorização). Nesse caso, hardware reverte para outro projeto da comunidade — combinado de antemão.
- **Sem participação obrigatória** — quem não puder contribuir financeiramente pode ajudar com mão de obra no dia da instalação.

## 🏛️ Por que não temos CNPJ?

CNPJ traria responsabilidades fiscais, contábeis e jurídicas que demandariam alguém dedicado. Por enquanto operamos como **iniciativa informal entre voluntários**, com vaquinhas pessoais e prestação de contas pública. Se a rede crescer ao ponto de exigir formalização, abriremos a discussão na comunidade.

## 🎁 Outras formas de apoiar

Se vaquinha não cabe no seu momento, você pode contribuir com:

- **Hardware doado** — rádios, baterias, painéis usados que você não usa mais.
- **Local físico** — disponibilizar um teto ou ponto alto para repetidora.
- **Mão de obra** — eletricista, soldador, instalador de antena, motorista.
- **Conhecimento** — palestras, oficinas, vídeos, traduções, ajuda neste site.
- **Divulgação** — falar do projeto em rádio comunitária, podcast, escola.
