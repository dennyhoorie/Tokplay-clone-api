# Tokplay (Backend)

Tokplay-clone-api (Backend) is a server for Tokopedia Play clone.

## Features

Required:

- Video Thumbnail List
- Product List
- Comment List
- Submit Comment

Additional:

- Insert video
- Get a video
- Insert product

## How to install & run project

Initialize a Node.js project and generates a package.json file with default values. Type the following code in the terminal.

```bash
npm init -y
```

The `-y` automatically answers "yes" to all requests during the initialization process, so you do not need to enter configuration options manually.

Use `npm` to install packages needed

```bash
npm i express mongoose body-parser cors dotenv express nodemon
```

To run this program, follow these steps:

```bash
npm start
```

The second option required this command in package.json, inside the `scripts`:

```bash
"start": "node index.js"
```

## Environment Variables

```bash
DATABASE_URL=mongodb://127.0.0.1:27017/tokopedia_play
PORT=3080
```

## How to run features

The server should start running on the specified port (e.g., `localhost:3080`).

### Video object

```bash
{
    videoID: integer,
    thumbnail: string
}
```

### GET /api/all-videos

Returns all videos from the database.

- URL Params<br>none
- Success response:<br>
  Code: 200<br>
  Content:

```bash
{
    "data": [
        {
            {<video_object>},
            {<video_object>},
            {<video_object>}
        }
    ]
}

```

### Product object

```bash
{
    videoID: integer,
    productID: integer,
    productUrl: string,
    title: string,
    price: integer
}
```

### GET /api/products/:videoID

Returns all products related to video clicked.

- URL Params<br>http://localhost:3080/api/products/1
- Data Params<br>none

- Success response:<br>
  Code: 200<br>
  Content:

```bash
{
    "success": true,
    "data": [
        {<product_object>}
    ]
}

```

### Comment object

```bash
{
    videoID: integer,
    username: string,
    comment: string,
    timestamp: datetime
}
```

### GET /comments/:videoID

Returns all comments related to video detail.

- URL Params<br>http://localhost:3080/api/comments/1
- Data Params<br>none

- Success response:<br>
  Code: 200<br>
  Content:

```bash
{
    "success": true,
    "data": <comment_object>,
    "message": "get comment successfully!"
}
```

### POST /upload-comment/:videoID

Returns submit status.

- URL Params<br>http://localhost:3080/api/upload-comment/1
- Data Params<br>

```bash
{
    "username":"dennyhoorie",
    "comment": "This product is cool. Any other colors available?"
}
```

- Success response:<br>
  Code: 200<br>
  Content:

```bash
Success
```

- Failed response:<br>
  Code: 500

```bash
Fail
```

#### Additional features:

### POST /insert-video

Returns video data that just created.

- URL Params<br>http://localhost:3080/api/insert-video
- Data Params<br>

```bash
{
    "videoID":5,
    "thumbnailUrl":"thumbnailUrl5"
}
```

- Success response:<br>
  Code: 200<br>
  Content:

```bash
    <video_object>
```

### GET /one-video/:videoID
Returns a video data after a video be clicked in homepage.

- URL Params<br>http://localhost:3080/api/one-video/1
- Data Params<br>
{
    "videoID":3
}

- Success response:<br>
  Code: 200<br>
  Content:

```bash
{
    "success": true,
    "message": "Get video detail success!",
    "data": [
        <video_object>
    ]
}
```

### POST /insert-product
Returns product data that just created.

- URL Params<br>http://localhost:3080/api/insert-product
- Data Params<br>

```bash
{
    "productID":5,
    "productUrl": "productUrl5",
    "title":"title5",
    "price": 10000
}
```

- Success response:<br>
  Code: 200<br>
  Content:

```bash
{
    "success": true,
    "data": <video_object>,
    "message": "new product uploaded successfully!"
}
```

## Database Structure

### Video collection

```bash
[
    {
      "_id": <mongoDB ObjectId>,
      "videoID": integer,
      "thumbnailUrl": string
    }
]
```

### Product collection

```bash
[
    {
        "_id": <mongoDB ObjectId>,
        "videoID": integer,
        "productID": string,
        "productUrl": string
        "title": string,
        "price": integer
    }
]
```

### Comment collection

```bash
[
    {
      "_id": <mongoDB ObjectId>,
      "videoID": integer,
      "username": string,
      "comment": string,
      "timestamp": datetime
    }
]
