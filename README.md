![](https://github.com/Suhogruzz/HWork_SQL3/blob/main/SQL_HWork3.jpg)

```sql
 CREATE TABLE IF NOT EXISTS performer (
	id SERIAL PRIMARY KEY,
	name VARCHAR(100) NOT NULL
);

CREATE TABLE IF NOT EXISTS album (
	id SERIAL PRIMARY KEY,
	album_name VARCHAR(100) NOT NULL,
	album_year NUMERIC(4) NOT NULL
);

CREATE TABLE IF NOT EXISTS track (
	id SERIAL PRIMARY KEY,
	track_name VARCHAR(100) NOT NULL,
	track_length REAL NOT NULL,
	id_album INTEGER REFERENCES album(id)
);

CREATE TABLE IF NOT EXISTS genre (
	id SERIAL PRIMARY KEY,
	genre_name VARCHAR(100) NOT NULL
);

CREATE TABLE IF NOT EXISTS collections (
	id SERIAL PRIMARY KEY,
	collection_name VARCHAR(100) NOT NULL,
	collection_year NUMERIC(4) NOT NULL 
);

CREATE TABLE IF NOT EXISTS genre_performer (
	performer_id INTEGER REFERENCES performer(id) NOT NULL,
	genre_id INTEGER REFERENCES genre(id) NOT NULL
);

CREATE TABLE IF NOT EXISTS performer_album (
	performer_id INTEGER REFERENCES performer(id) NOT NULL,
	album_id INTEGER REFERENCES album(id) NOT NULL 
);

CREATE TABLE IF NOT EXISTS collection_track (
	track_id INTEGER REFERENCES track(id) NOT NULL,
	collection_id INTEGER REFERENCES collections(id) NOT NULL 
