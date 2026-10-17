# Camada 4 — Transporte

## Conceito

A Camada de Transporte é responsável pela comunicação entre aplicações através de protocolos como **TCP** e **UDP**.

Ela utiliza números de porta para identificar os serviços envolvidos na comunicação.

### TCP

O **TCP (Transmission Control Protocol)** é um protocolo orientado à conexão e utiliza mecanismos de controle e confirmação da entrega dos dados.

### UDP

O **UDP (User Datagram Protocol)** realiza a transmissão sem estabelecer uma conexão e não possui os mesmos mecanismos de confirmação de entrega presentes no TCP.

### Portas e Sockets

As portas são utilizadas para identificar serviços ou aplicações durante uma comunicação.

A combinação entre um endereço IP e uma porta forma um socket, permitindo identificar um ponto da comunicação.

## Visão de Troubleshooting

Um possível sintoma relacionado à Camada 4 ocorre quando existe conectividade com o destino, mas determinado serviço não pode ser acessado.

Por exemplo, o `ping` pode responder normalmente enquanto uma porta TCP específica não aceita conexão.

Uma ferramenta que pode ser utilizada para testar a porta é o `nc`:

```bash
nc -zv <IP_de_destino> <porta>
```

O comando tenta estabelecer uma conexão com a porta informada e apresenta se a tentativa foi bem-sucedida ou não.

## Laboratórios Relacionados

- [Análise de portas e sockets TCP com ss](../../../labs/networking/02-ss-tcp-sockets.md)
