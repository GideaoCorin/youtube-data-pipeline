## Pipeline de Dados - YouTube Analytics

Este projeto implementa uma solução de Engenharia de Dados para automatizar a coleta de métricas de vídeos do YouTube, atendendo aos requisitos de um projeto de uma gravadora.

## 1. Objetivo e Escopo
A solução proposta substitui o processo de coleta de dados manual e amostral por um fluxo automatizado. A entrega foca em:
Automação Completa: Desenvolvimento em Python para extrair dados diretamente da API do YouTube.
Histórico: Implementação de um sistema de coleta que permite gerar histórico por data.
Sustentação: Os dados coletados sustentam os painéis de Visualizações e Interações atuais.

## 2. Tecnologias
- **Linguagem:** Python 3
- **Fonte de Dados:** YouTube Data API v3
- **Armazenamento:** Arquivo Plano (CSV) estruturado para leitura na ferramenta de DataViz (IBM Cognos).

## 3. Dicionário de Dados (Entregável)

O arquivo de saída `relatorio_youtube.csv` contém os seguintes campos, essenciais para sustentar os produtos de dados atuais:

| Nome da Coluna | Tipo de Dado | Descrição |
| :--- | :--- | :--- |
| `Data_Coleta` | Datetime | Data e hora da execução do script (`YYYY-MM-DD HH:MM`). Essencial para o histórico. |
| `ID_Video` | String | Identificador único do vídeo (11 caracteres). |
| `Titulo` | String | Título público do vídeo no momento da coleta. |
| `Visualizacoes` | Integer | Total acumulado de visualizações (para o Painel de Visualizações). |
| `Likes` | Integer | Total acumulado de "curtidas" (para o Painel de Interações). |
| `Comentarios` | Integer | Total acumulado de comentários (para o Painel de Interações). |

## 4. Arquitetura da Solução (Diagramação do Pipeline)

O diagrama abaixo ilustra o fluxo de dados automatizado e o processo AS IS vs. TO BE.

![Diagrama de Arquitetura do Pipeline ETL](/assets/Pipeline_Youtube_Final_v2.drawio.png)

---

## Como Executar
1. Clone este repositório.
2. Instale as dependências:
   ```bash
   pip install -r requirements.txt
