# Critérios de Aceitação — Sistema Eventus

Formato Dado/Quando/Então (Given/When/Then), organizados por História de Usuário. Cenários que dependem de uma regra ainda não definida pelos stakeholders são marcados como **[A VALIDAR]** em vez de assumir um comportamento — assim os critérios não induzem a equipe a construir/testar algo que ninguém decidiu.

## US-01 — Visualizar eventos disponíveis
- **Dado** que existem eventos com inscrições abertas, **quando** o participante acessa o catálogo, **então** o sistema exibe todos os eventos disponíveis em uma única listagem.

## US-02 — Receber comprovante de inscrição
- **Dado** que o participante concluiu uma inscrição, **quando** a inscrição é confirmada, **então** o sistema emite um comprovante.
- **[A VALIDAR]** canal de envio do comprovante (e-mail, área logada, etc.) — depende de L-05.

## US-03 — Cancelar inscrição
- **Dado** um evento que permite cancelamento e uma inscrição dentro do prazo permitido, **quando** o participante solicita o cancelamento, **então** o sistema cancela a inscrição e libera a vaga.
- **Dado** um evento que não permite cancelamento, **quando** o participante tenta cancelar, **então** o sistema informa que essa inscrição não pode ser cancelada pelo próprio participante.
- **[A VALIDAR]** definição de "dentro do prazo permitido" — depende de L-01.

## US-04 — Emitir certificado
- **Dado** um evento já realizado, **quando** o participante solicita o certificado, **então** o sistema gera e disponibiliza o documento, respeitando a condição de emissão vigente.
- **[A VALIDAR]** se a condição de emissão exige confirmação de presença — depende de L-04.

## US-05 — Inscrever-se em múltiplas atividades no mesmo dia
- **Dado** que o participante seleciona duas atividades sem conflito de horário, **quando** ele confirma ambas as inscrições, **então** o sistema registra as duas normalmente.
- **Dado** que o participante seleciona duas atividades com o mesmo horário, **quando** ele tenta se inscrever na segunda, **então** o sistema impede a inscrição por conflito de horário.
- **[A VALIDAR]** se o sistema deve apenas bloquear ou também sugerir alternativas — depende de L-07.

## US-06 — Controle automático de vagas
- **Dado** um evento com vagas disponíveis, **quando** uma inscrição é confirmada, **então** o número de vagas disponíveis é decrementado automaticamente.
- **Dado** um evento sem vagas disponíveis, **quando** um novo participante tenta se inscrever, **então** o sistema o direciona para a lista de espera (UC-02).

## US-07 — Lista de espera
- **Dado** um evento lotado, **quando** um participante solicita entrar na lista de espera, **então** o sistema registra sua posição.
- **[A VALIDAR]** critério e forma de promoção da lista de espera quando surgir uma vaga — depende de L-03.

## US-09 — Acompanhar inscritos em tempo real
- **Dado** um evento com inscrições em andamento, **quando** o organizador acessa o painel do evento, **então** o sistema exibe a quantidade atual de inscritos.

## US-11 — Confirmar pagamento
- **Dado** uma inscrição pendente de pagamento, **quando** a equipe financeira confirma o pagamento, **então** o sistema libera a inscrição do participante.
- **Dado** uma inscrição pendente de pagamento não confirmada, **quando** o prazo definido para pagamento expira, **então** **[A VALIDAR]** — não há regra definida sobre expiração de inscrição não paga; comportamento não deve ser assumido.

## US-12 — Processar reembolso
- **Dado** uma inscrição paga e cancelada dentro dos critérios de elegibilidade, **quando** a equipe financeira avalia o caso, **então** o reembolso é processado.
- **[A VALIDAR]** os critérios objetivos de elegibilidade ao reembolso — depende de L-02.

## US-14 — Palestrante consulta participantes
- **Dado** uma atividade sob responsabilidade do palestrante, **quando** ele acessa a lista de inscritos, **então** o sistema exibe os participantes com o conjunto de dados aprovado para esse perfil.
- **[A VALIDAR]** quais campos de dados pessoais são exibidos — depende de L-08 e de definição de privacidade/LGPD.
