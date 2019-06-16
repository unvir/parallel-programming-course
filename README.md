## ЛР1 - Многопоточное программирование

```
Необходимо распараллелить умножение матриц используя OpenMP
```

#### Запускалось на
- ОС: **Ubuntu 16.04.4 LTS**
- Процессор: **AMD Ryzen 3 2200G with Radeon Vega Graphics**
  - Ядер: **4**
  - Потоков: **4**
  
#### Тест кейсы
- [input1](https://github.com/unvir/parallel-programming-course/blob/lab1/input.txt) умножение матриц 2x3 и 3x2 
- [input2](https://github.com/unvir/parallel-programming-course/blob/lab1/input2.txt) умножение матриц 20x40 и 40x30
- [input3](https://github.com/unvir/parallel-programming-course/blob/lab1/input3.txt) умножение матриц 2x60 и 60x2

Запуск программы на каждом тестовом кейсе подразумевает **100000** умножений приведенных матриц.
*Команды для компиляции*:
```console
g++ -o omp_inputN -std=gnu++11 -fopenmp main.cpp
```
```console
g++ -o inputN -std=gnu++11 main.cpp
```

#### Результаты
[Результат](https://github.com/unvir/parallel-programming-course/blob/lab1/runner.out) выполнения [runner.sh](https://github.com/unvir/parallel-programming-course/blob/lab1/runner.sh)

*Среднее значение по 10 замерам (в секундах)*:

| Потоки | omp input1 | omp input2 | omp input3 | input1 | input2 | input3 |
|--------|------------|------------|------------|--------|--------|--------|
|1|0.048208|17.7966|0.215351|0.0260543|15.9993|0.176758|
|2|0.102437|11.3339|0.260857|0|0|0|
|4|0.125671|6.91229|0.303936|0|0|0|
|6|1.28173|7.46951|1.14831|0|0|0|
|10|1.83022|7.72546|1.80828|0|0|0|

> Update
 Изменен размер матрицы: умножение двух матриц 512x1024 и 1024x512 50раз
 
| thread/chunk | 1 | 5 | 10 | 25 | 50 | 100 |
|--------|------------|------------|------------|--------|--------|--------|
|1|125.098|124.144|124.358|124.479|124.013|124.915|
|2|112.676|87.291|68.183|65.809|63.175|66.549|
|4|74.912|43.675|30.858|44.343|42.933|40.121|
|6|75.259|45.233|31.054|44.729|44.322|45.109|
|10|77.545|45.761|30.977|44.712|46.277|45.511|
 
 
 
