<template>
  <header class="header-container shadow radius">
    <div class="header-content">
      <figure>
        <img
          class="radius"
          src="~/assets/profile-picture.jpeg"
          alt="profile picture"
        />
      </figure>

      <nav class="links">
        <ul>
          <li v-for="(e, i) in internalLinks" :key="i">
            <nuxt-link class="link" :to="`#${e.to}`"> {{ e.text }} </nuxt-link>
          </li>
        </ul>
      </nav>

      <nav class="social">
        <ul>
          <li class="radius-small" v-for="(e, i) in socialLinks" :key="i">
            <a :href="e.url" :title="e.title">
              <i class="bx" :class="e.icon"> </i>
            </a>
          </li>
        </ul>
      </nav>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header",

  props: {
    internalLinks: {
      type: Array
    }
  },

  data() {
    return {
      socialLinks: [
        {
          icon: "bxl-github",
          url: "https://github.com/brdtheo",
          title: "GitHub"
        },
        {
          icon: "bxl-codepen",
          url: "https://codepen.io/theo-billardey",
          title: "Codepen"
        },
        {
          icon: "bxl-linkedin",
          url: "https://www.linkedin.com/in/theo-billardey/",
          title: "LinkedIn"
        },
        {
          icon: "bx-envelope",
          url: "mailto:theo.billardey@gmail.com",
          title: "Send email"
        }
      ]
    };
  }
};
</script>

<style scoped>
.header-container {
  padding: 1rem;
  background: #fff;
}

.header-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

figure {
  max-width: 10rem;
}

figure img {
  width: 100%;
}

nav {
  display: flex;
  font-size: 1.8rem;
}

nav ul {
  display: inherit;
}

nav ul li {
  display: inline-flex;
}

.links ul li {
  margin: 0 1rem;
}

.link {
  display: flex;
  align-items: center;
  flex-direction: column;
}

.social {
  font-size: 1.9rem;
  display: flex;
  align-self: stretch;
}

.social ul {
  display: grid;
  gap: 1rem;
  grid-template: repeat(2, 1fr) / repeat(2, 1fr);
}

.social ul li {
  background: var(--green);
  width: 45px;
  overflow: hidden;
}

.social ul li a {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  color: rgba(255, 255, 255, 0.9);
  transition: background-color ease-in 130ms;
}

.social ul li a:hover {
  background: var(--green-darken);
}
</style>
