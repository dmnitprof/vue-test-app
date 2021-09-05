<template>
  <div>
    <h1>Страница с постами</h1>
        <d-input
            v-focus
            v-model="searchQuery"
            placeholder="Поиск..."
        />
        <div class="app__btns">
          <d-button
          >
            Создать пост
          </d-button>

          <d-select
              v-model="selectedSort"
              :options="sortOptions"
          />

        </div>

        <d-dialog v-model:show="dialogVisible">
          <post-form
          />
        </d-dialog>

        <post-list
            :posts="sortedAndSearchedPosts"
            v-if="!isPostLoading"
        />
        <div v-else>Идет загрузка...</div>
  </div>
</template>

<script>
import {usePosts} from '../hooks/usePosts'
import useSortedPosts from '../hooks/useSortedPosts'
import useSortedAndSearchedPosts from '../hooks/useSortedAndSearchedPosts'
import PostList from '../components/PostList.vue'
import PostForm from  '../components/PostForm.vue'
export default {
  components: {PostList, PostForm},
  data() {
    return {
      dialogVisible: false,
      sortOptions: [
        {value: 'title', name: 'По названию'},
        {value: 'body', name: 'По описанию'}
      ]
    }
  },
  setup(props) {
    const {posts, totalPages, isPostLoading} = usePosts(10)
    const {sortedPosts, selectedSort} = useSortedPosts(posts)
    const {searchQuery, sortedAndSearchedPosts} = useSortedAndSearchedPosts(sortedPosts)

    return {
      posts,
      totalPages,
      isPostLoading,
      sortedPosts,
      selectedSort,
      searchQuery,
      sortedAndSearchedPosts

    }
  }
}

</script>

<style>
.app__btns {
  display: flex;
  justify-content: space-between;
  margin: 1rem 0
}

.page__wrapper {
  display: flex;
  margin-top: 1rem;
}

.page {
  border: 1px solid black;
  padding: .8rem;
}

.current-page {
  border: 2px solid darkgoldenrod;
  background: lightsalmon;
}

.observer {
  height: 30px;
  background: cadetblue;
}
</style>

