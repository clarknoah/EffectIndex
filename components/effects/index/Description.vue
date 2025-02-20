<template>
  <div class="descriptionContainer">
    <p>
      The <span style="font-weight: bold;"> Subjective Effect Index </span> is a set of articles designed to serve as a comprehensive catalogue and reference for the range of subjective effects that may occur under the influence of psychoactive substances and other psychonautic techniques.
    </p>

    <transition name="grow">
      <div 
        v-show="show"
        class="showMoreContainer"
      >
        <p>
          The effects listed here are accompanied by detailed descriptions on the subjective experiences of them. They are written in a consistent and formal 
          <nuxt-link to="/documentation-style-guide">
            writing style 
          </nuxt-link> 
          that avoids the use of flowery metaphors or analogy; instead, they strive to use simple and accessible language. This is done with the hope that they will eventually serve as a universal terminology set that enables people to better communicate and share experiences that are, by nature, difficult to convey.
        </p>

        <p>
          The Index is separated into {{ effectCount }} effects, which are organised into categories based on the senses they affect and their behavior. Many of these are further broken down into leveling systems, subcomponents, and style variations that may occur across different substances. Detailed image, video, and audio <nuxt-link to="/replications">
            replications
          </nuxt-link> have been included wherever possible to supplement text-based descriptions.
        </p>

        <p>
          The content within this Index is based on the collective experiences of our contributors, scientific literature, and individual case reports. The Index itself, as well as a majority of the content, was originally created by our site founder <nuxt-link to="/profiles/Josie">
            Josie Kins.
          </nuxt-link>
        </p>
      </div>
    </transition>
    <div class="buttonContainer">
      <button 
        class="whiteButton"
        @click="toggleText"
      >
        {{ show ? 'Read Less' : 'Read More' }}
      </button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      show: false
    };
  },
  computed: {
    effectCount() {
      return this.$store.state.effects.list.length;
    }
  },
  methods: {
    toggleText() {
      this.show = !this.show;
    }
  }
};
</script>

<style scoped>

.descriptionContainer {
  margin-bottom: 2em;
}

.grow-enter-active {
  opacity: 1;
  transition: opacity 1s;
}
.grow-enter {
  opacity: 0;
}
</style>