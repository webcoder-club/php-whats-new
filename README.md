# Что нового в PHP
Вначале каждого списка идут изменения, которые затрагивают **производительность**, затем новая функциональность.

### PHP 5.0 (29.06.2003)

### PHP 5.1 (24.11.2005)
* **Скомпилированные переменные**
* **Специализированный исполнитель (Specialized executor)**
* **Кеш real-path**
* **Ускоренная обработка выражения switch()**
* **Ускоренные функции массивов**
* **Ускоренное извлечение переменных**
* **Ускоренный вызов «магических» методов**
* Добавлена поддержка констант класса и статических элементов внутри класса
* Добавлен typehint - `array`

### PHP 5.2 (02.11.2006)
* **Новый диспетчер памяти**
* **Оптимизированное копирование массивов/хеш-таблиц**
* **Оптимизированные выражения require_once() и include_once()**
* **Небольшие оптимизации специфических внутренних функций**
* **Улучшенное компилирование HEREDOC и компилирование интерполированных строк**
* Добавлена поддержка конструкторов в интерфейсах

### PHP 5.3 (30.06.2009)
* **Сегментированный стек VM**
* **Бесстековая VM**
* **Замена констант в ходе компилирования**
* **Ленивая инициализация таблицы символов**
* **Улучшение real-path кеша**
* **Улучшение скорости runtime и потребления памяти**
* **Ускоренный парсинг языка**
* **Улучшение размера двоичных PHP-файлов и запуска кода (code startup)**
* Добавлена поддержка [пространства имен](http://php.net/manual/ru/language.namespaces.php)
* Добавлена поддержка [позднего статического связывания](http://php.net/manual/ru/language.oop5.late-static-bindings.php)
* Добавлена поддержка [меток перехода](http://php.net/manual/ru/control-structures.goto.php)
* Добавлена поддержка нативных [замыканий](http://php.net/manual/ru/functions.anonymous.php)(closures/Lambda/Anonymous)
* Появились два магических метода: [__callStatic()](http://php.net/manual/ru/language.oop5.overloading.php#object.callstatic) и [__invoke()](http://php.net/manual/ru/language.oop5.magic.php#object.invoke)
* Появилась поддержка синтаксиса [Nowdoc](http://php.net/manual/ru/language.types.string.php#language.types.string.syntax.nowdoc), подобный [Heredoc](http://php.net/manual/ru/language.types.string.php#language.types.string.syntax.heredoc), но с одинарными кавычками
* Теперь возможно использовать [Heredoc](http://php.net/manual/ru/language.types.string.php#language.types.string.syntax.heredoc) для инициализации статических переменных и свойств/констант классов
* [Heredoc](http://php.net/manual/ru/language.types.string.php#language.types.string.syntax.heredoc) теперь может быть объявлен используя двойные кавычки, дополняющие синтаксис [Nowdoc](http://php.net/manual/ru/language.types.string.php#language.types.string.syntax.nowdoc)
* Константы теперь могут быть объявлены вне класса, используя ключевое слово const
* У [тернарного оператора](http://php.net/manual/ru/language.operators.comparison.php#language.operators.comparison.ternary) есть теперь сокращенный вид: ```?:```
* Обертка (wrapper) [HTTP-потока](http://php.net/manual/ru/wrappers.http.php) стала воспринимать коды статуса от 200 до 399 как успешные.
* Стал возможен динамический доступ к статическим методам:
  ```php
  <?php
  class C {
     public static $foo = 123;
  }
  
  $a = "C";
  echo $a::$foo;
  ```
  Результат выполнения данного примера:
  ```
  13
  ```
* [Исключения](http://php.net/manual/ru/language.exceptions.php) теперь могут быть вложенными:
  ```php
  <?php
  class MyCustomException extends Exception {}
  
  try {
      throw new MyCustomException("Exceptional", 112);
  } catch (Exception $e) {
      /* Обратите внимание, что для передачи $e
       * в RuntimeException используется третий параметр. */
      throw new RuntimeException("Rethrowing", 911, $e);
  }
  ```
* Добавлен [сборщик мусора](http://php.net/manual/ru/features.gc.php) для циклических ссылок. Он включен по умолчанию
* Функция [mail()](http://php.net/manual/ru/function.mail.php) теперь поддерживает журналирование отправки письма с помощью директивы [mail.log](http://php.net/manual/ru/mail.configuration.php#ini.mail.log).
 (Примечание: это применимо только для писем, отправленных этой функцией.)


### PHP 5.4 (01.03.2012)
* **Отложенное размещение хеш-таблицы**
* **Константные таблицы (Constant tables)**
* **Рантаймовые кеши привязки (binding caches)**
* **Интернированные строки (Interned Strings)**
* **Улучшенный уровень вывода (output layer)**
* **Улучшена производительность тернарных операторов при использовании массивов**
* Добавлен typehint - `callable`
* Добавлена поддержка [трейтов](http://php.net/manual/ru/language.oop5.traits.php)
* Добавлен короткий синтаксис объявления массивов. Например,
  `$a = [1, 2, 3, 4];`
  или
  `$a = ['one' => 1, 'two' => 2, 'three' => 3, 'four' => 4];`
* Добавлена возможность разыменования массивов, возвращаемых функциями
Например: `foo()[0]`
* Классы для создания анонимных функций ([Closures](http://php.net/manual/ru/functions.anonymous.php)) теперь поддерживают $this
* Оператор `<?=` теперь доступен всегда, несмотря на значение _php.ini_ опции `short_open_tag`
* Добавлена возможность получения доступа к члену класса при создании экземпляра. Например: (new Foo)->bar().
* Теперь поддерживается такой синтаксис: Class::{expr}().
* Добавлен бинарный формат задания чисел, например: 0b001001101.
* Улучшены сообщения об ошибках разбора и предупреждения о несовместимых аргументах.
* Расширение по работе с сессиями теперь может отслеживать [процесс загрузки](http://php.net/manual/ru/session.upload-progress.php) файлов.
* Встроенный [веб-сервер в режиме командной строки](http://php.net/manual/ru/features.commandline.webserver.php) для разработчиков.

### PHP 5.5 (20.06.2013)
* **Улучшено соглашение о вызове (calling convention) виртуальной машины**
* **Интеграция [OPcache](http://php.net/manual/ru/book.opcache.php)**
* **Другие оптимизации движка Zend**
* Добавлены [Генераторы](http://php.net/manual/ru/language.generators.php)
* Добавлено ключевое слово [finally](http://php.net/manual/ru/language.exceptions.php#language.exceptions.finally)
* foreach теперь поддерживает [list()](http://php.net/manual/ru/function.list.php)
  К примеру:
  ```php
  <?php
  $array = [
      [1, 2],
      [3, 4],
  ];
  
  foreach ($array as list($a, $b)) {
      echo "A: $a; B: $b\n";
  }
  ```
  Результат выполнения данного примера:
  ```
  A: 1; B: 2
  A: 3; B: 4
  ```
* [empty()](http://php.net/manual/ru/function.empty.php) поддерживает произвольные выражения
  К примеру:
  ```php
  <?php
  function always_false() {
      return false;
  }
  
  if (empty(always_false())) {
      echo "Это будет напечатано.\n";
  }
  
  if (empty(true)) {
      echo "Это не будет напечатано.\n";
  }
  ```
  Результат выполнения данного примера:
  ```
    Это будет напечатано.
  ```
* Литералы [array](http://php.net/manual/ru/language.types.array.php) и [string](http://php.net/manual/ru/language.types.string.php) разыменовываются
  К примеру:
  ```php
  <?php
  echo 'Разыменовывание массива: ';
  echo [1, 2, 3][0];
  echo "\n";
  
  echo 'Разыменовывание строки: ';
  echo 'PHP'[0];
  echo "\n";
  ```
  Результат выполнения данного примера:
  ```
  Разыменовывание массива: 1
  Разыменовывание строки: P
  ```
* Разрешение имен класса с помощью [::class](http://php.net/manual/ru/language.oop5.basic.php#language.oop5.basic.class.class)
  Теперь можно использовать конструкцию ClassName::class для получения полностью определенного имени класса ClassName.
  К примеру:
  ```php
  <?php
  namespace Name\Space;
  class ClassName {}
  
  echo ClassName::class;
  
  echo "\n";
  ```
  Результат выполнения данного примера:
    ```
    Name\Space\ClassName
    ```
* foreach теперь поддерживает нескалярные ключи
* Улучшения в GD
  * Поддержка зеркального отражения с помощью новой функции [imageflip()](http://php.net/manual/ru/function.imageflip.php)
  * Продвинутые возможности обрезки с помощью новых функций [imagecrop()](http://php.net/manual/ru/function.imagecrop.php) и [imagecropauto()](http://php.net/manual/ru/function.imagecropauto.php)
  * Поддержка чтения и записи WebP с помощью функций [imagecreatefromwebp()](http://php.net/manual/ru/function.imagecreatefromwebp.php) и [imagewebp()](http://php.net/manual/ru/function.imagewebp.php) соответственно
### PHP 5.6 (28.08.2014)
* **Оптимизирована обработка пустых строк, минимизирована необходимость в размещении новых пустых значений**
* Константные выражения.
  Теперь стало возможно представить скалярное выражение, включающее цифровой и строковые литералы и/или константы,
  в то время где ранее ожидалось статическое значение, например,
  в объявлениях констант или значениях агрументов функцуий по-умолчанию.
  К примеру:
    ```php
    <?php
    const ONE = 1;
    const TWO = ONE * 2;
    
    class C {
        const THREE = TWO + 1;
        const ONE_THIRD = ONE / self::THREE;
        const SENTENCE = 'The value of THREE is '.self::THREE;
    
        public function f($a = ONE + self::THREE) {
            return $a;
        }
    }
    
    echo (new C)->f()."\n";
    echo C::SENTENCE;
    ```
    Результат выполнения данного примера:
    ```
    4
    The value of THREE is 3
    ```
* Также можно определить массив array с использованием ключевого слова `const`:
  К примеру:
  ```php
  <?php
  const ARR = ['a', 'b'];
  echo ARR[0];
  ```
  Результат выполнения данного примера:
  ```
  a
  ```
* Функции с переменным количеством аргументов теперь можно реализовывать используя оператор `...`,
  вместо того, чтобы полагаться на [func_get_args()](http://php.net/manual/ru/function.func-get-args.php)
  К примеру:
  ```php
  <?php
  function f($req, $opt = null, ...$params) {
      // $params is an array containing the remaining arguments.
      printf('$req: %d; $opt: %d; number of params: %d'."\n",
             $req, $opt, count($params));
  }
  
  f(1);
  f(1, 2);
  f(1, 2, 3);
  f(1, 2, 3, 4);
  f(1, 2, 3, 4, 5);
  ```
  Результат выполнения данного примера:
  ```
   $req: 1; $opt: 0; number of params: 0
   $req: 1; $opt: 2; number of params: 0
   $req: 1; $opt: 2; number of params: 1
   $req: 1; $opt: 2; number of params: 2
   $req: 1; $opt: 2; number of params: 3
  ```
* Развертывание аргументов с помощью `...`.
  Массивы и объекты реализующие интерфейс Traversable могут быть развернуты в список аргументов
  при передаче в функцию с помощью оператора ....
  К примеру:
    ```php
    <?php
    function add($a, $b, $c) {
        return $a + $b + $c;
    }
    
    $operators = [2, 3];
    echo add(1, ...$operators);
    ```
    Результат выполнения данного примера:
    ```
    6
    ```
* Был добавлен право-ассоциативный оператор `**`, обозначающий возведение в степень.
  Так же доступен короткий синтаксис `**=`.
  К примеру:
    ```php
    <?php
    printf("2 ** 3 ==      %d\n", 2 ** 3);
    printf("2 ** 3 ** 2 == %d\n", 2 ** 3 ** 2);
    
    $a = 2;
    $a **= 3;
    printf("a ==           %d\n", $a);
    ```
    Результат выполнения данного примера:
    ```
    2 ** 3 ==      8
    2 ** 3 ** 2 == 512
    a ==           8
    ```  
* Оператор use был расширен для поддержки импорта функций и констант в дополнение к классам.
  Это достигается с помощью конструкций use function и use const соответственно.
  К примеру:
    ```php
    <?php
    namespace Name\Space {
        const FOO = 42;
        function f() { echo __FUNCTION__."\n"; }
    }
    
    namespace {
        use const Name\Space\FOO;
        use function Name\Space\f;
    
        echo FOO."\n";
        f();
    }
    ```
    Результат выполнения данного примера:
    ```
    42
    Name\Space\f
    ```
* Теперь PHP содержит интерактивный дебаггер, называющийся "[phpdbg](http://phpdbg.com/docs)"
  и реализованный как модуль SAPI
* Добавлен ini-параметр default_charset, в котором можно указать кодировку по умолчанию для использования в функциях
  htmlentities(), html_entity_decode() и htmlspecialchars(). Обратите внимание, что если (сейчас считается устаревшим)
  заданы параметры кодировки iconv и mbstring, они будут иметь преимущество пере default_charset для iconv и mbstring.
  Значение этой настройки по умолчанию равно UTF-8
* php://input теперь можно переоткрытьи читать столько раз, сколько нужно.
  Это также привело к значительному уменьшению объема памяти, необходимой для работы с данными POST
* Теперь можно загружать файлы размером более 2ГБ
* [GMP](http://php.net/manual/ru/book.gmp.php) поддерживает перезагрузку операторов
  К примеру:
   ```php
   <?php
   $a = gmp_init(42);
   $b = gmp_init(17);
   
   if (version_compare(PHP_VERSION, '5.6', '<')) {
       echo gmp_intval(gmp_add($a, $b)), PHP_EOL;
       echo gmp_intval(gmp_add($a, 17)), PHP_EOL;
       echo gmp_intval(gmp_add(42, $b)), PHP_EOL;
   } else {
       echo $a + $b, PHP_EOL;
       echo $a + 17, PHP_EOL;
       echo 42 + $b, PHP_EOL;
   }
   ```
   Результат выполнения данного примера:
   ```
   59
   59
   59
   ```
* Была добавлена функция hash_equals() для сравнения двух строк за постоянное время.
  Это должно помочь избежать атак по времени; для экземпляров,
  во время тестирования хэширования паролей функцией crypt()
  (при условии, что вы не можете использовать password_hash() и password_verify(),
  которые не восприимчивы к атакам по времени).
  К примеру:
  ```php
  <?php
  $expected  = crypt('12345', '$2a$07$usesomesillystringforsalt$');
  $correct   = crypt('12345', '$2a$07$usesomesillystringforsalt$');
  $incorrect = crypt('1234',  '$2a$07$usesomesillystringforsalt$');
  
  var_dump(hash_equals($expected, $correct));
  var_dump(hash_equals($expected, $incorrect));
  ```
  Результат выполнения данного примера:
  ```
  bool(true)
  bool(false)
  ``` 
* Был добавлен магический метод
  [__debugInfo()](http://php.net/manual/ru/language.oop5.magic.php#language.oop5.magic.debuginfo)
  для того, чтобы объект мог поменять значения свойств, выводимых при использовании var_dump().
  К примеру:
  ```php
  <?php
  class C {
      private $prop;
  
      public function __construct($val) {
          $this->prop = $val;
      }
  
      public function __debugInfo() {
          return [
              'propSquared' => $this->prop ** 2,
          ];
      }
  }
  
  var_dump(new C(42));
  ```
  Результат выполнения данного примера:
  ```
  object(C)#1 (1) {
    ["propSquared"]=>
    int(1764)
  }
  ```   
* Был добавлен алгоритм хэширования _gost-crypto_.
  Он реализует функцию хэширования GOST, используемую в таблицах CryptoPro S-box,
  определенных в [RFC 4357, секция 11.2](http://www.faqs.org/rfcs/rfc4357.html)
* Очень многое было сделано для улучшения поддержки SSL/TLS.
  Включая [разрешение верификации пиров по умолчанию](http://php.net/manual/ru/migration56.incompatible.php#migration56.incompatible.peer-verification),
  поддержка сверки отпечатков сертификатов,
  снижение воздействия атаки пересоединения TLS и множества новых [опций контекста SSL](http://php.net/manual/ru/context.ssl.php)
  для более гранулированного контроля над протоколом и настройками верификации при использовании зашифрованных потоков.
  Более подробно все эти изменения описаны в разделе [Изменения OpenSSL в PHP 5.6.x](http://php.net/manual/ru/migration56.openssl.php)
* Расширение [pgsql](http://php.net/manual/ru/book.pgsql.php) теперь поддерживает асинхронные соединения и запросы,
  тем самым разрешая неблокирующее взаимодействие с базами данных PostgreSQL.
  Асинхронные соединения могут быть установлены с помощью константы `PGSQL_CONNECT_ASYNC`,
  и новые функции [pg_connect_poll()](http://php.net/manual/ru/function.pg-connect-poll.php),
  [pg_socket()](http://php.net/manual/ru/function.pg-socket.php),
  [pg_consume_input()](http://php.net/manual/ru/function.pg-consume-input.php) и
  [pg_flush()](http://php.net/manual/ru/function.pg-flush.php),
  могут быть использованы для обработки асинхронных соединений и запросов    

### PHP 7.0 (03.12.2015)
* **Рефакторинг основных структур данных**
* **Улучшена конвенция вызова виртуальной машины**
* **Новый API парсинга параметров**
* **Новый диспетчер памяти**
* **Многочисленные улучшения исполнителя виртуальной машины**
* **Существенно уменьшено использование памяти**
* **Улучшены функции __call() и __callStatic()**
* **Улучшена конкатенация строк**
* **Улучшен поиск символов в строках**

### PHP 7.1 (01.12.16)
* **Новый оптимизационный фреймворк на базе SSA (встроен в opcache)**
* **Глобальная оптимизация байткода PHP на основе выведения типов (type inference)**
* **Высокоспециализированные обработчики опкодов виртуальной машины**

### PHP 7.2 (???)

---

### Полезные ссылки
* [RFC Implemented](https://wiki.php.net/rfc#implemented)
* [short changelog](http://php.net/manual/ru/doc.changelog.php)
* [full changelog php5](http://php.net/ChangeLog-5.php)
* [full changelog php7](http://php.net/ChangeLog-7.php)

Описание находится в ~~бесконечном~~ процессе.