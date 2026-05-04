# Checkpoint 2 — Dynamic Programming (FIAP)

## Sobre o Projeto

Este projeto tem como objetivo modelar redes de metrô como grafos ponderados e aplicar técnicas de programação dinâmica para encontrar:

- Caminho mais curto com memoização
- Caminho mais longo simples (sem ciclos)
- Análise de desempenho (tempo e memória)
- Impacto de horários (penalidades e bônus)

---

## Tecnologias Utilizadas

- Python 3.10+
- functools (memoização)
- tracemalloc (memória)
- matplotlib (gráficos)
- folium (mapa)

---

## Cidades Modeladas

- São Paulo (Metrô + CPTM)
- San Francisco (BART)
- Beijing (Metrô)

Cada grafo contém:
- Múltiplos caminhos
- Estrutura ponderada
- Simulação de tempo com base no horário

---

## Funcionalidades

### Caminho Mais Curto
Implementado com recursão e memoização, reduzindo significativamente o tempo de execução ao evitar recomputações.

### Caminho Mais Longo
Utiliza backtracking para explorar caminhos possíveis sem permitir ciclos.

### Fator de Horário

| Horário        | Fator | Descrição                  |
|---------------|------|----------------------------|
| 5h – 7h       | 0.6  | Baixo movimento (bônus)    |
| 7h – 9h       | 1.5  | Pico da manhã              |
| 9h – 17h      | 1.0  | Horário normal             |
| 17h – 20h     | 2.0  | Pico da tarde              |

---

## Análise de Desempenho

Foi realizada comparação entre:

- Execução com memoização
- Execução sem memoização

Resultados observados:
- Redução significativa no tempo de execução com memoização
- Evita recomputação de subproblemas
- Uso de memória controlado

---

## Visualizações

- Gráfico comparando tempo de execução entre cidades
- Mapa com rota destacada utilizando Folium

---

## Como Executar

```bash
# Criar ambiente virtual
python -m venv venv

# Ativar ambiente (Windows)
venv\Scripts\activate

# Instalar dependências
pip install matplotlib folium
```

Executar o projeto:

```bash
jupyter notebook
```

Abrir o arquivo:

```bash
notebook.ipynb
```

---

## Estrutura do Projeto

```plaintext
checkpoint_fiap/
│
├── notebook.ipynb
├── README.md
├── .gitignore
└── venv/
```

---

## Conceitos Aplicados

- Grafos ponderados
- Programação dinâmica
- Memoização
- Backtracking
- Análise de complexidade

---

## # Checkpoint 2 — Dynamic Programming

Nome do grupo: Atlas Engineering. 

Eduardo Bassan - RM561474
Henry Andrade - RM562622
Mariana S. do Egito Moreira - RM562544
João Victor Abe - RM561446
Deivid Ruan - RM566356 

Disciplina: FIAP — Dynamic Programming 

---

## Bibliografia

- Cormen, T. H. et al. Introduction to Algorithms  
- Python Documentation (functools, tracemalloc)  
- GeeksforGeeks — Graph Algorithms  

---

## Conclusão

A utilização de programação dinâmica mostrou-se eficiente para a resolução de problemas envolvendo grafos. A memoização reduziu significativamente o tempo de execução, enquanto o backtracking permitiu explorar caminhos mais complexos sem ciclos.

---

## Diferenciais do Projeto

- Comparação prática entre execução com e sem memoização  
- Visualização gráfica dos resultados  
- Representação geográfica com mapa  
- Código estruturado e documentado  
