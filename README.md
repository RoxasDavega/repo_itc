# pembelajaran_itc
---
## Installation
You need to install node v16.14.2 https://nodejs.org/en/blog/release/v16.14.2/ or latest https://nodejs.org/en/download/ \
You need to install all package with command:
```text
npm install
```
Create database MySQL with command:
```text
npx sequelize db:create
```
Create a table automatically with command:
```text
npx sequelize db:migrate
```
Insert data into tables from all seeders with command:
```text
npx sequelize-cli db:seed:all
```
You can run specific seeder with following command:
```text
 npx sequelize-cli db:seed --seed <name file.js>
```
Before start, create a .env file with contents like .env.example \
Start API with command:
```text
npm run start
```
or 
```text
npm run start-dev
```
\
For more information about sequelize check the [documentation](https://sequelize.org/docs/v6/).

## Table of Contents

- [Pembelajaran_itc](#pembelajaran-itc)
  - [Table of Contents](#table-of-contents)
  - [User](#user)
    - [Register User](#register-user)
    - [Login User](#login-user)
    - [Fetch User](#fetch-user)
    - [Refresh Token](#refresh-token)
    - [Link Reset Password](#link-reset-password)
    - [Reset Password](#reset-password)
  - [Course](#course)
    - [Fetch All Courses](#fetch-all-courses)
    - [Store Course](#store-course)
    - [Modify Course](#modify-course)
    - [Delete Course](#delete-course)
  - [Chapter](#chapter)
    - [Fetch All Chapters by Course id](#fetch-all-chapters-by-course-id)
    - [Store Chapter](#store-chapter)
    - [Modify Chapter](#modify-chapter)
    - [Delete Chapter](#delete-chapter)
  - [Division](#division)
    - [Fetch All Divisions](#fetch-all-divisions)
  - [Role](#role)
    - [Fetch All Roles](#fetch-all-roles)

---

## User

### Register User

Endpoint

```text
POST /user/register
```

Body

```json
{
    "username": "John",
    "fullName": "John Doe",
    "email": "johndoe@gmail.com",
    "password": "secret123",
    "id_division": 2
}
```

Response

```json
{
    "status": "success",
    "message": "Successfully register user",
    "data": {
        "id": 1,
        "username": "John",
        "fullName": "John Doe",
        "email": "johndoe@gmail.com",
        "generation": null,
        "phoneNumber": null,
        "id_division": 2,
        "id_role": 1
    }
}
```

### Login User

Endpoint

```text
POST /user/login
```

Body

```json
{
    "emailUsername":"johndoe@gmail.com",
    "password": "secret123"
}
```

Response

```json
{
    "status": "success",
    "data": {
        "user": {
            "id": 1,
            "email": "johndoe@gmail.com",
            "username": "John",
            "fullName": "John Doe",
            "id_role": 1,
            "id_division": 2,
            "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MzUsImVtYWlsIjoiam9obmRvZUBnbWFpbC5jb20iLCJ1c2VybmFtZSI6IkpvaG4iLCJyb2xlIjoiVXNlciIsImRpdmlzaW9uIjoiRnJvbnQgRW5kIiwiaWF0IjoxNjY3NTkwOTMxLCJleHAiOjE2Njc1OTIxMzEsInN1YiI6IkpvaG4ifQ.INPm4rFWzXcy95yfoL_pF-HN52d4G2l0IEMppPWPlps"
        }
    }
}
```

### Fetch User

Endpoint

```text
GET /user/:id => /user/1
```

Response

```json
{
    "status": "success",
    "message": "Successfully get user by id",
    "data": {
        "id": 1,
        "username": "John",
        "fullName": "John Doe",
        "email": "johndoe@gmail.com",
        "generation": null,
        "phoneNumber": null,
        "id_division": 2,
        "id_role": 1
    }
}
```

### Refresh Token

```text
POST /user/refresh-token
```

Body

```json
{
    "username":"John",
    "refreshToken": "8TgRNSUhAza7zaa3bMVmPYOa1l8RKy6YXjd0FDgCdeAStHvhwWbJqayvxWVlstBMfBn0jokn4KOA7XvQs73tqi3NHnvPqV2rMkZhVPz1Va87wfI500SAbh5Ie8i42oxh4MGBFkESIXwPilew6HVsLe0y4uoR6Vbn1jqvHLi2oZEeZyHxkWcUn1H2c7YKAjklnQPSyNTh1GcA0NsNh9O0KqNfGNEFHg6JaZcCyiDN3feRns9oizDz7TSopcQr3frp"
}
```

Response
```json
{
    "status": "success",
    "message": "Successfully refresh access token",
    "data": {
        "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MiwiZW1haWwiOiJyaW8xMjM0NTY3ODkxMjNAZ21haWwuY29tIiwidXNlcm5hbWUiOiJiaW50YW5nMDEiLCJyb2xlIjoidXNlciIsImlkX3JvbGUiOjEsImRpdmlzaW9uIjoiQmFjay1lbmQgRGV2ZWxvcGVyIiwiaWRfZGl2aXNpb24iOjEsImlhdCI6MTY2Nzg4NTk5MiwiZXhwIjoxNjY3ODg3MTkyLCJzdWIiOiJiaW50YW5nMDEifQ.SLhjrW1t3DAth06BK_4E-FMyLgzaoyYy2tJzq87HpEw"
    }
}
```
### Link Reset Password

Endpoint

```text
POST /reset-password/
```

Request

```json
{
    "email": "johndoe@gmail.com"
}
```

Response

```json
{
    "status": "success",
    "message": "email sent successfully"
}
```

### Reset Password

Endpoint

```text
POST /:id_user/:token
```

Request

```json
{
    "password": "passwordsecret"
}
```

Response

```json
{
    "status": "success",
    "message": "Password reset successfully"
}
```
---

## Course

### Fetch All Courses

Endpoint

```text
GET /course
```

Response

```json
{
    "status": "success",
    "message": "Successfully get all courses",
    "data": [
        {
            "id": 3,
            "title": "Lorem ipsum",
            "description": "Lorem ipsum dolor sit amet consectetur adipisicing elit. Quia error libero explicabo deserunt, eum quos",
            "image_thumbnail": "https://res.cloudinary.com/dd6stok7k/image/upload/v1667654597/itc-repo/course/sgvgxlblqkis0yh5ikfq.jpg",
            "cloudinary_id": "sgvgxlblqkis0yh5ikfq",
            "createdAt": "2022-11-05T13:23:17.000Z",
            "updatedAt": "2022-11-05T13:23:17.000Z",
            "id_division": 2,
            "id_user": 2
        }
    ]
}
```

### Store Course

Endpoint

```text
POST /course
```

Request

```json
{
    "auth": {
        "type": "bearer",
        "bearer": [
            {
                "key": "token",
                "value": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MiwiZW1haWwiOiJqYW5lZG9lQGdtYWlsLmNvbSIsInVzZXJuYW1lIjoiSmFuZSIsInJvbGUiOiJVc2VyIiwiaWRfcm9sZSI6MSwiZGl2aXNpb24iOiJGcm9udC1lbmQgRGV2ZWxvcGVyIiwiaWRfZGl2aXNpb24iOjIsImlhdCI6MTY2NzY1MzkzMCwiZXhwIjoxNjY3NjU1MTMwLCJzdWIiOiJKYW5lIn0.zKZfP9hJua9nYhAshczMTisL0mthOEds0uxMkww7ots",
            }
        ]
    },
    "body": {
        "mode": "formdata",
        "formdata": [
            {
                "key": "title",
                "value": "Lorem ipsum",
                "type": "text"
            },
            {
                "key": "description",
                "value": "Lorem ipsum dolor sit amet consectetur adipisicing elit. Quia error libero explicabo deserunt, eum quos",
                "type": "text"
            },
            {
                "key": "image",
                "type": "file",
                "src": "/D:/Home/Pictures/test.jpg"
            },
            {
                "key": "id_division",
                "value": "2",
                "type": "text"
            },
            {
                "key": "id_user",
                "value": "2",
                "type": "text"
            },
        ]
    },
}
```

Response

```json
{
    "status": "success",
    "message": "Successfully create course",
    "data": {
        "id": 2,
        "title": "Lorem ipsum",
        "description": "Lorem ipsum dolor sit amet consectetur adipisicing elit. Quia error libero explicabo deserunt, eum quos",
        "image_thumbnail": "https://res.cloudinary.com/dd6stok7k/image/upload/v1667654432/itc-repo/course/it7ejg37zr9br9advbxz.jpg",
        "cloudinary_id": "it7ejg37zr9br9advbxz",
        "id_division": 2,
        "id_user": 2,
        "updatedAt": "2022-11-05T13:20:33.206Z",
        "createdAt": "2022-11-05T13:20:33.206Z"
    }
}
```

### Modify Course

Endpoint

```text
PUT /course/:id => /course/2
```

Request

```json
{
    "auth": {
        "type": "bearer",
        "bearer": [
            {
                "key": "token",
                "value": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MiwiZW1haWwiOiJqYW5lZG9lQGdtYWlsLmNvbSIsInVzZXJuYW1lIjoiSmFuZSIsInJvbGUiOiJVc2VyIiwiaWRfcm9sZSI6MSwiZGl2aXNpb24iOiJGcm9udC1lbmQgRGV2ZWxvcGVyIiwiaWRfZGl2aXNpb24iOjIsImlhdCI6MTY2NzY1NTE3NiwiZXhwIjoxNjY3NjU2Mzc2LCJzdWIiOiJKYW5lIn0.XH4xzH3xgb7yX9mZqobxEeRVr9Os6AxnFgA86EetAHw",
            }
        ]
    },
    "body": {
        "mode": "formdata",
        "formdata": [
            {
                "key": "title",
                "value": "Lorem ipsum edited",
                "type": "text"
            },
            {
                "key": "description",
                "value": "Lorem ipsum dolor sit amet consectetur adipisicing elit. Quia error libero explicabo deserunt, eum quos",
                "type": "text"
            },
            {
                "key": "image",
                "type": "file",
                "src": "/D:/Home/Pictures/test.jpg"
            },
            {
                "key": "id_division",
                "value": "2",
                "type": "text"
            },
        ]
    },
}
```

Response

```json
{
    "status": "success",
    "message": "Successfully update course",
    "data": {
        "id": 2,
        "title": "Lorem ipsum edited",
        "description": "Lorem ipsum dolor sit amet consectetur adipisicing elit. Quia error libero explicabo deserunt, eum quos",
        "image_thumbnail": "https://res.cloudinary.com/dd6stok7k/image/upload/v1667654432/itc-repo/course/it7ejg37zr9br9advbxz.jpg",
        "cloudinary_id": "it7ejg37zr9br9advbxz",
        "createdAt": "2022-11-05T13:20:33.000Z",
        "updatedAt": "2022-11-05T13:34:11.374Z",
        "id_division": 2,
        "id_user": 2
    }
}
```

### Delete Course

Endpoint

```text
DELETE /course/:id => /course/2
```

Request

```json
{
    "auth": {
        "type": "bearer",
        "bearer": [
            {
                "key": "token",
                "value": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MiwiZW1haWwiOiJqYW5lZG9lQGdtYWlsLmNvbSIsInVzZXJuYW1lIjoiSmFuZSIsInJvbGUiOiJVc2VyIiwiaWRfcm9sZSI6MSwiZGl2aXNpb24iOiJGcm9udC1lbmQgRGV2ZWxvcGVyIiwiaWRfZGl2aXNpb24iOjIsImlhdCI6MTY2NzY1NTM3NCwiZXhwIjoxNjY3NjU2NTc0LCJzdWIiOiJKYW5lIn0.bthhCnOrZCgyv0SrC6UwniBou3Wf3K_JrG2Hq_5LSBc",
            }
        ]
    },
}
```

Response

```json
{
    "status": "success",
    "message": "Successfully delete course"
}
```
---
## Chapter

### Fetch All Chapters by Course id

Endpoint

```text
GET /course/:id_course/chapter
```

Response

```json
{
    "status": "success",
    "message": "Successfully get all chapters by specific course",
    "data": [
        {
            "id": 1,
            "title": "tipe data",
            "createdAt": "2022-11-14T14:07:13.000Z",
            "updatedAt": "2022-11-14T14:07:13.000Z",
            "id_course": 1
        },
        {
            "id": 2,
            "title": "looping",
            "createdAt": "2022-11-14T14:07:45.000Z",
            "updatedAt": "2022-11-14T14:07:45.000Z",
            "id_course": 1
        }
    ]
}
```

### Store Chapter

Endpoint

```text
POST /course/:id_course/chapter
```

Request
```json
{
    "title": "looping while"
}
```

Response
```json
{
    "status": "success",
    "message": "Successfully add chapter",
    "data": {
        "id": 16,
        "title": "looping while",
        "id_course": "2",
        "updatedAt": "2022-11-15T10:15:39.194Z",
        "createdAt": "2022-11-15T10:15:39.194Z"
    }
}
```

### Modify Chapter

Endpoint

```text
PUT /course/:id_course/chapter/:id_chapter
```

Request

```json
{
    "title": "looping while and for"
}
```
Response

```json
{
    "status": "success",
    "message": "Successfully update Chapter",
    "data": {
        "id": 16,
        "title": "looping while and for",
        "createdAt": "2022-11-15T10:15:39.000Z",
        "updatedAt": "2022-11-15T10:19:22.446Z",
        "id_course": 2
    }
}
```

### Delete Chapter

Endpoint

```text
DELETE /course/:id_course/chapter/:id_chapter
```

Response

```json
{
    "status": "success",
    "message": "Successfully delete chapter"
}
```

---

## Division

### Fetch All Divisions

Endpoint

```text
GET /division
```

Response

```json
{
    "status": "success",
    "message": "Successfully get division",
    "data": [
        {
            "id": 1,
            "divisionName": "Back End"
        },
        {
            "id": 2,
            "divisionName": "Front End"
        },
        {
            "id": 3,
            "divisionName": "Mobile"
        }
    ]
}
```

---

## Role

### Fetch All Roles

Endpoint

```text
GET /role
```

Response

```json
{
    "status": "success",
    "message": "Successfully get role",
    "data": [
        {
            "id": 1,
            "roleName": "User"
        },
        {
            "id": 2,
            "roleName": "Admin"
        }
    ]
}
```

