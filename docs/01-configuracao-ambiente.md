# 01 — Configuração do ambiente

## Objetivo

O laboratório foi preparado para estudar autenticação em um ambiente virtual controlado, sem direcionar testes a sistemas externos.

## Arquitetura

| Componente | Função |
| --- | --- |
| VirtualBox | Executa as máquinas virtuais do laboratório. |
| Kali Linux | Estação usada para os estudos e testes autorizados. |
| Metasploitable 2 | Sistema-alvo intencionalmente vulnerável, destinado a treinamento. |
| Rede Host-Only | Rede virtual que permite a comunicação dentro do laboratório. |

```text
Kali Linux ── rede Host-Only (VirtualBox) ── Metasploitable 2
```

## Preparação conceitual

1. Criar ou selecionar uma rede Host-Only no VirtualBox.
2. Conectar Kali Linux e Metasploitable 2 à rede virtual do laboratório.
3. Confirmar a comunicação entre as máquinas antes de iniciar atividades.
4. Revisar as interfaces de rede para manter o alvo dentro do escopo isolado.

Os parâmetros específicos da infraestrutura e da máquina não são necessários para descrever este projeto e não são registrados neste documento.

## Verificações

O ambiente foi usado nos testes FTP e de enumeração SMB descritos em [02 — FTP](02-ataque-ftp.md) e [04 — SMB](04-enumeracao-smb.md). Não são publicados capturas de tela nem identificadores da infraestrutura.
