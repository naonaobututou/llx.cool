<script setup lang="ts">
  import { useRouter } from "vue-router"
  import type { Post, PostType } from "~/types"

  const { dir } = defineProps<{
    dir: string
  }>()

  const router = useRouter()
  const routes: Post[] = router
    .getRoutes()
    .filter(
      i =>
        i.path.startsWith(dir) &&
        (import.meta.env.DEV ? true : i.meta.frontmatter.date)
    )
    .map(i => ({
      path: i.path,
      ...i.meta.frontmatter,
      date: formatDate(i.meta.frontmatter.date),
    }))

  const posts = computed(() =>
    routes.sort((a, b) => +new Date(b.date!) - +new Date(a.date!))
  )

  const iconConfig: { [key in PostType]: string } = {
    photo: "i-lucide-camera",
    post: "i-lucide-file-signature",
    cook: "i-lucide-chef-hat",
  }
</script>

<template>
  <!-- <pre>{{ JSON.stringify(posts, null, 2) }}</pre> -->
  <template v-if="posts.length">
    <div
      v-for="post in posts"
      :key="post.path"
      class="my4"
    >
      <span class="text-sm text-right ws-nowrap op75">
        {{ formatDate(post.date!) }}
      </span>
      <h3 class="mt-0">
        <RouterLink :to="post.path">
          <i
            v-if="post.type"
            :class="['mr-1', iconConfig[post.type]]"
          />
          <span>{{ post.title }}</span>
        </RouterLink>
      </h3>
    </div>
  </template>
</template>
