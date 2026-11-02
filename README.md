# SistemaReservas — Plataforma de Reservas para Complexos Esportivos

Projeto de estudo e integração de componentes open source para construir um sistema de reservas de quadras e recursos esportivos, com suporte a um ou vários complexos.

## Estratégia de desenvolvimento

O projeto prioriza reaproveitar componentes existentes quando suas licenças permitirem, conectá-los por contratos e APIs explícitos e só depois unificar gradualmente a stack. A intenção é evitar reescrever tudo do zero.

## Estrutura

| Diretório | Responsabilidade |
|---|---|
| `apps/web/` | Site público de reservas e painel da equipe |
| `apps/api/` | API/fachada de integração e regras específicas do produto |
| `modules/sports/` | Quadras, modalidades, unidades, horários, tarifas e manutenção |
| `modules/payments/` | Registro de pagamentos Pix e presenciais, estornos e conciliação |
| `modules/notifications/` | Adaptadores de notificações |
| `infrastructure/` | Ambiente local, banco, Docker e configuração |
| `sources/` | Projetos externos importados e preservados com licenças |
| `docs/` | Arquitetura, roadmap, decisões e inventário das fontes |

## Princípio arquitetural

Deve existir uma única autoridade para disponibilidade e conflitos de reserva. Pagamentos registram a liquidação, mas não determinam a disponibilidade da quadra; notificações comunicam eventos, mas não alteram reservas por conta própria.

## Fontes candidatas

As referências e condições de uso são mantidas em [docs/source-register.md](docs/source-register.md). Antes de importar código, confira a licença, versão, dependências, configuração e origem. Preserve avisos de copyright e registre as alterações.

## Estado atual

A estrutura de destino, o mapa de integração e as instruções por módulo estão documentados. Os projetos externos ainda não devem ser considerados integrados apenas por estarem listados como fontes candidatas.

## Próximos passos

1. Validar licenças e comandos de teste das fontes.
2. Importar e executar uma fonte por vez.
3. Documentar o comportamento de cada componente isolado.
4. Definir contratos comuns de API/JSON.
5. Integrar o motor de reservas aos módulos esportivos.
6. Adicionar pagamentos e notificações por adaptadores.
7. Unificar tecnologias gradualmente, após validar as integrações.

Consulte [docs/roadmap.md](docs/roadmap.md) para a sequência detalhada.