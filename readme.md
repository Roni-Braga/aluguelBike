## Projeção de Mercado para alugueis de Bicicletas
Olá Seja Bem vindo, vamos colocar em prática o que aprendemos no Bootcamp para <b>certificação da Microsoft IA-900</b>. Neste modelo de aprendizado de máquina, vamos criar e testar um modelo.

### Ferramentas

![Azure](https://img.shields.io/badge/azure-%230072C6.svg?style=for-the-badge&logo=microsoftazure&logoColor=white)
![Visual Studio Code](https://img.shields.io/badge/Visual%20Studio%20Code-0078d7.svg?style=for-the-badge&logo=visual-studio-code&logoColor=white)

### Plataformas

![Microsoft](https://img.shields.io/badge/Microsoft-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)
### Provisionando o Espaço de trabalho do Aprendizado de Máquina:

1- Vamos entrar no <a href="https://portal.azure.com/" target="__blank">portal do Microsoft Azure</a>, lembre-se temos que fazer o login com usuário e senha.<br>
2 - No menu lateral esquerdo, clique em <b>create resource</b> (criar um recurso).<br>
3 - Na barra de pesquisa digite "machine learning", logo após, clique em create logo abaixo de Azure Machine Learning.<br>
4- Todo recurso pertence há um grupo, então na próxima página vá ate o <b>Resource Group</b>, selecione um grupo já existente ou crie um caso.<br>
5- Crie também um nome para o WorkSpace, lembro que, tudo está sendo preenchido conforme a  <a href="https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/01-machine-learning.html" target="__blank">documentação oficial</a><br>
6 -Tudo preenchido clique em <b>review + create</b>, passando na Validação, podemos prosseguir.<br>
7 - Temos que aguardar o término de todo o desenvolvimento. Uma vez finalizado, clique em <b>go to resource</b> (vamos para o recurso) e depois clique em <b>launch studio</b>. Logo em seguida ele vai abri o <b>Machine Larning Studio.</b><br>

<b>Obs: Nos campos de região, conta, chaves, registro de container devemos deixar o valor default</b>

### Treinando o Modelo 

1 - Dentro do <b>Machine Learning Studio</b>, no menu do lado esquerdo, clique em <b>Automated ML</b>, em seguida <b>New Automated job ml.</b><br>
2 - Preenchar todos os dados como: Job name, New experiment name, Description. Lembrando que na documentação tem um exemplo de como preencher. Depois de preenchido clique em próximo<br>
3 - Coloque o tipo da tarefas e seus dados. No nosso caso será uma tarefa de regressão.<br>
4 - Selecione quais serão os nosso dados, primeiro vamos preencher os campos name, descrição, type. depois de avançar, devemos indicar onde estão os dados, seja em um WebService, Arquivo SQL.No nosso caso vamos selecionar Arquivos da Web e colocamos a url.<br>
5 - Em configurações troque somente o campo Column headers seleciona a opção, Somente o primeiro arquivo tem cabeçalho.<br>
6 - Em Schema (esquema) habilite a primeira opção para incluir todas as colunas em caminhos diferentes e clique em próximo e logo depois criar.<br>
7 - Em Task type &  data (tipo de tarefas e dados) selecione  tarefa que acabou de criar e clique em próximo.
8 - Em Target Column (coluna de destino) selecione a rentals integer.<br>
9 - logo em seguida, em configurações adicionais, selecione Erro quadrático médio da raiz normalizada, desmarque todos os checkbox.<br>
10 - Em modelos permitidos, selecione somente o RandomForest e LightGBM.<br>
11 - Em limites:
    <ul>
        <li>máximo de tentativas: 3</li>
        <li>máximo de tentativas simultâneas: 3</li>
        <li>nós máximos: 3</li>
        <li>pontuação métrica: 15</li>
        <li>Tempo limite: 15</li>
        <li>Tempo limite de iteração: 15</li>
        <li>Habilitar rescisão antecipada: Selecione está opção</li>
    </ul>
 <br>
12 - Em validação e teste, selecione o tipo para Divisão de validação e treinamento, logo em seguida, clique em avançar.<br>
13 - clique em próximo e depois em enviar trabalho de treinamento, vamos aguardar a execução.

### Implantar o Modelo 

1 - Na guia modelo, selecione implementar e escolha a opção Serviço Web<br>
2 - Informe os seguintes dados:       
    <ul>
        <li>Nome: predict-rentals</li>
        <li>Descrição: Prever aluguéis de ciclos</li>
        <li>Tipo de computação: Instância de Contêiner do Azure</li>
        <li>Habilitar autenticação: selecione está opção </li>
    </ul>
3 - Após finalizar a implantação, use nosso arquivo.json para testar nosso modelo.

