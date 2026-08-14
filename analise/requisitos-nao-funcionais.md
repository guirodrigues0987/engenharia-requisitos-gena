# Requisitos Não Funcionais — Sistema Eventus

O documento de elicitação afirma explicitamente, na seção 4 (Observações):

> "Não foram levantados requisitos relacionados à segurança, desempenho, disponibilidade, acessibilidade e privacidade dos dados."

Ou seja, **nenhum requisito não funcional foi validado com os stakeholders**. Por isso, esta lista não apresenta RNFs definitivos — apenas **candidatos a validar**, inferidos das características do domínio (pagamentos, dados pessoais, controle de vagas em tempo real). Nenhum valor numérico (SLA, tempo de resposta, uptime) foi atribuído, pois isso exigiria decisão de negócio que não está no material original.

| ID | Categoria | Candidato a RNF (a validar com stakeholders) | Motivação |
|----|-----------|-----------------------------------------------|-----------|
| RNFc-01 | Segurança | Dados de pagamento devem ser tratados por gateway/processo seguro, sem armazenamento de dados sensíveis de cartão pelo próprio sistema. | Existe fluxo de pagamento e reembolso (RF-12 a RF-14). |
| RNFc-02 | Privacidade / LGPD | Dados pessoais de participantes (e-mail, CPF, etc.) devem ter acesso restrito por perfil, especialmente para o perfil Palestrante. | RF-16 expõe dados de participantes a um terceiro perfil; escopo não definido (L-08). |
| RNFc-03 | Desempenho | Contagem de vagas/inscritos (RF-07, RF-10) deve refletir concorrência de múltiplos usuários se inscrevendo simultaneamente, sem gerar overbooking. | Controle automático de vagas em tempo real citado pelo organizador. |
| RNFc-04 | Disponibilidade | Sistema deve estar disponível durante períodos de abertura de inscrições, quando o volume de acesso tende a ser maior. | Substituição de planilhas/formulários manuais sugere pico de uso concentrado. |
| RNFc-05 | Acessibilidade | Interface de inscrição deve seguir diretrizes básicas de acessibilidade (WCAG), já que o público de participantes é amplo e não técnico. | Público-alvo é externo (participantes de congressos/workshops). |

**Decisão de tratamento:** optou-se por **registrar formalmente a lacuna de RNF** (ver `lacunas-e-ambiguidades.md`, L-09) em vez de assumir valores. Os RNFs acima são marcados como *candidatos*, não requisitos aprovados.
