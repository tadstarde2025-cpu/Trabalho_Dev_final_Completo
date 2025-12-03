# The Legend of Typing — O Portal do Runemestre

Seja bem-vindo ao **The Legend of Typing**, um jogo onde a sua agilidade no teclado se transforma em magia. Aqui, a digitação não é apenas uma mecânica: é a sua arma. Você assume o manto de um **Runemestre** em um universo de RPG medieval, onde cada palavra digitada corretamente é um feitiço lançado contra seus inimigos.

O projeto foi desenvolvido para unir diversão e aprendizado, oferecendo uma **Campanha Solo** desafiadora e um **Sistema de Ligas** para quem gosta de competir com os amigos.

---

## ✨ O que você vai encontrar

###  Identidade e Progresso
Sua jornada começa criando seu perfil. Utilizamos um sistema seguro de login (com `password_hash`) para proteger sua conta. No seu painel, você terá acesso a todas as suas estatísticas e ao histórico das suas batalhas épicas.

###  Modos de Jogo

* **Modo Campanha:** Enfrente capítulos com dificuldade progressiva. Aqui, sua vida (HP) é preciosa: errar uma letra custa saúde, mas manter uma sequência de acertos (combos) recupera suas forças. Ao vencer, você é recompensado com runas e seu progresso é salvo automaticamente.
* **Sistema de Ligas:** Quer saber quem é o digitador mais rápido do grupo? Crie ligas privadas com senha, convide seus amigos e disputem o topo do ranking semanal e geral.

###  Mecânicas de Combate
O jogo recompensa não apenas a velocidade, mas a precisão. O sistema calcula sua pontuação baseada no tempo de reação e nos combos realizados, tudo acompanhado de efeitos visuais que tornam cada acerto satisfatório.

---

##  Nos Bastidores (Tecnologias)

Para dar vida a este mundo, utilizamos uma stack clássica e robusta:

* **Frontend:** A interface foi construída com **HTML, CSS e JavaScript** puro, garantindo leveza e responsividade.
* **Backend:** A lógica do servidor roda em **PHP (7.4+)**, gerenciando sessões e as regras de negócio do jogo.
* **Banco de Dados:** Todo o histórico, usuários e ligas são armazenados em **MySQL/MariaDB**, acessados via PDO para maior segurança.
* **Servidor:** O ambiente recomendado é o Apache (via XAMPP).

---

##  Como Rodar o Projeto

Quer testar o jogo na sua máquina? É simples. Você vai precisar de um servidor local (como o XAMPP, WAMP ou LAMP) e um navegador atualizado.

1. **Clone o projeto:** Coloque a pasta do jogo dentro do diretório do servidor (ex.: `C:\xampp\htdocs\legend-of-typing`).
2. **Inicie os serviços:** Abra o painel do XAMPP e dê "Start" no Apache e no MySQL.
3. **Configure o Banco:**
   - Acesse o arquivo `setup_database.php` pelo navegador para criar o banco e as tabelas principais.
   - Em seguida, execute o `setup_ligas.php` para configurar o sistema de ligas.
   - *Dica:* Se sua senha do MySQL não for vazia, lembre-se de ajustar o arquivo `config.php`.
4. **Jogue:** Acesse `http://localhost/legend-of-typing/index.php` e comece sua aventura!

---

##  Guia de Combate

1. Crie sua conta e faça o login.
2. Escolha entre enfrentar a **Campanha** ou competir nas **Ligas**.
3. **Na batalha:**
   - O inimigo lançará uma palavra contra você.
   - Digite-a corretamente e pressione **Enter** para atacar.
   - Acertos geram combos e curam vida; erros drenam seu HP.
4. Sobreviva até o fim do capítulo para salvar sua pontuação lendária. Se seu HP zerar, é fim de jogo!

---

##  Estrutura do Código

O projeto está organizado para ser fácil de entender e manter:

* **Core:** `index.php` (entrada) e `config.php` (conexão com o banco).
* **Game Logic:** `capitulo.php` e `cap.js` controlam a mágica do jogo, enquanto `save_score.php` garante que seus pontos sejam registrados via AJAX.
* **Social:** `ligas.php` e `liga_ranking.php` gerenciam a competição entre jogadores.
* **Dados:** As tabelas `usuarios`, `historico_partidas` e `ligas` (no banco `runemestre_db`) armazenam toda a persistência do universo do jogo.

---