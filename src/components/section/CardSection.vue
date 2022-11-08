<template>
  <section id="cardType" class="card__wrap" :class="attr">
    <h2>{{ cardTitle.title }}</h2>
    <p>{{ cardTitle.desc }}</p>
    <div class="card__inner" :class="layout">
      <article class="card" v-for="ct in cardText" v-bind:key="ct">
        <figure class="card__header">
          <img :src="ct.imgSrc" alt="{{ct.cardTitle}}" />
        </figure>
        <div class="card__body">
          <h3 class="tit">{{ ct.cardTitle }}</h3>
          <p class="desc">
            {{ ct.cardDesc }}
          </p>
          <a :href="ct.btnLink" class="btn">
            {{ ct.linkText }}
            <span aria-hidden="true">
              <svg
                width="101"
                height="8"
                viewBox="0 0 101 8"
                fill="none"
                xmlns="http://www.w3.org/2000/svg"
              >
                <path
                  d="M100.354 4.35355C100.549 4.15829 100.549 3.84171 100.354 3.64645L97.1716 0.464466C96.9763 0.269204 96.6597 0.269204 96.4645 0.464466C96.2692 0.659728 96.2692 0.976311 96.4645 1.17157L99.2929 4L96.4645 6.82843C96.2692 7.02369 96.2692 7.34027 96.4645 7.53553C96.6597 7.7308 96.9763 7.7308 97.1716 7.53553L100.354 4.35355ZM0 4.5H100V3.5H0V4.5Z"
                  fill="black"
                />
              </svg>
            </span>
          </a>
        </div>
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
      cardTitle: {
        title: "화가 되어보기🧐",
        desc: "색에 대해 알았다면, 그림을 그려볼까요?",
      },
      cardText: [
        {
          imgSrc: "../../assets/img/card_bg01.jpg",
          cardTitle: "밑그림 그리기",
          cardDesc: `그림을 그리기에 앞서서 먼저 밑그림을 그려야겠죠? 아 참 그전에 뭘
            그릴지 목표부터 정해야 합니다. 우선 일상생활에서 흔히 볼 수 있는
            것들을 그려봐요 우리.`,
          btnLink: "/",
          linkText: "더 자세히 보기",
        },
        {
          imgSrc: "../../assets/img/card_bg02.jpg",
          cardTitle: "채색 구상하기",
          cardDesc: `밑그림을 훌륭하게 스케치 했다면, 채색을 해야겠죠? 꼭 그 물체가 있는 그대로의 색을 칠할 필요 없습니다. 본인의 독창성에 맞게 색을 생각해보죠.`,
          btnLink: "/",
          linkText: "더 자세히 보기",
        },
        {
          imgSrc: "../../assets/img/card_bg03.jpg",
          cardTitle: "채색 하기",
          cardDesc: `마무리 단계 입니다. 색을 다 구상 했다면, 물감으로 칠해 봐야 겠죠? 앞서서 배웠던 색의 효과와 힘에대해 주의하면서 색을 채워줍니다. 완성!.`,
          btnLink: "/",
          linkText: "더 자세히 보기",
        },
      ],
    };
  },
};
</script>

<style>
/* cardType */
.card__inner {
  display: flex;
  justify-content: space-between;
  /* 카드끼리 정렬 */
}

.card {
  width: 32%;
  background-color: #f5f5f5;
}

.card a.btn {
  display: inline-block;
  transition: all 0.4s ease;
}

.card a.btn:hover {
  background-color: rgba(235, 100, 100, 0.21);
  padding: 10px;
  border-radius: 5px;
  transform: scale(1.1) translateX(10px);
}

.card__body {
  padding: 24px 20px;
}

.card__body .tit {
  font-size: 24px;
  margin-bottom: 10px;
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
  padding-right: 20px;
}

.card__body .desc {
  font-size: 18px;
  line-height: 1.4;
  color: #666;
  margin-bottom: 20px;
  font-weight: 300;
  overflow: hidden;
  text-overflow: ellipsis;
  display: -webkit-box;
  -webkit-line-clamp: 4;
  -webkit-box-orient: vertical;
}

/* parallax */
#cardType h2 {
  opacity: 1;
  /* transform: translateX(-100px); */
  transition: all 1s 0.3s cubic-bezier(0.68, -0.55, 0.27, 1.55);
}

#cardType.parallax h2 {
  animation: h2 0.6s forwards;
}

@keyframes h2 {
  0% {
    opacity: 0.3;
    transform: translateX(-100px);
  }

  25% {
    opacity: 0.5;
    transform: translateX(100px);
  }

  50% {
    opacity: 0.7;
    transform: translateX(-100px);
  }

  100% {
    opacity: 1;
    transform: translateX(0px);
  }
}

#cardType > p {
  opacity: 1;
  /* transform: translateX(100px); */
  transition: all 1s 0.3s cubic-bezier(0.68, -0.55, 0.27, 1.55);
}

#cardType.parallax > p {
  animation: p 0.6s forwards;
}

@keyframes p {
  0% {
    opacity: 0.3;
    transform: translateX(100px);
  }

  25% {
    opacity: 0.5;
    transform: translateX(-100px);
  }

  50% {
    opacity: 0.7;
    transform: translateX(100px);
  }

  100% {
    opacity: 1;
    transform: translateX(0px);
  }
}

#cardType .card {
  opacity: 1;
  /* transform: translateY(200px) rotate(30deg) skew(20deg); */
  transition: all 1s 0.6s cubic-bezier(0.68, -0.55, 0.27, 1.55);
}

#cardType.parallax .card {
  opacity: 1;
  transform: translateY(0px) rotate(0) skew(0);
}

@media (max-width: 960px) {
  .card__inner {
    flex-wrap: wrap;
  }

  .card {
    width: 49%;
  }

  .card:last-child {
    display: none;
  }
}

@media (max-width: 600px) {
  .card {
    width: 100%;
  }

  .card:first-child {
    margin-bottom: 20px;
  }

  .card__body {
    padding: 20px;
  }

  .card__body .desc {
    font-size: 16px;
  }
}
</style>
