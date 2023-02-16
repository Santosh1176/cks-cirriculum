# Seccomp Paths

- Default Volumes Mounts needed for Seccomp to run as Container:

`/tmp/trace:tmp/trace`

`lib/modules/:/lib/modules/`

`/usr/src:/usr/src`


## Seccomp in Kubernetes

- Path for Custom Seccomp Profiles in Kubernetes:

`/var/lib/kubelet/seccomp`

We need to create a new Directory called `profile` in the above path and place our custom profiles in `json` format in that Dir.

- securityContext in kubernetes for seccmomp:
```yaml
podSpec:
  securityContext:
    seccompProfile:
      type: Localhost
      localhostProfile: &lt;Relative Path to seccom Profile in Profile Dir of the path mentione above
```
Addiionally, to secure container trying to gaintoot access we can turn off the privilage excalation in containers:

```yaml
.containers
- securityContext:
    allowPrivilegeEscalation: false
```