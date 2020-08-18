---
title: Práticas recomendadas e solução de problemas do servidor SFTP
description: Saiba mais sobre as práticas recomendadas e a solução de problemas do servidor SFTP.
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
source-git-commit: ee4addc88c6169603122259437d5cb0362851aa6
workflow-type: tm+mt
source-wordcount: '1003'
ht-degree: 63%

---


# Práticas recomendadas e solução de problemas do servidor SFTP {#sftp-server-usage}

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

## Problemas de conexão com o servidor SFTP hospedado no Adobe {#sftp-server-troubleshooting}

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

1. Verifique se o IP público a partir do qual você está tentando iniciar a conexão SFTP é aquele fornecido ao Suporte ao Adobe para a lista de permissões.
1. Se você usa uma autenticação baseada em senha, a senha pode ter expirado (as senhas têm um período de validade de 90 dias). Portanto, recomendamos usar uma autenticação baseada em chave (consulte [Práticas recomendadas para o servidor SFTP](#sftp-server-best-practices)).
1. Se você estiver usando uma autenticação baseada em chave, verifique se a chave usada é a mesma fornecida ao suporte da Adobe para a configuração de instância.
1. Se você estiver usando FileZilla ou uma ferramenta de FTP equivalente, forneça os detalhes dos logs de conexão no ticket de suporte.

## Erro &quot;Não foi possível resolver o nome do host&quot;, erro de upload no cURL

Esta seção fornece informações sobre as verificações e ações a serem executadas ao obter o &quot;Não foi possível resolver o nome do host&quot;. após conectar-se ao servidor FTP a partir do Campaign Classic.

O journal de fluxo de trabalho mostra os seguintes registros:

```
16/05/2016 12:49:03    fileTransfer    Upload error in cURL
16/05/2016 12:49:03    fileTransfer    Couldn't resolve host name
16/05/2016 12:49:03    fileTransfer    Couldn't resolve host name
16/05/2016 12:49:03    fileTransfer    Starting transfer of '/usr/local/neolane/nl6/var/williamreed/export/Recipients' to 'ftp://213.253.61.250/Recipients'
16/05/2016 12:49:03    fileTransfer    1 file(s) to transfer
```

Este erro ocorre ao tentar conectar o servidor FTP a partir de um fluxo de trabalho e baixar os arquivos do servidor, enquanto você ainda pode se conectar via FTP usando FileZilla ou WinSCP.

Esse erro indica que o nome de domínio do servidor FTP não pôde ser resolvido corretamente. Para solucionar problemas, faça o seguinte:

1. Solução de problemas de configuração **do servidor** DNS:

   1. Verifique se o nome do servidor foi adicionado ao servidor DNS local.
   1. Se sim, execute o seguinte comando no servidor Adobe Campaign para obter o endereço IP:

   `nslookup <server domain name>`

   Isso confirma que o servidor FTP está funcionando e acessível no servidor de aplicativos Adobe Campaign.

1. Solução de problemas de registros **de sessão**:

   1. No fluxo de trabalho, clique com o duplo do mouse na atividade de transferência [de](../../workflow/using/file-transfer.md) arquivos.
   1. Vá para a **[!UICONTROL File Transfer]** guia e clique em **[!UICONTROL Advanced Parameters]**.
   1. Marque a opção **[!UICONTROL Display the session logs]**.

   ![](assets/sftp-error-display-logs.png)

   1. Vá para a Auditoria de fluxo de trabalho e verifique se os registros mostram o erro &quot;Não foi possível resolver o nome do host&quot;.

   Se o servidor SFTP estiver hospedado pelo Adobe, verifique se o IP foi adicionado à lista de permissões entrando em contato com o Atendimento ao cliente.

   Caso contrário, valide:

   * A senha não contém &#39;@&#39;. A conexão falhará se houver &#39;@&#39; na senha.
   * Não há problemas de firewall que possam impedir a comunicação entre o servidor de aplicativos Adobe Campaign e o servidor SFTP.
   * Execute comandos tracert e telnet do servidor de campanha para o sftp para ver se há problemas de conexão.
   * Não há problemas de protocolo de comunicação.
   * Porta aberta.
