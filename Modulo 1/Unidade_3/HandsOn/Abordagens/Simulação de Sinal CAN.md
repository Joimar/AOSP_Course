
# Usando VCAN
## Instalação

Carregar o módulo vcan no linux:

```
modprobe vcan
```

Averiguar se o módulo foi carregado com sucesso:

```
lsmod | grep vcan
```

O tutorial diz que a saída deve ser parecido com o seguinte:

```
vcan                   16384  0
```

<span style="color:rgb(0, 176, 80)">O que me retornou foi o seguinte:</span>

```
vcan                   12288  0
can_dev                53248  1 vcan
```

Criando e configurando uma interface VCAN

```
ip link add dev vcan0 type vcan
ip link set vcan0 mtu 72
ip link set up vcan0
```

Averiguar as configurações da interface VCAN:

```
ifconfig vcan0
```

O tutorial diz que a saída deve ser parecido com o seguinte:

```
vcan0     Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          UP RUNNING NOARP  MTU:16  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

<span style="color:rgb(0, 176, 80)">O que me foi retornado foi o seguinte:</span>

```
vcan0: flags=193<UP,RUNNING,NOARP>  mtu 72
        unspec 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  txqueuelen 1000  (Não Especificado)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```


### Referência
https://netmodule-linux.readthedocs.io/en/latest/howto/can.html#resources