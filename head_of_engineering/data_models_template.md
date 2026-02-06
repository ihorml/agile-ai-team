# Data Models & Database Schema

## Entity Format

Every entity must follow this format:

```
### Entity: [Name]
**Table**: [table_name]
**Description**: [What this entity represents]

| Column | Type | Constraints | Description |
|---|---|---|---|
| id | UUID | PK, auto-generated | Unique identifier |
| created_at | TIMESTAMP | NOT NULL, default NOW() | Record creation time |
| updated_at | TIMESTAMP | NOT NULL, default NOW() | Last update time |
| [column] | [type] | [constraints] | [description] |

**Indexes**:
- [index description and columns]

**Relationships**:
- [Entity] → [Related Entity]: [relationship type] (one-to-many, many-to-many, etc.)
```

## Entity Relationship Diagram

```
┌──────────┐     ┌──────────┐     ┌──────────┐
│  User     │────▶│  [Entity] │────▶│  [Entity] │
└──────────┘     └──────────┘     └──────────┘
```

(Replace with actual ERD.)

## Defined Entities

(Fill in as the project takes shape.)

### Entity: User
**Table**: users
**Description**: Application user account

| Column | Type | Constraints | Description |
|---|---|---|---|
| id | UUID | PK, auto-generated | Unique identifier |
| email | VARCHAR(255) | UNIQUE, NOT NULL | User email address |
| password_hash | VARCHAR(255) | NOT NULL | Hashed password |
| display_name | VARCHAR(100) | NOT NULL | User display name |
| avatar_url | TEXT | NULLABLE | Profile picture URL |
| role | ENUM('user','admin') | NOT NULL, default 'user' | Access role |
| is_active | BOOLEAN | NOT NULL, default TRUE | Account active status |
| created_at | TIMESTAMP | NOT NULL, default NOW() | Account creation time |
| updated_at | TIMESTAMP | NOT NULL, default NOW() | Last update time |

**Indexes**:
- Unique index on `email`

**Relationships**:
- (Define per project)

## Migration Strategy

- Migrations are version-controlled and sequential
- Each migration has an UP and DOWN script
- No destructive migrations in production without a rollback plan
- Seed data is separate from schema migrations
