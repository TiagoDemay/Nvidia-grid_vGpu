# Nvidia-grid_vGpu

fazer o download como aluno Insper do arquivo abaixo:
https://insper-my.sharepoint.com/:u:/g/personal/tiagoaodc_insper_edu_br/Ec5cpds6oL5CiJyemtgb92UBxRd1p7OrxmIzTSOylT6rMg?e=TdxEi7

enviar o arquivo para a maquina virtual
```sh
scp NVIDIA-Linux-x86_64-450.89-grid.run  user@<IP_DA_VM>:/home/user/
```

```sh
chmod +x NVIDIA-Linux-x86_64-450.89-grid.run
sudo ./NVIDIA-Linux-x86_64-450.89-grid.run
```
Aceitar e clicar em OK ou yes as solicitações feitas pelo software 
Após a instalação do driver os comandos abaixo estarão funcionando:

* nvidia-smi
* nvcc --version

Configurações para buscar licença de uso no Servidor interno Nvidia
```sh
sudo cp /etc/nvidia/gridd.conf.template /etc/nvidia/gridd.conf
sudo nano /etc/nvidia/gridd.conf
```

Alterar o arquivo para os Parametro indicado aqui
```sh
# Description: Set License Server Address
# Data type: string
# Format:  "<address>"
ServerAddress=10.103.15.200
.
.
.
  
# Description: Set Backup License Server Address
# Data type: string
# Format:  "<address>"
BackupServerAddress=10.103.15.201

.
.
.

# Description: Set Feature to be enabled
# Data type: integer
# Possible values:
#    0 => for unlicensed state
#    1 => for GRID vGPU
#    2 => for Quadro Virtual Datacenter Workstation
#    4 => for NVIDIA Virtual Compute Server
# All other values reserved
FeatureType=4

```

reiniciar e testar o serviço da nvidia-grid

```sh
sudo service nvidia-gridd restart
sudo service nvidia-gridd status
```
A mensagem abaixo demostra que a licença está funcionando:

License acquired successfully. (Info: http://10.103.15.200:7070/request; NVIDIA Virtual Compute Server)

Bons Estudos...

