# Camada de Transporte

## Conceito

A Camada de Transporte faz a identificação e a multiplexação dos dados. Ou seja, ela identifica de qual porta vem e de qual porta vai. Tendo 2 protocolos principais, o protocolo TCP e o protocolo UDP. Com algumas diferenças entre eles, é a aplicação que define o que será utilizado.

### TCP

É um protocolo que é confiável e separa os dados em segmentos. Um protocolo com maior sobrecarga de controle, mas que garante a confiabilidade das informações enviadas, o sequenciamento, a confirmação de recebimento, através da flag `ACK` e a retransmissão de dados perdidos.

### UDP

É um protocolo ágil, mas que por si só, não é confiável. Por ser um protocolo mais simples e com menor sobrecarga de controle, não garante que as informações cheguem ao seu destino, não possui ordenação ou retransmissão automática.

## Visão de Troubleshooting

Na Camada de Transporte, problemas de conexão com serviços específicos podem estar relacionados às portas e aos sockets TCP.

Para investigar, podemos utilizar o comando `ss -tpan` no equipamento analisado, verificando os sockets TCP e seus respectivos estados.
