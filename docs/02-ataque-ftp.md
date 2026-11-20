# 02 — Teste controlado de autenticação FTP

## Status e objetivo

**Realizado** no laboratório descrito em [01 — Configuração do ambiente](01-configuracao-ambiente.md). O objetivo foi verificar se combinações preparadas para o exercício permitiam autenticação no serviço FTP do Metasploitable 2.

## Conceitos

FTP (File Transfer Protocol) é um protocolo usado para transferir arquivos. Na configuração tradicional, os dados de autenticação e o conteúdo transferido não são criptografados. Alguém capaz de observar o tráfego pode obter informações sensíveis. SFTP e FTPS são alternativas distintas que protegem a comunicação e devem ser configuradas de acordo com a necessidade.

Força bruta é a tentativa sistemática de várias combinações de autenticação. Uma wordlist contém valores candidatos, como nomes de conta e senhas, usados em um teste autorizado. O risco aumenta quando uma senha fraca ou previsível é aceita por um serviço.

Medusa é uma ferramenta que automatiza testes de autenticação em serviços compatíveis. No laboratório, foi usada para verificar combinações de uma lista preparada contra o serviço FTP. A automação não comprova por si só a validade de um resultado; por isso, uma autenticação identificada foi validada separadamente no próprio serviço.

## Preparação das wordlists

Foram preparadas listas para o exercício. Os arquivos e os valores não são distribuídos neste repositório. Para um laboratório seguro, use somente dados sintéticos e autorizados, mantenha listas fora do controle de versão quando houver dúvida sobre sua origem e não inclua senhas reais, reutilizadas ou dados pessoais.

## Metodologia

1. Preparar Kali Linux e Metasploitable 2 na rede Host-Only do laboratório.
2. Verificar que o serviço FTP está disponível no alvo autorizado.
3. Preparar as listas de candidatos para o exercício, sem credenciais reais.
4. Usar Medusa para realizar o teste controlado dentro do escopo do laboratório.
5. Validar uma credencial identificada por meio de uma autenticação FTP no mesmo serviço.
6. Registrar somente o resultado necessário, sem divulgar valores de acesso ou detalhes da infraestrutura.

Não são reproduzidos comandos, endereços, nomes de conta, senhas, contagens ou parâmetros específicos da execução.

## Resultado observado

Foram identificadas credenciais válidas e a autenticação foi confirmada no serviço FTP do laboratório. Os valores não são informados. O resultado demonstra que uma combinação testada foi aceita naquele serviço e momento; não permite concluir se a credencial era reutilizada nem estimar impacto em outros sistemas.

## Análise do risco

A aceitação de credenciais encontradas em um conjunto de candidatos é compatível com risco de senha fraca, previsível ou inadequadamente gerenciada. O teste não determina sozinho a causa, nem comprova que outras contas ou serviços estejam vulneráveis. Em ambientes reais, uma credencial exposta pode permitir acesso não autorizado e, conforme as permissões associadas, leitura ou alteração de dados.

## Recomendações de mitigação

- Desabilitar FTP sem criptografia quando não for necessário; avaliar SFTP ou FTPS para transferências protegidas.
- Usar senhas únicas e robustas, remover contas desnecessárias e substituir credenciais padrão.
- Aplicar limitação de tentativas e atrasos proporcionais, com cuidado para evitar bloqueios indevidos e indisponibilidade.
- Restringir o acesso ao serviço por segmentação de rede e regras de firewall.
- Aplicar menor privilégio às contas e revisar permissões.
- Monitorar falhas e sucessos de autenticação sem registrar senhas ou outros segredos.

## Limitações

O resultado se limita ao serviço FTP do laboratório e às informações resumidas neste documento. Não há uma contagem de tentativas nem a linha de comando exata registrada. DVWA, enumeração de usuários SMB e password spraying SMB não foram realizados; a enumeração de compartilhamentos SMB está documentada em [04 — Enumeração SMB](04-enumeracao-smb.md).
