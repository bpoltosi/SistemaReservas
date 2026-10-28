# modules/sports — domínio esportivo

## Responsabilidade

Modelar as diferenças entre agendamento genérico e reserva de quadras esportivas.

## Entidades previstas

- **Complexo:** organização/tenant que possui uma ou mais unidades.
- **Unidade:** local físico, endereço, timezone e regras de funcionamento.
- **Recurso/quadra:** recurso reservável, modalidade compatível, capacidade e estado.
- **Modalidade:** futebol, tênis, padel, vôlei etc.
- **Tarifa:** preço por período, faixa de horário, dia da semana ou modalidade.
- **Bloqueio:** manutenção, evento, indisponibilidade ou reserva administrativa.
- **Reserva:** referência ao motor, participantes, observações e estado de negócio.

## Regras a esclarecer antes do código

- Duração fixa ou múltiplas durações?
- Intervalo para limpeza/preparação entre reservas?
- Reserva recorrente? Lista de espera?
- Cancelamento, tolerância, atraso e no-show?
- Preços diferentes por horário, cliente ou tipo de quadra?
- Várias quadras podem ser reservadas em conjunto?
- Uma conta de usuário pode operar em vários complexos?

## Integração

O módulo traduz IDs e conceitos para o motor de reservas. Não deve criar uma segunda tabela/serviço que concorra com o motor como fonte oficial de horários reservados.
