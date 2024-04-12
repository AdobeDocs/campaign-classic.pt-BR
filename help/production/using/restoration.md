---
product: campaign
title: Restauração
description: Restauração
feature: Monitoring
badge-v7-prem: label="Somente no local/híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: ba4db1af-778c-4c34-9a3c-49f41faa49b5
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '76'
ht-degree: 14%

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
