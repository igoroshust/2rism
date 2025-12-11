- background-repeat
- object-fit



1. `ctrl + shift` - выделяет несколько родственных изобржений (например, иконок). Выбираем изображение, нажимаем `ctrl + shift`, выделяем соседние элементы и эксортируем группу
![alt text](materials/image.png)

+ `ctrl + shift` позволяет выделить группу названий (текст)

2. Подключение reset.css: https://webcademy.ru/blog/739/

3. Подключение шрифтов посредством fonts.google.com, через `@import`.

4. Плагин для подключения шрифтов через IDE: google fonts.

5. Пример структуры изображений в проекте
```javascript
assets/
├── images/
│   ├── backgrounds/          # Фоновые изображения (например, bg-header.jpg)
│   ├── photos/               # Фото контента
│   │   ├── about/            # Фото для секции "about" (если специфичны)
│   │   └── products/         # Фото товаров
│   └── icons/                # Все иконки
│       ├── ui/               # Общие UI-иконки
│       ├── social/           # Иконки соцсетей
│       └── thematic/         # Тематические иконки
└── sections/                 # Файлы секций (HTML, CSS, JS)
    ├── header/               # Файлы для header
    ├── footer/               # Файлы для footer
    └── about/                # Файлы для about (без изображений)
```

7. Верстку макетов проще делать по принципу "Desktop First", поскольку проще мыслить в парадигме "От большего – к меньшему".

**Контейнер**
Для расчёта ширины контейнера при вёрстке первого раздела важно проанализировать разметку контейнера для всего макета.

Для контейнера важно оставлять отступы слева и справа, чтобы контент не прилегал к краям экрана. Это особенно актуально для мобильных устройств.

В данном случае эти поля можно увидеть, выделив область контейнера:
![alt text](image-1.png)

Можно определить расстояние таким образом:
![alt text](image-2.png)

На контейенер можно повесить функцию распределения положения элементов на странице (добавляем модификатор container--header).
```html
<header class="header">
    <div class="container container--header">
        ...
    </div>
</header>
```
```css
.container--header {
    height: 100%; /* Растяжение контейнера по всей шапке */
    display: flex;
    flex-direction: column;
    justify-content: space-between;
}

/* Для выстраивания элементов в блоке важно, чтобы в .header высота была указана в height, а не min-height  */
```

+ Не рекомендуется делать один контейнер на весь макет. Можно сделать container для шапки, отдельно для контента (main + section), и ещё один для футера.

+ Можно придерживаться стиля: секция - внутри неё контейнер - элементы. Это защищает от правок всего контейнера, когда появляются задачи вроде карусели на всю ширину экрана или блок CTA.



**Вёрстка раздела Travel Tips от ИИ**
```html
<section class="section section--travel">
  <div class="container">
    <div class="heading__wrapper">
      <h3 class="section__heading">Travel Tips and Advice</h3>
      <div class="header-btn">
        <a href="#!" role="button" class="section__button">View all</a>
        <img src="/img/icons/ui/arrow-right-line.png" alt="Arrow">
      </div>
    </div>

    <div class="section__wrapper section__wrapper--travel">
      <!-- Item 1 -->
      <article class="section__item">
        <img src="/img/travel/img.jpg" alt="East Village Ice Cream Crawl" class="section__img">
        <p class="section__title">East Village Ice Cream Crawl</p>
        <p class="section__excerpt">
          We will stop at five different world-class ice cream shops on this 1.5 mile 1.5 hour tour.
          At each ice cream store we'll explore the story behind the business and see what
          makes the ice cream unique as you savor every…
        </p>
        <div class="section__meta">
          <div class="section__meta-item">
            <img src="/img/icons/thematic/calendar-2-line.svg" alt="Date">
            <span class="section__date">Today</span>
          </div>
          <div class="section__meta-item">
            <img src="/img/icons/thematic/Group.svg" alt="Author">
            <span class="section__author">Maria Philips</span>
          </div>
          <div class="section__meta-item">
            <img src="/img/icons/thematic/comment.svg" alt="Comments">
            <span class="section__comments">2</span>
          </div>
        </div>
      </article>

      <!-- Item 2 -->
      <article class="section__item">
        <img src="/img/travel/img-1.jpg" alt="Brooklyn Bridge cinematic photo walk" class="section__img">
        <p class="section__title">Brooklyn Bridge cinematic photo walk</p>
        <p class="section__excerpt">
          This experience takes place at the Brooklyn Bridge Park and Brooklyn Bridge,
          but I’m always open to capture clients at different locations upon request for
          an additional charge.
        </p>
        <div class="section__meta">
          <div class="section__meta-item">
            <img src="/img/icons/thematic/calendar-2-line.svg" alt="Date">
            <span class="section__date">Today</span>
          </div>
          <div class="section__meta-item">
            <img src="/img/icons/thematic/Group.svg" alt="Author">
            <span class="section__author">James Calzoni</span>
          </div>
          <div class="section__meta-item">
            <img src="/img/icons/thematic/comment.svg" alt="Comments">
            <span class="section__comments">17</span>
          </div>
        </div>
      </article>
    </div>
  </div>
</section>
```

```css
/* Travel Tips */
.section--travel {
  --travel-gap: 32px;
  --meta-gap: 24px;
}

.section__wrapper--travel {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: var(--travel-gap);
  margin-top: var(--travel-gap);
}

.section__item {
  display: flex;
  flex-direction: column;
  gap: 16px;
  background-color: #fff;
  border-radius: 12px;
  overflow: hidden;
}

.section__img {
  width: 100%;
  height: 200px;
  object-fit: cover;
  border-top-left-radius: 12px;
  border-top-right-radius: 12px;
}

.section__title {
  font-size: 20px;
  font-weight: 600;
  color: #5B5B5B;
  margin: 0 16px;
  line-height: 1.4;
}

.section__excerpt {
  font-size: 16px;
  line-height: 1.6;
  color: #4A4A4A;
  margin: 0 16px 16px;
}

.section__meta {
  display: flex;
  align-items: center;
  justify-content: flex-start;
  gap: var(--meta-gap);
  padding: 0 16px 16px;
}

.section__meta-item {
  display: flex;
  align-items: center;
  gap: 4px;
}

.section__date,
.section__author,
.section__comments {
  font-size: 12px;
  color: #878787;
  white-space: nowrap;
}

/* Адаптивность */
@media (max-width: 768px) {
  .section__wrapper--travel {
    grid-template-columns: 1fr;
    gap: 24px;
  }
  
  .section__meta {
    flex-wrap: wrap;
    gap: 16px;
  }
  
  .section__meta-item {
    min-width: fit-content;
  }
}

@media (max-width: 480px) {
  .section__title {
    font-size: 18px;
  }
  
  .section__excerpt {
    font-size: 14px;
  }
  
  .section__meta {
    padding: 0 12px 12px;
  }
}

```



### Структура разделов 
**discover**
![alt text](discover-blocks.png)

**Popular**
- Стоит ли использовать article?

**Travel (мой набросок)**
![alt text](image-3.png)


### CSS-свойства
1. `background-size: cover` - это значение заставляет фоновое изображение полностью покрыть контейнер, сохраняя пропорции. 

Изображение масштабируется так, чтобы его ширина и высота полностью совпали с шириной или высотой контейнера, сохранив при этом исходные пропорции изображения. Если пропорции изображения и контейнера не совпадают, часть изображения будет обрезана.

Если изображение шире контейнера – оно растягивается по высоте, а по ширине будет растягиваться слева и справа. Если изображение выше конейнера - оно растянется по ширине, а по высоте будет обрезано.

Используем для полноэкранных фоновых изображений, когда нужно заполнить всё пространство контейнера, в слайдерах и каруселях, для эффективных "обложек" разделов сайта.

2. `background-position: center` - это значение центрирует фоновое изображение внутри контейнера.

Изображение выравнивается по центру как по горизонтали, так и по вертикали. Это эквивалентно записи `background-position: 50% 50%`. При изменении пропорций контейнера изображение становится отцентрированным.

Значение может быть в пикселях (10px 20px), процентах (25% 75%), ключевых словах (top, right, botom, left) + комбинациях ключевых слов (center top, right center) и т.д.

**Совместное использование**
Комбинация `background-size: cover` и `background-position: center` - стандартный паттерн для фоновых изображений:
```css
.element {
    background-image: url('image.jpg');
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat; /* Предотвращает повторение */
}
```
Благодаря этой комбинации, изображение заполняет весь контейнер без искажений пропорций. Изображение отцентрировано - визуально сбалансировано. Нет повторения - изображение отображается один раз. При изменении размера контейнера изображение перемасштабируется и остаётся центрированнымю

**Дополнительно**
1. Производительность. Большие изображения могут замедлять загрузку, необходимо использовать оптимизированные файлы.
2. Доступность. Фоновые изображения не видны скринридерам. Если изображение несёт смысловую нагрузку, нужно использовать `<img>` + `alt`.
3. Кросс-браузерность. Оба свойства поддерживаются всеми современными браузерами.
4. Порядок свойств. Можно объединять в `background`, но лучше писать отдельно для читаемости.

+ Добавить `background-repeat: no-repeat`, чтобы изображение не дублировалось. 
+ Использовать медиа-запросы для подгрузки различных изображений для разных устройств.
+ Рассмотреть свойство `object-fit` для `img`, если нужно аналогичное поведение для контентных изображений
+ Для сложных случаев использовать несколько фоновых изображений через запятую.


## Вопросы на проработку
- Когда лучше использовать SVG, когда - PNG и в чём отличие?
- Как рекомендуется размещать иконки - все в отдельной папке или создавать отдельную секцию внутри каждого блока?


### Соответствие размера шрифта значениям font-size
- 100 - Thin / Hairline
- 200 - Extra Light / Ultra Light
- 300 - Light
- 400 - Normal / Regular
- 500 - Medium
- 600 - Semi Bold / Demi Bold
- 700 - Bold
- 800 - Extra Bold / Ultra Bold
- 900 - Black / Heavy