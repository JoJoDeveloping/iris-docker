ARG COQ_IMAGE=coqorg/coq:8.18.0-ocaml-4.14.2-flambda
FROM ${COQ_IMAGE}

LABEL org.opencontainers.image.source=https://github.com/JoJoDeveloping/iris-docker

ARG OPAM_PACKAGES="coq-stdpp.1.9.0 coq-equations.1.3+8.18 vscoq-language-server=2.1.7"

# Install opam packages
RUN opam update && \
    opam install -y -j ${NJOBS} ${OPAM_PACKAGES} && \
    opam clean -y -a -c -s --logs && \
    eval $(opam env)
