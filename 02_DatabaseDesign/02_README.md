
# Make download app
- this downloads stock data

```python
import yfinance

df = yfinance.download('AAPL', start='2020-01-01', end='2020-10-02')
df.to_csv('AAPL.csv')
```

# Install SQLite
```
brew install sqlite
```
- or download the [Mac OS binaries](https://sqlite.org/download.html)
# Make sqlite3 DB
- this makes the relational database that we'll structure our data in

```
sqlite app.db
```

- Make the SQL code to make table
```sql
CREATE TABLE IF NOT EXISTS stock (
  id INTEGER PRIMARY KEY,
  symbol TEXT NOT NULL UNIQUE,
  company TEXT NOT NULL
);
```

- Make SQL stock table

```sql
CREATE TABLE IF NOT EXISTS stock_price (
    id INTEGER PRIMARY KEY,
    stock_id INTEGER,
    date NOT NULL,
    open NOT NULL,
    high NOT NULL,
    low NOT NULL,
    close NOT NULL,
    adjusted_close NOT NULL,
    volume NOT NULL,
    FOREIGN KEY (stock_id) REFERENCES stock (id)
);
```

# CRUD operations