## Starbucks Review NLP

NLP = Natural language processing

A idéia desse repositório é ter um modelo que analise os reviews da starbucks em texto e converter para um valor de 1 a 5 com base no histório de avaliações que contem texto e nota.

### TODO

[ ] Criar jupiter notebook com o modelo
[ ] Criar uma API para exportar a funcionalidade do modelo

### Usando o Poetry como gerenciador de pacotes

Esse projeto utilizou como gerenciador de pacotes o poetry. A documentação para utilização do Poetry encontra-se em
[https://python-poetry.org/docs/](https://python-poetry.org/docs/)

Para utilizar o poetry para gerenciar seus pacotes basta baixar o poetry com o comando no Power Shell:
``` bash
(Invoke-WebRequest -Uri https://install.python-poetry.org -UseBasicParsing).Content | python -
```

Depois de baixado, é preciso criar um projeto poetry para começar a utilizá-lo.
Para isso siga os passos abaixo:

- Abra um terminal e direcione para a pasta em que deseja iniciar o projeto poetry.

- Digite ```bash poetry -–version``` para verificar se o poetry pode ser reconhecido pela pasta em questão.

- Digite poetry new nome_do_projeto.

- Direcione para a nova pasta criada e digite poetry shell para criar um ambiente virtual poetry.

- Após criado o ambiente virtual, digite exit para sair do poetry shell

Se desejar utilizar o jupiter notebook, é necessário instalar o ipykernel.
O ipykernel pode ser instalado com o comando via terminal: 
```bash
poetry run python -m ipykernel install --user --name pymedphys
```

Ou ainda, ao abrir o projeto na sua IDE (nesse projeto utilizei o VSCode), ao tentar criar um arquivo com terminação .ipynb, o próprio VSCode pergunta se deseja instalar o pacote, se marcar que sim, a instalação é feita automaticamente.

Uma outra coisa importante é verificar se a variável de ambiente criada via o comando poetry shell pôde ser reconhecida pela IDE. 

Depois de instalado o ipykernel, vai ser necessária a instalação de alguns pacotes. Isso é possível abrindo um terminal.
Ao digitar poetry shell, você habilita o shell para executar comandos python.

Agora para instalar os pacotes basta digitar no terminal:
```bash
poetry add nome_do_pacote
```

### About Spacy and Poetry

Para usar o Spacy como pacote de Processamento de Linguagem Natural é necessário fazer o download do modelo treinado. 
Para fazer o download do modelo treinado com Poetry basta ir na web page de documentação do Spacy [https://spacy.io/usage#quickstart](https://spacy.io/usage#quickstart)
e procurar o idioma em que se quer trabalhar. Há várias opções de idioma e algumas opções de modelos mais simples e com mais acurácia.
Escolha o modelo ideal e procure o link para download na web page [https://github.com/explosion/spacy-models/releases/](https://github.com/explosion/spacy-models/releases/)
Modifique o arquivo pyproject.toml acrescentando a dependência desejada. 
No projeto em questão, o modelo treinado escolhido foi o en_core_web_trf, e sua URL para download foi:
https://github.com/explosion/spacy-models/releases/download/en_core_web_trf-3.7.1/en_core_web_trf-3.7.1.tar.gz

Logo, foi acrescentado no arquivo de terminação .toml o seguinte:
en_core_web_trf = {url = "https://github.com/explosion/spacy-models/releases/download/en_core_web_trf-3.7.1/en_core_web_trf-3.7.1.tar.gz"}

Após essa etapa, rode em um terminal o seguinte comando:

```bash
poetry add https://github.com/explosion/spacy-models/releases/download/en_core_web_trf-3.7.1/en_core_web_trf-3.7.1.tar.gz
```
Após realizada essa etapa, o modelo treinado estará disponível para ser utilizado.
