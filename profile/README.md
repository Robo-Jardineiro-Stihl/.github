# Manual de Boa Práticas  <a name="indice"></a>

[Tabela de Comandos Github](#tabela-de-comandos-github)

[Como Clonar um Repositório Git](#como-clonar-um-repositório-git)

[Como Vincular uma Pasta Local a um Repositório Remoto](#como-vincular-uma-pasta-local-a-um-repositório-remoto)

[Boas Práticas de Commit](#boas-práticas-de-commit)


---

# Tabela de Comandos Github


| Comando               | Descrição                                                                 |
|-----------------------|---------------------------------------------------------------------------|
| `git init`            | Inicializa um novo repositório Git no diretório atual.                     |
| `git clone <url>`      | Clona um repositório existente a partir de uma URL.                       |
| `git status`          | Exibe o status atual do repositório, mostrando arquivos modificados, não rastreados, etc. |
| `git add <arquivo>`    | Adiciona o(s) arquivo(s) especificado(s) para serem preparados para o *commit*. |
| `git commit -m "mensagem"` | Realiza um *commit* com a mensagem especificada.                       |
| `git push`            | Envia os *commits* locais para o repositório remoto.                       |
| `git pull`            | Baixa atualizações do repositório remoto e as mescla com a branch local.   |
| `git branch`          | Lista todas as *branches* no repositório.                                  |
| `git checkout <branch>`| Alterna para a *branch* especificada.                                      |
| `git merge <branch>`   | Mescla a *branch* especificada com a *branch* atual.                       |
| `git log`             | Exibe o histórico de *commits* do repositório.                             |
| `git diff`            | Mostra as diferenças entre as alterações locais e o último *commit*.       |
| `git reset <arquivo>`  | Remove o arquivo da área de preparação, mas mantém as alterações locais.   |
| `git stash`           | Armazena temporariamente as mudanças feitas no código que ainda não foram *committed*. |
| `git stash apply`     | Aplica as mudanças armazenadas pelo `git stash`.                           |
| `git rebase <branch>`  | Reaplica os *commits* da *branch* atual sobre a base de outra *branch*.    |
| `git remote`          | Exibe os repositórios remotos configurados.                                |
| `git fetch`           | Baixa dados do repositório remoto sem mesclá-los à *branch* atual.         |
| `git rm <arquivo>`     | Remove um arquivo do diretório de trabalho e o marca para remoção no próximo *commit*. |
| `git tag <nome>`       | Cria uma tag (marcação) em um ponto específico da história do repositório. |
| `git blame <arquivo>`  | Exibe quem fez as alterações em cada linha de um arquivo.                 |
| `git revert <commit>`  | Reverte as mudanças introduzidas por um *commit* específico.              |
| `git show <commit>`    | Exibe informações detalhadas sobre um *commit* específico.                |

[Voltar ao Índice](#indice)

---

# Como Clonar um Repositório Git

## Pré-requisitos
- Ter o Git instalado na sua máquina. [Como instalar Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
- Acesso ao repositório Git que você deseja clonar ou vincular.

### Passo 1: Copie a URL do Repositório
No GitHub, GitLab ou outro serviço, vá até o repositório que deseja clonar. Localize e copie o link HTTPS ou SSH para clonar o repositório.

```markdown
Exemplo de URL HTTPS:

https://github.com/usuario/repo-exemplo.git


Exemplo de URL SSH:

git@github.com:usuario/repo-exemplo.git
```

### Passo 2: Abra o Terminal
No Windows, você pode usar o Git Bash. No macOS e Linux, basta usar o terminal padrão.

### Passo 3: Execute o Comando de Clone
No terminal, navegue até o diretório onde deseja clonar o repositório e execute o comando `git clone` seguido da URL copiada.

Comando:
```bash
git clone https://github.com/usuario/repo-exemplo.git
```

Ou usando SSH:
```bash
git clone git@github.com:usuario/repo-exemplo.git
```

### Passo 4: Acesse o Diretório Clonado
Após clonar o repositório, entre no diretório criado:

```bash
cd repo-exemplo
```

Agora você tem o repositório clonado localmente!

[Voltar ao Índice](#indice)

---

# Como Vincular uma Pasta Local a um Repositório Remoto

### Passo 1: Crie um Diretório Local
Se você já tem uma pasta com código, pode pular esse passo. Caso contrário, crie uma nova pasta local para o projeto.

```bash
mkdir meu-projeto
cd meu-projeto
```

### Passo 2: Inicialize um Repositório Git
Dentro da pasta do projeto, inicialize o Git com o comando:

```bash
git init
```

### Passo 3: Adicione o Repositório Remoto
Vincule o repositório remoto à sua pasta local usando o comando `git remote add origin` seguido da URL do repositório.

Comando:
```bash
git remote add origin https://github.com/usuario/meu-repo.git
```

Ou usando SSH:
```bash
git remote add origin git@github.com:usuario/meu-repo.git
```

### Passo 4: Verifique a Conexão com o Repositório Remoto
Execute o seguinte comando para verificar se o repositório remoto foi vinculado corretamente:

```bash
git remote -v
```

### Passo 5: Faça o Primeiro Commit
Se você já tem arquivos na pasta local, adicione-os ao Git e faça o primeiro commit:

```bash
git add .
git commit -m "Primeiro commit"
```

### Passo 6: Envie os Arquivos para o Repositório Remoto
Para enviar os arquivos locais para o repositório remoto, use o comando:

```bash
git push -u origin master
```

Agora, sua pasta local está vinculada ao repositório remoto e os arquivos foram enviados para o repositório!

[Voltar ao Índice](#indice)

---

# Boas Práticas de Commit

### Faça *commits* pequenos e frequentes
- Quebre suas alterações em partes pequenas e lógicas, para que cada *commit* tenha um propósito claro.
- Facilita o *debug* e a revisão de código, além de permitir reverter mudanças específicas com mais facilidade.

### Use mensagens de *commit* descritivas
- A mensagem deve explicar **o que foi feito** e, se necessário, **por que** a mudança foi feita.
- Exemplo: `Corrige bug de validação no formulário de login` ao invés de `Correções gerais`.

### Siga um formato de mensagem padronizado
- Considere usar um padrão como o [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/), que organiza os *commits* em tipos, como:
  - `feat:` para novas funcionalidades
  - `fix:` para correções de bugs
  - `docs:` para alterações na documentação
  - `refactor:` para mudanças no código que não afetam o comportamento da aplicação
- Exemplo: `feat: adiciona validação de e-mail no cadastro`.

### Evite mensagens de *commit* vagas
- Evite descrições como "update", "fix bug" ou "ajustes", que não deixam claro o que foi alterado.
- Inclua detalhes sobre o problema corrigido ou a funcionalidade implementada.

### Use a voz ativa nas mensagens
- Mensagens devem ser curtas e diretas, com um verbo no infinitivo que explique o que foi feito.
- Exemplo: `Adiciona função de verificação de token` ao invés de `Função de verificação de token adicionada`.

### Use referências a *issues* ou tarefas
- Relacione *commits* às tarefas ou *issues* que estão sendo resolvidas. Exemplo:
  - `fix: corrige erro na busca de usuários #123`
- Isso facilita o rastreamento e entendimento do propósito do *commit*.

### Teste antes de *commitar*
- Sempre teste seu código antes de fazer um *commit* para garantir que ele funciona como esperado e não introduz novos erros.

### Evite *commits* temporários ou de "debug"
- Não suba ao repositório *commits* temporários, como alterações locais usadas apenas para teste (`debug`, `console.log` etc.).
- Utilize ramificações locais se precisar trabalhar em progresso.

### Agrupe alterações relacionadas
- Não misture várias funcionalidades ou correções de bugs em um único *commit*. Isso dificulta o rastreamento e a reversão de mudanças.
- Cada *commit* deve ter um escopo claro.

### Revise suas alterações antes de *commitar*
- Use `git diff` para verificar suas mudanças e certifique-se de que apenas as alterações necessárias estão incluídas.

Seguir essas boas práticas ajudará a manter um histórico de *commits* limpo, organizado e fácil de entender, facilitando o trabalho em equipe e a manutenção do código a longo prazo.

[Voltar ao Índice](#indice)

---





