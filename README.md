# Engenharia de Requisitos com GenAI — Sistema de Gestão de Eventos (Eventus)

Atividade prática da disciplina de Engenharia de Requisitos (Pós-graduação em IA). O objetivo foi analisar o documento de elicitação fornecido (sistema Eventus) e, com apoio de IA Generativa, identificar requisitos, regras de negócio, lacunas e ambiguidades, além de selecionar e produzir os artefatos de especificação mais adequados.

## Estrutura do repositório

```
engenharia-requisitos-genai/
├── analise/
│   ├── requisitos-funcionais.md
│   ├── requisitos-nao-funcionais.md
│   ├── regras-de-negocio.md
│   └── lacunas-e-ambiguidades.md
├── especificacao/
│   ├── historias-de-usuario.md
│   ├── casos-de-uso.md
│   ├── criterios-de-aceitacao.md
│   └── glossario.md
└── README.md
```

## 1. Artefatos de especificação escolhidos

- **Histórias de Usuário**
- **Casos de Uso**
- **Critérios de Aceitação (Given/When/Then)**
- **Glossário de Domínio**

## 2. Por que esses artefatos foram considerados os mais adequados

O sistema envolve **cinco perfis de stakeholders** com necessidades bem distintas (participante, organizador, equipe financeira, palestrante, equipe de TI), extraídas de falas diretas em entrevista — isso favorece **Histórias de Usuário**, que preservam a voz de cada stakeholder no formato "Como [persona], eu quero [ação], para que [benefício]".

Vários fluxos são condicionais e multi-ator (inscrição com pagamento, cancelamento com regras variáveis por evento, lista de espera, reembolso) — histórias de usuário sozinhas não detalham exceções e decisões suficientemente. Por isso foram elaborados **Casos de Uso**, que descrevem fluxo principal, fluxos alternativos e — de forma deliberada — marcam explicitamente onde falta uma regra de negócio definida, em vez de presumir um comportamento.

Os **Critérios de Aceitação** em Dado/Quando/Então complementam as histórias tornando cada comportamento verificável e testável, e também servem para sinalizar, cenário a cenário, o que ainda depende de validação com os stakeholders (marcado como `[A VALIDAR]`).

O **Glossário** foi incluído porque a elicitação usa "evento", "workshop" e "atividade" de forma parcialmente intercambiável — um risco real de ambiguidade entre times técnicos e de negócio. O glossário também formaliza os *status* de inscrição e pagamento, hoje implícitos nas falas dos stakeholders.

Optou-se por **não produzir** um documento de especificação estilo IEEE-SRS completo, diagramas BPMN ou protótipos de interface neste momento — justificativa na seção 5.

## 3. Ferramenta de GenAI utilizada

Foi utilizado o **Claude** (Anthropic), no ambiente Claude (Cowork).

## 4. Como a IA apoiou as diferentes etapas da atividade

1. **Estruturação do material bruto** — o texto das entrevistas foi organizado em Requisitos Funcionais, Requisitos Não Funcionais, Regras de Negócio e Lacunas/Ambiguidades, referenciando cada item à fala de origem.
2. **Recomendação de artefatos** — a partir do perfil do projeto (múltiplos atores, fluxos condicionais, terminologia ambígua), a IA sugeriu como opções histórias de usuário, casos de uso, critérios de aceitação e glossário, explicando o motivo de cada um antes de qualquer redação.
3. **Elaboração dos artefatos** — a IA redigiu as primeiras versões dos quatro artefatos escolhidos, sempre referenciando de volta o RF/RN de origem (rastreabilidade).
4. **Sinalização ativa de lacunas** — em cada ponto do material original marcado como "não definido" (seção 4 do documento de elicitação), a IA foi instruída a **não presumir uma resposta plausível**, e sim marcar o trecho como ponto em aberto (`[PONTO EM ABERTO]` nos casos de uso, `[A VALIDAR]` nos critérios de aceitação), citando a lacuna correspondente.

## 5. Sugestões aproveitadas, modificadas ou descartadas

| Sugestão da IA | Decisão | Justificativa |
|-----------------|---------|----------------|
| Separar o material bruto em RF, RNF, Regras de Negócio e Lacunas antes de qualquer redação de artefato | **Aproveitada** | Deu rastreabilidade clara: cada história/caso de uso remete à origem. |
| Combinação Histórias de Usuário + Casos de Uso + Critérios de Aceitação + Glossário | **Aproveitada** | Cobre tanto a voz do stakeholder quanto os fluxos condicionais complexos, sem exigir artefatos pesados demais para o nível de definição atual do projeto. |
| Preencher os Requisitos Não Funcionais com valores plausíveis (ex.: "tempo de resposta < 2s", "99,9% de disponibilidade") | **Descartada** | O próprio documento de elicitação afirma que nenhum RNF foi levantado. Assumir números criaria uma falsa sensação de requisito validado. Optou-se por documentar RNFs apenas como *candidatos a validar* (`requisitos-nao-funcionais.md`). |
| Definir automaticamente critérios de reembolso, prazo de cancelamento, mecânica de lista de espera e regra de emissão de certificado | **Descartada** | São lacunas explicitamente registradas pelos próprios entrevistadores (seção 4 do documento). Preencher essas lacunas com respostas "razoáveis" da IA correria o risco de a equipe de desenvolvimento tratar uma suposição como decisão validada. Optou-se por manter os pontos em aberto, sinalizados em todos os artefatos. |
| Gerar um documento de especificação único no padrão IEEE 830 (SRS) | **Descartada** | Com 9 lacunas e pelo menos 4 regras de negócio pendentes, um SRS completo passaria uma falsa impressão de que a especificação está fechada. Histórias de usuário e casos de uso comunicam o mesmo conteúdo com mais transparência sobre o que ainda está incompleto. |
| Criar diagramas BPMN dos fluxos | **Descartada** | Exigiria ferramenta gráfica especializada e um nível de definição de processo que o material ainda não sustenta; o diagrama Mermaid (ER) já cobre a necessidade de visão estrutural neste estágio. |
| Produzir protótipos de interface (wireframes) | **Descartada por ora** | Lacunas de alta prioridade (L-01, L-06, L-07, L-08) afetam diretamente telas de inscrição/cancelamento; prototipar antes dessas definições geraria retrabalho. Fica como próximo passo após validação com stakeholders. |
| Detalhar campos de dados pessoais visíveis ao palestrante (UC-06) | **Modificada** | A IA inicialmente sugeriu uma lista de campos (nome, e-mail, empresa). Optou-se por não fixar esses campos, tratando a definição como pendente de análise de privacidade/LGPD (L-08), já que a decisão envolve risco de exposição de dados pessoais. |
| Regra de conflito de horário (RN-05) redigida a partir das duas falas do organizador e do participante | **Modificada** | A IA inicialmente tratou as duas falas ("workshops simultâneos no mesmo horário" e "inscrever-se em vários workshops no mesmo dia") como a mesma regra. Na revisão, elas foram separadas: uma trata da grade de programação (trilhas paralelas), outra do impedimento de inscrição conflitante para o mesmo participante — registrado em `lacunas-e-ambiguidades.md` (A-02). |

## 6. Próximos passos sugeridos

Validar com os stakeholders as 9 lacunas listadas em `analise/lacunas-e-ambiguidades.md`, com prioridade para as que bloqueiam funcionalidades centrais (L-01 cancelamento, L-02 reembolso, L-06 reserva de vaga, L-07 conflito de horário) antes de avançar para protótipos de interface ou modelagem de dados detalhada.
