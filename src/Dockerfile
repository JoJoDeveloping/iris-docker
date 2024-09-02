ARG COQ_IMAGE=coqorg/coq:8.19.2-ocaml-4.14.2-flambda
FROM ${COQ_IMAGE}

ARG OPAM_PACKAGES="coq-iris.4.2.0 coq-iris-heap-lang.4.2.0 coq-stdpp.1.10.0 coq-equations.1.3+8.19"

# Install opam packages
RUN opam install -y -j ${NJOBS} ${OPAM_PACKAGES} && \
    opam clean -y -a -c -s --logs && \
    eval $(opam env)
