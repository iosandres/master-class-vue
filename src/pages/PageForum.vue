<template>
<div :class="$style.forumWrapper">
    <div class="col-full push-top">
      <div class="forum-header">
        <div class="forum-details">
          <h1>{{forum.name}}</h1>
          <p class="text-lead">{{forum.description}}</p>
        </div>
        <a href="new-thread.html" class="btn-green btn-small">Start a thread</a>
      </div>
    </div>

    <div class="col-full push-top">
      <ThreadList :threads="threads"/>
    </div>
  </div>
</template>
<script>
import ThreadList from 'comp/ThreadList'
import SourceData from '@/data'

export default {
  components: {
    ThreadList
  },
  props: {
    id: {
      required: true,
      type: String
    }
  },
  computed: {
    forum () {
      return SourceData.forums[this.id]
    },
    threads () {
      return Object.values(SourceData.threads)
      .filter(thread => thread.forumId === this.id)
    }
  }
}
</script>
<style  module>
  .forumWrapper{
    width: 100%;
  }
</style>