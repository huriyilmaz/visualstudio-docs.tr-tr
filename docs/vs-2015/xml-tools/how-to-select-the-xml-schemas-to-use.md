---
title: 'Nasıl yapılır: kullanılacak XML şemalarını seçme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f607d500bfcb8a745bfb129490d2c2b09c6b105c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666513"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Nasıl Yapılır: Kullanılacak XML Şemalarını Seçme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML Düzenleyicisi,%InstallDir%\Xml\Schemas dizininde bulunan bir şema önbelleği sağlar. Şema önbelleği, IntelliSense ve XML belge doğrulaması için kullanılan iyi bilinen XML şemaları içerir.

 **Şemalar** belgesi özelliği, kullanılacak bir veya daha fazla XML şeması tanım DILI (xsd) şeması seçmek için kullanılır. Şema önbelleğinden şemaları seçmenizi veya önbellekte bulunmayan bir şemayı belirtmenizi sağlar.

 Belirttiğiniz şemalar, diğer tüm XML belge özellikleriyle birlikte gizli çözüm Kullanıcı seçenekleri dosyasına (. suo) kaydedilir. Sonuç olarak, çözümü bir sonraki açışınızda bu değerleri yeniden girmeniz gerekmez.

> [!NOTE]
> Düzenleyici, satır içi bir şemanın veya özniteliğin başvurduğu bir şemanın kullanımını doğrulayabilir `xsd:schemaLocation` . Daha fazla bilgi için bkz. [XML belge doğrulaması](../xml-tools/xml-document-validation.md).

### <a name="to-select-an-xml-schema-from-the-schema-cache"></a>Şema önbelleğinden bir XML şeması seçmek için

1. XML düzenleyicisinde bir dosya açın.

2. Belge Özellikleri penceresinde, **şemalar** alanındaki düğmesine tıklayın.

    **XML şemaları** iletişim kutusu görüntülenir. İletişim kutusu, şema önbelleğinde. xsd uzantılı tüm şemaları (catalog.xml dosyasında başvurulan şemalar dahil) ve aynı zamanda geçerli çözümdeki herhangi bir şemayı, bir `xsd:schemaLocation` öznitelikte başvurulan veya **şemalar** özelliğinde başvurulan Visual Studio 'da açık olarak listeler.

3. Aşağıdakilerden birini yaparak doğrulama için kullanılacak şemaları seçin:

   - **XML şemaları** iletişim kutusunda listelenen bir şemayı seçin, **kullan** sütununa tıklayın ve **Bu şemayı kullan**' ı seçin.

     -veya-

   - **XML şemaları** iletişim kutusunda listelenmiş birden çok şema seçin, sağ tıklayın ve **Bu şemayı kullan**' ı seçin.

4. **Tamam**’a tıklayın.

    Seçilen şemaların listesi, **şemalar** belge özelliğine geri kopyalanır.

### <a name="to-add-an-xml-schema-to-the-schema-cache"></a>Şema önbelleğine bir XML şeması eklemek için

1. Belge Özellikleri penceresinde, **şemalar** alanındaki düğmesine tıklayın.

2. **Ekle**'ye tıklayın.

     Bu, **Open xsd şeması** iletişim kutusunu açar.

3. Şema önbelleğine eklenecek şemaya gözatıp seçin.

4. **Aç**’a tıklayın.

     Şema önbelleğine eklenen şema (ler) ve **kullanım** sütunu değeri **Bu şemayı kullanacak**şekilde ayarlanır.

### <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>Şema önbelleğinden bir XML şemasını silmek için

1. Belge Özellikleri penceresinde, **şemalar** alanındaki düğmesine tıklayın.

2. Kaldırılacak şemayı seçin ve ardından **Kaldır**' a tıklayın.

     Şema, bellek içi şema önbelleğinden kaldırılır, ancak dosya sisteminden kaldırılmaz.

    > [!NOTE]
    > Şemaya hala bir özniteliği aracılığıyla başvurunuz varsa `schemaLocation` veya eşleşen bir eşleme varsa, `targetNamespace` Bu durum otomatik ilişkilendirme **Remove** nedeniyle bu durumda çalışmaz. Bu durumda, şemayı **Use** sütununda **Seçili şemaları kullanmayın** olarak işaretlemeniz önerilir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Şema önbelleği](../xml-tools/schema-cache.md) [XML şemaları Iletişim kutusu](../xml-tools/xml-schemas-dialog-box.md) [XML Düzenleyicisi](../xml-tools/xml-editor.md)
