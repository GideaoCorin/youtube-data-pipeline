# Pipeline de Dados - YouTube Analytics

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

---

## 4. Arquitetura da Solução (Diagramação do Pipeline)

O diagrama abaixo ilustra o fluxo de dados automatizado, demonstrando a transição do pipeline manual (AS-IS) para a solução proposta (TO-BE).

```mermaid
graph LR
    subgraph Cloud [Fonte de Dados]
        API[YouTube API v3]
    end

    subgraph ETL_Process [Engenharia de Dados (Python)]
        Script((Script ETL))
        Logic{Verifica Histórico?}
    end

    subgraph Storage [Armazenamento]
        CSV[(Base Histórica .csv)]
    end

    subgraph Analytics [Consumo]
        DASH[IBM Cognos / Excel]
    end

    % Conexões
    API -- "JSON Response" --> Script
    Script -- "Transformação/Tratamento" --> Logic
    Logic -- "Sim (Modo Append)" --> CSV
    CSV -- "Leitura" --> DASH

    % Estilos
    style Cloud fill:#f9f9f9,stroke:#333,stroke-width:2px
    style ETL_Process fill:#e1f5fe,stroke:#01579b,stroke-width:2px
    style Storage fill:#e8f5e9,stroke:#2e7d32,stroke-width:2px
    style Analytics fill:#fff3e0,stroke:#ef6c00,stroke-width:2px

    click API "https://developers.google.com/youtube/v3" "Documentação da API"

## Como Executar
1. Clone este repositório.
2. Instale as dependências:
   ```bash
   pip install -r requirements.txt
