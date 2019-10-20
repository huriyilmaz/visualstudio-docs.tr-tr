---
title: 'Nasıl yapılır: kullanılacak XML şemalarını seçme'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 275def786a93d42e6b8e110d3b3d785a24e948b1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601905"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Nasıl yapılır: kullanılacak XML şemalarını seçme

XML Düzenleyicisi, *%VSInstallDir%\Xml\Schemas* dizininde bulunan bir şema önbelleği sağlar. Şema önbelleği, IntelliSense ve XML belge doğrulaması için kullanılan iyi bilinen XML şemaları içerir.

Bir veya daha fazla XML şeması tanım dili (XSD) şeması seçmek için **şemalar** belge özelliğini kullanın. Şema önbelleğinden veya başka bir yerde şemaları seçebilirsiniz.

Belirttiğiniz şemalar bir (gizli) çözüm Kullanıcı seçenekleri dosyasına (. *suo*), diğer tüm XML belge özellikleriyle birlikte. Sonuç olarak, çözümü bir sonraki açışınızda bu değerleri yeniden girmeniz gerekmez.

> [!NOTE]
> Düzenleyici, satır içi bir şemanın veya `xsd:schemaLocation` özniteliği tarafından başvurulan bir şemanın kullanımını doğrulayabilir. Daha fazla bilgi için bkz. [XML belge doğrulaması](../xml-tools/xml-document-validation.md).

## <a name="to-select-an-xml-schema-from-the-schema-cache"></a>Şema önbelleğinden bir XML şeması seçmek için

1. XML düzenleyicisinde bir dosya açın.

2. Belge Özellikleri penceresinde, **şemalar** alanına tıklayın. Gezinme düğmesi (...) göründüğünde, bu düğmeye tıklayın.

   ![XML dosyası için Schemas özelliği](media/properties-schemas.png)

   [XML şemaları iletişim kutusu](xml-schemas-dialog-box.md) açılır. İletişim kutusu, içeren tüm şemaları listeler. şema önbelleğinde ( *Catalog. xml* dosyasında başvurulan şemalar dahil) *XSD* uzantısı ve ayrıca geçerli çözümdeki herhangi bir şema, bir `xsd:schemaLocation` özniteliğinde başvurulan veya **şemalarda** başvurulan Visual Studio 'da aç özelliði.

3. Aşağıdakilerden birini yaparak doğrulama için kullanılacak şemaları seçin:

   - **XML şemaları** iletişim kutusunda listelenen bir şemayı seçin, **kullan** sütununa tıklayın ve **Bu şemayı kullan**' ı seçin.

     veya

   - **XML şemaları** iletişim kutusunda birden çok şema seçin ve sağ tıklayın ve **Bu şemayı kullan**' ı seçin.

4. **Tamam ' ı**seçin.

   Seçilen şemaların listesi, **şemalar** belge özelliğine geri kopyalanır.

## <a name="to-add-an-xml-schema-to-the-schema-cache"></a>Şema önbelleğine bir XML şeması eklemek için

1. Belge Özellikleri penceresinde, **şemalar** alanındaki düğmesine tıklayın.

2. **Ekle**'yi tıklatın.

   **Open xsd şeması** iletişim kutusu açılır.

3. Şema önbelleğine eklenecek şemaya gözatıp seçin.

4. **Aç**' a tıklayın.

   Şemalar şema önbelleğine eklenir ve **Use** sütun değeri **Bu şemayı kullanacak**şekilde ayarlanır.

## <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>Şema önbelleğinden bir XML şemasını silmek için

1. Belge Özellikleri penceresinde, **şemalar** alanındaki düğmesine tıklayın.

2. Kaldırılacak şemayı seçin ve ardından **Kaldır**' a tıklayın.

   Şema, bellek içi şema önbelleğinden kaldırılır, ancak dosya sisteminden kaldırılmaz.

   > [!NOTE]
   > Şemaya hala bir `schemaLocation` özniteliği aracılığıyla başvurunuz varsa veya eşleşen bir `targetNamespace`, otomatik ilişkilendirme nedeniyle bu durumda **kaldırma** çalışmaz. Bu durumda, şemayı **Use** sütununda **Seçili şemaları kullanmayın** olarak işaretlemeniz önerilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Şema önbelleği](../xml-tools/schema-cache.md)
- [XML şemaları iletişim kutusu](../xml-tools/xml-schemas-dialog-box.md)
- [XML Düzenleyicisi](../xml-tools/xml-editor.md)