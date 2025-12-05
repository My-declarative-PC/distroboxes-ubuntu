FROM ghcr.io/my-declarative-pc/distroboxes-ubuntu-base AS curl

USER root

RUN nala update && \
    nala install --no-install-recommends -y curl

RUN mkdir -p /etc/apt/keyrings && \
    curl -sSfL https://packages.openvpn.net/packages-repo.gpg >/etc/apt/keyrings/openvpn.asc && \
    echo "deb [signed-by=/etc/apt/keyrings/openvpn.asc] https://packages.openvpn.net/openvpn3/debian $(lsb_release -cs) main" >>/etc/apt/sources.list.d/openvpn3.list

FROM ghcr.io/my-declarative-pc/distroboxes-ubuntu-base

COPY --from=curl /etc/apt/keyrings/openvpn.asc /etc/apt/keyrings/openvpn.asc
COPY --from=curl /etc/apt/sources.list.d/openvpn3.list /etc/apt/sources.list.d/openvpn3.list

RUN nala update && \
    nala install --no-install-recommends  -y apt-transport-https && \
    nala update && \
    nala install -y openvpn3-client && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    rm -rf /tmp/* /var/tmp/*

