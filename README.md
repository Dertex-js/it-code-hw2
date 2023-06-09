# Frontend разработчик. Домашнее задание №2

В данном домашнем задании вам необходимо реализовать функции, представленные ниже.
Для обработки ошибок, встречающихся при реализации, необходимо воспользоваться синтаксисом
`throw new Error(<код ошибки из задания>)`. Подробнее можно прочесть [здесь](https://learn.javascript.ru/try-catch).

###### Задачи повышеной сложности помечены \* крайне желательны, но не обязательны к выполнению.

## 1. Суммирование аргументов
Реализуйте функцию `sum`, которая принимает произвольное количество аргументов и возвращает их сумму.

**Ошибки, которые должны быть обработаны:**
1) Не переданы хотя бы два аргумента. Код ошибки `INVALID_ARGUMENTS_COUNT`.
2) Хотя бы один из аргументов не типа `number`. Код ошибки `INVALID_ARGUMENT`.

**Примеры использования:**
1) `sum(1, 2, 3);        // 6`
2) `sum();               // ошибка с кодом INVALID_ARGUMENTS_COUNT`
3) `sum(0, 1, '1', 2); // ошибка с кодом INVALID_ARGUMENT`

## 2. Пересечение двух массивов
Реализуйте функцию `intersection`, которая принимает два массива чисел и возвращает массив чисел, присутствующих в первом и во втором массивах.

**Ошибки, которые должны быть обработаны:**
1) Не переданы два аргумента. Код ошибки `INVALID_ARGUMENTS_COUNT`.
2) Хотя бы один из аргументов функции не массив. Код ошибки `INVALID_ARGUMENT`.
3) Хотя бы один из элементов массива не типа `number`. Код ошибки `INVALID_ELEMENT_IN_ARRAY`.

**Примеры использования:**
1) `intersection([1], [2]);            // []`
2) `intersection([1, 2], [3, 2, 1]);   // [1, 2]`
3) `intersection([1, 1], [1, 1]);      // [1]`
4) `intersection([1, 2, 1], [1]);      // [1]`
5) `intersection([], []);              // []`
6) `intersection()                     // ошибка с кодом INVALID_ARGUMENTS_COUNT`
7) `intersection([], '[]')             // ошибка с кодом INVALID_ARGUMENT`
8) `intersection([], [1, '2'])         // ошибка с кодом INVALID_ELEMENT_IN_ARRAY`

## 3. Сортировка строк
Реализуйте функцию `sort`, которая принимает строку, состоящую из слов, разделенных пробелами.
В каждом слове предложения она сортирует буквы в порядке кодовых точек Unicode, а слова по количеству букв в них,
и возвращает результат в виде строки.
Если в слове попадается буква в верхнем регистре, она должна быть приведена к нижнему.

**Ошибки, которые должны быть обработаны:**
1) Переданный аргумент не типа `string`. Код ошибки `INVALID_ARGUMENT`.

**Примеры использования:**
1) `sort('hello world');            // 'ehllo dlorw'`
2) `sort('1234 111');               // '111 1234'`
3) `sort(11);                       // ошибка с кодом INVALID_ARGUMENT`

## 4. Фильтрация не анаграмм
Реализуйте функцию `removeAnagrams`, которая принимает массив строк и удаляет из данного массива строки, являющиеся анаграммами.

**Ошибки, которые должны быть обработаны:**
1) Переданный аргумент не массив. Код ошибки `INVALID_ARGUMENT`.
2) В переданном массиве хотя бы один элемент не типа `string`. Код ошибки `INVALID_ELEMENT_IN_ARRAY`.

**Примеры использования:**
1) `removeAnagrams(['cat', 'act', 'arc']);  // ['arc']`
2) `removeAnagrams(['car', 'arc']);         // []`
3) `removeAnagrams('str');                  // ошибка с кодом INVALID_ARGUMENT`
4) `removeAnagrams(['str', 5]);             // ошибка с кодом INVALID_ELEMENT_IN_ARRAY`

## 5. Дополнительные методы массива
Реализуйте функцию `patchArrays`, которая для всех массивов добавляет следующие методы:
1) Метод `count` возвращает длину массива.
2) Метод `insert` осуществляет вставку элемента в массив по индексу и возвращает измененный данный массив. В случае отрицательного индекса, элемент становится первым. Если индекс > длинны массива, элемент становится последним.
3) Метод `remove` удаляет из массива первый встречающийся элемент с таким значением и возвращает измененный данный массив. Если такого элемента в массиве нет, он возвращает неизмененный данный массив.

[Подсказка](https://learn.javascript.ru/native-prototypes)

**Ошибки, которые должны быть обработаны:**
1) Первый аргумент метода `insert` не типа `number`. Код ошибки `INVALID_ARGUMENT`.

**Примеры использования:**
1) `[1, 2, 3].count();    // 3`
2) `[].count();           // 0`
3) `const arr = [];`<br/>
   `arr.insert(10, 1);     // [1]`<br/>
   `arr.insert(1, 'name'); // [1, 'name']`<br/>
   `arr.insert(1, null);   // [1, null, 'name']`<br/>
   `arr.insert(0, null);   // [null, 1, null, 'name']`<br/>
   `arr.remove(2);         // [null, 1, null, 'name']`<br/>
   `arr.remove(1);         // [null, null, 'name']`<br/>
   `arr.remove('name');    // [null, null]`<br/>
   `arr.remove(null);      // [null]`<br/>
   `arr.remove(null).insert('2');      // ['2']`
4) `[].insert('0', null) // ошибка с кодом INVALID_ARGUMENT`

## 6. Умножение с частичным применением*
Реализуйте функцию `multiply`.

[Подсказка](https://learn.javascript.ru/currying-partials)

**Ошибки, которые должны быть обработаны:**
1) Один из аргументов не типа `number`. Код ошибки `INVALID_ARGUMENT`.

**Примеры использования:**
1) `const multiplyByTen = multiply(10);`<br/>
   `multiplyByTen(2);   // 20`
2) `const multiplyByTwo = multiply(2);`<br/>
   `multiplyByTwo(3);   // 6`
3) `const multiplyByTwo = multiply(["two"]); ошибка с кодом INVALID_ARGUMENT`
4) `const multiplyByTwo = multiply(2);`<br/>
   `multiplyByTwo('3');   // ошибка с кодом INVALID_ARGUMENT`

## 7.1. Обход дерева в глубину* ([dfs](https://en.wikipedia.org/wiki/Depth-first_search))
Реализуйте функцию `dfs`, которая принимает в качестве аргумента объект, отражающий небинарное дерево(узел может иметь больше двух потомков) и возвращает массив узлов, соответствующий обходу в глубину.
Обход осуществляется слева направо (по возрастанию индекса в массиве).
<pre>
Пример графа:
            A 
          /   \ 
         B     C 
        /  \   / \ 
       D    E F   G

Этот же граф в виде объекта:
const graph = {
    A: ['B', 'C'],
    B: ['D', 'E'],
    C: ['F', 'G'],
    D: [],
    E: [],
    F: [],
    G: [],
};
</pre>

**Ошибки, которые должны быть обработаны:**
1) Переданный аргумент не объект. Код ошибки `INVALID_ARGUMENT`.

**Примеры использования:**
1) `dfs(graph) // ['A', 'B', 'D', 'E', 'C', 'F', 'G']`
2) `dfs('{}') // ошибка с кодом INVALID_ARGUMENT`

## 7.2. Обход дерева в ширину* ([bfs](https://en.wikipedia.org/wiki/Breadth-first_search))
Реализуйте функцию `bfs`, которая принимает в качестве аргумента объект, отражающий небинарное дерево(узел может иметь больше двух потомков) и возвращает массив узлов, соответствующий обходу в ширину.
Обход осуществляется слева направо(по возрастанию индекса в массиве).
<pre>
Пример графа:
            A 
          /   \ 
         B     C 
        /  \   / \ 
       D    E F   G

Этот же граф в виде объекта:
const graph = {
    A: ['B', 'C'],
    B: ['D', 'E'],
    C: ['F', 'G'],
    D: [],
    E: [],
    F: [],
    G: [],
};
</pre>

**Ошибки, которые должны быть обработаны:**
1) Переданный аргумент не объект. Код ошибки `INVALID_ARGUMENT`.

**Примеры использования:**
1) `bfs(graph) // ['A', 'B', 'С', 'D', 'E', 'F', 'G']`
2) `bfs('{}') // ошибка с кодом INVALID_ARGUMENT`