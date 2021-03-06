#Стандарты написания кода для LiveStreet

*Данный документ регламентирует стандарт написания кода для экосистемы LiveStreet.*

##1. Общий стиль

###1.1. Форматирование кода

При написании кода следует использовать табуляцию (не пробелы)

###1.2. Комментирование кода

При написании кода комментарии должны быть оформлены в виде многострочных комментариев:
~~~
/*
 * Это комментарий
 */
~~~
Допускается использование однострочных комментариев для временного комментирования строки кода. Для комментировани более одной строки кода рекомендуется использовать многострочные комментарии.

####1.2.1. Дополнительная справка в комментариях

Если участок кода нуждается в дополнительной подсказке или расширенном описании участка кода для будущих изменений, то следует использовать ключевое слово "tip":
~~~
/*
 * Это комментарий
 * tip: этот участок кода может быть дополнен дополнительной проверкой на айпи адрес пользователя, если будет нужно
 */
~~~

###1.3. Доработка кода

Если код в определенном месте будет нуждаться в доработке и на данный момент нет возможности выполнить эту доработку - следует в месте доработки добавить комментарий с ключевым словом "todo" в нижнем регистре с добавлением полного описания доработки:
~~~
/*
 * todo: добавить проверку корректности ввода данных
 */
~~~

##2. Стиль написания переменных

При написании кода используется [венгерская нотация](http://ru.wikipedia.org/wiki/%D0%92%D0%B5%D0%BD%D0%B3%D0%B5%D1%80%D1%81%D0%BA%D0%B0%D1%8F_%D0%BD%D0%BE%D1%82%D0%B0%D1%86%D0%B8%D1%8F "Венгерская нотация в Википедии") именования переменных. Данное правило распостраняется на простые функции и на классы.

###2.1. Основные префиксы переменных

Базовыми префиксами при написании переменных являются следующие:

* i - префикс для переменной целочисленного типа, независимо от разрядности и знака. Пример: `iCount`
* a - переменная-массив, независимо от типа значений. Пример: `aEntities`
* s - строка неограниченной длины. Пример: `sSql`
* b - булевая переменная, принимающая логическое true или false. Пример: `bSuccess`
* h - дескриптор, например, файлового потока. Пример: `hLogFile`
* o - объект для всех типов, например, сущность. Пример: `oTopic`
* m - значение смешанного типа. Например, если метод класса в качестве параметра может принимать id объекта или массив id объектов. Пример: `mIds`. Или если метод класса в качестве параметра может принимать id объекта или сущность. Пример: `mUser`. Если объект может принимать в переменную множественное число, например, id объекта или массив id объектов,
то написание переменной должно быть в множественном числе: `mIds` (а не `mId`).

###2.2. Имена переменных

Имя переменной должно лаконично расскрывать её предназначение, не быть слишком коротким или длинным. Плохие примеры именования переменных: `$i`, `$sTextForNewTargetTypeWithCompressedDataObjectsMixedBeforeWithServerResponse`

####2.2.1. В начале имени переменной должно быть основное её предназначение, а общий класификатор значения - в конце.

Хороший пример: `$iTopicsCount`, `$aFavouriteTopics`, `$bSuccessfullCheckingCurrent`

Плохой пример: `$iCountTopics`, `$aTopicsFavourite`, `$bCurrentSuccessfullChecking`