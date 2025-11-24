# 🏢 Análise de Dados do Mercado Imobiliário

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![Pandas](https://img.shields.io/badge/Library-Pandas-150458)
![Matplotlib](https://img.shields.io/badge/Library-Matplotlib-orange)
![Status](https://img.shields.io/badge/Status-Concluído-success)

> Um projeto de Ciência de Dados focado na limpeza, tratamento, engenharia de atributos e análise exploratória de uma base de dados de aluguéis residenciais e comerciais.

---

## 📋 Tabela de Conteúdos
- [Sobre o Projeto](#-sobre-o-projeto)
- [Dicionário de Dados](#-dicionário-de-dados)
- [Etapas do Projeto (Pipeline)](#-etapas-do-projeto-pipeline)
- [Consultas e Filtros Aplicados](#-consultas-e-filtros-aplicados)
- [Engenharia de Atributos](#-engenharia-de-atributos)
- [Visualização de Dados](#-visualização-de-dados)
- [Como Executar](#-como-executar)
- [Autor](#-autor)

---

## 📖 Sobre o Projeto

Este projeto tem como objetivo simular as demandas de uma empresa do setor imobiliário. Utilizando a biblioteca **Pandas**, o foco principal foi transformar dados brutos em informações estratégicas. 

O desafio envolveu importar uma base de dados desorganizada, remover inconsistências (dados nulos, tipos de imóveis irrelevantes) e criar novas métricas para auxiliar na tomada de decisão, como o cálculo do valor bruto mensal e anual por imóvel.

---

## 🗃 Dicionário de Dados

A base de dados original (`aluguel.csv`) contém as seguintes variáveis:

| Coluna | Descrição | Tipo de Dado |
| :--- | :--- | :--- |
| **Tipo** | Categoria do imóvel (ex: Apartamento, Casa, Loja) | String |
| **Bairro** | Localização do imóvel | String |
| **Quartos** | Quantidade de quartos | Inteiro |
| **Vagas** | Quantidade de vagas de garagem | Inteiro |
| **Suites** | Quantidade de suítes | Inteiro |
| **Area** | Metragem quadrada do imóvel ($m^2$) | Inteiro |
| **Valor** | Valor do aluguel base | Float |
| **Condominio** | Valor da taxa de condomínio | Float |
| **IPTU** | Imposto Predial e Territorial Urbano | Float |

---

## ⚙️ Etapas do Projeto (Pipeline)

O projeto seguiu um fluxo estruturado de tratamento de dados:

1.  **Coleta de Dados:** Importação da base de dados via URL/CSV.
2.  **Limpeza de Dados (Data Cleaning):**
    * Eliminação de dados nulos em campos críticos.
    * Preenchimento de valores nulos (NaN) em `Condominio` e `IPTU` com zero, assumindo isenção.
    * Remoção de imóveis comerciais para focar a análise no setor **residencial**.
3.  **Filtragem:** Seleção de imóveis baseada em critérios de negócio específicos.
4.  **Feature Engineering:** Criação de novas colunas para enriquecer a análise.
5.  **Exportação:** Salvamento dos dados tratados em novos arquivos CSV (`Dados_apartamentos.csv`, etc.).

---

## 🔍 Consultas e Filtros Aplicados

Para gerar relatórios específicos, foram aplicados filtros avançados utilizando o método `.query()` e Seleção Booleana:

* **Foco Residencial:** Remoção de tipos como *'Loja', 'Conjunto Comercial', 'Galpão'*.
* **Apartamentos Econômicos:** Seleção de apartamentos com 1 quarto e aluguel menor que R$ 1.200,00.
* **Apartamentos Médios/Grandes:** Seleção de apartamentos com pelo menos 2 quartos, aluguel abaixo de R$ 3.000,00 e área superior a 70 $m^2$.

---

## 🛠 Engenharia de Atributos

Novas variáveis foram criadas para facilitar a análise financeira e descritiva:

* `Valor_por_mes`: Soma do Aluguel + Condomínio.
* `Valor_por_ano`: (Valor por mês * 12) + IPTU.
* `Descricao`: Uma string concatenada resumindo o imóvel (ex: *"Apartamento em Leblon com 2 quartos..."*).
* `Possui_suite`: Variável categórica (Sim/Não) derivada da coluna numérica de suítes.

---

## 📊 Visualização de Dados

Foi realizada uma análise comparativa da média de preços por tipo de imóvel residencial.

*O gráfico abaixo (gerado via Matplotlib integrado ao Pandas) ilustra a diferença de média de valor entre tipos como Apartamentos, Casas e Casas de Condomínio.*

> *[Insira aqui uma imagem do gráfico gerado no notebook, se você o salvou como png]*

--


## 🚀 Como Executar

### Pré-requisitos
* Python 3.x
* Jupyter Notebook ou Google Colab
* Bibliotecas: `pandas`, `matplotlib`

### Instalação
```bash
# Clone este repositório
git clone [https://github.com/seu-usuario/nome-do-repositorio.git](https://github.com/seu-usuario/nome-do-repositorio.git)

# Instale as dependências
pip install pandas matplotlib
