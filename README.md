# 🐟 pg_clone.fish — Clone PostgreSQL Schema via Connection URLs

This Fish shell script allows you to **clone the database** from one PostgreSQL database to another using connection URLs.

---

## 📦 Features

- ✅ Clone the entire postgres database
- ✅ Uses `--from` and `--to` flags for clarity
- ✅ Validates connection to both databases before proceeding
- ✅ Uses a temporary file for schema export and cleans up afterward

---

## 🔧 Requirements

- [Fish shell](https://fishshell.com/)
- `psql` and `pg_dump` installed and available in `$PATH`
- PostgreSQL connection URLs (with credentials and accessible hosts)

---

## 🚀 Usage

```bash
./pg_clone.fish --from <existing_db_url> --to <new_db_url>
```

Example:

```bash
./pg_clone.fish --from "postgres://user1:pass@host1:5432/db1" --to "postgres://user2:pass@host2:5432/db2"
```

---

## 📝 Notes

- URLs must be full PostgreSQL connection URIs (e.g., `postgres://user:pass@host:port/db`)
- Only the schema is transferred — no data is copied
- The script uses a temp file for the dump and automatically deletes it after import
- If the destination database already has conflicting objects, import may fail

---

## 📁 Installation (Optional)

To use from anywhere:

```bash
mv pg_clone.fish ~/.local/bin/pg_clone
chmod +x ~/.local/bin/pg_clone
```

Make sure `~/.local/bin` is in your `$PATH`.

---

## ✅ Output

```text
🔌 Checking connection to existing DB...
🔌 Checking connection to new DB...
📦 Dumping schema from existing DB...
📥 Importing schema into new DB...
✅ Schema cloned successfully.
```

---
