<template>
  <div class="about">
    <transition
      name="fade"
      appear
      @before-enter="beforeEnter"
      @enter="enter"
      @after-enter="afterEnter"
    >
      <h1>About</h1>
    </transition>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Cum aperiam
      officia possimus delectus inventore quod quisquam culpa voluptas iusto,
      quae maiores quo dolorum, corporis laboriosam a <do></do>lore consequatur
      assumenda nam!
    </p>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Cum aperiam
      officia possimus delectus inventore quod quisquam culpa voluptas iusto,
      quae maiores quo dolorum, corporis laboriosam a dolore consequatur
      assumenda nam!
    </p>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Cum aperiam
      officia possimus delectus inventore quod quisquam culpa voluptas iusto,
      quae maiores quo dolorum, corporis laboriosam a dolore consequatur
      assumenda nam!
    </p>
  </div>
</template>

<script>
import { ref } from '@vue/reactivity';
import gsap from 'gsap';

export default {
  setup() {
    const beforeEnter = (el) => {
      console.log('before enter - set initial state');
      el.style.transform = 'translateY(-60px)';
      el.style.opacity = 0;
    };

    const enter = (el, done) => {
      console.log('enter', el);
      gsap.to(el, {
        y: 0,
        opacity: 1,
        duration: 0.5,
        ease: 'bounce.out',
        onComplete: done,
      });
    };

    const afterEnter = (el) => {
      console.log('after enter', el);
    };

    return {
      beforeEnter,
      enter,
      afterEnter,
    };
  },
};
</script>

<style>
.about {
  max-width: 600px;
  margin: 20px auto;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 3s ease;
}
</style>
