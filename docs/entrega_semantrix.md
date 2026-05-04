# Documentação de Entrega Semantrix: Projeto Wall-E

Esta documentação detalha as etapas de análise e visualização de daos construídas para solucionar
a problemática do **Dilema do Agente Confiável**, utilizando o ecossistema Python e Looker Studio.

---

### Coleta e Fontes de Dados

Para fundamentar a investigação, foi elaborada uma arquitetura de extração de dados públicos via API.
A coleta não armazenou dados localmente (atendendo a boas práticas de segurança), utilizando a biblioteca `kagglehub`
para download ecarregamento dinâmico. As fontes englobaram dados estruturados (.csv) e não estruturados (.json) que
precisaram de conversão e parsing:

- **Malicious Prompt Detection Dataset (MPDD)**: Dados primários utilizados para treinar o reconhecimento de
vocabulário malicioso e injeção de prompts.

- **LLM Safety Dataset for Chatbots**: Focado em técnicas avançadas de Jailbreak e evasão de filtros.

- **Amazon Top Cell Phones QA**: Base de perguntas e respostas reais (extraída e formatada a partir de um arquivo .json)
utilizada para simular o tráfego orgânico e o comportamento "seguro" de usuários.

---

### Modelagem e Análise Exploratória (EDA)

A etapa de processamento foi conduzida em linguagem Python. A Análise Exploratória de Dados (EDA)
buscou identificar a frequência de ataques e os atritos gerados na experiência do usuário.

- **Limpeza e Pré-processamento**: Higienização dos dados e mescla entre os dataset, criando um 
ambiente de testes balanceado.

- **Descobertas da EDA**: Foi mapeado que ataques possuem gatilhos semânticos repetitivos, termos como
*ignore*, *system*, *DAN*). No entanto, percebeu-se que aplicar bloqueios rígidos em palavras-chave gerava 
um alto volume de **falsos positivos**, bloqueando interações legítimas de usuários confusos.

- **Modelagem de Solução**: Com base nesse insight, foi modelada a arquitetura do "Motor Cerberus".
Em vez de um bloqueio total, os dados foram classificados em três camadas de risco: *Safe* (tráfego normal), 
*Blocked* (aataque explícito) e *Suspicius* (anomalias que exigem revisão humana).

---

### Conclusões e Visualização de Resultados

Os resultados da modelagem foram exportados e conectados ao **Looker Studio**, criando um dahsboard interativo com:

- **Visualização**: O painel narra visualmente a evolução investigativa do motor de segurança em três fases,
  iniciando no **Diagnóstico de Paranoia**, onde as regras rígidas geraram alta fricção e bloqueios equivocados
  de usuários comuns, passa pelo **Diagnóstico de Equilíbrio**, recalibragem de sensibilidade e termina na
  homologação final o **Motor Cerberus**.

- **Ação e Resolução**: A solução definitiva foi a implementação do modelo Cerberus, que atua com **três cabeças** de decisão:
- autorização de tráfego seguro (Safe), bloqueio sumário de ameaças (Blocked) e o roteamento de anomalias para revisão (Suspicious).
- O projeto conclui que a mitigação de riscos na automação de IA exige um modelo Human-in-the-Loop (Triagem Assistida).
- Essa arquitetura reduz o atrito, mantendo a conveniência operacional e protegendo a privacidade, em total alinhamento aos princípios da LGPD.

  
