#### English Version

# spaCy Resume Analysis

This project uses spaCy and other NLP tools to analyze and extract skills from resumes. It leverages various Python libraries for data manipulation, visualization, and machine learning.

## Table of Contents
- [Installation](#installation)
- [Usage](#usage)
- [Features](#features)
- [License](#license)

## Installation
1. Clone the repository:
    ```bash
    git clone https://github.com/GabrielTelles4K/spaCy-Resume-Analysis.git
    cd spaCy-Resume-Analysis
    ```
2. Create a virtual environment:
    ```bash
    python -m venv env
    ```
3. Activate the virtual environment:
    - On Windows:
        ```bash
        .\env\Scripts\activate
        ```
    - On macOS/Linux:
        ```bash
        source env/bin/activate
        ```
4. Install the required packages:
    ```bash
    pip install -r requirements.txt
    ```

## Usage
1. Load the resume dataset:
    ```python
    df = pd.read_csv("path/to/resume-dataset/Resume.csv")
    ```
2. Process the resumes and extract skills:
    ```python
    clean = []
    for i in range(data.shape[0]):
        review = re.sub(r'(@[A-Za-z0-9]+)|([^0-9A-Za-z \t])|(\w+:\/\/\S+)|^rt|http.+?', " ", data["Resume_str"].iloc[i])
        review = review.lower().split()
        lm = WordNetLemmatizer()
        review = [lm.lemmatize(word) for word in review if not word in set(stopwords.words("english"))]
        clean.append(" ".join(review))
    data["Clean_Resume"] = clean
    data["skills"] = data["Clean_Resume"].str.lower().apply(get_skills)
    data["skills"] = data["skills"].apply(unique_skills)
    data.head()
    ```
3. Visualize the results:
    ```python
    fig = px.histogram(data, x="Category", title="Distribution of Jobs Categories").update_xaxes(categoryorder="total descending")
    fig.show()
    ```

## Features
- Extracts and visualizes skills from resumes.
- Uses spaCy's NLP capabilities.
- Visualizes job categories and skill distributions.

## License
This project is licensed under the MIT License.

---

#### Versão em Português

# Análise de Currículos com spaCy

Este projeto utiliza spaCy e outras ferramentas de PLN para analisar e extrair habilidades de currículos. Utiliza várias bibliotecas Python para manipulação de dados, visualização e aprendizado de máquina.

## Sumário
- [Instalação](#instalação)
- [Uso](#uso)
- [Funcionalidades](#funcionalidades)
- [Licença](#licença)

## Instalação
1. Clone o repositório:
    ```bash
    git clone https://github.com/GabrielTelles4K/spaCy-Resume-Analysis.git
    cd spaCy-Resume-Analysis
    ```
2. Crie um ambiente virtual:
    ```bash
    python -m venv env
    ```
3. Ative o ambiente virtual:
    - No Windows:
        ```bash
        .\env\Scripts\activate
        ```
    - No macOS/Linux:
        ```bash
        source env/bin/activate
        ```
4. Instale os pacotes necessários:
    ```bash
    pip install -r requirements.txt
    ```

## Uso
1. Carregue o dataset de currículos:
    ```python
    df = pd.read_csv("caminho/para/resume-dataset/Resume.csv")
    ```
2. Processe os currículos e extraia habilidades:
    ```python
    clean = []
    for i in range(data.shape[0]):
        review = re.sub(r'(@[A-Za-z0-9]+)|([^0-9A-Za-z \t])|(\w+:\/\/\S+)|^rt|http.+?', " ", data["Resume_str"].iloc[i])
        review = review.lower().split()
        lm = WordNetLemmatizer()
        review = [lm.lemmatize(word) for word in review if not word in set(stopwords.words("english"))]
        clean.append(" ".join(review))
    data["Clean_Resume"] = clean
    data["skills"] = data["Clean_Resume"].str.lower().apply(get_skills)
    data["skills"] = data["skills"].apply(unique_skills)
    data.head()
    ```
3. Visualize os resultados:
    ```python
    fig = px.histogram(data, x="Category", title="Distribuição das Categorias de Empregos").update_xaxes(categoryorder="total descending")
    fig.show()
    ```

## Funcionalidades
- Extrai e visualiza habilidades de currículos.
- Utiliza as capacidades de PNL do spaCy.
- Visualiza categorias de emprego e distribuições de habilidades.

## Licença
Este projeto é licenciado sob a Licença MIT.
