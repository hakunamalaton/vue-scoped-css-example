# Introduction
This repository explains the `scoped CSS` in Vue with intuitive examples
References on Vue official documentation: https://vuejs.org/api/sfc-css-features.html#scoped-css

There is one example for each section:
- Child Component Root Elements
- Deep Selectors
- Slotted Selectors
- Global Selectors
- Mixing Local and Global Styles
- [Bonus] Scoped Style Tips

## Child Component Root Elements
From Vue documentation:

> With scoped, the parent component's styles will not leak into child components. However, a child component's root node will be affected by both the parent's scoped CSS and the child's scoped CSS. This is by design so that the parent can style the child root element for layout purposes.
