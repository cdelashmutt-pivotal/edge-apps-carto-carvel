FROM ubuntu
WORKDIR /root
RUN  apt-get update \
  && apt-get install -y wget \
  && rm -rf /var/lib/apt/lists/*
RUN wget https://github.com/vmware-tanzu/carvel-imgpkg/releases/download/v0.33.0/imgpkg-linux-amd64 && chmod +x imgpkg-linux-amd64
RUN wget https://github.com/vmware-tanzu/carvel-kbld/releases/download/v0.35.0/kbld-linux-amd64 && chmod +x kbld-linux-amd64
RUN wget https://github.com/stedolan/jq/releases/download/jq-1.6/jq-linux64 && chmod +x jq-linux64

FROM ubuntu  
COPY --from=0 /root/imgpkg-linux-amd64 /usr/local/bin/imgpkg
COPY --from=0 /root/kbld-linux-amd64 /usr/local/bin/kbld
COPY --from=0 /root/jq-linux64 /usr/local/bin/jq