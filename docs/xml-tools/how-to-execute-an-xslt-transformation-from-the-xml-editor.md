---
title: XSLT dönüşümü yürütme
description: XML düzenleyicisini kullanarak XSLT stil sayfalarını bir XML belgesiyle ilişkilendirmeyi, XSLT dönüşümü gerçekleştirmeyi ve çıkışı görüntülemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/05/2019
ms.topic: how-to
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: 3a3d94919b22233193d2f4b94dfd580e72f654557cd266ab9539547855a50c85
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121266941"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>Nasıl yapılır: XML düzenleyicisinden XSLT dönüşümü yürütme

XML düzenleyicisi, bir XSLT stil sayfalarını bir XML belgesiyle ilişkilendirmenizi, dönüştürmeyi gerçekleştirmenizi ve çıkışı görüntülemenizi sağlar. XSLT dönüşümünden elde edilen çıkış yeni bir belge penceresinde görüntülenir.

**Output özelliği** çıkışın dosya adını belirtir. Output **özelliği** boşsa geçici dizinde bir dosya adı oluşturulur. Dosya uzantısı stil sayfanız `xsl:output` öğesine dayalıdır ve olabilir.*xml*, . *txt veya* . *tarafından 2.*

Output **özelliği** ile bir dosya adı belirtirse. *html veya* . *html* uzantısı, XSLT çıkışı bir web tarayıcısı kullanılarak önizlemeye açılır. Diğer tüm dosya uzantıları, dosya uzantıları tarafından seçilen varsayılan düzenleyici kullanılarak Visual Studio. Örneğin, dosya uzantısı ise. *xml*, Visual Studio XML düzenleyicisini kullanır.

## <a name="execute-an-xslt-transformation-from-an-xml-file"></a>XML dosyasından XSLT dönüşümü yürütme

1. XML düzenleyicisinde bir XML belgesi açın.

2. XSLT stil sayfalarını XML belgesiyle ilişkilendirme.

    - XML `xml-stylesheet` belgesine işleme yönergesi ekleyin. Örneğin, belge giriş belgesine aşağıdaki satırı ekleyin: `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>`

       -veya-

    - Özellikler penceresini kullanarak XSLT stil **sayfası** ekleyin. XML dosyası düzenleyicide açıkken düzenleyicinin herhangi bir yerine sağ tıklayın ve Özellikler'i **seçin.** Özellikler **penceresinde** Stil Sayfası alanına **tıklayın ve** gözat düğmesini (...) seçin. XSLT stil sayfalarını ve ardından Aç'ı **seçin.**

3. Menü çubuğunda XML Başlatma  >  **XSLT Hata Ayıklama olmadan öğesini seçin.** Veya **Ctrl** Alt +  + **F5 tuşlarına basın.**

   XSLT dönüştürme çıkışı yeni bir belge penceresinde görüntülenir.

   > [!NOTE]
   > XML belgesiyle ilişkili bir stil sayfası yoksa, bir iletişim kutusu sizden, kullanmak üzere stil sayfası sağlamanız istenir.

## <a name="execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>XSLT stil sayfası üzerinde XSLT dönüşümü yürütme

1. XML düzenleyicisinde bir XSLT stil sayfası açın.

2. Belge Özellikleri penceresinin **Giriş alanında** bir XML **belgesi** belirtin.

   > [!NOTE]
   > XML belgesi, dönüştürme için kullanılan giriş belgesidir. XSLT dönüştürmesi başlatıcıda bir belge belirtilmezse, Dosya Aç iletişim kutusu görüntülenir ve o anda bir belge belirtebilirsiniz. 

3. Menü çubuğunda XML Başlatma  >  **XSLT Hata Ayıklama olmadan öğesini seçin.** Veya **Ctrl** Alt +  + **F5 tuşlarına basın.**

   XSLT dönüştürme çıkışı yeni bir belge penceresinde görüntülenir.

## <a name="specify-an-output-file-name"></a>Çıkış dosyası adı belirtme

Hem XML hem de XSL dosyaları için bir çıkış dosyası adı belirtebilirsiniz. Özellikler **penceresini** açın ve Çıktı alanında bir dosya **adı** belirtin.

## <a name="see-also"></a>Ayrıca bkz.

- [XML düzenleyicisi](../xml-tools/xml-editor.md)
