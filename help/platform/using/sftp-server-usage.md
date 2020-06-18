---
title: Uso do servidor SFTP
seo-title: Uso do servidor SFTP
description: Uso do servidor SFTP
seo-description: null
page-status-flag: never-activated
uuid: 5281058d-91bd-4f98-835d-1d46dc7b8b1f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
discoiquuid: f449ccd5-3965-4ab8-b5a9-993f3260aba9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: fecfff477b0750782c87c017a15e306acac4c61d
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 89%

---


# Uso do servidor SFTP{#sftp-server-usage}

## Práticas recomendadas do servidor SFTP {#sftp-server-best-practices}

Ao gerenciar arquivos e dados para fins de ETL, esses arquivos são armazenados em um servidor SFTP hospedado fornecido pela Adobe. Este SFTP foi projetado para ser um espaço de armazenamento temporário no qual você pode controlar a retenção e exclusão de arquivos.

Quando não é usado ou monitorado corretamente, esse espaço pode preencher rapidamente o espaço físico disponível no servidor e provocar arquivos truncados nos envios subsequentes. Quando o espaço está saturado, a limpeza automática pode ativar e apagar os arquivos mais antigos do armazenamento SFTP.

Para evitar esses problemas, a Adobe recomenda seguir as práticas recomendadas abaixo.

>[!NOTE]
>
>Se sua instância estiver hospedada no AWS, é possível monitorar o armazenamento do servidor SFTP com o [Painel de Controle](https://docs.adobe.com/content/help/pt-BR/control-panel/using/sftp-management/sftp-storage-management.html) do Campaign Classic.
>
>Para verificar se sua instância está hospedada no AWS, siga as etapas detalhadas [nessa seção](https://docs.adobe.com/content/help/pt-BR/control-panel/using/faq.html#ims-org-id) .

* As capacidades do tamanho do servidor variam de acordo com sua licença. Em qualquer caso, mantenha o mínimo de dados possíveis e somente pelo tempo necessário (o limite máximo de tempo é 15 dias).
* Para evitar a expiração de senhas, use a autenticação baseada em chave (as senhas têm um período de validade de 90 dias). Além disso, a autenticação baseada nessa opção permite gerar várias chaves para gerenciar diversas entidades, por exemplo. Ao contrário, essa opção de autenticação exige que a senha seja compartilhada com todas as entidades gerenciadas.

   O formato de chave compatível é SSH-2 RSA 2048. As chaves podem ser geradas com ferramentas como PuTTY (Windows) ou ssh-keygen (Unix). Será necessário fornecer a chave pública ao suporte da Adobe por meio de um [tíquete de suporte](https://support.neolane.net) para carregá-lo no servidor do Campaign.

* Use workflows para excluir corretamente os dados (gerencie a retenção de workflows consumindo os dados).
* Use em lotes em uploads de SFTP e em workflows.
* Manipule erros/exceções.
* Ocasionalmente, conecte-se no SFTP para verificar diretamente o que encontra-se lá.
* Lembre-se de que o gerenciamento de disco SFTP é predominantemente sua responsabilidade.
* Por padrão, todas as pastas criadas estão em modo de leitura/gravação somente para o seu identificador. Ao criar pastas que precisam ser acessadas pelo Campaign, certifique-se de configurá-las com direitos de leitura/gravação para todo o grupo. Caso contrário, os workflows podem não ser capazes de criar/excluir arquivos como são executados em um identificador diferente no mesmo grupo por motivos de segurança.
* Os IPs públicos dos quais você está tentando iniciar a conexão SFTP devem ser adicionados à lista de permissões na instância da Campanha. A adição de endereços IP à lista de permissões pode ser solicitada por meio de um ticket [de](https://support.neolane.net)suporte.

>[!CAUTION]
>
>Se você usar o seu próprio servidor SFTP, certifique-se de seguir as recomendações o máximo possível mencionadas acima.

## Solução de problemas do servidor SFTP {#sftp-server-troubleshooting}

A seção abaixo lista as informações para verificar e fornecer ao suporte da Adobe por meio de um [tíquete de suporte](https://support.neolane.net) ao encontrar problemas de conexão com os servidores SFTP hospedados pela Adobe.

1. Verifique se a sua instância está em execução. To do this, open your browser, then make a **[!UICONTROL GET]** call on the instance **[!UICONTROL /r/test]** endpoint:

   ```
   https://instanceUrl/r/test
   ```

   Se a instância estiver em execução, você deverá obter este tipo de resposta:

   ```
   <redir status='OK' date='YYYY-MM-DD HH:MM:SS' build='XXXX' instance='instanceName'
   sourceIP='AAA.BB.CCC.DD' host='instanceUrl' localHost='instanceName'/>
   ```

   Em qualquer caso, forneça a resposta do comando no tíquete de suporte.

1. Verifique se a porta de saída 22 está aberta no site do qual você está tentando iniciar a conexão SFTP. Para fazer isso, use o seguinte comando:

   ```
   bash-3.2$ nc -vz <SFTP_URL> 22
   # Replace the SFTP_URL with actual SFTP instance URL
   # If the port 22 is opened you will see output similar to the below one
   # for e.g. the  output for the command on myCompany-stage-sftp.neolane.net after ssh-out, will give
   bash-3.2$ nc -vz myCompagny-stage-sftp.neolane.net 22
   myCompany-stage-sftp.neolane.net [AAA.BBB.CCC.D] 22 (ssh) open
   ```

   >[!NOTE]
   >
   >A ferramenta Netcat permite gerenciar facilmente as conexões de rede em vários sistemas operacionais (consulte [https://eternallybored.org/misc/netcat/](https://eternallybored.org/misc/netcat/)).

   Se a porta não for aberta, certifique-se de abrir as conexões de saída em seu lado e tente novamente. Se ainda houver problemas de conexão, compartilhe o resultado do comando com o suporte da Adobe.

1. Verifique se o IP público do qual você está tentando iniciar a conexão SFTP é aquele fornecido ao suporte da Adobe para a lista de permissões.
1. Se você usa uma autenticação baseada em senha, a senha pode ter expirado (as senhas têm um período de validade de 90 dias). Portanto, recomendamos usar uma autenticação baseada em chave (consulte [Práticas recomendadas para o servidor SFTP](#sftp-server-best-practices)).
1. Se você estiver usando uma autenticação baseada em chave, verifique se a chave usada é a mesma fornecida ao suporte da Adobe para a configuração de instância.
1. Se você estiver usando FileZilla ou uma ferramenta de FTP equivalente, forneça os detalhes dos logs de conexão no ticket de suporte.

