﻿# INF1405 - Construção de Sistemas
## Professor: Edmundo Torreão

A proposta da matéria é montar um projeto a sua escolha e implementá-lo.

### Índice

 * [ O Projeto ](https://github.com/stephaniefay/inf1405#o-projeto)
 * [ Modelo ](https://github.com/stephaniefay/inf1405#modelo)
 * [ Programas Utilizados ](https://github.com/stephaniefay/inf1405#programas-eou-ferramentas-utilizadas-at%C3%A9-o-momento)
 * [ Arquivos da Pasta "media" ](https://github.com/stephaniefay/inf1405#arquivos-na-pasta-media)
 * [ Arquivos da Pasta "src" ](https://github.com/stephaniefay/inf1405#arquivos-na-pasta-src)
 * [ Save, Load & Pre-Load ](https://github.com/stephaniefay/inf1405#save-load--pre-load)

### O Projeto

A ideia é implementar um jogo estilo rogue-like onde os eventos são aleatórios e a continuidade depende da escolha do usuário. Possuirá poucos, ou nenhum, gráficos - visando a narrativa em texto e escolhas a partir do que o evento pede e o que o usuário pretende.

Haverão três ou mais personagens - alguns desbloqueáveis -, itens, side-kicks e uma história para ser seguida - não foi combinado um método de save, contudo planejo implementar - e será para apenas um jogador.

### Modelo

* Modelo de Entidade e Relacionamento feito, dentro da pasta modelo, onde descreve o esqueleto do projeto. Um possui os atributos, outro as relações.
* Diagrama de Atividades feito, também dentro da pasta modelo.

### Arquivos na pasta "media"

Os arquivos foram achados na internet com a ajuda do Google, nenhuma das imagens foi produzida por mim e os créditos vão para os devidos autores. Caso sua imagem esteja entre as citadas abaixo por favor me notifique para que eu possa deixar explícito. Infelizmente quando salvei as imagens não pensei em guardar o local original.

* [Estrela, por ???](http://static.tumblr.com/4df6c4cc48c95faa5cbcc14a01828a3a/qv6xy8l/kw3oetlc2/tumblr_static_4qezimh2iiasgogco0w0kcogk.gif)
* [Espada, por ???]( http://pixeljoint.com/files/icons/full/magic_sword.gif )
* [Floresta, por ???](http://www.animated-gifs.eu/category_nature/landscapes-forests/0016.gif)

Todos os arquivos referentes à sons, imagens, fontes e saves do jogo ficarão nessa pasta. Há imagens que não estão sendo utilizadas dentro das pastas porque em versões anteriores eu havia decidido colocá-las e eventualmente mudei de ideia. Contudo permaneceram na pasta do projeto porque não sei se vou voltar a utilizá-las.

### Arquivos na pasta "src"

ability.agc - Funções referentes às habilidades

attacks.agc - Funções referentes aos valores de ataque do personagem/inimigo

beginHandler.agc - Responsável por carregar a janela inicial (pós menu), com o efeito da máquina de escrever. Ele carrega o starterModule

character.agc - Funções referentes aos personagem

enemy.agc - Funções referentes aos inimigos

event.agc - Funções referentes aos eventos do jogo

item.agc - Funções referentes aos itens do jogo

readFromText.agc - Responsável por ler do arquivo inicial e preencher as estruturas com os itens, eventos, habilidades, inimigos e jogadores

starterModule.agc - Futuramente será o responsável por ler as informações necessárias do arquivo e inicializar as estruturas

typesDefinitions.agc - Arquivo contendo todas as estruturas de dados do jogo

### Save, Load & Pre-Load

O jogo irá ler as informações iniciais e salvar o jogo até o momento em arquivos .txt, também será implementado um "LOG", que gerará uma seed para que você possa rejogar o mesmo jogo (com os mesmos itens gerados, etc), somente se alterando caso você faça outra escolha.

Saving: dentro de media/saves terá os saves passados e o mais recente. O jogo irá salvar no arquivo toda vez que você fizer uma escolha.

Loading: dentro de media/saves ele vai ler o arquivo mais recente e carregar as informações no jogo na ultima escolha que você fez ou você poderá começar um jogo passado que vai gerar os mesmos itens e eventos novamente.

Pre-Loading: dentro da pasta media/infoGame tem um único arquivo chamado info.txt, deste ele vai carregar todas as configurações iniciais do jogo como itens, eventos, personagens disponíveis, inimigos e habilidades. Para acrescentar novos é necessário que entenda a estrutura do arquivo e altere o txt da maneira correta.

```
Abilities
	Quantidade de habilidades no arquivo (integer)
	Nome da habilidade (string)
	HP ganho com a habilidade (integer)
	Defesa ganha com a habilidade (integer)
	Ataque ganho com a habilidade (integer)
	Modificador ganho com a habilidade (integer)
	Descrição da Habilidade (string)
Events
	Quantidade de eventos no arquivo (integer)
	Se o evento possui item (bool)
	Quantidade de itens (integer) (-1 não tem itens)
	Descrição do evento (string)
	Quantidade de opções disponíveis para esse evento
	opção (string) (1)
	(...)
	opção (string) (n)
	Quantidade de inimigos (integer) (-1 não tem inimigos)
	Quantidade de cenas o evento pode aparecer (integer) (-1 não aparece em cenas)
	Index da cena (1) (integer)
	(...)
	Index da cena (n) (integer)
Items
	Quantidade de itens do arquivo (integer)
	Nome do item (string)
	Index da habilidade relacionada ao item (integer) (-1 não tem habilidade)
	Dano causado ao jogador quando pega o item (integer) (se <0 recupera a vida)
	Descrição do item (string)
	Index do evento relacionado ao item (integer) (-1 não tem evento)
Enemies
	Quantidade de inimigos no arquivo (integer)
	Quantidade de cenas que o inimigo aparece (integer) (sempre >= 1)
	Index da cena (integer) (1)
	(...)
	Index da cena (integer) (n)
	HP do inimigo (integer)
	Modificador do inimigo (integer)
	Index do evento relacionado ao inimigo (integer) (-1 não tem evento)
	Nome do inimigo (string)
	Descrição do inimigo (string)
	Quantidade de ataques que o inimigo possui (integer) (sempre >= 1)
	Valor do dano do ataque (integer) (1)
	Nome do Ataque (string)(1)
	(...)
	Valor do dano do ataque (integer) (n)
	Nome do Ataque (string) (n)
	Quantidade de falas do inimigo (integer) (sempre >=1)
	fala (string) (1)
	(...)
	fala (string) (n)
	Defesa do inimigo (integer)
Characters
	Quantidade de personagens do arquivo (integer)
	HP do personagem (integer)
	Index do item nativo do personagem (integer) (-1 não tem item)
	Index da habilidade nativa do personagem (integer) (-1 não tem habilidade)
	Nome do personagem (string)
	Descrição do personagem (string)
	Valor do ataque do personagem (integer)
	Nome do ataque do personagem (string)
	Modificador do personagem (integer)
	Defesa do personagem (integer)
```

### Programas e/ou Ferramentas utilizadas até o momento

| Nome | URL |
| ---- | --- |
| Draw.io | http://www.draw.io |
| Gif Splitter | https://ezgif.com/split |
| Git | https://git-scm.com/ |
| App Game Kit 2 | https://www.appgamekit.com/documentation/home.html |