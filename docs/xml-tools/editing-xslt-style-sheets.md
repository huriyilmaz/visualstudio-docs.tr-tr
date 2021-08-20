---
title: XSLT Stil Sayfalarını Düzenleme
description: XML düzenleyicisinde, sözdizimi renklendirme, alt çizgiler ve XSLT hata ayıklayıcısını düzenleyiciden başlatma dahil olmak üzere XSLT stil sayfalarını düzenleme özellikleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: 636d681080239dc80a210d590407e77c062bdc20
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122130240"
---
# <a name="edit-xslt-style-sheets"></a>XSLT stil sayfalarını düzenleme

XML Düzenleyicisi, XSLT stil sayfalarını düzenlemek için de kullanılabilir. IntelliSense, anahat oluşturma, XML parçacıkları vb. gibi varsayılan düzenleyici özelliklerinden yararlanabilirsiniz. Ayrıca, XSLT 'de geliştirmeyi kolaylaştıran yeni özellikler de vardır.

## <a name="xslt-features"></a>XSLT Özellikleri

Aşağıdaki tabloda XSLT stil sayfalarıyla çalışmaya özgü özellikler açıklanmaktadır.

**Sözdizimi renklendirme**

Ve gibi XSLT anahtar sözcükleri `template` , `match` **yazı tipleri ve renkler** ayarları tarafından belirtilen XSLT anahtar sözcüğü renginde görüntülenir.

**Dalgalı alt çizgiler**

XML Düzenleyicisi, XSLT stil sayfalarını doğrulamak için yüklü *XSLT. xsd* dosyasını kullanır. Doğrulama hataları mavi dalgalı alt çizgiler olarak gösterilir. XML Düzenleyicisi aynı zamanda stil sayfasını arka planda derler ve derleyici hatalarını ya da uyarıları uygun dalgalı alt çizgilerle raporlar.

**Betik blokları için destek**

Betik bloklarında kod, XSLT hata ayıklayıcısı tarafından desteklenir, böylece kesme noktaları ayarlayabilir ve komut dosyası blok kodunda ilerleyerek adımları izleyebilirsiniz.

**XSLT çıkışını görüntüle**

Bir XSL dönüşümünü yürütebilir ve XML düzenleyicisinden çıktıyı görüntüleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: XML DÜZENLEYICISINDEN XSLT dönüşümü yürütme](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md).

**XSLT hatası ayıklama**

XSLT hata ayıklayıcısını XML düzenleyicisinde bir XSLT dosyasından başlatabilirsiniz. Hata ayıklayıcı XSLT dosyasındaki kesme noktalarını ayarlamayı, XSLT yürütme durumunu görüntülemeyi ve daha fazlasını destekler. Bir XSLT değişkeninin üzerine gelindiğinde, değişkenin değerine sahip bir araç Ipucu oluşur. Hata ayıklayıcı, bir stil sayfasında hata ayıklamak veya başka bir uygulamadan çağrılan derlenmiş bir XSL dönüşümünün hatalarını ayıklamak için kullanılabilir. Daha fazla bilgi için bkz. [XSLT hata ayıklama](../xml-tools/debugging-xslt.md).

## <a name="see-also"></a>Ayrıca bkz.

- [XML düzenleyicisi](../xml-tools/xml-editor.md)
