# 🚇 FIAP — Dynamic Programming | Checkpoint 2

![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter&logoColor=white)
![Folium](https://img.shields.io/badge/Folium-Maps-green?logo=leaflet&logoColor=white)
![Status](https://img.shields.io/badge/Status-Concluído-brightgreen)

> Sistema de rotas para redes de metrô em três metrópoles — modelagem com grafos ponderados, recursão com memoização e visualização interativa com Folium.

---

## 👥 Integrantes do Grupo

| Nome | RA |
|------|----|
| Eduardo Bassan | RM561474 |
| Henry Andrade | RM562622 |
| Mariana S. do Egito Moreira | RM562544 |
| João Victor Abe | RM561446 |
| Deivid Ruan | RM566356 |

**Disciplina:** Dynamic Programming  
**Professor:** Andre Marques  
**Checkpoint:** 2 — Em Grupo  
**Entrega:** 04/05/2026

---

## 🎯 Descrição do Projeto

Desenvolvemos um sistema de rotas para redes de metrô de três grandes metrópoles, modelando cada rede como um **grafo ponderado não-dirigido** onde:

- **Nós** = estações de metrô
- **Arestas** = conexões entre estações adjacentes
- **Pesos** = tempo médio de viagem em minutos

O sistema encontra o **caminho mais curto** (recursão + memoização) e o **caminho mais longo simples** (backtracking) entre duas estações distantes, aplicando **fatores de penalidade e bônus** conforme o horário de partida.

---

## 🌆 As Três Cidades

| Cidade | Origem | Destino | Horário | Fator | Linhas |
|--------|--------|---------|---------|-------|--------|
| 🇧🇷 São Paulo | Tucuruvi (L1) | Capão Redondo (L5) | 18h | ×2.0 🔴 | 1, 2, 3, 5 |
| 🇨🇳 Beijing | Sihui East (L1) | Xizhimen (L2/4) | 8h | ×1.5 🟡 | 1, 2, 4, 10 |
| 🇺🇸 San Francisco | Dublin/Pleasanton | Daly City | 6h | ×0.6 🟢 | Azul, Amarela, Verde |

---

## ⏰ Fatores de Horário

| Faixa | Fator | Tipo |
|-------|-------|------|
| 05h – 07h | ×0.6 | 🟢 Bônus — metrô vazio |
| 07h – 09h | ×1.5 | 🟡 Pico da manhã |
| 09h – 17h | ×1.0 | 🔵 Horário normal |
| 17h – 20h | ×2.0 | 🔴 Pico da tarde |

---

## 🧠 Algoritmos Implementados

### 1. Caminho Mais Curto — Recursão + Memoização
```python
@functools.lru_cache(maxsize=None)
def menor_custo(origem, destino, hora, visitados=frozenset()):
    if origem == destino:
        return 0, (origem,)
    fator = fator_horario(hora)
    melhor_custo = float('inf')
    for vizinho, peso in grafo.get(origem, ()):
        if vizinho not in visitados:
            custo_r, cam_r = menor_custo(vizinho, destino, hora, visitados | {origem})
            if fator * peso + custo_r < melhor_custo:
                melhor_custo = fator * peso + custo_r
    return melhor_custo, melhor_caminho
```

### 2. Caminho Mais Longo — Backtracking
```python
def maior_custo(grafo, origem, destino, hora, visitados=None):
    # Explora todos os caminhos simples (sem ciclos)
    # Retorna o de maior custo total
```

### 3. Análise de Desempenho
- Tempo medido com `time.perf_counter()`
- Memória medida com `tracemalloc`
- Comparação com e sem memoização para as 3 cidades

---

## 📊 Complexidade

| Algoritmo | Tempo | Espaço |
|-----------|-------|--------|
| Menor custo **com** memoização | O(V × 2ᵛ) | O(V × 2ᵛ) |
| Menor custo **sem** memoização | O(V!) | O(V) |
| Maior custo (backtracking) | O(V!) | O(V) |

---

## 🗺️ Visualizações

Os três mapas interativos (Folium) mostram:
- 🔴 **Linha vermelha** — caminho mais curto
- 🟠 **Linha laranja** — caminho mais longo simples
- ⚪ **Cinza** — demais conexões do grafo
- 📍 Marcadores clicáveis com nome de cada estação

---

## ▶️ Como Executar

### Requisitos
```bash
pip install folium matplotlib jupyter
```

### Rodando o notebook
```bash
jupyter notebook notebook.ipynb
```

> Todas as células devem ser executadas em ordem. A célula interativa no final permite testar qualquer horário de partida para as 3 cidades.

---

## 📚 Bibliotecas Utilizadas

- `functools` — `lru_cache` para memoização
- `tracemalloc` — medição de uso de memória
- `time` — medição de tempo de execução
- `folium` — visualização dos grafos em mapas reais
- `matplotlib` — gráficos de desempenho
