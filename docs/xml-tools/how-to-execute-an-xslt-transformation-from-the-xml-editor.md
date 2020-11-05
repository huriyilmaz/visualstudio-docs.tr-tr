---
title: XSLT dönüşümü yürütme
description: XML düzenleyicisini kullanarak bir XSLT stil sayfasını bir XML belgesiyle ilişkilendirme, XSLT dönüştürmesi gerçekleştirme ve çıktıyı görüntüleme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 03/05/2019
ms.topic: how-to
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f1c7165f301c82dfaf5aa066a3e15bd7ab244089
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93399488"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>Nasıl yapılır: XML düzenleyicisinden XSLT dönüşümü yürütme

XML Düzenleyicisi bir XSLT stil sayfasını bir XML belgesi ile ilişkilendirmenize, dönüştürmeyi gerçekleştirmenize ve çıktıyı görüntülemenize imkan tanır. XSLT dönüşümünde elde edilen çıktı yeni bir belge penceresinde görüntülenir.

**Output** özelliği, çıktının dosya adını belirtir. **Output** özelliği boşsa, geçici dizininizde bir dosya adı oluşturulur. Dosya uzantısı, `xsl:output` Stil sayfanızdaki öğesine dayalıdır ve olabilir. *XML* ,. *txt* veya. *htm*.

**Output** özelliği ile bir dosya adı belirtiyorsa. *htm* veya. *HTML* UZANTıSı, XSLT çıktısı bir Web tarayıcısı kullanılarak önizlenebilir. Diğer tüm dosya uzantıları, Visual Studio tarafından seçilen varsayılan düzenleyici kullanılarak açılır. Örneğin, dosya uzantısı ise. *XML* , VISUAL Studio XML düzenleyicisini kullanır.

## <a name="execute-an-xslt-transformation-from-an-xml-file"></a>XML dosyasından XSLT dönüşümü yürütme

1. XML düzenleyicisinde bir XML belgesi açın.

2. XSLT stil sayfasını XML belgesiyle ilişkilendirin.

    - `xml-stylesheet`XML belgesine bir işleme yönergesi ekleyin. Örneğin, belge giriş satırına aşağıdaki satırı ekleyin: `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>`

       -veya-

    - **Özellikler** PENCERESINI kullanarak XSLT stil sayfasını ekleyin. Düzenleyicide XML dosyası açıkken, düzenleyicide herhangi bir yere sağ tıklayın ve **Özellikler** ' i seçin. **Özellikler** penceresinde, **stil sayfası** alanına tıklayın ve ardından (...) düğmesini seçin. XSLT stil sayfasını seçin ve sonra **Aç** ' ı seçin.

3. Menü çubuğunda, **XML**  >  **hata ayıklama olmadan XML Başlat XSLT** 'yi seçin. Ya da **CTRL** + **alt** + **F5** tuşuna basın.

   XSLT dönüştürmesinin çıktısı yeni bir belge penceresinde görüntülenir.

   > [!NOTE]
   > XML belgesiyle ilişkili bir stil sayfası yoksa, bir iletişim kutusu sizden kullanılacak stil sayfasını sağlamanızı ister.

## <a name="execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>XSLT stil sayfasından XSLT dönüşümü yürütme

1. XML düzenleyicisinde bir XSLT stil sayfası açın.

2. Belge **özellikleri** penceresinin **GIRIŞ** alanında bir XML belgesi belirtin.

   > [!NOTE]
   > XML belgesi, dönüştürme için kullanılan giriş belgesidir. XSLT dönüşümü başlatıldığında bir belge belirtilmemişse, **Dosya Aç** iletişim kutusu görüntülenir ve o sırada bir belge belirtebilirsiniz.

3. Menü çubuğunda, **XML**  >  **hata ayıklama olmadan XML Başlat XSLT** 'yi seçin. Ya da **CTRL** + **alt** + **F5** tuşuna basın.

   XSLT dönüştürmesinin çıktısı yeni bir belge penceresinde görüntülenir.

## <a name="specify-an-output-file-name"></a>Çıkış dosyası adı belirtin

XML ve XSL dosyaları için bir çıkış dosyası adı belirtebilirsiniz. **Özellikler** penceresini açın ve **Çıkış** alanında bir dosya adı belirtin.

## <a name="see-also"></a>Ayrıca bkz.

- [XML düzenleyicisi](../xml-tools/xml-editor.md)
