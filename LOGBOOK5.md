# Buffer Overflow Attack Lab (Set-UID Version)

## LOGBOOK Setup

* O Ubuntu e outros sistemas operacionais baseados em Linux implementam a Randomização de Espaço de Endereçamento (ASLR) para randomizar os endereços iniciais do heap e da stack. Isso torna a adivinhação dos endereços de memória exatos mais difícil, o que é um dos componentes-chave nos ataques de buffer overflow.

* Para desativar o ASLR, execute o seguinte comando:

```bash
$ sudo sysctl -w kernel.randomize_va_space=0
```

*Este comando desativa a randomização dos endereços de memória virtual, facilitando a execução do ataque.

## Task 1 : Getting Familiar with Shellcode






## Task 2 : Understanding the Vulnerable Program






## Task 3 : Launching Attack on 32-bit Program
