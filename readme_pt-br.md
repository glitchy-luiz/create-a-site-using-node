<p align="center">
 <h1 align="center">Criando um site usando node</h2>
 <p align="center">Creating a site using node (and a few of nodemon)/ Criando um site usando node (e um pouco de nodemon)</p>
</p>


> **Note**
> This Read.me will be translate to english and portuguese, for to see the engish version click below
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


