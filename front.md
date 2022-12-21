<h1> API-сервер. Клиентская часть.

<h2> Содержание
<h4>

* Среда разработки. Что такое Vue.js?
* Как работает Vue.js
* Реализация части методов
* Результат 
* Список источников
---

<h2> Среда разработки. Что такое Vue.js?

<h4> Vue.js - JavaScript-фреймворк с открытым исходным кодом для создания 
пользовательских интерфейсов. Легко интегрируется в проекты с 
использованием других JavaScript-библиотек. Может функционировать как 
веб-фреймворк для разработки одностраничных приложений в реактивном 
стиле.
Для работы c Vue.js требуется установить также Vue CLI, Node.js, npm и 
Visual Studio Code.

В отличие от фреймворков-монолитов, Vue создан пригодным для постепенного внедрения. Его ядро в первую очередь решает задачи уровня представления (view), что упрощает интеграцию с другими библиотеками и существующими проектами. С другой стороны, Vue полностью подходит и для создания сложных одностраничных приложений (SPA, Single-Page Applications), если использовать его совместно с современными инструментами и дополнительными библиотеками.

Vue.js обрёл огромную популярность во всём мире — теперь это open-source-проект, над которым трудится множество разработчиков из разных стран.
Vue.js очень любим разработчиками. Долгое время фреймворк удерживал первое место по количеству звёзд на GitHub. Сейчас другие проекты сумели побить его достижения, но среди фреймворков он всё так же остаётся лидером.
Vue.js имеет эталонную документацию, которая зачастую приводится в качестве примера того, как в принципе нужно делать официальную доку для какого-либо инструмента. 

Что касается организации кода во Vue.js, то, безусловно, самым популярным подходом является создание однофайловых компонентов, где каждый компонент Vue.js — это самодостаточная переиспользуемая единица, отдельный файл с расширением .vue. Такой файл содержит три секции, три отделённых друг от друга элемента: template (представление), script (модель) и style (стили).Из таких компонентов — строительных блоков, содержащих представление, модель и стили, — составляются полноценные веб-приложения.



В ядре Vue.js находится система, которая позволяет декларативно отображать данные в DOM с помощью простых шаблонов:
```JavaScript
<div id="app">
  {{ message }}
</div>
var app = new Vue({
  el: '#app',
  data: {
    message: 'Привет, Vue!'
  }
})
``` 
После этого мы увидим отображение текста "Привет, Vue!".

Вот примеры некоторых зарубежных компаний, которые используют Vue.js в качестве основного фронтенд-фреймворка: GitLab, Alibaba, Nintendo, Upwork, Zoom, Sony, Grammarly, 9GAG и другие. Российский энтерпрайз тоже не отстаёт — на Vue.js используют те же Ozon и «Спортмастер».

---
<h2> Как работает Vue.js. 
<h4>После парсинга HTML-страницы браузер строит дом-дерево. Vue под 
«капотом» строит виртуальное дом-дерево, то есть накапливает количество 
изменений, которое необходимо отобразить на странице, сравнивает 
оригинальное и виртуальное дерево, а потом пачкой применяет эти 
изменения к дом-дереву. После этого мы видим обновленную страницу с 
новыми данными.

![Vue](https://sun9-west.userapi.com/sun9-39/s/v1/ig2/T8FdC3F1RvG3wOl2DhiX4nMdWMNcPwFEeKMmQFAnT9XcNKGX0ATq-jCqEWYG1CEQ7DjBgB4CfDgVk5-z6leYlWuN.jpg?size=764x406&quality=96&type=album)
рис. 1 - дом-дерево

Vue пропагандирует компонентный подход.

Поговорим об этом подробнее:
Компонентный подход позволяет избежать мешанины кода и чётко выстраивать архитектуру приложения. Любую сложную страницу всегда можно разбить на меньшие составляющие. Каждую из таких частей при выделении в компонент проще поддерживать, а при необходимости повторять разбиение внутри компонента на ещё меньшие части.
Первым заметным плюсом подобного разбиения на компоненты будет удобство в поддержке — больше не нужно держать в голове логику всего приложения, можно сосредоточиться на конкретной его части. Вносить изменения или доработки нужно будет только в одном месте. Изолированность же компонентов избавит от появления конфликтов с другими частями приложения.

![Vue](https://sun9-west.userapi.com/sun9-2/s/v1/ig2/a9KryMMb7EI7NEquGUzJU8sRfrOrGaq21dTOX5qjHsdtrYAmCg3crER-3KEarD46-PnbjHPHcUoCJzrkPznhGOSu.jpg?size=974x561&quality=96&type=album)
рис. 2 - компонентный подход 

Есть еще такое понятие, как двустороннее связывание.
Двухстороннее связывание данных vue достигается путем перехвата данных в сочетании с режимом издателя-подписчика. Если vue перехвачен, мы можем сначала взглянуть на вывод консоли объекта, определенного в данных инициализации vue.
Если коротко, его задача сделать так, чтобы данные пути были связаны с конкретной моделью, то есть если пользователь вписывает в данную среду, то данные сразу заносятся в модель.
![Vue](https://sun1.userapi.com/sun1-90/s/v1/ig2/ozuEIdkdklgwY6FxRqpCVjBZTjqFtkHRJOdpKqbriTJua72_G78CYguOMbNiAs3ATXYB9bayb7jaYmEdUsvLYJFZ.jpg?size=858x449&quality=96&type=album)
рис. 3 - двустороннее связывание

![Vue](https://sun1.userapi.com/sun1-55/s/v1/ig2/r5fvH5pH-Zrjy7-HcCRK9S_hN9tPdWrGGWnfBZjRxtlwh2lRjpMRzdnVBYgaYKSEgIkir0h4uMFn0f99c8AzDNoH.jpg?size=840x486&quality=96&type=album)
рис. 4 -двустороннее связывание

Разбиение на компоненты.

Важной концепцией Vue являются компоненты. Эта абстракция позволяет собирать большие приложения из маленьких «кусочков». Они представляют собой пригодные к повторному использованию объекты. Если подумать, почти любой интерфейс можно представить как дерево компонентов.

![Vue](https://sun9-west.userapi.com/sun9-48/s/v1/ig2/OHojRVq_arlfAf5fsa3mCOvqgoWBAKV88ntlg8_RtV913ldlnDmSXAkBNOyl6UreefTicNbFSq0CPRkHSy6dTh6i.jpg?size=974x399&quality=96&type=album)
рис. 5 - разбиение на компоненты


Во Vue компонент — это, по сути, экземпляр Vue с предустановленными опциями. Создать новый компонент во Vue просто. 
Разберем на примере: 
```JavaScript
// Определяем новый компонент под именем todo-item
Vue.component('todo-item', {
  template: '<li>Это одна задача в списке</li>'
})

var app = new Vue(...)
``` 
Теперь его можно использовать в шаблоне другого компонента:

```JavaScript
<ol>
  <!-- Создаём экземпляр компонента todo-item -->
  <todo-item></todo-item>
</ol>
``` 
Также мы можем передать текст задачи в каждый компонент с помощью v-bind:
```JavaScript
<div id="app-7">
  <ol>
    <!--
      Теперь мы можем передать каждому компоненту todo-item объект
      с информацией о задаче, который будет динамически меняться.
      Мы также определяем для каждого компонента "key",
      значение которого мы разберём далее в руководстве.
    -->
    <todo-item
      v-for="item in groceryList"
      v-bind:todo="item"
      v-bind:key="item.id"
    ></todo-item>
  </ol>
</div>
``` 

---

<h2> Реализация части методов

<h4> Создание любого приложения Vue начинается с создания нового экземпляра приложения с помощью функции createApp:


```JavaScript
import { createApp } from 'vue'
import App from './App.vue'

createApp(App).mount('#app')
``` 
В файле App.vue мы указываем наши методы и компоненты: 

```JavaScript
export default {
  name: 'App',
  components: {
    InputData,
    OutputData,
    PreloadData,
    PostloadData,
    ContractilityData
  },

  methods: {
    newCalc(newCalculation) {
      console.log(newCalculation)
      

    const requestOptions = {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify(newCalculation)
    };
    fetch("http://localhost:5000/calculator/calc/new", requestOptions)
      .then(response => response.json())
      .then(data => (this.postId = data.id));
    }
  }
}
``` 
В самих компонентах (всего их у нас 5) также прописываем метод. 
Разберем на примере метода Output. 
```JavaScript
export default {

    data(){
        return {
            height: '', 
            weight: '',
            ppt: '',
            sv: '',
            chss: '',
            dzla: '',
            adsr: '',
            lasr: '',
            cvd: '',
            kdo: ''
        }
    },

    methods: {
        onSubmit() {
            if(this.height.trim() || this.weight.trim() ||this.ppt.trim()
                 || this.sv.trim() || this.chss.trim() || this.dzla.trim()
                 || this.adsr.trim() || this.lasr.trim() || this.cvd.trim() 
                 || this.kdo.trim()) {
                    const outputCalc = {
                        userId:1,
                        height: this.height,
                        weight: this.weight,
                        ppt: this.ppt,
                        sv: this.sv,
                        chss: this.chss,
                    }
                    this.$emit('output-calc', outputCalc)
                    this.height = ''
                    this.weight = ''
                    this.ppt = ''
                    this.sv = ''
                    this.chss = ''
                 }
        }
    }
}
``` 
---
<h2> Результат 

<h4> В результате работы работы, получаем приложение. 

![Vue](https://psv4.userapi.com/c235131/u362614713/docs/d28/f25f19d87df3/1.jpg?extra=y216M4sdZHs15ZD00aIlJuIZ9s3nTYxbQoLCloJaSbdrGggMu9y2lSxhiS2HydaxE6kTJYuRUIzQW68b6AC7rMVYJkXa_kTdPKthw4uneYbELCqKY6sdlggs3mF3L9-XXPy0u7geVzDvDGTHWUR00-bh)
рис. 1 - консоль с данными после вычислений. Ответ сервера. 

![Vue](https://sun9-west.userapi.com/sun9-15/s/v1/ig2/56uGCZ20F1wVbQ-0c6EPVGqjGexZwZafZ9mqP4by-bygCSMCMC0q6uAHOWVZrHqt72oZ5TkNfRUwKYJFsaQt_tED.jpg?size=1280x576&quality=95&type=album)
рис. 2 - окна для ввода данных с единицами измерения


---

<h2> Список источников

<h4>

1. Дронов, В. JavaScript в Web-дизайне / В. Дронов. - М.: БХВ-          Петербург, 2017. - 880 c.

2. «Vue 3 фундаментальный курс от А до Я» - [видеозапись] // YouTube.         Режим доступа: https://www.youtube.com/watch?v=XzLuMtDelGk&t=4s 

6.   «Vue JS быстрый курс за 50 минут» - [видеозапись] // YouTube. Режим      доступа: https://www.youtube.com/watch?v=OlnwgS-gk8Y&t=2s 