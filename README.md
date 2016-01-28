Для тестирования почты на сайтах используем [http://www.fakemailgenerator.com/ www.fakemailgenerator.com] (чтобы не засорять и не светить личную почту)

# Вёрстка 
[Малоиспользуемые, но от этого не менее прекрасные возможности LESS](http://habrahabr.ru/post/233653/)

[3 новых LESS/CSS-свойства, о которых вам следует знать](http://www.coolwebmasters.com/cssstyle-sheets/4879-less-css-new-features.html)

CSS-расческа: [офф.сайт](http://csscomb.com/) и [хабр](http://habrahabr.ru/post/230589/)

[правильное использование HTML5-элементов](https://yadi.sk/i/tax-fRxDZG7VB)

[Геометрические фигуры на CSS](http://habrahabr.ru/post/126207/)

[Как можно определить, что ваш CSS пованивает? (читать обязательно)](http://habrahabr.ru/post/160177/)

[Отложенная загрузка изображений (lazyload)](https://github.com/tuupola/jquery_lazyload)

[Вертикальное выравнивание IE9+](http://codepen.io/sebastianekstrom/pen/kzEhe)

[Как прижать подвал к низу страницы](http://www.zakharov.ms/footer/)

# Анализ CSS-файлов
[http://www.stylestats.org](http://www.stylestats.org)

[http://cssstats.com/](http://cssstats.com/)

# Генераторы 

[Ultimate CSS Gradient Generator](http://www.colorzilla.com/gradient-editor/)

[CSS3 Box Shadow Generator](http://css3gen.com/box-shadow/)

[Геометрические фигуры - генератор](http://coveloping.com/tools/css-shapes-generator)

[gradient-generator](http://www.webcore-it.com/colorful-background/)

[css-generator](http://www.bypeople.com/css-generator/)

[imagemap-generator](http://imagemap-generator.dariodomi.de/)

[lorempixel.com](http://lorempixel.com)

[генератор css-сетки](http://yui.github.io/gridbuilder/)

# Книги
[PHP Правильный путь.](http://getjump.github.io/ru-php-the-right-way/)

[devdocs.io/](http://devdocs.io/)

[рефакторинг](http://refactoring.guru)

# Повышение квалификации 
Что должен знать Junior-разработчик

Что должен знать Middle-разработчик

Что должен знать Senior-разработчик

[WebReference](https://webref.ru/)

[Это ваш путь к изучению веб-разработки](http://codenamecrud.ru/pages/curriculum)

[SVG](https://svg.zeef.com/willian.justen.de.vasconcellos?ref=yana.ledeneva0)

# Правила хорошего тона
[CSS GuideLines, часть 1.Синтаксис и форматирование](http://habrahabr.ru/post/235851/)

[CSS GuideLines, часть 2. Комментирование кода](http://habrahabr.ru/post/235893/)

[javascript-patterns](https://github.com/shichuan/javascript-patterns)

[JavaScript-Garden](http://bonsaiden.github.io/JavaScript-Garden/ru/)

# Видеообзоры
[Список YouTube-каналов для обучения веб-разработке](http://habrahabr.ru/post/247893/)

[laracasts.com - THE BEST PHP SCREENCASTS ON THE WEB](https://laracasts.com/)

# CMS
## Joomla 
[Github](https://github.com/joomla/joomla-cms) [Download](https://github.com/joomla/joomla-cms/archive/master.zip)

[API Virtuemart 2](http://docs.virtuemart.net/api-vm2/index.html)

Плагин отключения Mootools в Joomla [GitHub](https://github.com/Poznakomlus/joomla_options) [Download](https://github.com/Poznakomlus/joomla_options/archive/master.zip)

[J!Dump - плагин дебага для Joomla](http://extensions.joomla.org/extensions/miscellaneous/development/1509)

[JB LIBRARY PLUGIN - плагин управления библиотек в Joomla](http://www.joomlabamboo.com/joomla-extensions/jb-library-plugin-a-free-joomla-jquery-plugin)

[Selecting data using JDatabase](https://docs.joomla.org/Selecting_data_using_JDatabase)

[Вывод модуля Joomla! там, где вам нужно](http://www.master-web.info/display-joomla-module-anywhere/)

## 1C-Bitrix

### Полезные ссылки
#### Служебные директивы для работы Битрикса

[Специальные константы](http://dev.1c-bitrix.ru/api_help/main/general/constants.php)

[Bitrix Debug](http://marketplace.1c-bitrix.ru/solutions/scrollup.bxd/)

[Скрипт для диагностики проблем интеграции с 1С (не проверено!)](https://dev.1c-bitrix.ru/community/blogs/carter/2285.php)

[Различные функции](http://max22.ru/api-bitrix/other-api-functions/)

### сделать Пробный период бесконечным
БД, таблица b_option, NAME = admin_passwordh:
 FVgQeWYUBgQtCUVcDxcGCgsTAQ==

/bitrix/modules/main/admin/define.php:
 TEMPORARY_CACHE=ARtudgYHb2MMdQgebRtmG24A

удалить /bitrix/managed_cache/

### отправка писем через SMTP

для отправки будем использовать PHPMailer, который нужно предварительно скачать https://github.com/PHPMailer/PHPMailer

в какой-нить файл, например, /bitrix/php_interface/init.php добавляем ф-ию custom_mail, которая будет по дефолту переопределять стандартную mail() битрикса
 <?
    require_once $_SERVER['DOCUMENT_ROOT'] . '/PHPMailer/PHPMailerAutoload.php';
    
    function custom_mail($to, $subject, $message, $additionalHeaders = '') {
        $mail = new PHPMailer();
        $mail->IsSMTP(); // telling the class to use SMTP
        $mail->Host       = "smtp.mail.ru";         // sets the SMTP server
        $mail->SMTPAuth   = true;                   // enable SMTP authentication
        $mail->SMTPSecure = 'ssl';
        $mail->Port       = 465;                    // set the SMTP port for the GMAIL server
        $mail->Username   = "login@mail.ru";    // SMTP account username
        $mail->Password   = "password";             // SMTP account password
        $mail->CharSet = 'utf-8';
        preg_match('/From: ([\w]+@[\w\.]+)/i', $additionalHeaders, $matches);
        $mail->From = $matches[1];
        $mail->FromName = 'Your Name';
        $mail->addAddress($to);     // Add a recipient
        $mail->Subject = $subject;
        $mail->Body = preg_replace('/([\w\W]*)[\n]{2,}([\w\W]+)[\n]{2,}(.*)/','$2',$message);
    //    preg_match('/([\w\W]*)[\n]{2,}([\w\W]+)[\n]{2,}(.*)/',$message,$matches);
    
        if(!$mail->send()) {
            echo 'Message could not be sent. Mailer Error: ' . $mail->ErrorInfo;
            return false;
        } else {
            return true;
        }
    }

затем вызываем ф-ию bxmail($to, $subject, $message) со своими параметрами, например:
  bxmail('test@mail.ru', 'Мой заголовок письма', 'Мое сообщение');

### Экспорт каталога в файл
1. Заходим в админку и в левой панели выбираем Контент -> Информ. блоки -> Экспорт -> CSV

2. Выбираем необходимый инфоблок для экспорта

3. Указываем параметры экспорта и необходимые поля

4. Скачиваем полученный файл (кодировка обычно UTF-8)


### Корректный поиск по артикулам, именам в каталоге
нужно закомментировать строку '''209''' в файле /bitrix/components/bitrix/search.page/component.php

 $arLang = CSearchLanguage::GuessLanguage($q);


# CMF
[Laravel](http://laravel.com/docs/master)

[Laravel Cheat Sheet](http://cheats.jesse-obrien.ca/)

# Слайдеры, эффекты, карусели и прочие js-библиотеки

[Каталог ресурсов (javascripting.com)](http://www.javascripting.com/) и еще [www.unheap.com](http://www.unheap.com/) и [фронтенд-подборка скриптов](https://github.com/moklick/frontend-stuff)

[Интересная коллекция прелоадеров](http://simbyone.com/30-css-page-preload-animations/)

[jQuery Knob](http://anthonyterrien.com/knob/)

[scroll-effects](http://lab.hakim.se/scroll-effects/)

[slick](http://kenwheeler.github.io/slick/)

[liffect effect for lists](http://ademilter.com/lab/liffect/)

[http://www.jssor.com/](http://www.jssor.com/)

[DataTables Table plug-in for jQuery](http://www.datatables.net/)

[Динамическая расстановка блоков по ширине через Shuffle.js](http://vestride.github.io/Shuffle/adding-removing/)

[Animate.css](http://daneden.github.io/animate.css/)

[Стилизованные переключатели checkbox/radiobutton (IE8+)](http://ghinda.net/css-toggle-switch/)

[autoNumeric](http://www.decorplanit.com/plugin/)

[JQuery Raty](http://wbotelhos.com/raty)

# Иконочные шрифты
[Bootstrap glyphicons](http://getbootstrap.com/components/#glyphicons)

[Font-Awesome](http://fortawesome.github.io/Font-Awesome/icons/)

[ionicons.com](http://ionicons.com/)


# Прочее
[Online-редактор регулярных выражений](http://www.phpliveregex.com/)

[Как заставить Apache работать или как я реализую создание миниатюр изображений в своих проектах](http://habrahabr.ru/post/239501/)

[Практики для ускорения работы сайта](http://www.komtet.ru/lib/praktiki-dlya-uskoreniya-raboty-saita)

[Slopy Elements with CSS3](http://tympanus.net/Tutorials/SlopyElements/index2.html)

[Одиннадцатиклассница](http://habrahabr.ru/company/2gis/blog/246831/)

[Генератор аватарок](http://avatargenerator.ru/)

[300 потрясающих бесплатных сервисов](http://habrahabr.ru/post/250621/)

[An HTML linter for Bootstrap projects](http://www.bootlint.com/)

# DEBUG
[Пошаговая настройка Xdebug + OpenServer + PHPStorm](http://open-server.ru/forum/viewtopic.php?f=4&t=1249)

[kint](https://github.com/raveren/kint)


# SEO
[Поисковый плагин для сайта](http://htmlbook.ru/blog/poiskovyi-plagin-dlya-saita)

[SEO для мобильных](https://developers.google.com/webmasters/mobile-sites/mobile-seo/index?hl=ru)

# SQL
Выборка с получением кол-ва строк, без второго запроса на COUNT(*). может использоваться для пагинации.
 SELECT SQL_CALC_FOUND_ROWS id, address FROM addresses
 WHERE id > 3; -- LIMIT 1;
 SELECT FOUND_ROWS();

# Плагины/расширения для браузеров
## Google Chrome

[POSTMAN - отладка POST, GET-запросов](https://chrome.google.com/webstore/detail/postman-rest-client/fdmmgilgnpjigdojojpjoooidkmcomcm)

[DROP 64 - img2base64](https://chrome.google.com/webstore/detail/drop-64/jnkglmilmnhhhgcoeenalhcbkdandphp?utm_source=chrome-ntp-icon)

[SSH-terminal](https://chrome.google.com/webstore/detail/secure-shell/pnhechapfaindjhompbnflcldabbghjo?utm_source=chrome-ntp-icon)

[Lightshot](https://chrome.google.com/webstore/detail/lightshot-screenshot-tool/mbniclmhobmnbdlbpiphghaielnnpgdp)

[Lorem Ipsum Generator](https://chrome.google.com/webstore/detail/lorem-ipsum-generator-def/mcdcbjjoakogbcopinefncmkcamnfkdb)

[PHP Ninja](https://chrome.google.com/webstore/detail/php-ninja-manual/clbhjjdhmgeibgdccjfoliooccomjcab)

[Page Ruler](https://chrome.google.com/webstore/detail/page-ruler/jlpkojjdgbllmedoapgfodplfhcbnbpn)

[YSlow](https://chrome.google.com/webstore/detail/yslow/ninejjcohidippngpapiilnmkgllmakh)

[Сравнение сайта с макетом (попиксельная вертка)](https://chrome.google.com/webstore/detail/perfectpixel-by-welldonec/dkaagdgjmgdmbnecmcefdhjekcoceebi)

[Просмотр сео-заголовков](https://chrome.google.com/webstore/detail/meta-seo-inspector/ibkclpciafdglkjkcibmohobjkcfkaef)

# Занимательные вопросы/задачки

* У всех ли html-элементов существуют псевдо-классы before и after ? Если нет, то почему ?
* Какой будет результат запроса: select null from (select 'null' as `null`) as `null` where null.null is not null ?
* Как поведет себя браузер, если в тэг <a> положить еще один тэг <a> ?  а если в <a> положить < div> и в него <a> ?
