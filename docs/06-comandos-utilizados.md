# 06 — Comandos e ferramentas

Este documento separa as atividades confirmadas pelo histórico do laboratório dos comandos cujo texto exato não foi preservado. Os exemplos abaixo usam placeholders e explicam sintaxes; **não são transcrições garantidas das execuções**.

## O que foi realizado

| Ferramenta | Atividade confirmada | O que não está registrado |
| --- | --- | --- |
| Nmap | Identificação das portas SMB 139 e 445 e do serviço Samba. | Linha de comando exata e saída bruta. |
| Medusa | Teste controlado de força bruta no FTP com listas de usuários e senhas; credenciais válidas foram posteriormente validadas por conexão FTP. | Linha de comando exata e saída bruta; não registrar opções não confirmadas. |
| `smbclient` | Enumeração de compartilhamentos, conexão anônima ao `tmp` e listagem de arquivos e diretórios. | Linha de comando exata, sequência completa de comandos interativos e saída bruta. |

Enumeração de usuários SMB e password spraying não foram realizados. Não há comandos executados dessas atividades para documentar.

## Nmap — descoberta de serviço

As anotações disponíveis contêm esta forma de comando. O histórico confirma o uso do Nmap e as portas verificadas, mas não permite confirmar que todos os parâmetros abaixo correspondam à invocação executada:

```bash
nmap -n -p 139,445 -sV IP_DO_ALVO
```

- `-n`: não faz resolução de nomes por DNS.
- `-p 139,445`: limita a verificação às portas SMB indicadas.
- `-sV`: tenta identificar os serviços e suas versões.
- `IP_DO_ALVO`: placeholder; substitua apenas em um laboratório autorizado.

Use esta linha como referência didática, não como evidência do comando exato usado no teste.

## Medusa — autenticação FTP

A ferramenta Medusa automatiza tentativas de autenticação contra serviços compatíveis. O histórico confirma o uso de listas de usuários e senhas no teste FTP, mas **não preserva o comando exato**. Portanto, as linhas abaixo são exemplos ilustrativos, não comandos atribuídos à execução:

```bash
medusa -h IP_DO_ALVO -u USUARIO -P ARQUIVO_DE_SENHAS -M ftp
```

Esse formato ilustra o caso de um único usuário. Para indicar uma lista de usuários, a forma correspondente é:

```bash
medusa -h IP_DO_ALVO -U ARQUIVO_DE_USUARIOS -P ARQUIVO_DE_SENHAS -M ftp
```

- `-h`: define o host de destino.
- `-u`: informa um único nome de usuário.
- `-U`: informa um arquivo com uma lista de nomes de usuário.
- `-P`: informa um arquivo com candidatos a senha.
- `-M ftp`: seleciona o módulo FTP.

Não é possível determinar pelo histórico qual combinação de opções, paralelismo ou outros parâmetros foi usada. A preparação das listas e o resultado da autenticação estão resumidos em [02 — Teste FTP](02-ataque-ftp.md); os arquivos e valores das listas não são publicados.

## SMBClient — enumeração e acesso a compartilhamentos

O `smbclient` é um cliente de linha de comando para interagir com serviços SMB. As formas abaixo constam nas anotações do projeto e servem como referências ilustrativas; o histórico confirma as operações, mas não a linha exata executada:

```bash
smbclient -L //IP_DO_ALVO -N
```

`-L` solicita a listagem de compartilhamentos. `-N` suprime a solicitação interativa de senha; por si só, essa opção não comprova que o servidor aceitou uma sessão anônima. A confirmação de acesso anônimo é um resultado separado, descrito em [04 — Enumeração SMB](04-enumeracao-smb.md).

Forma ilustrativa para solicitar conexão a um compartilhamento específico:

```bash
smbclient //IP_DO_ALVO/NOME_DO_COMPARTILHAMENTO -N
```

O histórico confirma acesso sem autenticação ao compartilhamento `tmp` e listagem de seus itens. Não preserva a linha exata de conexão nem a sequência interativa; por isso, não se afirma que a forma acima foi a invocação real.

## Limites do registro

Os comandos exatos e saídas brutas não estão disponíveis para conferência nos arquivos atuais. Para uma documentação reprodutível, registre futuramente as linhas reais e saídas sanitizadas, sem endereços, credenciais, nomes de usuários, identificadores de máquina ou conteúdo privado. Não faça novos testes apenas para preencher esta lacuna sem escopo e autorização definidos.
