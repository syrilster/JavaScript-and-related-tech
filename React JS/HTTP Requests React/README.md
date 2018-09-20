## HTTP Requests in react
* Using axios library: https://github.com/axios/axios to make a HTTP ajax request in the componentDidMount() method
* Make fake requests using https://jsonplaceholder.typicode.com/
  ```
  state = {
    posts: []
  };

  componentDidMount() {
    const posts = axios
      .get("https://jsonplaceholder.typicode.com/posts")
      .then(response => {
        this.setState({
          posts: response.data
        });
      });
  }
  ```
