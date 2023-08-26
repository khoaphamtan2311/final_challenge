# Ideas Sharing And Conversations: Gist

Gist is a social network that allows people to join by creating account with a few information. Each user should provide a username, email, and a password to create an account. The email address must be unique for every account in the system.

After joining Gist, user can update their profile info like Avatar, Given name, Apellation, Company, JobTitle, Social Links, and a short decription about themselves.

Users can write Posts which is simple with 500 characters of text to share in-the-moment updates, and the option to attach links, photos and videos. The new post will be shown on the user profile page, allow other people to leave a comment or reaction toward the post. Feed also includes creations posted by people the user follow and new creators he/she haven’t discovered yet.

Users can follow other people that they are interested or have relationship with. User can be followed by others too. User can unfollow people they are following and removed who is following them as well. Also there are communties for users to join where they can have conversations about real-time topics

## User Stories

### Authentication

- [ ] As a user, I can register for a new account with username, email, and password.
- [ ] As a user, I can sign in with my email or username and password.

### Users

- [ ] As a user, I can see a list of my followers and who I am following so that I can follow/unfollow or remove followers
- [ ] As a user, I can get my current profile (stay signed in after refreshing page).
- [ ] As a user, I can see other user profile given a user ID.
- [ ] As a user, I can update my profile info like Avatar, Given name, Apellation, Company, JobTitle, Social Links, and about me.
- [ ] As a user, I can set my account private or public to other user.

### Posts

- [ ] As a user, I post a creations with text, image or videos.
- [ ] As a user, I can repost a creation of other user to my profile.
- [ ] As a user, I can see a list of posts of myself or my followings and also other people for me to discover.
- [ ] As a user, I can edit my post.
- [ ] As a user, I can delete my post.

### Comments

- [ ] As a user, I can see a lists of comments on the post.
- [ ] As a user, I can write comment on a post.
- [ ] As a user, I can update my post.
- [ ] As a user, I can delete my post.

### Reactions

- [ ] As a user, I can like, dislike or react a post or a comment.

### Followers/Followings

- [ ] As a user, I can follow a user that Im interested in if his/her account is public.
- [ ] As a user, I can send a follow request to the account that is private.
- [ ] As a user, I can see all the following requests if my account is private and choose to accept or decline that request.
- [ ] As a user, I can see a list of my followers.
- [ ] As a user, I can see a list of my following.
- [ ] As a user, I can remove a followers from my followers list.
- [ ] As a user, I can unfollow a user that Im following.
- [ ] As a user, I can follow/unfollow a user that Im interested in.

## Endpoint APIS

### Auth APIS

```javascript
/*
 * @route POST /auth/login
 * @description Log in with username and password
 * @body { email, password }
 * @access Public
 */
```

### Users APIS

```javascript
/*
 * @route POST /users
 * @description Register new user
 * @body { name, email, password }
 * @access Public
 */
```

```javascript
/*
 * @route GET /users?page=1&limit=10
 * @description Get users with pagination
 * @access Login required
 */
```

```javascript
/*
 * @route GET /users/me
 * @description Get current user info
 * @access Login required
 */
```

```javascript
/*
 * @route GET /users/:id
 * @description Get a user profile
 * @access Login required
 */
```

```javascript
/*
 * @route PUT /users/:id
 * @description Update user profile
 * @body { avatarUrl, givenName, apellation, company, city, country, jobTitle, facebookLink, instagramLink, linkedinLink,  twitterLink, aboutMe}
 * @access Login required
 */
```

```javascript
/*
 * @route PUT /users/:id/status
 * @description Change account status
 * @body { status: 'private' or 'public' }
 * @access Login required
 */
```

### Posts APIS

```javascript
/*
 * @route GET /posts/user/userId?page=1&limit=10
 * @description Get all posts an user can see with pagination
 * @access Login required
 */
```

```javascript
/*
 * @route POST /posts
 * @description Create a new post
 * @body { content, image, video}
 * @access Login required
 */
```

```javascript
/*
 * @route PUT /posts/:id
 * @description Update a post
 * @body { content, image, video}
 * @access Login required
 */
```

```javascript
/*
 * @route DELETE /posts/:id
 * @description Delete a post
 * @access Login required
 */
```

```javascript
/*
 * @route GET /posts/:id
 * @description Get a single post
 * @access Login required
 */
```

```javascript
/*
 * @route GET /posts/:id/comments
 * @description Get comments of a post
 * @access Login required
 */
```

```javascript
/*
 * @route GET /posts/:id/reactions
 * @description Get reactions of a post
 * @access Login required
 */
```

### Comments APIS

```javascript
/*
 * @route POST /comments
 * @description Create a new comment
 * @body { content, imageUrl, postId}
 * @access Login required
 */
```

```javascript
/*
 * @route PUT /comments/:id
 * @description Update a comment
 * @body { content, imageUrl }
 * @access Login required
 */
```

```javascript
/*
 * @route DELETE /comments/:id
 * @description Delete a comment
 * @access Login required
 */
```

### Reactions APIS

```javascript
/*
 * @route POST /reactions
 * @description Save a reaction to post or comment
 * @body { targetType: 'Post' or 'Comment', targetId, emoji: 'like', 'dislike', 'haha', 'wow', 'sad' }
 * @access Login required
 */
```

### Followers/Following APIS

```javascript
/*
 * @route POST /followers/requests
 * @description Send a follow request
 * @body { to: User ID}
 * @access Login required
 */
```

```javascript
/*
 * @route GET /follower/requests/incoming
 * @description Get the list of received pending requests
 * @access Login required
 */
```

```javascript
/*
 * @route GET /followers
 * @description Get the list of followers
 * @access Login required
 */
```

```javascript
/*
 * @route PUT /followers/requests/:userId
 * @description Accept/Reject a received pending requests
 * @body { status: 'accepted' or 'declined'}
 * @access Login required
 */
```

```javascript
/*
 * @route DELETE /followers/requests/:userId
 * @description Cancel a friend request
 * @access Login required
 */
```

```javascript
/*
 * @route DELETE /followers/:userId
 * @description Unfollow a user
 * @access Login required
 */
```

```javascript
/*
 * @route DELETE /followers/:userId/remove
 * @description Remove a user from following
 * @access Login required
 */
```
