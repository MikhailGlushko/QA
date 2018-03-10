## 1. Сколько ключевых слов зарезервировано языком, что это за слова, какие из них не используются?
>50, два из них не используются: const, goto;
>
>Для запоминания это:
> - Примитивы (byte, short, int, long, char, float, double, boolean)
> - Циклы и ветвления (if, else, switch, case, default, while, do, break, continue, for)
. - Исключения (try, catch, finally, throw, throws)
> - Области видимости (private, protected, public)
> - Объявление \ Импорт (import, package, class, interface, extends, implements, static, final, void, abstract, native)
> - Создание \ Возврат \ Вызов (new, return, this, super)
> - Многопоточность (synchronized, volatile)
> - instanceof, enum, assert, transient, strictfp, const, goto

## 2. Из каких символов может состоять имя переменной (корректный идентификатор)?
>Имя или идентификатор переменной — это последовательность из строчных и заглавных латинских букв, цифр, а также символов «$» и «_». Имя переменной может начинаться с любого из перечисленных символов, кроме цифры.
>
>Технически возможно начать имя переменной также с «$» или «_», однако это запрещено соглашением по оформлению кода в Java (Java Code Conventions). Кроме того, символ доллара «$», по соглашению, никогда не используется вообще. В соответствии с соглашением имя переменной должно начинаться именно с маленькой буквы (с заглавной буквы начинаются имена классов). Пробелы при именовании переменных не допускаются.

## 3. Что значит слово “инициализация”?
>Инициализация (от англ. initialization, инициирование) — создание, активация, подготовка к работе, определение параметров. Приведение программы или устройства в состояние готовности к использованию. С точки зрения Java — выделение памяти под объект, например при создании MyClass myClass = new MyClass(). Таким образом будет выделена память под объект myClass (он будет инициализирован). Без инициализации (new MyClass()) запись MyClass myClass; просто резервирует имя (объявляется переменная myClass типа MyClass).

## 4. На какие основные группы можно поделить типы данных?
## 5. Какие примитивные типы вы знаете?
>**Примитивные**
> - byte (целые числа, 1 байт, [-128, 127])
> - short (целые числа, 2 байта, [-32768, 32767])
> - int (целые числа, 4 байта, [-2147483648, 2147483647])
> - long (целые числа, 8 байт, [-922372036854775808,922372036854775807])
> - float (вещественные числа, 4 байта)
> - double (вещественные числа, 8 байт)
> - char (символ Unicode, 2 байта, [0, 65536])
> - boolean (значение истина/ложь, используется int, зависит от JVM)
>
>**Ссылочные.** В ссылочные типы входят все классы, интерфейсы, массивы.

## 6. Что вы знаете о преобразовании примитивных типов данных, есть ли потеря данных, можно ли преобразовать логический тип?
>Преобразование может быть неявным и явным (приведение типов). Неявное преобразование может выполняться если:
> 1.  типы совместимы (например — оба целочисленные)
> 2.  размер «принимающего» типа больше чем у того, который преобразуется (так называемое «преобразование с расширением»)
>
>Явное преобразование имеет вид переменная_нового_типа = (новый_тип) имя переменной;
>
>При повышении типа byte>short; short>int; int>long; float>double; char>int информация не потеряется. При сужении возможна потеря информации (см. пример выше byte = (byte) int).
>
>При различных операциях может происходить повышение типов в порядке «усиления» к более информативному типу. Например складывая int и double получим тип double. Но есть и особенность, например сложив double (8 байт) и long (8 байт) Java оставит знаки после запятой (double), а не более «длинный» тип. Аналогичный пример с вещественной частью
>
>Кратко можно записать такие правила:
> - byte, short, char в выражениях всегда повышаются до int
> - если в выражении участвует тип long — то именно к этому типу будет приведён результат
> - если в выражении участвует float — то результат приводится к float
> - если один из операндов имеет тип double — то к этому типу будет приведён весь результат
> - При выборе между длиной и возможностью сохранить дробную часть — будет выбрана дробная часть

## 7.  Какими значениями инициализируются переменные по умолчанию?
>Числа инициализируются 0 или 0.0. Объекты (в том числе String) — null, char — \u0000; boolean — false;

## 8.  Как передается значение переменной (по ссылке/значению)?
>Постоянный холивар по этому вопросу, видимо, связан с переводом на русский язык некоторых терминов, а так же работой Java с примитивами, строками и ссылочными объектами. По английски всё звучит строго — Java is always pass-by-value. Обычно спор вызывают особенности языка относящиеся к пониманию примитивов, ссылок и объектов в Java (и то, что некоторые из них неизменяемые). Итак:
> - Java передает всё по значению. Java никогда не передает ничего по ссылке. Примитивы, ссылки, null — всё передается по значению, не по «ссылке».
> - Передача по значению: Когда передается параметр в метод, то параметр копируется в другую переменную и она передается в метод. Поэтому это и называется «передача по значению».
> - Передача по ссылке: Если мы передаем в метод ссылочный тип (объект), то так же происходит передача копии этого объекта (ссылки), которая указывает на какую-либо область памяти (можно назвать ссылку — «указателем»). Изменив что-то в области памяти, будут изменены все объекты, которые ссылаются на эту область памяти. Отсюда идет название «передача по ссылке», хотя передается всё то же значение, просто значением является указатель на область памяти.

## 9. то вы знаете о функции main, какие обязательные условия ее определения?
>Обязательная запись  public static void main(String[] args) {/*тело метода*/ }
>
>Метод main() — точка входа в программу. Может быть несколько методов main. Входные параметры — только массив строк. Если этого метода не будет, то компиляция возможна, но при запуске будет Error: Main method not found.

## 10. Какие логические операции и операторы вы знаете?
## 11. В чем разница краткой и полной схемы записи логических операторов?

## 12. Что такое таблица истинности?
>Таблица истинности — это таблица, описывающая логическую функцию.

## 13.  Что такое тернарный оператор выбора?
>В языке Java есть также специальный тернарный условный оператор, которым можно заменить определённые типы операторов if-then-else — это оператор ?:
>
>Тернарный оператор использует три операнда. Выражение записывается в следующей форме:
>логическоеУсловие ? выражение1 : выражение2
>Если логическоеУсловие равно true, то вычисляется выражение1 и его результат становится результатом выполнения всего оператора. Если же логическоеУсловие равно false, то вычисляется выражение2, и его значение становится результатом работы оператора. Оба операнда выражение1 и выражение2 должны возвращать значение одинакового (или совместимого) типа.

## 14. Какие унарные и бинарные арифметические операции вы знаете?
>Унарные операции выполняются над одним операндом, бинарные — над двумя операндами, а также тернарные — выполняются над тремя операндами. Операндом является переменная или значение (например, число), участвующее в операции.
>
>Пример унарных арифметических операций:
> - ++ — постфиксный/префиксный инкремент, увеличивает значение целочисленной переменной на 1;
> - — (двойной минус) — постфиксный/префиксный декремент, уменьшает значение целочисленной переменной на 1;
> - + — оставляет знак числа;
> - — — изменяет знак числа.
>Слово постфиксный означает, что операция применится к операнду после вычисления всего выражения, в которое операнд входит. Аналогично префиксный означает, что операция применится до вычисления выражения.
>
>Пример бинарных арифметических операций:
> - + — сложение чисел или строк;
> - —  — вычитание чисел;
> - * — умножения чисел;
> - / — деления чисел;
> - % — вычисление остатка от деления чисел.
>Операция вычисления остатка от деления применима как к целым числам, так и к вещественным.

## 15. Какие побитовые операции вы знаете?

## 16. Какова роль и правила написания оператора выбора (switch)?
>Оператор switch сравнивает аргумент на равенство с предложенным значением.

## 17. Какие циклы вы знаете, в чем их отличия?
>В Java используются циклы for, while, do-while.

## 18. Что такое “итерация цикла”?
>Это одноразовое выполнение кода, размещенного в теле цикла.

## 19.  Какие параметры имеет цикл for, можно ли их не задать?

## 20. Какой оператор используется для немедленной остановки цикла?21. Какой оператор используется для перехода к следующей итерации цикла?
> - break; — выход из цикла (не затрагивает внешний цикл).
> - continue; — заканчивает выполнение кода в этом теле цикла. Переход к следующей итерации.

## 21. Что такое массив?
>Массив (в некоторых языках программирования также таблица, ряд, матрица) — тип или структура данных в виде набора компонентов (элементов массива), расположенных в памяти непосредственно друг за другом. При этом доступ к отдельным элементам массива осуществляется с помощью индексации, то есть ссылки на массив с указанием номера (индекса) нужного элемента. За счёт этого, в отличие от списка, массив является структурой с произвольным доступом.
>
>Размерность массива — это количество индексов, необходимое для однозначного доступа к элементу массива. Форма или структура массива — количество размерностей плюс размер (протяжённость) массива для каждой размерности; может быть представлена одномерным массивом.
>
>В Java массивы являются объектами. Это значит, что имя, которое даётся каждому массиву, лишь указывает на адрес какого-то фрагмента данных в памяти. Кроме адреса в этой переменной ничего не хранится. Индекс массива, фактически, указывает на то, насколько надо отступить от начального элемента массива в памяти, чтоб добраться до нужного элемента.

## 22. Какие виды массивов вы знаете?
>В Java — одномерные и многомерные массивы.

## 23. Что вы знаете о классах оболочках?
>Для каждого примитивного типа есть соответствующий класс (Byte, Double, Float, Integer, Long, Short). Числовые классы имеют общего предка — абстрактный класс Number, в котором описаны шесть методов, возвращающих числовое значение, содержащееся в классе, приведенное к соответствующему примитивному типу: byteValue(), doubleValue(), floatValue(), intValue(), longValue(), shortValue(). Эти методы переопределены в каждом из шести числовых классов-оболочек.

## 24. Что такое автоупаковка (boxing/unboxing)?
>Это автоматическое преобразование из примитивных типов данных к ссылочным и наоборот.

## 7. 