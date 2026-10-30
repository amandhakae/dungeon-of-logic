Dungeon of Logic
> RPG de puzzle matemático em 2D, feito com **Godot 4.7**.
Você é um aprendiz de mago que desce a uma masmorra para recuperar os Números Sagrados roubados por Caos. Em cada batalha, o HP do monstro é um número: monte uma equação com as cartas e os operadores disponíveis para alcançá-lo (ou ultrapassá-lo) antes que o tempo acabe.
Equipe: Amandha Kae Nakasone Watanabe, Ana Julia Soares Vicente, Gustavo Silveira Necal, Sofia Cristina da Silva.
Instituição: Centro Universitário Católica de Santa Catarina — Engenharia de Software.
---
Sumário
Requisitos
Instalação
Execução
Como jogar
Progressão das fases
Controles
Estrutura do repositório
Gerar o executável (opcional)
Problemas comuns
---
Requisitos
Windows 10/11 (64 bits) — plataforma do executável e do preset de exportação.
Godot Engine 4.7 (versão padrão, não a .NET). Gratuito e não exige instalação: basta extrair o `.zip`.
Git para clonar o repositório (ou baixe o ZIP pelo botão Code → Download ZIP no GitHub).
Placa de vídeo com suporte a OpenGL (o projeto usa o renderizador GL Compatibility).
Instalação
```bash
git clone https://github.com/<USUARIO>/<REPOSITORIO>.git
cd <REPOSITORIO>
```
> Substitua `<USUARIO>/<REPOSITORIO>` pelo endereço real deste repositório.
Execução
Opção A — Pelo editor Godot (recomendado)
Abra o Godot 4.7. Na tela inicial, clique em Importar.
Selecione o arquivo `project.godot` que está na raiz do projeto clonado e confirme.
Com o projeto aberto, pressione F5 (ou o botão ▶) para jogar.
A cena inicial é `scenes/Main.tscn` (menu → história → jogo).
> Na primeira abertura o Godot reimporta as imagens da pasta `assets/`; isso pode levar alguns segundos.
Opção B — Executável pronto (Windows)
Se o executável estiver disponível na aba Releases do repositório:
Baixe e extraia o arquivo da release.
Dê dois cliques em `Dungeon of Logic.exe`.
(`Dungeon of Logic.console.exe` abre o mesmo jogo com uma janela de console para depuração.)
> O Windows pode exibir o aviso do SmartScreen por o executável não ser assinado. Clique em **Mais informações → Executar assim mesmo**.
Como jogar
No menu, clique em JOGAR e avance pela história (botão CONTINUAR ou `Enter`/`Espaço`) até COMEÇAR AVENTURA.
Os monstros entram andando, um de cada vez, pela direita. Quando chegam até você, a batalha começa automaticamente.
Cada monstro tem um HP (um número). Você tem 5 cartas com números e os operadores liberados na fase atual.
Monte uma equação clicando nas cartas e operadores e pressione ATACAR:
Resultado igual ao HP → acerto perfeito.
Resultado maior que o HP → combo aritmético; pode ainda devolver +1 coração.
Resultado menor que o HP, expressão inválida ou resultado não inteiro → você perde 1 coração.
Você tem 30 segundos por batalha (22 s no chefe final). Se o tempo acabar, também perde 1 coração.
Você começa com 3 corações. Se chegarem a zero, é GAME OVER.
Cada monstro derrotado se transforma em um Número Sagrado. Recupere os 10 e derrote o Demônio do Caos para vencer.
Ao final, pressione R para recomeçar.
Progressão das fases
Fase	Nome	Operadores liberados
1	Celas Iniciais	`+` `-`
2	Salões de Multiplicação	`+` `-` `×`
3	Câmaras de Divisão	`+` `-` `×` `÷`
4	Sala do Caos	`+` `-` `×` `÷` `(` `)`
Final	Forma Verdadeira do Caos	todos, com menos tempo
As fases 1 a 3 têm 3 monstros cada.
No chefe Caos, o HP muda constantemente durante a luta (as cartas são reembaralhadas a cada poucos segundos).
Controles
Ação	Mouse	Teclado
Escolher carta	Clique na carta	`1` a `5`
Escolher operador	Clique no operador	—
Atacar	Botão ATACAR	`Enter`
Limpar equação	Botão LIMPAR	`Esc`
Avançar história	Botão CONTINUAR	`Enter` ou `Espaço`
Recomeçar (fim de jogo)	—	`R`
Estrutura do repositório
```
.
├── project.godot          # configuração do projeto Godot
├── export_presets.cfg     # preset de exportação (Windows Desktop)
├── icon.svg               # ícone do projeto
├── LEIAME.txt             # instruções resumidas
├── assets/                # sprites e cenários (aprendiz, caos, monstros, caverna...)
├── scenes/
│   ├── Main.tscn          # cena inicial (menu + história)
│   ├── World.tscn         # arena, monstros e HUD
│   ├── main.gd            # menu e narrativa
│   ├── world.gd           # fases, spawn de monstros, vitória/derrota
│   ├── battle_overlay.gd  # sistema de combate por equações
│   ├── sprites.gd         # carregamento de sprites
│   ├── monster_art.gd / monster_portrait.gd  # arte e retratos dos monstros
│   └── audio.gd           # sons e músicas (gerados pelo próprio jogo)
└── scripts/Main.gd        # protótipo inicial do sistema de monstros
```
Os sons e músicas são gerados por código (placeholders), então não há arquivos de áudio.
Gerar o executável (opcional)
Abra o projeto no Godot 4.7.
Instale os export templates: Editor → Gerenciar Modelos de Exportação → Baixar e Instalar.
Vá em Projeto → Exportar…, escolha Windows Desktop e clique em Exportar Projeto.
O preset já está configurado em `export_presets.cfg` (saída: `Dungeon of Logic.exe`).
Problemas comuns
O Godot avisa que a versão do projeto é diferente: use exatamente o Godot 4.7.
Imagens não aparecem na primeira abertura: aguarde a reimportação dos assets ou use Projeto → Recarregar Projeto Atual.
Tela preta ao abrir o `.exe`: atualize o driver de vídeo; o jogo usa o renderizador GL Compatibility.
Aviso do Windows SmartScreen: o executável não é assinado; veja a observação na seção de execução.
