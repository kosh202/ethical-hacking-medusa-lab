# Ethical Hacking com Kali Linux e Medusa

Projeto de estudo sobre avaliação controlada de autenticação e serviços de rede, desenvolvido em um laboratório virtual isolado. O trabalho registra testes realizados com Kali Linux e Metasploitable 2, além de conceitos, resultados e medidas de mitigação.

## Ambiente

O laboratório utiliza Kali Linux e Metasploitable 2 em máquinas virtuais no VirtualBox, conectadas por rede Host-Only. Os testes descritos foram realizados nesse ambiente autorizado. Endereços, credenciais e identificadores das máquinas foram omitidos.

## Cenários e status

| Cenário | Status | Resultado resumido | Documentação |
| --- | --- | --- | --- |
| Preparação do laboratório | Realizado | Kali Linux e Metasploitable 2 configurados em rede Host-Only. | [Configuração do ambiente](docs/01-configuracao-ambiente.md) |
| Força bruta FTP com Medusa | Realizado | Foram encontradas credenciais válidas e a autenticação foi confirmada no serviço FTP. | [Teste FTP](docs/02-ataque-ftp.md) |
| Enumeração SMB e acesso anônimo | Realizado | Foram enumerados compartilhamentos; o acesso anônimo ao compartilhamento `tmp` e a listagem de seu conteúdo foram confirmados. | [Enumeração SMB](docs/04-enumeracao-smb.md) |
| Enumeração de usuários SMB | Pendente | Não realizada. | [Enumeração SMB](docs/04-enumeracao-smb.md) |
| Password spraying em SMB | Pendente | Não realizado. | [Enumeração SMB](docs/04-enumeracao-smb.md) |
| Teste de autenticação com DVWA | Pendente | Não realizado. | [Cenário DVWA](docs/03-ataque-dvwa.md) |

As atividades são descritas conforme o histórico do laboratório. O repositório não contém capturas nem saídas brutas; comandos sem registro exato são identificados como exemplos ou referências, não como transcrições verificadas.

## Aprendizados e mitigação

O cenário FTP mostra o risco de senhas fracas ou previsíveis em um serviço de autenticação. No SMB, o acesso anônimo permitiu entrar em um compartilhamento e listar nomes de arquivos e diretórios; não há relato de leitura ou alteração desses arquivos. As recomendações correspondentes estão em [Análise de riscos e mitigações](docs/05-analise-e-mitigacoes.md).

## Documentação

- [Configuração do ambiente](docs/01-configuracao-ambiente.md)
- [Teste controlado de FTP](docs/02-ataque-ftp.md)
- [Cenário planejado com DVWA](docs/03-ataque-dvwa.md)
- [Enumeração SMB](docs/04-enumeracao-smb.md)
- [Análise de riscos e mitigações](docs/05-analise-e-mitigacoes.md)
- [Comandos utilizados e exemplos](docs/06-comandos-utilizados.md)
- [Política para wordlists](wordlists/README.md)

Não são distribuídos wordlists, scripts de ataque, capturas ou dados de acesso. Consulte também o [`.gitignore`](.gitignore), que reduz o risco de adicionar acidentalmente artefatos locais.

## Uso ético

Este projeto é educacional. Execute testes apenas em sistemas próprios ou com autorização explícita, dentro de um escopo definido e controlado. Não utilize os procedimentos contra sistemas de terceiros.
