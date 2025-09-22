## windows

```sql
psql -U postgres
CREATE DATABASE file_manager
\! cls

CREATE EXTENSION IF NOT EXISTS "uuid-ossp";

CREATE TABLE files (
    file_id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    name TEXT NOT NULL,
    type TEXT NOT NULL,
    size BIGINT NOT NULL,
    location TEXT NOT NULL,
    uploaded_at TIMESTAMP DEFAULT NOW(),
    description TEXT
);
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    username TEXT UNIQUE NOT NULL,
    password TEXT NOT NULL
);

-- Add default user
INSERT INTO users (username, password) VALUES ('admin', 'admin123')
ALTER TABLE files
DROP COLUMN description;
```

```go
go get github.com/lib/pq
```
