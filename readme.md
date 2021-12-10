Binary Studio Academy PHP 2022
====

### Домашнее задание ([UA](ua.md))

#### Требования

Внимание: до начала выполнения задания следует убедиться, что у вас настроено рабочее окружение.
А именно:
 - php 8
 - git
 - composer

Рекомендуется использовать Vagrant и виртуальную машину Homestead.
Подробнее здесь: [https://laravel.com/docs/master/homestead](https://laravel.com/docs/master/homestead)

***

#### Установка

Установка показана в рабочем окружении OS Linux:

```bash
git clone https://github.com/BinaryStudioAcademy/bsa-modern-php-2022.git
cd bsa-modern-php-2022
composer install
```

#### Структура заданий

Все задания разделены по папкам внутри `/src`.

Вашей задачей, в большинстве случаев, будет дополнить существующий код недостающей
функциональностью.
Набор данных для каждого задания будет жёстко задан с целью проверки в тестах.

***

#### Задание 1

В первом задании (Task1) необходимо работать с автомобильной гонкой.

Вам необходимо создать несколько автомобилей, опираясь на класс `Car`, 
и использовать часть данных из таблицы.

| Name         | Image
|--------------|--------------------------------------------------|
| BMW          | [https://pbs.twimg.com/profile_images/595409436585361408/aFJGRaO6_400x400.jpg](https://pbs.twimg.com/profile_images/595409436585361408/aFJGRaO6_400x400.jpg) |
| Tesla        | [https://i.pinimg.com/originals/e4/15/83/e41583f55444b931f4ba2f0f8bce1970.jpg](https://i.pinimg.com/originals/e4/15/83/e41583f55444b931f4ba2f0f8bce1970.jpg) |
| Ford         | [https://fordsalomao.com.br/wp-content/uploads/2019/02/1499441577430-1-1024x542-256x256.jpg](https://fordsalomao.com.br/wp-content/uploads/2019/02/1499441577430-1-1024x542-256x256.jpg) |

Далее вам необходимо работать с классом `Track`, 
реализовав методы 

* `add` (добавление автомобиля на трек)
* `all` (получение всех автомобилей, находящихся на треке)
* `run` (запуск гонки и определение победителя)

Метод run запускает гонку  по треку и должен возвращать автомобиль-победитель. При реализации данного метода необходимо 
учитывать такие параметры автомобиля, как speed (скорость в км/час), pitStopTime( время, необходимое автомобилю на пит
стопе для полной заправки бака, в с), fuelConsumption( расход бензина на 100км, в л), fuelTankVolume
(вместимость бака, в л), а также параметры трека: lapLength( протяженность трека, в км) и lapsNumber (количество кругов).

Проверить себя можно запустив:
```bash
./vendor/bin/phpunit --testsuite task1
```

***

#### Задание 2

Во втором задании (Task2) необходимо реализовать генератор (используя `yield`), который фильтрует и возвращает книги 
из двух источников (библиотека и магазин).

Для этого нужно реализовать метод `generate` класса `BookGenerator`, а также дополнить код других вспомогательных методов классов `BookGenerator` и `Book`.

Фильтрация в генераторе должна происходить, учитывая следующие условия:

* книги, полученные из библиотеки, (`libraryBooks`) должны иметь не менее чем `minPagesNumber` количество страниц
* книги, полученные из магазина, (`storeBooks`) должны быть не дороже `maxPrice`

Проверить себя можно запустив:
```bash
./vendor/bin/phpunit --testsuite task2
```

***

#### Задание 3

В третьем задании (Task 3) мы будем практиковаться со встроенным web-сервером php.
Ваша задача состоит в том, чтобы отрендерить список созданных вами 
в задании 1 автомобилей и отобразить страницу, используя встроенный web-сервер.

Для этого вам необходимо наполнить автомобильный трек в файле `index.php` 
и реализовать метод `present` класса `CarTrackHtmlPresenter`, 
опираясь на код тестов к заданию.

Если вы используете Homestead, то для начала нужно остановить `nginx`.

```shell
sudo pkill nginx
```
Затем запустить встроенный веб-сервер:

```
php -S 0.0.0.0:80 -t ./src/Task3
```

Мoжет потребоваться команда "sudo php -S 0.0.0.0:80 -t ./src/Task3".

Страница будет доступна в браузере по адресу:  

[http://192.168.10.10:80](http://192.168.10.10:80) - если используете homestead

[http://127.0.0.1:80](http://127.0.0.1:80) - если запускаете с локальной машины

Часть кода уже содержится в файле `index.php`. 

Проверить себя можно запустив:
```bash
./vendor/bin/phpunit --testsuite task3
```

***

#### Проверка

Вы уже, наверное, заметили, что для проверки заданий мы используем 
[PHPUnit](https://phpunit.de/getting-started.html).
Это необходимо для того, чтобы проверить соответсвуют ли ваши решения 
нашим ожиданиям (предложенной спецификации).
Если вы ранее не были знакомы с PHPUnit, то не расстраивайтесь. 
Мы рассмотрим его в дальнейших лекциях более подробно.

На данном этапе можете считать, что это лишь автопроверка 
(как на [codewars.com](https://www.codewars.com)).

Вначале все тесты "красные", т.е. поломанные. 
Для того чтобы они стали рабочими (зелёными) и не было ошибок,
вам необходимо реализовать необходимые решения.

**Какой профит от тестов?**

* **Для вас**: Уверенность, что вы на правильном пути (в тестах ну ооочень много подсказок).
* **Для нас**: Рутинная проверка сводится к минимуму 
и мы сможем сосредоточиться на рекомендациях и фидбеке.

**Чего делать нельзя**
* Менять код assert-ов в тестах
* Подгонять ответы под ожидаемые результаты (код мы все равно будем смотреть).


Запуск всех тестов:

```bash
./vendor/bin/phpunit
```

Запуск теста для конкретного задания:

```bash
./vendor/bin/phpunit --testsuite task1
```

#### Критерии оценивания

* Задания выполнены корректно и тесты проходят (6 баллов)

* Использованы современные возможности PHP 8 (1 балл)

* Валидация данных выполнена корректно (используются кастомные исключения, приложение не ломается при невалдиных входных значениях) (1 балл)

* Код написан чисто, комментариев в коде нет и код соответствует стандарту [PSR-12](https://www.php-fig.org/psr/psr-12/) (1 балл)

* Awesomness - остается на усмотрение проверяющего (1 балл)

#### Приём решений

Ваше решение необходимо разместить в отдельном репозитории на [Bitbucket](https://bitbucket.org/)
и прислать ссылку на него.

Задавайте вопросы в комментариях к заданию в случае возникновения проблем.

*Форкать* этот репозиторий **запрещено**!
