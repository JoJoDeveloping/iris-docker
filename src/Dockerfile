ARG ROCQ_IMAGE=rocq/rocq-prover:9.2
FROM ${ROCQ_IMAGE}

LABEL org.opencontainers.image.source=https://github.com/plf-lab-ethz/iris-docker

ARG OPAM_PACKAGES="rocq-stdpp.1.13.0 rocq-equations.1.3.2+9.2 coq-autosubst.1.10 vsrocq-language-server.2.4.3"

# Install opam packages
RUN opam update && \
    opam install -y -j ${NJOBS} ${OPAM_PACKAGES} && \
    opam clean -y -a -c -s --logs && \
    eval $(opam env)
