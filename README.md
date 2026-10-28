# SistemaReservas — complexo esportivo

Projeto de estudo e integração de componentes open source para gerenciar reservas de quadras e outros recursos esportivos em um ou vários complexos.

**Estratégia:** reaproveitar código existente de forma literal quando a licença permitir; conectar as peças por APIs/contratos explícitos; só depois refatorar gradualmente para uma stack dominante. Não vamos reescrever tudo desde o início.

## Estado atual

Este PR estabelece a estrutura de destino, o mapa de integração e instruções por módulo. Os projetos externos ainda não foram copiados para este repositório: cada cópia deverá ser feita após conferir versão, licença, dependências, configuração e origem dos arquivos.

## Mapa rápido

| Caminho | Responsabilidade |
|---|---|
| `sources/` | Cópias preservadas dos projetos de referência, com suas licenças e alterações rastreadas |
| `apps/web/` | Site público de reservas e painel da equipe |
| `apps/api/` | Fachada/API de integração e regras específicas de complexo esportivo |
| `modules/sports/` | Quadras, modalidades, unidades, horários, tarifas, manutenção e regras esportivas |
| `modules/payments/` | Registro de Pix, dinheiro/cartão presencial, estornos e conciliação manual |
| `modules/notifications/` | Adaptadores de e-mail e futuros canais de notificação |
| `infrastructure/` | Docker Compose, banco, variáveis de ambiente e execução local |
| `docs/` | Arquitetura, inventário das fontes, decisões e plano de integração |

## Fontes candidatas

- [Appointment Engine](https://github.com/aekiratli/appointment-engine) — candidato para o núcleo de disponibilidade/agendamento; licença Apache-2.0 informada no repositório. Validar maturidade e modelo antes de adotá-lo.
- [KortGo](https://github.com/kn8a/kortgo) — referência de UX e fluxo de reserva esportiva; conferir a licença do frontend e da API antes de copiar.
- [LibreBooking](https://github.com/LibreBooking/librebooking) — referência/API de administração e reservas; GPL-3.0, avaliar obrigações antes de incorporar código.
- [ep-3 Bookingsystem](https://github.com/tkrebs/ep3-bs) — referência de calendário e seleção de quadras; MIT para o código do sistema, mas nome/logo têm condições próprias.

Leia [o registro de fontes](docs/source-register.md) antes de importar qualquer arquivo.

## Regra central de integração

Deve existir **uma única autoridade para disponibilidade e conflito de reservas**. Não manter dois motores de reserva ativos em paralelo. O financeiro registra pagamentos, mas não decide se uma quadra está livre; notificações comunicam eventos, mas não alteram a reserva por conta própria.

## Primeiro ciclo de trabalho

1. Confirmar licenças, estrutura real e comandos de teste de cada fonte.
2. Importar uma fonte por vez para `sources/<nome>/`, preservando origem e licença.
3. Executar e documentar cada fonte isoladamente antes de conectá-la.
4. Definir um contrato comum de API/JSON e adaptar as diferenças.
5. Ligar a camada esportiva ao motor de reservas.
6. Acrescentar registro de pagamento e notificações sem acoplar esses módulos ao motor.
7. Só depois começar a unificação gradual de linguagem/framework.

## Cuidados

- Não commitar segredos, tokens, arquivos `.env` reais, dados pessoais ou dados de clientes.
- Não remover avisos de copyright/licença das cópias.
- Registrar cada alteração feita em código importado.
- Nunca afirmar que uma integração está funcional sem testes reproduzíveis.
- Para detalhes e tarefas, consulte `docs/roadmap.md`.
