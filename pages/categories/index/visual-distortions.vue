<template>
  <div class="pageContent">
    <h1>
      <nuxt-link to="/categories/">
        Effect Categories
      </nuxt-link> -      
      Visual Distortions
      <Icon
        filename="distortions.svg"
        class="categoryIcon"
      /> 
    </h1>

    <p>
      <b>Visual distortions</b> are defined as any subjective effect that alters the perception or appearance of pre-existing visual data without adding any entirely new content.
    </p>

    <p>
      This page lists the various visual distortions that can occur under the influence of certain psychoactive compounds.
    </p>

    <hr>

    <EffectList
      :effects="effects"
      :tags="['visual', 'distortion']"
    />
  </div>
</template>

<script>
import EffectList from '@/components/categories/EffectList';
import Icon from '@/components/Icon';

export default {
  components: {
    EffectList,
    Icon
  },
  scrollToTop: true,
  head() {
    return {
      title: "Visual Distortions"
    };
  },
  computed: {
    effects() {
      return this.$store.state.effects.list;
    }
  }
};
</script>