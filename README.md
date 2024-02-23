# <font size = 5 color = #00FF00> <center>PROJECT-6. Segmenting customers for an online gift store</center></font> 



##  <font color = #9ACD32> Содержание </font>

[1. Введение](https://github.com/DmitVasilev/Project-6.-Segmenting-customers-for-an-online-gift-store?tab=readme-ov-file#-1-%D0%B2%D0%B2%D0%B5%D0%B4%D0%B5%D0%BD%D0%B8%D0%B5-)   
[2. Описание задачи](https://github.com/DmitVasilev/Project-6.-Segmenting-customers-for-an-online-gift-store?tab=readme-ov-file#2-%D0%BE%D0%BF%D0%B8%D1%81%D0%B0%D0%BD%D0%B8%D0%B5-%D0%B7%D0%B0%D0%B4%D0%B0%D1%87%D0%B8)   
[3. Описание данных](https://github.com/DmitVasilev/Project-6.-Segmenting-customers-for-an-online-gift-store?tab=readme-ov-file#3-%D0%BE%D0%BF%D0%B8%D1%81%D0%B0%D0%BD%D0%B8%D0%B5-%D0%B4%D0%B0%D0%BD%D0%BD%D1%8B%D1%85)   
[4. Результат](https://github.com/DmitVasilev/Project-6.-Segmenting-customers-for-an-online-gift-store?tab=readme-ov-file#4-%D1%80%D0%B5%D0%B7%D1%83%D0%BB%D1%8C%D1%82%D0%B0%D1%82)                  
[5. Выводы](https://github.com/DmitVasilev/Project-6.-Segmenting-customers-for-an-online-gift-store?tab=readme-ov-file#5-%D0%B2%D1%8B%D0%B2%D0%BE%D0%B4%D1%8B)

### <font color = #9ACD32> 1. Введение </font>

В данном проекте решается бизнес-задача в области маркетинга. Необходимо произвести сегментацию клиентов на основе их покупательской способности, частоты совершения заказов и срока давности последнего заказа, а также определить оптимальную стратегию взаимодействия с ними.


Маркетинг — неотъемлемая часть любого бизнеса. Для повышения прибыли компании важно понимать своего клиента, его пожелания и предпочтения. С появлением электронной коммерции, или онлайн-продаж, стало намного проще собирать данные о клиентах, анализировать их, находить закономерности и реализовывать маркетинговые кампании.

Большинство интернет-магазинов используют инструменты веб-аналитики, чтобы отслеживать просмотры страниц, количество и поведение посетителей и коэффициент отказов. Но отчёта из Google Analytics или аналогичной системы может быть недостаточно для полного понимания того, как клиенты взаимодействуют с сайтом. Компаниям важно иметь возможность быстро и точно реагировать на перемены в поведении клиентов, создавая инструменты, которые обнаруживают эти изменения практически в режиме реального времени.

Машинное обучение помогает поисковой системе анализировать огромное количество данных о посетителях платформы, узнавать модели поведения профессиональных покупателей, определять категорию клиентов (например, лояльные/перспективные/новички/спящие/ушедшие) и выбирать правильную стратегию взаимодействия с ними.

Стоит также отметить, что компании, использующие машинное обучение на своих платформах электронной коммерции, могут постоянно повышать эффективность бизнес-процессов: настраивать товарную выборку персонально для каждого покупателя и предлагать выгодную цену в соответствии с бюджетом клиента и т. д. Эта задача относится к категории построения рекомендательных систем.

Как правило, наборы данных для электронной коммерции являются частной собственностью и, следовательно, их трудно найти среди общедоступных данных. 

**Проект будет состоять из шести частей:**

1. *Базовый анализ и знакомство с данными*
Первая часть проекта будет посвящена знакомству с исходными данными и их структурой.

2. *Предобработка и очистка данных*
Подготовка датасета для кластеризации, очистка от пропусков, дублей, выбросов и другого «мусора».

3. *Разведывательный анализ данных (EDA)*
Исследование данных, поиск первых закономерностей и выдвижение гипотез.

4. *RFM-сегментация клиентов. Часть I*
Знакомство с очень популярным в маркетинге методом сегментации клиентов под названием RFM (Recency, Frequency, Monetary). Формирование на основе этого метода из исходного датасета о транзакциях таблицы с RFM-характеристиками клиентов и их первичная сегментация.

5. *RFM-сегментация клиентов. Часть II*
Расширение клиентских сегментов и создание промежуточных категории с помощью нелинейных преобразований размерности. Это позволит произвести более качественную кластеризацию и улучшить стратегии взаимодействия с клиентами.

6. *RFM-сегментация клиентов. Часть III*
Построение модели классификации, которая позволит автоматически определять сегмент клиента на основе нескольких транзакций.
                          
:arrow_up:[к содержанию](https://github.com/DmitVasilev/Project-6.-Segmenting-customers-for-an-online-gift-store?tab=readme-ov-file#-%D1%81%D0%BE%D0%B4%D0%B5%D1%80%D0%B6%D0%B0%D0%BD%D0%B8%D0%B5-)      

###  <font color = #9ACD32>2. Описание задачи</font>

**Бизнес-задача:** произвести сегментацию существующих клиентов, проинтерпретировать эти сегменты и определить стратегию взаимодействия с ними.

**Техническая задача:** построить модель кластеризации клиентов на основе их покупательской способности, частоты заказов и срока давности последней покупки, определить профиль каждого из кластеров.

**Основные цели проекта:**
1. Произвести предобработку набора данных.
2. Провести разведывательный анализ данных и выявить основные закономерности.
3. Сформировать категории товаров и клиентов. 
4. Построить несколько моделей машинного обучения, решающих задачу кластеризации клиентов, определить количество кластеров и проинтерпретировать их.
5. Спроектировать процесс предсказания категории интересов клиента и протестировать модель на новых клиентах. 

:arrow_up:[к содержанию](https://github.com/DmitVasilev/Project-6.-Segmenting-customers-for-an-online-gift-store?tab=readme-ov-file#-%D1%81%D0%BE%D0%B4%D0%B5%D1%80%D0%B6%D0%B0%D0%BD%D0%B8%D0%B5-)               
                                 
###  <font color = #9ACD32>3. Описание данных</font>

В проекте используется датасет, в котором содержатся данные о более чем полумиллионе транзакций. Каждая из них описывается следующими признаками:

* InvoiceNo — номер счёта-фактуры (уникальный номинальный шестизначный номер, присваиваемый каждой транзакции; буква "C" в начале кода указывает на отмену транзакции);
* Stock Code — код товара (уникальное пятизначное целое число, присваиваемое каждому отдельному товару);
* Description — название товара;
* Quantity — количество каждого товара за транзакцию; 
* InvoiceDate — дата и время выставления счёта/проведения транзакции;
* UnitPrice — цена за единицу товара в фунтах стерлингов;
* CustomerID — идентификатор клиента (уникальный пятизначный номер, однозначно присваиваемый каждому клиенту);
* Country — название страны, в которой проживает клиент.
                     
:arrow_up:[к содержанию](https://github.com/DmitVasilev/Project-6.-Segmenting-customers-for-an-online-gift-store?tab=readme-ov-file#-%D1%81%D0%BE%D0%B4%D0%B5%D1%80%D0%B6%D0%B0%D0%BD%D0%B8%D0%B5-)                    

###  <font color = #9ACD32>4. Результат</font>

Ноутбук с решением на GitHub: [project_6.ipynb](https://github.com/DmitVasilev/Project-6.-Segmenting-customers-for-an-online-gift-store/blob/ca7851879e9f1599b591a612694fb8b3bc4b5acc/Project-6.ipynb).     
 
Обеспечить воспроизводимость кода поможет файл requirements.txt: [requirements.txt](https://github.com/DmitVasilev/PROJECT-6.-Segmenting-customers-for-an-online-gift-store/blob/f218c1a4b3db44b545df9cb8876f6b026a86178f/requirements.txt). 
                        
:arrow_up:[к содержанию](https://github.com/DmitVasilev/Project-6.-Segmenting-customers-for-an-online-gift-store?tab=readme-ov-file#-%D1%81%D0%BE%D0%B4%D0%B5%D1%80%D0%B6%D0%B0%D0%BD%D0%B8%D0%B5-)              


###  <font color = #9ACD32>5. Выводы</font>

  Удалось решить задачу по сегментации клиентов на основе их покупательской способности, частоты совершения заказов и срока давности последнего заказа. Выполнено исследование данных, поиск и обработка пропущенных значений и дубликатов. Выдвинуто и проверено несколько гипотез относительно странных значений некоторых признаков. Проведена очистка данных от выявленных некорректных значений. Выполнен разведывательный анализ данных и созданны дополнительные признаки для сегментации клиентов. Созданы новые признаки с помощью метода RFM. Применены методы снижения размерности PCA (метод главных компонент) и t-SNE. Определено оптимальное число кластеров с помощью коэффициента силуэта для методов кластеризации k-means, EM-алгоритма и  алгоритма алгомеративной кластеризации. Построены оптимальные модели кластеризации и проведен анализ профилей полученных кластеров. Решена проблема непараметричности t-SNE переходом от решения задачи кластеризации к задаче классификации. Использованы ансамблевые модели (RandomForestClassifier, GradientBoostingClassifier) с подбором оптимальных параметров с помощью GridSearhCV. Получена модель, которая на основе RFM-характерик клиента автоматически определяет его сегмент со значением метрики accuracy на тестовой выборке: 0.985.
                             
:arrow_up:[к содержанию](https://github.com/DmitVasilev/Project-6.-Segmenting-customers-for-an-online-gift-store?tab=readme-ov-file#-%D1%81%D0%BE%D0%B4%D0%B5%D1%80%D0%B6%D0%B0%D0%BD%D0%B8%D0%B5-)        