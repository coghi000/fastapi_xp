<h1 align="center">Call of Predict</h1>

<h2>Descrição</h2>
<p>Este projeto é um case de solução proposto pela XP Inc. Nós iremos implementar uma API REST para testar um modelo de machine learning que prevê a presença de diabetes com base em características médicas dos pacientes. Optei por utilizar este dataset, por ele ser mais completo e parte do desafio proposto.</p>

<p>A API será desenvolvida com FastAPI e estará disponível para receber requisições HTTP. Utilizaremos o Postman para testar as requisições e validar a funcionalidade da API.</p>
<h2>Objetivos do Projeto</h2>
<ul>
  <li>Criar uma API que possa receber dados de entrada e retornar previsões.</li>
  <li>Garantir que a API esteja em funcionamento e acessível através de endpoints específicos.</li>
  <li>Facilitar o teste das requisições utilizando o Postman.</li>
</ul>

<h2>Tecnologias</h2>
<ul>
  <li>Python: Nossa principal linguagem de programação</li>
  <li>FastAPI: A API mais veloz do velho oeste</li>
  <li>Postman: O mais famoso que o "Starman" de David Bowie, para realizarmos o nosso teste das requisições</li>
  <li>Docker: A mobidick da nossa aplicação</li>
  <li>MLFlow: Machine Learning Operation, o nosso monitoramento do modelo.</li>
</ul>

<h2>Requisitos</h2>
  <h3>Instalando Docker</h2>
<p> Neste passo vamos instalar o famoso Docker, e para que isso seja possivel, é necessário que você siga a a documentação e faça a instalação de acordo com o seu sistema operacional.</p>
 <a href=https://learn.microsoft.com/pt-br/virtualization/windowscontainers/manage-docker/configure-docker-daemon> Windows</a>
 <br>
 <a href=https://docs.docker.com/desktop/install/linux-install/>Linux</a>
 <br>
 <a href=https://docs.docker.com/desktop/install/mac-install/>Mac</a>
 <br>

 <h3>Instalando Python e Github</h3>
 <p>Guia de instalação da nossa plataforma de versionamento de codigo</p>
<a href=https://github.com/git-guides/install-git>GitHub</a>

 <h3>Instalando VSCode</h3>
<p>A IDE utilizada neste projeto é o "VSCode", por ser uma IDE mais interativa com a nossa aplicação e suas extensões. Mas você pode utilizar outra IDE de sua escolha.</p>

 <a href=https://code.visualstudio.com/download> Windows</a>
  <br>
  <a href=https://code.visualstudio.com/download/>Linux</a>
  <br>
  <a href=https://code.visualstudio.com/download/>Mac</a>
  
<p>Após seguir o tutorial de instalação do Docker e do VSCode, você vai na coluna a esquerda do seu VSCode e clique na opção "Extensions" e digite "Docker"</p>

   ![docker](https://brianchristner.io/content/images/2019/03/vs-code-docker-2.png)
<p>Logo em seguida você "Instala" esta extensão para que possa facilitar o teste da nossa aplicação.Você pode estar utilizando outras extensões tambem, seja para python ou outras aplicações.</p>


<h1>Mão na Massa</h1>
  <p>Após a instalação de todos os requisitos, vamos testar a aplicação, vá em um diretorio de sua preferencia e de o seguinte comando:</p>
        <p>git clone https://github.com/coghi000/fastapi_xp.git</p>

<p>Depois de dar este comando o projeto ira estar em sua maquina. Descompate o arquivo "fast_api_cm.zip" no diretorio de sua escolha e abra o projeto utilizando o vscode.Vá até a pasta "notebooks" e abra um terminal e digite o comando abaixo</p>
  
    docker build -t meu_jupyter_imagem -f dockerfile.jupyter .

<p>Depois de ter construirmos a imagem, agora vamos rodar ela.</p>

    docker run -v $(pwd)/../notebooks:/FAST_API_CM -p 8888:8888 -p 5010:5010 meu_jupyter_imagem

<p>Para acessar o notebook entre no link </p>

  <a href=http://localhost:8888/tree?>Jupyter</a>

 <p>Rode o nosso notebook "codigo_diabetes", este codigo ele treina um modelo utilizando um dataset de diabetes, chamado "Pima Indians", é um dataset relativamente grande e bem legal, onde classifica pessoal com diabetes ou não, nele eu utilize o modelo de "Random Forestes", que é o mais indicado para este dataset por justamente ele criar, varios sub-conjuntos  e no final ele gera um modelo unico. Tambem estamos utilizando "GridSearch" para colocar  hiperparâmetros para maximizar o desempenho do modelo e tambem o nosso "MLFlow" para que possamos ver as predições, estado de vida, e outros status do nosso modelo e o quanto de curacia que ele tem.</p>

 <p>Depois de criar o nosso modelo, você pode estar acessando o MLFlow:</p>
 <a href=http://0.0.0.0:5010 >MLFlow</a>

  



  
  


   
