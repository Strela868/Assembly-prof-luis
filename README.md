;```assembly
; Programa "Soma de Dois Números" em Assembly
; Autor: Luiz Angelo, FEAP
; Versão: Stela Veiga Monteiro, Curso: Engenharia da Computação

SYS_EXIT    equ 1
SYS_READ    equ 3
SYS_WRITE   equ 4
STDIN       equ 0
STDOUT      equ 1
STDOPE      equ 2

section .data
    msg1 db "A soma é: ", 0xA, 0xD ; Mensagem para imprimir a soma
    len equ $ - msg1

section .bss
    res resb 2 ; Variável para armazenar o resultado (como ASCII)

section .text
global _start

_start:
    ; Calcula a soma de dois números (3 + 4)
    mov eax, 3  ;movendo o valor '3' para registro 'eax'
    add eax, 4  ;somando o valor '4' para registro 'eax'

    ; Converte o resultado em ASCII (0 a 9 são valores ASCII sequenciais)
    add al, "0"

    ; Armazena o resultado na variável res
    mov [res], al

    ; Imprime a mensagem
    mov eax, 4
    mov ebx, 1
    mov ecx, msg1
    mov edx, len
    int 0x80

    ; Imprime o resultado
    mov eax, 4
    mov ebx, 1
    mov ecx, res
    mov edx, 1
    int 0x80

    ; Finaliza o programa
    mov eax, 1
    xor ebx, ebx
    int 0x80
