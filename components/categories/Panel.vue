<template>
  <div
    class="categoryContainer"
  >
    <h3 class="categoryTitle">
      <nuxt-link 
        v-if="page"
        :to="page"
      >
        {{ title }}
      </nuxt-link>
      <span v-else> {{ title }} </span>
      <Icon
        v-if="icon"
        :filename="icon"
        class="panelIcon"
      />
    </h3>
    <div class="actionContainer">
      <slot />
    </div>
  </div>
</template>

<script>
import Icon from '@/components/Icon';

export default {
  components: {
    Icon
  },
  props: {
    page: {
      type: String,
      default: ""
    },
    title: {
      type: String,
      default: ""
    },
    icon: {
      type: String,
      default: ""
    },
    image: {
      type: String,
      default: ""
    }
  },
};
</script>


<style scoped>
.actionContainer {
  padding: 0.5em;
}

.categoryContainer {
  margin-bottom: 1em;
  border: 1px solid #DDD;
  background-color: rgb(253, 253, 253);
}

.categoryContainer:last-child {
  margin-right: 0;
}

.categoryTitle {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  font-size: 14pt;
  margin: 0;
  text-align: left;
  padding: 0.5em;
  background-color: rgb(240, 240, 240);
  border-bottom: 1px solid #DDD;
  letter-spacing: 1px;
}

.panelIcon {
  opacity: 0.6;
}

</style>