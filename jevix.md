Jevix
=====
***Jevix*** — библиотека для автоматического типографирования с открытым исходным кодом, унифицирующая HTML-разметку и контролирующая допустимые теги и атрибуты, что позволяет предовратить возможные XSS-атаки в контенте, размещаемого пользователями сайта.

Возможности Jevix
-----------------
- Фильтрация введённого пользователем текста с HTML разметкой на основе заданных правил о разрешённых тегах и атрибутах
- Исправление ошибок HTML и формирование валидного HTML или XHTML кода
- Предотвращение XSS-атак
- Применение правил набора текстов (типографика) для русского языка 

Преимущества Jevix
------------------
- Jevix работает на конечном автомате, а не на регулярных выражениях. Соответственно обратная идеология: вместо запрещающих правил разрешающие (всё что не разрешено — запрещено)
- XSS-фильтация, валидация, обработка HTML и типографирование в одном файле 

Недостатки Jevix
----------------
- Jevix разделяет строки br-ами. Делать абзацы (p) он не умеет, и, в существующей архитектурной концепции вряд ли научится

Настройка Jevix
---------------
Настройки Jevix находятся в файле `/config/jevix.php`. Это массив, который состоит из разрешенных тегов и их параметров. Сам Jevix используется в модуле `/engine/modules/text/Text.class.php`, через который проходят все публикуемые тексты. Например, чтобы получить возможность публиковать видео из ВКонтакте, нужно в функцию
~~~
public function VideoParser($sText)
~~~
до строки `return $sText;` добавить:
~~~
$sText = preg_replace('/<video>http:\/\/vk\.com\/(.*)<\/video>/Ui', '<iframe src="http://vk.com/$1" width="607" height="360" frameborder="0"></iframe>', $sText);
~~~

Настройка Jevix из плагина
--------------------------
http://livestreet.ru/blog/questions/11584.html