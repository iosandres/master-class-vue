<template>
  <div class="col-full">
    <h1>{{category.name}}</h1>
    <CategoryListItem :category="category" />
  </div>
</template>
<script>
import CategoryListItem from 'comp/CategoryListItem'
import sourceData from '@/data'
export default {
  components: {
    CategoryListItem
  },
  props: {
    id: {
      required: true,
      type: String
    }
  },
  computed: {
    category () {
      return sourceData.categories[this.id]
    }
  }
}
</script>