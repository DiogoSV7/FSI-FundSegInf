# Environment Variable and Set-UID Program Lab

## Task 1 : Manipulating Environment Variables

* Para listar todas as variáveis de ambiente de um sistema, corremos o comando **printenv** ou simplesmente **env**.

  // print
  
* Para executarmos uma listagem de todas as variáveis contidas num ambiente ENV, executamos **printenv PWD** ou **env | grep PWD**.

  // print

* Para definirmos uma variável de ambiente podemos utilizar o comando **export VAR_NAME=value**.

  // print

* Para removermos esta variável criada, podemos usar **unset VAR_NAME**.

  // print

## Task 2 : Passing Environment Variables from Parent Process to Child Process

Nesta task, compilamos o programa myprintenv.c e guardamos as variáveis de ambiente do processo filho no ficheiro "childprocessenv" e as variáveis de ambiente do processo pai no ficheiro "parentprocessenv".

// print da criação destes 2 ficheiros

* Ao executar o comando **diff childprocessenv parentprocessenv** recebemos uma resposta vazia, o que significa que as variáveis de ambiente do processo pai são iguais às do processo filho, logo, podemos observar que após a utilização do comando **fork()** o variável de execução permanece igual.

// print das duas linhas do diff

## Task 3 : Environment Variables and execve()
