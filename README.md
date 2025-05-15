
# Mininet - Topologia Linear com 6 Switches

Este experimento utiliza o Mininet para criar uma topologia linear com 6 switches, testando conectividade e desempenho de rede entre os hosts conectados.



## 1. Criar a Topologia Linear

Execute o comando abaixo no terminal para iniciar o Mininet:

```bash
  sudo mn --topo=linear,6 --mac --link tc,bw=25
```
Este comando cria uma rede no Mininet com 6 switches em topologia linear, cada um conectado a um host, totalizando 6 hosts, configura endereços MAC automáticos, define largura de banda de 25Mbps para todos os links e utiliza o controlador padrão.


## 2. Inspecionar Informações da Rede

Dentro do CLI do Mininet (após executar o comando acima):

```bash
# Ver todos os nós (hosts e switches)
nodes

# Ver conexões de rede
net

# Ver IP e MAC de todos os nós
dump

# Ver interfaces de um host específico (exemplo: h1)
h1 ifconfig -a
```


## 3. Testes de Conectividade

Testar ping entre todos os hosts:

```bash
pingall
```

Testar ping entre dois hosts específicos (ex: h1 e h6):
```bash
h1 ping -c 5 h6
```


## 4. Teste de Desempenho TCP com iperf

Abrir terminais para os hosts h1 e h2:

```bash
xterm h1 h2
```

No terminal do h1 (servidor):
```bash
iperf -s -p 5555 -i 1
```

No terminal do h2 (cliente):
```bash
iperf -c 10.0.0.1 -p 5555 -i 1 -t 15
```