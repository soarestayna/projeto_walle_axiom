# Projeto WALL-E: Segurança de Agentes Autônomos e o Dilema da Hiper-Conveniência

### Parceria: EBAC & Semantix (Projeto Prático)

Este projeto consiste em uma investigação técnica e humana sobre os riscos de segurança associados à implementação de Agentes de IA Autônomos. O foco central é o paradoxo da **Hiper-Conveniência**: como a busca do usuário por automação extrema e redução de atrito abre brechas críticas para ataques cibernéticos e compromete a soberania dos dados.

---

## Visão Geral do Projeto

A análise investiga como Agentes de IA interagem com dados sensíveis (financeiros e de identidade) e explora vetores de ataque modernos, com destaque para a **Injeção de Prompt (Prompt Injection)**. O objetivo não é frear a inovação, mas aplicar inteligência de dados para criar guardrails que protejam o usuário sem inviabilizar a operação.

Vetores de Ataque Investigados

- **Prompt Injection**: Como instruções maliciosas podem "sequestrar" o comportamento da IA para contornar filtros de segurança.

- **Vazamento de Dados (Data Leakage)**: Riscos de exposição de informações sensíveis contidas no treinamento ou na memória de curto prazo do agente.

- **Praticidade vs Privacidade**: A análise do trade-off onde a facilidade de uso do usuário final acaba reduzindo as camadas de autenticação e verificação.

---

## Fundamentação Teórica e Arquitetura

Para embasar a estratégia de defesa, o projeto une conceitos multidisciplinares:

- **Análise de Dados (EBAC)**: Base para manipulação de datasets e modelagem estatística.

- **Análise de Redes Complexas (Scale-Free Networks)**: Baseado na teoria de Barabási-Albert, identifica-se que os Agentes de IA funcionam como Hubs Críticos em uma rede de transações. Proteger este nó central é vital, pois a sua queda ou manipulação gera um efeito cascata em todo o ecossistema financeiro.

- **Cibersegurança (Cisco/OWASP)**: Frameworks de segurança (OWASP Top 10 for LLMs) e monitoramento de logs para identificação de anomalias.

- **Lógica de Triagem e Inteligência de Ameaças (CTI)**

Para garantir que o analista humano receba dados prontos para a tomada de decisão, o sistema categoriza os alertas conforme a tabela abaixo:
| Tipo de Ameaça | Técnica Provável | Nível de Perigo | Ação do Sistema |
| :--- | :--- | :--- | :--- |
| **Prompt Injection** | Jailbreak (DAN) | Crítico | Bloqueio imediato e Alerta SOC |
| **Data Leakage** | Exfiltração via API | Alto | Suspensão de token e Revisão Humana | 
| **Anomalia de Consumo** | Automação Excessiva | Médio | Flag para análise de comportamento |
| **Prompt Seguro** | Interação Normal | Baixo | Autorizado |

---

## Soluções

**O Protocolo Cerberus**

Foi desenvolvido um motor de detecção evolutivo, culminando no Protocolo Cerberus, estruturado em três fases de maturação analítica:

- V1 (Protocolo de Vigilância Rígida): Alta taxa de bloqueios. Seguro, porém gerador de alto atrito operacional (falsos positivos).

- V2 (Protocolo de Equilíbrio Dinâmico): Implementação de regras heurísticas e validação de contexto para restaurar a conveniência, distinguindo intenções maliciosas de ruídos legítimos de suporte.

- V3 (Motor Cerberus e Resiliência): Teste de estresse massivo comprovando a estabilidade do sistema sob alta carga. O motor agora categoriza alertas com precisão cirúrgica, utilizando um modelo híbrido de Machine Learning e regras de CTI.


**Triagem Assistida (Human-in-the-Loop)**

A conclusão do projeto demonstra que a automação total de segurança é um risco. A solução ideal implementada é a Triagem Assistida: o motor de Machine Learning atua como um filtro de escala, reduzindo o ruído massivo, mas enriquecendo o alerta com metadados (Tags CTI) para que a decisão final e crítica permaneça com o analista humano.


---

## Estrutura do Repositório

O repositório foi desenhado seguindo práticas de segurança e código limpo:

- **`/imgs`**: Imagens de arquitetura e topologia de redes.

- **`/docs`**: Documentação teórica detalhada. Mais detalhes abaixo.

- **`investigacao_walle.ipynb`**: Notebook unificado contendo a Análise Exploratória (EDA), modelagem de Machine Learning e geração de grafos de rede.

- **`SECURITY.md`**: Diretrizes de segurança e política de reporte de vulnerabilidades do projeto.

- **`requirements.txt`**: Dependências necessárias para reprodução do ambiente.

---

## Documentação Detalhada

Acesse os capítulos para entender a fundamentação teórica completa:

1. [Introdução e Storytelling: O Paradoxo WALL-E](docs/01_contexto.md)
2. [Privacidade e LGPD: Transparência e Dados](docs/02_privacidade_lgpd.md)
3. [Riscos Residuais e Futuro: O Desafio Poliglota](docs/03_limitacoes_futuro.md)
4. [Referências Éticas e Bibliografia](docs/04_creditos_referencias.md)

---

## Visualização de Dados e Insights

Os resultados técnicos, a auditoria de risco e a eficácia do Protocolo Cerberus foram consolidados em um dashboard interativo.
**[Acesse o Dashboard no Looker Studio aqui](https://datastudio.google.com/reporting/85f8da3c-a751-4f99-afc9-bbc6e27f961f)**

---

#### Autora

Tayná Soares - [LinkedIn](https://www.linkedin.com/in/tayna-soares-4394ba150)
Investigação com foco em Cibersegurança, Análise de Dados e Governança.