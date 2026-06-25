---
product: campaign
title: Solução de problemas no Conector ACS
description: Solução de problemas no Conector ACS
feature: ACS Connector, Troubleshooting
audience: integrations
content-type: reference
topic-tags: acs-connector
hide: true
exl-id: 4693dca1-ee55-43f0-b3dc-62a5b67a8058
TQID: https://experienceleague.adobe.com/hqQ4rSZpOoCMn9sA0yu2VsHFxTGEnwGwOMi6cu6e-1Q
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: c5474392-5419-4296-9e41-f6f4ce4f6e9bid: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2: id: cbcf4d90-26be-46e2-b16a-aebc529dc41eid: df0d6518-6f49-46e2-b46e-3bcc513f553fid: eb007b6d-6e57-46ab-9485-3f24d6102304id: b1fd1501-3105-4d6b-b4d4-9af53126df75
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: c1579802-ddd4-4214-8a91-97b2066abe11id: d095671a-1355-40aa-8b5f-06c33c68080bid: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 870
ht-degree: 100%

---

# Solução de problemas no Conector ACS{#troubleshooting-the-acs-connector}



Dependendo da sua implementação, você pode enfrentar vários problemas comuns.

* **Quais são as diferenças da interface do usuário entre o Campaign Standard e o Campaign v7?**

  O Campaign Standard e o Campaign v7 funcionam de formas semelhantes. A maioria dos conceitos é o mesmo, mas em alguns casos, a abordagem pode ser um pouco diferente. Aqui estão alguns dos conceitos que podem ser diferentes no contexto do Conector ACS:

<table> 
 <thead> 
  <tr> 
   <th> Campaign v7<br /> </th> 
   <th> Campaign Standard<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> destinatários (ou qualquer outra dimensão de perfil)<br /> </td> 
   <td> perfis<br /> </td> 
  </tr> 
  <tr> 
   <td> lista<br /> </td> 
   <td> público-alvo<br /> </td> 
  </tr> 
  <tr> 
   <td> fluxos de trabalho da campanha, fluxos de trabalho de segmentação<br /> </td> 
   <td> fluxos de trabalho<br /> </td> 
  </tr> 
  <tr> 
   <td> operações<br /> </td> 
   <td> campanhas<br /> </td> 
  </tr> 
  <tr> 
   <td> aplicações Web<br /> </td> 
   <td> páginas de destino<br /> </td> 
  </tr> 
  <tr> 
   <td> tabela e extensão de esquema personalizadas<br /> </td> 
   <td> recursos e extensão de recursos personalizados<br /> </td> 
  </tr> 
  <tr> 
   <td> membros seed<br /> </td> 
   <td> perfis de teste<br /> </td> 
  </tr> 
 </tbody> 
</table>

* **Os destinatários da minha instância do Campaign v7 não são sincronizados nem visíveis no Campaign Standard.**

  Esse caso pode ocorrer por motivos diferentes:

   * Os destinatários recém-criados ou atualizados no Campaign v7. A sincronização é acionada a cada 15 minutos. Isso significa que os destinatários atualizados ou recém-criados estarão visíveis no Campaign Standard após a próxima sincronização.
   * Sua implementação pode ter sido definida para sincronizar apenas destinatários de pastas específicas. Os destinatários de outras pastas não são sincronizados.
   * O destinatário pode ser sincronizado, mas está visível no Campaign Standard. Verifique os direitos de mapear pastas.

* **Não encontro os campos de perfil que preciso para basear minha consulta no Campaign Standard.**

  Por padrão, 20 campos da tabela nms:recipient são sincronizados com o Campaign Standard. Consulte a lista detalhada de campos sincronizados. Qualquer campo adicional que você precise recuperar no Campaign Standard deve ser mapeado e configurado pelo seu consultor.

  Para garantir que o campo que você deseja usar está disponível, verifique a definição de recurso de perfil em **[!UICONTROL Administration > Development > Diagnosis > Data schemas]**.

  Além disso, todos os dados anexados aos destinatários e armazenados em tabelas relacionadas a nms:recipients não são sincronizados por padrão com o Campaign Standard.

  Para poder usar dados relacionados, é possível executar seu direcionamento no Campaign v7 e inserir dados adicionais, conforme explicado na seção [Sincronizar públicos-alvos](../../integrations/using/synchronizing-audiences.md), ou entre em contato com seu consultor para explorar as possibilidades de personalização.

* **Estou usando uma dimensão de perfil diferente do nms:recipient padrão no Campaign v7. Como posso sincronizá-la com o Campaign Standard?**

  O Campaign Standard usa um recurso de direcionamento exclusivo chamado **perfis**. A implementação básica do recurso Campaign Standard Connect fornece um mapeamento padrão entre os destinatários do Campaign v7 e os perfis do Campaign Standard.

  Se você usar outra dimensão de perfil no Campaign v7 ou se usar várias, elas deverão ser mapeadas com perfis do Campaign Standard. Entre em contato com seu consultor para abordar essa necessidade específica.

* **Quero compartilhar uma lista de perfis com o Campaign Standard por meio de um workflow, mas não consigo encontrar meu público-alvo no Campaign Standard**.

  Os públicos-alvos podem ser encontrados no menu **[!UICONTROL Audiences]** do Campaign Standard. Eles têm o rótulo especificado na atividade **[!UICONTROL List update]** do fluxo de trabalho do Campaign v7. Eles estão sujeitos ao mapeamento de pastas definido durante a implementação.

  A primeira coisa a verificar é se o fluxo de trabalho finalizou sem erro. Se você observar um erro na atividade **[!UICONTROL List update]**, significa que a sincronização com o Campaign Standard pode ter falhado. Para ver mais detalhes do que deu errado, acesse **[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**. Esta pasta contém fluxos de trabalho de sincronização acionados pela execução da atividade **[!UICONTROL List update]**.

  Além disso, verifique se a opção **[!UICONTROL Share with ACS]** está marcada na atividade **[!UICONTROL List update]** e se o fluxo de trabalho foi executado corretamente.

  Observe que os perfis de destinatários contidos na lista devem ter sido sincronizados com o Campaign Standard antes da execução do fluxo de trabalho. Depois de compartilhado com o Campaign Standard, os destinatários da lista são reconciliados com perfis do Campaign Standard, significando que eles devem existir lá. Os destinatários da lista que não podem ser reconciliados com perfis do Campaign Standard são ignorados.

  Se você compartilhar uma lista feita de perfis e se nenhuma for sincronizada com o Campaign Standard, ele criará um público-alvo de consulta vazio no Campaign Standard que não pode ser usado.

* **Recebi uma notificação informando que um fluxo de trabalho de sincronização está em estado de erro. O que devo fazer?**

  Verifique a configuração da conta externa no Campaign Standard e Campaign v7 testando a conexão:

   * **[!UICONTROL acsDefaultRelayAccount]** no Campaign Standard.
   * **[!UICONTROL acsDefaultAccount]** no Campaign v7.

* **Não tenho nenhum grupo de segurança disponível ao mapear pastas entre o Campaign v7 e o Campaign Standard.**

  Você precisa primeiro sincronizar seus grupos de segurança em **[!UICONTROL Administration > ACS Connector > Rights management > Security groups]**. Essa ação verifica os grupos de segurança disponíveis no Campaign Standard. Após a sincronização, você pode localizar os grupos de segurança ao configurar o mapeamento da pasta.

* **Não consigo editar um perfil, um público-alvo ou uma página de destino no Campaign Standard. O que isso significa?**

  Os recursos sincronizados do Campaign v7 estão no modo somente leitura no Campaign Standard para garantir a consistência dos dados. Se você precisar editar um desses elementos, poderá fazer isso no Campaign v7 e depois replicar a alteração no Campaign Standard.

* **Erros ocorrem no fluxo de trabalho de replicação do log de entrega do perfil do [ACS]. O que devo fazer?**

  Caso ambas as instâncias do Campaign Classic e do Campaign Standard sejam usadas para enviar emails com URLs rastreadas, um problema com tagIds de URL duplicadas pode ocorrer durante a sincronização. Nesse caso, o fluxo de trabalho de replicação do log de entrega do perfil do **[ACS]** (newRcpDeliveryLogReplication) falhará com o seguinte erro:

  `PGS-220000 PostgreSQL error: ERROR: duplicate key value violates unique constraint "nmstrackingurl_tagid" DETAIL: Key (stagid) = (1c7bdec2) already exists.`

  Para resolver o problema e evitar que ele ocorra novamente, atualize a atividade **Atualizar URLs de rastreamento** (writerTrackingUrls) no fluxo de trabalho e adicione o prefixo “ACS” à expressão de origem @tagId.
