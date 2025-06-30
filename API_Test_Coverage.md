# 📘 API Test Coverage - JSONPlaceholder

## 🔗 Base URL
`https://jsonplaceholder.typicode.com`

---

## ✅ Covered Endpoints

| Endpoint        | Method | Description                     |
|-----------------|--------|---------------------------------|
| `/posts`        | GET    | Fetch all posts                 |
| `/posts/{{id}}` | GET    | Fetch single post by ID         |
| `/posts`        | POST   | Create a new post               |
| `/posts/{{id}}` | PUT    | Update post by ID               |
| `/posts/{{id}}` | DELETE | Delete post by ID               |

---

## 🧪 Test Case Summary (27 Total)

| ID    | Endpoint        | Method | Scenario Description                               | Expected Result               | Actual Result  |
|-------|-----------------|--------|----------------------------------------------------|-------------------------------|----------------|
| TC01  | `/posts`        | GET    | Status code is 200                                 | 200 OK                        |Pass - Status code 200 OK received |
| TC02  | `/posts`        | GET    | Response is a JSON array                           | Array with 100 items          |Pass - JSON array returned with exactly 100 posts |
| TC03  | `/posts`        | GET    | Each post has `id`, `userId`, `title`, `body`      | All keys present              |Pass - Each post has userId, id, title, body keys |
| TC04  | `/posts/1`      | GET    | Get post by valid ID                               | 200 OK + post object          |Pass - Post with ID 1 returned with all keys |
| TC05  | `/posts/0`      | GET    | Get post by invalid ID                             | 404 Not Found                 |Pass - Status 404 received, response {} |
| TC06  | `/posts/abc`    | GET    | ID as string                                       | 404 Not Found                 |Pass - Status 404, response {} |
| TC07  | `/posts/9999`   | GET    | Get post by non-existent ID                        | 404 Not Found                 |Pass - Status 404 Not Found, response body is {}  |
| TC08  | `/posts`        | POST   | Create post with valid payload                     | 201 Created                   |Pass - Status 201 Created, response contains all sent fields + new id |
| TC09  | `/posts`        | POST   | Create post with missing title                     | Simulated 201 (mock API)      |Pass - Status 201 Created, response contains id only |
| TC10  | `/posts`        | POST   | Create post with missing body                      | Simulated 201 (mock API)      |Pass - Status 201 Created, response echoed title, userId, and new id |
| TC11  | `/posts`        | POST   | Send empty body                                    | Simulated 201 (mock API)      |Pass - Status 201 Created, response contains only id |
| TC12  | `/posts`        | POST   | Extra fields in payload                            | Simulated 201 (mock API)      |Pass - Status 201 Created, all extra fields and id returned in response |
| TC13  | `/posts`        | POST   | Invalid data types (number for title/body)         | Simulated 201 (mock API)      |Pass - Status 201 Created, numeric title/body accepted and returned |
| TC14  | `/posts/1`      | PUT    | Update title only                                  | 200 OK                        |Pass - Status 200 OK, response contains updated title only  |
| TC15  | `/posts/1`      | PUT    | Update body only                                   | 200 OK                        |Pass - Status 200 OK, response contains updated body only  |
| TC16  | `/posts/1`      | PUT    | Update with empty body                             | 200 OK                        |Pass - Status 200 OK, response unchanged |
| TC17  | `/posts/1`      | PUT    | Update with invalid types                          | 200 OK                        |Pass - Status 200 OK, invalid fields ignored, only id returned in response  |
| TC18  | `/posts/100`    | PUT    | Update boundary post (simulate)                    | 200 OK (mocked)               |Pass - Status 200 OK, response returned with updated title, body, userId, and id |
| TC19  | `/posts/1`      | PUT    | Update with missing fields                         | 200 OK                        |Pass - Status 200 OK, response returned with updated title only |
| TC20  | `/posts/1`      | PUT    | Update with extra fields                           | 200 OK                        |Pass - Status 200 OK, response includes extra fields from the request |
| TC21  | `/posts/1`      | DELETE | Valid delete request                               | 200 OK                        |Pass - Status 200 OK received, empty response body |
| TC22  | `/posts/0`      | DELETE | Delete invalid ID                                  |200 OK (mocked)                |Pass - Status 200 OK returned with empty {} response |
| TC23  | `/posts/abc`    | DELETE | Delete with string ID                              |200 OK (mocked)                |Pass - Status 200 OK, response returned empty {} |
| TC24  | `/posts/9999`   | DELETE | Delete non-existent ID                             |200 OK (mocked)                |Pass - Status 200 OK returned with empty {} response  |
| TC25  | `/posts`        | GET    | Response time under 1000ms                         | < 1000ms                      |Pass - Response time recorded under 1000ms |
| TC26  | `/posts`        | GET    | Response header contains `Content-Type: json`      | application/json              |Pass - Response header includes Content-Type: application/json |
| TC27  | `/posts/1`      | GET    | Validate response schema                           | All expected keys present     |Pass - All expected keys present in response body  |

---

## ⏱ Performance & Response Validations

- All GET requests should respond within 1000ms
- Response headers should include:
  - `Content-Type: application/json; charset=utf-8`
- All `POST`, `PUT`, `GET /:id` responses should be in valid JSON format

---

## 🚫 Negative Testing Covered

- Invalid ID types in path params (`abc`, `0`, `9999`)
- Missing or incomplete payloads in `POST` and `PUT` requests
- Extra/invalid fields and incorrect data types in payloads
- Attempted actions on non-existent resources (e.g., `/posts/9999`)

---

### 📊 Summary
- Total Test Cases: 27
- Passed: 27 ✅
- Failed: 0 ❌
- Status: ✅ All tests passed (mocked where applicable)

---

## 📦 Notes

- JSONPlaceholder is a fake/mock API.
- `POST`, `PUT`, `DELETE` simulate success but do not persist changes.

---