# BioInfo AI utilities

*** 

## Criando um container

Abra um terminal Linux e verifique que o Singularity está instalado:

```bash
singularity --version
```

Baixe o arquivo de definição do container que contém a linguagem Python e as bibliotecas de inteligência artificial:

```bash
wget https://raw.githubusercontent.com/pedro-jorge/BioInfo/main/container.def
```

Crie o container a partir do arquivo de definição:

```bash 
sudo singularity build --sandbox ubuntu24_04 container.def
```
