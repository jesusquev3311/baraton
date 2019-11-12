<template>
    <div class="side-bar">
      <ul>
        <li class="main-category" :key="category.id" v-for="category in categories">
          <span>{{category.name}}</span>
          <ul class="subcategories">
            <li class="sub-category" :key="subcat.id" v-for="subcat in category.sublevels">
              <span>{{subcat.name}}</span>
              <ul class="low-categories">
                <li class="low-category" :key="lowcat.id" v-for="lowcat in subcat.sublevels"  @click="levelClick(lowcat.id)">
                  <span>{{lowcat.name}}</span>
                </li>
              </ul>
            </li>
          </ul>
        </li>
      </ul>
    </div>
</template>

<script>
import categories from '../data/categories'
export default {
  name: 'sidebar',
  props: ['level'],
  data () {
    return {
      categories: categories.categories
    }
  },
  methods: {
    levelClick (level) {
      this.$emit('filter', level)
    }
  }
}
</script>

<style scoped lang="scss">
  $base-color: #f26d78;
  $title-color: #333;
  $sub-title-color: #8c8c8c;
  .side-bar{
    background-color: #fff;
    padding: 10px 20px;
    border: 1px solid #ededed;
    ul{
      padding: 0;
      list-style: none;
      text-align: left;
      .main-category{
        font-size: 18px;
        font-weight: bold;
        padding: 10px 5px;
        color: $title-color;
        cursor: pointer;
        .subcategories{
          color: $base-color;
          padding: 10px 20px;
          .sub-category{
            cursor: pointer;
          }
          .low-categories{
            .low-category{
              padding: 10px;
              color:$sub-title-color;
              cursor: pointer;
            }
          }
        }
      }
    }
  }
</style>
