# CTF 4 - Environment Variables

## Desafio 1

* Ao navegar através do link fornecido http://ctf-fsi.fe.up.pt:5002 e ao navegar através do mesmo decidimos testar alguns comandos para obtermos mais informações do servidor tais como:

  ```
  $bash
  curl -v http://ctf-fsi.fe.up.pt:5002
  ```
  
  <img width="557" alt="Captura de ecrã 2024-10-10, às 08 47 34" src="https://github.com/user-attachments/assets/21151442-5edd-4b67-b9f1-32acc9087636">
  
  *Imagem 1: Output do comando curl*

* Através do comando **curl** fazemos uma simples requesição GET e obtemos os detalhes da conexão. Na verdade, podemos retirar de importante a informação do **Apache 2.4.7**.

  ```
  $bash
  nikto -h http://ctf-fsi.fe.up.pt:5002
  ```

  <img width="569" alt="Captura de ecrã 2024-10-10, às 08 59 45" src="https://github.com/user-attachments/assets/4da604be-57bb-44a2-acf1-f14d617304d2">

  *Imagem 2: Output do comando nikto*

* Através do comando **nikto** conseguimos fazer um scan de todas as vulnerabilidades conhecidas em servidores HTTP, através da mesma ficamos a conhecer que a versão do Apache se encontra desatualizada e, também, algumas vulnerabilidades não muito importantes para o contexto.

* Para além disso, na barra de pesquisa do servidor, ao corrermos a mesma, observamos que de modo **default**, a mesma executa um comando "ls" do servidor

  <img width="453" alt="Captura de ecrã 2024-10-10, às 09 05 25" src="https://github.com/user-attachments/assets/d969aad1-c012-484b-ba82-62d904b23a80">

  *Imagem 3: Click na pesquisa do servidor sem nenhum input*

* Deste modo, podemos observar que o servidor permite injeção de comandos nesta barra de pesquisa. Assim, ao pesquisar CVE´s referentes a vulnerabilidades de servidores Apache HTTP, deparamo-nos com o **CVE-2014-6271**.

  <img width="1399" alt="Captura de ecrã 2024-10-10, às 09 09 28" src="https://github.com/user-attachments/assets/235370bf-7ce1-47fe-b72a-fa49c7ef06af">

  *Imagem 4: Informações do CVE-2014-6271**

* Finalmente, associando tudo e com algumas dicas do servidor, tais como, ***THE WEBSITE IS AS HARD AS A SHELL***, tornou-se óbvio que este era o CVE pedido, sendo assim, a flag que resolve o desafio é:

  ```
  flag{CVE-2014-6271}
  ```


