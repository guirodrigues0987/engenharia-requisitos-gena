# Histórias de Usuário — Sistema Eventus

Formato: **Como** [persona], **eu quero** [ação], **para que** [benefício]. Cada história referencia o(s) Requisito(s) Funcional(is) de origem e, quando aplicável, a lacuna correspondente.

## Participante

**US-01** — Como participante, eu quero visualizar todos os eventos disponíveis em um único lugar, para que eu possa escolher em quais quero me inscrever sem consultar fontes espalhadas.
*(RF-01)*

**US-02** — Como participante, eu quero receber um comprovante logo após me inscrever, para que eu tenha a confirmação de que minha inscrição foi registrada.
*(RF-02 — canal de envio ainda não definido, ver L-05)*

**US-03** — Como participante, eu quero cancelar minha inscrição sem precisar contatar a organização, para que eu resolva isso de forma rápida quando não puder comparecer.
*(RF-03 — prazo limite de cancelamento não definido, ver L-01; nem todo evento permite cancelamento, ver RN-03)*

**US-04** — Como participante, eu quero emitir meu certificado depois do evento, para que eu tenha comprovação da minha participação.
*(RF-04 — condição de emissão automática ou por presença não definida, ver L-04)*

**US-05** — Como participante, eu quero me inscrever em vários workshops no mesmo dia, para que eu aproveite melhor minha ida ao evento.
*(RF-05 — o sistema deve impedir inscrição em atividades com horário conflitante, ver RN-05 e L-07)*

## Organizador

**US-06** — Como organizador, eu quero que o sistema controle automaticamente o número de vagas, para que eu não precise atualizar planilhas manualmente.
*(RF-07)*

**US-07** — Como organizador, eu quero que uma lista de espera seja criada quando um evento lotar, para que eu não perca participantes interessados quando surgirem vagas.
*(RF-08 — mecânica de promoção da lista de espera não definida, ver L-03)*

**US-08** — Como organizador, eu quero definir se um evento permite cancelamento de inscrição, para que eu tenha flexibilidade conforme a política de cada evento.
*(RF-09, RN-03)*

**US-09** — Como organizador, eu quero acompanhar a quantidade de inscritos em tempo real, para que eu tenha visibilidade operacional durante a divulgação do evento.
*(RF-10)*

**US-10** — Como organizador, eu quero gerenciar os participantes inscritos nos meus eventos, para que eu tenha controle sobre quem está confirmado.
*(RF-11)*

## Equipe Financeira

**US-11** — Como membro da equipe financeira, eu quero confirmar pagamentos de inscrições pagas, para que a vaga do participante seja liberada corretamente.
*(RF-12, RF-13, RN-02)*

**US-12** — Como membro da equipe financeira, eu quero processar reembolsos quando o participante tiver direito, para que o cancelamento seja resolvido financeiramente.
*(RF-14 — critério de elegibilidade ao reembolso não definido, ver L-02)*

## Palestrante

**US-13** — Como palestrante, eu quero consultar a programação das minhas atividades, para que eu me organize com antecedência.
*(RF-15)*

**US-14** — Como palestrante, eu quero consultar a lista de participantes inscritos nas minhas atividades, para que eu conheça meu público previamente.
*(RF-16 — quais dados exatamente são visíveis ao palestrante não foi definido; requer validação de privacidade, ver L-08)*

---

**Nota sobre requisitos não funcionais:** não foram redigidas histórias de usuário para segurança, desempenho, disponibilidade, acessibilidade e privacidade porque nenhum RNF foi validado com stakeholders (ver `analise/requisitos-nao-funcionais.md`). Transformar RNFs especulativos em histórias de usuário passaria a falsa impressão de que esses requisitos já foram acordados.
