<template>
  <section id="imgTextType" class="imgText__wrap" :class="attr">
    <h2 class="blind">유용한 사이트 살펴보기</h2>
    <div class="imgText__inner" :class="layout">
      <div class="imgText__txt">
        <span>{{ itTitle.title1 }}</span>
        <h3>{{ itTitle.title2 }}</h3>
        <p>{{ itTitle.title3 }}</p>
        <ul v-for="it in itText" :key="it">
          <li>
            <a :href="it.link">{{ it.name }}</a>
          </li>
        </ul>
      </div>
      <div
        class="imgText__img"
        v-for="id in itDesc"
        :key="id"
        :class="id.class"
      >
        <a :href="id.linkTo" :class="id.class2">{{ id.name }}</a>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  props: {
    attr: String,
    layout: String,
  },
  data() {
    return {
      itTitle: {
        title1: "나만 아는 사이트!",
        title2: "유용한 사이트 살펴보기",
        title3: "색에 대한 감각이 없는 사람에게는 굉장히 유용한 사이트 입니다.",
      },
      itText: [
        {
          name: "튜토리얼 사이트",
          link: "/",
        },
        {
          name: "레퍼런스 사이트",
          link: "/",
        },
        {
          name: "색 추천 사이트",
          link: "/",
        },
        {
          name: "색 생성 사이트",
          link: "/",
        },
        {
          name: "색상 게임 사이트",
          link: "/",
        },
        {
          name: "Youtube 사이트",
          link: "/",
        },
      ],
      itDesc: [
        {
          class: "img1",
          name: "색 추천 사이트",
          linkTo: "/",
          class2: "",
        },
        {
          class: "img2",
          name: "색상 게임 사이트",
          linkTo: "/",
          class2: "blue",
        },
      ],
    };
  },
};
</script>

<style>
/* imgTextType */
.imgText__inner {
  display: flex;
  justify-content: space-between;
}

.imgText__inner > div {
  width: 32%;
  height: 500px;
}

.imgText__txt span {
  font-size: 16px;
  color: #666;
  text-decoration: underline;
  text-underline-position: under;
  margin-bottom: 20px;
  display: block;
}

.imgText__txt h3 {
  font-size: 50px;
  font-weight: 300;
  margin-bottom: 20px;
}

.imgText__txt p {
  font-size: 18px;
  font-weight: 300;
  line-height: 1.5;
  color: #666;
  margin-bottom: 10px;
}

.imgText__txt ul {
  font-size: 18px;
  font-weight: 300;
  line-height: 1.6;
}

.imgText__txt ul li {
  position: relative;
  padding-left: 20px;
}

.imgText__txt ul li::before {
  content: "";
  width: 5px;
  height: 5px;
  border-radius: 50%;
  position: absolute;
  left: 5px;
  top: 9px;
  background: #666;
}

.imgText__txt ul li a {
  color: #666;
}

.imgText__img {
  border-radius: 10px;
  position: relative;
}

.imgText__img a {
  display: inline-block;
  position: absolute;
  left: 30px;
  bottom: 30px;
  padding: 10px 30px;
  background-color: #7c2b39;
  color: #fff;
  font-size: 18px;
  border-radius: 30px;
}

.imgText__img a.blue {
  background-color: #2b387c;
}

.imgText__img a:hover {
  color: #7c2b39;
  background-color: #fff;
}

.imgText__img a.blue:hover {
  color: #2b387c;
  background-color: #fff;
}

.imgText__img.img1 {
  background: url("../../assets/img/imgText_bg01.jpg") no-repeat center / cover;
}

.imgText__img.img2 {
  background: url("../../assets/img/imgText_bg02.jpg") no-repeat center / cover;
}

/* parallax */
#imgTextType .imgText__txt {
  opacity: 1;
  transition: all 2s;
}

#imgTextType.parallax .imgText__txt {
  opacity: 1;
}

#imgTextType.parallax .imgText__img {
  transform: scale(1);
}

@media (max-width: 960px) {
  .section {
    padding: 100px 0;
  }

  .imgText__inner {
    flex-wrap: wrap;
  }

  .imgText__inner > div.imgText__txt {
    width: 100%;
    height: auto;
    text-align: center;
  }

  .imgText__inner > div.imgText__txt ul {
    display: none;
  }

  .imgText__inner > div.imgText__img {
    width: 49%;
  }

  .imgText__txt h3 {
    font-size: 40px;
  }

  .imgText__txt p {
    margin-bottom: 60px;
  }
}

@media (max-width: 600px) {
  .section {
    padding: 80px 0;
  }

  .imgText__txt h3 {
    font-size: 30px;
  }

  .imgText__txt p {
    margin-bottom: 50px;
    font-size: 16px;
  }

  .imgText__txt span {
    font-size: 14px;
    margin-bottom: 10px;
  }

  .imgText__inner > div.imgText__img {
    width: 100%;
    height: 300px;
  }

  .imgText__inner > div.imgText__img {
    margin-bottom: 20px;
  }

  .imgText__img a {
    left: 20px;
    bottom: 20px;
  }
}
</style>
