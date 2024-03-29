# **Текстовое описание решения задачи**

### **Задача:** Написать программу, которая из имеющегося массива строк формирует массив из строк, длина которых меньше либо равна 3 символа. Первоначальный массив можно ввести с клавиатуры, либо задать на старте выполнения алгоритма. При решении не рекомендуется пользоваться коллекциями, лучше обойтись исключительно массивами.  

### **Примеры:**
> ### ["hello", "2", "world", ":-)"] -> ["2", ":-)"]
> ### ["1234", "1567", "-2", "computer science"] -> ["-2"]
> ### ["Russia", "Denmark", "Kazan"] -> []  
  

### **Блок-схема решения задачи**  

![диаграмма](diagram.jpg)


### **Решение:**  

### Для начала необходимо инициализировать переменные, необходимые для дальнейшей обработки программой.  

### 1. Строковую переменную string для хранения массива 
### 2. Переменную int для записи количества строк массива
### 3. Переменную int для хранения количества символов, участвующих в отборе выводимых данных
### 4. Переменную string для ввода информации в массив
### 5. Переменную string для перезаписи массива
```
1. String[] StringMassive;
2. int count;
3. int SymbolLimit = 3;
4. string EnterData;
5. string[] OldMassive;
```
### Далее организуем цикл для наполнения массива данными. В данном случае массив заполняем с клавиатуры самостоятельно. Наполнение масссива выполняем через циклы __do...while__ и __for__
### На входе проверяем, введены ли данные, если да - записываем их во временный массив, добавляем новый элемент и перезаписываем основной массив данных, если нет - переходим к выводу данных.

```
Console.WriteLine("Введите данные массива (для завершения нажмите клавишу Enter):");
count = 0;
StringMassive = new string[count];
do
    EnterData = Console.ReadLine();
    if (EnterData != "")
    count++;
    OldMassive = new string[count];
    for (int i = 0; i < OldMassive.Length - 1; i++)
    OldMassive[i] = StringMassive[i];
    OldMassive[count - 1] = EnterData;
    StringMassive = OldMassive;  
while (EnterData != "");
```  
### Через оператор __if__ сравниваем данные для вывода, согласно условию задачи (ограничение по количеству знаков) и циклом __for__ выводим данные, которые соответствуют условию. Добавляем скобки и дополнительно через условие __if...else__ убираем из вывода последнюю запятую, согласно примера вывода.  
```  
Console.Write("[");
    for (int i = 0; i < StringMassive.Length; i++)
        if (StringMassive[i].Length <= SymbolLimit)
            if (i != StringMassive.Length - 1)  
Console.Write($"{StringMassive[i]}, ");
            else
Console.Write($"{StringMassive[i]}");
Console.Write("]");
```  
### Пример вывода:
``` 
Введите данные массива (для завершения нажмите клавишу Enter):
hello
2
world
:-

[2, :-]
``` 
### Пример вывода c кавычками (как в примере):
Добавили кавычки
``` 
Console.Write("[");
    for (int i = 0; i < StringMassive.Length; i++)  //cчетчик
        {
            if (StringMassive[i].Length <= SymbolLimit)   
                if (i != StringMassive.Length - 1)       
                    Console.Write("\"" +StringMassive[i] +"\"" +", "); 
                    Console.Write("\"" +StringMassive[i] +"\"" +"");
        }
    Console.Write("]");
``` 

Выводится так
``` 
Введите данные массива (для завершения нажмите клавишу Enter):
hello
2
world
:-

["2", ":-"]
``` 
    
    