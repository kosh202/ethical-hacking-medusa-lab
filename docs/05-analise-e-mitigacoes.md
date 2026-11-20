# 05 — Análise de riscos e mitigações

## Escopo e estado dos cenários

Foram realizados o teste de autenticação FTP e a enumeração SMB com confirmação de acesso anônimo a um compartilhamento e listagem de itens. DVWA, enumeração de usuários SMB e password spraying SMB permanecem pendentes. Esta análise distingue as observações do laboratório das recomendações gerais.

## Observações do laboratório

### FTP

O teste controlado com Medusa encontrou credenciais válidas, e uma conexão FTP confirmou a autenticação. Os valores não são publicados. O resultado demonstra que o serviço aceitou as credenciais testadas; não determina sua origem, reutilização ou impacto em outros sistemas.

### SMB

Foi possível conectar-se sem autenticação ao compartilhamento `tmp` e listar nomes de arquivos e diretórios. Não há relato de leitura, cópia ou alteração do conteúdo. A observação comprova exposição da listagem e acesso ao compartilhamento, mas não permite afirmar impacto além disso.

## Riscos e recomendações gerais

| Observação ou risco | Possível impacto | Mitigação recomendada |
| --- | --- | --- |
| Credenciais aceitas no FTP após teste com listas | Senhas fracas ou previsíveis podem permitir acesso não autorizado; o impacto depende das permissões da conta. | Usar senhas únicas e robustas, remover contas desnecessárias, restringir privilégios e limitar tentativas com monitoramento. |
| FTP tradicional sem criptografia | Credenciais e dados podem ser expostos a quem consiga observar o tráfego. | Desabilitar FTP sem criptografia quando não necessário; preferir SFTP ou FTPS corretamente configurado. |
| Compartilhamento SMB acessível anonimamente | Pode revelar estrutura e nomes de arquivos; dependendo das permissões e do conteúdo, pode facilitar exposição ou alteração de dados. | Restringir ou desabilitar acesso anônimo/convidado, conceder permissões apenas a contas necessárias e aplicar menor privilégio. |
| Tentativas automatizadas de autenticação | Podem facilitar adivinhação de senhas e gerar carga ou bloqueios. | Limitar tentativas, aplicar atrasos proporcionais, monitorar falhas e alertar para padrões anômalos. |
| Exposição excessiva de serviços | Aumenta a superfície disponível para enumeração e abuso. | Restringir SMB e FTP às redes e máquinas que precisam dos serviços e desabilitar serviços não necessários. |
| Falta de visibilidade | Acesso indevido ou tentativas repetidas podem passar despercebidos. | Registrar e revisar eventos de autenticação e acesso, protegendo os logs e evitando armazenar senhas ou tokens. |

As medidas são recomendações gerais, não controles que tenham sido testados ou comprovados no laboratório. A enumeração SMB não incluiu password spraying nem enumeração de usuários. Também não foi verificado acesso ao conteúdo dos itens listados.

## Próximas etapas

- Manter DVWA, enumeração de usuários SMB e password spraying SMB como pendentes até que sejam autorizados e realmente executados.
- Se esses cenários forem realizados, registrar escopo, método, resultados e limitações sem incluir dados de acesso ou identificadores privados.
- Revisar as permissões do compartilhamento e substituir as credenciais FTP no ambiente de laboratório, sem reutilizá-las em outros serviços.
