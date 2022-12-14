# Réinitialiser MDP root
1. Redémarrer
2. Dans le menu GRUB, appuyer sur "e"
3. changer quiet par rd.break
4. `mount -o remount,rw /sysroot`
5. `chroot /sysroot`
6. Changer le mdp
7. `touch /.autorelabel`