### Linux Stress Testing One liners


Test memory usage:

```

while true; do stress -c 2 -i 1 -m 1 --vm-bytes 2048M -t 10s; done

```

