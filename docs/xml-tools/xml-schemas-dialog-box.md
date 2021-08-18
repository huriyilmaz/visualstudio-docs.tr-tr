---
title: XML şemaları
description: XML belgesiyle ilişkilendirilen XML şema tanımı dilini (XSD) seçmek için kullanılan XML Şemaları iletişim kutusu hakkında bilgi edinmek için.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.xmleditor.schemasdialog
ms.assetid: 0271fa26-2205-49bd-96e0-ae1441571808
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: ce4aee5707144abd086056f0022cc4aac44618db
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122122585"
---
# <a name="xml-schemas-dialog-box"></a>XML Şemaları iletişim kutusu

**XML Şemaları iletişim** kutusu, bir XML belgesiyle ilişkilendirilen XML şema tanımlama dili (XSD) şemalarını seçmek için kullanılır. Şema önbelleğinden bir şemayı seçin veya önbellekte yer alan bir şema belirtin. Seçilen şemalar bir şema kümesi kapsamında kabul edilir. Şema kümesi IntelliSense ve xml belge doğrulaması için kullanılır.

XML Şemaları **iletişim kutusuna,** belge özellikleri **penceresindeki** Şemalar düğmesine tıklayarak veya XML menüsünden **Şemalar'ı** seçerek **erişebilirsiniz.**

## <a name="uielement-list"></a>UIElement Listesi

**Kullanım**

XML Şemasının nasıl kullan olacağını seçin.

- **Otomatik**. Bu şema geçerli belge tarafından kullanım dışıdır, ancak otomatik ilişkilendirme için kullanılabilir. XML belgesi bu şemayla eşleşen bir ad alanı bildirecekse şema otomatik olarak ilişkilendirilecek `targetNamespace` ve şema kümesine dahil edilir.

- **Bu şemayı kullanın.** Bu şema geçerli belge tarafından kullanılıyor. Kullanıcı bu sütuna tıklayarak bu şemanın açıkça kullanılmalarını ister veya şema eşleşen bir temel alarak otomatik olarak `targetNamespace` ilişkilendirildi.

- **Seçili şemaları kullanmayın.** Bu şema, eşleşen bir şemaya sahip olsa bile geçerli belge tarafından `targetNamespace` kullanılmaz. Bu ayar, şema önbelleğinde veya çözümünde aynı şemanın birden fazla sürümü olduğunda çakışmaları çözümlemek için yararlı olabilir.

**Hedef Ad Alanı**

XML Şeması ile ilişkili hedef ad alanını görüntüler.

**Dosya Adı**

XML Şeması dosya adını görüntüler.

**Ekle**

Şema **kümesine ek şemalar** eklemenizi sağlayan XSD Şemasını Aç iletişim kutusunu açar. Şema kümesine bir şema eklerken Sütun **kullan değeri Bu** şemayı kullan olarak **ayarlanır.**

**Kaldır**

Seçili olan şemayı şema kümesinden kaldırır. Bu, bellek içinde şema önbelleğinden şemayı kaldırır, ancak dosya sisteminden kaldırır.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Kullanmak üzere XML şemalarını seçme](../xml-tools/how-to-select-the-xml-schemas-to-use.md)
- [Şema önbelleği](../xml-tools/schema-cache.md)
