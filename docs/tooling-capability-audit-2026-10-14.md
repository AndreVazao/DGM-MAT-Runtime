# Avaliação de ferramentas externas para o runtime — 2026-10-14

Branch documental: `docs/tooling-capability-audit-2026-10-14`. Estado: avaliação proposta; não autoriza instalação nem execução em produção.

## Objetivo
Definir critérios para qualquer plugin, skill, agente, provider ou MCP que venha a executar dentro ou ao lado do runtime DGM-MAT.

## Princípios
- Não adicionar dependências pesadas sem benchmark no PC-alvo (2 núcleos, cerca de 3 GB RAM reportados).
- Preferir execução sob demanda, processos isolados e encerramento limpo.
- Declarar permissões, recursos, timeout, cancelamento, concorrência, dependências, custos e estratégia de falha.
- Não permitir instalação, escalada de privilégios, publicação ou alteração destrutiva sem aprovação explícita.
- Manter logs úteis, sem credenciais nem dados pessoais; auditar chamadas externas.
- Reutilizar componentes existentes antes de introduzir um novo orquestrador.

## Candidatos e decisão inicial
- Playwright: piloto de testes UI/browser, com escopo de sites autorizado.
- MCP Builder: avaliar servidores internos com ferramentas de leitura e diagnóstico primeiro.
- Superpowers / Skill Creator: candidatos para melhorar o processo de desenvolvimento, sem privilégios de runtime implícitos.
- Langflow, OpenHands, Open Dots, Habblaud, Maestro/Overclock: adiar até demonstrar vantagem sobre a orquestração existente.
- Scrapling: usar apenas em tarefas de extração autorizadas e após revisar dependências.
- Providers LLM gratuitos: verificar quota, rate limits, retenção, privacidade e custo após quota; nunca fazer fallback pago automaticamente.
- Ferramentas de vídeo/imagem: manter fora do runtime base; executar no pipeline de conteúdo ou serviço separado.

## Contrato mínimo de execução
Cada integração deve definir: identificador e versão; origem e licença; permissões; entradas/saídas; erros; timeout e cancelamento; limite de recursos; política de rede; tratamento de segredos; métricas/logs; plano de rollback e responsável.

## Gate de adoção
1. Identificar versão e fonte oficial.
2. Rever scripts, permissões e dependências.
3. Testar isoladamente sem credenciais de produção.
4. Medir CPU, RAM, tempo, falhas e qualidade.
5. Documentar evidência e decisão.
6. Só depois propor merge para a branch principal.

Nenhuma ferramenta foi instalada e nenhuma configuração de produção foi alterada nesta tarefa. Registo central: `AndreVazao/andreos-memory`, branch `docs/tooling-capability-audit-2026-10-14`.
