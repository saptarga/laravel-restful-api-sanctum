# LARAVEL 8 - RESTFUL API - SANCTUM AUTHENTICATION

## Description

Simple Restful API Using Laravel 8 And Sanctum Authentication.

Learning by Doing from https://codelapan.com/post/laravel-8-rest-api-authentication-dengan-sanctum

## Requirements

-   PHP >= 7.0.0
-   Database MYSQL
-   PDO PHP Extension

## Installation

```sh
# CLone this project
git@github.com:saptarga/laravel-restful-api-sanctum.git

# Install dependency
composer install
npm install

# Copy configuration for local development, and please set configuration for local development
cp .env.example .env

# Run migration file
php artisan migrate

# Run Service
php artisan serve
```

## Example Rest API

### Request Register User

Request

```http
curl --location --request POST 'http://127.0.0.1:8000/api/register' \
--form 'name="AdminTest"' \
--form 'email="admin_test@gmail.com"' \
--form 'password="1234567890"'
```

Response

```json
{
    "data": {
        "name": "AdminTest",
        "email": "admin_test@gmail.com",
        "updated_at": "2021-10-04T04:01:57.000000Z",
        "created_at": "2021-10-04T04:01:57.000000Z",
        "id": 2
    },
    "access_token": "4|IGRNRc05hww5nyMjrJE8M3pqvnnzuCgU8k5ADFb3",
    "token_type": "Bearer"
}
```

### Request Login User

Request

```http
curl --location --request POST 'http://127.0.0.1:8000/api/login' \
--form 'email="admin_test@gmail.com"' \
--form 'password="1234567890"'
```

Response

```json
{
    "message": "Hi AdminTest, welcome to home",
    "access_token": "5|G127DSNrWp6buBEi5TzOFMqs35mhDbTznLbPDc6D",
    "token_type": "Bearer"
}
```

### Request Get Profile User

Request

```http
curl --location --request GET 'http://127.0.0.1:8000/api/profile' \
--header 'Authorization: Bearer 5|G127DSNrWp6buBEi5TzOFMqs35mhDbTznLbPDc6D'
```

Response

```json
{
    "id": 2,
    "name": "AdminTest",
    "email": "admin_test@gmail.com",
    "email_verified_at": null,
    "created_at": "2021-10-04T04:01:57.000000Z",
    "updated_at": "2021-10-04T04:01:57.000000Z"
}
```

### Request Logout

Request

```http
curl --location --request POST 'http://127.0.0.1:8000/api/logout' \
--header 'Authorization: Bearer 5|G127DSNrWp6buBEi5TzOFMqs35mhDbTznLbPDc6D'
```

Response

```json
{
    "message": "You have successfully logged out and the token was successfully deleted"
}
```

## Reference

-   https://laravel.com/docs/8.x/sanctum
