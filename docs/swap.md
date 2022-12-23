# Configurer swap

Utiliser parted, file system linux-swap

`udevadm settle`

`mkswap` formate en swap

`swapon` pour monter le swap

```
UUID=39e2667a-9458-42fe-9665-c5c854605881   swap   swap   defaults   0 0
UUID=39e2667a-9458-42fe-9665-c5c854605881   swap   swap   pri=4     0 0
UUID=fbd7fa60-b781-44a8-961b-37ac3ef572bf   swap   swap   pri=10    0 0
```

pri définit la priorité, plus elle est basse, plus elle sera choisie
