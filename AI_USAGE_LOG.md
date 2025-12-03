# Relatório de Uso de Inteligência Artificial Generativa

Este documento registra todas as interações relevantes feitas com ferramentas de IA generativa (como Gemini, ChatGPT, Copilot etc.) durante o desenvolvimento do projeto. O objetivo é garantir transparência e uso responsável da IA, tratando-a como uma ferramenta de apoio — não como substituta do entendimento dos conceitos utilizados.

## Política de Uso

O uso de IA foi permitido para:

- Geração de ideias e brainstorming de algoritmos.
- Explicações de conceitos complexos.
- Criação de código base (ex.: estrutura de classes, leitura de arquivos).
- Sugestões de otimização e refatoração.
- Auxílio no debugging e identificação de erros.
- Criação de casos de teste.

É proibido utilizar código gerado pela IA sem antes compreendê-lo totalmente e adaptá-lo ao contexto do projeto. Qualquer trecho influenciado por IA deve ser registrado neste relatório.

---

### Interação 1

- **Data:** 09/11/2025
- **Etapa do Projeto:** 1 – Criação e Configuração do Banco de Dados
- **Ferramenta Utilizada:** Gemini
- **Objetivo:** Criar um script para inicializar o banco de dados e configurar as tabelas com tratamento de erros de conexão.

- **Prompts Utilizados:**  
  1. “Crie um script PHP setup_database.php que verifique se o banco de dados existe e o crie se não existir.”  
  2. “Como fazer o PDO testar múltiplas senhas comuns (root, vazio, 123456) caso a conexão falhe, para funcionar em diferentes ambientes XAMPP?”

- **Resumo da Resposta:**  
  A IA sugeriu usar um loop `foreach` para testar diferentes senhas de conexão e indicou a criação das tabelas com `CREATE TABLE IF NOT EXISTS`, incluindo usuários e histórico.

- **Aplicação no Projeto:**  
  O código serviu como base para a lógica de conexão e criação das tabelas no arquivo `setup_database.php`.

- **Referência no Código:** setup_database.php (conexão e criação das tabelas `usuarios` e `historico_partidas`).

---

### Interação 2

- **Data:** 10/11/2025
- **Etapa do Projeto:** 2 – Sistema de Autenticação
- **Ferramenta Utilizada:** Gemini
- **Objetivo:** Implementar login e registro seguros, com hash de senha.

- **Prompts Utilizados:**  
  1. “Como criar um sistema de login seguro em PHP usando password_hash e password_verify?”  
  2. “Gere um formulário de registro que verifique se o email já existe no banco antes de salvar.”

- **Resumo da Resposta:**  
  A IA reforçou a importância de nunca salvar senhas em texto puro e forneceu um modelo de código para login e registro usando sessões e validações.

- **Aplicação no Projeto:**  
  O código foi adaptado para redirecionar o usuário para `cap_intro.php` após o login. A lógica de verificação de sessão foi adicionada em todas as páginas protegidas.

- **Referência no Código:** login.php, registrar.php e logout.php.

---

### Interação 3

- **Data:** 12/11/2025
- **Etapa do Projeto:** Integração PHP e JavaScript
- **Ferramenta Utilizada:** Gemini
- **Objetivo:** Transferir dados do PHP para o JavaScript para configurar o capítulo atual do jogo.

- **Prompts Utilizados:**  
  1. “Como passar um array PHP para uma variável JavaScript dentro de uma tag <script>?”  
  2. “Como manter o HP do jogador entre recarregamentos usando PHP Session?”

- **Resumo da Resposta:**  
  A IA recomendou usar `json_encode` para gerar um objeto JavaScript e explicou como manipular `$_SESSION['hp']`.

- **Aplicação no Projeto:**  
  A solução foi adotada para carregar os dados de cada capítulo e salvar o HP do jogador automaticamente.

- **Referência no Código:** capitulo.php (definição do `window.CAP_DATA` e manipulação de `$_SESSION['hp']`).

---

### Interação 4

- **Data:** 14/11/2025
- **Etapa do Projeto:** 4 – Salvamento Assíncrono de Pontuação
- **Ferramenta Utilizada:** Gemini
- **Objetivo:** Salvar a pontuação no banco sem recarregar a página usando JSON enviado por `fetch()`.

- **Prompts Utilizados:**  
  1. “Como receber JSON enviado via fetch POST no PHP? $_POST está vindo vazio.”  
  2. “Script PHP para receber tempo em ms, converter em pontos e salvar no MySQL.”

- **Resumo da Resposta:**  
  A IA explicou que dados JSON devem ser lidos via `file_get_contents('php://input')` e decodificados com `json_decode`.

- **Aplicação no Projeto:**  
  A lógica foi usada no save_score.php, incluindo regras de pontuação e verificação de conclusão bem-sucedida do capítulo.

- **Referência no Código:** save_score.php (leitura e decodificação do JSON).

---

### Interação 5

- **Data:** 18/11/2025
- **Etapa do Projeto:** 5 – Sistema de Ligas
- **Ferramenta Utilizada:** Gemini
- **Objetivo:** Implementar lógica de ranking que atualiza a pontuação apenas se a nova for melhor que a anterior.

- **Prompts Utilizados:**  
  1. “Como fazer um UPDATE no SQL apenas se a nova pontuação for melhor que a salva?”  
  2. “Como estruturar uma tabela de ligas com pontuação semanal e total?”

- **Resumo da Resposta:**  
  A IA recomendou buscar a pontuação atual via SELECT, comparar no PHP e só então fazer o UPDATE. Também sugeriu uma tabela extra (`liga_participantes`).

- **Aplicação no Projeto:**  
  Essa lógica foi implementada no modo “liga” dentro do save_score.php.

- **Referência no Código:** save_score.php (lógica condicional de update), setup_ligas.php.

---

### Interação 6

- **Data:** 19/11/2025
- **Etapa do Projeto:** Exibição do Ranking na Página Inicial
- **Ferramenta Utilizada:** Gemini
- **Objetivo:** Mostrar os três melhores jogadores na home.

- **Prompt Utilizado:**  
  “Query SQL para selecionar os 3 usuários com maior pontuação e como exibir isso em uma tabela HTML usando PHP.”

- **Resumo da Resposta:**  
  A IA forneceu uma query com `ORDER BY pontuacao DESC LIMIT 3` e um exemplo de loop para montar a tabela.

- **Aplicação no Projeto:**  
  O código foi incorporado ao trabdev.php, com ajustes para lidar com menos de três jogadores cadastrados.

- **Referência no Código:** trabdev.php (seção “Ranking Geral de Runemestres”).

---


