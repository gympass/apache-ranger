The Ranger Trino plugin at this branch was patched to work with trino 433. The
base tag used to patch the plugin was `release-ranger-2.4.0`.

## How to build
Ranger admin required PhatonJS to build properly. PhatonJS requires an older
version of openssl to build with TLS support. Since we just need the Trino
plugin we can disable the tls support by settings the evironment variable
`OPENSSL_CONF` to `/dev/null`.

Make sure that you are using the Java version `21.0.1` and maven `3.9.6`.

```bash
OPENSSL_CONF=/dev/null mvn clean compile package -B \
    -Dorg.slf4j.simpleLogger.log.org.apache.maven.cli.transfer.Slf4jMavenTransferListener=warn \
    -Dmaven.test.skip=true -Drat.skip=true -Dpmd.skip=true -Dfindbugs.skip=true \
    -Dspotbugs.skip=true -Dcheckstyle.skip=true -P ranger-jdk21
```
