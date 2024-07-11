# vue-project

Нужно реализовать фигуру. Должен быть компонент, который можно переиспользовать на Vue2. Он принимает на вход такие параметры: MaxValue — максимальное значение (на картинке это 108), Value — актуальное значение (на картинке это 35), TargetValue — целевое значение (на картинке это 80).

Часы, которые в центре, вычисляются так: целевое — актуальное (80 — 35 = 45 ч).

После прохождения порога целевого значения (80): 
график и цифровые значения становятся зелеными вместо оранжевого;
текст “Ещё продать на завтра” пропадает ; 
по середине показывается актуальное значение из value.

Нужно сделать на Vue2. Нельзя использовать библиотеки.
Желательно делать на vue-cli или развернуть на github pages.


## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
