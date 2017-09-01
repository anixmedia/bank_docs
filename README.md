# Информация для парсера курсов отделений банка 

### Описание параметров в xml файле

```
<bank license="Номер лицензии банка" xml-version="1.0" encoding="UTF-8">
    <rates unit="Уникальный номер объекта" okato="Классификатор ОКАТО" date="Время последнего обновления курса" city="Название города" name="Название объекта" address="Полный адрес" phone="Телефон" hours="Время работы">
        <rate cur="Трехбуквенный код валюты">
            <type>Тип операции (cash|online)</type>
            <buy>59.00</buy>
            <sell>59.75</sell>
            <quantity>Количество единиц</quantity>
        </rate>
    </rates>
</bank>
```

- [license](#license)
- [unit](#unit)
- [okato](#okato)
- [date](#date)
- [city](#city)
- [name](#name)
- [address](#address)
- [phone](#phone)
- [hours](#hours)

#### license 
Номер генеральной лицензии на осуществление банковских операций, выданой Центральным Банком РФ.

`license="1481"`

#### unit 
Уникальный целочисленный номер объекта, назначается банком и необходим для соответствия двух фидов - курсов и объектов.

`unit="1"`

#### okato
Общероссийский классификатор объектов административно-территориального деления, параметр для решения спорных ситуаций, например, при совпадении названий в адресе объекта.

`okato="45297552102"`

#### date
Время последнего обновления курса.

`date="2017-08-18 13:47:16"`

#### city 
Название населенного пункта. При населении менее 100 000 человек, указывать тип населенного пункта.

`city="Москва"`

#### name 
Наименование объекта состоит из следующих частей: 
- тип объекта: Головной офис, Дополнительный офис, операционный офис, бюро, операционная касса вне кассового узла и т.д.;
- наименование: "Высотный/42",  "Томск", "Привокзальный/34", "Улан-Удэ/03";
- к какому филиалу относится: Новосибирского филиала, Санкт-Петебургского филиала №2;
- полное название банка: ПАО "Акционерный коммерческий банк «Абсолют Банк»", ПАО «Банк ВТБ»;

Исключения: Тип и наименование могут быть объединены в случае с головными офисами или филиалами - Головной офис в г. Москва, Санкт-Петебургский филиал №2.

`name="Дополнительный офис «Высотный/42» Санкт-Петебургского филиала №2 ПАО «Банк ВТБ»"`

### address
Полный адрес состоит из следующих частей:
- Страна: Россия;
- Почтовый индекс: 117485;
- Адрес: г. Москва, ул. Профсоюзная, д. 104 корпус 2.

`address="Россия, 423450, Республика Татарстан, г. Альметьевск, ул. Ленина, д. 46, помещение 2`

#### phone
Телефон отделения.

`phone="+1 (303) 499-7111 доб.4"`

#### hours
Время работы объекта составляется из следующих частей:
- тип лица: физлица, юрлица;
- день недели: пн вт ср чт пт сб вс, пн-пт;
- время работы указывается в формате 24h: 10:00-20:00, 08:00-16:00.
- перерывы: 13:00-13:15, 16:00-16:15

Примечание:
- по-умолчанию: тип лица - физлица, день недели - пн-вс, если не указано
- строгая последовательность: день(дни), время работы, перерывы, в ином случае перерыв не будет учитываться
- 00:00-00:00 - выходной
- 00:00-23:59 - круглосуточно

`hours="физлица: пн-пт 10:00-18:00 перерывы 13:00-13:30 16:00-16:30 сб 10:00-16:00 перерывы 12:00-12:30 15:00-15:00 вс выходной, юрлица пн-пт 10:00-16:00 сб-вс выходной"`

`hours="круглосуточно перерывы 13:00-13:30 18:00-18:30 23:15-00:15 04:00-04:30"`

### Файлы

* docs/rates.xml - пример XML 
* docs/rates.xsd - описания структуры XML