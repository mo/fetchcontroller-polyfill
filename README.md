# FetchController "polyfill"

Minimal stubs so that FetchController API can be used. Doesn't actually close the connection when
the request is aborted, but calls ```.catch()``` with ```err.name == 'AbortError'``` instead of ```.then()```.

```js
  const controller = new FetchController();
  const signal = this.controller.signal;
  fetch('/some/url', {signal}).then(res => res.json()).then(data => {
    // do something with "data"
  }).catch(err => {
    if (err.name == 'AbortError') {
      return;
    }
  });
```

# See also

* [FetchController on MDN](https://developer.mozilla.org/en-US/docs/Web/API/FetchController)
* [PR for fetch specification](https://github.com/whatwg/fetch/pull/523)

# License

MIT
