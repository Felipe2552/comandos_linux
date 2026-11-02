# Documentação – Comandos Linux

## Fontes

1. https://www.devmedia.com.br/comandos-importantes-linux/23893
2. https://hackmd.io/community/@dgpinheiro/linuxintro#Tabela-de-comandos-básicos

## Onde praticar

Dá para praticar Linux direto no navegador, sem instalar nada: o **JSLinux**, de Fabrice Bellard, é um terminal Linux online.

## Comandos mais usados

Estes comandos cobrem a maior parte do uso diário.

| Comando | O que faz |
|---|---|
| `ls` | Lista todos os arquivos do diretório |
| `pwd` | Mostra o caminho completo até o diretório atual |
| `df` | Mostra a quantidade de espaço usada no disco rígido |
| `top` | Mostra o uso da memória |
| `cd` | Acessa uma determinada pasta (diretório) |
| `mkdir` | Cria um diretório |
| `rm` | Remove um arquivo ou diretório |
| `cat` | Abre um arquivo |
| `vi` | Abre o editor vi (lê-se "viai") para editar ou criar arquivos |
| `exit` | Encerra a sessão |

## Navegação

Use estes comandos para saber onde você está e se mover entre as pastas.

| Comando | O que faz |
|---|---|
| `pwd` | Mostra onde você está |
| `ls` | Lista arquivos |
| `ls -l` | Lista com detalhes |
| `ls -la` | Lista incluindo arquivos ocultos |
| `cd pasta` | Entra na pasta |
| `cd ..` | Sobe um nível |
| `cd ~` | Vai para a home |
| `clear` | Limpa a tela do terminal (não é interface gráfica). O Tab funciona independentemente dele. |

## Criar, copiar e mover

| Comando | O que faz |
|---|---|
| `mkdir pasta` | Cria pasta |
| `touch arquivo.txt` | Cria arquivo vazio |
| `cp origem destino` | Copia arquivo |
| `cp arq1.txt arq2.txt arq3.txt pasta_destino/` | Copia vários arquivos para uma pasta específica |
| `cp -r pasta1 pasta2` | Copia pasta |
| `mv origem destino` | Move ou renomeia um arquivo |
| `rm arquivo` | Apaga arquivos específicos (**sem volta!**) |
| `rm *` | Apaga todos os arquivos da pasta (condição: estar dentro da pasta para executar o comando) |
| `rmdir` | Apaga diretório / pastas vazias |
| `rm -r` | Apaga pastas |

### Copiar para um destino usando variável

Uma forma eficaz de copiar arquivos para um diretório destino é criar previamente uma variável (a verificar).

1. Criar a variável: `variavel=~/caminho`
2. Confirmar o conteúdo: `echo "$variavel"/`
3. Copiar: `cp *.txt "$variavel"/` ou `cp arquivo1 arquivo2 "$variavel"/`
4. Apagar a variável: `unset variavel`
5. Confirmar que apagou: `echo "$variavel"` (se não aparecer nada, a variável foi apagada)

## Ver conteúdo

| Comando | O que faz |
|---|---|
| `cat arquivo` | Mostra o arquivo inteiro |
| `head -n 10 arquivo` | Mostra as primeiras 10 linhas |
| `tail -n 10 arquivo` | Mostra as últimas 10 linhas |
| `less arquivo` | Rola o arquivo (sai com `q`) |
| `wc -l arquivo` | Conta linhas |
| `file arquivo` | Mostra o formato do arquivo específico |
| `file *` | Mostra o formato de todos os arquivos da pasta |
| `sort` | Ordena as informações alfanumericamente |

## Buscar

| Comando | O que faz |
|---|---|
| `grep "texto" arquivo` | Procura texto no arquivo |
| `find . -name "*.fastq"` | Procura arquivos pelo nome |
| `locate` | Procura arquivo pelo nome |
| `history` | Lista os últimos comandos realizados |

## Sistema

| Comando | O que faz |
|---|---|
| `df -h` | Mostra o espaço em disco |
| `du -sh pasta` | Mostra o tamanho de uma pasta |
| `top` | Mostra os processos em execução (sai com `q`) |
| `whoami` | Mostra seu usuário |
| `man comando` | Abre o manual de um comando |

## Combinar comandos

| Comando | O que faz |
|---|---|
| `ls \| wc -l` | Conta os itens da pasta |
| `ls > lista.txt` | Salva a saída em um arquivo |

## Servidor

| Comando | O que faz |
|---|---|
| `ssh usuario@endereco` | Conecta ao servidor |
| `scp arquivo usuario@endereco:pasta/` | Copia um arquivo para o servidor |
| `tmux` | Mantém os processos rodando se a conexão cair |

---

# Exercícios

## Nível 1: Navegação

1. Descubra em que pasta você está e vá para `~/treino/amostras`.

   ```
   /home/npo/felipe
   /home/npo/felipe/treino_felipe/amostras_felipe
   ```

2. Liste o conteúdo com detalhes.

   ```
   controle_001_R1.fastq controle_001_R2.fastq gastrico_001_R1.fastq gastrico_001_R2.fastq
   gastrico_002_R1.fastq gastrico_002_R2.fastq
   ```

3. Volte para a home usando o atalho `~`.

   ```
   npo@npo-Inspiron-3280-AIO:~/felipe/treino_felipe/amostras_felipe$ cd ~
   npo@npo-Inspiron-3280-AIO:~$ pwd
   /home/npo
   ```

## Nível 2: Criar, copiar e mover

5. Dentro de `~/treino`, crie a pasta `backup`.

   ```
   npo@npo-Inspiron-3280-AIO:~/felipe/treino_felipe$ l
   amostras_felipe/ metadados.csv resultados/
   npo@npo-Inspiron-3280-AIO:~/felipe/treino_felipe$ mkdir backup
   npo@npo-Inspiron-3280-AIO:~/felipe/treino_felipe$ ls
   amostras_felipe backup metadados.csv resultados
   ```

6. Crie uma variável com o caminho de `backup`, confira o conteúdo com `echo`, copie todos os arquivos `gastrico_*` de `amostras` para lá usando a variável, e depois apague a variável e confirme que sumiu.
7. Renomeie `controle_001_R1.fastq` para `normal_001_R1.fastq`.
8. Crie um arquivo vazio `notas.txt` em `~/treino` e depois apague-o.

## Nível 3: Ver conteúdo

9. Mostre as 4 primeiras linhas de `gastrico_001_R1.fastq` e as 2 últimas.
10. Conte quantas linhas esse arquivo tem.
11. Descubra o formato de `metadados.csv` e de todos os arquivos da pasta `amostras`.
12. Abra `metadados.csv` com `less` e saia dele.

## Nível 4: Buscar

13. Encontre todos os arquivos `.fastq` a partir de `~/treino`.
14. Procure a palavra `tumor` em `metadados.csv`.
15. Veja o histórico dos seus comandos.

## Nível 5: Combinar comandos

16. Conte quantos arquivos existem em `amostras`.
17. Salve a lista de nomes dos arquivos de `amostras` em `~/treino/resultados/lista_amostras.txt`.
18. Descubra quantas amostras são do grupo `tumor` usando `grep` e `wc` juntos.
19. Mostre o tamanho total da pasta `treino` e o espaço livre em disco.

## Servidor (só escrever, sem executar)

20. Escreva o comando para conectar ao servidor com o usuário `felipe` no endereço `servidor.universidade.br`.
21. Escreva o comando para copiar `metadados.csv` para a pasta `dados/` do servidor.
22. Qual comando você usaria para a análise continuar rodando se sua conexão cair?

## Desafio

23. Sem apagar nada que já existe, crie `~/treino/teste_rm`, entre nela, crie 3 arquivos `.txt` e apague todos de uma vez. Antes de apagar, confirme com `pwd` que está na pasta certa. Por que esse cuidado importa?

---

## Gabarito (tente antes de olhar)

<details>
<summary>Clique para ver</summary>

1. `pwd` e `cd ~/treino/amostras`
2. `ls -l`
3. `ls -la`
4. `cd ..` e `cd ~`
5. `mkdir ~/treino/backup`
6. `destino=~/treino/backup` → `echo "$destino"/` → `cp ~/treino/amostras/gastrico_* "$destino"/` → `unset destino` → `echo "$destino"`
7. `mv controle_001_R1.fastq normal_001_R1.fastq` (dentro de `amostras`)
8. `touch ~/treino/notas.txt` e `rm ~/treino/notas.txt`
9. `head -n 4 gastrico_001_R1.fastq` e `tail -n 2 gastrico_001_R1.fastq`
10. `wc -l gastrico_001_R1.fastq`
11. `file ~/treino/metadados.csv` e `file *` (dentro de `amostras`)
12. `less ~/treino/metadados.csv` (sai com `q`)
13. `find ~/treino -name "*.fastq"`
14. `grep "tumor" ~/treino/metadados.csv`
15. `history`
16. `ls | wc -l`
17. `ls > ~/treino/resultados/lista_amostras.txt`
18. `grep "tumor" ~/treino/metadados.csv | wc -l` (o resultado será 2)
19. `du -sh ~/treino` e `df -h`
20. `ssh felipe@servidor.universidade.br`
21. `scp metadados.csv felipe@servidor.universidade.br:dados/`
22. `tmux`
23. `mkdir ~/treino/teste_rm` → `cd ~/treino/teste_rm` → `touch a.txt b.txt c.txt` → `pwd` → `rm *`. O `rm *` apaga tudo da pasta atual sem lixeira, então se você estiver na pasta errada, apaga os arquivos errados.

</details>
