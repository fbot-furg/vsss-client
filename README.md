# vsss-client package

### Instalação
```sh
pip install vsss_client
```

#### Exemplo de Uso
```py
from vsss_client import FIRASim, Command, Team

# Expecifique o arquivo de configuração ao instanciar o simulador
fira = FIRASim("config.ini")

cmd = Command(Team.BLUE, 1, -10, 10)
cmd2 = Command(Team.YELLOW, 1, 10, -10)
fira.send_command([cmd, cmd2])

while True:
    robot = fira.robot(Team.BLUE, 1)
    ball = fira.ball()
    
    print(ball.x, ball.y)
```

### Arquivo de Configuração
É possivel criar um arquivo de configuração e alterar os endereços e portas do simulador

`config.ini`
```ini
# Arquivo de configuração padrão
[FIRA]
vision_address = 224.0.0.1
vision_port = 10002
command_address = 127.0.0.1
command_port = 20011
```


### Regerando Protos / Ubuntu
Instale o `protobuf-compiler` 
```sh
apt install -y protobuf-compiler
protoc --version #Garanta que a versão seja 3+
```

Compilando protos
```sh
protoc -I=./protos --python_out=./vsss_client ./protos/*.proto
```

