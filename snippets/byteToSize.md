---
title: byToSize
tags: string, function, intermediate
firstSeen: 2021-11-13T17:14:22+02:00
---

Returns the conversion of bytes to different data measurement units.

- The constant i obtains the integer of the division of the neutral base of the number of bytes and the representation of a kilobyte using `Math.log()` and with `Math.floor()` the maximum integer.
- Math.pow()` is used to return the raised base, the number of bytes as the base and the neutral base of the constant i.
- And the result is the number of bytes divided by the raised base by concatenating the unit of measurement with the neutral base.

```js
const bytesToSize = (bytes, decimals = 2) => {
  if (bytes === 0) {
    return '0 Bytes';
  }

  const k = 1024;
  const dm = decimals < 0 ? 0 : decimals;
  const sizes = ['Bytes', 'KB', 'MB', 'GB', 'TB', 'PB', 'EB', 'ZB', 'YB'];
  const i = Math.floor(Math.log(bytes) / Math.log(k));

  return `${parseFloat(
    (bytes / Math.pow(k, i)
  ).toFixed(dm))} ${sizes[i]}`;
};
```

```js
bytesToSize(1934000); //'1.84 MB'
```
