# 📊 Teix Invest - Simulador de Investimentos em Fundos Imobiliários (FIIs)

Projeto desenvolvido como parte do desafio prático da **DIO (Digital Innovation One)**, com o objetivo de construir uma ferramenta no Microsoft Excel com visual de aplicativo para simulação de acúmulo de patrimônio e renda passiva através de FIIs.

---

## 🎯 Perguntas Respondidas pela Ferramenta

A ferramenta responde de forma clara e centralizada às principais dúvidas de planejamento financeiro:

| Pergunta de Negócio | Localização na Ferramenta |
| :--- | :--- |
| **Quanto investir por mês?** | Bloco **CONFIGURAÇÕES** / **INVESTIMENTO MENSAL** |
| **Por quantos anos?** | Bloco **INVESTIMENTO MENSAL** |
| **Qual a taxa de rendimento mensal?** | Bloco **INVESTIMENTO MENSAL** |
| **Quanto de patrimônio vai acumular?** | Bloco **INVESTIMENTO MENSAL** (Resumo) e Tabela **CENÁRIOS** (2, 5, 10, 20 e 30 anos) |
| **Quanto vai receber de dividendos por mês?** | Bloco **INVESTIMENTO MENSAL** e Tabela **CENÁRIOS** |

---

## 🧮 Aplicação das Fórmulas Principais

### 1. Função `VF` (Valor Futuro)
A função `VF` foi utilizada para projetar o crescimento do patrimônio acumulado ao longo do tempo, considerando aportes mensais recorrentes e juros compostos.
* **Fórmula aplicada:** `=VF(taxa_mensal; tempo_em_meses; -aporte_mensal)`
* **Onde foi usada:** Na projeção de patrimônio do período selecionado e na tabela comparativa de **CENÁRIOS** (2 a 30 anos).

### 2. Função `PROCV` com Chave Composta
A função `PROCV` é responsável por buscar dinamicamente o percentual de alocação de cada tipo de FII com base no perfil de investidor selecionado na lista suspensa.
* **Fórmula aplicada:** `=PROCV($C$30 & " - " & B34; 'Tabela de apoio'!$A:$D; 4; 0)`
* **Como funciona:** Junta o nome do Perfil selecionado (ex: `Moderado`) com o Tipo de FII (ex: `PAPEL`), criando a chave de busca `Moderado - PAPEL` para pesquisar na *Tabela de apoio*.

---

## 🏷️ Intervalos Nomeados Criados

Para tornar as fórmulas limpas e de fácil leitura, foram criados os seguintes intervalos nomeados:
* `salario`: Valor do salário bruto/líquido informado nas configurações.
* `rendimento_carteira`: Taxa média estimada de retorno do fundo.
* `sugestao_aporte`: Valor sugerido para investimento (30% do salário).
* `aporte`: Valor que o usuário decide investir por mês.
* `taxa_mensal`: Rendimento percentual mensal configurado.

---

## 📈 Perfis de Investidor e Percentuais

Os percentuais de alocação foram estruturados na aba **Tabela de apoio** e distribuídos em 6 categorias de FIIs (*Papel, Tijolo, Híbrido, FOFs, Desenvolvimento e Hotelarias*):

* **Conservador:** Foco em menor volatilidade, com maior exposição em *Tijolo* (50%) e *Papel* (30%).
* **Moderado:** Equilíbrio entre rentabilidade e risco, distribuindo entre *Tijolo* (40%), *Papel* (32%), *FOFs* (10%), *Desenvolvimento* (10%) e *Hotelarias* (10%).
* **Agressivo:** Foco em maior retorno/desconto, aumentando a fatia em *Papel* (50%) e *Desenvolvimento* (20%).

---

## 🖼️ Demonstração Prática

### Simulação 1: Perfil Moderado
> *<img width="1105" height="923" alt="image" src="https://github.com/user-attachments/assets/51a33fb0-1d32-4f99-a28b-c2930b8a1a4a" />*

### Simulação 2: Perfil Agressivo
> *<img width="1103" height="903" alt="image" src="https://github.com/user-attachments/assets/6ab7aa82-7d25-4688-8075-fc861d19ee57" />*
