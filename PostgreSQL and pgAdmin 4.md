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

Uncomment and set **listen_addresses = '*'**

```bash
sudo nvim /var/lib/postgres/data/postgresql.conf
```



```bash
sudo nvim /var/lib/postgres/data/pg_hba.conf
```