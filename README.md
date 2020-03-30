Проектная работа № 11 Яндекс.Практикум

Работа посвящена использованию инструментов webpack для организации кода веб-сайта, веб-приложения. В качестве сайта используются наработки проектной работы № 9, в которой создавалась страница с карточками, функционалом просомтра, установки/снятия лайка, подсчета количества лайков, возможности удаления только собственных карточек.

Перед началом В целях выполнения задания исходные файлы были скачаны со страницы проектной работы. На сайте GitHub.com в профиле Tatiana81 создан репозиторий Осуществлено клонирование средствами сайта GitHub.com

Предустановки (что было установлено на локальный компьютер) Во-первых, для корректной работы, выполнения команд был установлен GitHub Desktop Во-вторых, установлен пакет npm В-третьих, свободно распространяемый редактор кода Visual Studio Code После успешного клонирования в рабочей папке GitHub на локальном компьютере создастся каталог с названием репозитория. Копируем в эту папку скачанные файлы сайта

Этапы установки

Инициализируем npm: открываем терминал, переходим в рабочую папку репоозитория и выполняем команду npm init
С помощью команды npm i (install) имя_модуля --save-dev устанавливаем модули Список установленных модулей: webpack, webpack-dev-server, webpack-cli, file-loader, babel-loader, @babel/cli, @babel/core, @babel/preset-env, core-js@3.4.1, mini-css-extract-plugin, css-loader, html-webpack-plugin, webpack-md5-hash, postcss-loader, autoprefixer, cssnano, gh-pages
Производим настройку в соответствии с заданием 3.1 Настраиваем сборки build, dev, deploy 3.2 Включаем формирование имен файлов, включая хэш-код 3.3 Исправляем относительные пути в файлах css 3.4 В файле script.js подключаем стили 3.5 Настраиваем правила обработки javascript, css, файлов изображений и шрифтов
Версии установленных модулей: @babel/cli: 7.8.4, @babel/core: 7.9.0, @babel/preset-env: 7.9.0, babel-loader: 8.1.0, css-loader: 3.4.2, exports-loader: 0.7.0, file-loader: 6.0.0, gh-pages: 2.2.0, html-webpack-plugin: 3.2.0, image-webpack-loader: 6.0.0, imports-loader": 0.8.0, mini-css-extract-plugin: 0.9.0, optimize-css-assets-webpack-plugin: 5.0.3, postcss-import": 12.0.1, postcss-loader": 3.0.0, postcss-preset-env: 6.7.0, style-loader: 1.1.3, svg-inline-loader: 0.8.2, webpack: 4.42.0, webpack-cli: 3.3.11, webpack-dev-server: 3.10.3, webpack-md5-hash: 0.0.6


Автор: Суроева Татьяна
