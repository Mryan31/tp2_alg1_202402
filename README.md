# Diagnóstico da Rede Elétrica da Metalmax

## Introdução

Este projeto implementa uma análise da rede elétrica interna da Metalmax, uma siderúrgica especializada na produção de aço. A rede elétrica é composta por geradores, consumidores e conexões que transportam energia. O objetivo é diagnosticar o funcionamento da rede para identificar gargalos, falhas no fornecimento de energia e pontos de melhoria, garantindo a continuidade da produção com custos operacionais controlados.

---

## Objetivos do Projeto

O programa deve realizar os seguintes diagnósticos da rede elétrica:

1. **Energia Total**: Calcular a capacidade máxima que a rede suporta considerando as limitações das conexões.
2. **Energia Não-Atendida**: Determinar a quantidade de energia que não está chegando aos consumidores, ou seja, a demanda que não está sendo atendida.
3. **Energia Perdida**: Calcular a energia que é desperdiçada ao longo do trajeto da rede, por limitações das conexões.
4. **Conexão Crítica**: Identificar as conexões que estão operando em sua capacidade máxima e podem representar pontos de falha na rede.

---

## Modelagem

A rede elétrica será modelada utilizando **grafos direcionados**, onde:

- **Nó** representa geradores ou consumidores.
- **Aresta** representa conexões com capacidade máxima limitada.
  
O diagnóstico será baseado em algoritmos que trabalham sobre essa estrutura.

---

## Entrada e Saída

### Entrada

O programa lê da entrada padrão os dados no formato:

- Primeira linha: `V E`  
  Número de pontos (V) e conexões (E) na rede.
- Próximas V linhas: `Vi T`  
  Onde `Vi` é o identificador do ponto e `T` indica o tipo:
  - `0` para gerador (sem demanda)
  - valor > 0 para consumidor (indica demanda)
- Próximas E linhas: `Vi Vj C`  
  Indicam uma conexão do ponto `Vi` para o ponto `Vj` com capacidade máxima `C`.

### Saída

O programa imprime na saída padrão:

1. Energia total máxima que a rede suporta (ETotal).
2. Energia não atendida (EMissing).
3. Energia perdida (ELoss).
4. Quantidade de conexões críticas (PCritical).
5. Para cada conexão crítica: `Vi Vj CapacidadeUsada`.

---

## Como compilar e executar

```bash
g++ -std=c++17 -Wall -Wextra -Wpedantic -Wformat-security -Wconversion -Werror -o tp2 main.cpp graph.cpp diagnostics.cpp
./tp2 < testCase01.txt
