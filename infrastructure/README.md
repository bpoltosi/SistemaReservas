# infrastructure — execução e serviços locais

## Objetivo

Reunir configuração reproduzível para desenvolver e testar no Windows com Docker Desktop, sem exigir infraestrutura paga para começar.

## Serviços candidatos

- PostgreSQL: banco relacional principal, caso confirmado pelo motor selecionado.
- Redis: somente se necessário para cache, filas ou rate limiting.
- Aplicações importadas: subir inicialmente seguindo os arquivos Docker/README originais, isoladas dos demais serviços.

## Regras

- Não criar um segundo banco por padrão sem necessidade comprovada.
- Nunca commitar `.env` real, tokens, senhas ou dumps com dados pessoais.
- Fornecer `.env.example` com valores fictícios e documentação dos nomes de variáveis.
- Fixar versões de imagens depois da prova de execução.
- Documentar portas, volumes, comandos de inicialização e limpeza de dados.

## Próximo passo

Depois de escolher e testar o motor, criar `docker-compose.yml` com os serviços mínimos reais. Evitar escrever uma configuração fictícia que pareça funcional antes de confirmar as dependências.
