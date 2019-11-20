<template>
  <div>
    <h1>Welcome to the forum</h1>
    <ThreadList :threads="objec"/>
  </div>
</template>

<script>
  import sourceData from '@/data'
  import ThreadList from './ThreadList'
  export default {
    name: 'HelloWorld',
    components: {
      ThreadList
    },
    data () {
      return {
        threads: Object.values(sourceData.threads),
        posts: sourceData.posts,
        users: sourceData.users,
      }
    }
  }
</script>
