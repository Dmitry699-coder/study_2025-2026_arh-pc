# ОТЧЕТ
## ПО ЛАБОРАТОРНОЙ РАБОТЕ №6
### по дисциплине "Архитектура компьютера"

**Выполнил:** Савкин Дмитрий Вадимович  
**Группа:** НПИбд-02-25  
**Дата:** 2025 г.

---

## Цель работы

Освоение арифметических инструкций языка ассемблера NASM.

## Ход работы

### 6.3.1. Символьные и численные данные в NASM

#### Программа lab6-1.asm

**Первоначальный вариант (работа с символами):**
```asm
#include 'in_out.asm'
SECTION .bss
buff: RESB 80
SECTION .text
GLOBAL _start
_start:
mov eax,'6'
mov ebx,'4'
add eax,ebx
mov [buff],eax
mov eax,buff
call sprintLF
call quit
Исправленный вариант (работа с числами):
#include 'in_out.asm'
SECTION .bss
buf1: RESB 80
SECTION .text
GLOBAL _start
_start:
mov eax,6
mov ebx,4
add eax,ebx
mov [buf1],eax
mov eax,buf1
call sprintLF
call quit
Программа lab6-2.asm
Первоначальный вариант (работа с символами):
#include 'in_out.asm'
SECTION .text
GLOBAL _start
_start:
mov eax,'6'
mov ebx,'4'
add eax,ebx
call iprintLF
call quit
Исправленный вариант (работа с числами):Без перевода строки (iprint вместо iprintLF):
#include 'in_out.asm'
SECTION .text
GLOBAL _start
_start:
mov eax,6
mov ebx,4
add eax,ebx
call iprintLF
call quit
Без перевода строки (iprint вместо iprintLF):
Результат выполнения: 10dima@dimad-VirtualBox:~/work/arch-pc/lab06$
6.3.2. Выполнение арифметических операций в NASM
Программа lab6-3.asm

Вычисление выражения: (5 × 2 + 3) / 3
#include 'in_out.asm'
SECTION .data
div: DB 'Результат: ',0
rem: DB 'Остаток от деления: ',0
SECTION .text
GLOBAL _start
_start:
mov eax,5
mov ebx,2
mul ebx
add eax,3
xor edx,edx
mov ebx,3
div ebx
mov edi,eax
mov eax,div
call sprint
mov eax,edi
call iprintLF
mov eax,rem
call sprint
mov eax,edx
call iprintLF
call quit
Результат выполнения:
Результат: 4
Остаток от деления: 1
Модифицированная программа для выражения: (4 × 6 + 2) / 5
mov eax,4
mov ebx,6
mul ebx
add eax,2
xor edx,edx
mov ebx,5
div ebx
mov eax,4
mov ebx,6
mul ebx
add eax,2
xor edx,edx
mov ebx,5
div ebx
Результат выполнения:
Результат: 5
Остаток от деления: 1
6.3.3. Программа variant.asm

Ответы на вопросы:

    Строки для вывода "Ваш вариант":

        mov eax, [rem] и call sprint

    Назначение инструкций:

        mov ecx, x - сохранение адреса буфера для ввода

        mov edx, 80 - максимальная длина вводимой строки

        call sread - вызов процедуры чтения строки

    Назначение call atoi:

        Преобразование строки в целое число
    Строки для вычисления варианта:

    xor edx,edx - обнуление регистра edx

    mov ebx,20 - загрузка делителя

    div ebx - выполнение деления

Регистр для остатка от деления:

    edx

Назначение inc edx:

    Увеличение остатка на 1 (так как варианты обычно нумеруются с 1)

Строки для вывода результата:

    mov eax,edx - передача результата

    call iprintLF - вывод с переводом строки
6.4. Задание для самостоятельной работы
Программа lab6-4.asm

Вычисление выражения: y = 5(x-1)²
%include 'in_out.asm'
SECTION .data
msg: DB 'Программа вычисления y = 5(x-1)^2',0
prompt: DB 'Введите значение x: ',0
result: DB 'Результат: y = ',0
x1_msg: DB 'При x1=3: y = ',0
x2_msg: DB 'При x2=5: y = ',0
newline: DB '',10,0

SECTION .bss
x RESB 10

SECTION .text
GLOBAL _start
_start:
mov eax,msg
call sprintLF
mov eax,prompt
call sprint
mov ecx,x
mov edx,10
; ... остальной код вычислений
Результат выполнения:
Программа вычисления y = 5(x-1)^2
Введите значение x: 3
Результат: y = 20
При x1=3: y = 20
При x2=5: y = 80
Выводы:
В ходе лабораторной работы были приобретены навыки:

    Работы с символьными и численными данными в NASM

    Выполнения арифметических операций (сложение, умножение, деление)

    Использования подпрограмм из внешнего файла in_out.asm

    Организации ввода и вывода данных

    Вычисления арифметических выражений на языке ассемблера

    Отладки и тестирования ассемблерных программ

Были освоены основные арифметические инструкции NASM и принципы работы с регистрами процессора для выполнения вычислений.


