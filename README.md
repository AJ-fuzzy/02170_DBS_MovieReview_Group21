# 02170_DBS_MovieReview_Group21
SQL Database Project

```mermaid
erDiagram
    user {
        int UserID PK
        varchar Name
        varchar Email
        varchar Username
    }

    genre {
        int GenreID PK
        varchar GenreName
    }

    movie {
        int MovieID PK
        varchar Title
        date ReleaseDate
        int GenreID FK
    }

    review {
        int ReviewID PK
        int UserID FK
        int MovieID FK
        int Rating
        text ReviewText
        date ReviewDate
    }

    comment {
        int CommentID PK
        int UserID FK
        int ReviewID FK
        text CommentText
        date CommentDate
    }

    watchlist {
        int UserID PK, FK
        int MovieID PK, FK
        enum Status "SEEN, NOT_SEEN"
    }

    %% Relationships
    user ||--o{ review : "writes"
    movie ||--o{ review : "has"
    user ||--o{ comment : "posts"
    review ||--o{ comment : "contains"
    genre ||--o{ movie : "categorizes"
    user ||--o{ watchlist : "manages"
    movie ||--o{ watchlist : "listed_in"
