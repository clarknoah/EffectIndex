<template>
  <div class="blogPost">
    <client-only>
      <div 
        v-if="$auth.loggedIn"
        class="blogPost__admin"
      >
        <nuxt-link 
          :to="'/admin/blog/' + post.slug"
          class="blogPost__edit"
        > 
          <Icon
            :filename="'edit.svg'"
            color="green"
          /> 
        </nuxt-link>    
        <a 
          class="blogPost__delete"
          @click="$emit('delete-post', post._id)"
        >  
          <Icon
            :filename="'times.svg'"
            color="red"
          />
        </a>
      </div>
    </client-only>
    <h4 class="blogPost__date"> 
      <nuxt-link 
        :to="'/blog/' + post.slug + '/'"
        style="text-decoration: none;"
      >
        {{ formatDate(post.datetime) }}
      </nuxt-link>
    </h4>
    
    <h1 class="blogPost__title">
      <nuxt-link 
        :to="'/blog/' + post.slug + '/'"
        style="text-decoration: none;"
      >
        {{ post.title }}
      </nuxt-link>
    </h1>
    <!-- eslint-disable-next-line -->
    <div class="blogPost__body" v-html="$md.render(post.body)" /> 
  </div>
</template>

<script>
import fecha from "fecha";
import Icon from '@/components/Icon';

export default {
  components: {
    Icon
  },
  props: {
    post: {
      type: Object,
      default: undefined
    },
    loggedIn: {
      type: String,
      default: ""
    }
  },
  methods: {
    formatDate(date) {
      return fecha.format(new Date(date), "dddd MMMM DD YYYY");
    }
  }
};
</script>

<style scoped>
.blogPost__date {
  color: #999999;
  font-size: 16px;
  font-weight: 400;
  letter-spacing: normal;
}

.blogPost__date a {
  color: #aaa;
}

.blogPost__title a {
  color: black;
}

.blogPost__admin a {
  padding-right: 0.5em;
  cursor: pointer;
  padding-right: 0.5em;
}

</style>