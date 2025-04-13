# 🚇 Smart London Metro Routing

Sistema inteligente de roteamento para passageiros no metrô de Londres — o mais antigo em operação no mundo — considerando múltiplos fatores reais de mobilidade urbana.

## 📌 Descrição

Este projeto utiliza **programação dinâmica com recursão e memoization** para encontrar o melhor trajeto entre duas estações do metrô de Londres, levando em conta:

- 🌍 **Distâncias geográficas reais** (com latitude e longitude).
- 🚆 **Velocidade média dos trens:** 35 km/h.
- ⏱️ **Tempo de espera por estação:** depende da hora da viagem.
- 🔁 **Penalização por troca de linha.**
- 🧭 **Modos de rota:** mais rápida, média e mais longa (sem revisitar estações).

A rede do metrô é modelada como um **grafo georreferenciado**, e a visualização dos trajetos é feita com **Folium**, em um mapa interativo.

## 🧠 Função principal

```python
def menor_tempo_dp(origem, destino, hora_inicio, modo='menor')
```

**Parâmetros:**
- `origem`: nome da estação inicial.
- `destino`: nome da estação final.
- `hora_inicio`: string no formato `"HH:MM"`.
- `modo`: `'menor'` para o menor tempo total, `'maior'` para o trajeto mais longo (sem revisitar estações), `'medio'` para uma opção intermediária.

## 💡 Exemplo de saída esperada

```
Tempo total: 11.5 minutos  
Caminho: King's Cross → Oxford Circus → Green Park → Victoria Station  
Linhas: Victoria → Victoria → Victoria  
Trocas de linha: 0
```

## 📊 Visualização com Folium

- 🗺️ Mapa interativo com o trajeto percorrido.
- 📍 Marcadores para estação de início e fim.
- 🎨 Linhas coloridas representando cada linha do metrô.

## 📁 Dados fornecidos

- `stations_coordinates.csv`: nome, latitude e longitude de cada estação.
- `metro_edges.csv`: conexões entre estações e suas respectivas linhas (ex: Victoria, Northern, Bakerloo, Jubilee, Circle).

## 🎯 Objetivos implementados

- [x] Cálculo da distância geográfica com a fórmula de Haversine.
- [x] Cálculo do tempo de deslocamento baseado em distância e velocidade.
- [x] Adição de tempo de espera por horário:
  - Antes das 11h: 1.5 minutos.
  - Das 11h às 18h: 1.0 minuto.
  - Após as 18h: 2.0 minutos.
- [x] Penalidade por troca de linha.
- [x] Algoritmo com recursão + memoization.
- [x] Múltiplos modos de rota: menor, médio e maior tempo.
- [x] Visualização em mapa interativo com Folium.
