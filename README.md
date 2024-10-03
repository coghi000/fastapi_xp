<h1 align="center">Predict API</h1>

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

 <h3>Instalando Github</h3>
 <p>Guia de instalação da nossa plataforma de versionamento de codigo</p>
 <br>
<a href=https://github.com/git-guides/install-git>GitHub</a>
 <br>
 <h3>Instalando Postman</h3>
   
 <p>Guia de instalação da nossa ferramenta de teste para API</p>
<a href=https://www.postman.com/downloads/>Postman</a>

 <h3>Instalando VSCode</h3>
<p>A IDE utilizada neste projeto é o "VSCode", por ser uma IDE mais interativa com a nossa aplicação e suas extensões. Mas você pode utilizar outra IDE de sua escolha.</p>

 <a href=https://code.visualstudio.com/download> VSCODE</a>
  <br>
  
<p>Após seguir o tutorial de instalação do Docker e do VSCode, você vai na coluna a esquerda do seu VSCode e clique na opção "Extensions" e digite "Docker"</p>

   ![docker](https://brianchristner.io/content/images/2019/03/vs-code-docker-2.png)
<p>Logo em seguida você "Instala" esta extensão para que possa facilitar o teste da nossa aplicação.Você pode estar utilizando outras extensões tambem, seja para python ou outras aplicações.</p>


<h1>Mão na Massa</h1>
  <p>Após a instalação de todos os requisitos, vamos testar a aplicação, vá em um diretorio de sua preferencia e de o seguinte comando:</p>

      git clone https://github.com/coghi000/fastapi_xp.git
<br>

<p>Depois de dar este comando o projeto ira estar em sua maquina. Descompate o arquivo "fast_api_cm.zip" no diretorio de sua escolha e abra o projeto utilizando o vscode.Vá até a pasta "notebooks" e abra um terminal e digite o comando abaixo</p>
  
    docker build -t meu_jupyter_imagem -f dockerfile.jupyter .

<p>Depois de ter construirmos a imagem, agora vamos rodar ela.</p>

    docker run -v $(pwd)/../notebooks:/FAST_API_CM -p 8888:8888 -p 5010:5010 meu_jupyter_imagem

<p>Para acessar o notebook entre no link </p>

  <a href=http://localhost:8888/tree?>Jupyter</a>

 <p>Rode o nosso notebook "codigo_diabetes", este codigo ele treina um modelo utilizando um dataset de diabetes, chamado "Pima Indians", é um dataset relativamente grande e bem legal, onde classifica pessoal com diabetes ou não, nele eu utilize o modelo de "Random Forestes", que é o mais indicado para este dataset por justamente ele criar, varios sub-conjuntos  e no final ele gera um modelo unico. Tambem estamos utilizando "GridSearch" para colocar  hiperparâmetros para maximizar o desempenho do modelo e tambem o nosso "MLFlow" para que possamos ver as predições, estado de vida, e outros status do nosso modelo e o quanto de curacia que ele tem.</p>

 <p>Depois de criar o nosso modelo, você pode estar acessando o MLFlow e visualizar a curacia do modelo, clicando em "Diabetes" e ir na aba "Modem Metrics" e para ver mais detalhes, dos pacotes que foram instalados e o input de entrada, pode estar indo na aba "Artifacts" tambem.:</p>
 
 <a href=http://0.0.0.0:5010 >MLFlow</a>

 <p>Agora que ja treinamos o nosso modelo, vamos colocar a nossa "FastAPI" para rodar e para isso, precisamos ir na raiz do nosso projeto e abrir outro terminal e executar este comando de "Docker":</p>

     docker build -t fast_api_final -f dockerfile .
  
<p>E para rodar:</p>

     docker run -p 8000:8000 fast_api_final
<p>Por ultimo vamos testar a nossa API, utilizando o famoso "Postman", para ver se esta tudo funcionando.</p>

<p> Abra o seu postman e coloque o link de teste "http://localhost:8000/api/health" e verifique ao lado esquerdo do link se a caixa de opções esta no modo "GET", se estiver clique no botao "Send", após este processo ele vai aparecer na aba "Body" na parte de baixo, a seguinte mensagem "Estou saudável", se ele aparecer é por que a API esta funcionando corretamente.</p>
      
      
![Captura de tela de 2024-10-03 07-10-12](https://github.com/user-attachments/assets/d56d9379-9e5e-4027-bfa6-72ddbb7d8715)

<p>Agora e por ultimo testaremos o nosso famoso modelo e para isso, cliquei no sinal de "+" logo a cima da barra onde você coloca o link de teste ou se preferir na parte superior a esquerda, você pode clicar em "New" que uma nova aba irá abrir, após isso você pode estar colocando o seguinte link "http://localhost:8000/api/predict" e na caixa de opções do lado esquerdo, você pode estar trocando para o metodo "POST", veja que logo abaixo temos uma aba chamada "Body" clique nela e selcione a opção "Raw", apos isso no lado direito vai ter uma opção "Text", você precisa troca-lá para a opção "Json". Para testar cole o json de teste.</p>


    {"preg_count": 2, "glucose": 653, "blood_pressure": 15, "skin_thickness": 20, "insulin": 1, "bmi": 30.1, "diabetes_pedigree": 0.5, "age": 30}
  
  
  <p> E depois clique em "Send" e veja o resultado do nosso modelo.</p>

![image](https://github.com/user-attachments/assets/8a5376ef-5ec3-4a6c-b827-1ab3dcdfc160)

<br>

<p>Sinta-se à vontade para testar o código com diferentes valores de entrada e explorar os resultados. Aproveite para entender como o modelo se comporta e fique à vontade para sugerir ou implementar melhorias. Toda contribuição é bem-vinda!</p>


