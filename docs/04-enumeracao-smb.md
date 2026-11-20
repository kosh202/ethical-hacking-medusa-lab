# 04 — Enumeração SMB e acesso anônimo

## Status

**Enumeração realizada.** Password spraying e enumeração de usuários SMB permanecem **pendentes** e não fazem parte dos resultados abaixo.

## Objetivo e conceitos

O objetivo foi identificar o serviço SMB do laboratório, listar compartilhamentos disponíveis e verificar se havia acesso sem autenticação.

Enumeração consiste em coletar informações expostas por um serviço, como portas ou compartilhamentos; enumeração de usuários procura identificar contas e não foi realizada. Força bruta testa muitas combinações contra uma conta, enquanto password spraying testa uma ou poucas senhas candidatas contra várias contas. Nenhum desses testes de autenticação foi realizado no cenário SMB.

## Metodologia realizada

1. O Nmap foi utilizado para identificar as portas 139 e 445 e reconhecer o serviço Samba.
2. O `smbclient` foi utilizado para enumerar compartilhamentos.
3. Foi confirmado que o serviço aceitava uma conexão anônima.
4. Houve acesso sem autenticação ao compartilhamento `tmp`.
5. Foi executada a listagem de arquivos e diretórios disponíveis nesse compartilhamento.

O resultado confirmado é a possibilidade de conectar-se e listar nomes de arquivos e diretórios. Não há registro de leitura, cópia ou alteração dos arquivos; portanto, não afirmamos que o conteúdo deles foi acessado.

## Resultado e impacto

O acesso anônimo expôs a estrutura e os nomes dos itens listados no compartilhamento. Dependendo do conteúdo e das permissões, uma configuração semelhante pode revelar informações operacionais ou permitir ações não autorizadas. Neste laboratório, não há evidência documentada de leitura ou escrita dos arquivos.

## Recomendações de segurança

- Desabilitar acesso convidado/anônimo quando não houver necessidade explícita.
- Restringir cada compartilhamento às contas e aos grupos necessários.
- Aplicar o menor privilégio; disponibilizar leitura apenas quando necessária e escrita somente a usuários autorizados.
- Limitar a exposição SMB às redes e máquinas que precisam do serviço.
- Monitorar acessos anônimos, conexões e alterações nos compartilhamentos.
- Manter o Samba atualizado e revisar sua configuração periodicamente.

## Limitações e atividades pendentes

Os resultados são os relatados para o laboratório; não há saídas brutas de Nmap ou `smbclient` incluídas neste repositório. A enumeração de usuários e o password spraying SMB continuam pendentes. Não inferir resultados para essas atividades a partir da enumeração de compartilhamentos.
