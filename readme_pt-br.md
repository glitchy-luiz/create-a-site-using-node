<p align="center">
 <h1 align="center">Criando um site usando node</h2>
 <p align="center">Creating a site using node (and a few of nodemon)/ Criando um site usando node (e um pouco de nodemon)</p>
</p>


> **Note**
> This Read.me will be translate to english and portuguese, for to see the english version click below
<p align="center">
    <a href="README.md">English</a>
</p>


## Introdução
Oie, vou tentar explicar como criar um site no visual studio code usando o sistema node passo a passo.
Primeiramente vou tentar ensinar o que significa cada coisa que irei mostrar, porém caso você já entenda de node e só quer relembrar alguns tópicos, mais pra frente vou dar um resumo pronto para ser colado no seu vscode. 

use este readme como quiser, mas quero deixar bem avisado que sou apenas um aluno de front/back-end então não sou qualificado para ensinar nada, mas caso tenha alguma dúvida vou tentar responde-lá na aba wiki assim que eu cria-lá, e pelo discord : )

# Primeiros passos
Vou partir do ponto de que você já tenha o visual studio code e o node instalado na sua máquina, caso não tenha o node, basta ir neste site e seguir as especificações que preferir https://nodejs.org/pt-br/
<a align="center">
 ![image](https://user-images.githubusercontent.com/84513178/209035679-1ecaccb3-7f33-49bb-aea3-a1055c8abea3.png)
 </a>
Assim que baixar o node, abra o vscode para começar

## 1- Abra o terminal (Ctrl + ") e cole estes comandos:
Cole eles um de cada vez e apertando a tecla enter entre eles

```md
npm init -y
```
```md
npm i express ejs mongoose consign multer -s
```
```md
npm i nodemon -D
```

Se tudo estiver correto, vai aparecer um arquivo package.json


Esses comandos servem para instalar alguns pacotes que iremos usar, sendo o "i" a abreviação de install, e os sufixos finais significam:

-y = instalar no projeto 

-s = instalar na máquina

-D = instalar como administrador

## 2- Abra o arquivo package.json que foi criado e digite:

```md
"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "node app",
    "dev": "nodemon app"
  },
```

(digite em cima das dependencias)

E mude o main o "index.ejs" para "app.ejs", ou pra qualquer que seja o nome do seu arquivo principal, nesse caso irei usar o app.ejs

## 3- Crie as pastas

Essas são as pastas principais para o projeto funcionar por completo:
<li>
Views
</li>
<li>
Assets
</li>
<li>
Config
</li>
<li>
Models
</li>
<li>
Routes
</li>


E depois crie esse arquivo separado das pastas, ou seja, na pasta raiz:


<li>
 App.js
 </li>
 
 ## 4- Dentro da pasta "Config" crie o arquivo "servidor.js" e escreva:
 
```md
const express = require('express')
const app = express()

const porta = process.env.PORT || 3535

app.use(express.urlencoded({extended:false}))

app.use(express.static("./assets/"))

module.exports={app,porta} 
```

A const express que criamos server para chamar um dos pacotes que baixamos anteriormente (no caso, o próprio express).

E a const app serve para executar o pacote 


A const porta está ligando um servidor em um localhost, que é um servidor próprio da sua máquina, que pode ser aberto em qualquer navegador

>**Warning**
>O número 3535 é o número do localhost, você pode colocar o número de 4 digitos que quiser, MAS você não pode ter 2 projetos abertos na mesma porta ao mesmo tempo


## 5- Dentro da pasta "Views" crie um arquivo "index.ejs"

(pode ser qualquer nome obviamente) e dentro dele crie a base de um HTML (! + TAB). Caso mude o nome do arquivo, lembre-se de mudar o arquivo que será direcionado na routes 

E para deixar claro, a diferença entre um HTML e um EJS é básicamente a forma em que conseguimos implementar o front-end e o back-end no mesmo arquivo, mas de resto eles funcionam igualmente

## 6- Dentro da pasta "Routes" crie um arquivo chamado "index.js" e colar:

```md
module.exports= (app)=>{

app.get('/',(req,res)=>{
   res.render('index.ejs')
})
}
```

A pasta Routes, como o nome já diz, é onde vamos criar as rotas que serão usadas para acessar nossas páginas. Como no exemplo acima, nós dizemos que a rota padrão "/" vai renderizar a página "index.ejs"

## 7- Dentro do arquivo "App.js" que está fora das pastas digite:

```md
//const servidor = require('./config/servidor')
//const app = servidor.app
//const porta = servidor.porta

//para facilitar coloque:
const {app,porta} = require('./config/servidor')

//este consign pode estar ai, no servidor, e no app se quiser
const consign = require('consign') 
consign().include('./routes').into(app)

app.listen(porta)
```

As linhas que tem // no começo são cometários para facilitar a entender como funciona o código

O consign que está chamando o pacote consign faz com que ele crie rotas automáticas


### Em resumo, já está tudo pronto
>agora abra o terminal e escreva "node app" ou "nodemon app" no terminal, e no seu navegador escreva localhost:"numero da porta". 
> Por enquanto o site está em branco, mas isso é porque não temos nada no front-end, mas o projeto já está funcionando
>E agora, vamos continuar com alguns detalhes a mais que podem ajudar a melhorar seu projeto


* * *


## 8- Para fazer um banco de dados, vá na pasta config e crie o arquivo "database.js" e escreva:

Aqui nós vamos usar um banco de dados NoSQL chamado de mongoose, para usa-lo é preciso criar uma conta gratuita no site do mongo DB atlas. E também pode ser util instalar o mongo compass, mas isso não é obrigatório
```md
const mongoose = require('mongoose')

const conexao = async()=>{
    const atlas = await mongoose.connect('link do mongo')
}

module.exports = conexao
```

Fazer o login e pegar o link do mongo pode ser complicado, mas não quero me focar nisto
