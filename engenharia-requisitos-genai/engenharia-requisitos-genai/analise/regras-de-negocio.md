# Regras de Negócio — Sistema Eventus

Regras de negócio são fatos e políticas do domínio, distintos de comportamento de sistema (que fica registrado nos Requisitos Funcionais e detalhado nos Casos de Uso).

| ID | Regra de Negócio | Status |
|----|-------------------|--------|
| RN-01 | Um evento/atividade pode ser gratuito ou pago. | Definida |
| RN-02 | Inscrições em eventos pagos só são confirmadas após a confirmação do pagamento pela equipe financeira. | Definida |
| RN-03 | Nem todo evento permite cancelamento de inscrição; a permissão é definida por evento. | Definida |
| RN-04 | Quando as vagas de um evento/atividade se esgotam, novas inscrições entram em lista de espera. | Definida (mecânica de promoção pendente — L-03) |
| RN-05 | Um participante não pode se inscrever em duas atividades com horários conflitantes. | Definida (tratamento de tentativa de conflito pendente — L-07) |
| RN-06 | O direito a reembolso varia conforme o evento/situação; não é uma regra única para todo o sistema. | **Pendente de critério objetivo — L-02** |
| RN-07 | O prazo até o qual o participante pode cancelar a inscrição não é o mesmo para todos os eventos. | **Pendente de definição — L-01** |
| RN-08 | A emissão do certificado ocorre somente após a realização do evento. | Definida (condição de emissão — automática ou por confirmação de presença — pendente: L-04) |
| RN-09 | O momento em que a vaga é efetivamente reservada (início do pagamento vs. confirmação do pagamento) ainda não foi definido. | **Pendente — L-06** |

> Regras marcadas como "Pendente" foram **mantidas explicitamente em aberto** nos artefatos de especificação (não foram preenchidas com suposições da IA). Ver justificativa na seção 5 do `README.md`.
