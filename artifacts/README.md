# artifacts/

Large files kept out of git.
All are optional: without them the roles download the same things, if GitHub or Docker Hub are reachable from the nodes :)

| File | Role |
|---|---|
| `proxysql_3.0.11-ubuntu24_amd64.deb` | `proxysql` |
| `pmm-server-3.tar.gz` | `pmm_server` |
| `pxc-certs/` | `percona_cluster`, created on the first run of the PXC variant |

## ProxySQL

```bash
curl -fLO https://github.com/sysown/proxysql/releases/download/v3.0.11/proxysql_3.0.11-ubuntu24_amd64.deb
sha256sum proxysql_3.0.11-ubuntu24_amd64.deb
```

The hash must match `proxysql_deb_sha256` in `roles/proxysql/defaults/main.yml`
(the value is checked against the signed repository index: `apt-cache show proxysql`).
For another version change `proxysql_version` and `proxysql_deb_sha256`.

## PMM Server

```bash
docker pull percona/pmm-server:3
docker save percona/pmm-server:3 | gzip > pmm-server-3.tar.gz
```

## PXC certificates

`pxc-certs/` - the CA and the cluster node certificate
