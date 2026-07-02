# Clusterização de Textos Científicos com BERTimbau e Deep Learning

Projeto desenvolvido para a disciplina de **Deep Learning**, com foco na aplicação de **Transformers**, **Processamento de Linguagem Natural (NLP)** e **Aprendizado Não Supervisionado** para realizar a clusterização de projetos científicos brasileiros.

O projeto utiliza uma abordagem híbrida combinando **BERTimbau**, **Named Entity Recognition (NER)**, **TF-IDF**, **Word2Vec** e técnicas de redução de dimensionalidade para gerar representações semânticas robustas dos textos.

---

## Objetivos

- Construir embeddings semânticos utilizando um modelo Transformer em português.
- Filtrar automaticamente textos pertencentes a setores não tecnológicos.
- Extrair entidades relevantes utilizando NER treinado especificamente para o domínio.
- Combinar diferentes representações textuais em um único vetor híbrido.
- Aplicar algoritmos de clusterização para identificar grupos de projetos semelhantes.

---

# Arquitetura da Solução

```
Dataset
    │
    ▼
Pré-processamento
    │
    ▼
Pré-filtro Temático
    │
    ▼
Embeddings BERTimbau
    │
    ├────────► TF-IDF
    │
    ├────────► Word2Vec
    │
    └────────► NER Setorial
               │
               ▼
Representação Híbrida
               │
               ▼
Redução de Dimensionalidade
               │
               ▼
K-Means
               │
               ▼
Avaliação e Visualizações
```

---

# Tecnologias Utilizadas

- Python
- Pandas
- NumPy
- Scikit-Learn
- Transformers (Hugging Face)
- BERTimbau (`neuralmind/bert-base-portuguese-cased`)
- PyTorch
- spaCy
- Gensim
- Matplotlib
- Seaborn

---

# Metodologia

## 1. Carregamento do Dataset

O conjunto de dados é composto por projetos científicos brasileiros contendo título e descrição pública.

---

## 2. Construção do Texto

Para aumentar o peso semântico do tema principal, o título do projeto é repetido antes da descrição.

Exemplo:

```
Título + Título + Descrição
```

---

## 3. Pré-filtro Temático

Antes da geração dos embeddings é aplicado um filtro baseado em aproximadamente **63 palavras-chave**, organizadas em diferentes setores corporativos.

Essa etapa reduz o ruído do conjunto de dados e melhora a qualidade da clusterização.

---

## 4. Extração de Entidades (NER)

Foi treinado um modelo **spaCy** específico para reconhecer entidades relacionadas aos setores analisados.

As entidades identificadas são incorporadas à representação final do documento.

---

## 5. Geração dos Embeddings

O projeto utiliza o modelo:

**BERTimbau Base Portuguese Cased**

para transformar cada documento em um vetor semântico utilizando Mean Pooling.

---

## 6. Representação Híbrida

Cada documento é representado pela concatenação de quatro blocos de informação:

- Embeddings BERTimbau
- Vetores TF-IDF
- Representação Word2Vec
- Entidades extraídas pelo NER

Essa estratégia aumenta a capacidade de representação semântica dos textos.

---

## 7. Redução de Dimensionalidade

Após a concatenação dos vetores é realizada redução de dimensionalidade para facilitar o processo de clusterização e visualização.

---

## 8. Clusterização

Foi utilizado o algoritmo:

- K-Means

para identificar automaticamente grupos de projetos com características semelhantes.

---

## 9. Avaliação

A qualidade dos clusters é analisada utilizando métricas como:

- Silhouette Score
- Visualizações em PCA
- Visualizações em t-SNE

---

# Principais Técnicas de Deep Learning

- Transformers
- BERTimbau
- Word Embeddings
- Mean Pooling
- Processamento de Linguagem Natural (NLP)
- Named Entity Recognition (NER)
- Representação Híbrida de Documentos

---

# Contexto Acadêmico

Projeto desenvolvido como atividade da disciplina de **Deep Learning**, explorando técnicas modernas de Inteligência Artificial e Processamento de Linguagem Natural para análise semântica de textos científicos.

---

# Autor

**Matheus Lira**
