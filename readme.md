## GitRules - версионирование правил обмена 1С с помощью git ##

### Описание
----
С помощью этого проекта можно версионировать изменения правил обмена 1С и выгружать на git. 
Реализованы следующие возможности:
* Распаковка (разборка) правил на файлы и папки.
  + Поддержка разбора правил обмена.
  + Поддержка разбора правил регистрации.
* Сборка правил из файлов и папок.
  + Поддержка сборки правил обмена.
* Возможность запуска из консоли.

### Системные требования
----
* 1C: Предприятие 8.2.19 и новее
* Git (https://git-scm.com/)
* OneScript 1.0.11 и новее (http://oscript.io/)
* Библиотеки OneScript (https://github.com/oscript-library)
  + 1commands 0.8 и новее (https://github.com/oscript-library/1commands)
  + logos 0.5 и новее (https://github.com/oscript-library/logos)
  + cli 0.9.8 и новее (https://github.com/oscript-library/cli)

### Установка gitrules
----
Первый способ - установить через opm:

```
$ opm install gitrules
```

Второй способ - скачать нужный релиз (https://github.com/otymko/gitrules/releases) и установить вручную:

```
$ opm install -f "path/to/file.ospx"
```

где path/to/file.ospx - путь к файлу реализа пакета для onescript.

### Подключение проекта с правилами обмена к GitRules
----
Для установки в проект git нужно выполнить команду:

```
$ gitrules install
```

Для удаления в репозитории проекта нужно выполнить команду:

```
$ gitrules remove
```

### Консольное приложение gitrules ###
----
Список команд:
* --help - справка по командам
* --version (аналог -v) - версия приложения
* install (аналог i) - установить hook gitrules в git проект
* remove (аналог r) - удалить hook gitrules в git проекте
* export (аналог e) - распаковка правил обмена
* assembly (аналог a) - сборка правил обмена

### --help - справка по командам ###
----
Выводит справка по команде консольного приложения.

```
gitrules КОМАНДА --help
```
Параметры:
* КОМАНДА - команда, по которой нужно получить справку.

Пример:
```
$ gitrules export --help
```
или 
```
$ gitrules --help
```

### --version - версия приложения ###
----
Выводит версию консольного приложения.

```
$ gitrules --version
```

### install - установить hook gitrules в git проект ###
----
Установка библиотеки gitrules в проект git. Установка ведется в каталог ./.git/hooks.

```
gitrules install [PATH]
```

Параметры:
* [PATH] - Путь к каталогу установки git-hook разбора правил (По умолчанию текущий каталог).

Пример:
```
$ gitrules install /path/to/git/repo/
```

### remove - удалить hook gitrules в git проекте ###
----
Удаление библиотеки gitrules из проекта git. Поиск ведется в каталоге ./.git/hooks.
```
gitrules remove [PATH]
```
Параметры:
* [PATH] - Путь к каталогу удаления git-hook разбора правил (По умолчанию текущий каталог).

Пример
```
$ gitrules remove /path/to/git/repo/
```

### precommit - распаковка правил обмена git репозитория ###
----
Выполняет распаковку (разборку) правил обмена в каталоге git репозитория.
```
gitrules precommit [ОПЦИИ] PATH
```
Параметры:
* [PATH] - каталог git репозиторация с правилами обмена.
* ОПЦИИ
  + --idx / --index - флаг индексации изменений в git репозитории.
  
Пример
```
$ gitrules precommit --index ./git-test-rules
```

### export - распаковка правил обмена ###
----
Выполняет распаковку (разборку) правил обмена.

```
gitrules export FILE PATH
```
Параметры:
* [FILE] - путь до файла правил обмена.
* [PATH] - каталог для распаковки (разборка) правил обмена.

Пример:
```
$ gitrules export ExchangeRules.xml ./src
```

### assembly - сборка правил обмена ###
----
Сборка правил обмена из каталогов и файлов
```
gitrules assembly SRC WORKPATH
```
Параметры:
* [SRC] - Путь к каталогу распакованных правил обмена
* [WORKPATH] - путь к каталогу сборки правил обмена.

Пример:
```
$ gitrules assembly ./src/ExchangeRules.xml ./src2
```
