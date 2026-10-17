# Camada 3 — Rede

## Conceito

A Camada de Rede é responsável pelo **endereçamento lógico e pelo encaminhamento de pacotes entre redes**.

Protocolos como **IPv4** e **IPv6** operam nesta camada.

Ela permite que os dados sejam encaminhados da rede de origem até a rede de destino através de dispositivos responsáveis pelo roteamento.

## Visão de Troubleshooting

Um possível sintoma de problema relacionado à Camada 3 ocorre quando um dispositivo não consegue alcançar um destino localizado em outra rede.

Uma das ferramentas utilizadas para investigar o caminho até o destino é o `traceroute`.

```bash
traceroute <IP_de_destino>
```

O comando permite observar os saltos percorridos em direção ao destino e pode ajudar a identificar em qual parte do caminho a comunicação deixa de ser observada.

Uma resposta como:

```text
* * *
```

não significa necessariamente que aquele roteador esteja com problema, pois alguns equipamentos podem não responder às mensagens utilizadas pelo `traceroute`.

O resultado deve ser analisado considerando o comportamento geral da comunicação.
