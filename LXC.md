## LXC Commands:



Show image list to build containers from:
```
lxc image list

```


Build container from image:
```
 lxc launch local:symfonyapp-full-20.04 com-symfonyapp-sandbox02
```



Set volume mount:
```

lxc config device add com-symfonyapp-sandbox03 test_uploads disk source=/lxd_shared/test_uploads path=/srv/www/symfonyapp_uploads

```

Then check that it was added with:

```
lxc config show com-symfonyapp-sandbox04

```
