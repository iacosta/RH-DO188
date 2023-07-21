### Respuesta - Practica No. 3


1. Crear el Containerfile 

```bash
❯ cat > Containerfile << EOF

FROM centos:7

ARG USUARIO
ENV USUARIO=${USUARIO:-benito}

RUN useradd -m $USUARIO
USER $USUARIO

CMD["whoami"]

EOF
```

2. Construir imagen con paremetros correspondientes

```bash
❯ podman build -t benito-came:1.0 -f .

❯ podman build --build-arg buildname=elma -t elma-marcela:1.0 -f .
```
3. Creación de los contenedores desde las imagenes creadas anteriormente

```bash
❯ podman run -ti --name benito benito-came:1.0

❯ podman run -ti --name elma elma-marcela:1.0
```