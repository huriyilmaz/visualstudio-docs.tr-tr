---
title: XML şemaları
description: Bir XML belgesi ile ilişkilendirilecek XML şeması tanım dili (XSD) şemalarını seçmek için kullanılan XML şemaları iletişim kutusu hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.xmleditor.schemasdialog
ms.assetid: 0271fa26-2205-49bd-96e0-ae1441571808
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1c91e97d0508ab85893409386ddd3ab9dded7f45
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874852"
---
# <a name="xml-schemas-dialog-box"></a>XML Şemaları iletişim kutusu

XML **şemaları** iletişim kutusu, bir XML BELGESIYLE ilişkilendirilecek XML şeması tanım DILI (xsd) şemalarını seçmek için kullanılır. Şema önbelleğinden bir şema seçebilir veya önbellekte bulunmayan bir şema belirtebilirsiniz. Seçili şemalar bir şema kümesinin parçası olarak kabul edilir. Şema kümesi IntelliSense ve ayrıca XML belge doğrulaması için kullanılır.

Belge Özellikleri penceresinde **şemalar** düğmesine tıklayarak veya **XML** menüsünden **şemalar** ' ı seçerek **XML şemaları** iletişim kutusuna erişebilirsiniz.

## <a name="uielement-list"></a>UIElement Listesi

**Kullanım**

XML şemasının nasıl kullanılacağını seçin.

- **Otomatik**. Bu şema geçerli belge tarafından kullanımda değil, ancak otomatik ilişkilendirme için kullanılabilir. XML belgesi, bu şemanın ile eşleşen bir ad alanı bildiriyorsa `targetNamespace` , şema otomatik olarak ilişkilendirilir ve şema kümesine dahil edilir.

- **Bu şemayı kullanın**. Bu şema geçerli belge tarafından kullanılıyor. Kullanıcı, bu şemanın bu sütuna tıklanarak kullanılmasını açıkça istedi, ya da şema eşleşen bir temel alınarak otomatik olarak ilişkilendirildi `targetNamespace` .

- **Seçili şemaları kullanmayın**. Bu şema, şemanın eşleşen bir eşleşmesine sahip olsa bile geçerli belge tarafından kullanılmaz `targetNamespace` . Bu ayar, şema önbelleğinde veya çözümünde aynı şemanın birden fazla sürümü olduğunda çakışmaları çözümlemek için yararlı olabilir.

**Hedef ad alanı**

XML şemasıyla ilişkili hedef ad alanını görüntüler.

**Dosya adı**

XML şeması dosya adını görüntüler.

**Ekle**

Şema kümesine eklemek üzere ek şemalar seçmenize olanak sağlayan, **Açık xsd şeması** iletişim kutusunu açar. Şema kümesine bir şema eklediğinizde, **Use** sütun değeri **Bu şemayı kullanacak** şekilde ayarlanır.

**Kaldır**

Seçili olan şemayı şema kümesinden kaldırır. Bu, şemayı bellek içi şema önbelleğinden kaldırır, ancak dosya sisteminden kaldırır.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: kullanılacak XML şemalarını seçme](../xml-tools/how-to-select-the-xml-schemas-to-use.md)
- [Şema önbelleği](../xml-tools/schema-cache.md)
