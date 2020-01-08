---
title: XML şemaları
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.xmleditor.schemasdialog
ms.assetid: 0271fa26-2205-49bd-96e0-ae1441571808
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d01c56b04a9b046f695a19d61a9b47fcac73e06
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592340"
---
# <a name="xml-schemas-dialog-box"></a>XML Şemaları iletişim kutusu

XML **şemaları** iletişim kutusu, bir XML BELGESIYLE ilişkilendirilecek XML şeması tanım DILI (xsd) şemalarını seçmek için kullanılır. Şema önbelleğinden bir şema seçebilir veya önbellekte bulunmayan bir şema belirtebilirsiniz. Seçili şemalar bir şema kümesinin parçası olarak kabul edilir. Şema kümesi IntelliSense ve ayrıca XML belge doğrulaması için kullanılır.

Belge Özellikleri penceresinde **şemalar** düğmesine tıklayarak veya **XML** menüsünden **şemalar** ' ı seçerek **XML şemaları** iletişim kutusuna erişebilirsiniz.

## <a name="uielement-list"></a>UIElement Listesi

**Kullanma**

XML şemasının nasıl kullanılacağını seçin.

- **Otomatik**. Bu şema geçerli belge tarafından kullanımda değil, ancak otomatik ilişkilendirme için kullanılabilir. XML belgesi, bu şemanın `targetNamespace` eşleşen bir ad alanı bildiriyorsa, şema otomatik olarak ilişkilendirilir ve şema kümesine dahil edilir.

- **Bu şemayı kullanın**. Bu şema geçerli belge tarafından kullanılıyor. Kullanıcı, bu şemanın bu sütuna tıklanarak kullanılmasını açıkça istedi, ya da şema eşleşen bir `targetNamespace`göre otomatik olarak ilişkilendirildi.

- **Seçili şemaları kullanmayın**. Şema eşleşen bir `targetNamespace`olsa bile, bu şema geçerli belge tarafından kullanılmaz. Bu ayar, şema önbelleğinde veya çözümünde aynı şemanın birden fazla sürümü olduğunda çakışmaları çözümlemek için yararlı olabilir.

**Hedef ad alanı**

XML şemasıyla ilişkili hedef ad alanını görüntüler.

**Dosya adı**

XML şeması dosya adını görüntüler.

**Ekle**

Şema kümesine eklemek üzere ek şemalar seçmenize olanak sağlayan, **Açık xsd şeması** iletişim kutusunu açar. Şema kümesine bir şema eklediğinizde, **Use** sütun değeri **Bu şemayı kullanacak**şekilde ayarlanır.

**Kaldır**

Seçili olan şemayı şema kümesinden kaldırır. Bu, şemayı bellek içi şema önbelleğinden kaldırır, ancak dosya sisteminden kaldırır.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: kullanılacak XML şemalarını seçme](../xml-tools/how-to-select-the-xml-schemas-to-use.md)
- [Şema önbelleği](../xml-tools/schema-cache.md)
