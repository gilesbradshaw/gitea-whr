# gitea-whr


Hi thanks very much for your help with this


I am running below on linux (ubuntu server)

I have stripped down my docker compose file to remove all drone stuff as irrelevant.

This is running with docker swarm so you need to do

```
docker swarm init
```


then I start the swarm with my secrets and url

```shell
export WEBHOOK_RELAY_KEY=[I MESSAGE U THIS]
export WEBHOOK_RELAY_SECRET=[I MESSAGE U THIS 2]
export GITEA_HOST=git-sigyl.webrelay.io
docker stack deploy -c docker-compose.yml gitea-new

```

then open https://git-sigyl.webrelay.io/ and register with gitea (I use username giles)

create  new repo msd-2-0

from msd-2-0 repository that you cloned from github


```
git remote add origin-whr https://git-sigyl.webrelay.io/giles/msd-2-0.git
git push -u origin-whr master

```


The push fails (I contacted you about clone failing but it's the same issue and you can't clone till you've pushed..)

```

git remote add origin-whr https://git-sigyl.webrelay.io/giles/msd-2-0.git
$ git push -u origin-whr master
Username for 'https://git-sigyl.webrelay.io': giles
Password for 'https://giles@git-sigyl.webrelay.io': 
Enumerating objects: 19966, done.
Counting objects: 100% (19966/19966), done.
Delta compression using up to 4 threads
Compressing objects: 100% (10602/10602), done.
error: RPC failed; curl 92 HTTP/2 stream 0 was not closed cleanly: INTERNAL_ERROR (err 2)
fatal: the remote end hung up unexpectedly
Writing objects: 100% (19966/19966), 109.44 MiB | 1.79 MiB/s, done.
Total 19966 (delta 12145), reused 14108 (delta 8598)
fatal: the remote end hung up unexpectedly
Everything up-to-date

```


you CAN however push locally with:

```
git remote add origin-local http://localhost:3000/giles/msd-2-0.git

git push -u origin-local master

```


and then clone will fail (as I reported)


```
Cloning into 'new-repo'...
remote: Enumerating objects: 19966, done.
remote: Counting objects: 100% (19966/19966), done.
remote: Compressing objects: 100% (7051/7051), done.
fatal: the remote end hung up unexpectedly MiB | 102.00 KiB/s     
fatal: early EOFs:  20% (3994/19966), 5.96 MiB | 102.00 KiB/s   
fatal: index-pack failed

```
