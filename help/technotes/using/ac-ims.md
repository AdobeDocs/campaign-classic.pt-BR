---
title: Migrar para o Adobe Identity Management System (IMS)
description: Saiba como migrar seu processo de autenticação para o Adobe Identity Management System (IMS)
exl-id: 84853dbe-8b6f-4875-b29a-c1b755423a3c
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 5%

---

# Migrar para o Adobe Identity Management System (IMS) {#migrate-to-ims}

Como parte do esforço para reforçar a segurança e o processo de autenticação, a Adobe Campaign recomenda migrar o modo de autenticação do usuário final da autenticação nativa de logon/senha para o [Adobe Identity Management System (IMS)](https://helpx.adobe.com/br/enterprise/using/identity.html){target="_blank"}.

Além disso, o aplicativo cliente do Adobe Campaign agora chama APIs do Campaign diretamente usando o token da conta técnica IMS. Você deve migrar os operadores técnicos para o Adobe Developer Console.

>[!CAUTION]
>
>Essa alteração já é aplicável no Campaign Classic v7 e será **obrigatória** para mover para o Campaign v8. A autenticação de usuário/senha nativa não é permitida no Campaign v8. **A Adobe recomenda executar essa migração a partir do Campaign v7.3.5 para facilitar a migração para o Campaign v8.**
>

## Etapas de migração {#ims-steps}

A migração para o [Adobe Identity Management System (IMS)](https://helpx.adobe.com/br/enterprise/using/identity.html){target="_blank"} é uma obrigação de segurança para tornar seus ambientes seguros e padronizados, pois a maioria das outras soluções e aplicativos da Adobe Experience Cloud já está no IMS.

O Adobe ajuda você nesse esforço de migração. Você pode encontrar contexto detalhado e diretrizes passo a passo nos artigos abaixo:

* A migração para autenticação de usuários finais está detalhada em [esta página](migrate-users-to-ims.md).
* A migração para autenticação de operadores técnicos está detalhada em [esta página](ims-migration.md).
* A partir do Campaign v7.4.1, habilite a interface do usuário e as restrições de API para remover opções e recursos específicos da autenticação nativa, conforme detalhado em [esta página](impact-ims-migration.md).


## Versões compatíveis com a migração IMS {#ims-versions}

Um pré-requisito para essa migração é atualizar seu ambiente para uma das seguintes versões de produto:

* Campaign v7.4.1 (recomendado)
* Campaign v7.3.5
* Campaign v7.3.3.IMS
* Campaign v7.3.2.IMS

Essas versões do Campaign estão detalhadas nas [Notas de versão](../../rn/using/latest-release.md).

## Perguntas frequentes {#ims-migration-faq}

### Quando posso iniciar a migração? {#ims-migration-start}

Uma recomendação para a migração para o [Adobe Identity Management System (IMS)](https://helpx.adobe.com/br/enterprise/using/identity.html){target="_blank"} é atualizar seu ambiente para o Campaign Classic v7.4.1 (ou uma [versão compatível com a migração do IMS](#ims-versions)).

Você pode iniciar a migração IMS no ambiente de preparo depois que ele for atualizado para a versão mais recente e planejar adequadamente o ambiente de produção.

### O que acontece após a atualização de build para o Campaign Classic v7.4.1? {#ims-migration-after-upgrade}

Depois que seus ambientes forem atualizados para o Campaign Classic v7.4.1 (ou uma [versão compatível com a migração IMS](#ims-versions)), você poderá iniciar sua transição para o [Adobe Identity Management System (IMS)](https://helpx.adobe.com/br/enterprise/using/identity.html){target="_blank"}.

### Quando a migração é concluída? {#ims-migration-end}

Depois que a migração do usuário final e a migração do(s) operador(es) técnico(s) para o Adobe Identity Management System (IMS) forem concluídas, você deverá atualizar seu ambiente para remover as opções específicas da autenticação nativa e que não se aplicam mais à autenticação IMS. Esta atualização só está disponível a partir do Campaign v7.4.1. [Saiba mais](impact-ims-migration.md)



## Links úteis {#ims-useful-links}

* [Migração de usuários finais para o IMS](migrate-users-to-ims.md)
* [Migração de operadores técnicos para o console do Adobe Developer](ims-migration.md)
* [Notas de versão mais recentes do Adobe Campaign Classic v7](../../rn/using/latest-release.md)
* [O que é o Sistema Adobe Identity Management (IMS)](https://helpx.adobe.com/br/enterprise/using/identity.html){target="_blank"}
