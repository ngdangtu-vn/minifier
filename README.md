# minifier

An awesome language minifier for Deno that is powered by WebAssembly!

## Docs

### Language Object

To specify your language easier, you can use the `Language` object that is exported from the library. Here is an example of passing in your language into the `minify` function:

```ts
const code = `
html {
  margin: 0;
  padding: 0;
}`;

minify(Language.CSS, code);
```

### Minifying Code

To minify any given code, simply use the `minify` function and pass in the given language as your first argument and the code as the second. The language that you need to pass in can either be the `Language` variant discussed [later on](#supported-languages), or the actual lowercase string that is your language name. Here are two examples of us minifying some CSS code:

```ts
const code = `
html {
  margin: 0;
  padding: 0;
}`;

// both return the minifed CSS
minify(Language.CSS, code);
minify("css", code);
```

### Minifying HTML

As us HTML programmers know, you can include CSS and JS inside of your HTML code. If you want to minify the CSS/JS in your HTML, the just use the `minifyHTML` function! You just pass in the code first and the options for whether you want to minify CSS and/or JS second. Here is an example:

```ts
const code = `
<html>
<head>
  <style>
    html {
      margin: 0;
      padding: 0;
    }
  </style>
  <script>
    const x = 23;
    if (x > 20) {
      x--;
    }
    console.log(x);
  </script>
</head>
</html>
`;

// returns the minified HTML code with the CSS and JS code properly minified, too
minifyHTML(code, {
  minifyCSS: true,
  minifyJS: true,
});
```

## Supported Languages

The following languages are supported for minification. You can either pass in the `Language` object variant into our various functions to specify your language or the actual string in parentheses to pick your language.

- HTML ("html")

- CSS ("css")

- JS ("js")

- JSON ("json")

## Building

To build the project, make sure that you have the Go compiler and Cargo installed. After that, you can just run the `deno run -A build.ts` to generate the corresponding files.

## License

See the [attached license](./LICENSE) for more info.
