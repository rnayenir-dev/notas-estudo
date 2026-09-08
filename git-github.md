# Git e GitHub

## Conceitos
- **Git**: sistema de controle de versão local. Guarda o histórico de cada arquivo, permitindo voltar a versões anteriores sem precisar de cópias manuais (tcc.docx, tcc-final.docx, etc).
- **GitHub**: serviço web que hospeda repositórios remotos usando Git por baixo. Git != GitHub — o Git existiu primeiro (2005, criado por Linus Torvalds para o kernel Linux); o GitHub veio depois (2008). GitHub não é o único, existem alternativas como GitLab e Bitbucket.

## Branches (ramificações)
Permitem trabalhar em uma funcionalidade nova ou correção sem afetar o código estável da `main`.
**Regra de ouro: nunca commitar direto na main/master/prod.**

## Nomenclaturas de branch
- `feat`: nova feature
- `fix`: correção de bug
- `docs`: documentação
- `style`: estilização
- `refactor`: refatoração
- `perf`: performance
- `test`: testes
- `chore`: build, configs, dependências

## Configuração SSH
1. `ls -al ~/.ssh` — verificar se já existe chave
2. `ssh-keygen -t ed25519 -C "email@exemplo.com"` — gerar nova chave
3. `eval "$(ssh-agent -s)"` — iniciar o agente
4. `ssh-add ~/.ssh/id_ed25519` — adicionar chave ao agente
5. `clip < ~/.ssh/id_ed25519.pub` — copiar chave pública
6. Adicionar em GitHub → Settings → SSH and GPG keys
7. `ssh -T git@github.com` — testar conexão

## Comandos Git
| Comando | Função |
|---|---|
| `git init` | Inicia um repositório Git na pasta |
| `git status` | Mostra o estado atual (modificados, novos, staged) |
| `git add <arquivo ou .>` | Prepara arquivos para o commit |
| `git rm --cached <arquivo>` | Remove arquivo da staging area (não do disco) |
| `git branch` | Lista as branches locais |
| `git checkout -b <nome>` | Cria uma branch nova e muda para ela |
| `git checkout <nome>` | Muda para uma branch existente |
| `git merge <branch>` | Mescla a branch informada na branch atual |
| `git commit -m "mensagem"` | Salva as mudanças com uma mensagem |
| `git push` | Envia os commits locais para o repositório remoto |
| `git branch -D <nome>` | Apaga uma branch local |
| `git fetch` | Baixa referências do remoto sem mesclar |
| `git pull` | Baixa e mescla mudanças do remoto |

## Fluxo de trabalho em equipe (12 passos)
1. Criar repo
2. Clonar repo
3. Abrir no VSCode
4. Criar uma branch nova a partir da main
5. Desenvolver
6. `git add .`
7. `git commit -m "..."`
8. Abrir um Pull Request
9. Merge do Pull Request
10. Voltar para main (`git checkout main` + `git pull`)
11. Deletar a branch antiga da máquina (`git branch -D <nome>`)
12. Loop — voltar ao passo 4