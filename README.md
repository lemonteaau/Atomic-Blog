# React Context API Learning Project

This project is a simple application built to demonstrate the usage of the Context API in React. The Context API provides a way to manage and share state across multiple components without the need for prop drilling.

## Project Structure

The project consists of two main files:

1. `App.js`: This file serves as the entry point of the application and contains the main component.
2. `PostContext.js`: This file defines the `PostContext` and provides the `PostProvider` component and the `usePosts` custom hook.

## Features

- Generating random posts: The application generates an array of random posts using the `faker` library. Each post consists of a title and a body.
- Searching posts: The application allows users to search for posts based on the entered search query. The search is performed by filtering the posts based on the title and body.
- Adding and clearing posts: Users can add new posts to the list or clear all the posts using the provided functions.

## Usage

1. Wrap the components that need access to the post data with the `PostProvider` component. This will provide the necessary context to the child components.
2. Use the `usePosts` custom hook in any component that requires access to the post data or the related functions. This hook returns an object containing the following properties:
   - `posts`: An array of searched posts based on the current search query.
   - `onAddPost`: A function to add a new post to the list.
   - `onClearPosts`: A function to clear all the posts.
   - `searchQuery`: The current search query string.
   - `setSearchQuery`: A function to update the search query.

## Example

Here's an example of how to use the `PostProvider` and `usePosts` in a component:

```jsx
import { PostProvider, usePosts } from "./PostContext";

function App() {
  return (
    <PostProvider>
      <div>
        <SearchBar />
        <PostList />
        <AddPostForm />
        <ClearPostsButton />
      </div>
    </PostProvider>
  );
}

function SearchBar() {
  const { searchQuery, setSearchQuery } = usePosts();

  return (
    <input
      type="text"
      value={searchQuery}
      onChange={(e) => setSearchQuery(e.target.value)}
      placeholder="Search posts..."
    />
  );
}

function PostList() {
  const { posts } = usePosts();

  return (
    <ul>
      {posts.map((post, index) => (
        <li key={index}>
          <h3>{post.title}</h3>
          <p>{post.body}</p>
        </li>
      ))}
    </ul>
  );
}

// ... other component implementations ...
```

In this example, the `App` component wraps its child components with the `PostProvider`. The `SearchBar` component uses the `usePosts` hook to access the `searchQuery` and `setSearchQuery` functions, while the `PostList` component uses the hook to access the `posts` array.

## Conclusion

This project demonstrates the basic usage of the Context API in React to manage and share state across components. By utilizing the `PostContext` and the `usePosts` custom hook, you can easily access and manipulate the post data in any component that needs it, without the need for prop drilling.
