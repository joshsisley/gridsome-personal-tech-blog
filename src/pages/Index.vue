<template>
  <Layout>
    <!-- <section id="container-centre" class="column centre flex-1">
      <h1 class="page-title">Welcome to Skeleventy!</h1>
      <div class="content">
        <p>
          A 
          <a href="https://www.gridsome.org">Gridsome</a> starter built with
          <a href="https://tailwindcss.com">TailwindCSS</a>.
        </p>
        <h2 class="text-3xl">Features</h2>
        <ul class="mb-12 list-disc pl-4">
          <li>Build sites faster with the power of Gridsome, TailwindCSS and SCSS</li>
          <li>Image lazyloading via gridsome builtin functionality</li>
          <li>A simple blog with categories, tags and featured images</li>
        </ul>
      </div>
    </section> -->
    <!-- My intro -->
    <section class="intro-section">
      <div class="bg-image">
        <div class="intro-content">
          <h1>Hello, I'm <span>Josh Sisley</span>.</h1>
          <h1>I am a Full-Stack JavaScript Developer.</h1>
          <h2>I build high performance SaaS applications using the latest cutting edge web development technologies.</h2>
        </div>
      </div>
    </section>
    <section class="about-section">
      <div>
        <img src="../dev.svg" width="400">
      </div>
      <div class="short-intro">
        <h1>About Me</h1>
        <p>Hey there! Let me introduce myself again, my name is Josh and I am a full-stack JavaScript developer. I have over 6 years of experience developing websites and web applications for companies ranging from Startups to some of the largest companies in the country. My go to library on the front-end is Angular, and NodeJS on the backend.</p>
        <p>Currently, I'm working as a Senior Full Stack Developer at Daysmart Software Inc, building a stable and scalable SaaS application for pet boarding, daycare and groomer facilities.</p>
        <p>If you'd like, you can 
          <g-link
              :to="'/about'"
              class="inline-link"
              active-class="is-active-link"
              exact-active-class="active text-pink-500"
            >read more about me here</g-link>, or scroll to see the skills and tools that I use daily.</p>
      </div>
    </section>
    <!-- My experience -->
    <section class="bg-polygon skill-section">
      <div>
        <img :src="'../codetools.svg'" alt="">
        <h1>Skills &amp; Tools</h1>
      </div>
      <div class="skill-row">
        <div class="skill-col">
          <h2>Front End</h2>
          <div class="skills-vert-row"> 
            <div class="skill-card" v-for="skill in $static.metadata.frontend" :key="skill.name">
              <div class="icon">
                <img :src="skill.url" width="48">
              </div>
              <div class="info">
                <h3>{{ skill.name }}</h3>
                <p>{{ skill.description }}</p>
              </div>
            </div>
          </div>
        </div>
        <div class="skill-col">
          <h2>Back End</h2>
          <div class="skills-vert-row"> 
            <div class="skill-card" v-for="skill in $static.metadata.backend" :key="skill.name">
              <div class="icon">
                <img :src="skill.url" width="48">
              </div>
              <div class="info">
                <h3>{{ skill.name }}</h3>
                <p>{{ skill.description }}</p>
              </div>
            </div>
          </div>
        </div>
        <div class="skill-col">
          <h2>Cloud &amp; Database</h2>
          <div class="skills-vert-row">
            <div class="skill-card" v-for="cloud in $static.metadata.clouddb" :key="cloud.name">
              <div class="icon">
                <img :src="cloud.url" width="48">
              </div>
              <div class="info">
                <h3>{{ cloud.name }}</h3>
                <p>{{ cloud.description }}</p>
              </div>
            </div>
          </div>
        </div>
        <div class="skill-col">
          <h2>Other Tools</h2>
          <div class="skills-vert-row">
            <div class="skill-card" v-for="tool in $static.metadata.tools" :key="tool.name">
              <div class="icon">
                <img :src="tool.url" width="48">
              </div>
              <div class="info">
                <h3>{{ tool.name }}</h3>
                <p>{{ tool.description }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="skill-action">
        <p>For some examples of my work please check out my Github by clicking the link below!</p>
        <div class="btn-container">
          <a href="https://github.com/joshsisley" target="_blank" rel="noopener noreferrer" class="btn-cta">Go to Github</a>
        </div>
      </div>
    </section>
    <section class="contact-section">
      <div class="image">
        <img src="../email.svg" alt="">
      </div>
      <div class="info">
        <h1>Have a question?</h1>
        <p>Send me an email at:</p>
        <a class="link">josh@sisley.tech</a>
      </div>
    </section>
  </Layout>
</template>

<script>
export default {
  metaInfo: {
    title: "Home"
  }
};
</script>

<static-query>
query {
  metadata {
    siteName
    frontend {
      name
      description
      url
    }
    backend {
      name
      description
      url
    }
    clouddb {
      name
      description
      url
    }
    tools {
      name
      description
      url
    }
  }
}
</static-query>
