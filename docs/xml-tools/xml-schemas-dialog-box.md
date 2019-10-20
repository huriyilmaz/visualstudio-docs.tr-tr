---
title: XML şemaları
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.xmleditor.schemasdialog
ms.assetid: 0271fa26-2205-49bd-96e0-ae1441571808
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 11743756ffd8f59520448d2687dbada6d4eaca40
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72608043"
---
# <a name="xml-schemas-dialog-box"></a>XML Şemaları iletişim kutusu

XML **şemaları** iletişim kutusu, bir XML BELGESIYLE ilişkilendirilecek XML şeması tanım DILI (xsd) şemalarını seçmek için kullanılır. Şema önbelleğinden bir şema seçebilir veya önbellekte bulunmayan bir şema belirtebilirsiniz. Seçili şemalar bir şema kümesinin parçası olarak kabul edilir. Şema kümesi IntelliSense ve ayrıca XML belge doğrulaması için kullanılır.

Belge Özellikleri penceresinde **şemalar** düğmesine tıklayarak veya **XML** menüsünden **şemalar** ' ı seçerek **XML şemaları** iletişim kutusuna erişebilirsiniz.

## <a name="uielement-list"></a>UIElement Listesi

**Kullanırsınız**

XML şemasının nasıl kullanılacağını seçin.

- **Otomatik**. Bu şema geçerli belge tarafından kullanımda değil, ancak otomatik ilişkilendirme için kullanılabilir. XML belgesi, bu şemanın `targetNamespace` eşleşen bir ad alanı bildiriyorsa, şema otomatik olarak ilişkilendirilir ve şema kümesine dahil edilir.

- **Bu şemayı kullanın**. Bu şema geçerli belge tarafından kullanılıyor. Kullanıcı, bu şemanın bu sütuna tıklanarak kullanılmasını açıkça istedi, ya da şema eşleşen bir `targetNamespace` göre otomatik olarak ilişkilendirildi.

- **Seçili şemaları kullanmayın**. Şema eşleşen bir `targetNamespace` olsa bile, bu şema geçerli belge tarafından kullanılmaz. Bu ayar, şema önbelleğinde veya çözümünde aynı şemanın birden fazla sürümü olduğunda çakışmaları çözümlemek için yararlı olabilir.

**Hedef ad alanı**

XML şemasıyla ilişkili hedef ad alanını görüntüler.

**Dosya adı**

XML şeması dosya adını görüntüler.

**Add**

Şema kümesine eklemek üzere ek şemalar seçmenize olanak sağlayan, **Açık xsd şeması** iletişim kutusunu açar. Şema kümesine bir şema eklediğinizde, **Use** sütun değeri **Bu şemayı kullanacak**şekilde ayarlanır.

**Kaldır**

Seçili olan şemayı şema kümesinden kaldırır. Bu, şemayı bellek içi şema önbelleğinden kaldırır, ancak dosya sisteminden kaldırır.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: kullanılacak XML şemalarını seçme](../xml-tools/how-to-select-the-xml-schemas-to-use.md)
- [Şema önbelleği](../xml-tools/schema-cache.md)