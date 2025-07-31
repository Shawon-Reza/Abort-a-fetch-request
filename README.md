# Abort-a-fetch-request

```jsx
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

// Abort after 2 seconds
setTimeout(() => {
  controller.abort();
}, 2000);
