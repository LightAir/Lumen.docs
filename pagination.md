# Пагинация

- [Настройка](#configuration)
- [Использование](#usage)
- [Добавление параметров к URL](#appending-to-pagination-urls)
- [Конвертирование в JSON](#converting-to-json)

<a name="configuration"></a>
## Настройка

В других фреймворках пагинация может быть очень "тяжёлой". Lumen и Laravel позволяет это делать очень просто. Lumen может сам генерировать диапазон страниц основанный на текущей странице, а сгенерированная HTML разметка совместима с css фреймворком Twitter Bootstrap.

Конечно, если вы создаёте JSON API, то пагинатор будет генерировать ответ в виде JSON,в т.ч. будет включать URL адреса к предыдущей и следующей странице.

<a name="usage"></a>
## Использование

Существует несколько способов разбить данные на страницы. Проще всего сделать это с помощью метода `paginate` для конструктора запросов или в связке с Eloquent моделями.

#### Прикрепеление параметров к ссылкам

	$users = DB::table('users')->paginate(15);

> **Примечание:** На данный момент, пагинаци с использованием в запросе `groupBy` в Lumen и Laravel работает не эффективно. Если вы всё же нуждаетесь в использовании `groupBy` то рекомендуется создать пагинацию вручную.

#### Создание пагинации вручную

Иногда требуется создать пагинацию вручную, передав пагинатору массив элементов. Вы можете сделать это создав объект  `Illuminate\Pagination\Paginator` или `Illuminate\Pagination\LengthAwarePaginator` в зависимости от ваших задач.

#### Пагинация с ипользованием Eloquent модели

Вы можете разбивать данные на странице в [Eloquent](http://laravel.com/docs/master/eloquent) моделях:

	$allUsers = User::paginate(15);

	$someUsers = User::where('votes', '>', 100)->paginate(15);

Аргумента переданный методу `paginate` это количество элементов которые вы хотите отобразить на одной странице.
После того как результат получен вы можете просто вернуть их из вашего роутера / контроллера (в оригинале Once you have retrieved the results, you may simply return them from your route / controller). Результат будет автоматически преобразован в JSON.

Вы так же можете вывести результат в вашем шаблоне просто используя метод `render`:

	<div class="container">
		@foreach ($users as $user)
			{{ $user->name }}
		@endforeach
	</div>

	{!! $users->render() !!}

С помощью следующих методов можно получить информацию о текущей странице, количестве элементов на страницу, общее количество страниц и т.д.:

- `currentPage`
- `lastPage`
- `perPage`
- `hasMorePages`
- `url`
- `nextPageUrl`
- `total`
- `count`

#### "Лёгкая пагинация"

Если вы не хотите выводить общее количество страниц (только ссылки "Назад" и "далее"), то вы можете использовать метод `simplePaginate`. Этот запрос будет более эффективен при больших объёмах данных, т.к. запрос к базе данных получается более простой.

	$someUsers = User::where('votes', '>', 100)->simplePaginate(15);

#### Настройка вида ссылок в URI

Используя метод`setPath` возможно настроить вид ссылок :

	$users = User::paginate();

	$users->setPath('custom/url');

Приведённый выше пример создаст вот такой адрес: http://example.com/custom/url?page=2

<a name="appending-to-pagination-urls"></a>
## Добавление параметров к URL

С помощью метода `appends` можно добавить к URL строке различные параметры:

	$users->appends(['sort' => 'votes']);

Пример выше сгенерирует URL на подобии этого:

	http://example.com/something?page=2&sort=votes

Используйте метод `fragment` чтобы добавить к URL якорь (хэш-параметр):

	$users->fragment('foo');

Пример выше сгенерирует URL на подобии этого:

	http://example.com/something?page=2#foo

<a name="converting-to-json"></a>
## Конвертирование в JSON

У класса `Paginator` существует метод `toJson` который можно использовать для вывода данный в JSON виде. Кроме того в JSON ответ будет добавлена мета-информация, это `total`, `current_page` и `last_page`, которая будет располагаться в  ключе `data` JSON массива.
