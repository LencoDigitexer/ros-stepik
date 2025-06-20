# 1.6 Python - контрольные задания

# Шаг 2

Напишите программу на Python, которая считывает несколько чисел из строки (разделенных пробелом), а затем сообщает их количество и сумму.

## Решение

```python
# put your python code here
sum = 0
a = input().split(" ")

for i in range(len(a)):
    sum = sum + int(a[i])
    
    
print("Количество чисел: " + str(len(a)));
print("Сумма: " + str(sum))
```


# Шаг 3

## Определение направления движения робота
### Описание:
Напишите программу, которая определяет, в каком направлении будет ориентирован робот, после выполнения последовательности команд вида: `L`, `R`, `F`, `B`:

- `L`: поворот налево.
- `R`: поворот направо.
- `F`: движение вперёд.
- `B`: движение назад (задним ходом).

Программа принимает начальное направление (север `N`, юг `S`, восток `E`, запад `W`) и последовательность команд.

### Ввод:
Начальное направление (одна из `N`, `S`, `E`, `W`).
Последовательность команд (строка).
### Вывод:
Направление робота (ориентация) после выполнения команд.

#### Sample Input 1:

    N
    RRF

#### Sample Output 1:

    S

#### Sample Input 2:

    E
    LFFRBLL

#### Sample Output 2:

    W

## Решение

```python
def calc_degrees_from_word(argument):
    if argument == "N":
        return 0
    elif argument == "E":
        return 90
    elif argument == "S":
        return 180
    elif argument == "W":
        return 270
    else:
        return 0

def add_rotation(start_degrees):
    if start_degrees > 0:
        while start_degrees > 360:
            start_degrees = start_degrees - 360
        return start_degrees
    
    elif start_degrees < 0:
        while start_degrees < 0:
            start_degrees = start_degrees + 360
        return start_degrees
    else:
        return 0
        
def calc_word_from_degrees(argument):
    if argument == 0:
        return "N"
    elif argument == 90:
        return "E"
    elif argument == 180:
        return "S"
    elif argument == 270:
        return "W"
    else:
        return 0

# put your python code here
start_direction = input()
prog = list(input())

start_degrees = calc_degrees_from_word(start_direction)

for i in prog:
    if i == "R":
        start_degrees = add_rotation(start_degrees + 90)
    if i == "L":
        start_degrees = add_rotation(start_degrees - 90)


print(calc_word_from_degrees(start_degrees))
```