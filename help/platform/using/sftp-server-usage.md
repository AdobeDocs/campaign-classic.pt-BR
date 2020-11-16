---
title: Uso do servidor SFTP
description: Saiba mais sobre as práticas recomendadas e a solução de problemas do servidor SFTP.
page-status-flag: never-activated
uuid: 5281058d-91bd-4f98-835d-1d46dc7b8b1f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
discoiquuid: f449ccd5-3965-4ab8-b5a9-993f3260aba9
translation-type: tm+mt
source-git-commit: cb2fb5a338220c54aba96b510a7371e520c2189e
workflow-type: tm+mt
source-wordcount: '1007'
ht-degree: 92%

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

   O formato de chave compatível é SSH-2 RSA 2048. Keys can be generated with tools like PyTTY (Windows), or ssh-keygen (Unix).You will have to provide the public key to Adobe Support team via [Adobe Customer Care](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) to have it uploaded on the Campaign server.

* Use workflows para excluir corretamente os dados (gerencie a retenção de workflows consumindo os dados).
* Use em lotes em uploads de SFTP e em workflows.
* Manipule erros/exceções.
* Ocasionalmente, conecte-se no SFTP para verificar diretamente o que encontra-se lá.
* Lembre-se de que o gerenciamento de disco SFTP é predominantemente sua responsabilidade.
* Por padrão, todas as pastas criadas estão em modo de leitura/gravação somente para o seu identificador. Ao criar pastas que precisam ser acessadas pelo Campaign, certifique-se de configurá-las com direitos de leitura/gravação para todo o grupo. Caso contrário, os workflows podem não ser capazes de criar/excluir arquivos como são executados em um identificador diferente no mesmo grupo por motivos de segurança.
* Os IPs públicos a partir dos quais você está tentando iniciar a conexão SFTP devem ser adicionados à lista de permissões na instância do Campaign. Adding IP addresses to the allowlist can be requested via [Adobe Customer Care](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

>[!CAUTION]
>
>Se você usar o seu próprio servidor SFTP, siga as recomendações mencionadas acima o máximo possível.

## Problemas de conexão com o servidor SFTP hospedado pela Adobe {#sftp-server-troubleshooting}

The section below lists the information to check and provide to the Adobe Support team via [Adobe Customer Care](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) when encountering connection issues with Adobe hosted SFTP servers.

1. Verifique se a sua instância está em execução. Para fazer isso, abra o navegador e faça uma chamada **[!UICONTROL GET]** no ponto de extremidade da instância **[!UICONTROL /r/test]**:

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

1. Verifique se o IP público a partir do qual você está tentando iniciar a conexão do SFTP foi o informado ao suporte da Adobe para ser incluído na lista de permissões.
1. Se você usa uma autenticação baseada em senha, a senha pode ter expirado (as senhas têm um período de validade de 90 dias). Portanto, recomendamos usar uma autenticação baseada em chave (consulte [Práticas recomendadas para o servidor SFTP](#sftp-server-best-practices)).
1. Se você estiver usando uma autenticação baseada em chave, verifique se a chave usada é a mesma fornecida ao suporte da Adobe para a configuração de instância.
1. Se você estiver usando FileZilla ou uma ferramenta de FTP equivalente, forneça os detalhes dos logs de conexão no ticket de suporte.

## Erro “Não foi possível resolver o nome do host”

Esta seção fornece informações sobre as verificações e ações a serem executadas ao obter o erro “Não foi possível resolver o nome do host” após a conexão com o servidor FTP pelo Campaign Classic.

O journal de workflow mostra os seguintes logs:

```
16/05/2016 12:49:03    fileTransfer    Upload error in cURL
16/05/2016 12:49:03    fileTransfer    Couldn't resolve host name
16/05/2016 12:49:03    fileTransfer    Couldn't resolve host name
16/05/2016 12:49:03    fileTransfer    Starting transfer of '/usr/local/neolane/nl6/var/williamreed/export/Recipients' to 'ftp://213.253.61.250/Recipients'
16/05/2016 12:49:03    fileTransfer    1 file(s) to transfer
```

Este erro ocorre ao tentar conectar o servidor FTP a partir de um workflow e baixar os arquivos do servidor enquanto você ainda pode se conectar via FTP usando o FileZilla ou WinSCP.

Esse erro indica que o nome de domínio do servidor FTP não pôde ser resolvido corretamente. Para solucionar problemas, faça o seguinte:

1. Solução de problemas de **configuração do servidor DNS**:

   1. Verifique se o nome do servidor foi adicionado ao servidor DNS local.
   1. Em caso positivo, execute o seguinte comando no servidor do Adobe Campaign para obter o endereço IP:

      `nslookup <server domain name>`

      Essa ação confirma se o servidor FTP funciona e está acessível no servidor de aplicativos do Adobe Campaign.

1. Solução de problemas de **logs de seção**:

   1. No workflow, dê um duplo clique na atividade de [transferência de arquivos](../../workflow/using/file-transfer.md).
   1. Acesse a guia **[!UICONTROL File Transfer]** e clique em **[!UICONTROL Advanced Parameters]**.
   1. Marque a opção **[!UICONTROL Display the session logs]**.

      ![](assets/sftp-error-display-logs.png)

   1. Acesse a auditoria de workflow e verifique se os logs mostram o erro “Não foi possível resolver o nome do host”.

1. Se o servidor SFTP for hospedado pela Adobe, verifique através do Atendimento ao cliente se o IP foi adicionado à lista de permissões.

   Caso contrário, verifique se:

   * A senha não contém “@”. A conexão falhará se houver “@” na senha.
   * Não há problemas de firewall que possam impedir a comunicação entre o servidor de aplicativos do Adobe Campaign e o servidor SFTP.
   * Execute comandos tracert e telnet no servidor da campanha para o sftp a fim de verificar problemas de conexão.
   * Não há problemas de protocolo de comunicação.
   * A porta está aberta.
