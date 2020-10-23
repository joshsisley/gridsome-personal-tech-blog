<template>
  <Layout>
    <section id="container-centre" class="column centre flex-1">
      <div class="blog-header">
        <img :src="'../blog.svg'" width="48">
        <h1 class="page-title text-3xl md:text-center md:text-5xl mb-16 lg:mb-24 lg:text-6xl">The Blog</h1>
      </div>
      <div class="px-2">
        <!-- <div class="posts">
          <div
            class="mb-8 px-2"
            v-for="entry in $page.allBlog.edges"
            :key="entry.node.id"
          >
          <g-link
                    class="block text-purple-900"
                    :to="entry.node.path">
            <article class="article-card">
              <div class="post-image">
                <g-image :src="entry.node.image" :alt="entry.node.image_caption" />
              </div>
              <div class="post-info">
                <header class="text-2xl">
                  <ul>
                    <li>
                      <g-link :to="entry.node.category.path">{{ entry.node.category.title }}</g-link>
                    </li>
                  </ul>
                </header>
                <g-link class="article-name" :to="entry.node.path">{{entry.node.title}}</g-link>
                <div class="author-date">
                  <span>Posted by {{ entry.node.author.name }}</span>
                  <span> on <time :datetime="entry.node.datetime">{{ entry.node.humanTime }}</time></span>
                </div>
              </div>
            </article>
            </g-link>
          </div>
        </div> -->
        <div class="no-posts">
          <img :src="'../not-found.svg'" />
          <h1>Posts Coming Soon...</h1>
        </div>
      </div>
    </section>
  </Layout>
</template>

<script>
export default {
  metaInfo: {
    title: "Blog"
  }
};
</script>

<page-query>
  query {
    
    allBlog {
      
      edges {
        node {
          title
          path
          image(width:780)
          humanTime : created(format:"Do MMMM YYYY")
          datetime : created(format:"ddd MMM DD YYYY hh:mm:ss zZ")
          author {
            name
          }
          category {
            title
          }
        }
      }
    }
  }
</page-query>

