# Roadmap incremental

## Fase 0 — Estrutura e inventário (este PR)

- [x] Criar diretórios de destino e READMEs de orientação.
- [x] Registrar fontes, funções previstas e alertas de licença.
- [x] Definir fronteiras e contrato inicial.
- [ ] Inspecionar o código-fonte real de cada candidato.
- [ ] Confirmar licenças, versão/commit e comandos de teste.

## Fase 1 — Prova de execução isolada

- [ ] Importar primeiro o motor de reserva escolhido em `sources/`.
- [ ] Seguir as instruções do projeto original sem alterações funcionais.
- [ ] Documentar pré-requisitos e executar testes.
- [ ] Registrar problemas encontrados; não adaptar antes de ter uma baseline.

## Fase 2 — Adaptador esportivo

- [ ] Definir o mapeamento complexo/unidade/quadra/modalidade/recurso.
- [ ] Definir durações, intervalos, horários de abertura, manutenção e tarifas.
- [ ] Criar adaptador com DTOs próprios e tradução explícita de estados.
- [ ] Testar conflitos concorrentes, cancelamento e timezone.

## Fase 3 — Interface

- [ ] Selecionar e importar componentes úteis do KortGo/ep-3 apenas após verificar licenças.
- [ ] Manter separados site público, recepção e administração por rotas/permissões.
- [ ] Substituir chamadas internas pelo contrato comum, sem duplicar regras de reserva.

## Fase 4 — Financeiro e notificações

- [ ] Registrar pagamento Pix/manual e pagamento presencial como lançamentos separados da reserva.
- [ ] Registrar operador, método, valor, estado, horário e estorno.
- [ ] Criar eventos/outbox para confirmação, cancelamento e lembretes.
- [ ] Adicionar e-mail com configuração opcional e testes sem envio real.

## Fase 5 — Unificação gradual

- [ ] Medir duplicação, pontos de falha e custos de manutenção.
- [ ] Migrar uma peça por vez para a stack dominante escolhida.
- [ ] Manter testes de contrato para garantir equivalência.
- [ ] Remover uma implementação antiga só quando a substituta passar nos testes.

## Critérios mínimos para aceitar uma peça

- Licença compreendida e compatível com o uso pretendido.
- Setup reproduzível documentado.
- Testes existentes executados ou lacunas explicitadas.
- Nenhum segredo ou dado real incluído.
- Fronteira de integração definida.
- Nenhuma segunda fonte de verdade para reservas.
