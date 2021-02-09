---
title: XML Belge Özellikleri, Özellik Penceresi
description: XML düzenleyicisinde etkin belge hakkında temel bilgiler sağlayan Özellikler penceresi XML belge özellikleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 03/05/2019
ms.topic: reference
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1e12118f2f7f5d9189ca768f7be65a35b490eb54
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875022"
---
# <a name="xml-document-properties-properties-window"></a>XML belgesi özellikleri, Özellikler penceresi

**Özellikler** PENCERESI, XML düzenleyicisinde etkin olan belge hakkında temel bilgiler sağlar. Kullanılabilir özellikler, şu anda etkin olan XML belgesinin türüne bağlı olarak değişir.

> [!NOTE]
> Tüm XML belgesi özellikleri çözüme kaydedilir. Sonuç olarak, çözümü bir sonraki açışınızda bu değerleri yeniden girmeniz gerekmez.

**Kodlama**

Dosya için karakter kodlaması. Bu özelliğin değiştirilmesi, XML bildiriminde kodlama özniteliğini de değiştirir ve tam tersi de geçerlidir. Yeni kodlama dosyayı kaydettiğinizde dosyayı kodlamak için kullanılır.

**Giriş**

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

- [XML düzenleyicisi](../xml-tools/xml-editor.md)
