## PSQL Stuf

Connect to remote postgres with SSH tunneling:

```
ssh -L 5433:localhost:5432 user@host.com

```

Then in another terminal:

```
psql -h localhost -p 5433 -U symfony -d newdatabase

```
