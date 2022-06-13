# Procedure to create a disconnected registry using oc-mirror

Thi document explain all the steps required to create an OLM disconnected registry with oc-mirror.



## Prerequisites

- Local egistry running

```bash
./deploy_registry.sh
```

When your local registry is running, you need to authenticate it.

```bash
$ podman login registry.local:5000
Username: dummy
Password: 
Login Succeeded!
```

- Credentials for registry `registry.redhat.io`

```bash
$ podman login registry.redhat.io
Username: <your_user_name>
Password: 
Login Succeeded!

```

## Mirror to file

```bash
oc-mirror --config imageset.yaml file://archives
```

## From file to disconnected registry

```bash
oc-mirror --from ./archives/mirror_seq1_000000.tar docker://registry.local:5000/olm-mirror --dest-skip-tls
```
