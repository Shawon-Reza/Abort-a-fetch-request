# Abort-a-fetch-request

```jsx
 useEffect(() => {
    const controller = new AbortController();

    fetch('https://api.example.com/data', {
      signal: controller.signal,
    })
      .then(res => res.json())
      .then(data => console.log(data))
      .catch(err => {
        if (err.name === 'AbortError') {
          console.log('Request was aborted');
        }
      });

    // Abort fetch after 2 seconds
    const timeout = setTimeout(() => {
      controller.abort();
    }, 2000);

    // Cleanup on unmount
    return () => {
      clearTimeout(timeout);
      controller.abort();
    };
  }, []);
