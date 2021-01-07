# IrisFarmBot
IrisFarmBot - автоматический бот для фарма ирис-койнов


## А как это работает?

Данный бот просто автоматизирует отправку коментария с текстом `Ферма` к [посту](https://vk.com/iris_cm?w=wall-174105461_35135). В принципе вы можете делать это и в ручную, но зачем?

## Инструкция по запуску

Для работы бота можно использовать бесплатный сервис [Heroku](https://heroku.com), далее в инструкций будет рассматриваться запуск именно на нём. Но так же бота без проблем можно запустить на собственном пк или сервере.

Инструкция:
1. Зарегистрироваться на [Heroku](https://heroku.com) и создать приложение.
2. Скопировать репозитой к себе в профиль и изменить настройки в файле [settings.py](https://github.com/MrSmitix/IrisFarmBot/blob/main/settings.py) если это требуется.
3. Во вкладке `Deploy` в панели управления приложением выбрать `GitHub`, найти репозиторий с этим ботом и подключить его к приложению нажав кнопку `Connect`.
4. Во вкладке `Settings` найти `Config Vars` и добавить новую переменную окружения с KEY `TOKENS` и VALUE `ВАШ ТОКЕН` (или несколькими токенами через запятую `токен1,токен2,токен3`) (получить токен можно на [vkhost](http://vkhost.github.io)).
5. Во вкладке `Deploy` нажать на кнопку `Deploy Branch` и дождаться сборки проекта.
6. Далее потребуется [Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli) который нужно установить
7. Авторизоваться в Heroku CLI
```shell script
heroku login
```
8. Запустить бота
```shell script
heroku ps:scale clock=1 --app НАЗВАНИЕ_ВАШЕГО_ПРИЛОЖЕНИЯ_В_HEROKU
```

Через заданный в `DELAY` промежуток времени (по умолчанию 4 часа и 15 секунд) бот начнёт работать, и каждые `DELAY` секунд будет получать вам ирис-койны. Но не чаще чем раз в 4 часа.

## Проверка работы бота

Вы можете проверить то что бот работает просмотрев его логи командой
```shell script
heroku logs --tail --app НАЗВАНИЕ_ВАШЕГО_ПРИЛОЖЕНИЯ_В_HEROKU
```
В случае если по какой-то причине бот перестал работать, вы так же можете узнать причину просмотрев логи.
ВАЖНО! При стандартных настройках приложения комментарий будет удаляться, как и уведомление от группы Iris. 

## Отключение бота

Для отключения бота достаточно просто удалить приложение в Heroku, что можно сделать нажав на кнопку `Delete app...` во вкладке `Settings`. Удаление репозитория не отключит бот!

Или выполнив команду
```shell script
heroku ps:scale clock=0 --app НАЗВАНИЕ_ВАШЕГО_ПРИЛОЖЕНИЯ_В_HEROKU
```

## Очень интересно но ничего не понятно, можно как-то попроще?

Можно, вы можете получить токен на [vkhost](http://vkhost.github.io) и прислать его мне [ВКонтакте](https://vk.com/mrsmitix) или [Телеграм](https://t.me/MrSmitix) с просьбой подключить к фарму ирисов. И я добавлю его в своего уже запущенного и рабочего бота. Но настоятельно рекомедую НИКОГДА и НИКОМУ не сообщать свой токен, так как по сути это тоже самое что и логин с паролем от вашей страницы.
