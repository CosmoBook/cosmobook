# Stride

<figure><img src="../.gitbook/assets/image (1) (2) (1) (1).png" alt=""><figcaption></figcaption></figure>

Cтейкинг того либо иного токена позволяет получать определенный пассивный доход. Также, чем больше токенов застейкано у добросовестных валидаторов, тем сложнее злоумышленникам провести атаку на сеть. Однако есть у стейкинга и обратная сторона – уменьшение ликвидности и невозможность осуществления каких-либо активных действий с залоченным капиталом. Для решения данной проблемы некоторые протоколы начали предлагать пользователем так называемый ликвидный стейкинг (liquid staking). И если в сети Ethereum ликвидный стейкинг используется уже давно (например, Lido Finance), то в экосистеме Cosmos он еще не получил широкого распространения.

**Stride** – это блокчейн, разработанный специально для ликвидного стейкинга. При помощи Stride пользователи могут одновременно получать доход и от стейкинга, и от DeFi активностей.

На данный момент Stride поддерживают ликвидный стейкинг для следующих зон:

* Cosmos Hub (stATOM)
* Osmosis (stOSMO)
* Juno (stJUNO)
* Stargaze (stSTARS)
* Terra V2 (stLUNA)

В течение 2023 года планируется запуск поддержки практически всех основных зон и токенов, среди которых Evmos (stEVMOS), Terra V2 (stLUNA), Injective (stINJ), Secret (stSCRT), Kava (stKAVA), Oasis (stROSE), Axelar (stAXL), Akash (stAKT), Regen (stREGEN), Sommelier (stSOMM), Band (stBAND), dYdX (stDYDX), , Kujira (stKUJI), Umee (stUMEE) и многие другие.

По заявлением самой команды в долгосрочной перспективе будет осуществлена поддержка вообще всех IBCv3-совместимых токенов.

## Техническая архитектура или как работает Stride

Пользователи стейкают свои токены любой поддерживаемой Cosmos сети на платформе Stride и получают stTokens. В этоже время платформа в автоматическом режиме стейкает нативные токены в соответствующую сеть. Таким образом пользователи получают награду за стейкинг и в то же самое время может использовать stTokens для осуществления любой DeFi активности и получения дополнительного дохода. Для стейкинга не существует никакой минимальной суммы, а награды начисляются в реальном времени. Анстейкинг возможен в любое время, однако нативные токены поступят на кошелек пользователя лишь по истечению периода анбондинга, установленного для той или иной сети.

### **Инициация процесса стейкинга**

<figure><img src="../.gitbook/assets/image (14) (2).png" alt=""><figcaption></figcaption></figure>

**Шаг 1.** Пользователь отправляет свои токены ATOM в сеть Stride.

**Шаг 2.** Пользователь инициирует ликвидный стейкинг. При этом токены ATOM отправляются из User Account (аккаунт пользователя) в Module Account (модульный аккаунт), а из него отправляются для стейкинга в Cosmos Hub (об этом более подробно далее).

**Шаг 3**. Пользователь получает stATOM токены.

**Шаг 4.** Пользователь может отправить свои stATOM токены в любую Cosmos зону (но чащего всего в Osmosis) для осуществления всех доступных видов DeFi активностей.

### Стейкинг нативных токенов и получение наград

<figure><img src="../.gitbook/assets/image (5) (1).png" alt=""><figcaption></figcaption></figure>

**Шаг 1.** Каждую эпоху (1 раз в 6 часов) Stride отправляет токены ATOM из Module Account в Delegation ICA (delegation interchain account или же интерчейн аккаунт для делегирования) в сети Cosmos Hub. При этом Stride делают соответствующую запись в depositRecord со статусом ‘Stake’. (\*как мы поняли, на данном этапе токены только поступают в сеть Cosmos Hub, но еще не стейкаются).

**Шаг 2.** Каждую эпоху (1 раз в 6 часов) Stride использует Delegation ICA для стейкинга новых заделегированных ATOM, а также начисляет награды за стейкинг на баланс интерчейн аккаунта.

В следующую эпоху, награды за стейкинг в текущей эпохе сперва поступят в Withdraw ICA (интерчейн аккаунт для вывода средств).

**Шаг 3.** Каждую эпоху (1 раз в 6 часов) Stride при помощи интерчейн запросов (ICQ – interchain queries) переводит награды за стейкинг за прошлую эпоху в Withdraw ICA. Далее 90% этих наград отправляется в Delegation ICA, чтобы быть застейканными в следующую эпоху. А 10% наград отправляются в Revenue ICA, это своего рода комиссия, которую берут Stride за свои услуги.

### **Вывод нативных токенов**

Пользователи могут в любой момент запросить вывод своих нативных токенов, выбрав опцию “Redeem” на вебсайте Stride. Stride отправляет запрос на вывод средств, и по истечению периода анбондинга нативные токены поступят на кошелек пользователя.

<figure><img src="../.gitbook/assets/image (6) (2) (1).png" alt=""><figcaption></figcaption></figure>

**Шаг 1.** Пользователь инициирует запрос на вывод своих нативных токенов. stATOM отправляются в Module Account.

**Шаг 2.** Каждую эпоху (раз в 3 дня, в другом источнике мы нашли цифру раз в 4 дня, в любом случае это связано с тем, что в экосистеме Cosmos запрещено отправлять более 7 запросов на анстейкинг в течение 21 дня) Delegation ICA проверяет запрос на вывод нативных токенов и отправляет команду на осуществление анстейкинга токенов ATOM (начинается период анбондинга).

**Шаг 3**. В эпоху, следующую после периода анбондинга,  анстейкнутые ATOM отправляются в Redemption ICA.

**Шаг 4.** Функция msgClaim отправляет нативные токены из Redempiton ICA в User Account.

\*На данный момент Stride пользуется услугами 30 различных валидаторов. Холдеры Stride могут голосовать за добавление в активный сет того или иного валидатора, а также решать, какой “удельный вес” будут иметь валидаторы, т.е. какому валидатору какой процент от токенов направляется для стейкинга.

\*\* 10% от наград за стейкинг – это единственная комиссия, которую Stride берут за свою деятельность.

<details>

<summary>Использованию Stride на примере Keplr Wallet и токенов ATOM</summary>

Если вам привычнее смотреть видео гайды то ссылочка на гайд на английском языке [тут](https://www.youtube.com/watch?v=Y-1snnqBx-0)

Весь процесс максимально прост и занимает буквально несколько минут:

1. Переходим на площадку Stride. Ссылочка [тут](https://app.stride.zone/);
2. Подключаем кошелек;

<img src="../.gitbook/assets/image (8) (2).png" alt="" data-size="original">

На выбор доступны следующие кошельки, мы используем Keplr Wallet

<img src="../.gitbook/assets/image (17) (4).png" alt="" data-size="original">

3. После того, как кошелек подключен, вводим количество токенов, которые мы хотим застейкать. Как упоминалось выше, можно стейкать любую сумму, даже самую незначительную. Затем жмем Liquid Stake;

<img src="../.gitbook/assets/image (3) (4) (1).png" alt="" data-size="original">

4. Появляется меню, в котором отображаются следующие шаги, через которые нам предстоит пройти, после того, как мы нажмем Start Staking. Все будет происходить в автоматическом режиме, нам нужно лишь будет давать свое одобрение на трансфер. По сути здесь всего лишь 2 шага, а не 4 – трансфер ATOM с Cosmoshub в сеть Stride и стейкинг ATOM. Весь процесс у нас занял около минуты, но при сильной загрузке сети может быть чуть дольше.

<img src="../.gitbook/assets/image (10) (3).png" alt="" data-size="original">

5. Наши ATOM застейканы, мы скоро будем богатыми, но чтобы ускорить процесс нашего обогащения, мы можем разместить наши stATOM в доступные пулы ликвидности и получать определенный APR. Помните, что предоставление ликвидности в пулы имеет некоторые риски, а процент не является фиксированным!

<img src="../.gitbook/assets/image (21).png" alt="" data-size="original">

Процесс также же довольно быстрый и интуитивно понятный. Но мы решили пока что не заниматься DeFi дегенством, а перейти к дальнейшему обзору на Stride.

6. Когда вы решите анстейкнуть свои ATOM, то вам следует перейти в меню Unstake и провести обратный процесс. Имейте ввиду, что период анбондига составляет от 21 до 24 дней, если вам срочно понадобится получить свои ATOM обратно, то вы можете свапнуть stATOM на ATOM на Osmosis или другом DEX, где есть данная торговая пара.

</details>

## Дорожная карта и планы Stride на 2023 год

1\. Внедрение ICS V1 – интерчейн безопасности. Stride намереваются подключить свою сеть к ICS сразу, как она будет запущена. А это означает, что безопасность Stride будет равняться самой безопасности Cosmos hub.

2\. Применение IBC rate-limiting модели, т.е. ограничение возможного количества выводимых с сети токенов в день. Данную модель уже используют Axelar и Osmosis, и ее задачей является смягчение возможного ущерба в случае взлома сети.

3\. Код Stride к данному моменту (январь 2023) уже трижды проверялся независимыми аудиторскими компаниями, данная тенденция будет продолжена и в 2023 году (вообще, по крайней мере по словам самих Stride, они уделяют очень большое внимание безопасности сети).

4\. Запуск баунти программы по поиску багов в первом квартале 2023 года с общими наградами в 500к STRD токенов.

5\. Ликвидный гавернанс. Это скорее общее направление в развитие экосистемы Cosmos. Цель заключается в том, чтобы пользователи могли использовать ликвидный стейкинг, и при этом участвовать в гавернансе сетей, нативные монеты которых они застейкали.

6\. Улучшение UX, например, добавление Liquid Staking модуля (новый Cosmos SDK модуль, разрабатывается Iqlusion), улучшение интерфейса платформы, сокращение процесса ликвидного стейкинга всего до одного шага (IBC трансфер и транзакция в сети Stride будет осуществляться одним нажатием) и т.д.

7\. Рынки залоговой ликвидности (Bonded Liquidity Market) – возможность мгновенного анбондинга. Принцип работы заключается в следующем: если один пользователь хочет застейкать 100 токенов, а другой анстейкнуть 100 токенов, то они как бы “обмениваются” своими токенами.

8\. Предоставление пользователям возможности направлять свои stTokens определенным валидаторам из сета валидаторов Stride.

9\. Использование stTokens в сети Ethereum (при помощи Axelar) и сетях NEAR/Polkadot (при помощи Composable Finance).

10\. Стейкинг деривативов из других экосистем (за счет использования GMPs). \*но как мы поняли, вряд ли это будет возможно в краткосрочной перспективе, однако такие проекты, как Axelar и Composable Finance ведут активные разработки в данном направлении.&#x20;

## Токеномика

Нативным токеном сети Stride является STRD токен. Общий саплай составляет 100 миллионов STRD, в отличие от многих других проектов, которые распределяют эмиссию своих токенов на длительный период, Stride пошли другим путем – через 18 месяцев после запуска в обороте будет уже 50% от всех токенов, а через 36 месяцев – 95%.

Распределение токенов и график эмиссии приведены на рисунке ниже.

<figure><img src="../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

Эмиссия STRD токенов происходит 3 способами:

1. 9.450.000 STRD токенов будут выпускаться равномерно по блокам. Период халвинга составляет 1 год.
2. 31М токенов приходится на пул вознаграждений. Кому и как распределять эти награды определяет Stride DAO. Однако для того, чтобы сделать распределение токенов более предсказуемым, установлены определенные квоты – в первый год должно быть распределено 20М токенов, а остальные в последующие года.
3. 16.7М токенов предназначены для партнеров Stride и 24.2М токенов для ключевых контрибьюторов. Период лока составляет один год, с последующим линейным разлоком в течение двух лет. Токены, находящие в вестинге, застейканы для улучшения безопасности сети, но на них не начисляются награды за стейкинг.

Более подробно с распределением STRD токенов можно ознакомиться [тут](https://stride.zone/blog/stride-tokenomics) и [тут](https://stride.zone/blog/strd-tokenomics-updates-and-clarifications).

STRD токен выполняет как гавернанс, так и утилити функцию. Как упоминалось выше, 10% от наград за ликвидный стейкинг отходит протоколу. Изначально все эти награды будут поступать Stride Foundation. Однако, в будущем холдеры ST могут проголосовать за любое другое распределение этих наград. Также холдеры ST путем голосования принимают ключенвые решения такие, как выбор сета валидаторов, распределение “веса” этих валидаторов, распределение наград, управление фондами пулов сообщества, добавление новых функций в протокол и т.д.

{% hint style="info" %}
В конце января пользователи проголосовали, что 100% от комиссии за использовании площадки будет идти в качестве наград холдерам STRD.
{% endhint %}

## **Ссылки**

1\.       Официальный сайт Stride: [https://stride.zone](https://stride.zone)

2\.       Документация: [https://docs.stride.zone/docs](https://docs.stride.zone/docs)

3\.       Блог: [https://stride.zone/blog](https://stride.zone/blog)

4\.       Твиттер: [https://twitter.com/stride\_zone](https://twitter.com/stride\_zone)

5\.       Дискорд: [https://discord.com/invite/e4bzG6zNdf](https://discord.com/invite/e4bzG6zNdf)
