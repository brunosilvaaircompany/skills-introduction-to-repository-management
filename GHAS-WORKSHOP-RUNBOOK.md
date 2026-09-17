# Secure Repository Operations with GitHub Advanced Security

Runbook minuto a minuto para adaptar `/home/runner/work/skills-introduction-to-repository-management/skills-introduction-to-repository-management` a um workshop demonstrativo de 90 minutos sobre GitHub Advanced Security.

## 1. Objetivo do instrutor

- Concluir a demonstração em 90 minutos sem depender de configuração administrativa improvisada e sem inserir credenciais reais ou dados confidenciais.

## 2. Objetivos de aprendizagem

Ao final do workshop, o participante deve conseguir:

1. Diferenciar **GitHub Code Security**, **GitHub Secret Protection** e o termo **GHAS**, que ainda aparece em documentação, licenciamento e ambientes específicos.
2. Explicar onde **Code Scanning**, **Secret Scanning**, **Push Protection**, **Dependabot** e **Dependency Review** entram no ciclo de desenvolvimento.
3. Interpretar um alerta sem tratá-lo como prova automática de exploração.
4. Diferenciar um problema encontrado por scanner de um problema que exige revisão arquitetural.
5. Explicar por que remover um segredo do arquivo não substitui revogação, rotação, atualização dos serviços afetados e revisão de acessos.
6. Distinguir **dependency graph**, **Dependabot alerts**, **security updates**, **version updates** e **dependency review**.
7. Priorizar um alerta por impacto, exposição, exploitabilidade, criticidade e confiança.
8. Explicar como o Copilot pode apoiar a investigação sem substituir revisão humana, testes e validação.

## 3. Objetivo pedagógico central

Ferramentas ajudam a detectar e prevenir riscos, mas segurança efetiva depende de contexto, priorização, correção, validação, governança e revisão humana.

## 4. Superfícies do repositório a usar na demonstração

- Aplicação FastAPI e ponto de entrada: `/home/runner/work/skills-introduction-to-repository-management/skills-introduction-to-repository-management/src/app.py`
- Backend de autenticação e atividades:
  - `/home/runner/work/skills-introduction-to-repository-management/skills-introduction-to-repository-management/src/backend/routers/auth.py`
  - `/home/runner/work/skills-introduction-to-repository-management/skills-introduction-to-repository-management/src/backend/routers/activities.py`
- Base sintética e seed data:
  - `/home/runner/work/skills-introduction-to-repository-management/skills-introduction-to-repository-management/src/backend/database.py`
- Frontend estático:
  - `/home/runner/work/skills-introduction-to-repository-management/skills-introduction-to-repository-management/src/static/app.js`
  - `/home/runner/work/skills-introduction-to-repository-management/skills-introduction-to-repository-management/src/static/index.html`
- Dependências:
  - `/home/runner/work/skills-introduction-to-repository-management/skills-introduction-to-repository-management/requirements.txt`
- Estrutura do exercício e narrativa atual:
  - `/home/runner/work/skills-introduction-to-repository-management/skills-introduction-to-repository-management/.github/steps`
  - `/home/runner/work/skills-introduction-to-repository-management/skills-introduction-to-repository-management/.github/workflows`

## 5. Controles principais do workshop

- **Proteção da branch principal**: controle de merge
- **CODEOWNERS**: mecanismo principal de ownership
- **SECURITY.md**: canal principal de reporte

Material complementar:

- rulesets avançados
- private vulnerability reporting
- issue templates
- CONTRIBUTING
- security configurations em escala

## 6. Avisos obrigatórios de dados e segurança

- Os nomes, usernames e emails do repositório são sintéticos.
- Não usar emails de participantes.
- Não inserir dados reais de alunos, clientes, funcionários ou terceiros.
- Não usar credenciais reais.
- Não usar dados confidenciais.
- Em incidente real, remover o segredo do arquivo não basta; a credencial deve ser revogada ou rotacionada, os serviços afetados devem ser atualizados e os acessos devem ser revisados.

## 7. Checklist de “não demonstrar”

- Não inserir token real.
- Não usar chave privada real.
- Não testar credencial de produção.
- Não expor dados pessoais.
- Não fazer bypass com justificativa falsa.
- Não executar limpeza destrutiva de histórico durante a transmissão.
- Não apresentar ausência de alerta como prova de segurança.
- Não aplicar sugestão do Copilot sem revisão e testes.

## 8. Preparação obrigatória antes da transmissão

### Ambiente

- Validar acesso à organização de demonstração.
- Confirmar plano/licenciamento compatível com os recursos demonstrados.
- Confirmar permissões administrativas.
- Confirmar a conta ou licença do Copilot usada na demonstração.
- Confirmar GitHub Actions habilitado.
- Confirmar links diretos para páginas da demo.
- Registrar screenshots dos estados antes e depois.

### Repositório

- Manter `main` protegida.
- Confirmar uso de **CODEOWNERS** como mecanismo principal de ownership.
- Preparar branch-base de restauração ou tag de reset.
- Testar o reset completo uma vez.
- Preparar branch ou PR com alerta de CodeQL já validado.
- Preparar branch efêmera para segredo fictício.
- Confirmar se padrões customizados de segredo estão disponíveis no ambiente e se exigem GitHub Secret Protection.
- Confirmar que Push Protection está ativo no cenário de demonstração.
- Validar PR de dependência e o comportamento esperado do Dependency Review.
- Confirmar que nenhum dado real ou segredo real está presente.
- Manter artefatos de fallback disponíveis localmente ou remotamente.

### Ensaio

- Executar um ensaio completo cronometrado em 90 minutos.
- Validar CodeQL e Dependabot próximo à data do workshop.
- Se a demonstração principal não funcionar em 60–90 segundos, migrar imediatamente para o fallback.
- Nunca sacrificar os dois minutos finais de encerramento.

## 9. Quadro de referência rápida para dependências

- **Dependency graph**: inventário das dependências
- **Dependabot alerts**: vulnerabilidades conhecidas nas dependências existentes
- **Security updates**: atualização automática para corrigir vulnerabilidades
- **Version updates**: atualização contínua para manter versões atuais
- **Dependency review**: avaliação do impacto de mudanças de dependência em uma pull request

## 10. Matriz simples de priorização

| Fator | Pergunta |
| --- | --- |
| Impacto | O que pode acontecer se o problema for explorado? |
| Exposição | O ativo é público, interno ou restrito? |
| Exploitabilidade | Existe caminho plausível até o problema? |
| Criticidade | O componente suporta dados ou operações importantes? |
| Confiança | O achado foi validado ou pode ser falso positivo? |
| Correção | Existe correção segura e testável? |
| Prazo | Há SLA, obrigação regulatória ou janela operacional? |

## 11. Estrutura padrão para cada demonstração

Cada demo deve registrar:

1. Objetivo
2. Pré-requisitos
3. Tela/ação do instrutor
4. Resultado esperado da ferramenta
5. Interpretação esperada
6. Mensagem que o público deve levar
7. Critério de sucesso
8. Critério de encerramento
9. Fallback
10. Reset

## 12. Critérios de encerramento por tipo de alerta

- **Code Scanning**: encerrado quando a análise posterior não encontra mais o problema, ou quando o alerta é fechado com justificativa adequada.
- **Secret Scanning**: encerrado quando a credencial fictícia foi tratada conforme o cenário; em caso real, com revogação ou rotação, atualização dos serviços afetados e revisão de acesso.
- **Dependabot / risco de dependência**: encerrado quando a dependência foi atualizada, os testes passam e a PR foi revisada e integrada.
- **Falso positivo ou adiamento**: encerrado apenas com análise registrada e justificativa documentada.

Observação: nomes de botões, estados e fluxos podem variar por produto, permissão, plano e plataforma.

## 13. Agenda minuto a minuto

| Tempo | Bloco | Limite operacional |
| ---: | --- | --- |
| 0–8 min | Contexto e arquitetura | Mostrar poucos arquivos e preparar a narrativa |
| 8–15 min | Produtos, planos, permissões e pré-requisitos | Usar quadro simples, sem explorar telas demais |
| 15–25 min | Governança mínima | Focar só em proteção de branch, CODEOWNERS e SECURITY.md |
| 25–43 min | Code Scanning / CodeQL | Máximo de 10 min de navegação e 8 min de interpretação |
| 43–56 min | Secret Scanning / Push Protection | Máximo de 5 min para bloqueio e 8 min para tratamento |
| 56–68 min | Dependabot / Dependency Review | Não configurar `dependabot.yml` ao vivo |
| 68–77 min | Triagem e priorização | Usar um caso comparativo simples |
| 77–84 min | Security Overview | Abandonar demo interativa após 2 min se não carregar |
| 84–88 min | Copilot responsável | Não aplicar código ao vivo |
| 88–90 min | Encerramento | Sempre preservar |

## 14. Runbook por bloco

### 14.1 Contexto e arquitetura (0–8 min)

- **Objetivo**: situar a audiência no repositório e nas superfícies que serão usadas.
- **Pré-requisitos**: ambiente aberto, repositório carregado, abas preparadas.
- **Tela/ação do instrutor**:
  - mostrar `/home/runner/work/skills-introduction-to-repository-management/skills-introduction-to-repository-management/src/app.py`
  - mostrar um router em `/home/runner/work/skills-introduction-to-repository-management/skills-introduction-to-repository-management/src/backend/routers/activities.py`
  - mostrar `/home/runner/work/skills-introduction-to-repository-management/skills-introduction-to-repository-management/src/static/app.js`
  - mostrar `/home/runner/work/skills-introduction-to-repository-management/skills-introduction-to-repository-management/requirements.txt`
- **Resultado esperado da ferramenta**: não aplicável; objetivo é contextualização.
- **Interpretação esperada**: o repositório contém app, frontend, dependências e automação suficientes para uma demo realista.
- **Mensagem que o público deve levar**: GHAS faz mais sentido quando conectado ao ciclo real de desenvolvimento.
- **Critério de sucesso**: audiência entende o mapa básico do sistema.
- **Critério de encerramento**: quatro superfícies principais apresentadas sem aprofundar demais.
- **Fallback**: usar screenshots ou abrir só a árvore do repositório.
- **Reset**: voltar à página inicial do repositório.

### 14.2 Produtos, planos, permissões e pré-requisitos (8–15 min)

- **Objetivo**: esclarecer dependências de plano, permissão e plataforma.
- **Pré-requisitos**: material visual preparado.
- **Tela/ação do instrutor**: apresentar quadro com GitHub Code Security, GitHub Secret Protection e o termo GHAS.
- **Resultado esperado da ferramenta**: não aplicável; é uma explicação operacional.
- **Interpretação esperada**: recursos podem variar entre GitHub.com, GitHub Enterprise Cloud, GitHub Enterprise Server e entre repositórios públicos e privados.
- **Mensagem que o público deve levar**: nem toda falha de demo é falha do produto; muitas são de permissão ou configuração.
- **Critério de sucesso**: audiência sabe que a experiência depende de plano, visibilidade e permissões.
- **Critério de encerramento**: produto, permissão e Actions explicados.
- **Fallback**: usar slide estático.
- **Reset**: voltar à aba principal da demo.

### 14.3 Governança mínima (15–25 min)

- **Objetivo**: mostrar que segurança começa antes do alerta.
- **Pré-requisitos**: branch protection ativa, branch de demo e artefatos preparados.
- **Tela/ação do instrutor**:
  - mostrar controle de merge na branch principal
  - mostrar `CODEOWNERS` na branch preparada
  - mostrar `SECURITY.md` na branch preparada
- **Resultado esperado da ferramenta**: controles visíveis e compreensíveis.
- **Interpretação esperada**: governança define quem revisa, como reportar e como mudar com segurança.
- **Mensagem que o público deve levar**: scanner sem processo gera pouco resultado operacional.
- **Critério de sucesso**: três controles apresentados com clareza.
- **Critério de encerramento**: branch protection, CODEOWNERS e SECURITY.md conectados à narrativa.
- **Fallback**: screenshots dos controles.
- **Reset**: voltar à visão de código ou settings principal.

### 14.4 Code Scanning / CodeQL (25–43 min)

- **Objetivo**: mostrar detecção, interpretação, decisão e validação.
- **Pré-requisitos**:
  - alerta já aberto
  - PR ou branch preparada
  - captura de fallback disponível
- **Tela/ação do instrutor**:
  - abrir alerta previamente validado
  - correlacionar com o trecho de `/home/runner/work/skills-introduction-to-repository-management/skills-introduction-to-repository-management/src/static/app.js`
  - declarar explicitamente: **“Este trecho foi escolhido como cenário didático e validado previamente pelo instrutor na configuração de CodeQL usada na demonstração.”**
- **Resultado esperado da ferramenta**: alerta de Code Scanning visível.
- **Interpretação esperada**: o alerta indica um risco a ser analisado, não prova automática de exploração.
- **Mensagem que o público deve levar**: o scanner encontra padrões e fluxos; a decisão ainda é humana.
- **Critério de sucesso**: pelo menos um alerta demonstrado e interpretado.
- **Critério de encerramento**:
  - análise posterior não encontra mais o problema; ou
  - o alerta é encerrado com justificativa apropriada.
- **Fallback**: screenshots do alerta e da execução anterior.
- **Reset**: voltar à branch-base da demo.

### 14.5 Revisão humana complementar no backend (embutida no bloco CodeQL)

- **Objetivo**: contrastar ausência de alerta com falha arquitetural.
- **Pré-requisitos**: arquivos de backend abertos.
- **Tela/ação do instrutor**:
  - mostrar autenticação baseada em `teacher_username` em `/home/runner/work/skills-introduction-to-repository-management/skills-introduction-to-repository-management/src/backend/routers/activities.py`
  - mostrar “sessão” por username em `/home/runner/work/skills-introduction-to-repository-management/skills-introduction-to-repository-management/src/backend/routers/auth.py`
- **Resultado esperado da ferramenta**: não necessariamente haverá alerta.
- **Interpretação esperada**: risco relevante pode exigir revisão arquitetural e conhecimento do domínio.
- **Mensagem que o público deve levar**: ausência de alerta não é evidência de segurança.
- **Critério de sucesso**: audiência entende a diferença entre detecção automática e revisão humana.
- **Critério de encerramento**: problema arquitetural claramente explicado.
- **Fallback**: apontar apenas o fluxo em slide ou screenshot.
- **Reset**: retornar à aba do alerta principal.

### 14.6 Secret Scanning / Push Protection (43–56 min)

- **Objetivo**: demonstrar prevenção antes do merge e tratamento correto do caso.
- **Pré-requisitos**:
  - padrão customizado fictício validado
  - Push Protection ativa
  - branch efêmera pronta
  - comportamento de bypass conhecido
- **Tela/ação do instrutor**:
  - inserir apenas segredo fictício controlado
  - demonstrar bloqueio
  - remover o valor
  - explicar tratamento real
- **Resultado esperado da ferramenta**: bloqueio ou alerta esperado para o padrão fictício.
- **Interpretação esperada**: proteção de push reduz exposição, mas não substitui resposta a incidente.
- **Mensagem que o público deve levar**: em incidente real, é preciso revogar ou rotacionar a credencial, atualizar serviços e revisar acessos.
- **Critério de sucesso**: fluxo de bloqueio ou fallback demonstrado sem usar credenciais reais.
- **Critério de encerramento**:
  - cenário fictício limpo; e
  - procedimento real de tratamento explicado corretamente.
- **Fallback**: vídeo curto ou screenshots do bloqueio.
- **Reset**:
  - remover valor fictício
  - confirmar branch descartável
  - restaurar branch-base
  - garantir que o padrão fictício não seja confundido com credencial real

### 14.7 Dependabot / Dependency Review (56–68 min)

- **Objetivo**: mostrar inventário, risco conhecido e revisão de mudança.
- **Pré-requisitos**:
  - PR de dependência preparada
  - advisory ou visual esperado validado recentemente
  - versões original e proposta registradas
- **Tela/ação do instrutor**:
  - abrir a PR que altera `/home/runner/work/skills-introduction-to-repository-management/skills-introduction-to-repository-management/requirements.txt`
  - apontar o que é dependency review
  - diferenciar alerts, security updates e version updates
- **Resultado esperado da ferramenta**: visualização de risco ou contexto da mudança de dependência.
- **Interpretação esperada**: supply chain precisa de monitoramento contínuo e revisão antes do merge.
- **Mensagem que o público deve levar**: Dependabot não é um único recurso; são camadas diferentes de apoio.
- **Critério de sucesso**: distinção entre os conceitos entendida pelo público.
- **Critério de encerramento**:
  - mudança de dependência analisada
  - testes definidos ou executados
  - decisão de revisão explicada
- **Fallback**: screenshots da PR e dos alertas.
- **Reset**: restaurar a branch-base da PR de demonstração.

### 14.8 Triagem e priorização (68–77 min)

- **Objetivo**: ensinar decisão, não só navegação.
- **Pré-requisitos**: um caso comparativo simples preparado.
- **Tela/ação do instrutor**: comparar um alerta do frontend, um risco de autenticação e um caso de dependência.
- **Resultado esperado da ferramenta**: não aplicável; trata-se de interpretação.
- **Interpretação esperada**: severidade técnica e prioridade operacional não são a mesma coisa.
- **Mensagem que o público deve levar**: tratar tudo com a mesma urgência gera fila ruim e decisões fracas.
- **Critério de sucesso**: público entende por que contexto muda prioridade.
- **Critério de encerramento**: matriz aplicada ao menos uma vez.
- **Fallback**: usar tabela estática.
- **Reset**: voltar à navegação principal.

### 14.9 Security Overview (77–84 min)

- **Objetivo**: mostrar visão agregada de governança e exposição.
- **Pré-requisitos**:
  - organização preparada
  - dados já disponíveis
  - permissões confirmadas
- **Tela/ação do instrutor**:
  - abrir Security Overview da organização
  - mostrar filtros e distribuição de risco
- **Resultado esperado da ferramenta**: painel carregando com dados visíveis.
- **Interpretação esperada**: visibilidade organizacional ajuda priorização, cobertura e ownership em escala.
- **Mensagem que o público deve levar**: esta parte é organizacional e não é pré-requisito para repetir exercícios individuais.
- **Critério de sucesso**: visão agregada demonstrada sem bloquear o restante da agenda.
- **Critério de encerramento**: painel visto ou fallback acionado em até 2 minutos.
- **Fallback**: screenshots do painel com narrativa preparada.
- **Reset**: voltar ao repositório base da demo.

### 14.10 Copilot responsável (84–88 min)

- **Objetivo**: demonstrar investigação assistida, não remediação completa.
- **Pré-requisitos**:
  - conta Copilot disponível
  - prompt preparado
  - alerta ou trecho contextualizado
- **Tela/ação do instrutor**:
  - usar prompt contextualizado
  - pedir explicação do risco
  - questionar a resposta
- **Resultado esperado da ferramenta**: análise resumida e proposta inicial de investigação ou correção.
- **Interpretação esperada**: Copilot acelera análise, mas não substitui validação humana.
- **Mensagem que o público deve levar**: usar IA com contexto e senso crítico produz melhores decisões.
- **Critério de sucesso**: audiência vê utilidade e limite do Copilot.
- **Critério de encerramento**: análise assistida apresentada sem aplicar código ao vivo.
- **Fallback**: resposta previamente capturada.
- **Reset**: fechar aba ou limpar contexto da conversa.

Prompt sugerido:

> Analise este alerta de segurança em uma aplicação FastAPI com frontend JavaScript estático. Explique a origem dos dados, o ponto de uso inseguro, o impacto potencial e as premissas necessárias para exploração. Proponha uma correção mínima e uma correção estrutural. Não introduza novas bibliotecas sem justificar. Inclua testes que devem ser executados e indique possíveis efeitos colaterais. Não considere o alerta encerrado sem validação humana e execução dos testes.

Perguntas obrigatórias ao Copilot:

- Quais premissas você está assumindo?
- Como sabe que essa é a origem dos dados?
- Qual teste comprova a correção?
- A solução remove a causa ou apenas oculta o sintoma?
- Há impacto no comportamento existente?

### 14.11 Encerramento (88–90 min)

- **Objetivo**: fixar a mensagem principal e orientar repetição posterior.
- **Pré-requisitos**: links e próximos passos preparados.
- **Tela/ação do instrutor**:
  - reforçar o fluxo detectar → interpretar → priorizar → corrigir → validar → governar
  - indicar ordem dos exercícios posteriores
- **Resultado esperado da ferramenta**: não aplicável.
- **Interpretação esperada**: participantes saem com caminho claro para repetir.
- **Mensagem que o público deve levar**: segurança no ciclo de desenvolvimento depende de ferramentas e de processo.
- **Critério de sucesso**: próximos passos comunicados antes do fim do tempo.
- **Critério de encerramento**: workshop encerrado em até 90 minutos.
- **Fallback**: usar slide final com links.
- **Reset**: deixar o ambiente na branch-base ou tela inicial.

## 15. Exercícios posteriores recomendados

1. Habilitar ou revisar dependency graph.
2. Criar ou revisar `SECURITY.md`.
3. Configurar proteção da branch principal.
4. Adicionar `CODEOWNERS`.
5. Habilitar Code Scanning com CodeQL.
6. Analisar um alerta.
7. Configurar Secret Scanning e Push Protection em ambiente compatível.
8. Repetir o fluxo com segredo fictício controlado.
9. Alterar `requirements.txt` em uma nova PR.
10. Observar Dependency Review.
11. Diferenciar security updates e version updates.
12. Corrigir o risco de frontend demonstrado.
13. Melhorar o modelo de autenticação do backend.

## 16. Critérios de sucesso

### Sucesso técnico

- Alerta CodeQL disponível.
- Cenário de segredo fictício validado.
- PR de dependência acessível.
- Security Overview carregando ou fallback pronto.
- Copilot disponível ou fallback pronto.
- Reset testado.

### Sucesso pedagógico

- Participantes entendem que alerta não é prova de exploração.
- Participantes distinguem detecção de priorização.
- Participantes sabem que remover arquivo não revoga segredo.
- Participantes distinguem os recursos de dependência.
- Participantes sabem qual exercício repetir depois.
- O instrutor conclui dentro do tempo.

## 17. Procedimento resumido de reset

1. Voltar para a branch-base ou tag de restauração.
2. Garantir que `main` permaneceu intacta.
3. Descartar a branch efêmera do segredo fictício.
4. Restaurar a branch ou PR de dependência.
5. Confirmar que nenhum valor fictício ficou em arquivos ou commits da demo reutilizada.
6. Reabrir as páginas de fallback e links principais.
7. Validar novamente os alertas se houver ensaio adicional próximo ao evento.
