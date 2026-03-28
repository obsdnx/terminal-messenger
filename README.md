> Terminal-based real-time chat — Python, sockets, and SQLite. Nothing else.

---

## Stack

| | |
|---|---|
| Language | Python 3.10+ |
| Networking |
| UI | `curses` (stdlib) |
| Database | `sqlite3` (stdlib) |
| Protocol | Newline-delimited JSON over TCP |

---

## Setup

```bash
pip install bcrypt
```

**Start the server**
```bash
python server/server.py --host 0.0.0.0 --port 5000
```

**Connect a client**
```bash
python client/client.py --host <server-ip> --port 5000
```

---

## Commands

| Command | Action |


---

## Project structure

```
terminal-messenger/
├── server/
│   ├── server.py      # asyncio TCP server
│   ├── router.py      # message routing
│   ├── rooms.py       # room management
│   └── auth.py        # login / registration
├── client/
│   ├── client.py      # TCP connection
│   └── ui.py          # curses interface
├── db/
│   ├── database.py    # query helpers
│   └── schema.sql     # users, rooms, messages
├── shared/
│   └── protocol.py    # message format
└── requirements.txt
```

---

## Schema

```sql
CREATE TABLE users    (id INTEGER PRIMARY KEY, username TEXT UNIQUE, password TEXT);
CREATE TABLE rooms    (id INTEGER PRIMARY KEY, name TEXT UNIQUE);
CREATE TABLE messages (id INTEGER PRIMARY KEY, room_id INTEGER, user_id INTEGER, content TEXT, sent_at DATETIME);
```

---

## Roadmap

- [ ] Direct messages
- [ ] Presence indicators
- [ ] TLS support
- [ ] Docker image

---

MIT License
