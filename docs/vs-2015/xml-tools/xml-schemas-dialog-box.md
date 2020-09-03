---
title: XML şemaları Iletişim kutusu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 0271fa26-2205-49bd-96e0-ae1441571808
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d637cb3c25772685d5a782eb74bf94878ded36c2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669430"
---
# <a name="xml-schemas-dialog-box"></a>XML Şemaları İletişim Kutusu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML **şemaları** iletişim kutusu, bir XML BELGESIYLE ilişkilendirilecek XML şeması tanım DILI (xsd) şemalarını seçmek için kullanılır. Şema önbelleğinden bir şema seçebilir veya önbellekte bulunmayan bir şema belirtebilirsiniz. Seçili şemalar bir şema kümesinin parçası olarak kabul edilir. Şema kümesi IntelliSense ve ayrıca XML belge doğrulaması için kullanılır.

 Belge Özellikleri penceresinde **şemalar** düğmesine tıklayarak veya **XML** menüsünden **şemalar** ' ı seçerek **XML şemaları** iletişim kutusuna erişebilirsiniz.

## <a name="uielement-list"></a>UIElement Listesi
 **Kullanım** XML şemasının nasıl kullanılacağını seçin.

- **Otomatik**. Bu şema geçerli belge tarafından kullanımda değil, ancak otomatik ilişkilendirme için kullanılabilir. XML belgesi, bu şemanın ile eşleşen bir ad alanı bildiriyorsa `targetNamespace` , şema otomatik olarak ilişkilendirilir ve şema kümesine dahil edilir.

- **Bu şemayı kullanın**. Bu şema geçerli belge tarafından kullanılıyor. Kullanıcı, bu şemanın bu sütuna tıklanarak kullanılmasını açıkça istedi, ya da şema eşleşen bir temel alınarak otomatik olarak ilişkilendirildi `targetNamespace` .

- **Seçili şemaları kullanmayın**. Bu şema, şemanın eşleşen bir eşleşmesine sahip olsa bile geçerli belge tarafından kullanılmaz `targetNamespace` . Bu ayar, şema önbelleğinde veya çözümünde aynı şemanın birden fazla sürümü olduğunda çakışmaları çözümlemek için yararlı olabilir.

  **Hedef ad alanı** XML şemasıyla ilişkili hedef ad alanını görüntüler.

  **Dosya adı** XML şeması dosya adını görüntüler.

  **Ekle** Şema kümesine eklemek üzere ek şemalar seçmenize olanak sağlayan, **Açık xsd şeması** iletişim kutusunu açar. Şema kümesine bir şema eklediğinizde, **Use** sütun değeri **Bu şemayı kullanacak**şekilde ayarlanır.

  **Kaldır** Seçili olan şemayı şema kümesinden kaldırır. Bu, şemayı bellek içi şema önbelleğinden kaldırır, ancak dosya sisteminden kaldırır.

## <a name="see-also"></a>Ayrıca Bkz.
 [XML Düzenleyicisi bileşenleri](../xml-tools/xml-editor-components.md) [nasıl yapılır: şema ÖNBELLEĞI kullanmak Için XML şemaları seçme](../xml-tools/how-to-select-the-xml-schemas-to-use.md) [Schema Cache](../xml-tools/schema-cache.md)
