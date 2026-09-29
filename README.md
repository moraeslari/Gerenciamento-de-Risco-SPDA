# Gerenciamento de Risco SPDA

As descargas atmosféricas representam uma das principais ameaças às insta-
lações elétricas, podendo causar danos a equipamentos, interrupções no fornecimento
de energia e riscos à segurança das pessoas. Em subestações de alta tensão, a adoção
de um Sistema de Proteção contra Descargas Atmosféricas (SPDA) adequadamente
projetado é fundamental para garantir a confiabilidade operacional e a proteção
da instalação. Nesse contexto, o gerenciamento de risco desempenha um papel es-
sencial, pois permite determinar a necessidade de proteção e o nível de proteção
mais adequado para a estrutura. Este trabalho apresenta o desenvolvimento de uma
ferramenta computacional com interface gráfica destinada à automatização dos cál-
culos de gerenciamento de risco e ao auxílio no projeto de SPDA. Para validação
da aplicação, foi realizado um estudo de caso em uma subestação de alta tensão,
utilizando dados reais da instalação.

A ferramenta permite calcular automaticamente:

- Áreas equivalentes de exposição;
- Número anual de eventos perigosos;
- Probabilidades de dano;
- Componentes de risco;
- Perdas associadas;
- Riscos R1, R2 e R3;
- Frequência de danos (Norma 2026);
- Indicadores comparativos entre risco calculado e risco tolerável.

O sistema foi desenvolvido como parte do Trabalho de Conclusão de Curso em Engenharia Elétrica.


# ⚡ Gerenciamento de Risco para Sistemas de Proteção contra Descargas Atmosféricas (SPDA)

## 📖 Sobre o Projeto

O **Gerenciamento de Risco para SPDA** é uma ferramenta computacional desenvolvida em **Python** com interface gráfica em **Streamlit**, destinada à automação da análise de risco de estruturas e subestações frente às descargas atmosféricas.

A aplicação foi desenvolvida como Trabalho de Conclusão de Curso (TCC) em Engenharia Elétrica com o objetivo de auxiliar projetistas e engenheiros na aplicação da metodologia estabelecida pela **ABNT NBR 5419**, reduzindo erros de cálculo, aumentando a produtividade na elaboração de estudos e fornecendo uma interface intuitiva para avaliação dos riscos associados a descargas atmosféricas.

---

## 🎯 Objetivos

- Automatizar os cálculos de análise de risco previstos na ABNT NBR 5419;
- Reduzir o tempo necessário para realização dos estudos;
- Minimizar erros decorrentes de cálculos manuais;
- Auxiliar no dimensionamento e na tomada de decisão sobre medidas de proteção;
- Disponibilizar uma interface amigável para utilização por engenheiros e projetistas.

---

## ⚠️ Contexto

As descargas atmosféricas representam uma das principais causas de danos em instalações elétricas de potência, podendo ocasionar:

- Choques elétricos em pessoas;
- Danos físicos às estruturas;
- Falhas em sistemas internos;
- Interrupções de serviço;
- Prejuízos econômicos;
- Indisponibilidade operacional de subestações.

Nesse contexto, a análise de risco prevista pela ABNT NBR 5419 torna-se essencial para determinar a necessidade de medidas de proteção e seus respectivos níveis de proteção.

---

# 🚀 Funcionalidades

A ferramenta permite:

✅ Cálculo automático das áreas equivalentes de exposição;

✅ Cálculo do número médio anual de eventos perigosos;

✅ Determinação das probabilidades de dano;

✅ Cálculo das perdas associadas;

✅ Determinação dos componentes de risco;

✅ Avaliação dos riscos:

- R1 – Perda de vida humana;
- R2 – Perda de serviço ao público;
- R3 – Perda de patrimônio cultural;
- F – Frequência de danos (Norma 2026).

✅ Comparação entre risco calculado e risco tolerável;

✅ Visualização detalhada de todas as etapas dos cálculos;

✅ Banco de dados integrado de densidade de descargas atmosféricas (NG).

---

# 🖥️ Interface Gráfica

A aplicação foi desenvolvida utilizando **Streamlit**, proporcionando:

- Interface intuitiva;
- Configuração dinâmica dos parâmetros;
- Visualização dos resultados em tabelas;
- Indicadores visuais de conformidade;
- Gráficos comparativos;
- Organização dos parâmetros por categorias.

---

# 📊 Metodologia de Cálculo

A ferramenta implementa as equações da ABNT NBR 5419 para avaliação de risco contra descargas atmosféricas.

A estrutura geral dos cálculos é baseada em:

```math
R = N \times P \times L
```

onde:

- **N** = número de eventos perigosos;
- **P** = probabilidade de dano;
- **L** = perda associada.

---

## Eventos Perigosos

### Descargas diretas na linha elétrica

```math
N_L = N_G \times A_L \times C_I \times C_E \times C_T \times 10^{-6}
```

### Descargas próximas à linha elétrica

```math
N_I = N_G \times A_I \times C_I \times C_E \times C_T \times 10^{-6}
```

com:

```math
A_L = 40 \times L_L
```

```math
A_I = 4000 \times L_L
```

---

# 💻 Trechos da Implementação

## Cálculo das Áreas Equivalentes

```python
AL = 40 * LL
AI = 4000 * LL

AL_s = 40 * LLs
AI_s = 4000 * LLs
```

---

## Cálculo dos Eventos Perigosos

```python
NL = NG * AL * CI * CE * CT * 10**-6
NI = NG * AI * CI * CE * CT * ****-6

NL_s = NG * AL_s * CI * CE * CT * 10**-6
NI_s** NG ***I_s * CI * CE * CT * 10**-6
```

---

## Cálculo dos Componentes de Risco

```python
RA = ND * PA * LA
RB = ND * PB * LB
RU = NL * PU * LU
RV = NL * PV * LV
```

---

## Cálculo dos Riscos

```python
R1 = RA + RB + RU + RV

R2 = RB2 + RV2_s

R3 = 0.0
```

---

## Obtenção Automática do NG

```python
resultado = df[
    (df["UF"] == uf) &
    (df["Município"] == municipio)
]

ng = resultado.iloc[0]["NG"]
```

---

# 🗂️ Estrutura do Projeto

```text
Gerenciamento-de-Risco-SPDA/
│
├── app.py
├── interface.py
├── README.md
├── requirements.txt
│
├── dados/
│   └── banco_ng_municipios.xlsx
│
├── imagens/
│   ├── interface_principal.png
│   ├── exemplo_resultado.png
│   └── fluxo_calculo.png
│
└── assets/
```

---

# 📥 Instalação

Clone o repositório:

```bash
git clone https://github.com/moraeslari/Gerenciamento-de-Risco-SPDA.git
```

Acesse a pasta:

```bash
cd Gerenciamento-de-Risco-SPDA
```

Instale as dependências:

```bash
pip install -r requirements.txt
```

---

# ▶️ Execução

Execute a aplicação localmente:

```bash
streamlit run app.py
```

---

# 📋 Fluxo de Utilização

1. Selecionar a origem do parâmetro NG;
2. Informar as características da estrutura;
3. Informar os parâmetros das linhas de energia;
4. Informar os parâmetros das linhas de sinal;
5. Configurar os parâmetros por zona;
6. Executar o cálculo;
7. Analisar os resultados obtidos;
8. Comparar os riscos calculados com os riscos toleráveis.

---

# 📈 Resultados Disponíveis

A aplicação disponibiliza:

- Resumo dos riscos;
- Áreas equivalentes;
- Eventos perigosos;
- Probabilidades;
- Componentes de risco;
- Perdas;
- Frequência de danos (Norma 2026);
- Gráfico comparativo entre riscos calculados e riscos toleráveis.

---

# 🛠️ Tecnologias Utilizadas

- Python
- Streamlit
- Pandas
- NumPy
- Plotly

---

# 🎓 Trabalho Acadêmico

Este projeto foi desenvolvido como Trabalho de Conclusão de Curso em Engenharia Elétrica.

**Título do Trabalho:**

> Desenvolvimento de uma Ferramenta Computacional para Análise de Risco e Auxílio ao Dimensionamento de Sistemas de Proteção contra Descargas Atmosféricas em Subestações.

---

# 👩‍💻 Autora

**Larissa Moraes dos Santos**

Graduanda em Engenharia Elétrica

Universidade Federal do Rio de Janeiro (UFRJ)

---

# 📄 Licença

Este projeto foi desenvolvido com fins acadêmicos e educacionais.
