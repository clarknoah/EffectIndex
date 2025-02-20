<template>
  <div class="pageContent">
    <h1>
      <nuxt-link to="/categories/">
        Effect Categories
      </nuxt-link> -      
      Disconnective Effects
      <Icon
        filename="disconnective.svg"
        class="categoryIcon"
      /> 
    </h1>

    <p>
      <b>Disconnective effects</b> are defined as any subjective effect that feels as if it disconnects one from the external environment, their senses, and/or their consciousness.
    </p>

    <p>
      These effects are typically associated with <nuxt-link to="/effects/dissociative-intensity-scale">
        dissociative hallucinogens
      </nuxt-link> and likely occur due to the way in which these compounds function as NMDA receptor antagonists. This means they bind to receptors in the brain but do not activate them, thus blocking other neurotransmitters from doing so. The result is a dose-dependent decrease in the passing of electrical signals across the brain and an overall disconnection of neurons, which leads to states of disconnection between conscious parts of the brain and its sensory organs.
    </p>

    <p>
      This page lists the various disconnective effects that can occur under the influence of certain psychoactive compounds.
    </p>

    <hr>

    <EffectList
      :effects="effects"
      :tags="['disconnective']"
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
      title: "Disconnective Effects"
    };
  },
  computed: {
    effects() {
      return this.$store.state.effects.list;
    }
  }
};
</script>
