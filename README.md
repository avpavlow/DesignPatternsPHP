# Краткое описание паттернов. Выведено в ходе наблюдения кода самостоятельно

## Порождающий паттерн
1. **Абстрактная фабрика**
     - Цель: Создание системы взаимосвязанных объектов, не привязываясь к конкретным классам создаваемых объектов
     - Реализация: Создается  интерфейс фабрики, где имеются методы создания типов объектов. На основе интерфейса
    фабрики создаются объекты фабрики, в которых методы умеют создавать связанные объекты для себя. Таким образом, чтобы создать всю
    систему взаимосвязанных объектов необходимо создать правильную фабрику.

2. **Строитель**
    - Цель: Нужен общий интерфейс для создания частей объектов, читабельный
    - Реализация: Создается интерфейс с методами создания каждой части объекта. На основе этого интерфейса создается объект,
    реализующий каждый из перечисленных методов. Частью данного паттерна является `Директор`(`Менеджер`), которому передается
    готовый объект-строитель через указатель-интерфейс. И он строит ныжные вещи в зависимости от переданного объекта-строителя
    
3. **Фабричный метод**
    - Цель: Нужно создать фабрику, для которой в подтипах будут уточнения и разная реализация
    - Реализация: Создается интерфейс фабрики, в котором имеется методы создания объекта. Создаются подклассы, в которых 
    меняется тип создаваемого объекта
  
4. **Пулл-объектов**
    - Цель: В связи с тем, что долго и ресурсоемко создавать новые объекты необходимо держать объекты созданными
    и нужно обращаться к ним по мере необходимости. Уничтожать и заново создавать эти объекты ресурсоемко.
    - Реализация: Создается объект, содержащий коллекции объектов. Имеются методы установки и получения объектов
    из коллекции по ключу, например, хэш-объектов   

5. **Прототип**
    - Цель: В связи с тем, что долго и ресурсоемко создавать новые объекты, нужно создавать прототип и клонировать его
    - Реализация: В базовом классе и его подтипах должен быть метод клонирования, а также установки аттрибутов. 
    Создаем сначала прототип объекта, а потом клонируем его и меняем аттрибут


    
## Структурные паттерны

1. **Адаптер**
     - Цель: Объект который имеет требуемые данные и поведение должен итметь тот же интерфейс, базовый класс, что и другой
     объект
     - Реализация: Создается новый объект, который реализует интерфейс, наследуется от необходимого базового класса, а в
     составе имеет адаптируемый объект. Все запросы в таком новом объекте идут на адаптируемый объект в своей структуре
     
2. **Мост**
    - Цель: Отделить слой абстракции от слоя реализации (Не нужно путать с интерфнйсами и абстрактным классами)
    - Реализация:  
        - Объект разделяется на 2 объекта, один из которых реализует слой абстракции, другой слой реализации
    Соединяются они передачей абстрактного объекта в конструкторе или специальным методом в состав слоя реализации.
        - Можно реализовать с помощью наследования

3. **Композитный**
    - Цель: Объединить много объектов в одно целое и работать с этим как с одним объектом
    - Реализация: Делают 1 объект со встроенными массивами, коллекциями объектов. Перекликается с итераторами где нужно выполнять
    обход всех элементов коллеции
    
4. **Data mapper**
    - Цель: Установить связь, трансляцию между доменными данными и объектом в памяти БД
    - Реализация: В виде объекта, содержащего преобразующие функции полей в объекты памяти. При этом в конструктор или методы
    могут передаваться репозитории или адаптеры данных как инъекции.
    
5. **Декоратор**
    - Цель: Добавлять динамически дополнительную функциональность объектам
    - Реализация: Сделать общий интерфейс для всех объектов с общими функциями. Динамически создавать объект-декоратор и 
    передавать декорируемый объект в конструктор. Декорируемый объект будет храниться в структуре декоратора и  использоваться в
    методах декоратора
    
6. **Внедрение зависимостей**
    - Цель: Создать слабосвязанную архитектуру для лучшей тестируемости, поддержки и расширения кода
    - Реализация: В конструкторе объекта приходит объект, от которого зависим, внедряется в структуру и используется его методами 
    
7. **Фасад**
    - Цель: Уменьшить связанность с API, с большим набором сложного кода. Упростить работу со сложными системами 
    - Реализация: Создать объект, который принимает в конструкторе ссылку на сложные объекты. В фасаде-объекте используются
    возможности возможности полученных объектов и пишутся новые функции для внешнего использования
    
8. **Гладкий интерфейс**
    - Цель: Увеличить читабельность кода
    - Реализация: В объекте имеются функции, названия которых имеют читабельный вид и результат выполнения функции
    всегда возвращается ссылку на сам объект. 
    
9. **Легковес**
    - Цель: Уменьшить объем потребляемой памяти когда необходимо хранить похожие типы объектов.
    - Реализация: В объекте имеются функции "создать/получить". В методе `создать` если в коллекции имеется объект, то возвращается
    или создается, если его нету. Также в коллекции хранится наименьший объем данных с указанием типа данных, но не сами 
    объекты, занимающие большую память. Создаются объекты при запросе на получение    
      
10. **Прокси**
    - Цель: Перехватывать все обращения к какому-то конкретному объекту. Все вызовы к объекту происходят через объект-заместитель.
    - Реализация: Создаем объект, который наследует проксируемый элемент, либо получаем ссылку на объект в конструкторе.
    Интерфейс объекта-прокси и самого элемента должен совпадать. Должны быть те же реализации функций и методов
    
11. **Регистр**
    - Цель: Реализовать централизованное хранение данных, объектов
    - Реализация: Создается абстрактный класс с статическими методами для установки и получения значений. Установленные значения 
    хранятся в статической переменной. Почему в статической переменной, потому что там не уничтожается до конца выполнения скрипта.
         
         
## Поведенческие паттерны
1. **Цепочка обязанностей.** 
    - Цель: Реализовать над серией объектов с заданными типами обработку в отдельном объекте-обработчике.
    - Реализация: Создаем объект обработчика с методом вызова обработки `handle` в котором определяется как мы обрабатываем 
объекты. Делаем последовательные вызовы `handle` с параметрами-объектами из цепочки

2. **Команда.** 
    - Цель: Реализовать в объекте однообразное выполнение действий c единственным методом `execute`. Вся информация и 
    алгоритмы должны быть инкапуслированы в данном объекте  
    - Реализация: Реализуется созданием объекта, в котором имеется однообразный вызов метода `execute`. При желании в этот объект можно 
делать инъекции в конструкторе, по отношению к чему выполняется команда и куда будут складываться результаты

3. **Итератор.** 
     - Цель: Реализовать удобный обход контейнера и его элементов
     - Реализация: Создаем объект, содержащий данные в виде массива, списка. В этом объекте имеются методы для перехода к следущему или 
предыдущему элементу списка, определения существующей позиции

4. **Посредник.**
    - Цель: Описать взаимодействие объектов друг с другом
    - Реализация: Создаем объект, содержащий и управляющий вложенными объектами. При этом во вложенных объектах могут предусматриваться 
методы, связывающие друг с другом. Но управление происходит только в объекте-посреднике

5. **Снимок.**
     - Цель: Реализовать способность объектов сохранять себя и восстанавливать в предыдущее состояние
     - Реализация: Создаем объект, который содержит все данные базового объекта, но не содержит логику. Управление объектом-снимком происходит
из базового объекта.

6. **Null-объект.**
    - Цель: Использование с целью замены проверок существования объекта на объект с пустым телом реализации
    - Реализация: Создается объект с пустой реализацией но с тем же интерфейсом. Действия с данным объектом происходят также как с обычными,
просто они не приводят к результатам

7. **Наблюдатель.**
     - Цель: Выделить отношения основного и зависимого элемента
     - Реализация: Создаются 2 объекта один из которых наблюдатель, другой - обычный объект. Обычный объект содержит список объектов-наблюдателей и
и при каких-то изменениях в объекте выполняются действия над наблюдателями в виде использований методов наблюдателя

9. **Спецификация**
    - Цель: Описать требования к бизнес-объектам и затем использовать их. Описать, что и как нужно сделать
    - Реализация: Создается интерфейс объекта. На этой основе создаются объекты с такой же сигнатурой функций как в интерфейсе. 

10. **Состояние**
     - Цель: Позволять менять объектам поведение, когда меняется их статус
     - Реализация: Создается интерфейс состояния с методами для замены самого себя на объекты состояний для контекста самого объекта.
Каждый объект состояния знает о предыдущих и последущем соседнем состоянии и заменяется в контексте

11. **Стратегия**
    - Цель: Выбор алгоритма во время работы программы. 
    - Реализация:
        - Создается интерфейс с методом-коллбэком. На этой основе создаются объекты, реализующие коллбэк и используемые в контексте.
Данные объекты называются стратегиями.
        - Либо просто создается объект с алгоритмом и используется другими объектами

12. **Шаблонный метод** 
    - Цель использования: Удобный каркас, в который наследники могут подставить свои реализации
    - Реализация: Объявлем классы, подклассы, переопределяя методы

13. **Визитер**
    - Цель: Разделить сущности от алгоритмов визитера. При этом сущности сами будут выбирать и использовать алгоритм
    - Реализация: Реализуется объект-визитер, в котором описаны методы. Визитер сам не выбирает какой метод запускать. Объект использующий
визитер получает визитера в параметрах и запускает один из его методов. (Визитер много что умеет, но он бесправный. 
Когда и что запускать определяет объект использующий визитера)

## Еще паттерны
1. **EAV**
    - Цель: Динамически добавляется сущность, ее аттрибуты и значения аттрибутов(Например, для интернет-магазина товаров)
    - Реализация: Создаются сущности-аттрибуты. Создаются значения c указанием аттрибута, которые в итоге присваиваются
    массиву значений(с указанием аттрибута) сущности
   
2. **Репозиторий**
    - Цель: Имеются функции сохранения доменного объекта(модель предметной области), получения доменных объектов, 
    получение по идентификатору доменного объекта. Куда их вынести7 Это получается слой между доменным уровнем и
    слоем распределения. Правильно, репозитории.
    - Реализация: Реализуется объект содержащий объект распределения(объект для персистентности), реализующий
    переброску объекта в службы распределения, а также переброска из служб распределения в доменный объект

3. **Сервис-локатор** (иногда антипаттерн поскольку нарушает связанность приложения)
    - Цель: Создать централизованное хранение и использование 
    сервисов в приложении.
    - Реализация: Реализуется объектом, который хранит объекты сервисов в ассоциативном массиве и выдает их по запросу.
    Также может быть реализована фабрика сервисов, которая создает сервис при первом обращении и также хранит в ассоциативном
    массиве
