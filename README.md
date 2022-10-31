# Разработка игровых сервисов
Отчет по лабораторной работе #4 выполнил(а):
- Фалалеев Вадим Эдуардович
- РИ-300012

Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
| Задание 3 | * | 20 |

знак "*" - задание выполнено; знак "#" - задание не выполнено;

Работу проверили:
- к.т.н., доцент Денисов Д.В.
- к.э.н., доцент Панов М.А.
- ст. преп., Фадеев В.О.

Структура отчета

- Данные о работе: название работы, фио, группа, выполненные задания.
- Цель работы.
- Задание 1.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 2.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 3.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Выводы.

## Цель работы
подготовить разрабатываемое интерактивное приложение к сборке и публикации.

## Задание 1
### Используя видео-материалы практических работ 1-5 повторить реализацию приведенного ниже функционала:
– 1 Практическая работа «Создание анимации объектов на сцене»

– 2 Практическая работа «Создание стартовой сцены и переключение между ними»

– 3 Практическая работа «Доработка меню и функционала с остановкой игры»

– 4 Практическая работа «Добавление звукового сопровождения в игре»

– 5 Практическая работа «Добавление персонажа и сборка сцены для публикации на web-ресурсе»

Ход работы:

- Начнем создавать стартовую сцену при запуске игры. Для этого скопируем нашу сцену и эту копию переименуем в _1Scene. Теперь в _0Scene удалим объект Ground, в объекте Canvas удалим Score. Удалим с объекта Main Camera скрипт Dragon Picker, а с объекта Enemy удалим скрипт Enemy Dragon. Так же изменим значения Position, Rotation и Scale у объектов Enemy и DragonMountain, как показано на скриншотах.

![image](https://user-images.githubusercontent.com/54228342/199060292-ca896375-8697-4e9e-9001-79e477a48d70.png)
![image](https://user-images.githubusercontent.com/54228342/199060315-7b85a815-8783-414f-9f19-f6338f6b15d3.png)

- После этих действий у нас получается следующая сцена.

![image](https://user-images.githubusercontent.com/54228342/199060773-dea8c88d-1098-4bf2-8537-b7e564e5444f.png)

- Далее нужно поработать с анимацией для дракона. В папке _Animations создадим Animator Controller и назовем его DragonIDLE. Добавим в него анимацию idle01, после чего объекту Enemy заменим контроллер на только что созданный.

![image](https://user-images.githubusercontent.com/54228342/199061863-37c1340f-2aa7-4ed9-bad9-dd5c7e0d3a9d.png)

- После этого нам нужно добавить новый ассет "Painted HQ 2D Forest Medieval Background" по той же схеме, что и прошлые. Так же его загружаем в Unity и импортируем в проект.
- В папке Day из этого ассета копируем Cloud02, перемещяем копию в папку _Textures нашего проекта. Затем этот же объект перемещаем на сцену так, чтобы он оказался дочерним объектом у Canvas.
- Наверху слева нажимаем кнопку Window > Animation > Animation. Окно прикрепляем в удобную часть экрана. В самом окне нажимаем кнопку Create, создаем анимацию CloudAnimation в папке _Animations.
- В окне нажимаем Add Property > Transform > Position для того, чтобы менять позицию облака. Переместим последние два ключа на вторую минуту, а на первую изменим позицию облака и добавим ключ. Так мы создаем самую простую анимацию и облако будет летать в одну сторону и возвращаться.

![image](https://user-images.githubusercontent.com/54228342/199066941-8d6e0db9-a4c3-41ad-b1ed-cacde244d65d.png)

- Зайдем в папку с анимациями и изменим скорость анимации облака на 0.1, чтобы оно не передвигалось слишком быстро.

![image](https://user-images.githubusercontent.com/54228342/199067687-7a49e52d-2779-4706-9fa6-4183f4de2103.png)

- Последним действием первого видео является добавление компонента Rect Transform и привязка облака к верхнему правому углу, чтобы при любом разрешении оно было в одном и том же месте на экране.

![image](https://user-images.githubusercontent.com/54228342/199068583-4bd166c8-2d30-497a-9d8f-6e0d05d79328.png)

- Теперь мы можем посмотреть на результаты действий после первого видео.



## Задание 2
### Привести описание того, как происходит сборка проекта под другие платформы. Какие могут быть особенности?

Ход работы:



## Задание 3
### Добавить в меню Option возможность изменения громкости (от 0 до 100%) фоновой музыки в игре.

Ход работы:



## Выводы
