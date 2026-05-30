# Mission Control AI 🚀

Este projeto simula o backend de um centro de controle de missão espacial chamado **Orion Test Alpha**. O sistema monitora telemetrias críticas ciclo a ciclo (temperatura, comunicação, bateria, oxigênio e estabilidade operacional), calcula o nível de risco de forma determinística via Python e integra-se a um modelo de Inteligência Artificial local para fornecer diagnósticos preditivos e relatórios finais.

## Integrantes
* **Iago Neiva** — RM 570234
* **Kelly Stephanie** — RM 569044
* **Renan de Castro** — RM 570532

---

## Objetivo do Projeto
O objetivo da aplicação é demonstrar a união de lógica de programação estruturada com modelos de linguagem locais (LLMs). O sistema:
1. Recebe dados de sensores a cada ciclo da missão.
2. Pontua os riscos de cada sistema automaticamente (Regras de Alerta).
3. Identifica tendências de melhora ou piora.
4. Permite ao usuário acionar uma IA assistente (**Llama 3.2:1b**) para gerar pareceres técnicos e recomendações em tempo real.
5. Gera um sumário executivo consolidado ao encerramento da simulação.

---

## Tecnologias Utilizadas
* **Python 3** (Lógica principal, subprocessos e requisições HTTP)
* **Ollama** (Ferramenta para execução local do modelo de IA)
* **Llama 3.2:1b** (Modelo de linguagem leve integrado via API local)
* **Google Colab / Jupyter Notebook** (Ambiente de desenvolvimento)

---

## Como Executar o Projeto

Se você estiver executando o arquivo `missao_espacial_AI.ipynb` em um ambiente como o **Google Colab**, basta executar as células em ordem sequencial. O próprio script se encarrega de:

1. **Instalar as dependências do sistema** (`zstd` para descompactação).
2. **Instalar o Ollama** diretamente no ambiente Linux do notebook.
3. **Iniciar o servidor do Ollama** em segundo plano (`ollama serve`).
4. **Baixar o modelo leve** necessário (`ollama pull llama3.2:1b`).
5. **Iniciar a simulação interativa**, onde você poderá interagir digitando `sim` ou `nao` para as análises de ciclo.

> **Nota:** Certifique-se de que o ambiente do Colab possui conectividade com a internet para baixar o instalador do Ollama e os pesos do modelo Llama na primeira execução.

---

## Estrutura de Monitoramento (Regras de Negócio)

O script avalia os seguintes parâmetros para compor a pontuação de risco:

| Métrica | Faixa Normal (0 pts) | Faixa de Atenção (1 pt) | Faixa Crítica (2 pts) |
| :--- | :--- | :--- | :--- |
| **Temperatura** | 18°C a 29°C | Menor que 18°C OU de 30°C a 34°C | Maior ou igual a 35°C (Superaquecimento) |
| **Comunicação** | Maior ou igual a 60% | 30% a 59% | Menor que 30% |
| **Bateria** | Maior ou igual a 50% | 20% a 49% | Menor que 20% |
| **Oxigênio** | Maior ou igual a 90% | 80% a 89% | Menor que 80% |
| **Estabilidade**| Maior ou igual a 70% | 40% a 69% | Menor que 40% |

---
*Fim da documentação do projeto.*
