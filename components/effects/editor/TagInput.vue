<template>
  <div>
    <input 
      v-model="tagInputText"
      class="effectEditor__input"
      @keyup="changeInput"
    >
    <ul class="tagList">
      <li
        v-for="(tag, index) in value"
        :key="tag"
        class="tagItem" 
      >
        <div class="tagItem__content">
          {{ tag }}
          <a @click="removeTag(index)">
            <Icon
              filename="times-circle.svg"
              color="red"
            />
          </a>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
import Icon from '@/components/Icon';

export default {
  components: {
    Icon
  },
  props: {
    value: {
      type: Array,
      default: () => []
    }
  },
  data() {
    return {
      tagInputText: ""
    };
  },
  methods: {
    changeInput(e) {
      if (e.keyCode === 13) {
        if (this.value.indexOf(e.target.value) === -1) {
          this.$emit(
            "input",
            [e.target.value.trim()].concat(this.value).sort()
          );
        }
        this.tagInputText = "";
      } else if (e.target.value.indexOf(",") > -1) {
        let arr = e.target.value
          .split(",")
          .map(val => val.trim())
          .filter(val => val.length > 0);

        let newValue = [];

        arr.forEach(tag => {
          if (this.value.indexOf(tag) === -1) {
            newValue.push(tag);
          }
        });

        this.$emit("input", newValue.concat(this.value).sort());
        this.tagInputText = "";
      }
    },
    removeTag(index) {
      let newArr = this.value.slice();
      newArr.splice(index, 1);
      this.$emit("input", newArr);
    }
  }
};
</script>

<style scoped>
.tagItem {
  display: inline-block;
  width: 200px;
  color: black;
  background-color: #f5f5f5;
  padding-left: 10px;
  border: 1px dotted #ccc;
  margin: 3px;
  padding: 7px;
  border-radius: 15px;
}

.tagItem a {
  color: #555;
}

.tagItem a:hover {
  color: rgb(134, 19, 19);
}

.tagList {
  list-style: none;
  max-height: 300px;
  overflow-y: auto;
  font-size: 14px;
  margin-top: 1em;
  padding: 0;
}

.icon {
  height: 1em;
  width: 1em;
  opacity: 0.5;
}

.icon:hover {
  opacity: 1;
}

.tagItem__content {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
</style>