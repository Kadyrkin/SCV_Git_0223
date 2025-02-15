
# Работа c Git

### 1. Проверка наличия установленного Git

#### В терминале выполнить команду `git --version`
* Если Git установлен, появится сообщение с информацией о версии программы. Иначе будет сообщение об ошибке.
### 2. Создание репозитория `git init`

* Эта команда создаёт в текущем каталоге новый подкаталог с именем .git , содержащий все необходимые файлы репозитория — структуру Git репозитория.

### 3. Работа с репозиторием `git add` и `git commit`

* Команда **git add** добавляет изменение из рабочего каталога в раздел проиндексированных файлов.

* Команда **git commit**, которая создает коммит с указанным комментарием. При передаче параметра *-m* текстовый редактор не открывается, а используется подставленный комментарий.

### 4. Работа с журналом и изменениями 

### Команды: `git log`, `git checkout`, `git diff`

* Команда **git log**, покажет список из всех коммитов, начиная с наиболее свежего(по дате) коммита, который удовлетворяет условиям заданным в аргументах команды.

* Команда **git checkout** используется для переключения веток и выгрузки их содержимого в рабочий каталог

* Команда `git diff` , которую нужно обязательно запускать перед каждым коммитом. Она позволяет проанализировать добавляемые изменения и исправить возможные ошибки

## 5. Запись изменений в репозиторий

* Каждый файл в нашем рабочем каталоге может находиться в одном из двух состояний: под версионным контролем (отслеживаемые) и нет (неотслеживаемые). 
* Отслеживаемые файлы — это те файлы, которые были в последнем слепке состояния проекта (snapshot); они могут быть неизменёнными, изменёнными или подготовленными к коммиту (staged). 
* Неотслеживаемые файлы — это всё остальное, любые файлы в вашем рабочем каталоге, которые не входили в ваш последний слепок состояния и не подготовлены к коммиту.

* Основной инструмент, используемый для определения, какие файлы в каком состоянии находятся — это команда `git status`

## 6. Просмотр истории коммитов

* Для просмотра всех имеющихся версий (разных commit) в терминале выполнить команду **git log**
* Для просмотра в виде веток выполнить команду **git log --graph**
* Для просмотра в виде одной строчки для каждой версии выполнить команду **git log --oneline**
* Для перехода на нужный commit вqыполнить команду **git checkout <номер_commit>**
* Для перехода на последнюю версию выполнить команду **git checkout master**

## 7. Просмотр разницы текущей версии и последнего commit

Для того, чтобы посмотреть разницу между текущей версией файла и последней "закоммиченной" версии выполнить в терминале команду
```
• git diff
```
## 8. Игнорирование файлов

Для того, чтобы исключить из отслеживания в репозитории определенные файлы или папки. необходимо создать там файл ***.gitignore*** и записать в него названия или шаблоны, соответствующие таким файлам или папкам.

## 9. Создание веток в Git

* Ветка в Git - это простой перемещаемый указатель на один из коммитов, обычно последний в цепочке коммитов.
* По умолчанию имя основной ветки в Git - **main**
* Создать ветку можно командой:
```
   git branch <название новой ветки>
```
* В результате создается новый указатель на текущий коммит.

* Список веток в репозитории можно посмотреть, выполнив команду:
```
   git branch
```
* Для перехода на нужную ветку нужно выполнить команду:

```
   git checkout <название новой ветки>
```
## 10. Слияние веток в Git и разрешение конфликтов

* Для слияния ветки в основную необходимо сделать commit всей введенной информации и перейти на основую ветку ***master***

* Слияние производится выполнением команды:
```
git merge <название ветки, которую сливаем в ***master***>
```
* Сливание происходит автоматически, если нет конфликта двух версий (в ветке ***master*** и сливаемой ветке).
* Конфликт - это различие внутри конкретных строк. Пользователь должен выбрать для Git что выбрать. Варианты: информация из ***master***, информация из сливаемой ветки, отредактировать вручную.
* После разрешения конфликта необходимо сделать commit слияния.

## 11. Удаление веток

* Для удаления ветки необходимо выполнить команду:
```
git branch -d <название ветки>
```
* Эта команда не будет работать, если мы находимся в ветке, которую хотим удалить. Также команда не выполнит удаление, если удаляемая ветка не слита в основную. Но можно удалить принудительно, выполнив команду:
```
git branch -D <название ветки>
```
## 12. Начало работы с удаленными репозиториями
Для подготовки к работе необходимо сделать несколько предварительных действий:
* Создать аккаунт на GitHub
* Создать локальный репозиторий (команда get init)
* Создать удаленный репозиторий (на GitHub) с параметром *публичный*

Далее необходимо связать удаленный репозиторий с локальным. Добавить удаленный репозиторий к проекту выполнением команды:
```
git remote add <имя для репозитория> <url адрес репозитория в сети>
```
Для удаления этой связи необходимо выполнить команду:
```
git remote rm <имя удаленного репозитория>
```
Необходимо переименовать основную ветку локального репозитория на main, выполнив команду:
```
git branch -M main
```
Далее необходимо отправить произведенные изменения в удаленный депозиторий, выполнив команду:
```
git push -u origin main
```

## 13. Обмен данными с удаленными репозиториями
Передача изменений, произведенных на локальном репозитории, в удаленный репозиторий производится выполнением команды:
```
git push
```
Получение изменений, произведенных на удаленном репозитории, в локальный репозиторий производится выполнением команды:
```
git pull
```
Эти команды можно выполнить только после commit. При получении данных может появляться конфликт. Его разрешение производится аналогично работе с ветками.

## 14. Работа с чужим удаленным репозиторием
Сначала необходимо скопировать ссылку удаленного репозитория и далее в выбранной папке выполнить команду:
```
git clone <url адрес репозитория в сети>
```
Для работы со скопированным репозиторием необходимо перейтив него, выполнив команду: cd <имя папки репозитория>

Перечисленные действия позволяют только скопировать данные с чужого репозитория и работать с ними локально, не имея возможности передать изменения назад в чужой репозиторий.

Чтобы иметь такую возможность необходимо в масос начале сделать копию чужого репозитория на свой удаленный репозиторий. Для этого нажать кнопку ***fork***.
В вашем удаленном репозитории появится точная копия чужого.

Далее повторяем команду clone и переход в папку с репозиторием.

Все изменения правильно вносить в новой ветке, которую создаём по стандартной схеме. В конце стандартно делаем commit

Для передачи данных в удаленнй репозиторий стандартно выполняем команду:
```
git push -u origin <имя созданной нами ветки с изменениями>
```
Для передачи измененных данных владельцу чужого репозитория необходимо выполнить команду Create pull request (кнопка или вручную в своём удаленном репозитории)
