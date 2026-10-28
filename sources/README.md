# sources — projetos originais preservados

Esta pasta guarda cópias dos projetos externos que serão conectados. Cada projeto deve ficar isolado no próprio subdiretório, com seu código e arquivos de licença preservados.

## Procedimento obrigatório para cada importação

1. Conferir `LICENSE`, avisos de copyright e eventuais `NOTICE`.
2. Escolher e registrar tag/commit exato em `docs/source-register.md`.
3. Copiar sem misturar arquivos de projetos diferentes.
4. Manter README original e adicionar um `INTEGRATION.md` explicando a finalidade local.
5. Rodar os testes/comandos do projeto original e salvar os resultados no registro.
6. Listar mudanças locais e não sobrescrever silenciosamente a origem.
7. Não importar `.env`, credenciais, uploads, banco de dados real ou dados pessoais.

## Layout esperado

- `appointment-engine/`: candidato a motor principal.
- `kortgo/`: referência de frontend esportivo.
- `kortgo-api/`: API associada, se for importada separadamente.
- `librebooking/`: referência de administração/API, caso a licença seja compatível.
- `ep3-bs/`: referência de calendário e seleção.

A estrutura ainda não contém os códigos externos. Não instalar todas as aplicações como um único sistema: primeiro validar cada uma separadamente e depois escolher o que realmente será integrado.
