---
title: XSLT Stil Sayfalarını Düzenleme
description: XML düzenleyicisinde söz dizimi renklendirme, alt çizgiler ve düzenleyiciden XSLT hata ayıklayıcısını başlatma gibi XSLT stil sayfalarını düzenlemeye uygun özellikler hakkında bilgi öğrenin.
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
ms.openlocfilehash: 75f2b4c0300ebbf437a989003626e0ee796853aa88f4b725a94f0f6e0d848a78
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121351024"
---
# <a name="edit-xslt-style-sheets"></a>XSLT Stil Sayfalarını Düzenleme

XML düzenleyicisi XSLT stil sayfalarını düzenlemek için de kullanılabilir. IntelliSense, açıklama, XML kod parçacıkları gibi varsayılan Düzenleyici özelliklerinden faydalanabilirsiniz. Ayrıca, XSLT'de geliştirmeyi kolaylaştıran yeni özellikler de vardır.

## <a name="xslt-features"></a>XSLT Özellikleri

Aşağıdaki tabloda, XSLT stil sayfalarıyla çalışmaya özgü özellikler açık almaktadır.

**Söz dizimi renklendirme**

ve gibi XSLT anahtar sözcükleri Yazı Tipleri ve Renkler ayarları tarafından belirtilen `template` `match` XSLT anahtar sözcük **renginde** görüntülenir.

**Dalgalı alt çizgiler**

XML düzenleyicisi, XSLT stil sayfalarını doğrulamak için yüklü *xslt.xsd* dosyasını kullanır. Doğrulama hataları mavi dalgalı alt çizgi olarak gösterilir. XML düzenleyicisi ayrıca stil sayfalarını arka planda derler ve uygun dalgalı alt çizgilerle derleyici hatalarını veya uyarılarını raporlar.

**Betik blokları desteği**

Betik bloklarında kod XSLT hata ayıklayıcısı tarafından desteklenmiş, bu nedenle kesme noktaları ayarp betik bloğu kodunda adım adım geçebilirsiniz.

**XSLT çıkışını görüntüleme**

Bir XSL dönüştürmesi yürütülür ve XML düzenleyicisinden çıktıyı görüntü olur. Daha fazla bilgi için, [bkz. How to: Execute an XSLT transformation from the XML editor](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md).

**XSLT hatası ayıklama**

XML düzenleyicisinde bir XSLT dosyasından XSLT hata ayıklayıcısını başlatabilirsiniz. Hata ayıklayıcısı XSLT dosyasında kesme noktaları ayarlamayı, XSLT yürütme durumunu görüntülemeyi ve bu şekilde devamini destekler. XSLT değişkeninin üzerine gelindiğinde, değişkenin değeriyle birlikte bir ToolTip getirir. Hata ayıklayıcı, bir stil sayfası için hata ayıklamak veya başka bir uygulama tarafından çağrılan derlenmiş bir XSL dönüştürmede hata ayıklamak için kullanılabilir. Daha fazla bilgi için bkz. [XSLT'de Hata Ayıklama.](../xml-tools/debugging-xslt.md)

## <a name="see-also"></a>Ayrıca bkz.

- [XML düzenleyicisi](../xml-tools/xml-editor.md)
