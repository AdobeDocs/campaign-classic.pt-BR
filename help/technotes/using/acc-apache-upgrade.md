---
product: campaign
title: Nota técnica - Adobe Campaign - Atualização de segurança da versão do Apache
description: Adobe Campaign - Atualização de segurança da versão do Apache
hide: true
hidefromtoc: true
exl-id: 3d2f5d1d-4b31-4cc6-b6fb-13589856e00c
source-git-commit: a3eae4e253f66f5a651ffe0458f60b1f8bdf2258
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 3%

---

# Adobe Campaign - Atualização de segurança da versão do Apache {#apache-update}

>[!CAUTION]
>Este artigo aplica-se a: **Campaign Classic v7 Managed Services** clientes, **Campanha v8** clientes e **Campaign Standard** clientes.

O Adobe Campaign trabalha com ferramentas de terceiros e a compatibilidade é atualizada regularmente, a fim de implementar somente as versões compatíveis e se beneficiar das correções e melhorias mais recentes.

O Adobe Campaign inclui o Apache Tomcat, que atua como ponto de entrada no servidor de aplicativos via HTTP e é integrado ao servidor da Web Apache. A Apache Software Foundation lançou o Apache HTTP Server 2.4.53. Esta versão aborda vulnerabilidades que podem permitir que um invasor remoto assuma o controle de um sistema afetado. Saiba mais em [Anúncio do Apache 2.4.53](https://downloads.apache.org/httpd/Announcement2.4.html){target="_blank"}.

A equipe da Adobe Campaign realizará a atividade de atualização de segurança da versão do Apache ao **15 de junho de 2022** para mitigar essa vulnerabilidade do Apache e tornar seu ambiente de instância mais seguro. Essa atualização se aplica a todos os clientes do Campaign Classic v7 Managed Services, Campaign v8 e Campaign Standard em execução em uma versão vulnerável do Apache HTTP Server. Se você for afetado, o Adobe já entrou em contato para informá-lo sobre essa atualização.

Essa atualização deve ser executada automaticamente fora do horário comercial normal para que você continue usando o serviço do Campaign sem interrupções.

As instâncias que não são de produção serão atualizadas pelo Adobe primeiro, e as instâncias de produção serão atualizadas. Como esse é um processo de atualização automático de propriedade do Adobe, não há necessidade de ação de seu lado. No entanto, se tiver problemas, entre em contato com [Atendimento ao cliente do Adobe](https://experienceleague.adobe.com/?support-solution=Campaign#support).


>[!NOTE]
>Essa atualização requer o para reiniciar o servidor Web Apache. O tempo de inatividade não excederá 10 minutos no período mencionado abaixo.

## Perguntas frequentes {#apache-faq}

* **Por que essa é uma atualização obrigatória?**

   A versão atual do Apache é vulnerável e tem uma possível ameaça à segurança. É importante que sua(s) instância(s) do Campaign seja(m) atualizada(s) para a versão mais recente do Apache aplicável para lidar com o risco de segurança.

* **Quais clientes são direcionados para atualizações de segurança?**

   Todos os clientes que usam ambientes do Campaign implementados em versões mais antigas do Apache são atualizados para a versão mais recente aplicável do Apache.

* **Qual é o tempo de inatividade esperado?**

   O tempo de inatividade esperado é inferior a 10 minutos.

* **Há alguma ação necessária do cliente para essa atualização de segurança?**

   Nenhuma ação é necessária, pois a atualização de segurança será executada automaticamente.

* **Qual é o impacto nas campanhas/workflows em execução durante a janela de manutenção?**

   Durante a janela de manutenção, o workflow e os serviços de email serão interrompidos e as atividades agendadas não serão executadas. Todas as atividades em andamento ou processos em execução serão interrompidas durante o tempo de inatividade até que o servidor seja reiniciado. Quando a atividade for concluída e o servidor for reiniciado, todos os serviços serão retomados.

* **Quais validações precisam ser executadas pelos clientes?**

   Não é necessário nenhum teste específico para esta atualização de segurança. Caso algum problema seja observado, entre em contato com o [Atendimento ao cliente do Adobe](https://experienceleague.adobe.com/?support-solution=Campaign#support).


* **Posso solicitar uma alteração em Data/Hora para o slot de atualização de segurança agendado?**

   Como essa é uma correção de segurança, recomendamos que você se adapte ao agendamento existente.


Para qualquer outra pergunta, entre em contato com o [Atendimento ao cliente da Adobe](https://experienceleague.adobe.com/?support-solution=Campaign#support).
