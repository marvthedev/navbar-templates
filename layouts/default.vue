<template>
  <div>
    <Nuxt />
  </div>
</template>

<style>
html {
  font-family: "Open Sans", sans-serif;
  font-size: 62.5%;
  font-weight: 300;
  color: #777777;
  word-spacing: 0;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  border: none;
}

/* Typography Defaults */
h1,
h2 {
  color: #212529;
}

h1 {
  font-weight: 700;
}

p {
  font-size: 1.7rem;
}

a {
  text-decoration: none;
  color: inherit;
}

/* Forms */
input,
textarea {
  font-family: inherit;

  /* Remove unwanted thick border-top on iOS devices */
  background-clip: padding-box;
}

textarea {
  resize: none;
  border-radius: 0;
}
</style>
