<template>
  <div class="pageContent">
    <h1>
      <nuxt-link to="/categories/">
        Effect Categories
      </nuxt-link> -      
      Physical Alterations
      <Icon
        filename="cogs.svg"
        class="categoryIcon"
      /> 
    </h1>

    <p>
      <b>Physical alterations</b> are defined as any subjective effect that changes a facet of a person's physical body in a manner which is not <nuxt-link to="/categories/uncomfortable-physical-effects">
        uncomfortable
      </nuxt-link> and does not involve a clearly definable <nuxt-link to="/categories/physical-amplifications">
        amplification
      </nuxt-link> or <nuxt-link to="/categories/physical-suppressions">
        suppression.
      </nuxt-link>
    </p>

    <p>
      This page lists the various physical alterations that can occur under the influence of certain psychoactive compounds.
    </p>

    <hr>

    <EffectList
      :effects="effects"
      :tags="['physical', 'alteration']"
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
      title: "Physical Alterations"
    };
  },
  computed: {
    effects() {
      return this.$store.state.effects.list;
    }
  }
};
</script>
