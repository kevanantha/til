# In Rust, What Is The Purpose Of A `mod.rs` File?

Generally, it's like `index.js` in JS.

Imagine if structure folder like this:

```
code/
  - main.rs
  - something/
    - mod.rs
```

If in `main.rs` you do `mod something;` then it'll look in the file `something/mod.ts` file to use as the contents of the module declaration for `something`.

> _NOTE:_ this `mod something;` is calling a file `something.rs` in the same directory or calling a file `mod.rs` in the `something` directory

Just like JS, if you `import { anything } from './something'`, it'll look in the file `something/index.js`

Reference:
[Stackoverflow](https://stackoverflow.com/questions/26435102/in-rust-what-is-the-purpose-of-a-mod-rs-file)
