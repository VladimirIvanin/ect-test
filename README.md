# Тестовый вариант использования шаблонизатора ECT.js

```html
<div class="wrap">
  <!-- Конейнер для вывода -->
  <div class="js-output"></div>
</div>

<!-- шаблон -->
<script type="text/template" hidden id="list">

  <div class="news-list">
    <% for news_item in @news : %>
    <div class="news-item">
      <strong><%= news_item.title %></strong>
      <br />
      <small><%= news_item.date %></small>
    </div>
    <% end %>
  </div>
  
</script>
```

```js
$(function(){

  //renderer - объект ECT
  //renderer содержит root в котором хранятся id и html шаблонов
  //В нашем случае один шаблон <script type="text/template" hidden id="list">
  var renderer = ECT({ 
    root: {
      list: $('#list').html()
    }
  });

  //JSON с данными
  $data = {
    news: [
    {
      title: "новость 1",
      date: "1 апреля 2015"
    },
    {
      title: "новость 2",
      date: "2 апреля 2015"
    },
    {
      title: "новость 3",
      date: "3 апреля 2015"
    },
    ]
  };

  //Рендер шаблона в контейнер
  //Берем ранее созданный объект ECT и вызываем в нём метод рендер в который передаём id шаблона и наш JSON с данными
  $('.js-output').html(renderer.render( 'list', $data ))
});
```
