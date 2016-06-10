# Font size adjust bug testcase

A test case for a bug found in how `font-size-adjust` affects flow content.

## Requirements

Node 4.x.x and above.

## Set up

```
npm install
npm start
```

## Notes on the bug

I've been testing it on Chrome, above version 44. The problem doesn't appear on Safari (9.1.1), Firefox (47.0) or Opera (38.0).

To see the bug you need to run an app which uses the new transport font (the prototype kit doesn’t by default) and set a base font on the body:

https://github.com/tombye/font-size-adjust-testcase/commit/0c04c32727eaac922e3ced85c63ffbe0983e558a

This makes the child `<div>`s of the `.footer-meta` element go out of alignment.

I think it’s because `font-size-adjust` is changing how flow content is laid out in the `.footer-meta` element, which has its child `<div>` elements set to `display: inline-block`. This is based on the fact that setting `font-size-adjust: none` on the `.footer-meta` element fixes it.

Here's the fix:

https://github.com/tombye/font-size-adjust-testcase/commit/e12cf1b37671284bff44f5fd1cd88521c56a6eea

## See the bug

https://font-size-adjust-testcase.herokuapp.com/

## See it with the fix

https://font-size-adjust-testcase-fix.herokuapp.com/

(You'll need credentials to view it, email me for them.)

## See it in the wild

### The bug

https://jsbin.com/puzarakubu/1/edit?css,output

### With a fix

https://jsbin.com/finususote/edit?css,output
