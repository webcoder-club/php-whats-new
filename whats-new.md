### PHP 5.0 (29.06.2003)
* Переезд на [Zend Engine 2](resourses/ZendEngine-2.0.pdf)

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
  123
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
  Массивы и объекты реализующие интерфейс [Traversable](http://php.net/manual/ru/class.traversable.php) могут быть развернуты в список аргументов
  при передаче в функцию с помощью оператора `...`
  
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
* Оператор `use` был расширен для поддержки импорта функций и констант в дополнение к классам.
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
* Была добавлена функция [hash_equals()](http://php.net/manual/ru/function.hash-equals.php) для сравнения двух строк за постоянное время.
  Это должно помочь избежать атак по времени; для экземпляров,
  во время тестирования хэширования паролей функцией [crypt()](http://php.net/manual/ru/function.crypt.php)
  (при условии, что вы не можете использовать [password_hash()](http://php.net/manual/ru/function.password-hash.php)
  и [password_verify()](http://php.net/manual/ru/function.password-verify.php),
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
* [Декларация скалярных типов](http://php.net/manual/ru/functions.arguments.php#functions.arguments.type-declaration) введена в двух вариантах: принуждающая (по умолчанию) и строгая.
  Следующие типы могут использоваться для декларации параметров (в обоих вариантах):
  строки (string), целые (int), рациональные числа (float) и логические значения (bool).
  Они дополняют аргументы других типов, введенных в PHP 5: имена классов, интерфейсов, array и callable.
  
  К примеру:
  ```php
  <?php
  // Принуждающий режим
  function sumOfInts(int ...$ints)
  {
      return array_sum($ints);
  }
  
  var_dump(sumOfInts(2, '3', 4.1));
  ```
  Результат выполнения данного примера:
  ```
  int(9)
  ``` 
  Для установки строгого режима, в самом начале файла необходимо поместить одну директиву declare.
  Это означает, что строгость декларации работает на уровне файла и не затрагивает весь остальной код.
  Эта директива затрагивает не только декларацию параметров, но и возвращаемые значения функций
  (см. декларация возвращаемого типа), встроенные функции PHP и функции загруженных расширений.
  Подробную документацию и примеры использования читайте в разделе декларация типов.
* Добавлена поддержка [декларация возвращаемого типа](http://php.net/manual/ru/functions.returning-values.php#functions.returning-values.type-declaration).
  Аналогично как и декларация типов аргументов, декларация типа возвращаемого значения указывает,
  значение какого типа должна вернуть функция. Для декларации типа возвращаемого значения доступны [все те же типы](http://php.net/manual/ru/functions.arguments.php#functions.arguments.type-declaration.types),
  что и для декларации типов аргументов.
  
  К примеру:
  ```php
  <?php
  function arraysSum(array ...$arrays): array
  {
      return array_map(function(array $array): int {
          return array_sum($array);
      }, $arrays);
  }
  print_r(arraysSum([1,2,3], [4,5,6], [7,8,9]));
  ```
  Результат выполнения данного примера:
  ```
  Array
  (
      [0] => 6
      [1] => 15
      [2] => 24
  )
  ``` 
  Подробную документацию и примеры использования читайте в разделе декларация возвращаемого типа.
* Добавлен оператор объединения с null (`??`),
  являющийся синтаксическим сахаром для достаточно распространенного действия,
  когда совместно используются тернарный оператор и функция [isset()](http://php.net/manual/ru/function.isset.php).
  Он возвращает первый операнд, если он задан и не равен `NULL`,
  а в обратном случае возвращает второй операнд
  
  К примеру:
  ```php
  <?php
  // Извлекаем значение $_GET['user'], а если оно не задано,
  // то возвращаем 'nobody'
  $username = $_GET['user'] ?? 'nobody';
  // Это идентично следующему коду:
  $username = isset($_GET['user']) ? $_GET['user'] : 'nobody';
  
  // Данный оператор можно использовать в цепочке.
  // В этом примере мы сперва проверяем, задан ли $_GET['user'], если нет,
  // то проверяем $_POST['user'], и если он тоже не задан, то присваеваем 'nobody'.
  $username = $_GET['user'] ?? $_POST['user'] ?? 'nobody';
  ```
  Но стоит быть внимательным со значениями `''`, `0` или `false`
  
  К примеру:
    ```php
    <?php
    $a = ''; // или 0 или false
    
    $b = $a ?? 'a';  
    // $b == '' или 0 или false
    
    $c = $a ?: 'a'; 
    // $c == 'a'
    ```
* Добавлен оператор spaceship `<=>`
  Этот оператор предназначен для сравнения двух выражений.
  Он возвращает -1, 0 или 1 если $a, соответственно, меньше, равно или больше чем $b.
  Сравнение производится в соответствии со [правилами сравнения](http://php.net/manual/ru/types.comparisons.php) типов PHP.
  
  К примеру:
  ```php
  <?php
  // Целые
  echo 1 <=> 1; // 0
  echo 1 <=> 2; // -1
  echo 2 <=> 1; // 1
  
  // Рациональные
  echo 1.5 <=> 1.5; // 0
  echo 1.5 <=> 2.5; // -1
  echo 2.5 <=> 1.5; // 1
   
  // Строки
  echo "a" <=> "a"; // 0
  echo "a" <=> "b"; // -1
  echo "b" <=> "a"; // 1
  ```
* Задание констант массивов с помощью [define()](http://php.net/manual/ru/function.define.php).
  В PHP 5.6, такие константы можно было задавать только с помощью const.
  
  К примеру:
  ```php
  <?php
  define('ANIMALS', [
      'dog',
      'cat',
      'bird'
  ]);
  
  echo ANIMALS[1]; // выводит "cat"
  ``` 
* Добавлена поддержка анонимных классов с помощью `new class`.
  Их можно использовать тогда, когда нужен одноразовый класс и создавать полноценный класс,
  а потом его объект не имеет смысла.
  
  К примеру:
  ```php
  <?php
  interface Logger {
      public function log(string $msg);
  }
  
  class Application {
      private $logger;
  
      public function getLogger(): Logger {
           return $this->logger;
      }
  
      public function setLogger(Logger $logger) {
           $this->logger = $logger;
      }
  }
  
  $app = new Application;
  $app->setLogger(new class implements Logger {
      public function log(string $msg) {
          echo $msg;
      }
  });
  
  var_dump($app->getLogger());
  ```
  Результат выполнения данного примера:
  ```
  object(class@anonymous)#2 (0) {
  }
  ```
* Добавлен синтаксис кодирования Unicode.
  Берем шестнадцатеричный код Unicode и записываем его в формате UTF-8 в двойных кавычках или формате heredoc.
  Любой корректный код будет принят. Лидирующие нули по желанию.
  
  К примеру:
  ```php
  <?php
  echo "\u{aa}";
  echo "\u{0000aa}";
  echo "\u{9999}";
  ```
  Результат выполнения данного примера:
  ```
  ª
  ª (То же самое, что и первый вариант, но с лидирующими нулями)
  香
  ```
* [Closure::call()](http://php.net/manual/ru/closure.call.php) является более производительным и коротким способом временного связывания
  области действия объекта с замыканием и его вызовом.
  
  К примеру:
  ```php
  <?php
  class A {private $x = 1;}
  
  // До PHP 7
  $getX = function() {return $this->x;};
  $getXCB = $getX->bindTo(new A, 'A'); // промежуточное замыкание
  echo $getXCB();
  
  // PHP 7+
  $getX = function() {return $this->x;};
  echo $getX->call(new A);
  ```
  Результат выполнения данного примера:
  ```
  1
  1
  ```
* [unserialize()](http://php.net/manual/ru/function.unserialize.php) с фильтрацией
  Этот функционал обеспечивает более высокий уровень безопасности при десериализации объектов с непроверенными данными.
  Это позволяет предотвратить возможную инъекцию кода, позволяя разработчику использовать
  белый список классов для десериализации.
  
  К примеру:
  ```php
  <?php
  // Преобразование всех объектов в __PHP_Incomplete_Class
  $data = unserialize($foo, ["allowed_classes" => false]);
  
  // Преобразование всех объектов кроме MyClass и MyClass2 в __PHP_Incomplete_Class
  $data = unserialize($foo, ["allowed_classes" => ["MyClass", "MyClass2"]]);
  
  // Поведение по умолчанию принимает все классы (можно просто не задавать второй аргумент)
  $data = unserialize($foo, ["allowed_classes" => true]);
  ```
* Новый класс [IntlChar](http://php.net/manual/ru/class.intlchar.php) добавляет новую функциональность в _ICU_.
  Класс определяет несколько статических методов и констант для манипулирования символами Unicode
  
  К примеру:
  ```php
  <?php
  printf('%x', IntlChar::CODEPOINT_MAX);
  echo IntlChar::charName('@');
  var_dump(IntlChar::ispunct('!'));
  ```
  Результат выполнения данного примера:
  ```
  10ffff
  COMMERCIAL AT
  bool(true)
  ```
  Для использования это класса необходимо установить расширение _Intl_.
* [Ожидания](http://php.net/manual/ru/function.assert.php#function.assert.expectations) являются улучшенной, обратно совместимой версией старой функции
  [assert()](http://php.net/manual/ru/function.assert.php).
  Они позволяют делать предположения с нулевой стоимостью в промышленном коде и
  предоставляют возможность выбрасывать пользовательские исключения в случае провала ожидания.
  
  Вместе тем, что старое API поддерживается, assert() теперь является языковой конструкцией,
  принимающей первым аргументом выражения, а не только строки для оценки или логические значения для проверки.
  
  К примеру:
  ```php
  <?php
  ini_set('assert.exception', 1);
  class CustomError extends AssertionError {}
  assert(false, new CustomError('Some error message'));
  ```
  Результат выполнения данного примера:
  ```
  Fatal error: Uncaught CustomError: Some error message
  ```  
  Подробное описание этого функционала, а также инструкции для его конфигурирования
  для тестовых и промышленных сред, читайте в секции Ожидания раздела посвященному assert().
* Групповые декларации [use](http://php.net/manual/ru/language.namespaces.importing.php)
  Классы, функции и константы импортируемые из одного и того же [namespace](http://php.net/manual/ru/language.namespaces.definition.php), теперь можно группировать в одном операторе `use`.
  
  К примеру:
  ```php
  <?php
  // До PHP 7
  use some\namespace\ClassA;
  use some\namespace\ClassB;
  use some\namespace\ClassC as C;
  
  use function some\namespace\fn_a;
  use function some\namespace\fn_b;
  use function some\namespace\fn_c;
  
  use const some\namespace\ConstA;
  use const some\namespace\ConstB;
  use const some\namespace\ConstC;
  
  // PHP 7+
  use some\namespace\{ClassA, ClassB, ClassC as C};
  use function some\namespace\{fn_a, fn_b, fn_c};
  use const some\namespace\{ConstA, ConstB, ConstC};
  ```   
* Выражение return в генераторах
  Эта функциональность добавлена к генераторам, введенным в PHP 5.5.
  Она позволяет использовать оператор return в генераторах в качестве
  финального возвращаемого значение (возврат по ссылке недопустим).
  Это значение можно извлечь с помощью нового метода `Generator::getReturn()`,
  которые можно использовать только после того, как генератор вернул все сгенерированные значение.

  К примеру:
  ```php
  <?php
  $gen = (function() {
      yield 1;
      yield 2;
  
      return 3;
  })();
  
  foreach ($gen as $val) {
      echo $val, PHP_EOL;
  }
  
  echo $gen->getReturn(), PHP_EOL;
  ```
  Результат выполнения данного примера:
  ```
  1
  2
  3
  ```
  Возможность явно получать финальное значение генератора является очень полезной,
  так как позволяет клиентскому коду, использующему генератор, получать и
  обработать самое последнее значение генератора, после которого точно ничего больше не будет.
  Это сильно проще, чем вынуждать разработчика проверять,
  последнее ли значение вернулось и как-то по особенному его обрабатывать.
* Делегация генератора
  Теперь генератор может автоматически делегировать другому генератору,
  объекту класса [Traversable](http://php.net/manual/ru/class.traversable.php) или массиву без необходимости писать в нем дополнительную обработку полученных значений.
  Достигается это с помощью конструкции [yield from](http://php.net/manual/ru/language.generators.syntax.php#control-structures.yield.from).
  
  К примеру:
  ```php
  <?php
  function gen()
  {
      yield 1;
      yield 2;
      yield from gen2();
  }
  
  function gen2()
  {
      yield 3;
      yield 4;
  }
  
  foreach (gen() as $val)
  {
      echo $val, PHP_EOL;
  }
  ```
  Результат выполнения данного примера:
  ```
  1
  2
  3
  4
  ```
* Новая функция [intdiv()](http://php.net/manual/ru/function.intdiv.php) производит целочисленное деление операндов и возвращает его результат.

  К примеру:
  ```php
  <?php
  var_dump(intdiv(10, 3));
  ```
  Результат выполнения данного примера:
  ```
  int(3)
  ```
* Теперь [session_start()](http://php.net/manual/ru/function.session-start.php) принимает массив опций,
  которые переопределят [конфигурационные директивы сессии](http://php.net/manual/ru/session.configuration.php) установленные в _php.ini_.
  Также опции были расширены включенной по умолчанию опцией _session.lazy_write_,
  которая говорит PHP о том, что файл сессии надо перезаписывать,
  только если изменились даные сессии, и опцией read_and_close,
  которую можно задать только через session_start() для того,
  чтобы PHP закрывал сессию сразу же как прочитает ее данные и не вносил в нее каких либо изменений.
  
  К примеру, для задания session.cache_limiter равным private и немедленному закрытию сессии после чтения ее данных:
  ```php
    <?php
    session_start([
        'cache_limiter' => 'private',
        'read_and_close' => true,
    ]);
    ```
* Новая функция [preg_replace_callback_array()](http://php.net/manual/ru/function.preg-replace-callback-array.php) позволяет писать более чистый код,
  когда требуется использовать функцию [preg_replace_callback()](http://php.net/manual/ru/function.preg-replace-callback.php).
  До PHP 7 при необходимости обработать разные регулярные выражения разными функциями,
  приходилось для каждой такой обработки писать отдельный вызов функции.
  
  Теперь же можно использовать одну функцию, передавая в нее ассоциативный массив,
  ключами которого являются регулярные выражения, а значениями - функции обратного вызова
* Были добавлены две новые кроссплатформенные функции для генерации
  криптографически безопасных строк и целых чисел: [random_bytes()](http://php.net/manual/ru/function.random-bytes.php)
  и [random_int()](http://php.net/manual/ru/function.random-int.php).
* Теперь функция [list()](http://php.net/manual/ru/function.list.php) всегда может раскрывать объекты реализующие
  [ArrayAccess](http://php.net/manual/ru/class.arrayaccess.php)
* В PHP 5 [list()](http://php.net/manual/ru/function.list.php) присваивает значения начиная с самого правого.
  В PHP 7 [list()](http://php.net/manual/ru/function.list.php) - с самого левого.  
* Добавлена возможность обращения к методам и свойствам класса при клонировании, т.е. `(clone $foo)->bar()`      
* ```php
  <?php
  class foo { static $bar = 'baz'; }
  var_dump('foo'::$bar);
  ```
  Результат выполнения данного примера:
  ```
  string(3) "baz"
  ```
  Хотя до PHP7 возвращал синтакисческую ошибку.  
### PHP 7.1 (01.12.2016)
* **Новый оптимизационный фреймворк на базе SSA (встроен в opcache)**
* **Глобальная оптимизация байткода PHP на основе выведения типов (type inference)**
* **Высокоспециализированные обработчики опкодов виртуальной машины**
* Добавлены обнуляемые типы. Типы для параметров и возвращаемых значений могут быть помечены как обнуляемые,
  путем добавления префикса в виде знака вопроса. Это означает, что указанные параметры и возвращаемые значения,
  могут быть как указанного типа, так и NULL.
  
  К примеру:
  ```php
  <?php
  function testReturn(): ?string
  {
      return 'elePHPant';
  }
  
  var_dump(testReturn());
  
  function testReturn(): ?string
  {
      return null;
  }
  
  var_dump(testReturn());
  
  function test(?string $name)
  {
      var_dump($name);
  }
  
  test('elePHPant');
  test(null);
  test();
  ```
  Результат выполнения данного примера:
  ```
  string(10) "elePHPant"
  NULL
  string(10) "elePHPant"
  NULL
  Uncaught Error: Too few arguments to function test(), 0 passed in...
  ```   
* Добавлены ничего не возвращающие функции.Был добавлен тип возвращаемого значения void.
  Функции с таким заданным типом возвращаемого значения не должны ничего возвращать.
  То есть либо вообще не содержать ни одного оператора return, либо использовать его без параметра.
  NULL не является корректным значением для возврата в таких функциях.
  
  К примеру:
  ```php
  <?php
  function swap(&$left, &$right): void
  {
      if ($left === $right) {
          return;
      }
  
      $tmp = $left;
      $left = $right;
      $right = $tmp;
  }
  
  $a = 1;
  $b = 2;
  var_dump(swap($a, $b), $a, $b);
  ```
  Результат выполнения данного примера:
  ```
  null
  int(2)
  int(1)
  ```
  Попытка использовать возвращаемое значение таких функций приведет к тому,
  что это значение будет считаться за NULL, без вывода предупреждения.
  Причина этого в том, что предупреждения будут вызывать общих функций высшего порядка.
* Симметричная деструктуризация массива. Можно использовать короткий синтаксис ([]) для деструктуризации массивов
  с целью присвоения (в том числе в foreach), как альтернатива функции [list()](http://php.net/manual/ru/function.list.php), которая, впрочем, все еще поддерживается.
  
  К примеру:
  ```php
  <?php
  $data = [
      [1, 'Tom'],
      [2, 'Fred'],
  ];
  
  // list() style
  list($id1, $name1) = $data[0];
  
  // [] style
  [$id1, $name1] = $data[0];
  
  // list() style
  foreach ($data as list($id, $name)) {
      // logic here with $id and $name
  }
  
  // [] style
  foreach ($data as [$id, $name]) {
      // logic here with $id and $name
  }
  ```
  Также можно поменять значения переменных более элегантным способом без list:
    ```php
    [$a, $b] = [$b, $a];
    ```
* Видимость констант класса. Добавлена поддержка задания области видимости для констант класса.
  
  К примеру:
  ```php
  <?php
  class ConstDemo
  {
      const PUBLIC_CONST_A = 1;
      public const PUBLIC_CONST_B = 2;
      protected const PROTECTED_CONST = 3;
      private const PRIVATE_CONST = 4;
  }
  ```                             
* Псевдо-тип `iterable`. Был добавлен новый псевдо-тип (похожий на [callable](http://php.net/manual/ru/language.types.callable.php)),
  названный `iterable`.
  Он может использоваться как параметр, так и в качестве возвращаемого значения там, где используется массив
  или объект реализующий интерфейс [Traversable](http://php.net/manual/ru/class.traversable.php).
  Что касается подтипов, типы параметров из дочерних классов могут
  расширить декларацию родителей типа array или Traversable до `iterable`. Для типов возврата, дочерние классы могут
  сужать тип возвращаемого значения с iterable до array или объекта реализующего Traversable.
                       
  К примеру:
  ```php
  <?php
  function iterator(iterable $iter)
  {
      foreach ($iter as $val) {
          //
      }
  }
  ```
* Обработка нескольких исключений в одном блоке catch. В блоке catch теперь можно обрабатывать несколько исключений,
  перечисляя их через символ вертикальной черты `|`. Это может быть полезно,
  если различные исключения обрабатываются одинаково.
  
  К примеру:
  ```php
  <?php
  try {
      // Какой то код
  } catch (FirstException | SecondException $e) {
      // Обрабатываем оба исключения
  }
  ```                                                       
* Поддержка ключей в list(). Теперь вы можете указывать ключи в операторе list(), или в его новом, коротком,
  синтаксисе []. Это позволяет деструктурировать массивы с нечисловыми или непоследовательными ключами.
                             
  К примеру:
  ```php
  <?php
  $data = [
      ["id" => 1, "name" => 'Tom'],
      ["id" => 2, "name" => 'Fred'],
  ];
  
  // стиль list()
  list("id" => $id1, "name" => $name1) = $data[0];
  
  // стиль []
  ["id" => $id1, "name" => $name1] = $data[0];
  
  // стиль list()
  foreach ($data as list("id" => $id, "name" => $name)) {
      // logic here with $id and $name
  }
  
  // стиль []
  foreach ($data as ["id" => $id, "name" => $name]) {
      // logic here with $id and $name
  }
  ```
* Поддержка отрицательных смещений для строк. Поддержка отрицательных смещений для строк добавлена в
  [функции манипуляции строками](http://php.net/manual/ru/book.strings.php),
  также как в [индексации строк](http://php.net/manual/ru/language.types.string.php#language.types.string.substr)
  с помощью [] или {}. В этих случаях,
  отрицательные смещения интерпретируются как смещения относительно конца строки.
                                              
  К примеру:
  ```php
  <?php
  var_dump("abcdef"[-2]);
  var_dump(strpos("aabbcc", "b", -3));
  ```
  Результат выполнения данного примера:
  ```
  string (1) "e"
  int(3)
  ```
  Теперь поддерживаются отрицательные смещения в простом синтаксисе указания индекса в строках и массивах.
  
  К примеру:
  ```php
  <?php
   $string = 'bar';
   echo "The last character of '$string' is '$string[-1]'.\n";
  ```
  Результат выполнения данного примера:
  ```
  The last character of 'bar' is 'r'.
  ```
* Использование пустого индекса вызывает фатальную ошибку, ранее в подобном случае строка преобразовывалась в массив без предупреждения.  
* Поддержка AEAD в ext/openssl. Поддержка AEAD (режимы GCM и CCM) была добавлена путем расширения функций
  openssl_encrypt() и openssl_decrypt() дополнительными параметрами.
* Преобразование callable в Closure с помощью Closure::fromCallable(). Новый статический метод добавлен в класс
  Closure для возможности легко преобразовать callable в объекты типа Closure.
  
  К примеру:
  ```php
  <?php
   class Test
   {
       public function exposeFunction()
       {
           return Closure::fromCallable([$this, 'privateFunction']);
       }
   
       private function privateFunction($param)
       {
           var_dump($param);
       }
   }
   
   $privFunc = (new Test)->exposeFunction();
   $privFunc('some value');
  ```
  Результат выполнения данного примера:
  ```
  string(10) "some value"
  ```
* Асинхронная обработка сигналов. Новая функция pcntl_async_signals() была добавлена для разрешения
  асинхронной обработки сигналов без использования тиков (которые производят много накладных расходов).
  
  К примеру:
  ```php
  <?php
  pcntl_async_signals(true); // включает асинхронные сигналы
  
  pcntl_signal(SIGHUP,  function($sig) {
      echo "SIGHUP\n";
  });
  
  posix_kill(posix_getpid(), SIGHUP);
  ```
  Результат выполнения данного примера:
  ```
  SIGHUP
  ```                                  
* Поддержка HTTP/2 server push в ext/curl. Поддержка "server push" добавлена в расширение CURL
  (требуется версия 7.46 и выше). Использовать можно в функции [curl_multi_setopt()](http://php.net/manual/ru/function.curl-multi-setopt.php)
  с новой константой
  CURLMOPT_PUSHFUNCTION. Также добавлены константы CURL_PUSH_OK и CURL_PUSH_DENY,
  для определения, был ли прнинят или отклонен "server push".
### PHP 7.2 (??.??.2017)
* **В Opcache добавлена глобальная оптимизация на основе анализа потока данных с использованием SSA
  (Static single assignment form): Sparse Conditional Constant Propagation (SCCP), удаление мертвого кода
  (Dead Code Elimination — DCE) и удаление неиспользуемых локальных переменных**
* **Оптимизирована работа встроенной функции in_array() с помощью поиска хеша в перевернутом массиве**
* Добавлена возможность перегрузки абстрактных методов
* Добавлена возможность опускать `typehint` у потомков
  
  К примеру:
    ```php
    <?php
    class ArrayClass {
      public function foo(array $foo) { /* ... */ }
    }
     
    class EverythingClass extends ArrayClass {
      public function foo($foo) { /* ... */ }
    }
    ```
* Добавлен typehint `object`
* Добавлена возможность указывать запятую в конце группированных нейспейсов
  
  К примеру:
  ```php
  <?php
  // Раньше это работало только для массивов
  $array = [1, 2, 3,];
  // Следующие выражения возвращали ошибку `Parse error`
  
  // Группировка нейспейсов
  use Foo\Bar\{ Foo, Bar, Baz, };
  ```
* Добавлено новое криптографическое расширение Sodium
  [RFC: Make Libsodium a Core Extension](https://wiki.php.net/rfc/libsodium)
* Расширения теперь разрешено загружать в ini файлах по имени `(extension=<name>)`
* Строки без кавычек теперь вызывают _E_WARNING_.
  В PHP2 такие строки вызывали `Syntax error`, но в PHP3 бета поведение было изменено.
  
  К примеру:
  ```php
  $foo = flase; // Опечатка, но вызывалась ошибка E_NOTICE, которая часто отключается.  
  // ...
  if ( $foo ) {
     var_dump($foo); // string(5) "flase"
  }
    ```
