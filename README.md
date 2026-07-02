# Clusterização de Textos Científicos com BERTimbau e Named Entity Recognition (NER)

Projeto desenvolvido para a disciplina de **Deep Learning**, explorando técnicas modernas de **Processamento de Linguagem Natural (NLP)**, **Transformers**, **Named Entity Recognition (NER)** e **Aprendizado Não Supervisionado** para identificar automaticamente grupos temáticos em projetos científicos brasileiros.

A solução utiliza o modelo **BERTimbau** para gerar embeddings semânticos, treina um modelo de **NER com spaCy** utilizando weak supervision e aplica **K-Means** para descobrir padrões presentes nos documentos.

---

# Objetivo

O objetivo deste projeto é desenvolver um pipeline completo para análise semântica de textos científicos em português, combinando diferentes técnicas de Inteligência Artificial para:

- Gerar embeddings utilizando Transformers;
- Extrair entidades nomeadas automaticamente;
- Treinar um modelo NER específico para o domínio;
- Agrupar documentos semanticamente semelhantes;
- Interpretar automaticamente os grupos encontrados.

---

# Arquitetura da Solução

```
Dataset DL-2024
        │
        ▼
Pré-processamento
        │
        ▼
Título + Descrição
        │
        ▼
Extração de Entidades (spaCy)
        │
        ▼
Treinamento NER
        │
        ▼
Embeddings BERTimbau
        │
        ▼
Escolha do melhor K
(Silhouette Score)
        │
        ▼
K-Means
        │
        ├────────► PCA
        │
        ├────────► t-SNE
        │
        └────────► TF-IDF
                   │
                   ▼
Interpretação dos Clusters
```

---

# Tecnologias Utilizadas

- Python
- Pandas
- NumPy
- PyTorch
- Hugging Face Transformers
- BERTimbau (`neuralmind/bert-base-portuguese-cased`)
- spaCy
- Scikit-Learn
- K-Means
- PCA
- t-SNE
- TF-IDF
- Matplotlib

---

# Dataset

Foi utilizado o dataset **DL-2024**, contendo milhares de projetos científicos brasileiros.

Cada documento foi construído a partir da concatenação de:

- **Título Público**
- **Descrição Pública**

Essa estratégia aumenta o peso semântico do tema principal durante a geração dos embeddings.

---

# Metodologia

## 1. Pré-processamento

Os textos foram normalizados e combinados em um único documento textual contendo título e descrição.

---

## 2. Extração de Entidades

Inicialmente foi utilizado o modelo **pt_core_news_lg** do spaCy para identificar automaticamente entidades nomeadas.

Como o dataset não possui anotações NER, foi utilizada uma estratégia de **Weak Supervision**, na qual as entidades detectadas servem como exemplos para treinamento de um modelo específico para o domínio científico.

---

## 3. Geração dos Embeddings

Cada documento foi convertido em um vetor semântico utilizando o modelo:

**BERTimbau Base Portuguese Cased**

Os embeddings foram obtidos através de **Mean Pooling** sobre a última camada oculta do Transformer.

---

## 4. Clusterização

Os embeddings foram agrupados utilizando o algoritmo **K-Means**.

A escolha do número ideal de clusters foi realizada automaticamente através do **Silhouette Score**, sendo identificado que **2 clusters** apresentavam o melhor desempenho para o conjunto de dados.

---

## 5. Visualização

Para facilitar a interpretação dos agrupamentos foram utilizadas duas técnicas de redução de dimensionalidade:

- PCA (Principal Component Analysis)
- t-SNE (t-distributed Stochastic Neighbor Embedding)

---

## 6. Interpretação

Após a clusterização, foi aplicado **TF-IDF** para identificar os termos mais representativos de cada grupo.

Isso permitiu interpretar automaticamente os temas predominantes encontrados pelo modelo.

---

# Resultados

O pipeline foi capaz de identificar automaticamente **dois grandes grupos temáticos** de projetos científicos.

## Cluster 1 — Sistemas Inteligentes e IoT

Projetos relacionados a:

- Desenvolvimento de software
- Plataformas inteligentes
- Sistemas embarcados
- Internet das Coisas (IoT)
- Monitoramento
- Gerenciamento
- Comunicação entre dispositivos

**Principais termos identificados:**

```
software
plataforma
monitoramento
controle
embarcado
dispositivos
IoT
protótipo
inteligente
gerenciamento
inteligência
hardware
comunicação
módulo
```

---

## Cluster 2 — Engenharia, Materiais e Energia

Projetos relacionados a:

- Engenharia
- Produção industrial
- Materiais avançados
- Energia
- Processos tecnológicos
- Tratamento
- Otimização
- Aplicações industriais

**Principais termos identificados:**

```
produção
aplicação
energia
materiais
controle
monitoramento
otimização
tratamento
solução
base
visando
através
```

---

# Avaliação

O desempenho da clusterização foi avaliado utilizando o **Silhouette Score**, permitindo selecionar automaticamente o número de clusters mais adequado.

Além disso, foram geradas duas formas de visualização:

### PCA

Mostrou uma separação global consistente entre os dois grupos de documentos.

### t-SNE

Revelou subgrupos internos e regiões de transição entre alguns documentos, indicando que os embeddings do BERTimbau capturam nuances semânticas além da divisão principal dos clusters.

Esse comportamento é esperado em bases textuais, onde diferentes áreas do conhecimento compartilham conceitos e vocabulário semelhantes.

---

# Competências Demonstradas

- Deep Learning
- Transformers
- BERTimbau
- Processamento de Linguagem Natural (NLP)
- Named Entity Recognition (NER)
- Weak Supervision
- Document Embeddings
- Clusterização Não Supervisionada
- K-Means
- PCA
- t-SNE
- TF-IDF
- Ciência de Dados
- Machine Learning

---

# Autor

**Matheus Lira**
