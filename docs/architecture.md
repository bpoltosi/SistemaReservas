# Arquitetura-alvo e fronteiras

## Visão geral

```text
Cliente / recepção / administração
              |
           apps/web
              |
      contrato HTTP/JSON
              |
           apps/api
       /       |        \
  sports   booking-core  payments
                |
           PostgreSQL
                |
        notifications/outbox
```

O diagrama é a arquitetura pretendida, não uma afirmação de que os módulos já estão implementados.

## Autoridade por responsabilidade

- **Booking core:** disponibilidade, bloqueios, criação/cancelamento/remarcação e prevenção de sobreposição.
- **Sports:** traduz conceitos do domínio esportivo para o modelo do motor: complexo, unidade, quadra/recurso, modalidade, duração, tarifa e manutenção.
- **Payments:** registra valor, método, estado, horário, operador e referência do pagamento. Na primeira versão, Pix e pagamentos presenciais podem ser lançados manualmente; não simular confirmação automática de Pix.
- **Notifications:** recebe eventos e tenta enviar mensagens; falhas de e-mail não devem apagar nem duplicar reservas.
- **Web:** interface pública e interna. Não deve ser fonte da verdade para disponibilidade ou preço final.
- **Infrastructure:** execução local reproduzível, banco e configuração.

## Contrato de integração inicial

Usar HTTP + JSON como protocolo comum entre aplicações, com datas ISO 8601 e fuso explícito. Cada adaptador deve documentar o mapeamento de IDs e estados. Não presumir que dois projetos usam os mesmos nomes de campos.

Endpoints conceituais a alinhar depois da inspeção dos códigos:
- `GET /api/complexes`
- `GET /api/resources?complexId=...`
- `GET /api/availability?resourceId=...&date=...`
- `POST /api/reservations`
- `PATCH /api/reservations/:id/cancel`
- `POST /api/reservations/:id/payments`
- `GET /api/admin/reservations`

Esses caminhos são propostas, não endpoints implementados.

## Regras de integridade

1. Bloquear reservas sobrepostas no backend/banco, inclusive em requisições simultâneas.
2. Isolar dados por complexo/tenant desde o modelo de dados e autorização.
3. Distinguir estado da reserva de estado do pagamento.
4. Armazenar horário com timezone e definir o fuso operacional do complexo.
5. Usar idempotência onde uma repetição de requisição possa duplicar uma operação.
6. Registrar auditoria para cancelamentos, alterações administrativas e lançamentos financeiros.

## Evolução da stack

A prioridade inicial é preservar código útil, não impor uma reescrita. A unificação em TypeScript/Node.js pode ser avaliada depois de os adaptadores e contratos estarem funcionando e os custos de migração forem conhecidos.
