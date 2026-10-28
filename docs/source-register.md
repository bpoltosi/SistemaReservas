# Registro das fontes e plano de importação

Este arquivo registra procedência, papel pretendido e cuidados. Verificar novamente o conteúdo e a licença no commit/tag exato antes de importar; a informação abaixo não substitui a leitura dos arquivos de licença.

## 1. Appointment Engine

- Repositório: https://github.com/aekiratli/appointment-engine
- Papel candidato: núcleo de disponibilidade, recursos, agendamentos, proteção contra sobreposição e eventos/webhooks.
- Stack descrita: Next.js, PostgreSQL, Prisma e autenticação JWT/Supabase.
- Licença reportada: Apache-2.0.
- Destino após cópia: `sources/appointment-engine/`.
- Integração prevista: consumir/adaptar o motor por HTTP; mapear recurso/agendamento para quadra/reserva esportiva.
- Verificar: atividade/maturidade, testes, setup local, autenticação, isolamento multi-tenant, concorrência, migrações e se a licença/NOTICE acompanha a cópia.

## 2. KortGo

- Repositório: https://github.com/kn8a/kortgo
- API associada: https://github.com/kn8a/sport-booking-api
- Papel candidato: referência de experiência mobile-first, seleção de quadra, fluxo de reserva, papéis de usuário e check-in.
- Destino previsto: `sources/kortgo/`; API, se importada, em `sources/kortgo-api/`.
- Verificar: LICENSE em ambos os repositórios antes de copiar. Não assumir que são licenciados de forma permissiva.
- Cuidado: fluxo financeiro baseado em saldo/carteira não deve ser adotado automaticamente como modelo de pagamento.

## 3. LibreBooking

- Repositório: https://github.com/LibreBooking/librebooking
- Papel candidato: referência de painel administrativo, permissões, relatórios e API de reservas.
- Stack descrita: PHP e MySQL/MariaDB.
- Licença reportada: GPL-3.0.
- Destino previsto: `sources/librebooking/`.
- Verificar: licença e obrigações de distribuição, versão, configuração de API, modelo de autorização e autenticação.
- Decisão provisória: usar como referência/API isolada; não adicionar um segundo motor como fonte da verdade.

## 4. ep-3 Bookingsystem

- Repositório: https://github.com/tkrebs/ep3-bs
- Papel candidato: calendário visual, disponibilidade, horários de funcionamento e apresentação de preços.
- Stack descrita: PHP/Zend Framework e MySQL.
- Licença reportada: MIT para o código; nome e logo podem ter condições distintas.
- Destino previsto: `sources/ep3-bs/`.
- Verificar: arquivo LICENSE, dependências, compatibilidade e quais componentes são realmente reutilizáveis.

## Registro por importação

Para cada importação, preencher:
- URL do repositório de origem;
- commit SHA/tag exato;
- data de importação;
- licença e arquivos de copyright preservados;
- diretórios/arquivos copiados;
- alterações locais (patches);
- comandos executados e resultados;
- limitações conhecidas e dependências de segurança.
