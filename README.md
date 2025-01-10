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

Verifique se o container está funcional:

```bash
singularity shell ubuntu24_04
```

Isso deverá fazer com que o container seja iniciado, com a linha de comando iniciando com "Singularity >".

Verifique que o Python está corretamente instalado:

```bash
python
```

Isso deverá fazer com que o Python seja iniciando, mostrando "Python 3.12.7 | package Anaconda, Inc. |"

Ainda dentro do Python, verifique se a biblioteca Pytorch está corretamente instalada:

```bash
import torch 
```

Se havendo neenhuma mensagem de erro, o container está pronto para uso.