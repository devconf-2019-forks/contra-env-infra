FROM fedora:29

LABEL k8s.io.description="Container to help build containers" \
      k8s.io.display-name="container-tools" \
      openshift.io.tags="contra, container-tools"

RUN dnf install -y buildah make podman dumb-init procps && \
    chmod 664 /etc/passwd

# change cgroup manager from systemd to cgroupfs
COPY libpod.conf /etc/containers/libpod.conf

ADD ./bin /bin

USER 1001

ENTRYPOINT ["/usr/bin/dumb-init", "--", "uid_entrypoint"]

