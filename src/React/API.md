# API Call in React

- async function
- `await fetch`
- `await response.text()`
- request
  - method
  - heads
    - ```
    'Content-Type': 'application/json',
    ```
  - body
    - ```
    JSON.stringify({
    name: 'John',
    age: 30,
    }),
    ```

```JSX
const [isLoading, setIsLoading] = useState(false);
const [error, setError] = useState(null);
async function fetchData() {
    try{
        setIsLoading(true);
        setError(null);
         const response = await fetch('https://api.example.com/data',{
            method: 'GET',
            headers: {
            'Content-Type': 'application/json',
            },
            body: JSON.stringify({
            name: 'John',
            age: 30,
            }),
        });
        if(response.ok){
            setLiked(!liked)
        }
        const data = await response.json();
        return data;
    }catch(error){
        setError(error);
        console.error('Error fetching data:', error);
    } finally {
        setIsLoading(false);
    }
  const data = await response.json();
  return data;
}
```