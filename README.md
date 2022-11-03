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

![Видео 31-10-2022 222536](https://user-images.githubusercontent.com/54228342/199071032-fdb81a33-174b-4822-bb9c-22074cdb0659.gif)

- Во втором видео мы продолжим делать стартовый экран и поработаем с переключением сцен.
- Начнем с показа названия игры. Создадим в Canvas объект Text, назовем его Title. В самом тексте напишем "Dragon picker". Поставим якорь на верхний левый угол и настроим положение объекта на сцене.

![image](https://user-images.githubusercontent.com/54228342/199519940-ceed23b1-953a-4859-bc09-5c53781a2f36.png)

- Создадим пустой объект и назовем его MainMenu. Создадим скрипт и дадим ему аналогичное название, после чего повесим его на пустой объект. Сам скрипт будет выглядеть следующим образом.

```c#

using UnityEngine;
using UnityEngine.SceneManagement;

public class MainMenu : MonoBehaviour
{
    public void PlayGame()
    {
        SceneManager.LoadScene(SceneManager.GetActiveScene().buildIndex + 1);
    }

    public void QuitGame()
    {
        Application.Quit();
    }
}

```

- Создадим 3 кнопки для начала игры, настроек и выхода, Сделаем их дочерними для объекта MainMenu, при этом данный объект должен находиться в Canvas. Настроим кнопкам нужные названия, текс, размер шрифта и положение на экране. Каждой кнопке присваиваем спрайт облаков из последнего ассета в Source Image компонента Image.
- Последним шагом будет настроить функционал этим кнопкам. В компоненте Button объекта PlayButton внутри окна On Click() нажимаем на +, в пустую ячейку добавляем объект MainMenu. После этого нажимаем No function > MainMenu > PlayGame(). Данная кнопка будет активировать метод PlayGame() скрипта MainMenu.

![image](https://user-images.githubusercontent.com/54228342/199526718-5830af64-bd82-4131-b9b6-a5a647e2f247.png)

- В билде проекта добавляем игровую сцену.

![image](https://user-images.githubusercontent.com/54228342/199527456-867fade3-309f-45d2-b3d4-49f82584d8f6.png)

- Теперь можно посмотреть на рабочее стартовое меню и работу кнопки.

![Видео 02-11-2022 201356](https://user-images.githubusercontent.com/54228342/199527898-e9b2ca7e-012d-4810-ab08-2e3a34fb1430.gif)

- В третьем видео мы будем дорабатывать функционал стартового меню, и сделаем возможность поставить игру на паузу и выйти на главноый экран.
- Добавим кнопке выхода из игры метод Quit() по такой же схеме, как и с кнопкой начала игры.
- Скопируем объект MainMenu, назовем его SettingMenu. В нем кнопку QuitButton переименуем в BackButton. Перепишем текст кнопки на "BACK". Удалим все прочие кнопки. В окне On Click() кнопки сделаем, как на скриншоте.

![image](https://user-images.githubusercontent.com/54228342/199531802-da4bd2de-64ef-492c-8b2f-edfac663aa2c.png)

- Для кнопки OptionButton объекта MainMenu сделаем тоже самое, но поменяем местами галочку. Объект SettingMenu изначально должен быть выключен. Для этого слева от названия объекта нужно убрать галочку.

![image](https://user-images.githubusercontent.com/54228342/199532832-1d6dcbe1-4e2b-4a08-ad56-7876085f114c.png)
![image](https://user-images.githubusercontent.com/54228342/199532903-e449117d-2133-4205-8fbc-50e32a890596.png)

- Перейдем на сцену игры, создадим скрипт Pause и поместим его на MainCamera. В скрипт запишем следующее.

```c#

using UnityEngine;
using UnityEngine.SceneManagement;

public class Pause : MonoBehaviour
{
    private bool paused = false;
    public GameObject panel;

    void Update()
    {
        if (Input.GetKeyDown(KeyCode.Space))
        {
            if (!paused)
            {
                Time.timeScale = 0;
                paused = true;
                panel.SetActive(true);
            }
            else
            {
                Time.timeScale = 1;
                paused = false;
                panel.SetActive(false);
            }
        }

        if (Input.GetKeyDown(KeyCode.Escape))
            SceneManager.LoadScene(SceneManager.GetActiveScene().buildIndex - 1);
    }
}

```

- Cоздадим текст, назовем его Pause. В самом тексте напишем "Paused". Настроим размер и цвет шрифта, а также расположение текста на экране. Добавим объекту якорь. Изначально сделаем его неактивным и добавим его в пустую ячейку последнего созданного скрипта. Данный текст будет появляться, если игра стоит на паузе.
- Теперь посмотрим на результаты работы после просмотра третьего видео.

![Видео 02-11-2022 205606](https://user-images.githubusercontent.com/54228342/199538783-35a795b5-138b-4b42-8ed7-742e93a03200.gif)

- Следующий шаг: поработаем с музыкой и звуками для игры. В первую очередь добавим, установим и импортируем новый ассет со звуками "Free Orchestral Music Pack". 
- На сцене стартового меню объекту MainCamera добавим комопнент Audio Source. Добавим аудиофайл "Aspiration Woods" в папку _AudioFiles и в этот компонент. Поставим галочки напротив Play On Awake и Loop. Такие же действия совершим в сцене самой игры, но уже с аудиофайлом "Final Struggle". После удалим папку ассета, она нам больше не понадобится.

![image](https://user-images.githubusercontent.com/54228342/199549078-7df1af5a-382e-482b-8ab2-1e421ca19145.png)

- Поработаем теперь со следующим ассетом, в котором уже будут звуковые эффекты: "Grenade Sound FX". После импорта его в проект перенесем файл Grenade2Short в папку _AudioFilesи переименуем его в DragonEggExplosion. После чего совершаем знакомые действия в префабе DragonEgg - добавляем компонент AudioSource, в него добавляем наш новый аудиофайл, и убираем галочку напротив Play On Awake.
- Зайдем в скрипт DragonEgg и добавим в него несколько строчек для работы аудиофайла.

```c#

public class DragonEgg : MonoBehaviour
{
    public static float bottomY = -30f;
    public AudioSource audioSource; // new

    private void OnTriggerEnter(Collider other)
    {
        ParticleSystem ps = GetComponent<ParticleSystem>();
        var em = ps.emission;
        em.enabled = true;

        Renderer rend = GetComponent<Renderer>();
        rend.enabled = false;

        audioSource = GetComponent<AudioSource>(); // new
        audioSource.Play(); // new
    }
    
    ...

```

- Возьмем из ассета файл Impact on Snow, переименуем его в DragonEggImpact, перенесем его в папку с нашими аудифайлами. Сделаем все по такой же схеме, как и с прошлым аудиофайлом, но теперь в префабе EnergyShield. В скрипт EnergyShield добавим некоторые строчки кода.

```c#

public class EnergyShield : MonoBehaviour
{
    public TextMeshProUGUI scoreGT;
    public AudioSource audioSource; // new
    
    ...
    
    private void OnCollisionEnter(Collision collision)
    {
        GameObject collided = collision.gameObject;
        if (collided.tag == "Dragon Egg")
            Destroy(collided);

        int score = int.Parse(scoreGT.text);
        score += 1;
        scoreGT.text = score.ToString();

        audioSource = GetComponent<AudioSource>(); // new
        audioSource.Play(); // new
    }
}

```

- Теперь можем проверить, что все звуки и музыка работают на каждой сцене.

https://user-images.githubusercontent.com/54228342/199641735-81fa0051-391d-4ff8-b399-3644e1adfc3e.mp4

- 

## Задание 2
### Привести описание того, как происходит сборка проекта под другие платформы. Какие могут быть особенности?

Ход работы:



## Задание 3
### Добавить в меню Option возможность изменения громкости (от 0 до 100%) фоновой музыки в игре.

Ход работы:



## Выводы
