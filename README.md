# Cloud Native Reference Architecture

The [CNCF](https://www.cncf.io/) Cloud Native Reference Architecture site is hosted at [https://architecture.cncf.io/](https://architecture.cncf.io/) and is intended to be used as a reference for common cloud native architectures.


## Getting started

If you'd like to help with the site we'd love to have your contributions! 

## License

All code contributions are under the Apache 2.0 license. Documentation is distributed under CC BY 4.0.

## Setting up a local instance

To improve the site itself, install a local copy with these instructions. Note you must have [npm](https://www.npmjs.com/) and [Hugo](https://gohugo.io/) installed.

```sh
git clone https://github.com/cncf/architecture.git
npm install
```

You can then run the site using `npm run serve` (select "[Hugo]"). To have the site run locally with a functioning local search, run `npm run serve:with-pagefind`.
