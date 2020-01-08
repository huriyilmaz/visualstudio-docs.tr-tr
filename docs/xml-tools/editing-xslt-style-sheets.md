---
title: XSLT Stil Sayfalarını Düzenleme
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 81bab324c58c06cc1ca553bae2f81faf474c4ad0
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592847"
---
# <a name="edit-xslt-style-sheets"></a>XSLT stil sayfalarını düzenleme

XML Düzenleyicisi, XSLT stil sayfalarını düzenlemek için de kullanılabilir. IntelliSense, anahat oluşturma, XML parçacıkları vb. gibi varsayılan düzenleyici özelliklerinden yararlanabilirsiniz. Ayrıca, XSLT 'de geliştirmeyi kolaylaştıran yeni özellikler de vardır.

## <a name="xslt-features"></a>XSLT Özellikleri

Aşağıdaki tabloda XSLT stil sayfalarıyla çalışmaya özgü özellikler açıklanmaktadır.

**Sözdizimi renklendirme**

`template` ve `match`gibi XSLT anahtar sözcükleri, **yazı tipleri ve renkler** ayarları tarafından belirtilen XSLT anahtar sözcüğü renginde görüntülenir.

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
