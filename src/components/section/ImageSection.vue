<template>
  <section id="imageType" class="image__wrap" :class="attr">
    <h2>{{ imgTitle.title }}</h2>
    <p>{{ imgTitle.desc }}</p>
    <div class="image__inner" :class="layout">
      <article
        v-for="img in imgText"
        :key="img"
        :class="img.class"
        class="image"
      >
        <h3 class="image__title">{{ img.title }}</h3>
        <p class="image__desc">{{ img.desc }}</p>
        <a
          :href="img.linkTo"
          :title="img.linkText"
          class="image__btn"
          :class="img.class2"
          >{{ img.linkText }}</a
        >
      </article>
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
      imgTitle: {
        title: "강렬한 색감은 사람을 이끈다",
        desc: "이렇게 강렬한 사람을 본적 있습니까? 이게 바로 색의 효과입니다. 빨강색은 뭐든 돋보기에 해주죠",
      },
      imgText: [
        {
          class: "img1",
          title: "빨강은 강렬한 색채의 상징",
          desc: `빨강은 무척이나 강렬한 색채입니다. 색 그자체가 의미하는 바도
          명확하구요. 이렇게 무채색 계열에 빨강을 입히면 주목성을 이끌 수
          있습니다...`,
          linkText: "자세히 보기",
          linkTo: "/",
          class2: "",
        },
        {
          class: "img2",
          title: "쓸쓸한 느낌의 검정",
          desc: `그림에서 무엇이 연상되시나요? 고독.. 겨울.. 기약없는 기다림... 이러한
          것들이 내포되어 있죠.. 검정색의 배경은 사람을 참 쓸쓸하게 하죠?`,
          linkText: "자세히 보기",
          linkTo: "/",
          class2: "yellow",
        },
      ],
    };
  },
};
</script>

<style>
/* imageType */
.image__inner {
  display: flex;
  justify-content: space-between;
}

.image {
  width: 49%;
  height: 370px;
  color: #fff;
  padding: 200px 30px 30px 30px;
  box-sizing: border-box;
  transition: all 0.7s ease;
}

.image:hover {
  transform: scale(1.05);
}

.image.img1 {
  background: url("../../assets/img/imgType01_01.jpg") no-repeat center;
}

.image.img2 {
  background: url("../../assets/img/imgType01_02.jpg") no-repeat center;
}

.image__title {
  font-size: 32px;
  margin-bottom: 10px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.image__desc {
  font-size: 16px;
  margin-bottom: 10px;
  line-height: 1.5;
  font-weight: 300;
  overflow: hidden;
  text-overflow: ellipsis;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
}

.image__btn {
  font-size: 16px;
  color: #fff;
  background-color: #99420f;
  padding: 10px 20px;
  display: inline-block;
}

.image__btn:hover {
  background-color: #fff;
  color: #99420f;
}

.image__btn.yellow {
  background-color: #464444;
}

.image__btn.yellow:hover {
  background-color: #fff;
  color: #464444;
}

/* parallax */
#imageType h2 {
  opacity: 1;
  transition: all 0.5s;
}

#imageType p {
  opacity: 1;
  transition: all 0.5s;
}

#imageType .img1 {
  opacity: 1;
  /* transform: translateX(-100px); */
  transition: all 0.5s 0.3s cubic-bezier(0.68, -0.55, 0.27, 1.55);
}

#imageType .img2 {
  opacity: 1;
  /* transform: translateX(100px); */
  transition: all 0.5s 0.3s cubic-bezier(0.68, -0.55, 0.27, 1.55);
}

#imageType.parallax h2 {
  opacity: 1;
}

#imageType.parallax p {
  opacity: 1;
}

#imageType.parallax .img1 {
  opacity: 1;
  transform: translateX(0px);
}

#imageType.parallax .img1:hover {
  transform: scale(1.05);
}

#imageType.parallax .img2 {
  opacity: 1;
  transform: translateX(0px);
}

#imageType.parallax .img2:hover {
  transform: scale(1.05);
}

@media (max-width: 600px) {
  .image__inner {
    flex-direction: column;
  }

  .image {
    width: 100%;
    padding: 205px 20px 20px 20px;
  }

  .image:first-child {
    margin-bottom: 20px;
  }

  .image__title {
    font-size: 24px;
  }
}
</style>
