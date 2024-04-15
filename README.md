# Canny Debugging Test

Howdy Candidate, we've created this pared down version of Canny to get a better idea of your experience debugging web applications. Best of luck!

## Getting Started

1. **Initialize your environment**

We recommend using nvm for managing node versions.

Install nvm from [here](https://github.com/creationix/nvm)

Then install the node version for this assessment:

```sh
nvm i
```

1. **Install dependencies**

Next you'll need to install this app

```sh
npm install
```

1. **Run the backend**

The backend is a node server. Everything to do with the server lives in `/server`.

Terminal tab #1:

```sh
npm run backend
```

1. **Run the frontend**

Webpack is used to bundle and serve our app. Everything to do with the frontend lives in `/app`.

Terminal tab #2:

```sh
npm run frontend
```

Once everything is running, you should see the app running http://127.0.0.1:8080.

## Customer Issues

For each of the following issues:

1. Identify the issue
1. Apply the fix
1. Provide a response to each technical customer in 1-2 sentences

**Customer 1:** When I open the application, my posts do not load and all I see is a 'server error'.

**Fix:** The issue was caused by a typo in the code. In the `authenticateUser` function, the condition `!userData.nayme` was used instead of `!userData.name`.

**Response:** We apologize for the inconvenience caused by the server error. The issue has been resolved, and your posts should now load properly when you open the application. Please let us know if you encounter any further problems.

**Customer 2:** When I click on "Top" or "Old", the selector does not update with my new selection.

**Fix:** Added `selectedSort` to the component's state to track the current sorting option. Used `selectedSort` from the state in the render method to determine the selected option.

**Response:** We have fixed the issue with the selector not updating when clicking on 'Top' or 'Old'. The selector will now correctly display the selected option. Please refresh the page and try again. If you still experience any problems, please let us know.


**Customer 3:** When I sort by "Top", there are posts with only 28 votes ranking higher than posts with 180 votes!
**Fix:** The issue was caused by the `sortBy` function not correctly sorting the posts based on their numeric vote counts. The sortBy function likely treated the `votes` property as a string and sorted the posts alphabetically. The fix was to replace `sortBy` with a custom sorting function `Posts.slice().sort((a, b) => b.votes - a.votes)` that compares the 'votes' property of two posts, ensuring proper sorting in descending order.
**Response:** We apologize for the confusion caused by the incorrect sorting of posts when selecting the 'Top' option. We have resolved the issue, and posts are now properly sorted based on their vote counts. The posts with the highest number of votes will appear at the top. Please try sorting by 'Top' again, and let us know if you have any further problems.

**Customer 4:** When I page through posts, although the posts are changing, the vote count in the top left corner does not match the total count of votes of the displayed posts.
**Fix:** The issue was caused by not updating the vote count after fetching posts when paging or changing the sorting option. The fix involved dispatching the `recountVotes` action after the `fetchPosts` action is completed in both the `PostList` component's `getPosts` method and the `PostSort` component's `changeSort` method.
**Response:** We apologize for the inconvenience caused. We have resolved the issue with the vote count in the top left corner not matching the total count of votes of the displayed posts when paging through posts. The vote count will now be updated correctly after each page change. Please try navigating through the pages again, and you should see the vote count accurately reflecting the total votes of the visible posts. If you encounter any further problems, please let us know.

## 🎉 You're Done 🎉

Congrats on completing our assessment. All that is left for you to do is submit your assessment. We made a command that will zip your submission and send it to us. Send us an email to confirm that we got it.

```sh
npm run submit
```
