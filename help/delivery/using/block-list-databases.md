---
solution: Campaign Classic
product: campaign
title: Bancos de dados da lista de bloqueios
description: Bancos de dados da lista de bloqueios
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: ht
source-git-commit: 3139a9bf5036086831e23acef21af937fcfda740
workflow-type: ht
source-wordcount: '392'
ht-degree: 100%

---


# Bancos de dados da lista de bloqueios{#denylist-databases}

Várias organizações mantêm bancos de dados de endereços IP e domínios que são reputados para serem usados por remetentes de spam. Consultar esses sites pode ser útil para entender por que determinadas mensagens foram rejeitadas como spam. Geralmente é possível solicitar a remoção de um endereço adicionado incorretamente a essas listas.

Esses bancos de dados são chamados de RBLs (Listas de Buraco Negro em Tempo Real) e são consultados por meio de um mecanismo DNS. Há três tipos de RBLs:

* Por endereço IP: lista endereços IP que enviam spam ou provavelmente retransmitem spam.
* Por domínio remetente: lista domínios de remetente (domínio completo do endereço de email de devolução) enviando spam ou configurado incorretamente.
* Por domínio da Web: lista os domínios (domínios de alto nível como registrados com os registradores) encontrados nas URLs dos links e imagens contidas no conteúdo de spam. No Adobe Campaign, o domínio a ser considerado em geral é o endereço usado para rastreamento.

Veja a seguir uma lista das RBLs mais utilizadas. Para obter uma lista mais abrangente, consulte [https://www.dnsstuff.com/](https://tools.dnsstuff.com/).

* **Spamhaus**

   Consulte [https://www.spamhaus.org/](https://www.spamhaus.org/)

   O banco de dados é mais importante. Estar classificado nesta lista geralmente é uma situação grave. Se isso acontecer, você deverá agir IMEDIATAMENTE e avisar os serviços comerciais, a capacidade de entrega e o [Atendimento ao cliente da Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

* **SpamCop**

   Consulte [https://www.spamcop.net/](https://www.spamcop.net/)

   É um dos bancos de dados mais conhecidos. Se um dos seus endereços IP for colocado nessa lista, isso geralmente significa que os usuários do SpamCop declararam suas mensagens como spam ou que você enviou mensagens para uma armadilha SpamCop.

* **URIBL**

   Consulte [https://www.uribl.com/](https://www.uribl.com/)

   Esta lista identifica os domínios que aparecem regularmente nas mensagens declaradas como spam. Se o seu domínio aparecer nessa lista, ele poderá afetar significativamente seu deliverability. Você deve informar os serviços de capacidade de entrega e o [Atendimento ao cliente da Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) imediatamente.

* **SURBL**

   Consulte [http://www.surbl.org/](http://www.surbl.org/)

   SURBL identifica os sites que aparecem regularmente como spam. Se o seu domínio aparecer nessa lista, ele poderá afetar significativamente seu deliverability. Você deve informar os serviços de capacidade de entrega e o [Atendimento ao cliente da Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) imediatamente.

* **iX Manitu**

   Esta é uma lista de IPs amplamente usada na Alemanha. Consulte [https://www.heise.de/ix/nixspam/](https://www.heise.de/ix/nixspam/)

<!--* SORBS

  [https://www.nl.sorbs.net](https://www.nl.sorbs.net) compiles a list of IP addresses that are reputed to be dynamic IP address (i.e. attributed temporarily to ISP subscribers) or "open relay" addresses. Certain domains check whether the IP address of a sender is not listed on this site before accepting email. Checking the IP addresses on this site can prove useful.-->