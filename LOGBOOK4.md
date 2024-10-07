# Environment Variable and Set-UID Program Lab

## Task 1: Manipulating Environment Variables

* Para listar todas as variáveis de ambiente de um sistema, corremos o comando **printenv** ou simplesmente **env**.

  // print
  
* Para executarmos uma listagem de todas as variáveis contidas num ambiente ENV, executamos **printenv PWD** ou **env | grep PWD**.

  // print

* Para definirmos uma variável de ambiente podemos utilizar o comando **export VAR_NAME=value**.

  // print

* Para removermos esta variável criada, podemos usar **unset VAR_NAME**.

  // print

## Task 2: Passing Environment Variables from Parent Process to Child Process

Nesta task, compilamos o programa myprintenv.c e guardamos as variáveis de ambiente do processo filho no ficheiro "childprocessenv" e as variáveis de ambiente do processo pai no ficheiro "parentprocessenv".

// print da criação destes 2 ficheiros

* Ao executar o comando **diff childprocessenv parentprocessenv** recebemos uma resposta vazia, o que significa que as variáveis de ambiente do processo pai são iguais às do processo filho, logo, podemos observar que após a utilização do comando **fork()** o variável de execução permanece igual.

// print das duas linhas do diff

## Task 3: Environment Variables and execve()

* Uma vez que ao passar o terceiro argumento da função "**execve()**" a NULL, iremos receber um output vazio, porque este terceiro argumento representa um array de strings com as variáveis de ambiente para o novo processo criado, se este parametro é NULL, recebemos um output vazio ao dar print às variáveis de ambiente do mesmo processo.

// print de correr o ./myenv

* Ao alterar este terceiro argumento para **environ**, recebemos um print de todas as variáveis de ambiente, uma vez que agora passamos o array de strings com as mesmas como argumento.

// print de correr o ./myenv alterado com o 3 argumento

## Task 4: Environment Variables and system()

* A função system() cria um processo filho que invoca o shell (/bin/sh) e, através dele, executa o comando especificado como argumento.

* Ao contrário da função **execve()**, em que é necessário passar manualmente as variáveis de ambiente (caso contrário, elas não estarão disponíveis no novo programa), a função system() transmite automaticamente as variáveis de ambiente do processo atual para o novo processo de shell.

  // print do correr o task4.c

## Task 5: Environment Variable and Set-UID Programs

* Primeiramente criarmos um programa que dá print a todas as variáveis de ambiente de um processo, neste caso chamamos-lhe foo.

  // print da criação do ficheiro
  
* Posteriormente, alteramos o proprietário do programa para "**root**" e tornámo-lo num programa **set-UID** com os seguintes comandos:

  // print do chown and chmod

* Ao verificarmos que não somos um utilizador **root**, através do comando **whoami**, utilizamos novamente o comando **export** para alterar e criar algumas variáveis de ambiente.

  // print dos 3 comandos de export

* Ao executarmos novamente o programa, podemos observar que apenas a variável criada e a variável **PATH** estão presentes na lista das variáveis. Isto deve-se ao facto de o sistema remover variáveis de ambiente perigosas como a **LD_LIBRARY_PATH** de programas **set-UID** para prevenir ataques de escalonamento de privilégios.

* **LD_LIBRARY_PATH** permite que o utilizador ou programador adicione diretórios personalizados à lista de locais onde o sistema procura essas bibliotecas, sem que seja necessário instalá-las nas pastas padrão.

## Task 6: The PATH Environment Variable and Set-UID Programs

## Task 8: Invoking External Programs Using system() versus execve() - Step 1


  
