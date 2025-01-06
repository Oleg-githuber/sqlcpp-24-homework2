# Домашняя работа
## Задание 1
Для создания базы данных музыкального сайта были использованы команды:
```sh
CREATE TABLE IF NOT EXISTS genres (
	id SERIAL PRIMARY KEY, 
	genre_name VARCHAR(20) NOT NULL
);

CREATE TABLE IF NOT EXISTS artists (
	id SERIAL PRIMARY KEY, 
	artist_name VARCHAR(40) NOT NULL
);

CREATE TABLE IF NOT EXISTS albums (
	id SERIAL PRIMARY KEY, 
	album_name VARCHAR(40) NOT NULL, 
	year_of_album DATE NOT NULL
);

CREATE TABLE IF NOT EXISTS songs (
	id SERIAL PRIMARY KEY, 
	song_name VARCHAR(40) NOT NULL,
	album_id INTEGER NOT NULL REFERENCES albums(id)
);

CREATE TABLE IF NOT EXISTS collections (
	id SERIAL PRIMARY KEY, 
	collection_name VARCHAR(40) NOT NULL, 
	year_of_collection DATE NOT NULL
);

CREATE TABLE IF NOT EXISTS artists_and_genres (
	genre_id INTEGER NOT NULL REFERENCES genres(id),
	artist_id INTEGER NOT NULL REFERENCES artists(id),
	CONSTRAINT pk_genre PRIMARY KEY (genre_id, artist_id)
);

CREATE TABLE IF NOT EXISTS artists_and_albums (
	album_id NTEGER NOT NULL REFERENCES albums(id),
	artist_id NTEGER NOT NULL REFERENCES artists(id),
	CONSTRAINT pk_albu PRIMARY KEY (album_id, artist_id)
);

CREATE TABLE song_info (
	song_id NTEGER NOT NULL REFERENCES songs(id),
	artist_id NTEGER NOT NULL REFERENCES artists(id),
	genre_id NTEGER NOT NULL REFERENCES genres(id),
	CONSTRAINT pk_song PRIMARY KEY (song_id, artist_id, genre_id)
);

CREATE TABLE collection_info (
	collection_id NTEGER NOT NULL REFERENCES collections(id),
	song_id NTEGER NOT NULL REFERENCES songs(id),
	CONSTRAINT pk_col PRIMARY KEY (collection_id, song_id)
);
```
Результат создания таблиц:
![скриншот](img/1.jpg)
Диаграмма связей таблиц БД:
![скриншот](img/2.jpg)
## Задание 2
Для создания базы данных сотрудников были использованы команды:
```sh
CREATE TABLE IF NOT EXISTS employees (
	id SERIAL PRIMARY KEY,
	employee_name VARCHAR(40) NOT NULL,
	post VARCHAR(40) NOT NULL, 
	department VARCHAR(40) NOT NULL
);

ALTER TABLE employees 
	ADD COLUMN manager_id INTEGER REFERENCES employees(id);

```
Результат создания таблиц:
![скриншот](img/2.1.jpg)
Диаграмма связей таблиц БД:
![скриншот](img/2.2.jpg)