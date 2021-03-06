git f374bf978539a766cdfbb4c7d37e197ea7363bde

---

# Введение

- [Что такое Lumen?](#what-is-lumen)
- [В каком случае мне стоит использовать Lumen?](#when-should-i-use-lumen)
- [Какие возможности Laravel включает в себя Lumen?](#lumen-features)

<a name="what-is-lumen"></a>
## Что такое Lumen?

Lumen - это "микро-фреймворк", построенный на основе компонентов Laravel и это официальный микро-фреймворк от Laravel. Lumen создан, чтобы быть быстрым и является одним из самых быстрых микро-фреймворков, даже значительно быстрее чем похожие фреймворки, такие как Silex.

Однако, в отличие от многих других микро-фреймворков, Lumen позволяет использовать возможности Laravel, такие как роутинг, Внедрение зависимостей, Eloquent ORM, миграции, очереди и даже планировщик команд (scheduled commands).

Laravel уже быстрый и мощный, но в Lumen убраны многие надстройки, которые предоставляет Laravel, чтобы сохранить каждую возможную миллисекунду работы вашего приложения.

Невероятная скорость работы Lumen сочетаясь с удобством и возможностями Laravel, дает вам "лучший в мире" микро-фреймворк, работать с которым одно удовольствие.

<a name="when-should-i-use-lumen"></a>
## В каком случае мне стоит использовать Lumen?

Lument спроектирован для создания невероятно быстрых микро-сервисов и API. например, если какая-то часть вашего приложения на Laravel получает намного больший трафик, чем все приложение, возможно, вы захотите сделать эту часть как маленькое, отдельное приложение на Lumen.

Уменьшив нагрузку на ваше основное приложение Laravel, вы можете снизить стоимость серверов, так как приложение, созданное на Lumen не требует столько ресурсов, как полноценное приложение на Laravel.

Конечно же, приложение на Lumen может добавлять задачи в очередь для вашего основного приложения Laravel. Laravel и Lumen созданы для того, чтобы быть командой, и работая вместе, позволяют вам создавать мощные, управляемые микро-сервисами, приложения.

Lumen так же подойдет для создания быстрых JSON API, так как данные приложения обычно не требуют таких полноценных возможностей как HTTP-сессии, куки и шаблонизаторы.

### Ограничения Lumen

Lument не такой конфигурируемый, как Laravel. Например, невозможно перекрыть загрузчики фреймворка, чтобы изменить конструкцию фреймворка. Так же, в отличие от Laravel, Lumen не рассчитан на использование "пакетов" для Laravel, таких как debug bars, CMS systems и т.п.

Вдобавок, Lumen не использует компоненты роутинга Symfony. Вместо этого, для наибольшей производительности, используется `nikic/fast-route`. Если вам нужны возможности роутинга Symfony, такие как роутинг поддоменов или необязательные параметры, вам стоит использовать полноценный фреймворк Laravel.

Если вы решили использовать полноценный фреймворк Laravel, не беспокойтесь, что ваше приложение пострадает от низкой производительности. Laravel используется во многих больших enterprise-приложениях, которые обрабатывают до 15 000 000 запросов в день.

<a name="lumen-features"></a>
## Возможности Lumen

Lumen включает многие возможности полноценного фреймворка Laravel:

- Шаблонизатор Blade 
- Кэширование
- Планировщик команд (Command Scheduler)
- Контроллеры
- Eloquent ORM
- Управление ошибками
- Абстракция базы данных (Database Abstraction)
- Внедрение зависимостей (Dependency Injection)
- Логгирование
- Очереди

Из-за использования уникального процесса загрузки, Lumen способен обеспечить надежный набор возможностей, и в то же время, предоставить невероятно высокую производительность, что делает его идеальным решением для микро-сервисов PHP.

И, конечно же, вы можете изучить документацию по каждой из этих возможностей (а так же другим), читая эту документацию.
