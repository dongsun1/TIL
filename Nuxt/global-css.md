# Nuxt에 Global CSS 적용하는 법

1. 먼저 nuxt.config.js에 원하는 폰트 링크를 추가한다.

```javascript
link: [
      ...,
      {
        ref: "stylesheet",
        type: "text/css",
        href: "https://fonts.googleapis.com/css2?family=Hi+Melody&display=swap",
      },
    ],
```

2. assets/fonts/global.css 파일만들어 CSS를 적용한다.

```javascript
@import url("https://fonts.googleapis.com/css2?family=Hi+Melody&display=swap");

body {
  font-family: "Hi Melody", cursive;
}
```

   

