# apps/web — site e painel

## Responsabilidade

Interface para clientes reservarem quadras e para a equipe consultar e administrar reservas. Inicialmente pode abrigar as duas áreas no mesmo frontend, com rotas e permissões distintas.

## O que entra aqui

- Site público: escolher complexo/unidade, modalidade, quadra, data e horário.
- Fluxo de reserva e tela de confirmação.
- Área da recepção: consultar, criar, cancelar e registrar pagamentos conforme permissão.
- Área administrativa: recursos, horários, tarifas, bloqueios e relatórios.
- Componentes reutilizáveis de calendário e seleção, depois de licença e procedência conferidas.

## O que não entra

- Regra definitiva de conflito/ disponibilidade (pertence ao motor de reservas).
- Segredos de banco ou chaves de serviços no bundle do navegador.
- Lógica para marcar pagamento como confirmado sem evidência/ação autorizada.

## Integração

Consumir apenas a API documentada em `apps/api/`. Não acoplar telas diretamente ao banco nem depender de nomes de campos de um projeto externo sem adaptador.

## Estado

Diretório reservado; nenhum frontend foi importado ou executado neste PR.
