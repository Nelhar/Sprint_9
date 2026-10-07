
# Описание проектной работы 9 спринта — Яндекс Практикум

Спринт 9/9: Спринт 9. 28.09 - 11.10 ЖД 🔴 → Тема 2/2: Итоговый проект → Урок 2/6

# Описание проектной работы 9 спринта

**🔍 Обратите внимание:** вам не нужно выполнять эти задания прямо сейчас.

В конце спринта будет ещё один урок с проектной работой. Там мы повторим описание заданий, а ещё дадим форму, куда нужно отправить ваши решения.

Мы предлагаем вам посмотреть на задания заранее, чтобы вы могли распланировать своё время. Однако делать это необязательно. Если вы хотите сначала изучить теорию, пропустите этот урок и переходите к следующему.

В итоговом спринте вы будете работать над кейсом компании Africa Delivery.

Крупный инвестор хочет реализовать маркетплейс в одной из стран Африки, то есть на рынке, где подобного еще нет. Реклама уже запущена. Открытие намечено через два месяца. Средств на реализацию немного, но запуститься нужно точно в срок. При этом даётся полный карт-бланш.

Документации нет — есть только нескольких писем от стейкхоледров. Технологическую историю создания и внедрения платформы предстоит выстроить с нуля от выяснения требований до работающего продукта.

Africa Delivery — цифровая платформа, которая выступает посредником между покупателем и продавцом для совершения коммерческих сделок.

Планируется разработать мультикатегорийный маркетплейс с широким ассортиментом (от одежды до электроники), собственной логистической сетью пунктов выдачи и самостоятельной регистрацией продавцов без сложного онбординга.

Ставка делается на низкую цену и объём продаж, а не на маржинальность отдельной сделки.

Команды пока нет. Есть только инвестор, нанятый CEO, CFO, CTO и вы — специалист в области архитектурных решений. Продуктовую команду предстоит ещё собрать. Был также привлечённый менеджер продукта, но он уволился, не выдержав прессинга инвестора.

Инвестор придерживается жёсткой и требовательной позиции в работе и нередко настаивает на собственных решениях даже в вопросах, выходящих за пределы его компетенции. У него нет MBA, зато есть опыт реализации критически важных и государственных проектов с бюджетами от сотен миллионов долларов и серьёзные связи в госструктурах. Свободно владеет английским языком и разбирается в технических вопросах.

Требования бизнеса включают уровень доступности системы Mission Critical (99,99% времени безотказной работы, деградация недопустима), сертификацию платформы по критериям Cloud Native (CNCF) в условиях нестандартной инфраструктуры развивающегося рынка, а также возможность разместить платформу у любого из доступных compute-провайдеров (Amazon, Google, Microsoft или on-premise) с учётом географической распределённости и катастрофоустойчивости.

Целевой рынок охватывает 1,4 миллиарда человек, из которых порядка 700 миллионов — активные пользователи смартфонов. Свыше 60% трафика приходится на мобильные устройства с подключением по технологии 3G или 4G.

Среди платёжных систем доминируют M-Pesa, Flutterwave и Paystack, тогда как банковские карты используют лишь около 20%. Кроме того, для работы с платежами необходимы соответствующие лицензии, что предполагает партнёрство с лицензированным провайдером.

Местное законодательство регулирует защиту данных и требует их локализацию данных. В частности, закон NDPR в Нигерии обязывает хранить персональные данные нигерийцев локально в стране, при этом допускается режим маскирования данных. Закон POPIA в ЮАР предусматривает обязательное управление согласием пользователей, а без полученного согласия реклама запрещена. В Кении согласно KICA, интернет-провайдеры обязаны блокировать или удалять нелегальный контент по требованию государственных регуляторов. Закон также закладывает правовую основу для цифровых подписей, транзакций и защиты прав потребителей в цифровой среде.

Географические особенности рынка проявляются в отсутствии собственной ИТ-инфраструктуры, из-за чего локальные курьерские и логистические службы приходится подключать через партнёрский API. Во многих африканских деревнях нет интернета, поэтому может сложиться ситуация, при которой оформить получение заказа онлайн будет невозможно, а только через USSD или смс. Дополнительную сложность создаёт отсутствие нормальной адресной системы домов (например, в Нигерии) и удалённых районах в целом.

Продавцы представляют собой малый и средний бизнес, часть которого работает без интернета и управляет товарами через мессенджер или USSD. При этом на рынке уже присутствуют конкуренты (Jumia и Takealot), которые уже успели занять свою нишу.

## Структура компании

- CEO — нанят, ранее работал в Jumia — прямом конкуренте.
- CFO — отвечает за финансы.
- CTO — ранее занимал аналогичную позицию в логистической платформе.
- Вы — специалист в области архитектурных решений, которому предлагают стать заместителем CTO.
- Product Manager — уже уволился из Africa Delivery.
- При этом в компании нет ни одного сотрудника с локального рынка.

## Технологический стек

- Legacy-систем нет — разработка ведётся с нуля (greenfield).
- Мобильный трафик составляет 100%, сети — 3G/LTE с нестабильным покрытием и частыми перерывами в связи (в этих условиях лучше работают приложения с кешем контента внутри).
- Локальные платёжные провайдеры: Flutterwave API, M-Pesa API, Paystack.
- Логистика: Sendbox API (Нигерия) и Sendy (Кения).
- WhatsApp* Business API — канал для продавцов без личного кабинета
- У CTO сильный бэкграунд в Golang и Oracle, а также хорошее понимание логистических платформ, поэтому он часто настаивает, что писать нужно самостоятельно.

**Принадлежит компании Meta, признанной экстремистской и запрещённой на территории РФ*

## Цели бизнеса

**Через два месяца** необходимо получить промежуточное решение (MVP). Предполагается, что запустится работающий пилот маркетплейса Africa Delivery в Нигерии и Кении, а потом и в ЮАР. В рамках пилота должны быть реализованы каталог товаров на 5000 SKU от 100 продавцов, оформление заказа с оплатой через M-Pesa и Flutterwave, уведомления по смс и в мессенджерах, простой личный кабинет покупателя, а также базовая аналитика для CEO.

**Через год** ожидается, что Africa Delivery будет локализовано в пяти странах и выйдет в B2B-сегмент. К этому моменту у маркетплейса будет уже более миллиона пользователей. Планируется реализовать личный кабинет продавца с аналитикой, логистическую интеграцию с отслеживанием отправлений (track & trace), обработку возвратов и защиту от мошенничества на пунктах выдачи заказов с обязательной видеофиксацией, а также локализацию на английский, французский и местные языки.

**В долгосрочных планах (через три года)** предусмотрено расширение присутствия на 12–15 стран с целью занять 40% рынка.

# Материалы для проектной работы — Яндекс Практикум

# Материалы для проектной работы

В этом уроке представлены артефакты, которые помогут разобраться с контекстом проекта, а также шаблоны для выполнения заданий.

## Артефакты

1. Транскрипт встречи с инвестором, содержащий общие формулировки без технических деталей.
2. Маркетинговый бриф с описанием целевой аудитории и позиционирования платформы.
3. Юридическое письмо, в котором упоминается NDPR, но не раскрываются технические требования к его соблюдению.
4. Список из 29 функций без приоритизации, составленный Product Manager. Он настаивал, что все они нужны с первого дня работы маркетплейса, однако сам уже покинул Africa Delivery.
5. Письмо от CTO с требованием заложить масштабирование до десяти миллионов пользователей с первого дня и разместить всю инфраструктуру в облаке.
6. Письмо от CFO с указанием бюджета на облачную инфраструктуру (не более пяти тысяч долларов в месяц на старте).
7. Записка от инвестора.
8. Схема системы.

Africa Delivery — международный проект, поэтому вся коммуникация ведётся на английском. Артефакты для проектной представлены на двух языках: в оригинале (на английском) и в переводе (на русском).

Это все материалы, которые существуют по проекту: нет ни требований к продукту, ни архитектуры, ни бэклога, ни команды. Все восемь перечисленных артефактов написаны разными людьми, в разное время и для разных аудиторий. Их никто не сверял, не редактировал и не согласовывал между собой. Поэтому материалы могут противоречить друг другу или быть неполными. Обнаружить это — часть вашей работы.

### Структура компании

На русском языке

**К. Орлов** — инвестор и единственный акционер Africa Delivery, финансирующий проект. Жёсткий переговорщик с обширными связями в государственных структурах на трёх континентах.

**Марк Лефевр** — CEO, нанятый шесть недель назад. Ранее работал в Jumia — прямом конкуренте Africa Delivery.

**Раджеш Менон** — CTO, ранее занимавший аналогичную позицию в логистической платформе, что дало ему опыт работы со схожими техническими задачами. Имеет сильный бэкграунд в Go и Oracle и только что вернулся с конференции KubeCon + CloudNativeCon, под впечатлением от которой формирует свои технические требования к платформе.

**Анна Вебер** — CFO, отвечающая за контроль денежных потоков компании; в её полномочия входит подписание каждого счёта на сумму свыше 500 долларов.

**Том Брэдли** — Product Manager, работавший над проектом до 4 августа 2026 года. Он уволился, не выдержав давления со стороны инвестора. После него остался список функций.

**София Алмейда** — руководитель маркетинга. Рекламная кампания уже забронирована и оплачена.

**Адаезе Нвосу** — внешний юрист из Лагоса, автор юридического письма, представленного в Артефакте 3. Работает по почасовой ставке.

Вы — специалист в области архитектурных решений, приступивший к работе над проектом 12 августа 2026 года. Помимо основной роли, вам также поступило предложение стать заместителем CTO.

На английском языке

**K. Orlov** — Investor, sole shareholder. Funds the project. Hard driver. Deep government network across three continents.

**Marc Lefèvre** — CEO. Hired six weeks ago, ex-Jumia.

**Rajesh Menon** — CTO. Ex-CTO of a logistics platform. Strong Go and Oracle background. Just back from KubeCon + CloudNativeCon.

**Anna Weber** — CFO. Controls the cash. Signs every invoice above $500.

**Tom Bradley** — Product Manager. Resigned 4 August 2026. Left behind the feature list in Artifact 4.

**Sofia Almeida** — Head of Marketing. Campaign already booked and paid for.

**Adaeze Nwosu** — External counsel, Lagos. Wrote Artifact 3. Bills by the hour.

You — Solution Architect. Started 12 August 2026. Also offered the Deputy CTO title.

### Артефакт 1. Транскрипт встречи с инвестором («кик офф» звонок)

На русском языке

**Дата:** 10 августа 2026, 21:40 EAT

**Участники:** К. Орлов (инвестор), М. Лефевр (CEO), Р. Менон (CTO), Solution Architect

**Запись:** частичная — первые восемь минут не сохранились

**ОРЛОВ:** …так что давайте не будем тратить три месяца на обследование. Я делал проекты с бюджетами больше трёхсот миллионов долларов. Государственные проекты. Критические системы. Я знаю, как это работает. Ты делаешь мне Amazon, только в Африке. Всё. Вот тебе всё техзадание.

**СПЕЦИАЛИСТ В ОБЛАСТИ АРХИТЕКТУРНЫХ РЕШЕНИЙ:** Какие именно части Amazon? У них двадцать лет разработки за…

**ОРЛОВ:** Всё. Каталог, заказы, оплата, доставка, кабинеты продавцов, приложение. Всё, из-за чего это работает. Слушай, я не собираюсь проектировать за тебя, ты архитектор. Полный карт-бланш. Просто сделай, чтобы работало.

**СПЕЦИАЛИСТ В ОБЛАСТИ АРХИТЕКТУРНЫХ РЕШЕНИЙ:** А сроки?

**ОРЛОВ:** Пятнадцатое октября. Не обсуждается. Реклама уже закуплена и оплачена, София подтвердит. Радио, билборды в Лагосе и Найроби. Человек услышит рекламу и откроет приложение. Приложение должно быть в апп сторе.

**ЛЕФЕВР:** В Jumia запуск такого масштаба занимал год

**ОРЛОВ:** Jumia — это причина, по которой мы вообще этим занимаемся. Они медленные, дорогие и убыточные. Мы возьмём сорок процентов рынка за три года. Пятнадцать стран.

**СПЕЦИАЛИСТ В ОБЛАСТИ АРХИТЕКТУРНЫХ РЕШЕНИЙ:** 15 стран за три года, начиная с Нигерии и Кении?

**ОРЛОВ:** Нигерия, Кения, потом ЮАР. Потом всё остальное. Лицензии — не твоя забота, у меня есть отношения. В Нигерии я решаю это одним звонком. У меня там друзья в министерстве торговли.

**СПЕЦИАЛИСТ В ОБЛАСТИ АРХИТЕКТУРНЫХ РЕШЕНИЙ:** Я бы хотел поговорить с продавцами, прежде чем проектировать кабинет продавца. Хотя бы с десятью-пятнадцатью в Лагосе…

**ОРЛОВ:** Зачем? Что они тебе расскажут такого, чего я не знаю? Они хотят продавать. Они хотят деньги на счёт сегодня, а не через тридцать дней. Вот это и построй.

**МЕНОН:** С точки зрения платформы, я бы сказал микросервисы с первого дня, мы не можем загонять себя в…

**ОРЛОВ:** Раджеш, сами договоритесь. Технологии — твоя зона. Но я скажу, чего я не хочу. Я не хочу слышать «оно лежит». Никогда. Эта система не падает. Одна минута простоя во время распродажи — это двенадцать тысяч долларов выручки. Я посчитал.

**СПЕЦИАЛИСТ В ОБЛАСТИ АРХИТЕКТУРНЫХ РЕШЕНИЙ::** Двенадцать тысяч в минуту подразумевают определённый уровень вложений в резервирование. Это стоит денег…

**ОРЛОВ:** Денег мало. Очень мало. Анна покажет тебе цифры, с Анной не спорь. Но работать должно. Оба утверждения верны. Именно поэтому здесь ты, а не кто-то подешевле.

**СПЕЦИАЛИСТ В ОБЛАСТИ АРХИТЕКТУРНЫХ РЕШЕНИЙ:** Понял. По продукту Том оставил список функций. Примерно 30 пунктов. Считать его скоупом?

**ОРЛОВ:** Том ушёл, потому что не выдержал давления. Забудь про него. Хотя список неплохой. Прочитай. Часть вещей там — правильное чутьё.

**ЛЕФЕВР:** Нам нужно чётко разделить, что входит в первый релиз, а что нет.

**ОРЛОВ:** Всё, к чему прикасается покупатель, входит в первый релиз. Бэк-офис подождёт.

**МЕНОН:** А блокчейн, который мы обсуждали?

**ОРЛОВ:** Да — у моего друга в Дубае токенная программа лояльности, у него отлично работает. Изучите. Не к октябрю, но изучите.

**СПЕЦИАЛИСТ В ОБЛАСТИ АРХИТЕКТУРНЫХ РЕШЕНИЙ:** Можно спросить, что для вас значит «работает» 16 октября? Что заставит вас сказать, что запуск удался?

**ОРЛОВ:** [пауза] Люди покупают. Продавцы получают деньги. Ничего не ломается. И мне не звонит министр с вопросом, почему нигерийские данные лежат на сервере во Франкфурте.

**СПЕЦИАЛИСТ В ОБЛАСТИ АРХИТЕКТУРНЫХ РЕШЕНИЙ:** К последнему пункту я бы хотел вернуться отдельно.

**ОРЛОВ:** Возвращайся с решением, а не с проблемой. В четверг я улетаю. Пришли мне одну страницу.

На английском языке

**Date:** 10 August 2026, 21:40 EAT

**Attendees:** K. Orlov (investor), M. Lefèvre (CEO), R. Menon (CTO), Solution Architect (you)

**Recording:** partial — the first eight minutes were not captured

**ORLOV:** …so let's not spend three months on discovery. I have done projects with budgets over three hundred million dollars. State projects. Critical systems. I know how this works. You build me Amazon, but in Africa. That's it. That's the whole brief.

**ARCHITECT:** Which parts of Amazon specifically? They have 20 years of…

**ORLOV:** All of it. Catalogue, orders, payments, delivery, seller accounts, the app. Everything that makes it work. Look, I'm not going to design it for you, you're the architect. Full carte blanche. Just make it work.

**ARCHITECT:** And the timeline?

**ORLOV:** 15 October. Non-negotiable. The advertising is already booked and paid, Sofia can confirm. Radio, billboards in Lagos and Nairobi. When people hear the ad they will open the app. The app has to be there.

**LEFÈVRE:** At Jumia a launch like this took us one year.

**ORLOV:** Jumia is why we're doing this. They're slow, they're expensive, they lose money. We will take forty percent of the market in three years. 15 countries.

**ARCHITECT:** 15 countries in three years, starting with Nigeria and Kenya?

**ORLOV:** Nigeria, Kenya, then South Africa. Then everything. Licences are not your problem, I have the relationships. In Nigeria I can make one phone call. [inaudible] …ministry.

**ARCHITECT:** I'd like to talk to a few sellers before we design the seller experience. Maybe ten or fifteen in Lagos

**ORLOV:** Why? What will they tell you that I don't know? They want to sell. They want money in their account today, not in thirty days. Build that.

**MENON:** From a platform perspective I'd say microservices from day one, we can't paint ourselves into

**ORLOV:** Rajesh, whatever you two agree. Technology is your area. But I'll tell you what I don't want. I don't want to hear "it's down". Ever. This system does not go down. One minute of downtime during a sale is twelve thousand dollars of revenue. I've done the arithmetic.

**ARCHITECT:** Twelve thousand a minute implies a certain level of investment in redundancy. That has a cost

**ORLOV:** Money is tight. Very tight. Anna will show you the numbers, don't argue with Anna. But it has to work. Both things are true. That's why you're here and not somebody cheaper.

**ARCHITECT:** Understood. On the product side Tom left a feature list. About 30 items. Should I treat that as the scope?

**ORLOV:** Tom left because he couldn't take pressure. Ignore him. Although the list is not bad. Read it. Some of it is the right instinct.

**LEFÈVRE:** We should be clear about what's in the first release versus later.

**ORLOV:** Everything a customer touches is in the first release. The back office can wait.

**MENON:** And the blockchain piece we discussed?

**ORLOV:** Yes, my friend in Dubai runs a token loyalty programme, it works very well for him. Look into it. Not for October, but look into it.

**ARCHITECT:** Can I ask what "working" means to you on October 16? What would make you say the launch succeeded?

**ORLOV:** [pause] People buy things. Sellers get paid. Nothing breaks. And I don't get a call from a minister asking why Nigerian data is sitting on a server in Frankfurt.

**ARCHITECT:** That last one I'd like to come back to.

**ORLOV:** Come back to it with a solution, not with a problem. I'm on a plane Thursday. Send me one page.

### Артефакт 2. Маркетинговый бриф

На русском языке

**От:** София Алмейда, Head of Marketing

**Кому:** Продукт и разработка

**Дата:** 6 августа 2026

**Тема:** Africa Delivery — позиционирование и бриф на запуск (ФИНАЛ — медиа уже выкуплены)

**Кампания стартует 15 октября.** Радио (Лагос, Ибадан, Найроби, Момбаса), наружная реклама (12 сайтов в Лагосе, 8 в Найроби), Facebook* и TikTok. Бюджет законтрактован и не возвращается: $180 000. Креативы в печати.

### Позиционирование

**«Всё, что нужно. С доставкой. В любую точку Африки».**

Мы — быстрая и надёжная альтернатива Jumia. Там, где они медленные и дорогие, мы быстрые и честные. Всё держится на доверии: африканские онлайн-покупатели уже обжигались на подделках и сорванных доставках. Каждое наше сообщение — про уверенность.

### Целевая аудитория

- **Основная:** городские и пригородные покупатели 22–40 лет, Лагос / Абуджа / Найроби / Момбаса. Смартфон в приоритете (Android, преимущественно аппараты дешевле $150). Мобильный интернет дорогой, мегабайты считают.
- **Вторичная:** мелкие продавцы и торговцы, которые сейчас продают через WhatsApp *и Instagram* и хотят больше покупателей.
- **Третичная:** сельские покупатели с кнопочными телефонами или нестабильной связью — доступны через смс и USSD. Нам говорят, что это 30–40% адресуемого рынка, и мы намерены обращаться к ним с первого дня.

**Принадлежат компании Meta, признанной экстремистской и запрещённой на территории РФ*

### Обещания, которые уже звучат в креативах

Это уже записано в радиороликах и напечатано на билбордах. Изменить нельзя.

1. «Миллион покупателей в первый месяц». (Используется в отраслевой прессе и в презентации для инвестора.)
2. «Доставка день в день в Лагосе и Найроби. В остальные точки — за 48 часов».
3. «Платите как удобно — M-Pesa, карта, банковский перевод или наличные курьеру».
4. «Бесплатный возврат 30 дней, без вопросов, деньги возвращаются мгновенно».
5. «Покупай на своём языке». Креативы идут на английском, французском, суахили, хауса и йоруба — значит, и приложение тоже.
6. «Настоящие товары, настоящие продавцы, проверено». Значок верификации есть на всех макетах.
7. «Смотри вживую». Live-стримы с покупками от блогеров каждую пятницу начиная с недели запуска. Подписаны шесть блогеров. Первый стрим 17 октября. Ожидаем 50 тысяч одновременных зрителей.

### Требования к продукту со стороны бренда

- Фотографии товаров должны выглядеть премиально — во весь экран, высокое разрешение, с зумом. Именно так мы ломаем восприятие «здесь подделки».
- Приложение должно ощущаться мгновенным. Бенчмарк нашего агентства — «меньше двух секунд до первого товара».
- Пуш-уведомление всем зарегистрированным пользователям в день запуска, плюс смс по рекламной базе (410 тысяч номеров, приобретены у партнёра).
- Таймер обратного отсчёта и механика флеш-распродаж на главном экране в неделю запуска.
- В день запуска нужен живой дашборд: регистрации, заказы, выручка, обновление раз в минуту. Инвестор будет смотреть его с телефона.

### Что нужно от разработки

Страницы в магазинах приложений должны быть опубликованы к 1 октября (за две недели до старта кампании), чтобы в креативах стояли ссылки на скачивание. Диплинки из рекламы должны открывать конкретную карточку товара.

На английском языке

**From:** Sofia Almeida, Head of Marketing

**To:** Product & Engineering

**Date:** 6 August 2026

**Subject:** Africa Delivery — launch positioning & campaign brief (FINAL — media already booked)

**Campaign is live from 15 October.** Radio (Lagos, Ibadan, Nairobi, Mombasa), outdoor billboards (12 sites Lagos, 8 sites Nairobi), Facebook* and TikTok. Spend committed and non-refundable: $180,000. Creative is at the printer.

### Positioning

**"Everything you need. Delivered. Anywhere in Africa.**

**"**Africa Delivery is a fast, trustworthy alternative to Jumia. Where they are slow and expensive, we are quick and fair. Trust is the whole game — African online shoppers have been burned by fake products and failed deliveries. Every message we run is about certainty.

### Target audience

- **Primary:** urban and peri-urban shoppers, 22–40, Lagos / Abuja / Nairobi / Mombasa. Smartphone-first (Android, mostly sub-$150 handsets). Data is expensive and they count megabytes.
- **Secondary:** small sellers and traders who currently sell over WhatsApp *and Instagram* and want more customers.
- **Tertiary:** rural buyers with feature phones or intermittent connectivity — reachable by SMS and USSD. We are told this is 30–40% of the addressable market and we intend to speak to them from day one.

### Promises we are making in the creative

These are already in the recorded radio spots and printed on the billboards. They cannot be changed.

1. **"One million shoppers in our first month."** (Used in trade press and the investor deck.)
2. **"Same-day delivery in Lagos and Nairobi. Anywhere else in 48 hours."**
3. Pay any way you like — M-Pesa, card, bank transfer, or cash to the courier."
4. **"Free returns for 30 days, no questions asked, money back instantly."**
5. **"Shop in your language."** Creative runs in English, French, Swahili, Hausa and Yoruba, so the app must too.
6. **"Real products, real sellers, verified."** We show a verification badge in every asset. "Watch it live." Influencer live-stream shopping events every Friday from launch week. Six influencers signed, first stream 17 October, expected 50,000 concurrent viewers.

### Experience requirements from the brand side

- Product photography must look premium — full-bleed, high-resolution, zoomable. This is how we beat the "fake goods" perception.
- The app must feel instant. Our agency benchmark is "under two seconds to first product".
- Launch-day push notification to every registered user, plus SMS to the campaign list (410,000 numbers acquired from a partner).
- Countdown timer and flash-sale mechanics on the home screen for the launch week sale.
- We need a live dashboard on launch day: registrations, orders, revenue, refreshed every minute. The investor will be watching it on his phone.

### What we need from engineering

App store listings live by **1 October** (two weeks before campaign start) so the creative can carry the download links. Deep links from the ads must open the exact product page.

**Принадлежат компании Meta, признанной экстремистской и запрещённой на территории РФ*

### Артефакт 3. Юридическое письмо

На русском языке

**Nwosu & Partners** · Адвокатское бюро · 14 Ozumba Mbadiwe Ave, Victoria Island, Лагос

**Кому:** Совету директоров Africa Delivery Holdings Ltd

**Дата:** 8 августа 2026

**Исх.:** AFRICA_DELIVERY/2026/011

**Тема:** Предварительные замечания по защите данных и лицензированию на рынках запуска

Уважаемые господа,

В ответ на ваш запрос от 30 июля излагаем предварительные замечания. Обращаем внимание, что они носят исключительно предварительный характер и не могут рассматриваться как окончательное изложение ваших обязательств.

1. **Нигерия.** Nigeria Data Protection Regulation и последующий закон устанавливают обязательства в отношении обработки персональных данных нигерийских субъектов. По нашему прочтению, персональные данные граждан Нигерии должны храниться на территории страны, а передача за рубеж допустима лишь в ограниченных случаях. Маскирование данных и схожие техники могут быть приемлемы в определённых конфигурациях. Вам также потребуется зарегистрироваться в Комиссии, назначить сотрудника по защите данных и ежегодно подавать аудиторскую отчётность. С учётом публичности ваших инвесторов рекомендуем вступить в контакт с регулятором на раннем этапе.
2. **Южная Африка.** POPIA применяется с момента начала обработки. Управление согласиями обязательно и должно быть подтверждаемым. Прямой маркетинг субъекту, не давшему согласия, запрещён и влечёт санкции. Отмечаем, что предполагаемое использование маркетинговой командой приобретённой базы телефонных номеров, исходя из изложенных нам обстоятельств, будет проблематичным в ЮАР и, вероятно, в Нигерии.
3. **Кения.** KICA и Data Protection Act 2019 устанавливают требования к регистрации и требования, близкие к локализации. Требования к данным, связанным с платежами, строже, чем к общим клиентским данным.
4. **Платежи.** Приём платежей в любой из трёх юрисдикций требует либо лицензии, либо договорных отношений с лицензированным провайдером. Получение лицензии напрямую в заявленные вами сроки нереалистично. Рекомендуем партнёрскую модель.
5. **Ответственность маркетплейса.** Ваши риски в связи с реализацией контрафакта сторонними продавцами существенно различаются в трёх странах. Осветим это отдельно.

Мы понимаем, что вашей технической команде потребуется конкретика — сроки хранения, допустимые механизмы трансграничной передачи, точный объём понятия «персональные данные» в каждом режиме и вопрос о том, подпадают ли под регулирование псевдонимизированные данные заказов. На данном этапе мы не в состоянии предоставить эту конкретику. Нам потребуется привлечь местных консультантов в Найроби и Йоханнесбурге и вернуться к вам в надлежащий срок, который мы оцениваем в четыре-шесть недель.

Считаем необходимым предостеречь от финализации технической архитектуры до получения указанного заключения.

С уважением,

Адаезе Нвосу, партнёр

*Настоящее письмо носит предварительный характер, подлежит дальнейшему уточнению и не является юридической консультацией. Nwosu & Partners не несёт ответственности за решения, принятые с опорой на него.*

На английском языке

**Nwosu & Partners** · Legal Practitioners · 14 Ozumba Mbadiwe Ave, Victoria Island, Lagos

**To:** The Board, Africa Delivery Holdings Ltd

**Date:** 8 August 2026

**Ref:** AFRICA_DELIVERY/2026/011

**Subject:** Preliminary observations on data protection and licensing across launch markets

Dear Sirs,

Further to your enquiry of 30 July, we set out below our preliminary observations. Please note these are preliminary only and should not be relied upon as a definitive statement of your obligations.

1. **Nigeria.** The Nigeria Data Protection Regulation and the subsequent Act establish obligations regarding the processing of personal data of Nigerian data subjects. Our reading is that personal data relating to Nigerian citizens should be retained within the territory, and that transfers abroad are permissible only in limited circumstances. Data masking or similar techniques may be acceptable in certain configurations. You will also need to register with the Commission, appoint a data protection officer, and file an annual audit return. We would advise engaging the regulator early given the profile of your investors.
2. **South Africa.** POPIA applies from the commencement of processing. Consent management is mandatory and must be demonstrable. Direct marketing to a data subject who has not opted in is prohibited and carries penalties. Note that the marketing team's proposed use of an acquired telephone list would, on the facts as described to us, be problematic in South Africa and likely also in Nigeria.
3. **Kenya.** KICA and the Data Protection Act 2019 impose registration and localisation-adjacent requirements. Requirements for payment-adjacent data are stricter than for general customer data.
4. **Payments.** Operating payment collection in any of the three jurisdictions requires either a licence or a contractual arrangement with a licensed provider. Obtaining a licence directly is not realistic within your stated timeframe. We recommend the partner route.
5. **Marketplace liability.** Your exposure for counterfeit goods sold by third-party sellers differs materially across the three markets. We will address this separately.

We are conscious that your engineering team will require specifics — retention periods, permissible transfer mechanisms, the precise scope of "personal data" in each regime, and whether pseudonymised order data falls within scope. We are not in a position to provide those specifics at this stage. We would need to instruct local counsel in Nairobi and Johannesburg and revert in due course, which we estimate at four to six weeks.

We would caution against finalising your technical architecture before that advice is received.

Yours faithfully,

Adaeze Nwosu, Partner

*This letter is provided on a preliminary basis, is subject to further review, and does not constitute formal legal advice. Nwosu & Partners accepts no liability for reliance placed upon it.*

### Артефакт 4. Список функций от менеджера продукта

На русском языке

**Автор:** Том Брэдли, Product Manager

**Последнее изменение:** 3 августа 2026 (за день до увольнения)

**Имя файла:**`AFRICA\_DELIVERY\_FEATURES\_v11\_FINAL\_final2.md`

*Всё, что здесь есть, нужно к запуску. Я всё это обсудил с инвестором. Ничего не выбрасывать, не поговорив с ним. — ТБ*

1. Каталог товаров, неограниченное число категорий, неограниченные атрибуты на категорию.
2. Полнотекстовый поиск с исправлением опечаток на пяти языках.
3. Голосовой поиск на суахили и хауса.
4. ИИ-рекомендации — «покупатели вроде вас также покупали».
5. Live-стримы с покупкой прямо из трансляции и живым чатом.
6. Чат покупателя с продавцом, с автоматическим переводом.
7. Оценки и отзывы с загрузкой фото и видео.
8. Онбординг продавца полностью через WhatsApp* без веб-формы.
9. Онбординг продавца через USSD для тех, у кого нет смартфона.
10. Кабинет продавца с аналитикой продаж, когортным анализом и прогнозом остатков.
11. Оплата: M-Pesa, Flutterwave, Paystack, карта, банковский перевод, наличные при получении.
12. Рассрочка на четыре платежа с собственным кредитным скорингом.
13. Мультивалютный кошелёк с балансом в приложении и переводами между пользователями.
14. Программа лояльности на криптотокенах (просьба инвестора — см. его записку)
15. «Колесо фортуны» на главном экране, награды за ежедневные заходы.
16. Флеш-распродажи с таймерами и резервированием остатков.
17. Движок динамического ценообразования, реагирующий на цены Jumia (парсинг).
18. Отслеживание заказа, живая карта курьера, ETA с точностью до минуты.
19. Доставка в пункты выдачи с видеофиксацией каждой выдачи для разбора споров.
20. Возвраты и рефанды, 30 дней, деньги возвращаются мгновенно в момент оформления возврата.
21. ML-антифрод по заказам, аккаунтам и возвратам.
22. B2B-режим: оптовые цены, коммерческие предложения, счета, отсрочка 30 дней.
23. Партнёрская и реферальная программа с учётом выплат.
24. Офлайн-заказ через USSD и смс для зон без мобильного интернета.
25. PWA и нативный iOS и нативный Android (полный паритет функций во всех трёх).
26. Административный бэк-офис: модерация каталога, KYC продавцов, разбор споров, возвраты, контент.
27. Публичный GraphQL API для партнёрских интеграций.
28. Дашборд для руководства в реальном времени (инвестор просил отдельно).
29. Тёмная тема.

**Заметки в конце файла:**

- Приоритеты: всё P0. Инвестор выразился однозначно.
- Собственный склад и фулфилмент — инвестор говорит, может быть, на второй год, но CTO хочет закладывать это уже сейчас.
- Раджеш всё время говорит, что доставку надо писать самим, а не интегрировать Sendbox/Sendy. Я был против. Оставил открытым.
- Кто-нибудь должен проверить, законна ли вообще видеофиксация в пунктах выдачи.

**Принадлежит компании Meta, признанной экстремистской и запрещённой на территории РФ*

На английском языке

**Author:** Tom Bradley, Product Manager

**Last modified:** 3 August 2026 (one day before resignation)

**File name:**`AFRICA\_DELIVERY\_FEATURES\_v11\_FINAL\_final2.md`

*Everything here is required for launch. I've discussed all of it with the investor. Do not cut anything without talking to him first. — TB*

1. Product catalogue, unlimited categories, unlimited attributes per category.
2. Full-text search with typo tolerance, in five languages.
3. Voice search in Swahili and Hausa.
4. AI recommendation engine — "customers like you also bought".
5. Live-stream shopping with in-stream purchase and live chat.
6. Buyer–seller chat, with automatic translation.
7. Ratings and reviews, with photo and video upload.
8. Seller onboarding entirely over WhatsApp*, no web form.
9. Seller onboarding over USSD for sellers without smartphones.
10. Seller dashboard with sales analytics, cohort analysis and stock forecasting.
11. Payments: M-Pesa, Flutterwave, Paystack, card, bank transfer, cash on delivery.
12. Buy-now-pay-later, four installments, in-house credit scoring.
13. Multi-currency wallet with in-app balance and peer-to-peer transfer.
14. Crypto token loyalty program (investor's request — see his note).
15. Spin-the-wheel gamification on the home screen, daily streak rewards.
16. Flash sales with countdown timers and stock reservation.
17. Dynamic pricing engine reacting to competitor prices scraped from Jumia.
18. Order tracking, live courier map, ETA to the minute.
19. Delivery to pickup points, with video recording of every handover for fraud disputes.
20. Returns and refunds, 30 days, refund issued instantly on return initiation.
21. Fraud detection ML on orders, accounts and returns.
22. B2B mode: bulk pricing, quotes, invoices, 30-day credit terms.
23. Affiliate and referral program with payout tracking.
24. Offline ordering by USSD and SMS for areas without data coverage.
25. Progressive web app and native iOS and native Android (feature parity across all three).
26. Admin back office: catalogue moderation, seller KYC, dispute handling, refunds, content.
27. Public GraphQL API for partner integrations.
28. Real-time executive dashboard (the investor asked for this specifically).
29. Dark mode.

**Notes at the bottom of the file:**

- Priorities: everything is P0 (priority). The investor was clear.
- Warehouse and own fulfillment — investor says maybe year two, but the CTO wants to design for it now.
- Rajesh keeps saying we should build the delivery and logistic platform ourselves rather than integrate Sendbox/Sendy. I disagreed. Left it open.
- Someone needs to check whether the pickup-point video recording is even legal.

**Принадлежит компании Meta, признанной экстремистской и запрещённой на территории РФ*

### Артефакт 5. Письмо от CTO

На русском языке

**От:** Rajesh Menon [r.menon@](mailto:r.menon@wbafrica.io)[africadelivery.io](http://africadelivery.io/)

**Кому:** Solution Architect

**Копия:** К. Орлов; М. Лефевр

**Дата:** 11 августа 2026, 02:14

**Тема:** Re: архитектура — мысли после KubeCon (длинно, извини)

**Вложения**: [CN чек-лист](https://code.s3.yandex.net/solution-architect/CN_check-list.docx)

Добро пожаловать. Пишу из аэропорта, только что с KubeCon + CloudNativeCon, голова кипит. Хочу, чтобы мы синхронизировались до того, как ты начнёшь рисовать квадратики.

**Целевой масштаб.** Планируем

**10 миллионов пользователей с первого дня**. Не когда-нибудь, а с первого дня. Рекламный охват огромный, и я не собираюсь быть тем CTO, у которого платформа легла в ночь запуска. Проектируем под 10M, потом отмасштабируемся вниз, если ошиблись. Компании умирают под трафиком потому что откладывали на потом масштабирование.

**Cloud native по-настоящему.** Хочу сертификацию CNCF и хочу зафиксировать это письменно (посмотри CN чек лист утащил с конференции). Конкретно:

- Kubernetes, мульти-кластер, минимум три кластера (два региона плюс один on-prem под нигерийские данные)
- Service mesh — Istio. mTLS повсюду, управление трафиком, канареечные релизы
- Kafka как хребет системы. Всё событийно, никаких синхронных вызовов между сервисами
- 40–50 сервисов в целевом состоянии. Набросал карту сервисов в самолёте, скину
- GitOps на ArgoCD, всё декларативно, никаких ручных изменений никогда
- OpenTelemetry, Prometheus, Grafana, Jaeger, Loki — весь стек, с первого дня
- Мульти-облако с самого начала. **Никакого vendor lock-in**. Ничему, что мы запускаем, не должно быть важно, где оно работает — AWS, GCP, Azure или наше железо. Совет директоров прямо сказал, что вариант on-prem должен оставаться на столе.

**Именно поэтому я не хочу managed-сервисы.** Managed Postgres, managed Kafka, managed что угодно — это тот же lock-in, только с ежемесячным счётом. Поднимаем своё в Kubernetes. Операторы сейчас зрелые, я видел три доклада ровно про это.

**База данных.** Oracle для транзакционного ядра. Я знаю, что об этом думают в комнате, но я шесть лет эксплуатировал Oracle под нагрузкой на логистической платформе и точно знаю, как он себя ведёт. Postgres для периферийных сервисов, если настаиваешь. Go для всех сервисов — здесь я не торгуюсь: полиглотный стек при такой численности команды заканчивается тем, что в три часа ночи чинить некому.

**Строим, а не покупаем.** Мне всё время говорят, что надо интегрировать Sendbox и Sendy. Я уже строил логистический движок — маршрутизация, зоны, назначение курьеров, подтверждение доставки. Шесть месяцев, четыре инженера. Мы владели бы самой защищаемой частью бизнеса, а не арендовали её. Тот же аргумент по платёжной оркестрации: агрегаторы вечно берут процент с каждой транзакции, а мы можем говорить с M-Pesa и Flutterwave напрямую.

**Доступность.** Минимум 99,99%, active-active между регионами, автоматическое переключение, никаких единых точек отказа. Мультирегион с запуска. RPO — ноль.

**По срокам** — да, я знаю, что восемь недель. Я делал агрессивные запуски. Если наймём трёх-четырёх сильных Go-разработчиков в ближайшие две недели, мы в порядке; и, честно говоря, инструментарий за последние два года ушёл так далеко, что бо́льшая часть этого — выходные за написанием YAML.

Ещё одно. Инвестор спрашивал меня про блокчейн для лояльности. Я сказал, что мы это оценим. Пожалуйста, обеспечь, чтобы это где-нибудь фигурировало в документе о видении архитектуры, чтобы потом не прилетело обратно.

Пришли мне черновик ADR до встречи в Найроби. Хочу, чтобы мы зашли туда согласованными.

Раджеш

*Отправлено с телефона*

На английском языке

**From:** Rajesh Menon [r.menon@](mailto:r.menon@wbafrica.io)[africadelivery.io](http://africadelivery.io/)

**To:** Solution Architect

**Cc:** K. Orlov; M. Lefèvre

**Date:** 11 August 2026, 02:14

**Subject:** Re: architecture — thoughts after KubeCon (long, sorry)

**Attachment**: [CN check list](https://code.s3.yandex.net/solution-architect/CN_check_list_en.docx)

Welcome aboard. I'm writing this from the airport, just came out of KubeCon + CloudNativeCon and my head is full. I want us aligned before you start drawing boxes.

**The target.** We plan for **10 million users from day one**. Not "eventually" — day one. The advertising reach is enormous and I refuse to be the CTO whose platform fell over on launch night. Design for 10M concurrent-capable, we scale down if we're wrong. Scaling up later is what kills companies.

**Cloud native, properly.** I want us CNCF-certified and I want it on the record (see attached CN check list i grab from the conference). Concretely:

- Kubernetes, multi-cluster, at least three clusters (two regions plus one on-prem for the Nigerian data)
- Service mesh — Istio. mTLS everywhere, traffic shifting, canary releases
- Kafka as the backbone. Everything event-driven, no synchronous calls between services
- 40–50 services at target state. I sketched a service map on the plane, will share
- GitOps with ArgoCD, everything declarative, no manual changes ever
- OpenTelemetry, Prometheus, Grafana, Jaeger, Loki — full stack, from day one
- Multi-cloud from the start. **No vendor lock-in.** Nothing we run should care whether it sits on AWS, GCP, Azure or our own metal. The board has been explicit that on-prem must remain an option.

**Which is why I don't want managed services.** Managed Postgres, managed Kafka, managed anything — that is lock-in with a monthly invoice attached. We run our own on Kubernetes. Operators are mature now, I saw three talks on exactly this.**Database.** Oracle for the transactional core. I know what the room thinks, but I have run Oracle at scale on a logistics platform for six years and I know exactly what it does under load. Postgres for the peripheral services if you insist.

**Golang** for all services — I'm not negotiating on language, a polyglot stack with this team size is how you end up with nobody able to fix anything at 3am.

**Build, don't buy.** I keep hearing "integrate Sendbox and Sendy". I've built a logistics engine before — routing, zones, courier assignment, proof of delivery. Six months, four engineers. We'd own the most defensible part of the business instead of renting it. Same argument for payment orchestration: the aggregators take a cut of every transaction forever, and we can talk to M-Pesa and Flutterwave directly.

**Availability.** 99.99% minimum, active-active across regions, automatic failover, no single point of failure anywhere. Multi-region from launch. RPO zero.

**On timing** — yes, I know it's eight weeks. I've done aggressive launches. If we hire three or four strong Go engineers in the next two weeks we're fine, and honestly the tooling has moved so far in the last two years that a lot of this is a weekend of YAML.

One more thing. The investor asked me about blockchain for loyalty. I told him we'd evaluate it. Please make sure it appears somewhere in the vision document so it doesn't come back at us later.

Send me your ADR draft before the Nairobi meeting. I'd like us to walk in agreeing.

Rajesh

*Sent from my phone*

### Артефакт 6. Письмо от CFO

На русском языке

**От:** Anna Weber [a.weber@africadelivery.io](mailto:a.weber@wbafrica.io)

**Кому:** Solution Architect

**Копия:** М. Лефевр

**Дата:** 11 августа 2026, 09:05

**Тема:** Реальность бюджета — прочитайте, прежде чем что-либо обещать

**Вложения**

[TCO_model_Africa_Delivery.xlsx](https://code.s3.yandex.net/solution-architect/TCO_model_Africa_Delivery.xlsx)

Здравствуйте, и поздравляю с выходом. Мне сказали, что вы будете представлять архитектуру в Найроби. Прежде чем вы это сделаете — цифры, внутри которых вам предстоит работать:

1. Инфраструктура: максимальный бюджет — пять тысяч долларов в месяц первые полгода. Сюда входит всё техническое, что создаёт регулярные расходы, — вычисления, хранение, базы данных, CDN, мониторинг и любые SaaS-инструменты. Это жёсткий потолок, а не ориентир. Если вам называли девять тысяч долларов, эта цифра из презентации для совета директоров, она включает маркетинговые технологии и аналитические лицензии и разработке недоступна.
2. Любая позиция дороже 500 долларов в месяц требует моего письменного согласования заранее, с коммерческим предложением и названной альтернативой, которую вы рассматривали.
3. Никаких годовых предоплат и многолетних обязательств. У нас девять месяцев runway. Я не стану замораживать деньги в контракте, который переживёт определённость компании. Это касается и reserved instances, и committed-use скидок, какими бы привлекательными они ни выглядели.
4. Корпоративной карты для облачных провайдеров пока нет. Мы платим по счетам с отсрочкой 45 дней. Если провайдер требует привязанную карту с автоматическим ежемесячным списанием — скажите сразу, это отдельный закупочный процесс на три недели.
5. Наём заморожен — шесть контракторов до декабря. Я видела письмо с предложением нанять «трёх-четырёх сильных Go-разработчиков в ближайшие две недели». Под это нет бюджетной строки. Если архитектура требует больше людей, чем у нас есть, — неверна архитектура, а не бюджет.
6. Стоимость приёма платежей должна оставаться ниже 2,5% от GMV, всё включено, вместе с конвертацией. Выше этого юнит-экономика при нашей марже не сходится, и мне придётся выносить вопрос на инвестора.
7. Лицензионное ПО: исходите из того, что нет. Лицензии на промышленные СУБД, коммерческий APM, всё с ценой за ядро или за хост — приходите с обоснованием и будьте готовы к отказу. Open source или сервис с помегабайтной тарификацией и небольшим ежемесячным счётом.

Что мне нужно от вас, и нужно до Найроби, а не после:

- Стоимость одного заказа — на объёмах запуска и на объёмах через 12 месяцев
- Совокупная стоимость владения на пять лет для того, что вы предложите, включая людей, которые будут это эксплуатировать, а не только счёт за инфраструктуру
- Сколько стоит ошибиться: если мы построим под десять миллионов пользователей, а придёт пятьдесят тысяч — что мы потратили зря? И обратный случай: если построим маленькое и оно взлетит, сколько стоит переделка?

Я не пытаюсь вам мешать. Я пытаюсь сделать так, чтобы на седьмом месяце мы всё ещё существовали. Запущенная платформа, которую мы не можем содержать, — это тот же результат, что и отсутствие платформы.

С уважением,

Анна Вебер, CFO

На английском языке

**From:** Anna Weber [a.weber@africadelivery](mailto:a.weber@wbafrica.io)

**To:** Solution Architect

**Cc:** M. Lefèvre

**Date:** 11 August 2026, 09:05

**Subject:** Budget reality — please read before you commit to anything

**Attachement**

[TCO_model_Africa_Delivery.xlsx](https://code.s3.yandex.net/solution-architect/TCO_model_Africa_Delivery.xlsx)

Hello, and congratulations on joining.I'm told you'll be proposing an architecture in Nairobi. Before you do, the numbers you'll be working inside:

1. Infrastructure: $5,000 per month, maximum, for the first six months. This covers everything technical that carries a recurring cost — compute, storage, databases, monitoring, and any SaaS tooling. It is a hard ceiling, not a target. If someone has quoted you $9,000, that figure is from the board deck and includes marketing technology and analytics licences; it is not available to engineering.
2. Anything above $500 per month on a single line item needs my written approval in advance, with a quote and a named alternative you considered.
3. No annual prepayments and no multi-year commitments. Our runway is nine months. I will not lock cash into a contract that outlives the company's certainty. This includes reserved instances and committed-use discounts, however attractive the discount looks.
4. No corporate card for cloud providers yet. We pay on invoice, 45-day terms. If a provider requires a card on file with automatic monthly charges, tell me now, because that's a procurement conversation and it takes three weeks.
5. Headcount is frozen at six contractors through December. I've seen an email suggesting we hire "three or four strong Go engineers in the next two weeks". There is no budget line for that. If the architecture requires more people than we have, the architecture is wrong, not the budget.
6. Payment processing costs must stay under 2.5% of GMV, all-in, including Foreign Exchange (FX). Above that the unit economics don't work at our margin and I'll have to raise it with the investor.
7. Licensed software: assume no. Enterprise database licenses, commercial APM, anything with a per-core or per-host price — bring it to me with a TCO model and expect the answer to be no. Open source or commercial service with a small monthly bill.

What I need back from you, and I need it before Nairobi meeting, not after:

- Cost per order, at launch volume and at 12-month volume
- A five-year total cost of ownership for whatever you propose, including the people to run it, not just the infrastructure invoice
- What it costs to be wrong: if we build for ten million users and get fifty thousand, what have we spent that we didn't need to? And the reverse — if we build small and it works, what does the rebuild cost?

I'm not trying to block you. I'm trying to make sure that in month seven we still exist. A launched platform we can't afford to run is the same outcome as no platform.

Best regards,

**Anna Weber**, CFO

### Артефакт 7. Записка от инвестора

На русском языке

Africa Delivery

— как Wildberries. ПРОСТО.

— 15 ОКТ. НЕ ДВИГАЕТСЯ.

— НЕ должно падать. 1 мин = $12k

— Нигерия + Кения → ЮАР → 15 стран

— 40% рынка. 3 года.

— данные остаются в стране (министр!!)

— продавцам платить В ТОТ ЖЕ ДЕНЬ

— дёшево. очень дёшево максимально дёшево

— без отговорок. мы договорились.

На английском языке

Africa Delivery

— like Wildberries. SIMPLE.

— OCT 15. NOT MOVING.

— must NOT go down. 1 min = $12k

— Nigeria + Kenya → South Africa → 15 countries

— 40% market share. 3 years.

— data stays in-country (minister!!)

— pay sellers SAME DAY

— cheap. very cheap maximally cheap

— no excuses. we agreed.

### Артефакт 8. Схема системы

Схему приложения СТО первоначально отрисовал буквально на салфетке.

Link![](Материалы-для-проектной-работы-—-Яндекс-Практикум/image_1789141537.png)

Однако позже он всё-таки передал её в более [читаемом виде](https://code.s3.yandex.net/solution-architect/Africa_Delivery.pptx).

## Шаблоны

### Шаблон 1. ТСО модель проект

[Модель TCO](https://code.s3.yandex.net/solution-architect/TCO_model_Africa_Delivery_template.xlsx)

Вы можете заполнить шаблон за 20-30 минут. Заполните только жёлтые ячейки:

- На листе «Допущения» драйверы бизнеса по годам: пользователи, заказы, средний чек, GMV (Gross Merchandize Value)
- Финансовые параметры: инфляция, рост ФОТ, ставка дисконтирования, резерв, SLO, бюджет на инфраструктуру от CFO, цена минуты простоя.

На листе «TCO» по каждой статье вводится только база за Год 1 и выбирается из выпадающего списка драйвер роста: фикс / инфляция / ФОТ / пользователи / заказы / GMV. Годы 2–5 разворачиваются автоматически через таблицу индексов — это главное упрощение, которое делает модель быстро заполняемой.

**Шесть блоков затрат:**

- Облачная инфраструктура,
- Лицензии и SaaS,
- Транзакционные расходы (комиссии M-Pesa/Flutterwave/Paystack, смс, WhatsApp*, логистика),
- Команда (ФОТ),
- Разовые затраты и комплаенс,
- Стоимость недоступности — считается из целевого SLO и $12k за минуту простоя и включается переключателем.

**Принадлежит компании Meta, признанной экстремистской и запрещённой на территории РФ*

Внизу — метрики, которые и нужны для ADR №1:

- TCO за 5 лет,
- NPV,
- стоимость на заказ,
- доля ИТ-затрат в GMV и автоматическая проверка «облако в Год 1 vs $9k/мес CFO».

**На что обратить внимание:**

- В примерных числах транзакционные расходы съедают ~68% TCO — это не ошибка, а реальность маркетплейса. Но они одинаковы для любой архитектуры, поэтому варианты сравниваются по блокам 1, 2, 4 и 6.
- Разовые статьи (комплаенс-аудит, миграция) модель по умолчанию тянет во все пять лет — в инструкции написано, что лишние годы нужно перезаписать нулём вручную. Это осознанный компромисс ради простоты.

### Шаблон 2. Failure Mode and Effects Analysis (FMEA)

[Шаблон](https://code.s3.yandex.net/solution-architect/Failure_Mode_and_Effects_Analysi.md)

### Шаблон 3. Data Residency Map

[Шаблон](https://code.s3.yandex.net/solution-architect/Data_Residency_Map.md)

Link![](Материалы-для-проектной-работы-—-Яндекс-Практикум/Ramochka_dopmaterialov_vverkh_1789323962.png)
