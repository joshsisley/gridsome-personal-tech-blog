<template>
  <Layout>
    <section id="container-centre" class="blog-post-container">
      <div class="post-header">
        <div class="category-container">
          <ul>
            <li v-for="tag in $page.blog.tags" :key="tag.id">
              <g-link :to="tag.path">
                {{ tag.title}}
              </g-link>
            </li>
          </ul>
        </div>
        <h1
          v-html="$page.blog.title"
        ></h1>
        <div class="text-sm md:text-base text-gray-600 flex blog-author-container">
          <div class="author">
            <span>Posted by <strong>{{ $page.blog.author.name }}</strong></span>
            <span>on <time :datetime="$page.blog.datetime">{{ $page.blog.humanTime }}</time></span>
          </div>
          <div class="share">
            <span>Posted in <g-link :to="$page.blog.category.path">{{ $page.blog.category.title }}</g-link></span>
            <!-- <ul>
              <li>
                <a>
                  <img :src="'../../facebook.svg'" />
                </a>
              </li>
              <li>
                <a>
                  <img :src="'../../twitter.svg'" />
                </a>
              </li>
              <li>
                <a>
                  <img :src="'../../linkedin.svg'" />
                </a>
              </li>
            </ul> -->
          </div>
          <!-- <p class="category">
            Posted in
            <g-link :to="$page.blog.category.path">{{ $page.blog.category.title }}</g-link>
          </p> -->
        </div>
        <figure>
          <g-image :alt="$page.blog.image_caption" :src="$page.blog.image" />
          <figcaption
            class="text-center text-sm italic text-gray-600 mt-4"
          >{{ $page.blog.image_caption }}</figcaption>
        </figure>
      </div>

      <div class="content post md:px-16">
      
        <p v-html="$page.blog.excerpt"></p>

        <div v-html="$page.blog.content"></div>

        <ul class="flex pt-8 border-t border-gray-100">
          <li class="mr-2" v-for="tag in $page.blog.tags" :key="tag.id">
            <g-link
              :to="tag.path"
              class="inline-block border border-pink-300 px-4 py-2 text-pink-500 text-xs font-semibold rounded hover:text-white hover:bg-pink-500 hover:border-pink-500"
              
            >{{ tag.title}}</g-link>
          </li>
        </ul>
      </div>

      
    </section>
  </Layout>
</template>


<page-query>
  query($id: ID!) {
    blog(id: $id) {
      title
      path
      image(width:1200)
      image_caption
      excerpt
      content
      humanTime : created(format:"Do MMMM YYYY")
      datetime : created(format:"ddd MMM DD YYYY hh:mm:ss zZ")
      category {
        title
        path
      }
      author {
        name
      }
      tags {
        id
        title
        path
      }
    }


    
  }
</page-query>

<script>
export default {
  metaInfo() {
    return {
      title: this.$page.blog.title
    };
  }
};
</script>
