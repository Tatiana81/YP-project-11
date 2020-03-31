Проектная работа № 11 Яндекс.Практикум

Работа посвящена использованию инструментов webpack для организации кода веб-сайта, веб-приложения. В качестве сайта используются наработки проектной работы № 9, в которой создавалась страница с карточками, функционалом просомтра, установки/снятия лайка, подсчета количества лайков, возможности удаления только собственных карточек.

Перед началом В целях выполнения задания исходные файлы были скачаны со страницы проектной работы. На сайте GitHub.com в профиле Tatiana81 создан репозиторий Осуществлено клонирование средствами сайта GitHub.com

Предустановки (что было установлено на локальный компьютер) Во-первых, для корректной работы, выполнения команд был установлен GitHub Desktop Во-вторых, установлен пакет npm В-третьих, свободно распространяемый редактор кода Visual Studio Code После успешного клонирования в рабочей папке GitHub на локальном компьютере создастся каталог с названием репозитория. Копируем в эту папку скачанные файлы сайта

Этапы установки

Чтобы установить проект на локальном компьютере необходимо:

1. Скачать из репозитория https://github.com/Tatiana81/YP-project-11/src файлы проекта (структура файлов соответствует спецификации БЭМ). Javascript файлы находятся в папке js, файлы стилей в папке и подпапках blocks.

2. Скачать с официального сайта www.nodejg.org/en/download дистрибутив для используемой платформы. Порядок установки для разных платформ может отличаться.

3. Проверить корректность установки npm путем введения команды в консоли npm –v. Признаком нормальной установки и настройки является ответ, в котором указана установленная версия npm.

4. Все дальнейшие действия осуществляются в командной строке (если не оговорено другое)

5. Командой cd имя_директории заходим в рабочую директорию проекта (папка на локальном компьютере, в которую были скачаны файлы в первом пункте).

6. Для инициализации npm запускаем команду npm init. В результате выполнения команды на экране будут появляться вопросы, предполагающие как ответ пользователя, так и предусматривающие ответ по умолчанию. Альтернативный вариант инициализации npm – выполнение команды npm init –yes. В этом случае, скрипт выполнится неитеративно, на все вопросы будет установлен ответ по умолчанию.

7. В результате инициализации получим в рабочей папке файл package.json, в котором будет записан словарь. В этом словаре сохраняться значения, введенные пользователем в качестве ответов на вопросы или запишутся значения по умолчанию. В качестве дополнительных ключей словаря будет создан «scripts», который понадобится для дальнейшей работы проекта на локальном компьютере.

8. Так как в проекте присутствуют файлы javascript, css, файлы картинок и шрифтов, следует установить дополнительные модули для их обработки.

9. Установим модуль webpack. Для этого в рабочей директории выполним команду

  npm i webpack –save-dev. 
В результате работы скрипта в рабочей папке должны находиться:
  папка node_modules
  package.json  
  package.json.lock

10. Для взаимодействия с настройками webpack из терминала разработчики пакета придумали интерфейс, который необходимо установить командой 
  npm i webpack-cli --save-dev.

11. При разработке проекта разработчику необходимо иметь две сборки: непосредственно для разработки (ветка develop, dev), и финальная сборка (ветка build). Настройка параметров запуска сборки осуществляется в файле package.json в разделе «scripts». После установки webpack по умолчанию представлена только сборка test, предназначенная для самотестирования. Ключ и значение можно смело удалять. В дальнейшей работе оно не пригодится.

12. Напишем скрипт для сборки проекта (релиз). Для этого в файле package.json в ключе scripts напишем значение:

  “build”: “webpack --mode production”

13. Для поддержки разработчика установим локальный веб-сервер. Для этого выполним команду npm i webpack-dev-server –save-dev. В проекте появится поддержка веб-сервера разработчика.

14. Для обеспечения поддержки разработки проекта необходимо иметь еще одну сборку, сборку development. Для ее создания в файле package.json в ключе scripts запишем второе значение

  “dev”: “webpack-dev-server --mode development --open”

15. После установки webpack следует произвести его настройку. Для настройки webpack необходимо создать в рабочей папке проекта файл webpack.config.js.

16. Первой характеристикой, которую необходимо указать для правильной работы – это указать точку входа. Точка входа – javascript файл, который начинает обрабатывать webpack в начале работы при запуске той или иной сборки проекта. Для этого в файл необходимо внести следующую строку:

  module_exports = {
    entry: “main: ./src/js/script.js”
  }
При этом, в качестве точки входа используется файл script.js.

17. Для формирования релиза веб-ресурса в файле webpack.config.js необходимо указать параметр output следующим образом:
  module_exports = {
   entry: “main: ./src/js/script.js”,
  output: {
    path: “./dist/”,
    filename: main.js
          }
    }

18. Настроить корректную работу webpack с относительными путями. Для этого внести в файл webpack.config.js следующие изменения:

const path = require(‘path’)
module_exports = {
  entry: “main: ./src/js/script.js”,
  output: {
    path: path.resolve(__dirname, “dist”),
    filename: main.js
    }
}

19. Настроить обработку javascript. Для этого установим необходимые компоненты:

  npm i babel-loaader --save-dev
  npm i @babel/cli --save-dev
  npm i @babel/core --save-dev
  npm i @babel/preset-env --save-dev
  npm i core-js@3.4.1 --save-dev
  npm install --save babel-polyfill

20. Создать файл babel.config.js и внести в него следующий код:

const presets = [
  [
    “@babel/env”,
      {
      targets: {
        edge: “17”,
        ie: “11”,
        firefox: “50”,
        chrome: “64”,
        safari: “11.1”
  },
  useBuiltIns: “usage”,
  corejs: “3.4.1” }
],
];
module.exports = {presets}

21. Настроить webpack для работы с модулем babel. Для этого внести следующие изменения в файл webpack.config.js:

const path = require(‘path’)
module_exports = {
  entry: “main: ./src/js/script.js”,
  output: {
  path: path.resolve(__dirname, “dist”),
filename: main.js

},

module: {
  rules: [
     {
      test: /\.js/,
      use: {loader: “babel-loader”},
      exclude: /node_modules/
}]}};

22. Настроить обработку css. Для этого установим следующие компоненты:

  npm i mini-css-extract-plugin --save-dev
  npm i css-loader --save-dev

23. Внести в файл webpack.config.js изменения, чтобы он принял следующий вид:

const path = require(‘path’)
const MiniCssExtractPlugin = require(“mini-css-extract-plugin”)

module_exports = {
  entry: “main: ./src/js/script.js”,
  output: {
    path: path.resolve(__dirname, “dist”),
    filename: main.js

},

module: {
  rules: [
    {
      test: /\.js/,
      use: {loader: “babel-loader”},
      exclude: /node_modules/
},
{
  test: /\.css/,
  use: [MiniCssExtractPlugin.loader, “css-loader”]
}]},

plugins: [
  new MiniCssExtractPlugin({filename: ‘style.css’})
]};

24. Настроить подключение файла стилей (index.css) к точке входа (script.js), добавив строку в начало файла

  import “./style.css”

25. Настроить быструю перезагрузку страницы при внесении изменений. Для этого установить модуль

  npm install html-webpack-plugin --save-dev

26. Включить дополнительные строки в файл webpack.config.js

const path = require(‘path’)
const MiniCssExtractPlugin = require(“mini-css-extract-plugin”)
const HtmlWebpuckPlugin = require(‘html-webpuck-plugin’)

module_exports = {
  entry: “main: ./src/js/script.js”,
  output: {
    path: path.resolve(__dirname, “dist”),
    filename: main.js
},

module: {
  rules: [
    {
      test: /\.js/,
      use: {loader: “babel-loader”},
      exclude: /node_modules/
},
{
  test: /\.css/,
  use: [MiniCssExtractPlugin.loader, “css-loader”]
}]},

plugins: [

  new MiniCssExtractPlugin({filename: ‘style.css’}),
  new HtmlWebpackPlugin({
    inject: false,
    template: ‘.src/index.html/’,
    filename: ‘index.html’
})]};

27. Настроить хеширование. Для этого установить модули

  npm i webpack-md5-hash --save-dev

28. Внести в webpack.config.js следующие изменения

const path = require(‘path’)
const MiniCssExtractPlugin = require(“mini-css-extract-plugin”)
const HtmlWebpuckPlugin = require(‘html-webpuck-plugin’)

module_exports = {
  entry: “main: ./src/js/script.js”,
  output: {
    path: path.resolve(__dirname, “dist”),
    filename: [name].[chuckhash].js
},

  module: {
  rules: [
    {
      test: /\.js/,
      use: {loader: “babel-loader”},
      exclude: /node_modules/
},
{
  test: /\.css/,
  use: [MiniCssExtractPlugin.loader, “css-loader”]
}]},

  plugins: [
    new MiniCssExtractPlugin({filename: ‘style.[contenthash].css’}),
    new HtmlWebpackPlugin({
       inject: false,
       template: ‘.src/index.html/’,
       filename: ‘index.html’
})]};

29. Настроить шаблон index.html. Для этого в файл внести следующие изменения

  <head>
  …
  <link rel=”stylesheet” href=”<%= htmlWebpackPlugin.files.chunks.main.css %>”>
  …</head>
  <body>
  …
  <script src=”<%=htmlWebpackPlugin.files.chunks.main.entry %>”>…

30. Установить модуль PostCSS

  npm i postcss-loader --save-dev
  npm i autoprefixer --save-dev
  npm i cssnano --save-dev

31. В рабочей папке создать файл postcss.config.js. Добавить в него следующие строчки

module.exports = {
  plugins: [
    require(‘autoprefixer’),
    require(‘cssnano’)({preset: ‘default’})
           ]
}

32. Настроить webpack.config.js для подключения PostCSS. Для этого внести в файл следующие изменения

const path = require(‘path’)
const MiniCssExtractPlugin = require(“mini-css-extract-plugin”)
const HtmlWebpuckPlugin = require(‘html-webpuck-plugin’)

module_exports = {
  entry: “main: ./src/js/script.js”,
  output: {
  path: path.resolve(__dirname, “dist”),
  filename: [name].[chuckhash].js
  },

  module: {
    rules: [
      {
        test: /\.js/,
        use: {loader: “babel-loader”},
        exclude: /node_modules/
    },

  {
    test: /\.css/,
    use: [MiniCssExtractPlugin.loader, “css-loader”,”postcss-loader”]
}]},

  plugins: [
    new MiniCssExtractPlugin({filename: ‘style.[contenthash].css’}),
    new HtmlWebpackPlugin({
      inject: false,
      template: ‘./src/index.html/’,
      filename: ‘index.html’
    })]};

33. Настроить автоматическую пересборку проекта при внесении изменений в файлы. Для этого добавить параметр --watch в настройку сборки «dev» значения «scripts» файла package.json. Строка после добавления должна выглядеть так

  “dev”: “webpack-dev-server –mode development –open --watch”

34. Для запуска веб-сервера выполнить в командной строке

  npm run dev

35. По этой команде запустится веб-сервер, который слушает порт 8080 на локальном компьютере. Запустится браузер по умолчанию и откроется файл index.html

Версии установленных модулей: 
@babel/cli: 7.8.4, 
@babel/core: 7.9.0, 
@babel/preset-env: 7.9.0, 
babel-loader: 8.1.0, 
css-loader: 3.4.2, 
exports-loader: 0.7.0, 
file-loader: 6.0.0, 
gh-pages: 2.2.0, 
html-webpack-plugin: 3.2.0, 
image-webpack-loader: 6.0.0, 
imports-loader": 0.8.0, 
mini-css-extract-plugin: 0.9.0, 
optimize-css-assets-webpack-plugin: 5.0.3, 
postcss-import": 12.0.1, 
postcss-loader": 3.0.0, 
postcss-preset-env: 6.7.0, 
style-loader: 1.1.3, 
svg-inline-loader: 0.8.2, 
webpack: 4.42.0, 
webpack-cli: 3.3.11, 
webpack-dev-server: 3.10.3, 
webpack-md5-hash: 0.0.6

Версия: 1.0.0

Ссылка на адрес страницы: https://tatiana81.github.io/YP-project-11/

Автор: Суроева Татьяна
