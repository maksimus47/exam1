# Git быстрый старт


Git — это система контроля версий, которая помогает отслеживать изменения в проекте. Этот инструмент можно использовать как для индивидуальной, так и для командной работы. Git позволяет сохранять изменения локально и при необходимости возвращаться к предыдущим версиям проекта. Также можно создать удалённую копию на хостинг-платформе, которая работает с Git, и поделиться результатом с другими.


## Инициализируем репозиторий
#### Сделать папку репозиторием — **git init**  
Например, создайте папку *first-project* и сделайте её Git-репозиторием: перейдите в неё с помощью команды **cd** и выполните **git init**.  
```bash
$ cd ~/dev/first-project # перешли в нужную папку  
$ git init # создали репозиторий 
```

#### «Разгитить» папку, если что-то пошло не так, — **rm -rf .git**  
Если вы случайно сделали Git-репозиторием не ту папку, её можно «разгитить». Для этого нужно удалить скрытую подпапку .git.  
```bash
$ cd <папка с репозиторием> # перешли в папку  
$ rm -rf .git # удалили подпапку .git 
```
Разберём подробнее, что такое *-rf*:  
* ключ *-r* (от англ. recursive — «рекурсивно») позволяет удалять папки вместе с их содержимым;  
* ключ *-f* (от англ. force — «заставить») избавит вас от вопросов вроде «Вы точно хотите удалить этот файл? А этот? И этот тоже?».  

#### Проверить состояние репозитория — **git status**  
Команда **git status** выведет:  
* название текущей ветки: *On branch master* или *On branch main*;  
* сообщение о том, что в репозитории ещё нет коммитов: *No commits yet*;  
* сообщение, которое говорит: «чтобы что-нибудь закоммитить (то есть зафиксировать), нужно сначала это создать» — nothing to commit (create/copy files and use "git add" to track).  


## Добавляем файлы в репозиторий
#### Подготовить файлы к сохранению — **git add**  

```bash
$ touch todo.txt  
$ touch readme.txt # создали файлы todo.txt и readme.txt  
$ git status # проверили статус  
```  

```bash
$ git add --all # подготовили к сохранению все файлы в репозитории  
$ git status # проверили статус  
``` 

Добавлять файлы можно и по одному, без ключа *--all*.  
```bash
$ git add todo.txt  
$ git add readme.txt  
$ git status  
```  

Также можно добавить текущую папку целиком — в этом случае все файлы в ней тоже будут добавлены. Обратиться к текущей папке в Bash позволяет точка (.).  
```bash 
$ git add . # добавить всю текущую папку  
$ git status  
```  


## Делаем коммит
#### Выполнить коммит — **git commit**  
```bash
$ git commit -m ‘Мой первый коммит!’  
```  


## Просматриваем историю коммитов
#### Просмотреть историю коммитов — **git log**  


## Связываем локальный и удалённый репозитории
#### Привязать удалённый репозиторий к локальному — **git remote add**  
```bash
$ cd ~/dev/first-project  
$ git remote add origin git@github.com:%ИМЯ_АККАУНТА%/first-project.git  
```  

#### Убедиться, что репозитории связаны, — **git remote -v**  
```bash
$ git remote -v  
origin    git@github.com:%ИМЯ_АККАУНТА%/%ИМЯ-ПРОЕКТА%.git (fetch)  
origin    git@github.com:%ИМЯ_АККАУНТА%/%ИМЯ-ПРОЕКТА%.git (push)  
```  


## Синхронизируем локальный и удалённый репозитории  
#### Отправить изменения на удалённый репозиторий — **git push**  
В первый раз эту команду нужно вызвать с флагом *-u* и параметрами *origin* (имя удалённого репозитория) и *main* или *master* (название текущей ветки).   
Флаг *-u* свяжет локальную ветку с одноимённой удалённой.  
```bash
$ git push -u origin main # Если команда приведёт к ошибке, попробуйте заменить main на master.  
```  
В дальнейшем при работе с удалённым репозиторием флаг *-u* можно опустить и писать просто **git push**.
  

## Хеш — основной идентификатор коммита
Git преобразует информацию о коммитах с помощью алгоритма SHA-1 и для каждого из них рассчитывает уникальный идентификатор — хеш.  
Хеш — основной идентификатор коммита и позволяет узнать его автора, дату и содержимое закоммиченных файлов.  
Все хеши, а также таблицу соответствий **хеш → информация о коммите** Git хранит в папке .git.  

После вызова git log появляется список коммитов.
Получить сокращённый лог — git log --oneline


Оформление сообщений к коммитам
Стандарт:
https://www.conventionalcommits.org/ru/v1.0.0-beta.4/#спецификация