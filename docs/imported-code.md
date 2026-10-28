# Importação de código upstream

Este repositório usa **Git submodules fixados em commits específicos** para disponibilizar os projetos originais sem misturar seus históricos, licenças, dependências e convenções com o código próprio. Os submodules são dependências de código-fonte; não significa que já estejam integrados nem que passem testes dentro deste produto.

## Baixar os códigos

Clone incluindo submodules:

```bash
git clone --recurse-submodules https://github.com/bpoltosi/SistemaReservas.git
cd SistemaReservas
```

Se o repositório já foi clonado:

```bash
git submodule update --init --recursive
```

Para conferir os commits exatos importados:

```bash
git submodule status
```

Não atualize os submodules automaticamente para `main`/ `master`: alterações de versão devem ser feitas em PR, com revisão de licença, dependências, configuração, testes e impacto na integração.

## Mapeamento por responsabilidade

| Fonte importada | Uso que vamos avaliar | Destino lógico no produto | Decisão atual |
|---|---|---|---|
| [Appointment Engine](https://github.com/aekiratli/appointment-engine) | API headless de agenda, disponibilidade e prevenção de conflitos | `apps/api` e domínio de reservas | **Candidato principal** a motor único; validar segurança multi-tenant, testes, modelo de recursos e concorrência antes de adotá-lo |
| [KortGo](https://github.com/kn8a/kortgo) | Fluxos e interface React para reservar quadras, perfis e check-in | `apps/web` | Referência/experimento isolado; o repositório não declara uma licença detectável no GitHub, portanto não copiar nem redistribuir arquivos até esclarecer a autorização |
| [Sport Booking API](https://github.com/kn8a/sport-booking-api) | Rotas e modelo de API do projeto que acompanha KortGo | `apps/api` | Referência/experimento isolado; sem licença detectável, não copiar nem redistribuir código até esclarecer a autorização |
| [LibreBooking](https://github.com/LibreBooking/librebooking) | Recursos, permissões, quotas, relatórios e padrões administrativos | `modules/sports` e futura administração | Referência de comportamento; licença GPL-3.0 exige análise de compatibilidade antes de incorporar ou distribuir código. Não operar como segundo motor de reservas |
| [ep-3 Bookingsystem](https://github.com/tkrebs/ep3-bs) | Calendário de quadras, horários, preços e regras de disponibilidade | `apps/web` e `modules/sports` | Referência para componentes/fluxos; MIT no repositório. Preservar licença e avisos se houver reutilização. Não operar como segundo motor |

## Regras de integração

1. **Uma única fonte de verdade para reservas:** só o motor escolhido decide disponibilidade, conflitos, cancelamentos e remarcações. Não executar Appointment Engine, LibreBooking e ep-3 em paralelo como motores ativos.
2. **Não misturar aplicações diretamente:** cada fonte continua isolada em `vendor/`. Primeiro execute e avalie cada projeto separadamente; depois crie adaptadores explícitos em `apps/api`.
3. **Não presumir compatibilidade:** tecnologias, versões de runtime, esquema de dados, autenticação, autorização e contratos HTTP devem ser auditados antes de conectar.
4. **Multi-tenant é requisito de segurança:** todas as leituras e gravações precisam provar isolamento entre complexos. Não confiar apenas em filtros do frontend.
5. **Pagamentos permanecem próprios no MVP:** registrar Pix confirmado manualmente e pagamentos presenciais em `modules/payments`; não adotar automaticamente carteira/saldo do KortGo.
6. **Preservar atribuição:** não remover LICENSE, NOTICE, cabeçalhos, créditos ou histórico do upstream. Registrar alterações locais e revisar dependências/licenças transitivas.
7. **Não versionar segredos nem dados reais:** usar arquivos de exemplo sem credenciais e dados fictícios.

## Próxima etapa técnica

Antes de mover qualquer código para `apps/web`, `apps/api` ou `modules/`:

- revisar os READMEs, arquivos de licença e dependências de cada fonte;
- executar testes e instalação em ambiente isolado;
- documentar riscos conhecidos e o que realmente funciona;
- escolher o motor de reservas único;
- importar somente os componentes necessários, preservando seus avisos legais;
- escrever testes de integração para sobreposição de reservas, fuso horário, cancelamento, concorrência e isolamento entre complexos.

**Estado deste PR:** os códigos originais estão referenciados por submodules em commits fixos. Nenhuma integração funcional entre os projetos é declarada; KortGo e sua API estão marcados como uso restrito até esclarecer licença.
