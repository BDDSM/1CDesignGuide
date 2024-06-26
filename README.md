# Гайд для создания форм на 1С

**Идея:**

1. Создать гайд по интерфейсу для приложения 1С
2. В гайде планирую показать основные элементы и когда и как их использовать
3. Стоит подготовить примеры и антипримеры форм

**Что уже есть:**

1. Стандарты по оформлению форм - <https://its.1c.ru/db/v8std#browse:13:-1:11>
2. Maker - <https://1cmaker.com/>
3. Хитрости и советы по созданию форм - <https://rarus.ru/publications/20220530-ot-ekspertov-hitrosti-po-sozdaniyu-form-1c-532555/>
4. Контур.Гайды - <https://guides.kontur.ru/>
5. Алан Купер об интерфейсе. Основы проектирования взаимодействия

Возможно, что-то есть еще, но быстрым поиском не нашел.

- [Гайд для создания форм на 1С](#гайд-для-создания-форм-на-1с)
  - [Элементы формы](#элементы-формы)
    - [Декорация](#декорация)
    - [Группы](#группы)
      - [Обычная группа](#обычная-группа)
      - [Свертываемая группа](#свертываемая-группа)
      - [Всплывающая группа](#всплывающая-группа)
    - [Флажок](#флажок)
    - [Поле ввода](#поле-ввода)
    - [Гиперссылки](#гиперссылки)
    - [Переключатель](#переключатель)
    - [Тумблер](#тумблер)
    - [Кнопка](#кнопка)
    - [Табличная часть](#табличная-часть)
    - [Диалоговое окно](#диалоговое-окно)
  - [Компоновка формы](#компоновка-формы)
    - [Командная панель](#командная-панель)
    - [Команды формы](#команды-формы)
    - [Шапка формы](#шапка-формы)
    - [Подвал формы](#подвал-формы)
    - [Сохранение размера формы](#сохранение-размера-формы)

## Элементы формы

### Декорация

Самый простой элемент дизайна форм. Можно вывести любой текст.

<img src=img/usualLabel.png width=500>

**Использование:**

1. Декорация-надпись:

  - Может использоваться как заголовок у сложных полей.
  - Может использоваться как подсказка на форме. В этом случае часто используют Форматированную строку, чтобы добавить гиперссылки и оформление.

    <img src=img/formatString.png width=500>

2. Декорация-картинка

  - Картинка может использовать для иллюстрации или чтобы обратить внимание пользователя
  - Картинка может быть и в составе форматированной строки, и отдельным элементом.

      <img src=img/pictureLabel.png width=500>

**Неправильное использование:**

1. Не следует использовать [Декорацию](#декорация) для установки заголовки простых полей.

  В этом случае не срабатывает автофокус на поле и часто забывают поставить двоеточие в заголовке поля.
  
  <details><summary>Как выглядит В ЕДТ</summary>
      <img src=img/wrongLabel1.png width=500>
  </details>

2. Не следует использовать [Декорацию](#декорация) для выравнивания элементов. Лучше использовать для этого свойства [Групп](#группы).

### Группы

Группы используются для объединения элементов вместе. Группы позволяют управлять расположением элементов.

#### Обычная группа

1. В большинстве случае не следует отображать заголовок у группы
2. Не следует в заголовке группы писать слово "Группа" (по умолчанию платформа его добавляет - следует убрать)
3. Не следует оставлять бессмысленные подсказки в группе, так как они выводится при удержании курсора над группой (по умолчанию платформа добавляет - следует убрать)
4. Лучше избегать Расположение - Горизонтально, если возможно. Исходить следует из минимально допустимого расширения 1280х768 px
5. Типы выделения обычной группы. Сильное выделение - добавляется полоса и отступ у подчиненных реквизитов, Обычное выделение и Слабое выделение - крупный заголовок.

   <img src=img/highlightGroup.png width=500>

6. Обычное выделение имеет больший отступ вокруг себя. [Подробнее о слабом и обычном отображении групп](https://t.me/Aripovn/31)
   
   <img src=img/representationGroup.gif width=500>


**Использование:**

1. Для выравнивая элементов в подчиненных группах следует использовать свойство - **Сквозное выравнивание**. Это свойство позволяет выравнять элементы, которые находятся в подчиненных группах.

<details><summary>Как выглядит В ЕДТ</summary>

  <img src=img/endToEndAlignment.png width=500>

</details>

2. Для прижатия элементов к одному из краев следует использовать свойство - **Выравнивание элементов и заголовков**

<details><summary>Как выглядит В ЕДТ</summary>

  <img src=img/aligment.png width=500>

</details>

#### Свертываемая группа

Свертываемая группа используется, чтобы скрыть элементы - это делаем форму компактнее и удобнее для работы.
Также смотри стандарт - [Оформление групп разделов с настройками и справочниками](https://its.1c.ru/db/v8std/content/753/hdoc)

**Использование:**

1. В заголовке свертываемой группы с реквизитами следует давать описание содержашихся значений, например, см. Банковский счет и Адрес:

  <img src=img/titleOnGroup.png width=500>

В случае если в группе находятся только команды или гиперссылки (см. пример в Администрирование в БСП), то заголовок свернутой группы необязательно формировать. В этом случае мы упрощаем навигацию по форме для пользователя.

2. У свертываемой группы с реквизитами следует снять флаг "Отображать отступ слева", чтобы элементы была вровень с остальными реквизитами формы.

<details><summary>Как выглядит В ЕДТ</summary>

![Свертываемая группа](img/collapsibleGroup.png)

</details>

3. Лайфхак для программного управлением свойства группы Свернута. Управлять этим свойством программно нельзя, но можно создать две группы с одинаковыми реквизитами, одна по умолчанию свернута, а другая по умолчанию развернута. ПриСозданииНаСервере следует проверить какую группу показать пользователю.

**Неправильное использование:**

1. Не следует помещать в свертываемую группу элементы, которые требуются часто или являются обязательными.
2. Не следует размещать свертываемую группы выше обычных групп.

#### Всплывающая группа

Всплывающая группа может использоваться для размещения необязательных или справочных реквизитов, чтобы форма была компактнее.

![Всплывающая группа](img/popupGroup.png)

**Использование:**

1. Следует понимать, что для пользователя такая группа не является привычным элементом и он может пропустить ее. Поэтому следует использовать элемент с осторожностью.
2. В случае если реквизиты заполнены, то следует давать описание содержащихся значений в заголовке группы, чтобы пользователь мог посмотреть их не открывая
3. У группы следует установить Отображение управления = Картинка, чтобы появилась соответствующая пиктограмма. Это позволит пользователю узнавать поведение таких элементов.
4. Всплывающую группу можно использовать как группу с подсказкой, на которой можно разместить не только форматированную строку, но и дополнительные реквизиты. Важно в этом случае сделать говорящий заголовок, побуждающий пользователя на него нажать.

**Неправильное использование:**

1. Не следует помещать во всплывающую группу обязательные реквизиты, а также реквизиты, которые часто используются
2. Не следует экономить на заголовке у всплывающих групп. Пользователь должен понимать что ожидать при нажатии на заголовок.

### Флажок

**Использование:**

- Флажок используем для включения или выключения какой-либо опции.
- Обычно зона действия флажка небольшая и находится непосредственно рядом с самим флажком.
- У флажка заголовок устанавливаем справа. Здесь следует отойти от умолчания платформы

<details><summary>Как выглядит В ЕДТ</summary>

![Заголовок флажка](img/checkbox.png)

</details>

**Неправильное использование:**

1. Не следует использовать заголовок слева, так как это непривычно для пользователя. Здесь следует отойти от умолчания платформы.

<details><summary>Как выглядит В ЕДТ</summary>

![НеправильныйФлажок](img/wrongCheckbox.png)

</details>

### Поле ввода

1. Если в поле ввода предусмотрено удаление или пустое значение, то нужно добавить кнопку Очистки (x).
2. Для строковых полей ввода иногда следует предусмотреть кнопку выбора, например, выбор Пути к файлу или например выбор Наименования.
3. Не всегда нужно использовать заголовок поля ввода. Например, в шапке отчета мы не пишем у поля Организация заголовок, так как правило пользователи знают свою организацию и по значению могут понять что в этом поле указывает.

<details><summary>Как выглядит В ЕДТ</summary>

![Организация](img/organization.png)

</details>

В случае если заголовок не указываем, то обязательно должна быть подсказка ввода.

<details><summary>Как выглядит В ЕДТ</summary>

![Пустая организация](img/emptyOrganization.png)

</details>

То есть для Организаций в отчете следует писать: По всем организациям. Таким образом, показываем, что сейчас символизирует собой этой поле.

### Гиперссылки

Гиперссылка используется для перехода к другой форме

<img src=img/hyperlink.png width=300>

**Использование:**

1. Открытие подчиненных и служебных форм. Например, настройка НДС.
2. Гиперссылка должна иметь осмысленное название и достаточно длинным, чтобы в нее можно было нажать.

**Неправильное использование:**

1. С помощью гиперссылки не следует выполнять действия на форме. Для этого следует использовать Кнопки
2. Не следует менять цвет гиперссылки.

### Переключатель

Переключатель должен действовать на то, что находится под ним. Не следует менять что-то по переключателю, что находится над ним. Так как на форму мы смотрим сверху-вниз

### Тумблер

Тумблер выглядит как кнопки, поэтому лучше использовать его именно таким образом.
Тумблер лучше использовать для 3 или больше элементов, так как когда их 2 - не ясно какой из них нажат.

### Кнопка

1. Кнопка должна выполнять какое-то действие.
2. Допускается использовать кнопку Без фигуры для команд, которые не рекомендуется выполнять или когда кнопок слишком много.

### Табличная часть

1. В табличной части должен быть заголовок в 1 строку. При необходимости вывести сложный заголовок следует рассмотреть возможность выводить эти значения в самой таблице. Например, см. Корректировка реализации
2. В случае если табличная часть из одной колонки, то шапка не нужна. В этом случае лучше описать декорацией содержание табличной части, если это требуется.
3. В табличной части последней колонкой должна идти пустая колонка, чтобы проще было управлять шириной табличной части. У этой колонки следут отключить заголовок, включить флаг "Только просмотр" и установить "Растягивать по горизонтали".
4. Заголовок колонки табличной части следует прижимать к значению, например, для Числа следует прижимать вправо, а для Строка или Ссылка оставлять по умолчанию слева.

Еще некоторые пункты оформления описаны в стандарте для проектирования интерфейсов - https://its.1c.ru/db/v8std/content/717/hdoc

<img src=img/table.png width=800>

### Диалоговое окно

1. Кнопка по крестику в правом верхнем углу должна тоже обрабатываться. Обычно рекомендуется создать свои команды для этого окна, чтобы одна из них была Закрыть.
TODO - привести пример кода и формы.

## Компоновка формы

### Командная панель

Командную панель можно собрать самостоятельно если требуется добавить свои команды

### Команды формы

1. В модальных формах не на весь экран основная кнопка располагается справа внизу, Например, ОК.
2. В формах на весь экран основная кнопка обычно располагается слева вверху, например, Провести.

### Шапка формы

Элементы располагаем сверху вниз, слева направо.

1. Поля, которые нужно редко менять располагаем справа:
Например, поле Организация или Подразделение как правило заполняется значениями по умолчанию и не требуют внимания пользователя, поэтому располагаем их справа.
Для таких полей обязательно проверить, что они заполняются автоматически или сохраняются предыдущие значения.

2. Не следует стремится сделать левую и правую часть симметричной. Гораздо важнее чтобы слева были важные поля, а справа неважные. Вполне вероятно, что с правой стороны будет больше полей, чем с левой.

3. Необязательные поля могут скрываться по Функциональным опциям, например, Организация или Подразделение

### Подвал формы

В подвале располагается наименее важныя реквизиты. Также там может быть справочная информация в виде итогов.
В Бухгалтерии предприятия последними реквизитами обычно идут Комментарий и Ответственный.

### Сохранение размера формы

Для сохранения размера и положения окна следует испольпользовать свойство **КлючСохраненияПоложенияОкна**

Подробнее - <https://t.me/AriN1C/45>

```
&НаКлиентеНаСервереБезКонтекста 
Процедура УправлениеФормой(Форма, Шаг) 
  
 Элементы = Форма.Элементы; 
  
 Если Шаг = 1 Тогда  
   
  Элементы.ГруппаСтраницы.ТекущаяСтраница = Элементы.СтраницаВход; 
  Элементы.СтраницаВход.Видимость = Истина; 
  Элементы.СтраницаРеквизиты.Видимость = Ложь;
                Элементы.СтраницаУспешно.Видимость = Ложь; 
   
 ИначеЕсли Шаг = 2 Тогда 
   
  Элементы.ГруппаСтраницы.ТекущаяСтраница = Элементы.СтраницаРеквизиты; 
  Элементы.СтраницаВход.Видимость = Ложь; 
  Элементы.СтраницаРеквизиты.Видимость = Истина;
                Элементы.СтраницаУспешно.Видимость = Ложь; 
 Иначе 
   
  Элементы.ГруппаСтраницы.ТекущаяСтраница = Элементы.СтраницаУспешно; 
  Элементы.СтраницаВход.Видимость = Ложь; 
  Элементы.СтраницаРеквизиты.Видимость = Ложь;
                Элементы.СтраницаУспешно.Видимость = Истина; 
 
 КонецЕсли; 
 
 Форма.КлючСохраненияПоложенияОкна = СтрШаблон("СостояниеФормыШаг%", Шаг); 
  
КонецПроцедуры
```
