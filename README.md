git clone https://github.com/hellyneandrade/atlas-minerario-brasil.git
[README.md](https://github.com/user-attachments/files/33977218/README.md)
# Atlas Minerário Brasil

**Mapa interativo dos processos minerários da ANM, por estado, fase e substância.**

![status](https://img.shields.io/badge/status-em%20desenvolvimento-yellow)
![python](https://img.shields.io/badge/python-3.10%2B-blue)
![license](https://img.shields.io/badge/license-MIT-green)

> 🚧 Projeto em desenvolvimento. Começando por Pernambuco e expandindo para os demais estados.

## Sobre o projeto

O Atlas Minerário Brasil transforma dados abertos da Agência Nacional de Mineração (ANM) em mapas interativos que rodam direto no navegador. A ideia é facilitar a leitura de quem tem direitos minerários onde, em que fase está cada processo e qual substância é objeto de cada título.

O projeto une duas áreas: **mineração** (interpretação dos processos e das fases) e **análise de dados geoespaciais** (Python, GeoPandas e Folium).

## Funcionalidades

- [x] Leitura e exploração do shapefile de processos minerários (SIGMINE/ANM)
- [ ] Filtro por estado, fase e substância
- [ ] Mapa interativo com Folium (tooltips e popups com dados do processo)
- [ ] Cores por substância
- [ ] Camada de geologia do SGB/CPRM
- [ ] Publicação no GitHub Pages

## Fontes de dados

| Fonte | O que oferece | Onde encontrar |
|---|---|---|
| **ANM / SIGMINE** | Poligonais dos processos minerários | Portal gov.br/anm → Acesso à Informação → Dados Abertos |
| **SGB/CPRM (GeoSGB)** | Geologia, ocorrências minerais e outros dados | geosgb.sgb.gov.br |

> Os endereços dos portais mudam com frequência. Se um link não abrir, busque pelo nome da base.
> Os dados brutos **não** são versionados neste repositório (pasta `data/` no `.gitignore`). Baixe-os diretamente das fontes oficiais.

## Entendendo as fases dos processos

Cada processo minerário passa por etapas administrativas na ANM. As principais:

| Fase | O que significa |
|---|---|
| **Requerimento de pesquisa** | A área foi solicitada, mas a pesquisa ainda não foi autorizada. |
| **Autorização de pesquisa** | A empresa pode pesquisar a área para avaliar se existe jazida. |
| **Requerimento de lavra** | A pesquisa foi concluída e o titular pediu o direito de explorar. |
| **Concessão de lavra** | Direito de extrair o minério concedido (a mina pode operar). |
| **Licenciamento** | Regime simplificado, usado para certos minerais de uso na construção civil. |
| **Lavra garimpeira** | Regime específico para garimpo. |
| **Disponibilidade** | Área liberada, que pode ser requerida novamente. |

Os nomes exatos das fases variam na base de dados, então confira os valores reais com `value_counts()` ao explorar o arquivo.

## Tecnologias

- Python 3.10+
- [GeoPandas](https://geopandas.org/): leitura e manipulação de dados geoespaciais
- [Folium](https://python-visualization.github.io/folium/): mapas interativos (Leaflet)
- Pandas e Jupyter

## Como rodar

```bash
# 1. Clonar o repositório
git clone https://github.com/SEU-USUARIO/atlas-minerario-brasil.git
cd atlas-minerario-brasil

# 2. Criar e ativar o ambiente virtual
python -m venv venv
venv\Scripts\activate          # Windows
# source venv/bin/activate     # Mac/Linux

# 3. Instalar as dependências
pip install geopandas folium pandas jupyter

# 4. Baixar o shapefile da ANM e colocar na pasta data/
#    (exemplo: data/processos_PE.shp)

# 5. Abrir o notebook e executar célula por célula
jupyter notebook
```

> Se a instalação do GeoPandas der problema no Windows, uma alternativa é usar o [Anaconda](https://www.anaconda.com/).

## Estrutura do projeto

```
atlas-minerario-brasil/
├── data/          # arquivos baixados (não versionados)
├── notebooks/     # exploração (.ipynb)
├── src/           # scripts finais
├── output/        # mapas gerados (.html)
├── README.md
└── .gitignore
```

## Roteiro

1. Ler o shapefile e explorar as colunas
2. Filtrar por estado, fase e substância
3. Gerar o primeiro mapa
4. Colorir por substância, adicionar popups e filtros
5. Adicionar a camada de geologia do SGB
6. Documentar e publicar no GitHub Pages

## Limitações

- Os dados refletem a data de download do arquivo; a ANM atualiza as bases periodicamente.
- A visualização mostra a situação cadastral dos processos e não substitui consulta oficial ao Cadastro Mineiro da ANM.

## Licença

Distribuído sob a licença MIT. Veja o arquivo `LICENSE`.

## Autor

**Seu Nome**
[LinkedIn](https://www.linkedin.com/in/SEU-PERFIL) · [GitHub](https://github.com/SEU-USUARIO)

---

*Dados: Agência Nacional de Mineração (ANM) e Serviço Geológico do Brasil (SGB/CPRM), disponibilizados como dados abertos.*
