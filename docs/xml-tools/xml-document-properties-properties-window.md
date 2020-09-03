---
title: XML Belge Özellikleri, Özellik Penceresi
ms.date: 03/05/2019
ms.topic: reference
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1b21f4435737597136e1ac4a4dd8651decaf4c65
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75592431"
---
# <a name="xml-document-properties-properties-window"></a>XML belgesi özellikleri, Özellikler penceresi

**Özellikler** PENCERESI, XML düzenleyicisinde etkin olan belge hakkında temel bilgiler sağlar. Kullanılabilir özellikler, şu anda etkin olan XML belgesinin türüne bağlı olarak değişir.

> [!NOTE]
> Tüm XML belgesi özellikleri çözüme kaydedilir. Sonuç olarak, çözümü bir sonraki açışınızda bu değerleri yeniden girmeniz gerekmez.

**Kodlama**

Dosya için karakter kodlaması. Bu özelliğin değiştirilmesi, XML bildiriminde kodlama özniteliğini de değiştirir ve tam tersi de geçerlidir. Yeni kodlama dosyayı kaydettiğinizde dosyayı kodlamak için kullanılır.

**Girdi**

XSLT stil sayfasıyla ilişkili giriş belgesi. **Başlangıç XSLT** komutları tarafından kullanılır, örneğin, **XML**,  >  **hata ayıklama olmadan XSLT Başlat**. Bir belge, gezinme (**...**) düğmesi kullanılarak seçilebilir.

Bu özellik yalnızca düzenleyicide bir XSLT dosyası açıkken görünür.

**Çıktı**

Bir XML belgesi dönüştürülürken oluşturulan dosya.

Bir dosya belirtilmemişse, varsayılan dosya adı öğe üzerindeki özniteliği temel alınarak oluşturulur ve `method` `xsl:output` Bu dosya uzantısını belirler. Varsayılan dosya, geçerli kullanıcının geçici dizininde bulunur.

**Şemalar**

Doğrulama için kullanılacak şemalar. Düğme, kullanılacak şemaları seçmek için kullanılabilecek **xsd şemaları** iletişim kutusunu açar.

Ayrıca, şemaların yolunu da girebilirsiniz. Birden çok şema belirtilirse, her şema yolunun çift tırnak içine alınması gerekir.

**Larýnda**

**XSLT hata ayıklamayı Başlat** ve **XSLT 'yi hata ayıklama komutları olmadan Başlat** kullanıldığında BELGEYI dönüştürmek için kullanılan XSLT dosyası kullanılır. Bu alan boşsa, düzenleyici `xml-stylesheet` belgenin işleme yönergesinde belirtilen değeri kullanır veya bir dosya adı ister.

XSLT dosyası düzenlenirken, bu özellik, **XSLT hata ayıklamayı Başlat** veya **XSLT 'yi hata ayıklama komutu olmadan Başlat** seçiliyken farklı bir stil sayfasının kullanılması gerektiğini belirtmek için kullanılabilir. Örneğin, bir üst stil sayfasına dahil olan bir stil sayfasını düzenlediğinizde bunu yapmak isteyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [XML Düzenleyicisi](../xml-tools/xml-editor.md)
