# Build
FROM golang:1.23.7 AS build_context

ENV OUTDIR=/out
RUN mkdir -p ${OUTDIR}/usr/local/bin/

WORKDIR /workspace
ADD . /workspace/

RUN make ks-apiserver
RUN mv /workspace/bin/cmd/ks-apiserver ${OUTDIR}/usr/local/bin/

##############
# Final image
#############

FROM alpine:3.21.3

COPY --from=build_context /out/ /

WORKDIR /

EXPOSE 9090
CMD ["sh"]
