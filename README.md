function setup() {
  createCanvas(400, 400);
}

function draw() {
  background(220);
}

let tela = 0;

let perguntaAtual = 0;
let pontos = 0;
let agua = 0;

let gotas = [];

let perguntas = [

{
pergunta:"Qual atitude ajuda a economizar água?",
opcoes:["Guardar água da chuva","Deixar a torneira aberta"],
correta:0
},

{
pergunta:"A água da chuva pode ser usada para:",
opcoes:["Regar plantas","Tomar banho"],
correta:0
},

{
pergunta:"O que prejudica o meio ambiente?",
opcoes:["Reutilizar água","Escovar os dentes com a torneira aberta"],
correta:1
},

{
pergunta:"Qual é uma prática sustentável?",
opcoes:["Consertar vazamentos","Lavar calçada diariamente"],
correta:0
},

{
pergunta:"Produzir alimentos com responsabilidade significa:",
opcoes:["Economizar recursos","Gastar água sem controle"],
correta:0
}

];

function setup(){

createCanvas(1000,600);

textAlign(CENTER);

for(let i=0;i<30;i++){
gotas.push(new Gota());
}

}

function draw(){

if(tela==0) blog();

if(tela==1) inicio();

if(tela==2) quiz();

if(tela==3) jogo();

if(tela==4) final();

}

function blog(){

background(220,240,255);

fill(0,100,180);
textSize(36);

text(
"💧 REUTILIZAÇÃO DA ÁGUA 💧",
width/2,
50
);

fill(0);

textSize(18);

text(
"Produção de Alimentos e Meio Ambiente",
width/2,
90
);

textAlign(LEFT);

textSize(18);

text(
"A água é um dos recursos naturais mais importantes para a vida no planeta. "+
"Ela é essencial para o consumo humano, para a produção de alimentos e para a manutenção dos ecossistemas.\n\n"+

"Com o aumento da população e do consumo, a preservação desse recurso tornou-se um grande desafio. "+
"Por isso, reutilizar a água é uma atitude sustentável que ajuda a reduzir desperdícios e a garantir que esse recurso esteja disponível para as futuras gerações.\n\n"+

"No campo, a água da chuva pode ser armazenada e utilizada para irrigar plantações, limpar equipamentos e auxiliar em diversas atividades agrícolas. "+
"Essa prática diminui o consumo de água potável e contribui para uma produção de alimentos mais consciente.\n\n"+

"Além disso, pequenas ações do dia a dia, como consertar vazamentos, fechar a torneira ao escovar os dentes e reaproveitar água sempre que possível, fazem uma grande diferença para o meio ambiente.\n\n"+

"Neste projeto, você irá aprender mais sobre a importância da reutilização da água por meio de um quiz educativo e de um jogo interativo. "+
"Seu desafio será coletar água da chuva, aumentar sua pontuação e ajudar uma árvore a crescer saudável, mostrando como o uso responsável da água contribui para a preservação da natureza.",
80,
150
);

fill(255);
  
  fill(0,180,0);

rect(width/2-120,500,240,60,15);

fill(255);

textSize(28);


textAlign(CENTER);

text(
"CONTINUAR",
width/2,
540
);

}

function inicio(){

background(120,200,255);

fill(255);

textSize(42);

text(
"💧 ÁGUA E SUSTENTABILIDADE 💧",
width/2,
120
);

fill(0);

textSize(24);

text(
"Teste seus conhecimentos",
width/2,
220
);

fill(0,180,0);

rect(width/2-120,320,240,70,15);

fill(255);

textSize(30);

text(
"INICIAR QUIZ",
width/2,
365
);

}

function quiz(){

background(230);

fill(0);

textSize(32);

text(
"QUIZ DA ÁGUA",
width/2,
80
);

let p = perguntas[perguntaAtual];

textSize(24);

text(
p.pergunta,
width/2,
160
);

fill(50,150,255);

rect(250,250,500,60,10);

fill(255);

text(
p.opcoes[0],
width/2,
290
);

fill(255,120,120);

rect(250,350,500,60,10);

fill(255);

text(
p.opcoes[1],
width/2,
390
);

fill(0);

textSize(18);

text(
"Pontos: "+pontos,
width/2,
500
);

text(
"Pergunta "+(perguntaAtual+1)+" de 5",
width/2,
540
);

}

function jogo(){

background(180,230,255);

fill(0);

textSize(28);

text(
"🌧️ COLETE ÁGUA DA CHUVA",
width/2,
50
);

textSize(20);

text(
"Pontos: "+pontos,
100,
100
);

text(
"Água: "+agua+"/100",
850,
100
);

desenharArvore();

fill(100,70,30);

rect(
mouseX-50,
height-50,
100,
20
);

for(let g of gotas){

g.cair();

g.mostrar();

if(
g.y>height-50 &&
g.x>mouseX-50 &&
g.x<mouseX+50
){

agua++;

pontos++;

g.resetar();

}

}

}

function desenharArvore(){

let nivel = min(agua,100);

fill(120,80,40);

rect(470,350,60,170);

fill(0,180,0);

ellipse(
500,
320,
nivel+50,
nivel+50
);

if(nivel>20)
ellipse(450,340,nivel,nivel);

if(nivel>40)
ellipse(550,340,nivel,nivel);

if(nivel>60)
ellipse(500,260,nivel,nivel);

if(nivel>80)
ellipse(440,260,nivel,nivel);

if(nivel>90)
ellipse(560,260,nivel,nivel);

fill(0);

textSize(18);

text(
"🌳 Crescimento da Árvore: "+nivel+"%",
500,
560
);

if(agua>=100){

tela=4;

}

}

function final(){

background(200,255,200);

fill(0,150,0);

textSize(40);

text(
"🏆 PARABÉNS! 🏆",
width/2,
120
);

fill(0);

textSize(24);

text(
"Você economizou água e ajudou a natureza.",
width/2,
220
);

text(
"Pontuação Final: "+pontos,
width/2,
300
);

text(
"🌳 Sua árvore cresceu totalmente!",
width/2,
360
);

text(
"Produzir alimentos de forma sustentável protege o futuro.",
width/2,
430
);

}

function mousePressed(){

if(tela==0){

if(
mouseX>width/2-120 &&
mouseX<width/2+120 &&
mouseY>500 &&
mouseY<560
){

tela=1;

}

}

else if(tela==1){

if(
mouseX>width/2-120 &&
mouseX<width/2+120 &&
mouseY>320 &&
mouseY<390
){

tela=2;

}

}

else if(tela==2){

let p = perguntas[perguntaAtual];

if(
mouseX>250 &&
mouseX<750 &&
mouseY>250 &&
mouseY<310
){

if(p.correta==0){

pontos+=10;

}

proximaPergunta();

}

if(
mouseX>250 &&
mouseX<750 &&
mouseY>350 &&
mouseY<410
){

if(p.correta==1){

pontos+=10;

}

proximaPergunta();

}

}

}


function proximaPergunta(){

perguntaAtual++;

if(perguntaAtual>=5){

tela=3;

}

}

class Gota{

constructor(){

this.resetar();

}

resetar(){

this.x=random(width);

this.y=random(-600,0);

this.vel=random(3,8);

}

cair(){

this.y+=this.vel;

if(this.y>height){

this.resetar();

}

}

mostrar(){

fill(0,100,255);

ellipse(
this.x,
this.y,
12,
18
);

}

}# Agrinho---Sustentabilidade2026
