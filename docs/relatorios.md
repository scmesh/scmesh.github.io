# Relatórios pós-evento

Cada simulado, ocorrência real ou exercício comunitário gera um relatório curto e honesto do que funcionou e do que falhou. O objetivo é coletivo: aprender em vez de repetir o erro.

## 📋 Por que documentar

- **Memória institucional.** Voluntários entram e saem; o aprendizado fica.
- **Confiança.** Comunidade que admite falha publicamente é a que melhora.
- **Insumo técnico.** Padrões emergem ao longo dos relatórios — pontos cegos da malha, falhas de hardware recorrentes, erros de protocolo.
- **Prestação de contas.** Quando há vaquinha ou recurso público envolvido, o relatório fecha o ciclo.

## 🗂️ Relatórios publicados

*Ainda em construção. Os primeiros simulados e relatos vão entrar aqui.*

| Data | Tipo | Local | Resultado |
| :--- | :--- | :--- | :--- |
| — | — | — | Em construção |

## ✍️ Como escrever um relatório

Cada relatório vira um arquivo Markdown em `docs/relatorios/<ano-mes-dia>-<slug>.md`. Estrutura sugerida:

```markdown
# <Tipo>: <Título curto> — <Data>

## Contexto
1-2 parágrafos: o que aconteceu, quem participou, qual o objetivo.

## Cronologia
- HH:MM — Evento 1
- HH:MM — Evento 2
- ...

## O que funcionou
- Item 1 com explicação curta.
- Item 2.

## O que falhou
- Item 1 com explicação curta e impacto.
- Item 2.

## Métricas
| Indicador | Valor |
| :--- | ---: |
| Nós participantes | N |
| Mensagens trocadas | N |
| Tempo médio de chegada do [SOS] | N s |
| Cobertura efetiva | N km |
| ... | |

## Lições e ações
- [ ] Ação concreta 1 (responsável, prazo)
- [ ] Ação concreta 2

## Anexos
- Print da malha durante o evento
- Coordenadas dos pontos
- Mensagens-chave (sem dados pessoais)
```

## 🧪 Tipos de relatório

### Simulado de emergência

Trimestral. Cenário fictício orquestrado pela comunidade. Avalia:
- Adesão ao [formato padrão](emergencia.md#formato-padrao-de-mensagem).
- Tempo do `[SOS]` ao primeiro reconhecimento.
- Disciplina de canal.
- Autonomia dos nós solares.

### Field day / teste de alcance

Resultado do mapeamento sistemático da cobertura — vira insumo para [Infraestrutura](infraestrutura.md).

### Mutirão de instalação

Relato da subida de uma repetidora: BOM final, fotos, configuração aplicada, primeiros pacotes recebidos, lições.

### Ocorrência real

Quando a rede foi efetivamente usada em situação real (enchente, busca, evento). Mais cuidado com privacidade — anonimize pessoas envolvidas.

### Pós-mortem técnico

Quando algo quebrou: nó offline por semanas, antena caiu, firmware corrompeu, rede saturou. Foco em **causa raiz**, não em culpados.

## 🛡️ Cuidados de privacidade

Em relato de ocorrência real:

- **Anonimize pessoas resgatadas/auxiliadas.** Nome só com consentimento explícito.
- **Coordenadas precisas só de pontos públicos** (cruzamento, abrigo). Casas individuais arredondem.
- **Mensagens transcritas:** se contiverem dados pessoais, edite antes de publicar.
- **Fotos** com pessoas exigem consentimento.
- Se em dúvida, **não publique** o detalhe — peça revisão na comunidade.

## 🔁 Cadência

- **Após simulados:** publique em até 2 semanas.
- **Após mutirão:** em até 1 semana.
- **Após ocorrência real:** depende do calor do evento. 30 dias é razoável.
- **Pós-mortem técnico:** assim que diagnosticado o problema.

## 📈 Síntese anual

No início de cada ano, a comunidade pode publicar um sumário consolidando os relatórios do ano anterior:

- Total de eventos.
- Cobertura e crescimento da rede.
- Principais aprendizados.
- Ações concluídas / pendentes.
- Próximos focos.

Esse documento serve como prestação de contas pública e atrai novos contribuidores.

## 🤝 Quem pode escrever

Qualquer pessoa que participou do evento. Não precisa de aprovação prévia. Abra um PR; a comunidade revisa e sugere ajustes antes do merge. Veja [Contribuindo](contribuindo.md) para o fluxo.
