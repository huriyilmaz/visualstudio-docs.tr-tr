---
title: XML belgesi özellikleri, Özellikler penceresi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f620cc2bd189dccf067c6276f760d21cde5cf05e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669513"
---
# <a name="xml-document-properties-properties-window"></a>XML Belge Özellikleri, Özellik Penceresi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Özellikler** PENCERESI, XML düzenleyicisinde etkin olan belge hakkında temel bilgiler sağlar. Kullanılabilir özellikler, şu anda etkin olan XML belgesinin türüne bağlı olarak değişir.

> [!NOTE]
> Tüm XML belgesi özellikleri çözüme kaydedilir. Sonuç olarak, çözümü bir sonraki açışınızda bu değerleri yeniden girmeniz gerekmez.

 **Kodlama** Dosya için karakter kodlaması. Bu özelliğin değiştirilmesi, XML bildiriminde kodlama özniteliğini de değiştirir ve tam tersi de geçerlidir. Yeni kodlama dosyayı kaydettiğinizde dosyayı kodlamak için kullanılacaktır.

 **Giriş** XSLT stil sayfasıyla ilişkili giriş belgesi. **Showxslt output** komutu tarafından kullanılır. Bir belge, gezinme (**...**) düğmesi kullanılarak seçilebilir.

 Bu özellik yalnızca düzenleyici penceresinde şu anda etkin olan bir XSLT dosyası olduğunda görülebilir.

 **Çıkış** Bir XML belgesi dönüştürülürken oluşturulan dosya.

 Bir dosya belirtilmemişse, `method` `xsl:output` dosya uzantısını belirleyen öğesindeki özniteliği temel alarak varsayılan bir dosya adı oluşturulur. Varsayılan dosya, geçerli kullanıcının geçici dizininde bulunur.

 **Şemalar** Doğrulama için kullanılacak şemalar. Düğme, kullanılacak şemaları seçmek için kullanılabilecek **xsd şemaları** iletişim kutusunu açar.

 Ayrıca, şemaların yolunu da girebilirsiniz. Birden çok şema belirtilirse, her şema yolunun çift tırnak içine alınması gerekir.

 **Stil sayfası** **XSLT çıkışını göster** komutu kullanıldığında belgeyi dönüştürmek IÇIN kullanılan XSLT dosyası. **XSLT çıkışını göster** komutu kullanıldığında bu alan boşsa, düzenleyici `xml-stylesheet` belgenin işleme yönergesinde belirtilen değeri kullanır veya dosya adını ister.

 XSLT dosyasını düzenlenirken, bu özellik **XSLT çıktısını göster** veya **XSLT** 'yi görüntüle komutu seçildiğinde farklı bir stil sayfasının kullanılması gerektiğini belirtmek için kullanılabilir. Örneğin, bir üst stil sayfasına dahil olan bir stil sayfasını düzenlediğinizde bunu yapmak isteyebilirsiniz.

## <a name="see-also"></a>Ayrıca Bkz.
 [XML Düzenleyicisi](../xml-tools/xml-editor.md) [XML Düzenleyicisi bileşenleri](../xml-tools/xml-editor-components.md)
