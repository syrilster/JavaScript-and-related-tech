## HTTP Requests in react
* Using axios library: https://github.com/axios/axios to make a HTTP Ajax request in the componentDidMount() method
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
* **componentDidUpdate()** method to make call to HTTP requests in case of any updation of the components.
**Note that if the state is updated in this method then it's going to cause a infinite loop of render() calls.** Hence make the HTTP calls with some conditional logic.
* Post data to server:
  ```
  postDatahandler = () => {
    const postData = {
      title: this.state.title,
      body: this.state.content,
      author: this.state.author
    };
    
    axios
      .post("https://jsonplaceholder.typicode.com/posts", postData)
      .then(response => {
        console.log(response);
      });
  };
  ```
* Delete data using:
    ```
    deletePostHandler = () => {
    axios
      .delete("https://jsonplaceholder.typicode.com/posts/" + this.props.id)
      .then(response => {
        console.log(response);
      });
    };
    ```
* Using catch block to handle errors:
    ```
    .catch(error => {
        this.setState({
          hasError: true
        });
      });
    ```
* Using interceptors to globally modify/capture the actual request:
    ```
    axios.interceptors.request.use(
      request => {
        console.log(request);
        return request;
      },
      error => {
        console.log(error);
        return Promise.reject(error);
      }
      );

  axios.interceptors.response.use(
    response => {
      console.log(response);
      return response;
    },
    error => {
      console.log(error);
      return Promise.reject(error);
    }
  );
    ```
