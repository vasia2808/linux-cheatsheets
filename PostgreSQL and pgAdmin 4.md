# PostgreSQL on a Virtual Machine

```bash
sudo pacman -S postgresql
sudo -iu postgres
initdb -D /var/lib/postgres/data
exit
sudo systemctl enable --now postgresql
sudo -iu postgres
createuser --interactive
createdb -O user dbname
psql -d dbname
\password user
\q
exit
```

Uncomment and set**listen_addresses = '*'**

```bash
sudo nvim /var/lib/postgres/data/postgresql.conf
```

Append: **host    dbname            user           192.168.122.0/24        scram-sha-256**

```bash
sudo nvim /var/lib/postgres/data/pg_hba.conf
```

# pgAdmin 4

```bash
sudo mkdir /var/lib/pgadmin
sudo mkdir /var/log/pgadmin
sudo chown $USER /var/lib/pgadmin
sudo chown $USER /var/log/pgadmin
(venv) pip install pgadmin4
(venv) pdadmin4
```
