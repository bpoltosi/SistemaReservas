# apps/api — fachada e integração

## Responsabilidade

Camada de entrada para o domínio esportivo. Valida pedidos, autoriza operações, converte o contrato comum para a API do motor escolhido e coordena financeiro/notificações.

## Regras

- O motor de reservas escolhido é a única autoridade para disponibilidade e conflitos.
- A API não deve duplicar regras críticas de reserva em memória.
- Validar tenant/complexo e permissão em toda operação administrativa.
- Usar IDs externos apenas dentro do adaptador; expor IDs estáveis do contrato próprio.
- Registrar erros de integração sem incluir tokens ou dados sensíveis nos logs.

## Contrato proposto

Ver `docs/architecture.md`. Antes de implementar endpoints, confirmar o que o motor realmente oferece e documentar qualquer diferença.

## O que adicionar futuramente

- Adaptadores para booking core, esportes, pagamentos e notificações.
- Validação de DTOs e respostas de erro consistentes.
- Testes unitários e testes de contrato contra o motor.

## Estado

Ainda não há servidor/API implementado neste diretório.
