ARG ROCQ_IMAGE=rocq/rocq-prover:9.0-ocaml-4.14-flambda
FROM ${ROCQ_IMAGE}

LABEL org.opencontainers.image.source=https://github.com/plf-lab-ethz/iris-docker

ARG OPAM_PACKAGES="coq-stdpp.1.12.0 rocq-equations.1.3.1+9.0 coq-autosubst.1.9 vsrocq-language-server=2.3.1"

# Install opam packages
RUN opam update && \
    opam install -y -j ${NJOBS} ${OPAM_PACKAGES} && \
    opam clean -y -a -c -s --logs && \
    eval $(opam env)
