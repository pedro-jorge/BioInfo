# BioInfo AI utilities

*** 

## Criando um container com Ubuntu 24

Instruções para a criação de um container com o sistema operacional Ubuntu 24.04.

Abra um terminal Linux e verifique se o Singularity está instalado. Caso não esteja, siga as [instruções oficiais de instalação](https://docs.sylabs.io/guides/3.5/user-guide/quick_start.html).

```bash
singularity --version
```

Uma vez verificado, vá para a pasta onde deseja realizar a instalação:

```bash
cd path/to/container/
```

Crie um arquivo .def:

```bash
nano container.def 
```

Defina o sistema operacional Ubuntu 24.04, escrevendo as seguintes linhas no *container.def*:

```bash
Bootstrap: docker
From: ubuntu:24.04
```

Pressione **CTRL X** para salvar o arquivo e sair do *nano*.

Crie o container a partir do arquivo *container.def*.

```bash
sudo singularity build --sandbox ubuntu24_04 container.def
```

Isso criará uma pasta chamada *ubuntu24_04*.

Entre no container para prosseguir com as próximas instalações:

```bash
sudo singularity shell --writable ubuntu24_04
```


## Instalação do Anaconda, Java e R:

Uma vez dentro do container, instale o *curl* (necessário para baixar arquivos):

```bash
apt update && apt install curl
```

Baixe o script de instalação do Anaconda:

```bash
curl -O https://repo.anaconda.com/archive/Anaconda3-2024.10-1-Linux-x86_64.sh
```

Instale o Anaconda:

```bash
bash Anaconda3-2024.10-1-Linux-x86_64.sh -bfp /usr/local
```

Instale o Java:

```bash
apt install default-jre
```

Instale o R:

```bash
apt install r-base-dev
```


## Instalação da IA #1: Deep learning prediction of enzyme optimum pH ✅

Vá para o diretório onde deseja instalar: 

```bash 
cd path/to/AI
```

Clone o repositório e vá para dentro dele:

```bash
git clone https://github.com/jafetgado/EpHod.git && cd EpHod
```

Baixe o YAML que contém as dependências a serem instaladas:

```bash
curl -O https://raw.githubusercontent.com/pedro-jorge/BioInfo/main/EpHod.yml
```

Crie o ambiente da IA no Anaconda:

```bash
conda env create -n ephod -f ./EpHod.yml -p ./env
```

Para ativar esse ambiente:

```bash
source activate && conda activate ephod
```


## Instalação da IA #2: A sequence embedding method for enzyme optimal condition analysis ✅

Vá para o diretório onde deseja instalar: 

```bash 
cd path/to/AI
```

Essa IA está escrita em Java. Basta apenas clonar o repositório:

```bash
git clone https://github.com/bj600800/EOCA.git
```

Nota: provavelmente algumas modificações devem ser feitas no código. Aparentemente, os diretórios usados para leitura e escrita de arquivos estão escritos de acordo com o PC utilizado pelos autores.

## Instalação da IA #3: Rapid protein stability prediction using deep learning representations ❌

Ainda por terminar.

Vá para o diretório onde deseja instalar: 

```bash 
cd path/to/AI
```

Crie um ambiente da IA no Anaconda:

```bash
conda create --name rasp --file=rasp_env.yml
```

Ative o ambiente criado:

```bash
source activate && conda activate rasp
```

```bash
git clone https://github.com/KULL-Centre/_2022_ML-ddG-Blaabjerg.git
```


```bash 
cd src/pdb_parser_scripts
```

```bash 
git clone https://github.com/rlabduke/reduce.git
```

```bash
cd reduce
```

```bash
make; make install 
```

```bash
cd ../../../data/test/Human/
```

```bash 
curl -O https://sid.erda.dk/share_redirect/fFPJWflLeE/rasp_preds_exp_strucs_gnomad_clinvar.csv
```

```bash 
curl -O https://sid.erda.dk/share_redirect/fFPJWflLeE/rasp_preds_alphafold_UP000005640_9606_HUMAN_v2_vaex_dataframe.zip
```



## Instalação da IA #4: EnZymClass: Substrate specificity prediction tool of plant acyl-ACP thioesterases based on ensemble learning ✅

Vá para o diretório onde deseja instalar: 

```bash 
cd path/to/AI
```

Crie o ambiente da IA no Anaconda:

```bash
conda create -n enzymclass -c conda-forge -c bioconda -c anaconda python=3.9 scikit-learn pandas multiprocess blast wget bioconductor-kebabs
```

Ative o ambiente:

```bash
source activate && conda activate enzymclass
```

Instale as bibliotecas complementares:

```bash
pip install ngrampro ifeatpro pssmpro
```

Clone o repositório e vá para dentro dele::

```bash
git clone https://github.com/deeprob/EnZymClass.git && cd EnZymClass
```

Baixe o dataset de treino utilizado pelos autores:

```bash 
curl -O https://github.com/deeprob/ThioesteraseEnzymeSpecificity/blob/master/data/raw/TE_trainset.csv
```

Baixe o dataset de teste utilizado pelos autores:

```bash
curl -O https://github.com/deeprob/ThioesteraseEnzymeSpecificity/blob/master/data/raw/TE_testset.csv
```


## Instalação da IA #5: Machine learning-based prediction of activity and substrate specificity for OleA enzymes in the thiolase superfamily ✅

Vá para o diretório onde deseja instalar: 

```bash 
cd path/to/AI
```

Clone o repositório:
```bash 
git clone https://github.com/serina-robinson/thiolase-machine-learning.git
```

Inicialize o R:

```bash
R 
```

Instale as bibliotecas necessárias:

```bash 
pacman::p_load("tidyverse", "viridis", "readxl", "ggtree", "caret", "rsample", "ranger", "pROC", "RColorBrewer", "ggpubr", "ggpmisc", "Biostrings", "DECIPHER","kableExtra", "readr")
```