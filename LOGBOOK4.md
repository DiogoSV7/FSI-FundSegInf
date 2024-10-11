# Environment Variable and Set-UID Program Lab

## Task 1: Manipulating Environment Variables

* Para listar todas as variáveis de ambiente de um sistema, corremos o comando **printenv** ou simplesmente **env**.

![printenv](https://github.com/user-attachments/assets/3038d2a1-912f-4ad0-97d2-be2a1294a06e)
![ENV](https://github.com/user-attachments/assets/d980201a-b5e7-45b1-806a-205d78c03f87)

  
* Para executarmos uma listagem de todas as variáveis contidas num ambiente ENV, executamos **printenv PWD** ou **env | grep PWD**.

![printenv PWD](https://github.com/user-attachments/assets/8f068e28-b903-438a-bd49-84e418538d6a)


* Para definirmos uma variável de ambiente podemos utilizar o comando **export VAR_NAME=value**.

![export MY_VAR](https://github.com/user-attachments/assets/cb745472-0d83-49ba-8726-9f78d2256d46)


* Para removermos esta variável criada, podemos usar **unset VAR_NAME**.

![unset](https://github.com/user-attachments/assets/6938e113-63d2-45a4-8c17-c54eac222ba6)


## Task 2: Passing Environment Variables from Parent Process to Child Process

Nesta task, compilamos o programa myprintenv.c e guardamos as variáveis de ambiente do processo filho no ficheiro "childprocessenv" e as variáveis de ambiente do processo pai no ficheiro "parentprocessenv".

![criação dos files](https://github.com/user-attachments/assets/581772bb-b779-4629-b579-77ddf141b678)


* Ao executar o comando **diff childprocessenv parentprocessenv** recebemos uma resposta vazia, o que significa que as variáveis de ambiente do processo pai são iguais às do processo filho, logo, podemos observar que após a utilização do comando **fork()** o variável de execução permanece igual.

![diff](https://github.com/user-attachments/assets/c9a1e017-b60f-4d01-955c-27023e51ccfc)


## Task 3: Environment Variables and execve()

* Uma vez que ao passar o terceiro argumento da função "**execve()**" a NULL, iremos receber um output vazio, porque este terceiro argumento representa um array de strings com as variáveis de ambiente para o novo processo criado, se este parametro é NULL, recebemos um output vazio ao dar print às variáveis de ambiente do mesmo processo.

![myenv null](https://github.com/user-attachments/assets/70892307-10dd-4695-8967-06a4e76c8c13)


* Ao alterar este terceiro argumento para **environ**, recebemos um print de todas as variáveis de ambiente, uma vez que agora passamos o array de strings com as mesmas como argumento.

![myenv environ](https://github.com/user-attachments/assets/0e9b3218-626b-43b0-aa01-3807dec9f5fc)


## Task 4: Environment Variables and system()

* A função system() cria um processo filho que invoca o shell (/bin/sh) e, através dele, executa o comando especificado como argumento.

* Ao contrário da função **execve()**, em que é necessário passar manualmente as variáveis de ambiente (caso contrário, elas não estarão disponíveis no novo programa), a função system() transmite automaticamente as variáveis de ambiente do processo atual para o novo processo de shell.

![task4](https://github.com/user-attachments/assets/6c7093fa-dcd4-4097-9bc9-632801250558)


## Task 5: Environment Variable and Set-UID Programs

* Primeiramente criarmos um programa que dá print a todas as variáveis de ambiente de um processo, neste caso chamamos-lhe foo.
  
* Posteriormente, alteramos o proprietário do programa para "**root**" e tornámo-lo num programa **set-UID** com os seguintes comandos:

![chown chmod](https://github.com/user-attachments/assets/b81de475-852f-4889-8fae-9c5b90bd832a)


* Ao verificarmos que não somos um utilizador **root**, através do comando **whoami**, utilizamos novamente o comando **export** para alterar e criar algumas variáveis de ambiente.

![Screenshot from 2024-10-07 05-05-50 (1)](https://github.com/user-attachments/assets/baa98f15-4455-46e7-977a-f9b1f237a648)



* Ao executarmos novamente o programa, podemos observar que apenas a variável criada e a variável **PATH** estão presentes na lista das variáveis. Isto deve-se ao facto de o sistema remover variáveis de ambiente perigosas como a **LD_LIBRARY_PATH** de programas **set-UID** para prevenir ataques de escalonamento de privilégios.

![exports3](https://github.com/user-attachments/assets/c7182983-b6c3-4276-aefb-4d779f5e0178)


* **LD_LIBRARY_PATH** permite que o utilizador ou programador adicione diretórios personalizados à lista de locais onde o sistema procura essas bibliotecas, sem que seja necessário instalá-las nas pastas padrão.

## Task 6: The PATH Environment Variable and Set-UID Programs

## Task 8: Invoking External Programs Using system() versus execve() - Step 1


  
