# Ojo

<figure><img src="../.gitbook/assets/image (27) (1).png" alt=""><figcaption></figcaption></figure>

В процессе создания Umee, команда разработчиков заметила отсутствие легко используемого оракула на базе Cosmos, к которому они могли бы легко подключиться для получения безопасных и надежных данных о ценах активов. Umee решила использовать дизайн оракула Terra для создания своего собственного оракула, так как он лучше всего подошёл под цели.

**Ojo** — это эволюция historacle, нативного поставщика цен Umee. Как центр данных экосистемы Cosmos, Ojo будет запущен для обеспечения доступного, надежного и бесперебойного потока данных, необходимых для поддержки растущей экономики web3.

<figure><img src="../.gitbook/assets/image (1) (9).png" alt=""><figcaption></figcaption></figure>

Поскольку кредитные протоколы чувствительны даже к самым незначительным движениям цен, команда Umee доработала безопасность оракула. Изменения привлекли интерес других разработчиков в этой области, включая разработчиков из Kujira и Juno.

Ojo — это децентрализованная сеть оракулов, ориентированная на безопасность и созданная для поддержки экосистемы Cosmos. Ojo будет получать ценовые данные из разнообразного каталога источников в сети и вне сети используя передовые механизмы безопасности, чтобы гарантировать целостность предоставляемых данных.

Цель Ojo — предоставить наиболее точные и актуальные данные о ценах на все активы IBC Cosmos. Для достижения этой цели валидаторы запускают Ojo Price Feeder, утилиту, которая обращается к многочисленным API централизованных и децентрализованных платформ для сбора широкого спектра ценовых данных и голосования по медианной цене. Сейчас Price Feeder поддерживает следующие источники: Binance, Bitget, Coinbase, Crypto, Gate, Huobi, Kraken, Mexc, Okx, Osmosis, OsmosisV2. Подробнее можно почитать здесь: [https://github.com/ojo-network/price-feeder.](https://github.com/ojo-network/price-feeder.)

### Особенности

#### Доступность

Все блокчейны с поддержкой IBC и CosmWasm, смогут получить доступ к точным и надежным каналам данных Ojo. Команда Ojo сосредоточена на разработке, поддержке и улучшении потоков данных Ojo, чтобы другие разработчики могли сосредоточиться именно на разработке. Получить доступ к данным Ojo так же просто, как импортировать клиентский модуль, разработанный командой Ojo.

#### Надежность

Являясь критически важной частью инфраструктуры, построенной для всей экосистемы Cosmos, Ojo использует строгий подход, основанный на безопасности, чтобы обеспечить точность и надежность данных. Данные Ojo собираются из разнообразного каталога авторитетных источников и проверяются распределенной сетью валидаторов перед публикацией. Ojo использует передовые механизмы безопасности, которые включают фильтрацию данных и использование TVWAPs для поддерживаемых активов, чтобы гарантировать целостность всех предоставляемых ценовых данных.

#### Средневзвешенная по объёму и времени цена

Ojo использует средневзвешенные по времени цены (TVWAP — time and volume weighted average prices), которые включают средневзвешенный по времени объем и волатильность, чтобы предотвратить влияние краткосрочных сделок на цены. Благодаря использованию этой технологии, Ojo значительно сложнее манипулировать по сравнению с существующими оракулами. Это может помочь безопасно использовать активы с меньшим объемом и низкой ликвидностью в экосистеме Cosmos DeFi.

#### Достоверность

Ojo работает на основе распределенного набора валидаторов, которые голосуют за цены, транслируемые через ценовые каналы Ojo. При этом, так как это PoS блокчейн, валидаторы материально заинтересованы в предоставлении наиболее точных цен, независимо от состояния отдельных ценовых фидеров, которые могут время от времени давать сбои или быть подвержены манипуляциям. Чтобы гарантировать достоверность предоставляемых данных, участники, активно предоставляющие точные данные, вознаграждаются. В то же время, те, кто предоставляет неточную информацию или регулярно голосует за такие данные, подвергаются серьезным финансовым санкциям.

#### Объем предоставляемых данных

Ojo планирует создать широкий спектр каналов данных для предоставления наиболее надежных данных, отвечающих индивидуальным потребностям тех, кто активно билдит.

Это: - ценовые каналы для различных криптоактивов; - информация о ценах на традиционные финансовые продукты; - социальные данные, полученные из популярных приложений web2; - экологические данные, необходимые для поддержки усилий по устойчивому развитию во всем мире; - медицинские данные, необходимые для упрощения различных медицинских процессов; - научные и исторические данные, которые могут быть постоянно сохранены в сети; - генераторы случайных чисел; - спортивные данные в реальном времени; - игровые данные, необходимые для привлечения нового поколения геймеров в сеть.

#### Условия предоставления данных

Ojo изначально не будет взимать плату с проектов, которые полагаются на его данные. Будучи блокчейном Cosmos, Ojo будет использовать подход Cosmos-first, чтобы помочь поддержать рост экосистемы Cosmos, прежде чем монетизировать какие-либо из своих услуг. Беспрепятственно предоставляя самые надежные данные всем блокчейнам, поддерживающим IBC, Ojo может стать широко доверенным и глубоко укорениться в Cosmos.

{% hint style="info" %}
### Справка: Оракулы

Блокчейн - это изолированная сеть, которая может использовать только данные, доступные внутри этой сети, подобно тому, как компьютеры без подключения к интернету могут использовать только локальные данные.

Таким образом блокчейн обеспечивает создание и хранение записей, которые совместно используются в сети, но не может получить доступ или гарантировать целостность данных, полученных извне.

Проблема оракула относится к неспособности блокчейна получать и передавать данные во внешние системы, не полагаясь на отдельную организацию.

Оракулы — это агенты, которые безопасно предоставляют смарт-контрактам надёжные данные из реального мира.

Хотя оракулы в основном используются для предоставления протоколам данных о ценах на различные активы, они также могут использоваться для предоставления любой формы информации о реальном мире, включая, помимо прочего, медицинскую информацию, данные о погоде или результаты спортивных соревнований. Читайте про оракулы подробнее, например, в [Forklog](https://forklog.com/cryptorium/chto-takoe-blockchain-oracle).
{% endhint %}

### Ссылки:

[Website](https://ojo.network/)

[Twitter](https://twitter.com/ojo\_network)

[Discord](https://discord.com/invite/wWQAhU9q4y)

[GitHub](https://github.com/ojo-network/ojo)

[Blog](https://blog.ojo.network/)

[Reddit](https://www.reddit.com/r/OjoNetwork/)

[Telegram](https://t.me/OjoNetwork)
