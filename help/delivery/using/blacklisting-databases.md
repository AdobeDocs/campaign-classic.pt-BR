---
title: Bancos de dados da blacklist
seo-title: Bancos de dados da blacklist
description: Bancos de dados da blacklist
seo-description: null
page-status-flag: never-activated
uuid: 8a4a69f9-87d5-4044-bc55-76cdcb2e7800
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: eede254d-2b25-46ed-b10f-fa1d54780a75
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: ac3a0ca00591943d79563e9fd4d85d71fa0ba81a

---


# Bancos de dados da blacklist{#blacklisting-databases}

Várias organizações mantêm bancos de dados de endereços IP e domínios que são reputados para serem usados por remetentes de spam. Consultar esses sites pode ser útil para entender por que determinadas mensagens foram rejeitadas como spam. Geralmente é possível solicitar a remoção de um endereço adicionado incorretamente a essas listas.

Esses bancos de dados são chamados de RBLs (Listas de Buraco Negro em Tempo Real) e são consultados por meio de um mecanismo DNS. Há três tipos de RBLs:

* Por endereço IP: lista endereços IP que enviam spam ou provavelmente retransmitem spam.
* Por domínio remetente: lista domínios de remetente (domínio completo do endereço de email de devolução) enviando spam ou configurado incorretamente.
* Por domínio da Web: lista os domínios (domínios de alto nível como registrados com os registradores) encontrados nas URLs dos links e imagens contidas no conteúdo de spam. No Adobe Campaign, o domínio a ser considerado em geral é o endereço usado para rastreamento.

Veja a seguir uma lista das RBLs mais utilizadas. Para obter uma lista mais abrangente, consulte [https://www.dnsstuff.com/](https://tools.dnsstuff.com/) (formulário &quot;Spam Blacklist Lookup&quot;).

* **Spamhaus**

   Consulte [https://www.spamhaus.org/](https://www.spamhaus.org/)

   O banco de dados é mais importante. Estar classificado nesta lista geralmente é uma situação grave. Se isso acontecer, você deverá agir IMEDIATAMENTE e avisar serviços comerciais, deliverability e suporte ao Adobe Campaign.

* **SpamCop**

   Consulte [https://www.spamcop.net/](https://www.spamcop.net/)

   É um dos bancos de dados mais conhecidos. Se um dos seus endereços IP for colocado nessa lista, isso geralmente significa que os usuários do SpamCop declararam suas mensagens como spam ou que você enviou mensagens para uma armadilha SpamCop.

* **URIBL**

   Consulte [https://www.uribl.com/](https://www.uribl.com/)

   Esta lista identifica os domínios que aparecem regularmente nas mensagens declaradas como spam. Se o seu domínio aparecer nessa lista, ele poderá afetar significativamente seu deliverability. Você deve informar os serviços deliverability e o suporte ao Adobe Campaign imediatamente.

* **SURBL**

   Consulte [https://www.surbl.org/](https://www.surbl.org/)

   SURBL identifica os sites que aparecem regularmente como spam. Se o seu domínio aparecer nessa lista, ele poderá afetar significativamente seu deliverability. Você deve informar os serviços deliverability e o suporte ao Adobe Campaign imediatamente.

* **iX Manitu**

   Esta é uma lista de IPs amplamente usada na Alemanha. Consulte [https://www.heise.de/ix/nixspam/](https://www.heise.de/ix/nixspam/)

<!--* SORBS

  [https://www.nl.sorbs.net](https://www.nl.sorbs.net) compiles a list of IP addresses that are reputed to be dynamic IP address (i.e. attributed temporarily to ISP subscribers) or "open relay" addresses. Certain domains check whether the IP address of a sender is not listed on this site before accepting email. Checking the IP addresses on this site can prove useful.-->