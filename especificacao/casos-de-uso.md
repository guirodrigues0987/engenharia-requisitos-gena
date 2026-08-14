# Casos de Uso — Sistema Eventus

Foram detalhados os fluxos que envolvem múltiplos atores, decisões condicionais e exceções — cenários em que as Histórias de Usuário, isoladamente, não são suficientes. Pontos que dependem de definição ainda não tomada pelos stakeholders são marcados como **[PONTO EM ABERTO]**, referenciando a lacuna correspondente, e **não foram preenchidos com suposições**.

---

## UC-01 — Inscrever-se em Evento/Atividade

**Ator principal:** Participante
**Atores secundários:** Equipe Financeira (eventos pagos)
**Pré-condição:** Participante autenticado; evento/atividade com inscrições abertas.
**Pós-condição (sucesso):** Inscrição registrada; comprovante emitido (RF-02).

**Fluxo principal:**
1. Participante seleciona um evento/atividade no catálogo (RF-01).
2. Sistema verifica disponibilidade de vagas (RN-04).
3. Sistema verifica se há conflito de horário com outra inscrição já confirmada do participante (RN-05).
4. Se o evento for gratuito, sistema confirma a inscrição imediatamente.
5. Se o evento for pago, sistema encaminha para o fluxo de pagamento (RN-02).
6. Sistema emite comprovante (RF-02).

**Fluxos alternativos:**
- **3a. Conflito de horário detectado:** sistema impede a inscrição. **[PONTO EM ABERTO — L-07]** o comportamento exato (bloqueio total, aviso com opção de prosseguir, sugestão de alternativa) não foi definido pelos stakeholders.
- **2a. Vagas esgotadas:** participante é direcionado ao UC-02 (Entrar em Lista de Espera).
- **5a. Momento de reserva da vaga:** **[PONTO EM ABERTO — L-06]** não está definido se a vaga é reservada no início do processo de pagamento ou somente após a confirmação. Enquanto essa regra não for validada, o sistema não deve presumir reserva automática antes da confirmação, para evitar overbooking.

---

## UC-02 — Entrar em Lista de Espera

**Ator principal:** Participante
**Pré-condição:** Evento/atividade com vagas esgotadas (RN-04).

**Fluxo principal:**
1. Sistema informa ao participante que não há vagas disponíveis.
2. Participante opta por entrar na lista de espera.
3. Sistema registra o participante na lista de espera do evento/atividade.

**[PONTO EM ABERTO — L-03]** A mecânica de promoção da lista de espera (ordem de chegada, promoção automática ao surgir vaga, prazo para o participante confirmar) não foi definida no material de elicitação. Este caso de uso propositalmente não descreve o passo de promoção, para não induzir a equipe de desenvolvimento a um comportamento não validado.

---

## UC-03 — Cancelar Inscrição

**Ator principal:** Participante
**Pré-condição:** Inscrição ativa; evento permite cancelamento (RN-03).

**Fluxo principal:**
1. Participante solicita cancelamento da própria inscrição, sem necessidade de contato com a organização.
2. Sistema verifica se o evento permite cancelamento (RN-03).
3. Sistema verifica se o cancelamento está dentro do prazo permitido. **[PONTO EM ABERTO — L-01]** não há definição de prazo.
4. Sistema efetiva o cancelamento e libera a vaga.
5. Sistema encaminha para avaliação de reembolso, se o evento for pago (ver UC-04).

**Fluxo alternativo:**
- **2a. Evento não permite cancelamento:** sistema informa ao participante que essa inscrição não pode ser cancelada por ele mesmo (RN-03).

---

## UC-04 — Processar Reembolso

**Ator principal:** Equipe Financeira
**Ator secundário:** Participante (originador via UC-03)
**Pré-condição:** Inscrição paga cancelada.

**Fluxo principal:**
1. Sistema encaminha o caso à equipe financeira após um cancelamento em evento pago.
2. Equipe financeira avalia elegibilidade ao reembolso.
3. Se elegível, equipe financeira processa o reembolso.

**[PONTO EM ABERTO — L-02]** O critério que define quando o participante tem direito a reembolso não foi levantado nas entrevistas ("em alguns casos o participante tem direito ao reembolso, em outros não"). Este caso de uso não presume um critério (ex.: prazo de X dias) — a decisão de elegibilidade permanece como avaliação manual da equipe financeira até que a regra seja validada com os stakeholders.

---

## UC-05 — Emitir Certificado

**Ator principal:** Participante
**Pré-condição:** Evento já realizado.

**Fluxo principal:**
1. Participante solicita emissão do certificado após o evento (RF-04).
2. Sistema verifica se as condições para emissão foram atendidas.
3. Sistema gera e disponibiliza o certificado ao participante.

**[PONTO EM ABERTO — L-04]** Não está definido se a emissão é automática para todo inscrito ou condicionada à confirmação de presença. O passo 2 deste caso de uso é intencionalmente genérico até essa definição.

---

## UC-06 — Consultar Participantes de uma Atividade

**Ator principal:** Palestrante
**Pré-condição:** Palestrante autenticado; atividade sob sua responsabilidade.

**Fluxo principal:**
1. Palestrante seleciona uma de suas atividades.
2. Sistema exibe a lista de participantes inscritos (RF-16).

**[PONTO EM ABERTO — L-08]** O conjunto de dados do participante exibido ao palestrante (nome apenas? e-mail? empresa?) não foi definido. Por envolver dados pessoais, essa definição deve considerar princípios de minimização de dados antes da implementação — recomenda-se tratar como requisito de privacidade a validar (ver `analise/requisitos-nao-funcionais.md`).

---

## Matriz de Rastreabilidade (Casos de Uso → Requisitos → Regras)

| Caso de Uso | Requisitos Funcionais | Regras de Negócio | Lacunas envolvidas |
|-------------|------------------------|--------------------|----------------------|
| UC-01 | RF-01, RF-02, RF-05, RF-07 | RN-02, RN-04, RN-05, RN-09 | L-06, L-07 |
| UC-02 | RF-08 | RN-04 | L-03 |
| UC-03 | RF-03 | RN-03, RN-07 | L-01 |
| UC-04 | RF-14 | RN-06 | L-02 |
| UC-05 | RF-04 | RN-08 | L-04 |
| UC-06 | RF-16 | — | L-08 |
