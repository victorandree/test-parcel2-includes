# test-parcel2-includes

> Demonstrates that included files don't ~~cause a rebuild or~~ cache invalidation

This repository has a single `index.pug` file
which includes `include.pug`.

At least for the Parcel 1 pug transformer,
the cases listed below would work.

## ~~Updating `include.pug` doesn't trigger a rebuild~~

**Note:**
[parcel@v2.0.0-alpha.3.2](https://www.npmjs.com/package/parcel/v/2.0.0-alpha.3.2)
does seem to trigger a rebuild
when the included file changes.
However, the cache is not invalidated.

---

When running `watch`, updating `include.pug` doesn't trigger a rebuild.

```shell
$ npx parcel watch index.pug
Built in 1.32s.

dist/index.html    133 B    293ms
└── index.pug      133 B    458m
```

Touching `index.pug` triggers a rebuild,
whereas making changes to `include.pug` doesn't.

## Changes made to `include.pug` don't invalidate the cache for `index.pug`

Running a build and then changing `include.pug`
won't result in a new `index.html` file.
It seems like the cache for `index.pug` hasn't been invalidated.
