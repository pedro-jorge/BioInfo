# BioInfo AI utilities

*** 

## Criando um container Ubuntu 24

Instruções para a criação de um container do sistema operacional Ubuntu 24.04 em conjunto com a linguagem de programação Python e bibliotecas de computação científica e inteligência artificial.

Abra um terminal Linux e verifique se o Singularity está instalado:

```bash
singularity --version
```

Vá para a pasta onde deseja instalar o container:

```bash
cd path/to/container/
```

Baixe o arquivo de definição do container, que contém as instruções de instalação da linguagem Python e das bibliotecas de inteligência artificial:

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

Dentro do container, verifique se o Python está corretamente instalado:

```bash
python
```

Isso deverá fazer com que o Python seja iniciando, mostrando "Python 3.12.7 | package Anaconda, Inc. |"

Dentro do Python, verifique se a biblioteca Pytorch está corretamente instalada:

```bash
import torch 
```

Não havendo nenhuma mensagem de erro, o container está pronto para uso.