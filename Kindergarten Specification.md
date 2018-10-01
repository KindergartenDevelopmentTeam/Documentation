# Kindergatren App Specification

## Kindergarten backend

### Endpoints

- `/createGroup` `POST`
- `/group/{groupId}` `GET` 
  - `/addTeacher` `POST`
  - `/removeTeacher` `POST`
  - `/addChild` `POST`
  - `/removeChild` `POST`
  - `/deleteGroup` `POST`
  - `/getParents` `GET`
  - `/getTeachers` `GET`
  - `/getUsers` `GET` = `getTeachers` + `getParents`
  - `/getChildren` `GET`
  - `/getPosts` `GET`
  - `/post/{postId}` `GET`
    - `/like` `GET` or `POST`?
    - `/comment` `POST`
    - `/vote` `POST`
    - `/edit` `POST`
  - `/createPost` `POST`
  - `/getMessages` `GET`
  - `/sendMessage` `POST`
- `/user/{parentId}` `GET`
  - `/sendMessage` `POST`
  - `/getMessages` `GET`
- `/child/{childId}` `GET`
  - `/addNote` `POST`
  - `/getNotes` `GET` <-- same as posts, but not in group?
  - `/edit` `POST`, only parent
  - `/editPresence` `POST`
  - `/setParent` `POST`
- `/createChild` `POST`

### Socket.io Endpoints

- `/user/{userId}/messages`
- `/group/{groupId}/posts`
- `/group/{groupId}/post/{postId}`
- `/group/{groupId}/messages`

### Entities

- `Group`

  ```json
  {
      "id": Int
      "name": String,
      "posts": List<Post>,
      "teachers": List<User>,
      "children": List<Child>,
      "messages": List<Message>,
      "creationDate": Date
  }
  ```

- `Post`

  ```json
  {
      "id": Int,
      "createor": User,
      "content": String,
      "image": Image?,
      "poll": Poll?, // Todo heterogen collection?
      "likes": List<Like>,
      "comments": List<Comment>,
      "creationDate": Date
  }
  ```

- `Comment`

  ```json
  {
      "id": Int,
      "creator": User,
      "content": String,
      "creationDate": Date
  }
  ```

- `User`

  ```json
  {
      "id": Int,
      "name": String,
      "role": Role
  }
  ```

- `Child`

  ```json
  {
      "id": Int,
      "name": String,
      "parent": User,
      "presence": List<Presence>, // TODO better name
      "notes": List<Note>
  }
  ```

- `Message`

  ```json
  {
      "id": Int,
      "content": String,
      "creationDate": Date
  }
  ```

- `Note`

  ```json
  {
      "id": Int,
      "content": String
  }
  ```

- `Presence`

  ```json
  {
      "id": Int,
      "wasThere": Boolean,
      "date": Date
  }
  ```

- `Image`

  ```json
  {
      "id": Int,
      "path": Stirng
  }
  ```

- `Poll`

  ```json
  {
      "id": Int,
      "options": List<String>,
      "votes": List<Vote>
  }
  ```

- `Like`

  ```json
  {
      "id": Int,
      "user": User,
      "creationDate": Date
  }
  ```

- `Date`

  Built in date format

- `Role`

  ```json
  {
      "id": Int,
      "name": String
  }
  ```

### Database



## TODO

- `Role` class or separate `Admin`, `Teacher` and `Parent` classes
- https://editor.swagger.io/

- https://www.justinmind.com/



- képernyőterv

- arch design