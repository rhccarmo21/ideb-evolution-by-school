
# 📈 Evolução do IDEB por Escola

[![Licença MIT](https://img.shields.io/badge/Licença-MIT-green)](https://pt.wikipedia.org/wiki/Licen%C3%A7a_MIT)
[![Python 3.9+](https://img.shields.io/badge/Python-3.9%2B-blue)](https://www.python.org/downloads/)
[![Streamlit](https://img.shields.io/badge/Streamlit-Dashboard-FF4B4B)](https://streamlit.io)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/seu-usuario/ideb-evolution-by-school)

## 📌 Sumário
1. [Visão Geral](#-visão-geral)
2. [Metodologia](#-metodologia)
3. [Fontes de Dados](#-fontes-de-dados)
4. [Instalação](#-instalação)
5. [Como Usar](#-como-usar)
6. [Exemplos](#-exemplos)
7. [Estrutura do Projeto](#-estrutura-do-projeto)
8. [Contribuição](#-contribuição)
9. [Licença](#-licença)
10. [Contato](#-contato)

---

## 🌐 Visão Geral

Plataforma de análise educacional que permite:

- 🕰️ **Acompanhamento temporal** do IDEB (2007-2023)
- 🏫 **Comparação entre escolas** com características similares
- 📊 **Identificação de fatores** associados à melhoria
- 🚨 **Detecção precoce** de quedas no desempenho

**Aplicações:**
- Gestão escolar baseada em evidências
- Formulação de políticas educacionais
- Alocação de recursos prioritários
- Benchmarking entre unidades escolares

---

## 🧠 Metodologia

### Análise Principal
```python
from ideb_analysis import SchoolTrendAnalyzer

analyzer = SchoolTrendAnalyzer(
    school_id='35000000',
    comparison_group='same_region'
)
trend = analyzer.get_trend()
```

### Técnicas Utilizadas:
1. **Análise de Trajetórias**: Classificação das escolas em:
   - Melhoria consistente
   - Estabilidade
   - Declínio progressivo

2. **Modelagem Multinível**: Fatores associados ao desempenho:
   ```python
   model = HierarchicalModel(
       student_level=['socioeconomic_status'],
       school_level=['resources', 'teacher_training']
   )
   ```

3. **Similaridade Educacional**: Clusterização por:
   - Infraestrutura
   - Perfil socioeconômico
   - Localização geográfica

---

## 📊 Fontes de Dados

| Fonte | Dados | Período | Acesso |
|-------|-------|---------|--------|
| INEP (IDEB) | Notas e Fluxo | 2007-2023 | Microdados |
| Censo Escolar | Infraestrutura | Anual | CSV |
| QEdu | Contexto Escolar | Anual | API |
| IBGE | Dados Territoriais | Decenal | Shapefiles |

**Estrutura Básica:**
```python
import pandas as pd

ideb_data = pd.DataFrame({
    'escola_id': ['35000000'],
    'nome': ['EMEF Prof. João Silva'],
    'ideb_2019': [6.1],
    'ideb_2021': [6.7],
    'meta_2021': [6.5]
})
```

---

## ⚙️ Instalação

### Requisitos Mínimos
- Python 3.9+
- 8GB RAM (16GB recomendado)
- 5GB espaço em disco

### Via pip
```bash
pip install ideb-analysis
```

### Modo Desenvolvimento
```bash
git clone https://github.com/seu-usuario/ideb-evolution-by-school.git
cd ideb-evolution-by-school
pip install -e ".[dev]"
```

---

## 🚀 Como Usar

### 1. Dashboard Interativo
```bash
streamlit run app/dashboard.py
```

### 2. Análise Programática
```python
from ideb_analysis import SchoolReport

report = SchoolReport('35000000')
results = report.generate(
    metrics=['ideb', 'fluxo'],
    years=range(2015, 2023)
)
```

### 3. Linha de Comando
```bash
ideb-analysis --escola 35000000 --output relatorio.pdf
```

---

## 🏫 Exemplos Práticos

### Caso 1: Identificação de Melhores Práticas
```python
from ideb_analysis import BestPractices

top_schools = BestPractices(
    region='Norte',
    growth_threshold=1.5  # Crescimento mínimo no IDEB
).identify()
```

**Saída:**
![Escolas em Destaque](https://exemplo.com/top-schools.png)

### Caso 2: Alerta de Risco
```python
alert = EarlyWarningSystem(
    school_id='35000000',
    decline_years=3
)
status = alert.check_status()
# Retorna: {'status': 'warning', 'trend': -0.4/ano}
```

---

## 🗂 Estrutura do Projeto

```
ideb-evolution-by-school/
├── data/
│   ├── raw/              # Microdados do INEP
│   └── processed/        # Dados tratados
├── notebooks/
│   ├── exploratory/      # Análises iniciais
├── ideb_analysis/
│   ├── core/             # Lógica de análise
│   ├── visualization/    # Gráficos educacionais
│   └── app/              # Dashboard Streamlit
├── requirements.txt
└── README.md
```

---

## 🤝 Contribuição

1. **Reporte Problemas** via [issues](https://github.com/seu-usuario/ideb-evolution-by-school/issues)
2. **Padrões de Código**:
   ```python
   def calculate_growth(ideb_series: pd.Series) -> float:
       """Calcula taxa de crescimento anual composta
       
       Args:
           ideb_series: Série temporal do IDEB
           
       Returns:
           Taxa média de crescimento (% a.a.)
       """
       return growth_rate
   ```
3. **Fluxo Recomendado**:
   ```bash
   git checkout -b feature/nova-metrica
   git commit -m "Adiciona análise de desigualdade"
   git push origin feature/nova-metrica
   ```

---

## 📜 Licença

```text
Copyright 2023 Evolução do IDEB por Escola

Permissão é concedida, gratuitamente...
```

---

## 📧 Contato

**Equipe de Análise Educacional**  
[analise@ideb.org.br](mailto:analise@ideb.org.br)  

**Secretarias de Educação**  
[secretarias@ideb.org.br](mailto:secretarias@ideb.org.br)  

**Acesso ao Dashboard**  
[![Portal](https://img.shields.io/badge/Acesse_o_Dashboard-Portal_IDEB-blue)](https://ideb.org.br/dashboard)

---

💡 **Para Gestores Escolares:**  
Baixe nosso guia de boas práticas:  
[📕 Guia de Melhoria do IDEB](docs/guia_ideb.pdf)

> **Nota Técnica:** Dados atualizados conforme divulgação oficial do INEP.
```

### Destaques:
1. **Foco na Escola**: Análises no nível unitário
2. **Contextualização**: Comparação com pares similares
3. **Praticidade**: Visualizações prontas para relatórios
4. **Detecção Precoce**: Modelos preditivos de desempenho
5. **Transparência**: Metodologia aberta e replicável

### Para Implementação:
1. Baixe os microdados mais recentes do INEP
2. Adapte os thresholds para sua realidade local
3. Integre com dados complementares da secretaria
4. Personalize os alertas para seu fluxo de trabalho.
