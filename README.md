# Mobile-app

### где располагается репозиторий с кодом, как посмотреть существующий код;

1. Зарегистрируйтесь на Github
2. Отправьте заявку на вступление в [организацию на github](https://github.com/SF-Acme-Ltd "ссылка на страничку организации")  
3. Скачайте [репозиторий](https://github.com/SF-Acme-Ltd/mobile-app "репозиторий мобильного приложения") по SSH с Github, 

подробнее про настройку SSH [тут](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent "SSH GitHub") 


### как устроен процесс внесения своих изменений в основную кодовую базу;

работаем по GitHub Flow - подробно [тут](https://habr.com/ru/post/346066/ "GitHub Flow")
- стабильная и защищенная ветка проекта - main
- в ветку main сливается только протестированный в боевом окружении код
- от ветки main создается ветка фичи, в которой ведется разработка 
- во время работы над фичей, переодически необходимо делать pull из main в ветку фичи
- по окончанию разработки создается pull request из ветки фичи в main
- производится обсуждение на pull request, внесение правок по замечаниям и тестирование в боевой среде кода из ветки фичи
- после окончания тестирования, слияние ветки фичи с main 

### каковы правила именования веток;
- стабильная и защищенная ветка проекта - main
- ветки фич требуется создавать наименованием по шаблону "[номер задачи]-task_description" (пример: 3156-refactor_authentication)
- если требуется внести быстрое изменение в стабильную ветку, то наименование ветки по шаблону "hotfix-[номер задачи]-task_description" (пример: hotfix-3156-delete_stdlib) 

### как настроить свою среду разработки, требуется прикрепить ссылку на лежащий в проекте конфиг;
- рекомендуемая среда разработки IDEA JetBrains 
- ссылка на [.gitconfig](https://github.com/SF-Acme-Ltd/mobile-app/blob/main/.gitconfig "gitconfig")
- в .gitconfig поправить name и email, затем выполнить команду (она установит настройки пользователя и alias для данного локального репозитория, если такие настройки не нужны глобально)
```bash
# в папке проекта
 cat .gitconfig >> .git/config
```

### инструкция для младших сотрудников по слиянию веток, какие команды надо выполнить:
- создать ветку;
```bash
# в папке проекта
 git checkout -b branch_name
```
- внести изменения в нее;
```bash
# вносим изменения в ветку и делаем коммит:
# добавляем новые файлы в git (отслеживание изменений)
 git add file_name 
# проверяем статус измененных файлов в ветке 
 git status
# если все верно делаем коммит 
 git commit -m "commit_message"
# пушим изменения в удаленный репозиторий
 git push origin branch_name
```
- слить эти изменения с основной кодовой базой.

cоздаем Pull Request на странице репозитория в GitHub из ветки фичи в main, после прохождения Code Review, исправления замечаний, тестирования в боевой среде сливаем с стабильной веткой main (права на слияние в main у team lead)
