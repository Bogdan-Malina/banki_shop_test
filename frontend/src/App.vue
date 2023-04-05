<template lang="pug">
#app
  NavsTop(:searchContent="content")
  MainContent(:content='content')
  NavsBottom
</template>

<script>
import NavsTop from "./components/NavsTop";
import MainContent from "./components/MainContent";
import NavsBottom from "./components/NavsBottom";

export default {
  name: 'App',
  components: {
    NavsTop,
    MainContent,
    NavsBottom
  },
  data() {
    return {
      content: [
        {
          id: 1,
          img: "https://upload.wikimedia.org/wikipedia/commons/thumb/0/0b/Sandro_Botticelli_-_La_nascita_di_Venere_-_Google_Art_Project_-_edited.jpg/1024px-Sandro_Botticelli_-_La_nascita_di_Venere_-_Google_Art_Project_-_edited.jpg",
          name: "Рождение венеры",
          author: "Сандро Боттичели",
          price: 1000000,
          old_price: 2000000,
          in_stock: 1,
          desc: "«Рождение Венеры» (итал. Nascita di Venere) — картина итальянского художника тосканской школы Сандро Боттичелли. Представляет собой живопись темперой на холсте размером 172,5 × 278,5 см. В настоящее время хранится в галерее Уффици, Флоренция. "
        },
        {
          id: 2,
          img: "https://upload.wikimedia.org/wikipedia/commons/thumb/4/48/The_Last_Supper_-_Leonardo_Da_Vinci_-_High_Resolution_32x16.jpg/1024px-The_Last_Supper_-_Leonardo_Da_Vinci_-_High_Resolution_32x16.jpg",
          name: "Тайная вечеря",
          author: "Леонардо да Винчи",
          price: 3000000,
          in_stock: 1,
          desc: "«Та́йная ве́черя» (итал. Il Cenacolo или L’Ultima Cena) — монументальная роспись работы Леонардо да Винчи, изображающая сцену последней трапезы Христа со своими учениками. Создана в 1495—1498 годы в доминиканском монастыре Санта-Мария-делле-Грацие в Милане. Ранее ошибочно называлась фреской, однако было установлено, что роспись выполнена не фреской, и не «а-секко», а в особой технике, придуманной художником: яичной темперой по масляному грунту из свинцовых белил. "
        },
        {
          id: 3,
          img: "https://upload.wikimedia.org/wikipedia/commons/thumb/7/73/God2-Sistine_Chapel.png/1024px-God2-Sistine_Chapel.png",
          name: "Сотворение Адама",
          author: "Микеланджело",
          price: 5000000,
          old_price: 6000000,
          in_stock: 1,
          desc: "«Сотворение Адама» (итал. La creazione di Adamo) — фреска Микеланджело, написанная около 1511 года."
        },
        {
          id: 4,
          img: "https://upload.wikimedia.org/wikipedia/commons/thumb/4/4d/Rembrandt_-_The_Anatomy_Lesson_of_Dr_Nicolaes_Tulp.jpg/1024px-Rembrandt_-_The_Anatomy_Lesson_of_Dr_Nicolaes_Tulp.jpg",
          name: "Урок анатомии",
          author: "Рембрандт",
          price: 1000000,
          old_price: 2000000,
          in_stock: 0,
          desc: "«Урок анатомии доктора Тульпа» — картина Рембрандта, написанная в 1632 году. "
        },
        // {
        //   id: 1,
        //   img: "https://upload.wikimedia.org/wikipedia/commons/thumb/0/0b/Sandro_Botticelli_-_La_nascita_di_Venere_-_Google_Art_Project_-_edited.jpg/1024px-Sandro_Botticelli_-_La_nascita_di_Venere_-_Google_Art_Project_-_edited.jpg",
        //   name: "Рождение венеры",
        //   author: "Сандро Боттичели",
        //   price: 1000000,
        //   old_price: 2000000,
        //   in_stock: 1
        // },
      ]
    }
  },
}
</script>

<style>
@import '~bootstrap/dist/css/bootstrap.css';

#app {
  font-family: 'Merriweather', serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

h1 {
  font-style: normal;
  font-weight: 700;
  font-size: 24px;
  line-height: 150%;
}

h2 {
  font-style: normal;
  font-weight: 400;
  font-size: 18px;
  line-height: 150%;
}

h3 {
  font-style: normal;
  font-weight: 700;
  font-size: 16px;
  line-height: 150%;
}

h4 {
  font-style: normal;
  font-weight: 700;
  font-size: 16px;
  line-height: 150%;
}

h5 {
  font-style: normal;
  font-weight: 400;
  font-size: 16px;
  line-height: 150%;
}

h6 {
  font-style: normal;
  font-weight: 300;
  font-size: 16px;
  line-height: 150%;
}

.btn {
  background: #403432;
  color: white;
  padding: 14px 28px 13px;
  border-radius: 0;

  font-style: normal;
  font-weight: 700;
  font-size: 14px;
}

.btn:hover {
  background: #776763;
  color: white;
}

.btn:disabled {
  background: #C1B4B1;
  color: white;
}

.btn.in-basket {
  background: #5B3A32;
}

input {
  min-width: 300px;
  max-width: 300px;
}

.search-input {
  border-radius: 0;
  border-right: none;
  margin-top: 1px;
  margin-bottom: 1px;
  margin-right: -2px;
  font-style: normal;
  font-weight: 400;
  font-size: 14px;
  line-height: 150%;
  border-color: #E1E1E1;
}

.search-input:focus {
  border-color: #B5B5B5;
  outline: none;
  box-shadow: none;
}

footer {
  margin-top: 7px;
  background: #ECEAEA;
  min-height: 20vh;
}

header {
  max-height: 30vh;
}

.logo {
  height: 14px;
  width: 10px;
  margin-bottom: 1px;
  margin-right: 10px;
}

.hide {
  display: none;
}

</style>
