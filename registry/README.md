# Docker/Podman registry

Currenly, the registry does not support systemd socket-activation.

A pull-request has been generated to add this support here: https://github.com/distribution/distribution/pull/4020

In the meantime, this patch can be manually applied to the latest version and the container rebuilt.  The patch
can support either open or TLS connections

# Usage
* Build socket-activated registry:
  ./build_socket_activated_registry.sh
* alter registry.service:
  * enable TLS or other configuartion features as per https://docs.docker.com/registry/
  * change named-vaolume `registry` to something useful to you
* cp registry.service registry.socket ~/.config/systemd/user/
* systemctl --user daemon-reload
* systemctl --user enable registry.socket
* systemctl --user start registry.socket
