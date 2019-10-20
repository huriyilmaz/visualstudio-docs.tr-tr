---
title: XSLT Stil Sayfalarını Düzenleme
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7fc987f8362d5daf435b7e9de860cc13f16a1aaf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646065"
---
# <a name="edit-xslt-style-sheets"></a>XSLT stil sayfalarını düzenleme

XML Düzenleyicisi, XSLT stil sayfalarını düzenlemek için de kullanılabilir. IntelliSense, anahat oluşturma, XML parçacıkları vb. gibi varsayılan düzenleyici özelliklerinden yararlanabilirsiniz. Ayrıca, XSLT 'de geliştirmeyi kolaylaştıran yeni özellikler de vardır.

## <a name="xslt-features"></a>XSLT Özellikleri

Aşağıdaki tabloda XSLT stil sayfalarıyla çalışmaya özgü özellikler açıklanmaktadır.

**Sözdizimi renklendirme**

@No__t_0 ve `match` gibi XSLT anahtar sözcükleri, **yazı tipleri ve renkler** ayarları tarafından belirtilen XSLT anahtar sözcüğü renginde görüntülenir.

**Dalgalı alt çizgiler**

XML Düzenleyicisi, XSLT stil sayfalarını doğrulamak için yüklü *XSLT. xsd* dosyasını kullanır. Doğrulama hataları mavi dalgalı alt çizgiler olarak gösterilir. XML Düzenleyicisi aynı zamanda stil sayfasını arka planda derler ve derleyici hatalarını ya da uyarıları uygun dalgalı alt çizgilerle raporlar.

**Betik blokları için destek**

Betik bloklarında kod, XSLT hata ayıklayıcısı tarafından desteklenir, böylece kesme noktaları ayarlayabilir ve komut dosyası blok kodunda ilerleyerek adımları izleyebilirsiniz.

**XSLT çıkışını görüntüle**

Bir XSL dönüşümünü yürütebilir ve XML düzenleyicisinden çıktıyı görüntüleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: XML DÜZENLEYICISINDEN XSLT dönüşümü yürütme](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md).

**XSLT hata ayıklama**

XSLT hata ayıklayıcısını XML düzenleyicisinde bir XSLT dosyasından başlatabilirsiniz. Hata ayıklayıcı XSLT dosyasındaki kesme noktalarını ayarlamayı, XSLT yürütme durumunu görüntülemeyi ve daha fazlasını destekler. Bir XSLT değişkeninin üzerine gelindiğinde, değişkenin değerine sahip bir araç Ipucu oluşur. Hata ayıklayıcı, bir stil sayfasında hata ayıklamak veya başka bir uygulamadan çağrılan derlenmiş bir XSL dönüşümünün hatalarını ayıklamak için kullanılabilir. Daha fazla bilgi için bkz. [XSLT hata ayıklama](../xml-tools/debugging-xslt.md).

## <a name="see-also"></a>Ayrıca bkz.

- [XML Düzenleyicisi](../xml-tools/xml-editor.md)