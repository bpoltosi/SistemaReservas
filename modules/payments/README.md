# modules/payments — registro financeiro

## Objetivo inicial

Controlar o pagamento associado à reserva sem depender de um gateway. O sistema deve permitir registrar Pix (conferido manualmente), dinheiro ou cartão presencial e manter histórico de alterações.

## Dados mínimos de um lançamento

- Reserva e complexo relacionados.
- Valor e moeda.
- Método: Pix, dinheiro, cartão presencial ou outro configurado.
- Estado: pendente, pago, parcial, estornado ou cancelado.
- Data/hora, operador responsável e referência/comprovante opcional.
- Observação e histórico de auditoria.

## Limites de segurança

- Não guardar credenciais bancárias nem dados completos de cartão.
- Não tratar o envio de uma imagem/comprovante como confirmação automática de Pix.
- Exigir permissão explícita para marcar como pago, estornar ou corrigir um lançamento.
- Separar o estado financeiro do estado da reserva.
- Gateway online é uma integração futura e opcional.

## Integração

O módulo recebe o ID da reserva do contrato comum. Não altera disponibilidade; política de expiração de reserva pendente deverá ser decidida com o motor de reservas.

## Estado

Especificação inicial apenas; nenhum lançamento financeiro foi implementado neste PR.
