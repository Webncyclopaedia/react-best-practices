# React best practices
The place where react best practices found their home.

## Hooks
 
<details>
<summary>useDebounce</summary>
 
```js
const useDebounce = (callback, delay) => {
  const timer = useRef();

  const debouncedCallback = useCallback(
    (...args) => {
      if (timer.current) {
        clearTimeout(timer.current);
      }
      timer.current = setTimeout(() => {
        callback(...args);
      }, delay);
    },
    [callback, delay]
  );

  return debouncedCallback;
};
```

</details>
