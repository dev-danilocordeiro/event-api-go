# event-api-go

#golan migrate
migrate create -ext sql -dir ./cmd/migrate/migrations -seq create_users_table


curl -X POST http://localhost:8080/api/v1/auth/register \
-H "Content-Type: application/json" \
-d '{
  "email": "test@example.com",
  "password": "password",
  "name": "Test User"
}'

curl -X POST http://localhost:8080/api/v1/events \
-H "Content-Type: application/json" \
-d '{
  "name": "Go Conference",
  "ownerId": 1,
  "description": "A conference about Go programming",
  "date": "2025-05-20",
  "location": "San Francisco"
}' \
-w "\nHTTP Status: %{http_code}\n"

curl -X GET http://localhost:8080/api/v1/events \
-H "Content-Type: application/json" \
-w "\nHTTP Status: %{http_code}\n"

curl -X GET http://localhost:8080/api/v1/events/1 \
-H "Content-Type: application/json" \
-w "\nHTTP Status: %{http_code}\n"

curl -X PUT http://localhost:8080/api/v1/events/1 \
-H "Content-Type: application/json" \
-d '{
  "name": "Go Conference",
  "ownerId": 1,
  "description": "A conference about Go programming",
  "date": "2025-05-20",
  "location": "New York"
}' \
-w "\nHTTP Status: %{http_code}\n"

curl -X DELETE http://localhost:8080/api/v1/events/1 \
-H "Content-Type: application/json" \
-w "\nHTTP Status: %{http_code}\n"