title: React summary
tags:
- React
- ES6
categories:
- Frontend
- React
date: 2017-07-04 11:19:12
---

![React](/img/logo_small_2x.png)

## [Codeschool React summary](https://www.codeschool.com/courses/powering-up-with-react) of [React](https://facebook.github.io/react/).

** React is a Javascript library for building UIs. **
** Why React? **
React was built to solve one problem: building large
applications with data **that changes over time**.

**Code of this post:**
{% githubCard user:Luisangonzalez repo:codeschool-react-tutorial %}

React is a [Component-based Architecture](https://en.wikipedia.org/wiki/Component-based_software_engineering), these component uses [virtual-DOM](https://en.wikipedia.org/wiki/React_(JavaScript_library)#Virtual_DOM).
React support [ES6 with babel](https://babeljs.io/blog/2015/06/07/react-on-es6-plus).



* ### Structure & scaffolding

There are different ways:

  1. The best way is Uses [Creact React App](https://facebook.github.io/react/blog/2016/07/22/create-apps-with-no-configuration.html)
  2. Import librarys in html, for example this Structure:

  ```html
  project
  │   index.html  
  │
  └───vendors
  │   │   react.js
  │   │   react-dom.js
  │   │   babel.js

  // In html file:

  <!DOCTYPE html>
  <html>
    <body>
      <script src="vendors/react.js"></script>
      <script src="vendors/react-dom.js"></script>
      <script src="vendors/babel.js"></script>
      <script type="text/babel" src="components.js"></script>
    </body>
  </html>
  ```

* ### First React component
A component in React works similarly to Javascript functions: It generates an output every time it is invoked.

  * component.js
    ```jsx

    // Component
    class FirstReactComponent extends React.Component {
      render() {
        return( <div>Hello World!!</div> );
      }
    }

    // Render component
    ReactDom.render(
      <FirstReactComponent />, document.getElementById('root-app');
    );
  ```
  * index.html
```html
<!DOCTYPE html>
<html>
  <body>
      <div id="root-app"></div>
  </body>
</html>
```


  * ### JSX (Javascript XML) is a new markup to write React apps.
      * Markup looks similar to HTML, but ultimately gets transpiled to JavaScript function calls, which React will know how to render to the page.
      * Code written within curly braces is interpreted as literal JavaScript.
      * It is a common pattern to map arrays to JSX elements.
      ```jsx
      // Component
      class FirstReactComponent extends React.Component {

        const now = new Date();

        render() { // The class in JSX is className
          return( <div className="hello">Hello World at { now.toTimeString() }</div> );
                                                  // Code written in curly braces
                                                  // gets interpreted as literal js.
        }
      }

      // Render component
      ReactDom.render(
        // React component are written in upper camel case
        <FirstReactComponent />, document.getElementById('root-app');
      );
      ```


* ### Cominication between Component

  For example create two components: coment-box (parent) and comment (child), in html:
  ```html
  <div class="comment-box"> <!-- Parent component: ComentBox -->
    <h3>Comments</h3>
    <h4 class="comment-count">2 comments</h4>
    <div class="comment-list">

      <!--Child Component: Comment  -->
      <div class ="comment">
        <p class ="comment-header">Anne Droid</p>
        <p class ="comment-body">
          I wanna know what love is...
        </p>
        <div class ="comment-footer">
          <a href="#" class ="comment-footer-delete">
            Delete comment
          </a>
        </div>
      </div>
      <!--Child Component: Comment  -->

    </div>
  </div><!-- Parent component: ComentBox -->
  ```
  Write **Comment** component:
  ```jsx
  class Comment extends React.Component {
    render() {
      return(
        <div className ="comment">
          <p className ="comment-header">Anne Droid</p>
          <p className ="comment-body">
          I wanna know what love is...
          </p>
          // class becomes className in JSX
          <div className ="comment-footer">
            <a href="#" className ="comment-footer-delete">
              Delete comment
            </a>
          </div>
        </div>
      );
    }
  }  
  ```
  Write the **CommentBox** Component:
  ```jsx
    class CommentBox extends React.Component {
      render () {
        return (
          <div className="comment-box"> <!-- Parent component: ComentBox -->
            <h3>Comments</h3>
            <h4 className="comment-count">2 comments</h4>
            <div className="comment-list">
              // Child Component: Comment
              <Comment />
              <Comment />
            </div>
          </div>// Parent component: ComentBox
        );
      }
    }
  ```
  * #### Arguments in components --> [Props](https://facebook.github.io/react/docs/components-and-props.html)
      * ##### Accept Arguments:
      In child component `Comment` add props: *author and body props*.
          ```jsx
          class Comment extends React.Component {
            render() {
              return(
                <div className ="comment">       <!-- Reading the autor prop (argument) -->
                  <p className ="comment-header">{this.props.author}</p>
                  <p className ="comment-body">
                    // Reading the body prop (argument)
                    {this.props.body}
                  </p>
                  // class becomes className in JSX
                  <div className ="comment-footer">
                    <a href="#" className ="comment-footer-delete">
                      Delete comment
                    </a>
                  </div>
                </div>
              );
            }
          }  
          ```

      * ##### Use props in the component
      Write the **CommentBox** Component with `<Comment />` component in JSX and parsing props:
      ```jsx
        class CommentBox extends React.Component {
          render () {
            return (
              <div className="comment-box"> <!-- Parent component: ComentBox -->
                <h3>Comments</h3>
                <h4 className="comment-count">2 comments</h4>
                <div className="comment-list">

                  // Passing Arguments to child Component: Comment
                  <Comment author="Morgan Serrano" body="Yeah!!" />
                  <Comment author="Bending González" body="Ohou Yeah!!" />

                </div>
              </div>// Parent component: ComentBox
            );
          }
        }
      ```
      * ##### Example dynamics props && use Unique keys to improve performance:
      ```jsx
      class CommentBox extends React.Component {
        render () {
          // get comments
          const comments = this._getComments();

          return (
            <div className="comment-box"> <!-- Parent component: ComentBox -->
              <h3>Comments</h3>
              <h4 className="comment-count">2 comments</h4>
              <div className="comment-list">

                // JSX knows how render arrays
                {comments}

              </div>
            </div>// Parent component: ComentBox
          );
        }

        _getComments() {

          const commentList = [
            { id: 1, author: 'Morgan McCircuit', body: 'Great picture!' },
            { id: 2, author: 'Bending Bender', body: 'Excellent stuff' }
          ];

          return commentList.map(( comment) => {
            return (                                             // add id in key to improve
              <Comment author={comment.author} body={comment.body} key={comment.id} />
          );
        });
      }
    }
    ```
  * #### Handling Data Changes With [State](https://facebook.github.io/react/docs/state-and-lifecycle.html)
    In React, we don’t modify the DOM directly. Instead, we modify a component state object in
    response to user events and let React handle updates to the DOM.
    The state is a vital part of React apps, making user interface interactive.
    **Events --> Update state --> DOM updates**

    * **Important on State:**
      * State represents data that changes over time.
      * We declare an *initial state* in the component constructor.
      * We update state by calling this.setState();
      * Calling *this.setState()* causes our component to re-render.

      ```jsx
      class CommentBox extends React.Component {

        // We set the initial state of our comments
        // in the class constructor
        constructor {
          // super() must be called in our constructor
          super();

          this.state = {
            showComments = false;
          }
        }

        render () {
          // get comments
          const comments = this._getComments();

          // Create list of comment if state is true
          let commentNodes;

          if (this.state.showComments){
            commentNodes = <div className="comment-list">{comments}</div>;
          }

          // button text based on component state
          let buttonText = 'Show comments';
          if (this.state.showComments) {
            buttonText = 'Hide comments';
          }

            return (

              <div className="comment-box">
              // Button that will togle state on click event
              // Important bind context
              <button onClick={this._handleClick.bind(this)}>{buttonText}</button>

                <h3>Comments</h3>
                <h4 className="comment-count">{this._getCommentsTitle(comments.length)}</h4>
                {commentNodes}
              </div>
            );
          }

          _handleClick() {
                // change state with setState method
            this.setState({  showComments: !this.state.showComments; });
          }

          _getComments() {

            const commentList = [
              { id: 1, author: 'Morgan McCircuit', body: 'Great picture!' },
              { id: 2, author: 'Bending Bender', body: 'Excellent stuff' }
            ];

            return commentList.map(( comment) => {
              return (                                            // add id in key
                <Comment author={comment.author} body={comment.body} key={comment.id} />
            );
          });
        }
      }
      ```
  * #### [SyntanticEvents](https://facebook.github.io/react/docs/events.html) and [Refs](https://facebook.github.io/react/docs/refs-and-the-dom.html)
  Capture DOM events, for example submit in form.
  In order to ensure events have consistent properties across different browsers, React wraps the browser’s native events into synthetic events, consolidating browser behaviors into one API.

    **Quick Recap:**

      * We use React’s event system to capture user input, including form submissions and button clicks.
      * [Refs](https://facebook.github.io/react/docs/refs-and-the-dom.html) allow us to reference DOM elements in our code after the component has been rendered.
      * Parent components can pass callback functions as props to child components to allow two-way
        communication.
      * [SyntanticEvents](https://facebook.github.io/react/docs/events.html) are a cross-browser wrapper around the browser’s native event.

    Create Component **CommentForm**:

      ```jsx
        class CommentForm extends React.Component {
          render() {
            return (
              <form className="comment-form" onSubmit={this._handleSubmit.bind(this)}>
                          // OnSubmit: Add on event listener to the sumbit even
                          // Important, bind thi
                <label>Join the discussion</label>
                <div className="comment-form-fields">
                                          // We will use these refs to access value from
                                          // inputs elements
                  <input placeholder="Name:" ref={(input) => this._author = input}/>
                  <textarea placeholder="Comment:" ref={(textarea) => this._body = textarea}>
                  </textarea>
                </div>
                <div className="comment-form-actions">
                  <button type="submit">Post comment</button>
                </div>
              </form>
            );
          }
          _handleSubmit(event) {
            // Prevents page from reloading
            event.preventDefault();
            let author = this._author;
            let body = this._body;

            // This method has been passed as an argument to use in parent component (CommentBox)
            this.props.addComment(author.value, body.value);
          }          
        }
      ```
      Using CommentForm to Add Comments:

      ```jsx
      class CommentBox extends React.Component {

        constructor {
          // super() must be called in our constructor
          super();

          this.state = {
            showComments = false;
            // Now part of the component's state
            comment = {
              id: this.state.comments.length + 1,
              author,
              body
            };
          }
        }

        render () {
          return (
            <div className="comment-box">
                <CommentForm addComment={this._addComment.bind(this)} />
                  // Using the newly created CommentForm component
            </div>
          );
        }

        _addComment(author, body) {
          const comment = {
            id: this.state.comments.length + 1,
            author,
            body
          };

          // New array references help React stay fast.
          // So concat works better than push here.
          this.setState({ comments: this.state.comments.concat([comment]) });
          // Updates state when function is called by adding new comment
        }

        _getComments() {

                  // Reading from comment's state
          return this.state.comments.map(( comment) => {
            return (
              <Comment author={comment.author} body={comment.body} key={comment.id} />
          );
        });
      }
    }
    ```

* ### **Using Lifecycle Methods to Load Comments** & Talking remote server

  First all one, is important understand **React's Lifecycle Methods**:

  Lifecycle methods in React are functions that get called while the component is rendered for the first time or about to be removed from the DOM.

    * constructor()
    * **componentWillMount()** method is called **before** the component is rendered to the page.
    * render()
    * **componentDidMount()** is called after the component is rendered.
    * **componentWillUnmount()** is called immediately before the component is removed from the DOM.

  Note: In React, **mounting** means rendering for the first time.
  [More info in facebook docs](https://facebook.github.io/react/docs/react-component.html#the-component-lifecycle)



  * #### Load data component with fetch data
    To load data, use [fetch](https://developer.mozilla.org/es/docs/Web/API/Fetch_API/Utilizando_Fetch) and this method is call in **componentWillMount()** method before render().

    ```jsx
      class CommentBox extends React.Component {
        constructor() {
          super();
          this.state = {
            showComments: false,
            comments: [] // Initialed to an empty array
          };
        }
        // call fetch comments in componentWillMount Lifecycle
        componentWillMount() {
          this._fetchComments();
        }
        // fetch comment
        async _fetchComments() {
          try {
            let response = await fetch('comments.json');
            let comments = await response.json();
            this.setState({ comments })
          } catch(error) {
            console.log(error);
          }
        }

      }
    ```
      * ##### Getting Periodic Updates
      In order to check whether new comments are added, we can periodically check the server for updates. This is known as polling.

      ```jsx
        class CommentBox extends React.Component {
          ...
          componentDidMount() {
            setInterval(() => this._fetchComments(), 5000);
          }
        }
      ```
      React optimizes the rendering process by only updating the DOM when changes are detected on the resulting markup.
        * New state value after inital request --> DOM change happens
        * No new state value after second periodic Ajax request --> No DOM change
        * New state value after third periodic Ajax request --> DOM change happens

      * ##### Memory Leaks on Page Change
      Page changes in a single-page app environment will cause each CommentBox component to keep loading new comments every five seconds, even when they are no longer displayed.
        * **Preventing Memory Leaks**
        Each component is responsible for removing any timers it has created. We will remove the timer on the componentWillUnmount method.
        ```jsx
          class CommentBox extends React.Component {
            ...
            componentDidMount() {
              // Store timer as object property
              this._timer = setInterval(
                () => this._fetchComments(),
                5000
              );
            }
            // Run when component is about to be removed from the DOM
            componentWillUnmount() {
              clearInterval(this._timer);
            }
            ...
          }
        ```
        **Reviewing the steps for loading Comments**
          1.  componentWillUnmount is called.
          2.  render() is called and CommentBox is mounted.
          3.  Component waits for API response and when it is received, setState() is called, causing render() to be called again.
          4.  componentDidMount is called, causing this _fetchComments to be triggered    
* ### Routes
      React not including routing, is necessary routes dependencies, for example react-router and react-router-dom.

      In this example use this versions:
          *  "react": "^15.6.1",
          *  "react-dom": "^15.6.1",
          *  "react-router": "^4.1.1",
          *  "react-router-dom": "^4.1.1"

      This example is [other project](https://github.com/Luisangonzalez/react-proof):

      {% githubCard user:Luisangonzalez repo:react-proof %}

      The scaffolding:

        ```
        project
        │
        └───public
        │   │   favicon.ico
        │   │   index.html
        │   │   manifest.json
        └───src
        │   │__home
        |   |   |_home.js
        |   |
        │   │__login
        |   |   |_login.js
        |   |
        │   │__register
        |       |_register.js
        |
        |__App.js
        |
        |__index.js
        ```

        In index.js import react-dom and use BrowserRouter to route the component App:

        ```jsx
        import React from 'react';
        import { BrowserRouter } from 'react-router-dom'
        import ReactDOM from 'react-dom';
        import App from './App';

        ReactDOM.render((
          <BrowserRouter>
            <App />
          </BrowserRouter>
        ), document.getElementById('root'));
        ```
        The componnet App.js have other componnet to routing:

        ```jsx
        import React from 'react';
        import { Route, Switch, Link } from 'react-router-dom'

        import './App.css';

        import Home from './home/home';
        import Login from './login/login';
        import Register from './register/register';

        const Main = () => (
          <main>
            <Switch>
              <Route exact path='/' component={Home}/>
              <Route path='/login' component={Login}/>
              <Route path='/register' component={Register}/>
            </Switch>
          </main>
        )

        // The Header creates links that can be used to navigate
        // between routes.
        const Header = () => (
          <header>
            <nav>
              <ul className="navigation">
                <li><Link to='/'>Home</Link></li>
                <li><Link to='/login'>Login</Link></li>
                <li><Link to='/register'>Register</Link></li>
              </ul>
            </nav>
          </header>
        )

        // Componet App to routing
        class App extends React.Component {
          render() {
            return (
              <div>
                <Header />
                <Main />
              </div>
              )
          }
        }

        export default App;
        ```

**And it is all, any question please write me ;)**
