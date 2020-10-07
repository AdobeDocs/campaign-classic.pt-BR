---
title: Versão 18.6
seo-title: Versão 18.6
description: Versão 18.6
seo-description: null
page-status-flag: never-activated
uuid: 72941f8f-0b84-4868-a768-8aa972459ef2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rn
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 79a6d3cf-2425-49b9-9b92-b56be26438bf
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '813'
ht-degree: 100%

---


# Versão 18.6{#release-18-6}

## Versão 18.6.2 - Build 8949{#release-18-6-3-build-8949}

22 de agosto de 2018

>[!CAUTION]
>
>Esta configuração foi retomada. [Atualize para a configuração mais recente](https://helpx.adobe.com/br/campaign/kb/acc-build-upgrade.html) ou entre em contato com o [suporte técnico](https://support.neolane.net/).

**Novidades**

<table> 
 <thead> 
  <tr> 
   <th> Funcionalidade<br /> </th> 
   <th> Descrição<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Faixas de query<br /> </td> 
   <td> <p>Quando vários usuários do Campaign se conectam à mesma conta externa FDA Teradata, agora você pode passar uma faixa de query (pares de chave-valor) específica para cada usuário. Sempre que um usuário do Campaign realizar um query no banco de dados Teradata, o Adobe Campaign agora poderá enviar metadados associados ao usuário. Esses dados, que consistem em uma lista de chaves e valores, podem ser então usados pelos administradores Teradata para fins de auditoria ou para gerenciar direitos de acesso, por exemplo.</p><p>Para obter mais informações, consulte a <a href="https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_External_accounts.html#Teradata_external_account">documentação detalhada</a>.</p> </td>
  </tr> 
 </tbody> 
</table>

**Aprimoramentos**

* Os logs de arquivamento de emails foram aprimorados, o que facilita e agiliza a verificação de quais emails foram entregues com êxito ou falharam no arquivamento do Cco. (NEO-10675)
* Correção de um problema que levou à exibição dos IPs do balanceador de carga em vez dos IPs do cliente no rastreamento de broadlogs. (NEO-11295)
* Correção de um problema aleatório que fazia com que as propriedades de um delivery fossem substituídas incorretamente. (NEO-11015)
* Correção de um erro de sintaxe ao classificar resultados da atividade de enriquecimento. (NEO-11394)
* Correção de um problema ao usar campos calculados em uma atividade de workflow **[!UICONTROL Survey answers]**. (NEO-11382)
* O Tomcat foi atualizado para evitar a exploração de vulnerabilidades. (NEO-11503)
* Correção de um erro com codificação LATIN1 ao usar um FDA Connection para um banco de dados PostgreSQL. (NEO-11299)
* Correção de um problema que ocorria ao usar a opção de delivery **[!UICONTROL Prepare the personalization data with a workflow]**. (NEO-11047)
* Correção de um problema postupgrade que impedia o envio de SMS ao usar um conector estendido.
* Importação/exportação de pacotes aprimorada (log e região foram adicionados à interface).
* Correção de um problema que exibia erros inúteis no log após a atualização quando uma atividade de workflow **[!UICONTROL Survey answers]** não estava totalmente configurada.

**Evoluções técnicas**

Faixas de query

Uma chave específica (PROXYUSER ou PROXYROLE) é usada para associar um usuário ou função Teradata a um usuário do Campaign. Uma nova permissão foi adicionada para usar este usuário/função proxy. É necessário adicionar o acesso GRANT CONNECT THROUGH à conta do banco de dados (aquele definido na conta externa do Teradata).

Uma nova guia foi adicionada nas contas externas do Teradata. A guia **[!UICONTROL Query banding]** inclui as seguintes opções:

* **[!UICONTROL Active]**: marque esta caixa para ativar o recurso.
* **[!UICONTROL Default]**: insira uma faixa de query padrão que será usada se um usuário não tiver nenhuma faixa de query associada. Se não houver faixa de query padrão definida, os usuários que não tiverem nenhuma faixa de query associada não poderão usar o Teradata.
* **[!UICONTROL Users]**: para cada usuário, especifique uma faixa de query. Você pode adicionar quantos pares chave-valor forem necessários. Por exemplo: &quot;priority=1;workload=high;&quot;

Para obter mais informações sobre faixa de query, consulte esses artigos:

* [https://docs.teradata.com/reader/cY5B~oeEUFWjgN2kBnH3Vw/a5G1iz~ve68yTMa24kVjVw](https://docs.teradata.com/reader/cY5B%7EoeEUFWjgN2kBnH3Vw/a5G1iz%7Eve68yTMa24kVjVw)
* [https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ)

## Versão 18.6 - Build 8947{#release-18-6-build-8947}

25 de junho de 2018

>[!CAUTION]
>
>Esta configuração foi retomada. [Atualize para a configuração mais recente](https://helpx.adobe.com/br/campaign/kb/acc-build-upgrade.html) ou entre em contato com o [suporte técnico](https://support.neolane.net/).

**Novidades**

<table> 
 <thead> 
  <tr> 
   <th> Funcionalidade<br /> </th> 
   <th> Descrição<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Melhorias de segurança<br /> </td> 
   <td> Uma série de aprimoramentos de segurança foi adicionada ao Campaign Classic. Os aprimoramentos e correções estão listados abaixo.<br /> </td> 
  </tr> 
  <tr> 
   <td> Suporte do Windows Server 2016<br /> </td> 
   <td> O Adobe Campaign agora é compatível com o Windows Server 2016. Consulte <a href="https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html">Matriz de compatibilidade do Campaign Classic</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Aprimoramentos de segurança**

decryptString

A função **decryptString** foi preterida. Consulte o artigo [Recursos Preteridos e Removidos](https://helpx.adobe.com/br/campaign/kb/deprecated-and-removed-features.html).

Para novos clientes, essa função agora é usada apenas para descriptografar a ID criptografada do recipient nas landing pages. Para descriptografar senhas armazenadas em uma conta externa, use a nova função **decryptPassword** .

Para clientes existentes, o comportamento dessa função não é alterado, mas recomendamos que você use **decryptPassword** em vez de **decryptString**. A opção de compatibilidade **XtkSecurity_Unsafe_DecryptString** é adicionada pelo postupgrade e ativada por padrão, permitindo que continue usando a função. Se deseja desativar o **decryptString**, desative a opção.

decryptPassword

A função **decryptPassword** foi adicionada. Permite descriptografar uma senha armazenada em uma conta externa. Consulte a documentação [JSAPI](https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html) para obter mais informações.

APIs de Arquivo

Para novas instalações, o acesso às pastas por meio de APIs de arquivo é limitado à **var**, **sftp** e pastas temporárias do Adobe Campaign.

Para clientes existentes, as APIs de arquivo não podem mais acessar a pasta **conf** do Adobe Campaign. A opção de compatibilidade **XtkSecurity_Disable_JSFileSandboxing** é adicionada pelo postupgrade e ativada por padrão, permitindo que continue acessando as outras pastas. Se você quiser limitar o acesso ao **var**, **sftp** e pastas temporárias do Adobe Campaign, desative a opção.

**Correção**

* Correção de um problema que poderia afetar o desempenho da mensagem transacional de SMS. (NEO-9812)
