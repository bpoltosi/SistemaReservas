# Fonte: Appointment Engine

Repositório original: https://github.com/aekiratli/appointment-engine

## Papel candidato

Motor de agendamento: disponibilidade, recursos, reservas, prevenção de sobreposição e eventos. É o candidato inicial a ser testado como fonte única da verdade para reservas.

## Importação

Ainda não copiado. Antes de copiar, conferir LICENSE/NOTICE, fixar o commit/tag e preservar o README original. Registrar os passos em `docs/source-register.md`.

## Testes obrigatórios após importar

- Instalação e inicialização limpa.
- Testes unitários e de integração fornecidos.
- Criação/cancelamento/remarcação de agendamento.
- Duas tentativas simultâneas para o mesmo recurso e horário.
- Isolamento entre tenants/complexos.
- Autenticação e autorização de operações administrativas.
- Timezone, repetição de requisição e falha de notificação/webhook.

## Adaptação esportiva posterior

Mapear recurso/serviço/agendamento para quadra/modalidade/reserva sem alterar o núcleo antes da baseline. Não presumir que o modelo atende a todos os requisitos até validar código e testes.
