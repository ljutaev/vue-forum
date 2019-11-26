<template>
  <div>
    <div class="push-top col-large">
      <!-- <h1>{{thread.title}}</h1> -->
      <PostList :posts="posts"/>
      <!-- <PostList :posts="[0]"/> -->
      <form @submit="addPost">
        <div class="form-group">
          <textarea 
            name="" 
            id="" 
            cols="30" 
            rows="10" 
            class="form-input"
            v-model="newPostText"
          ></textarea>
        </div>
        <div class="form-actions">
          <button class="btn-blue">Submit post</button>
        </div> 
      </form>
    </div>
  </div>
</template>

<script>
  import sourceData from '@/data'
  console.log(sourceData)
  import PostList from '@/components/PostList'
  export default {
    name: 'ThreadShow',
    components: {
      PostList
    },
    props: {
      id: {
        required: true,
        type: String
      }
    },
    data () {
      return {
        thread: sourceData.threads[this.id],
        newPostText: '',
      }
    },
    computed: {
      posts () {
        const postIds = Object.values(this.thread.posts)
        return Object.values(sourceData.posts)
          .filter(post => postIds.includes(post['.key']))
      }
    },
    methods: {
      addPost () {
        const post = {
          text: this.newPostText,
          publishedAt: Math.floor(Date.now() / 1000),
          threadId: this.id,
          userId: "7uVPJS9GHoftN58Z2MXCYDqmNAh2"
        }
        const postId = 'greatPost' + Math.random()
        sourceData.posts[postId] = post
        this.thread.posts[postId] = postId
      }
    }
  }
</script>
