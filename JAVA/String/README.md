## 1. Какие “строковые” классы вы знаете?
> - public final class String implements java.io.Serializable, Comparable<String>, CharSequence
> - public final class StringBuffer extends AbstractStringBuilder implements java.io.Serializable, CharSequence
> - public final class StringBuilder extends AbstractStringBuilder implements java.io.Serializable, CharSequence

## 2. Какие основные свойства “строковых” классов (их особенности)?
>Все строковые классы — final (следовательно от них нельзя унаследоваться).
>
>**String.**
>Строка — объект, что представляет последовательность символов. Для создания и манипулирования строками Java платформа предоставляет общедоступный финальный (не может иметь подклассов) класс java.lang.String. Данный класс является неизменяемым (immutable) — созданный объект класса String не может быть изменен.
>
>**StringBuffer**
>Строки являются неизменными, поэтому частая их модификация приводит к созданию новых объектов, что в свою очередь расходует драгоценную память. Для решения этой проблемы был создан класс java.lang.StringBuffer, который позволяет более эффективно работать над модификацией строки. Класс является mutable, то есть изменяемым — используйте его, если Вы хотите изменять содержимое строки. StringBuffer может быть использован в многопоточных средах, так как все необходимые методы являются синхронизированными.
>
>**StringBuilder**
>StringBuilder — класс, что представляет изменяемую последовательность символов. Класс был введен в Java 5 и имеет полностью идентичный API с StringBuffer. Единственное отличие — StringBuilder не синхронизирован. Это означает, что его использование в многопоточных средах нежелательно. Следовательно, если вы работаете с многопоточностью, Вам идеально подходитStringBuffer, иначе используйте StringBuilder, который работает намного быстрее в большинстве реализаций.

## 3. Можно ли наследовать строковый тип, почему?
>Классы объявлены final, поэтому наследоваться не получится.

## 4. Дайте определение понятию конкатенация строк.
>Конкатенация — операция объединения строк, что возвращает новую строку, что является результатом объединения второй строки с окончанием первой

## 5. Как преобразовать строку в число?
>У каждой обертки для примитивов есть свой метод valueOf(String s), который возвращает преобразованное численное значение из строки. При этом форматы строки и принимаемого типа должны совпадать. 

## 6.  Как сравнить значение двух строк?
>Оператор == работает с ссылками объекта String. Если две переменные String указывают на один и тот же объект в памяти, сравнение вернет результат true. В противном случае результат будет false, несмотря на то что текст может содержать в точности такие же символы. Оператор == не сравнивает сами данные типа char. Для сравнения посимвольно необходимо использовать метод equals();

## 7.  Как перевернуть строку?
>>String s = "ABCDEFG";
>>StringBuilder stringBuilder = new StringBuilder(s);
>>stringBuilder.reverse();
>>System.out.println(stringBuilder.toString()); //GFEDCBA
>Можно и алгоритмом переставляя каждый char, но это на ваше усмотрение:).

## 8.  Как работает сравнение двух строк?
>Строка в Java — это отдельный объект, который может не совпадать с другим объектом, хотя на экране результат выводимой строки может выглядеть одинаково. Просто Java в случае с логическим оператором == (а также !=) сравнивает ссылки на объекты.
>
>Метод equals сравнивает посимвольно на эквивалентность.

## 9. Как обрезать пробелы в конце строки?
>trim()

## 10. Как заменить символ в строке?
>Можно использовать метод replace(CharSequence target, CharSequence replacement), который меняет символы в строке. Можно преобразовать в массив символов и заменить символ там. Можно использовать StringBuilder и метод setCharAt(int index, char ch)

## 11. Как получить часть строки?
>Метод substring(int beginIndex, int lastIndex) — возвращает часть строки по указанным индексам.

## 12. Дайте определение понятию “пул строк”.
>Пул строк – это набор строк, который хранится в памяти Java heap. Мы знаем, что String это специальный класс в Java, и мы можем создавать объекты этого класса, используя оператор new точно так же, как и создавать объекты, предоставляя значение строки в двойных кавычках.
>
>Пул строк возможен исключительно благодаря неизменяемости строк в Java и реализации идеи интернирования строк. Пул строк также является примером паттерна Приспособленец (Flyweight).
>Пул строк помогает экономить большой объем памяти, но с другой стороны создание строки занимает больше времени.
>Когда мы используем двойные кавычки для создания строки, сначала ищется строка в пуле с таким же значением, если находится, то просто возвращается ссылка, иначе создается новая строка в пуле, а затем возвращается ссылка.
>Тем не менее, когда мы используем оператор new, мы принуждаем класс String создать новый объект строки, а затем мы можем использовать метод intern() для того, чтобы поместить строку в пул, или получить из пула ссылку на другой объект String с таким же значением.

## 13. Какой метод позволяет выделить подстроку в строке?
>В дополнении к «как получить часть строки» можно использовать метод string.indexOf(char c), который вернет индекс первого вхождения символа. Таким образом потом можно использовать этот номер для выделения подстроки с помощью substring();

## 14. Как разбить строку на подстроки по заданному разделителю?
>Мы можем использовать метод split(String regex) для разделения строки на массив символов, используя в качестве разделителя регулярное выражение. Метод split(String regex, int numOfStrings) является перегруженным методом для разделения строки на заданное количество строк. Мы можем использовать обратную черту для использования специальных символов регулярных выражений в качестве обычных символов.

## 15. Какой метод вызывается для преобразования переменной в строку?
>toString()

## 16. Как узнать значение конкретного символа строки, зная его порядковый номер в строке?
>str.charAt(int i) вернет символ в по индексу.

## 17.  Как найти необходимый символ в строке?
>str.indexOf(char ch) или lastIndexOf(ch c) — вернет индекс первого и последнего вхождения символа.

## 18. Можно ли синхронизировать доступ к строке?
>String сам по себе потокобезопасный класс. Если мы работаем с изменяемыми строками, то нужно использовать StringBuffer.

## 19.  Что делает метод intern()?
>Когда метод intern() вызван, если пул строк уже содержит строку, эквивалентную к нашему объекту, что подтверждается методом equals(Object), тогда возвращается ссылка на строку из пула. В противном случае объект строки добавляется в пул и ссылка на этот объект возвращается.
>Этот метод всегда возвращает строку, которая имеет то же значение, что и текущая строка, но гарантирует что это будет строка из пула уникальных строк.

## 20. Чем отличаются и что общего у классов String, StringBuffer и StringBuilder?

## 21. Как правильно сравнить значения строк двух различных объектов типа String и StringBuffer?
>Привести их к одному типу и сравнить.

## 22. Почему строка неизменная и финализированная в Java?
>Есть несколько преимуществ в неизменности строк:
> - Строковый пул возможен только потому, что строка неизменна в Java, таким образом виртуальная машина сохраняет много места в памяти(heap space), поскольку разные строковые переменные указывают на одну переменную в пуле. Если бы строка не была неизмененяемой, тогда бы интернирование строк не было бы возможным, потому что если какая-либо переменная изменит значение, это отразится также и на остальных переменных, ссылающихся на эту строку.
> - Если строка будет изменяемой, тогда это станет серьезной угрозой безопасности приложения. Например, имя пользователя базы данных и пароль передаются строкой для получения соединения с базой данных и в программировании сокетов реквизиты хоста и порта передаются строкой. Так как строка неизменяемая, её значение не может быть изменено, в противном случае любой хакер может изменить значение ссылки и вызвать проблемы в безопасности приложения.
> - Так как строка неизменная, она безопасна для многопоточности и один экземпляр строки может быть совместно использован различными нитями. Это позволяет избежать синхронизации для потокобезопасности, строки полностью потокобезопасны.
> - Строки используются в Java classloader и неизменность обеспечивает правильность загрузки класса при помощи Classloader. К примеру, задумайтесь об экземпляре класса, когда вы пытаетесь загрузить java.sql.Connection класс, но значение ссылки изменено на myhacked.Connection класс, который может осуществить нежелательные вещи с вашей базой данных.
> - Поскольку строка неизменная, её hashcode кэшируется в момент создания и нет необходимости рассчитывать его снова. Это делает строку отличным кандидатом для ключа в Map и его обработка будет быстрее, чем других ключей HashMap. Это причина, почему строка наиболее часто используемый объект, используемый в качестве ключа HashMap.

## 23. Почему массив символов предпочтительнее строки для хранения пароля?
>Строка неизменяемая в Java и хранится в пуле строк. С тех пор, как она была создана, она остается в пуле, пока не будет удалена сборщиком мусора, поэтому, когда мы думаем, что закончили работу с паролем, он остается доступным в памяти некоторое время, и нет способа избежать этого. Это риск безопасности, поскольку кто-либо, имеющий доступ к дампу памяти сможет найти пароль в виде чистого текста.
>Если мы используем массив символов для хранения пароля, мы можем очистить его после того, как закончим с ним работать. Таким образом, мы можем контролировать, как долго он находится в памяти, что позволяет избежать риска безопасности, свойственного строке.

## 24. Почему строка является популярным ключом в HashMap в Java?
>Поскольку строки неизменны, их хэшкод кэшируется в момент создания, и не требует повторного пересчета. Это делает строки отличным кандидатом для ключа в Map и они обрабатываются быстрее, чем другие объекты-ключи HashMap. Вот почему строки преимущественно используются в качестве ключей HashMap.

## 25. Напишите метод удаления данного символа из строки.
>Мы можем использовать метод replaceAll для замены всех вхождений в строку другой строкой. Обратите внимание на то, что метод получает в качестве аргумента строку, поэтому мы используем класс Character для создания строки из символа, и используем её для замены всех символов на пустую строку.
