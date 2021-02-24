<template>
  <header class="header-container radius">
    <div class="header-content">
      <figure>
        <img
          class="radius"
          src="https://randomuser.me/api/portraits/men/78.jpg"
          alt=""
        />
      </figure>

      <nav class="links">
        <ul>
          <li v-for="(e, i) in localLinks" :key="i">
            <nuxt-link class="link" :to="e.to">{{ e.text }}</nuxt-link>
          </li>
        </ul>
      </nav>

      <nav class="social">
        <ul>
          <li v-for="(e, i) in socialLinks" :key="i">
            <a :href="e.url">
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

  data() {
    return {
      localLinks: [
        {
          text: "About me",
          to: "#work"
        },
        {
          text: "Work",
          to: "#work"
        }
      ],

      socialLinks: [
        {
          icon: "bxl-github",
          url: "https://github.com/brdtheo"
        },
        {
          icon: "bxl-codepen",
          url: "https://codepen.io/theo-billardey"
        },
        {
          icon: "bxl-linkedin",
          url: "https://www.linkedin.com/in/theo-billardey/"
        },
        {
          icon: "bx-envelope",
          url: "mailto:theo.billardey@gmail.com"
        }
      ]
    };
  }
};
</script>

<style scoped>
.header-container {
  padding: 1rem;
  box-shadow: 0.2rem 0.2rem 1.4rem 2px rgba(40, 40, 40, 0.12);
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
  display: inline-block;
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
  font-size: 2.2rem;
}

.social ul li {
  margin: 0 0.4rem;
}
</style>
