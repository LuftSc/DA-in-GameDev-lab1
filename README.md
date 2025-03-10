# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #1 выполнил(а):
- Бердышев Артём Александрович
- РИ210942
Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
| Задание 3 | * | 20 |

знак "*" - задание выполнено; знак "#" - задание не выполнено;

Работу проверили:
- к.т.н., доцент Денисов Д.В.
- к.э.н., доцент Панов М.А.
- ст. преп., Фадеев В.О.

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

Структура отчета

- Данные о работе: название работы, фио, группа, выполненные задания.
- Цель работы.
- Задание 1.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 2.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 3.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Выводы.
- ✨Magic ✨

## Цель работы
Ознакомиться с основными операторами зыка Python на примере реализации линейной регрессии.

## Задание 1
### Написать программы Hello World на Python и Unity
Ход работы:
Для Python привожу скриншот с демострацией запуска программы, выводящей сообщение Hello World
![изображение](https://user-images.githubusercontent.com/104849066/190551973-c3371dba-1e45-4606-b3d4-0b706ffc42b3.png)

Для Unity так же привожу скриншот с демонстрацией запуска программы, выводящей Hello World! в консоль
![изображение](https://user-images.githubusercontent.com/104849066/190552824-dd21f803-94b0-447e-8094-a485880c2979.png)

![изображение](https://user-images.githubusercontent.com/104849066/190552725-a74b2dab-6353-4ab9-b5d0-de17bddc2386.png)

## Задание 2
### В разделе "Ход работы" пошагово выполнить каждый пункт с описанием и примеров реализации задачи по теме лабораторной работы
- Произвожу подготовку данных для работы с алгоритмом линейной регрессии
![изображение](https://user-images.githubusercontent.com/104849066/190554513-01d71899-a863-4808-8cf8-d70b561b913b.png)
- Определяю связанные функции. Функция модели: определяет модель линейной регрессии wx+b. Функция потерь: функция потерь среднеквадратичной ошибки. Функция оптимизации: метод градиентного спуска для нахождения частных производных w и b.
![изображение](https://user-images.githubusercontent.com/104849066/190555949-b4279f74-261d-49df-985a-96493f5a85da.png)
- Начинаю итерацию
Шаг 1 Инициализация и модель итеративной оптимизации
![изображение](https://user-images.githubusercontent.com/104849066/190557074-9204c94e-9584-41eb-acda-730fc031ec3a.png)
Шаг 2 На второй итерации отображается значения параметров, значения потерь и эффекты визулизации после итерации
![изображение](https://user-images.githubusercontent.com/104849066/190557269-b8c837f7-9e61-43c4-b0bd-37358406bc17.png)
Шаг 3 Третья итерация показывает значения параметров, значения потерь и визуализацию после итерации
![изображение](https://user-images.githubusercontent.com/104849066/190557490-64ed962f-8446-41ec-8914-306f7665ce75.png)
Шаг 4 На четвёртой итерации отображаются значения параметров, значения потерь и эффекты визулизации
![изображение](https://user-images.githubusercontent.com/104849066/190558151-fee00e07-780d-47ee-9eb3-be4317b87d10.png)

Шаг 5 Пятая итерация показывает значение параметра, значение потерь и эффект визуализации после итерации
![изображение](https://user-images.githubusercontent.com/104849066/190557714-d20bb3fb-f7c0-4a5a-b0fe-03c7cc204c89.png)
Шаг 6 10000-я итерация, показывающая значение параметров, потери и визуализацию после итерации
![изображение](https://user-images.githubusercontent.com/104849066/190557833-584abbe3-1481-488a-afce-94de60c97243.png)

## Задание 3
### Изучить код на Python и ответить на вопросы:
```py
def model(a, b, x):
    return a * x + b

def loss_function(a, b, x, y):
    num = len(x)
    predication = model(a,b,x)
    return (0.5/num) * (np.square((predication - y))).sum()

def optimize(a,b,x,y):
    num = len(x)
    predication = model(a,b,x)
    da = (1.0 / num) * ((predication - y) * x).sum()
    db = (1.0 / num) * ((predication - y).sum())
    a = a - Lr * da
    b = b - Lr * db
    return a,b

def iterate(a,b,x,y,times):
    for i in range(times):
        a,b = optimize(a,b,x,y)
    return a,b

#Import the required modules, numpy for calculation, and Matplotlib for drawing
import numpy as np
import matplotlib.pyplot as plt

# define data, and change list to array
x = [3,21,22,34,54,34,55,67,89,99]
x = np.array(x)
y = [2,22,24,65,79,82,55,130,150,199]
y = np.array(y)

#Show the effect of a scatter plot
plt.scatter(x,y)

a = np.random.rand(1)
print(a)
b = np.random.rand(1)
print(b)
Lr = 0.000001

a,b = iterate(a,b,x,y,2)
predication = model(a,b,x)
loss = loss_function(a,b,x,y)
print(a,b,loss)
plt.scatter(x,y)
plt.plot(x,predication)
```
- Должна ли величина loss стремиться к нулю при изменении исходных данных?
Да, должна. Если использовать данные, которые даны изначально, то величина loss колеблется в районе 
(от 1000 до 5000).
![изображение](https://user-images.githubusercontent.com/104849066/190559162-2ea91063-ac58-470b-95cd-d8e0473a98fc.png)
Если же изменить исходные данные(списки а и b) например, на убывающую последовательность, как будет показано на скрине, то величина loss будет колебаться уже в пределах(от 50 до 2 200)
![изображение](https://user-images.githubusercontent.com/104849066/190559504-26e167a0-decd-469f-a130-47e91722f84d.png)

- Какова роль параметра Lr?
Этот параметр ограничивает значения а, b, loss. При Lr = 0.000001, a,b находятся в промежутке примерно(от 0 до 1), loss примерно (от 1 000 до 5 000)
![изображение](https://user-images.githubusercontent.com/104849066/190560117-17eee3e5-7b42-4d6d-829b-8387aa121e2a.png)
Попробуем увеличить этот параметр в 100 раз, теперь Lr = 0.0001 a теперь в промежутке (от 1 до 1.4),
loss примерно (от 400 до 1 300)
![изображение](https://user-images.githubusercontent.com/104849066/190560577-17c0adf5-9dbb-4f26-837e-49c49716c5ca.png)
Увеличим его ещё в 10 раз, теперь он равен 0.001, что в 1 000 раз больше, чем его изначальное значение!
Теперь a колеблется (от -7 до -2), b (от -1 до 1), а loss (от 10 000 до 100 000)
![изображение](https://user-images.githubusercontent.com/104849066/190561073-e2b3d965-3ffc-425a-8115-08e038d7e1c3.png)

## Выводы
В ходе выполнения этой лабораторной работы я настроил своё программное обеспечение (Unity, Visual Studio, PyCharm) для дальнейшней работы с ними. Написал традиционное Hello World в Unity и в PyCharm'е,
а так же разобрался, как пользоваться GitHub'ом.

## Powered by

**Artem Berdyshev**
