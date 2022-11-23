---
product: campaign
title: Solução de problemas no ACS Connector
description: Solução de problemas no ACS Connector
audience: integrations
content-type: reference
topic-tags: acs-connector
hide: true
hidefromtoc: true
exl-id: 4693dca1-ee55-43f0-b3dc-62a5b67a8058
source-git-commit: 978da934b483a54509ad806f375d9b2bb0577dac
workflow-type: ht
source-wordcount: '870'
ht-degree: 100%

---

# Solução de problemas no ACS Connector{#troubleshooting-the-acs-connector}

![](../../assets/v7-only.svg)

Dependendo da sua implementação, você pode enfrentar vários problemas comuns.

* **Quais são as diferenças da interface do usuário entre o Campaign Standard e o Campaign v7?**

   O Campaign Standard e o Campaign v7 funcionam de formas semelhantes. A maioria dos conceitos é o mesmo, mas em alguns casos, a abordagem pode ser um pouco diferente. Aqui estão alguns dos conceitos que podem ser diferentes no contexto do ACS Connector:

<table> 
 <thead> 
  <tr> 
   <th> Campaign v7<br /> </th> 
   <th> Campaign Standard<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> recipients (ou qualquer outra dimensão de perfil)<br /> </td> 
   <td> perfis<br /> </td> 
  </tr> 
  <tr> 
   <td> lista<br /> </td> 
   <td> público-alvo<br /> </td> 
  </tr> 
  <tr> 
   <td> workflows da campanha, workflows para construção do target<br /> </td> 
   <td> workflows<br /> </td> 
  </tr> 
  <tr> 
   <td> operações<br /> </td> 
   <td> campanhas<br /> </td> 
  </tr> 
  <tr> 
   <td> aplicações Web<br /> </td> 
   <td> páginas de aterrissagem<br /> </td> 
  </tr> 
  <tr> 
   <td> tabela e extensão de schema personalizadas<br /> </td> 
   <td> recursos e extensão de recursos personalizados<br /> </td> 
  </tr> 
  <tr> 
   <td> membros seed<br /> </td> 
   <td> perfis de teste<br /> </td> 
  </tr> 
 </tbody> 
</table>

* **Os recipients da minha instância do Campaign v7 não são sincronizados nem visíveis no Campaign Standard.**

   Esse caso pode ocorrer por motivos diferentes:

   * Os recipients recém-criados ou atualizados no Campaign v7. A sincronização é acionada a cada 15 minutos. Isso significa que os recipients atualizados ou recém-criados estarão visíveis no Campaign Standard após a próxima sincronização.
   * Sua implementação pode ter sido definida para sincronizar apenas recipients de pastas específicas. Os recipients de outras pastas não são sincronizados.
   * O recipient pode ser sincronizado, mas está visível no Campaign Standard. Verifique os direitos de mapear pastas.

* **Não encontro os campos de perfil que preciso para basear meu query no Campaign Standard.**

   Por padrão, 20 campos da tabela nms:recipient são sincronizados com o Campaign Standard. Consulte a lista detalhada de campos sincronizados. Qualquer campo adicional que você precise recuperar no Campaign Standard deve ser mapeado e configurado pelo seu consultor.

   Para garantir que o campo que você deseja usar está disponível, verifique a definição de recurso de perfil em **[!UICONTROL Administration > Development > Diagnosis > Data schemas]**.

   Além disso, todos os dados anexados aos recipients e armazenados em tabelas relacionadas a nms:recipients não são sincronizados por padrão para o Campaign Standard.

   Para poder usar dados relacionados, é possível executar seu direcionamento no Campaign v7 e inserir dados adicionais, conforme explicado na seção [Sincronizar públicos](../../integrations/using/synchronizing-audiences.md), ou entre em contato com seu consultor para explorar as possibilidades de personalização.

* **Estou usando outra dimensão de perfil do nms:recipient no Campaign v7, como posso sincronizá-la com o Campaign Standard?**

   O Campaign Standard usa um recurso de target exclusivo chamado **perfis**. A implementação básica do recurso Campaign Standard Connect fornece um mapeamento padrão entre os recipients do Campaign v7 e os perfis do Campaign Standard.

   Se você usar outra dimensão de perfil no Campaign v7 ou se usar várias, elas deverão ser mapeadas com perfis do Campaign Standard. Entre em contato com seu consultor para abordar essa necessidade específica.

* **Quero compartilhar uma lista de perfis com o Campaign Standard por meio de um workflow, mas não consigo encontrar meu público no Campaign Standard**.

   Os públicos podem ser encontrados no menu **[!UICONTROL Audiences]** do Campaign Standard. Eles têm o rótulo especificado na atividade **[!UICONTROL List update]** do workflow do Campaign v7. Eles estão sujeitos ao mapeamento de pastas definido durante a implementação.

   A primeira coisa a verificar é se o workflow finalizou sem erro. Se você observar um erro na atividade **[!UICONTROL List update]**, significa que a sincronização com o Campaign Standard pode ter falhado. Para ver mais detalhes do que deu errado, acesse **[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**. Esta pasta contém workflows de sincronização acionados pela execução da atividade **[!UICONTROL List update]**.

   Além disso, verifique se a opção **[!UICONTROL Share with ACS]** está marcada na atividade **[!UICONTROL List update]** e se o workflow foi executado corretamente.

   Observe que os perfis de recipients contidos na lista devem ter sido sincronizados com o Campaign Standard antes da execução do workflow. Depois de compartilhado com o Campaign Standard, os recipients da lista são reconciliados com perfis do Campaign Standard, significando que eles devem existir lá. Os recipients da lista que não podem ser reconciliados com perfis do Campaign Standard são ignorados.

   Se você compartilhar uma lista feita de perfis e se nenhuma for sincronizada com o Campaign Standard, ele criará um Query vazio de público no Campaign Standard que não pode ser usado.

* **Recebi uma notificação informando que um workflow de sincronização está em estado de erro. O que devo fazer?**

   Verifique a configuração da conta externa no Campaign Standard e Campaign v7 testando a conexão:

   * **[!UICONTROL acsDefaultRelayAccount]** no Campaign Standard.
   * **[!UICONTROL acsDefaultAccount]** no Campaign v7.

* **Não tenho nenhum grupo de segurança disponível ao mapear pastas entre o Campaign v7 e o Campanha Standard.**

   Você precisa primeiro sincronizar seus grupos de segurança em **[!UICONTROL Administration > ACS Connector > Rights management > Security groups]**. Essa ação verifica os grupos de segurança disponíveis no Campaign Standard. Após a sincronização, você pode localizar os grupos de segurança ao configurar o mapeamento da pasta.

* **Não consigo editar um perfil, um público ou uma landing page no Campaign Standard. O que isso significa?**

   Os recursos sincronizados do Campaign v7 estão no modo somente leitura no Campaign Standard para garantir a consistência dos dados. Se você precisar editar um desses elementos, poderá fazer isso no Campaign v7 e depois replicar a alteração no Campaign Standard.

* **Erros ocorrem no fluxo de trabalho de replicação do log de entrega do perfil do [ACS]. O que devo fazer?**

   Caso ambas as instâncias do Campaign Classic e do Campaign Standard sejam usadas para enviar emails com URLs rastreadas, um problema com tagIds de URL duplicadas pode ocorrer durante a sincronização. Nesse caso, o fluxo de trabalho de replicação do log de entrega do perfil do **[ACS]** (newRcpDeliveryLogReplication) falhará com o seguinte erro:

   ```PGS-220000 PostgreSQL error: ERROR: duplicate key value violates unique constraint "nmstrackingurl_tagid" DETAIL: Key (stagid) = (1c7bdec2) already exists.```

   Para resolver o problema e evitar que ele ocorra novamente, atualize a atividade **Atualizar URLs de rastreamento** (writerTrackingUrls) no fluxo de trabalho e adicione o prefixo “ACS” à expressão de origem @tagId.
