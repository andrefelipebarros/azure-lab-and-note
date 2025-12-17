# 🔍 Azure AI Search: Mineração de Conhecimento com Inteligência Artificial

Este repositório contém a documentação do laboratório prático realizado através da plataforma **DIO**, com foco na utilização do **Azure AI Search** para indexação e busca inteligente de dados.

## 🎯 Objetivo
O objetivo deste projeto é configurar uma solução de mineração de conhecimento (*Knowledge Mining*) que permite extrair insights de dados não estruturados, utilizando habilidades de IA para enriquecer o conteúdo e facilitar a pesquisa.

## 🛠️ Tecnologias Utilizadas
* **Azure AI Search:** Motor de busca e indexação.
* **Azure Storage Account:** Armazenamento dos documentos brutos (PDFs, imagens, etc).
* **Azure AI Services:** Serviços de IA para enriquecimento (OCR, análise de imagem, etc).

## 📋 Passo a Passo Realizado

### 1. Criação dos Recursos
Foram criados os recursos necessários no portal da Azure: o serviço de busca, o armazenamento e os serviços cognitivos.

### 2. Ingestão de Dados (Data Ingestion)
Carregamento de documentos de exemplo (como avaliações de clientes) em um container de Blob Storage para servir como fonte de dados.

### 3. Configuração do Indexador (Indexer)
Configuração do processo de leitura dos dados, onde a IA:
* Extraiu texto de documentos.
* Realizou OCR (Reconhecimento de caracteres) em imagens.
* Detectou frases-chave e sentimentos.

### 4. Exploração de Dados
Utilização do **Search Explorer** no portal do Azure para realizar consultas JSON e validar os resultados indexados.

## 💡 Insights Obtidos
* **Automatização:** A capacidade de processar milhares de documentos e extrair metadados automaticamente economiza centenas de horas de trabalho manual.
* **Busca Semântica:** A IA consegue encontrar termos relacionados mesmo que a palavra exata não esteja no documento, aumentando a precisão da busca.
* **Escalabilidade:** A infraestrutura da Azure permite lidar com volumes massivos de dados sem perda de performance.
