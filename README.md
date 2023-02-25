
The archive_reader.py script (or the `ArchiveReader` class within) reads in your Mastodon archive outbox.json (specifically posts you made) and creates a `main.db` sqlite3 database.

The database holds two tables and one view: 

    * `search_data`. This is a virtual table created with FTS5 that allows for full text search of your posts.
    * `full_data`. This is every column from the archive that contains an `object_id` 
    * `combined`. This is a view that combines the two tables above on extracted integer post id column

Creating the sqlite database requires pandas and [html2text](https://pypi.org/project/html2text/).

I also include a plotly dash `app.py` to allow for GUI searching of the archive, using sqlite full text search ([FTS5](https://www.sqlite.org/fts5.html)) on the contents of the archived posts.