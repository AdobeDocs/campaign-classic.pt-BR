---
product: campaign
title: Restauração
description: Restauração
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: ba4db1af-778c-4c34-9a3c-49f41faa49b5
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '65'
ht-degree: 4%

---

# Restauração{#restoration}



Em um servidor limpo, o procedimento de restauração é o seguinte:

* em um sistema operacional instalado e configurado (redes),
* instalar aplicativos de terceiros: servidor Web, JDK (se necessário),
* instalar binários do Adobe Campaign com a mesma build do sistema de origem,
* copiar arquivos de configuração, logs de rastreamento e arquivos de redirecionamento,
* criar e recriar o banco de dados,
* inicie o Adobe Campaign.

Para obter mais informações, consulte **Guia de instalação**.
