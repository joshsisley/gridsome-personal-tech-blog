<template>
  <header
    id="header"
    class="header flex flex-col md:flex-row md:justify-between items-center p-4 md:p-6"
    role="banner"
  >
    <div class="header-container">
      <g-link
        class="company-logo-link block text-white font-bold text-2xl md:text-3xl hover:text-pink-500"
        to="/"
        aria-label="Back to home"
      ><span class="bracket-logo">{</span>{{ $static.metadata.siteName }}<span class="bracket-logo">}</span></g-link>

      <nav id="nav" class="nav hidden md:flex pages">
        <ul class="menu flex flex-col md:flex-row items-center list-reset text-base">
          <li
            class="level-1 mb-4 md:mb-0"
            v-for="element in $static.metadata.menu"
            :key="element.name"
          >
            <g-link
              :to="element.link"
              class="link font-bold text-white hover:text-pink-500"
              active-class="is-active-link"
              exact-active-class="active text-pink-500"
            >{{ element.name }}</g-link>
          </li>
        </ul>
      </nav>
      <nav id="nav" class="nav hidden md:flex social">
        <ul class="menu flex flex-col md:flex-row items-center list-reset text-base">
          <li
            class="level-1 mb-4 md:mr-4 md:mb-0"
          >
            <a>F</a>
          </li>
        </ul>
      </nav>
    </div>
  </header>
</template>

<script>
export default {
  methods: {
    socialIcon(element) {
      return `/icons.svg#icon-${element.icon}`;
    }
  }
};
</script>

<static-query>
query {
  metadata {
    siteName
    menu {
      name
      link
    }
  }
}
</static-query>