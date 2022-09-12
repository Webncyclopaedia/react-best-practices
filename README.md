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
      // Eng: We clear previous timeout and set new if callback or delay changed.
      // Ru: Мы очищаем предыдущий timeout и сеттим новый, если callback или delay поменялись.
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

<details>
<summary>useRequest</summary>
 
```js
const useRequest = (request) => {
    const [data, setData] = useState(null);
    const [loading, setLoading] = useState(false);
    const [error, setError] = useState("");

    useEffect(() => {
      setLoading(true);
      setTimeout(() => {
        request()
          .then((response) => setData(response.data))
          .catch((error) => setError(error))
          .finally(() => setLoading(false));
      }, 1000);
    }, []);

    return [data, loading, error];
};
```
</details>
