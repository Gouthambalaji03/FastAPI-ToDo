# FastAPI ToDo API

A simple REST API for managing todo items built with FastAPI and PostgreSQL.

## Live Demo

- **API Base URL**: https://fastapi-todo-server-p8g9.onrender.com
- **Swagger UI**: https://fastapi-todo-server-p8g9.onrender.com/docs
- **API Documentation (Postman)**: [View API Docs](https://documenter.getpostman.com/view/45894584/2sBXVcnDnS)

## Features

- Full CRUD operations for todo items
- PostgreSQL database with SQLAlchemy ORM
- Request/response validation with Pydantic
- Auto-generated API documentation (Swagger UI)
- Ready for deployment on Render

## Tech Stack

- **Framework**: FastAPI
- **Database**: PostgreSQL
- **ORM**: SQLAlchemy
- **Server**: Uvicorn

## Project Structure

```
FastAPI-ToDo/
├── main.py          # API endpoints
├── database.py      # Database configuration
├── model.py         # SQLAlchemy model
├── schemas.py       # Pydantic schemas
├── requirements.txt # Dependencies
└── .env             # Environment variables
```

## Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/Gouthambalaji03/FastAPI-ToDo.git
   cd FastAPI-ToDo
   ```

2. **Create a virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Set up environment variables**

   Create a `.env` file with your database URL:
   ```
   DATABASE_URL=postgresql://username:password@localhost:5432/your_database
   ```

5. **Run the application**
   ```bash
   uvicorn main:app --reload
   ```

6. **Access the API**
   - API: http://localhost:8000
   - Swagger Docs: http://localhost:8000/docs
   - ReDoc: http://localhost:8000/redoc

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/todos` | Create a new todo |
| `GET` | `/todos` | Get all todos |
| `GET` | `/todos/{id}` | Get a specific todo |
| `PUT` | `/todos/{id}` | Update a todo |
| `DELETE` | `/todos/{id}` | Delete a todo |

## Todo Schema

```json
{
  "id": 1,
  "title": "Buy groceries",
  "description": "Milk, eggs, bread",
  "completed": false
}
```

## Example Usage

**Create a todo:**
```bash
curl -X POST "http://localhost:8000/todos" \
  -H "Content-Type: application/json" \
  -d '{"title": "Buy groceries", "description": "Milk, eggs, bread", "completed": false}'
```

**Get all todos:**
```bash
curl "http://localhost:8000/todos"
```

**Update a todo:**
```bash
curl -X PUT "http://localhost:8000/todos/1" \
  -H "Content-Type: application/json" \
  -d '{"title": "Buy groceries", "description": "Milk, eggs, bread", "completed": true}'
```

**Delete a todo:**
```bash
curl -X DELETE "http://localhost:8000/todos/1"
```

## Deployment

This project is configured for deployment on [Render](https://render.com):

1. Create a new Web Service on Render
2. Connect your GitHub repository
3. Set the build command: `pip install -r requirements.txt`
4. Set the start command: `uvicorn main:app --host 0.0.0.0 --port $PORT`
5. Add your `DATABASE_URL` environment variable

## License

MIT License
