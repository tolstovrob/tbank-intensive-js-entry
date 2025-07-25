# Вступительный экзамен для Frontend разработчика &mdash; решение @tolstovrob

## Описание проекта

Было реализовано ванильное веб-приложение для создания резюме на основе шаблона.

## Особенности решения

Я долго думал как лучше реализовать идею и пришёл к такому: у нас будет грид, который будет содержать коробки с контентом. В грид мы будем генерировать коробки на основании информации пользователя. Таким образом система становится **масштабируемой** &mdash; по сути мы свели задачу интегрирования нового блока резюме к разработке дочернего класса и его интеграции.

При этом система стилей построена так, что мы максимально абстрагируемся от классов высокого уровня, обеспеучивая высокий уровень изоляции стилей.

### О компонентах

Реализован базовый класс компонента, методы которого перегружаются другими компонентами. Компонент коробки `Box`, который унаследован от `Component`, также является базовым для компонентов-блоков резюме (`AvatarBox`, `InfoBox`, ...). Необходимые свойства подгружаются через специальный объект `options`, который передаётся в конструктор. В нём содержится базовая информация о коробке, а также необходимая полезная нагрузка (для `AvatarBox`, например, специфично поле `src` с путём к изображению пользователя).

Для создания элементов и помещения в `Grid` используется реализация паттерна Фабричный метод (см. банду четверых), для работы со свойствами &mdash; паттерн Конфигурационный объект.
