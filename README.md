# express-graphql-mongodb-boilerplate

## Authentication from scratch

### SignIn, SignUp, ResetPassword, ChangePassword, UpdateUser, SwitchLocale

### User verification, i18next - for languages, cron jobs for clear expired reset password, verification tokens etc

#### Redis for token blacklisting

## Package list

    "agenda"
    "apollo-upload-server"
    "bcryptjs"
    "body-parser"
    "crypto-random-string"
    "dotenv"
    "express"
    "express-graphql"
    "graphql"
    "graphql-compose"
    "graphql-compose-mongoose"
    "i18next"
    "i18next-express-middleware"
    "ioredis"
    "jsonwebtoken"
    "module-alias"
    "moment"
    "mongoose"
    "nodemailer"
    "validator"

### copy .env.example to .env

### App Start

    npm run start
    npm run start:local - with nodemon

### Cron Start

    npm run agenda
    npm run agenda:local - with nodemon

### ESlint Start

    npm run lint
    npm run lint:write - with prefix --fix

## Queries

```graphql
query user {
  user {
    _id
    email
    firstName
    lastName
    locale
    account {
      verification {
        verified
      }
    }
    updatedAt
    createdAt
  }
}
```

## Mutations

```graphql
mutation signIn($email: String!, $password: String!) {
  signIn(email: $email, password: $password) {
    accessToken
  }
}

mutation signUp($email: String!, $password: String!) {
  signUp(email: $email, password: $password) {
    accessToken
  }
}

mutation logout {
  logout {
    succeed
  }
}

mutation verifyRequest {
  verifyRequest {
    succeed
  }
}

mutation verify($token: String!) {
  verify(token: $token) {
    accessToken
  }
}

mutation resetPassword($email: String!) {
  resetPassword(email: $email) {
    succeed
  }
}

mutation newPassword($token: String!, $newPassword: String!) {
  newPassword(token: $token, newPassword: $newPassword) {
    accessToken
  }
}

mutation changePassword($currentPassword: String!, $newPassword: String!) {
  changePassword(currentPassword: $currentPassword, newPassword: $newPassword){
    succeed
  }
}

mutation updateUser($email: String!, $firstName: String!, $lastName: String!) {
  updateUser(email: $email, firstName: $firstName, lastName: $lastName) {
    _id
    email
    firstName
    lastName
    locale
    account {
      verification {
        verified
      }
    }
    updatedAt
    createdAt
  }
}

mutation switchLocale($locale: Locale!) {
  switchLocale(locale: $locale) {
    locale
  }
}
```
