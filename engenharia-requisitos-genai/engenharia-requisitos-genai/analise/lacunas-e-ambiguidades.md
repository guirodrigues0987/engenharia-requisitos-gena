# Lacunas e Ambiguidades — Sistema Eventus

Itens identificados na seção 4 (Observações) do documento de elicitação, complementados por inconsistências terminológicas encontradas durante a análise.

## Lacunas explícitas (citadas no documento original)

| ID | Lacuna | Impacto |
|----|--------|---------|
| L-01 | Prazo limite para cancelamento de inscrição não definido. | Afeta RF-03 / RN-07. |
| L-02 | Critério de elegibilidade para reembolso não definido. | Afeta RF-14 / RN-06. |
| L-03 | Mecânica de funcionamento da lista de espera (ordem, promoção automática ou manual) não definida. | Afeta RF-08 / RN-04. |
| L-04 | Não definido se o certificado é emitido automaticamente ou depende de confirmação de presença. | Afeta RF-04 / RN-08. |
| L-05 | Canal de envio de comprovantes e notificações (e-mail, SMS, push) não definido. | Afeta RF-02. |
| L-06 | Momento de reserva da vaga (início do pagamento vs. confirmação) não definido. | Afeta RF-07 / RN-09. |
| L-07 | Tratamento de tentativa de inscrição em atividades com horário conflitante não definido (bloqueio automático? aviso?). | Afeta RF-05 / RN-05. |
| L-08 | Quais dados do participante podem ser visualizados pelo palestrante não foi definido. | Afeta RF-16 — risco de exposição indevida de dados pessoais. |
| L-09 | Nenhum requisito não funcional (segurança, desempenho, disponibilidade, acessibilidade, privacidade) foi levantado com os stakeholders. | Afeta todo o sistema — ver `requisitos-nao-funcionais.md`. |

## Ambiguidades identificadas durante a análise

| ID | Ambiguidade | Tratamento |
|----|-------------|------------|
| A-01 | Os termos "evento", "workshop" e "atividade" são usados de forma parcialmente intercambiável no documento (ex.: um "evento" pode conter vários "workshops"/"atividades" em paralelo). | Formalizado no `glossario.md`, com relação hierárquica evento → atividade. |
| A-02 | A fala do organizador "os workshops que acontecem no mesmo horário devem ocorrer simultaneamente" descreve grade de programação (trilhas paralelas), enquanto a fala do participante "inscrever-se em vários workshops no mesmo dia" trata de inscrição em múltiplas atividades — não necessariamente no mesmo horário. As duas falas não são contraditórias, mas foram inicialmente confundidas como se fossem a mesma regra. | Separadas em RN-05 (conflito de horário na inscrição) e observação de agenda (fora do escopo de requisito, é característica do modelo de dados de programação). |

**Encaminhamento:** todas as lacunas (L-01 a L-09) foram mantidas como pontos em aberto nos artefatos de especificação (histórias de usuário, casos de uso e critérios de aceitação), em vez de serem resolvidas com suposições. Essa foi uma decisão deliberada ao usar a IA — ver seção 5 do `README.md`.
