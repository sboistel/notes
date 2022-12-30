# Repository

`dnf repolist all`: liste les repos disponibles
`dnf config-manager --enable reponame`
`dnf config-manager --add-repo="url"`

Fichiers de conf repo dans /etc/yum.repos.d

Exemple de conf:

```
[EPEL]
name=EPEL 9
baseurl=https://dl.fedoraproject.org/pub/epel/9/Everything/x86_64/
enabled=1
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-9
```
