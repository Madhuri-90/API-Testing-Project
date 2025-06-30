# JSONPlaceholder API Testing with Postman

This project demonstrates API testing using Postman on the public JSONPlaceholder API. It covers CRUD operations, response validation, and environment setup.

## 🔧 Tools Used
- Postman
- JSONPlaceholder (https://jsonplaceholder.typicode.com)

## 📦 Endpoints Covered
- `/posts`
  - GET all posts
  - GET single post by ID
  - POST create new post
  - PUT update post
  - DELETE post

## 🚀 How to Use
1. Import the collection from `/postman/JSONPlaceholder.postman_collection.json`
2. Import the environment from `/postman/JSONPlaceholder_environment.json`
3. Set the environment to `JSONPlaceholder`
4. Run each request manually or in sequence

## ✅ Test Scenarios
- Valid request tests
- Negative scenarios (e.g., invalid ID)
- Response schema checks
