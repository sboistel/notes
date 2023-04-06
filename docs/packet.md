# RPM

- `rpm -qa`: liste les paquets
- `rpm -q package`: version
- `rpm -ql package`: liste les fichiers installés

# DNF

- `dnf list`
- `dnf history`
- `dnf history undo x`

- `dnf repolist all`
- `dnf config-manager --enable rhel-9-server-debug-rpms`
- `dnf config-manager --add-repo="url"`

repos stockés dans /etc/yum.repos.d

- `rpm --import url`: importer clé gpg
- `dnf install urlrepo`: installer repo