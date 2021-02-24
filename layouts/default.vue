<template>
  <div>
    <Nuxt />
  </div>
</template>

<style>
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@300;400;700&display=swap");
:root {
  --black: #353b48;
  --white: #f5f6fa;
}

*,
*::before,
*::after {
  box-sizing: inherit;
  margin: 0;
  padding: 0;
}

html {
  font-size: 62.5%;
  box-sizing: border-box;
}

body {
  background: var(--black);
  color: var(--white);
  font-family: "Inter", sans-serif;
}
</style>
