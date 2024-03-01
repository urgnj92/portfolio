
<!-- HTML -->
<template>
  <div class="container">
    <header id="header">
      <transition name="fade">
        <div v-if="show">
          <h1 class="site-title">TANAKA URA<span>R</span>A</h1>
        </div>
      </transition>
      <nav class="menu">
        <ul>
          <li @click="scrollToSection('mainvisual')">Top</li>
          <li @click="scrollToSection('profile')">Profile</li>
          <li @click="scrollToSection('skills')">Skills</li>
          <li @click="scrollToSection('works')">Works</li>
          <li @click="animateItem">Contact</li>
        </ul>
      </nav>

    </header>

    <main>
      <div id="mainvisual">
        <img src="../assets/mainvisual.jpg" alt="mainvisual">
      </div>

      <div id="sub-title">
        <p>Thank you for coming to my portfolio</p>
      </div>


      <section id="profile" class="wrapper">
        <div class="image">
          <img src="../assets/prof_purple.png" alt="profile_img">
        </div>

        <div class="contents">
          <h2 class="section-title">Profile</h2>
          <p>
            1992年生まれ 茨城県出身・在住<br>
            大学卒業後、接客業、事務職を経験しIT企業に入社。<br>
            事務職の時にWebサイトのデザイン考案に携わる機会があり、「もっとこの業界のことを知りたい！自分でいろんなもの作ってみたい！」という好奇心からIT企業への転職を決意。<br>
            現在は研修期間中に学んだ言語を使って、Webサイト制作に励んでいます。Webデザイナー・フロントエンドエンジニアを目指して奮闘中。
          </p>
        </div>
      </section>

      <section id="skills" class="wrapper">
        <div class="image">
          <img src="../assets/skills_logo.png" alt="skill_icons">
        </div>

        <div class="contents">
          <h2 class="section-title">Skills</h2>
          <p>
            HTML/CSSを用いた静的サイトの作成、JavaScriptを用いた動的サイトの作成が可能です。<br>
            PHP Laravel(mySQL)を用いてCRUD機能の実装を行った経験があります。<br>
            Vue3、Photoshop、Illustlator、Adobe XDについて現在学習中です。
          </p>
        </div>
      </section>

      <section id="works" class="wrapper">
        <div class="image">
          <img src="../assets/works_1.png" alt="works">
        </div>
        <div class="contents">
          <h2 class="section-title">Works</h2>
          <h3 class="sub_title">Title</h3>
          <ul>
            <li><a href="https://urgnj92.github.io/portfolio/">TANAKA URARA PORTFOLIO</a></li>
          </ul>
          <h3 class="sub_title">Language</h3>
          <ul>
            <li>HTML, CSS, JavaScript</li>
          </ul>
          <h3 class="sub_title">Description</h3>
          <ul>
            <li>当ポートフォリオサイト。デザインとフロントの実装後、Github pagesを利用して公開。</li>
            <li>フレームワークはVue3を使用しています。</li>
          </ul>
          <p>-Other works are coming soon</p>
        </div>
      </section>

    </main>

    <footer id="footer">
      <p>&copy; 2024 Portfolio</p>
    </footer>
  </div>
</template>

<!-- JS -->
<script>
export default {
  name: 'myPortfolio',
  props: {
    msg: String,
  },
  data() {
    return {
      show: false,
    };
  },
  mounted() {
    this.show = true;
    // this.$nextTick(() => {
    //   // 横からフェードイン
    //   this.$el.style.transform = 'translateX(0)';
    // });
  },
  methods: {
    // worksのimgアニメーション処理
    animateItem(event) {
      const liElement = event.target;
      // 移動距離適宜調整
      liElement.style.transform = 'translateY(-10px)';
    },
    // スクロール時のアニメーション処理
    scrollToSection(sectionId) {
      const sectionElement = document.getElementById(sectionId);
      if (sectionElement) {
        // ヘッダーの高さを取得
        const headerHeight = document.getElementById('header').offsetHeight;
        // スクロール処理
        window.scrollTo({
          top: sectionElement.offsetTop - headerHeight,
          behavior: 'smooth',
        });
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 7s;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

html {
  scroll-behavior: smooth;
}


main {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  align-items: center; /* 中央寄せ */
}

h2 {
  display: block;
}

h3 {
  margin: 5px 0 5px 0;
}

ul {
  padding: 0;
}

li {
  margin: 0 10px;
  list-style-type: none;
}

span {
  color: #AC00BA;
}

a {
  color: #707070;
}

/* header */
#header {
  height: 120px;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  background-color: #FFF;
  padding: 10px;
  z-index: 1000;
  box-shadow: 3px 5px 3px #EAE7E7;
}

#header .menu ul {
  display: flex;
  color: #707070;
}

#header .menu li {
  border-bottom: dotted #AC00BA;
  text-align: center;
}


/* main visual */
#mainvisual {
  margin-top: 160px;
  margin-bottom: 10px;
}

#mainvisual img {
  width: 1200px;
  height: 550px;
  object-fit: cover;
  /* padding-top: 50px; */
}

#sub-title {
  width: 100%;
}

#sub-title p {
  text-align: center;
  color: #fff;
  background-color: #CC83D1
}


#works .image {
  padding-top: 30px;
}

#works .image img {
  border: 2px solid #CC83D1;
}

#works .contents p {
  text-align: right;
  padding-top: 10px;
}

/* footer */
#footer {
  color: #707070;
  text-align: center;
  /* width: 100%; */
}

.menu li {
  transition: transform 0.3s ease-in-out;
  cursor: pointer;
}

.menu li:hover {
  transform: translateY(-5px);
}


.container {
  /* max-width: 1200px; */
  margin: 0 auto;
}

.wrapper {
  width: 100%;
  margin: 0 auto;
  padding-top: 100px;
  padding-bottom: 100px;
  display: flex;
  justify-content: space-between;
}

.wrapper .image img {
  width: 400px;
  margin: 0 auto;
  display: flex;
  padding: 30px;
}

.contents {
  color: #707070;
  padding: 0 30px 30px 40px;
  font-size: 16px;
  text-align: left;
  width: 700px;
}

.section-title {
  color: #707070;
  margin-bottom: 30px;
  border-bottom: dotted #AC00BA;
}



/* sp */
@media screen and (max-width: 767px) {
  main {
    max-width: 100%;
    align-items: center;
  }

  h1 {
    margin: 10px;
  }

  /* Header */
  #header {
    height: auto;
    padding: 0;
    flex-direction: column;
  }

  #header ul {
    justify-content: flex-start;
  }

  #header li {
    font-size: 0.8rem;
  }

  #header .menu li {
    border-bottom: none;
  }

  #mainvisual {
    margin-top: 70px;

  }

  #mainvisual img {
    width: 100%;
    height: 250px;
  }

  #sub-title p {
  margin-top: 0;
}


  #works ul {
    flex-direction: column;
  }

  #works li {
    width: 100%;
  }

  .menu {
    align-items: center;
  }

  .wrapper {
    max-width: 100%;
    margin-bottom: 35px;
    flex-direction: column;
  }

  .wrapper .image img {
    margin: 0 auto;
    padding: 0;
    width: 70%;
  }

  .wrapper .contents {
    margin: 0 auto;
    padding: 0;
    width: 80%;
  }

  .site-title {
    margin-top: 20px;
  }

  .section-title {
    margin-bottom: 20px;
  }

}
</style>
