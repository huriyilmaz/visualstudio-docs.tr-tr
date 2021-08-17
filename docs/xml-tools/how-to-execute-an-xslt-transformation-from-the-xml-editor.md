---
title: XSLT dönüşümü yürütme
description: XML düzenleyicisini kullanarak bir XSLT stil sayfasını bir XML belgesiyle ilişkilendirme, XSLT dönüştürmesi gerçekleştirme ve çıktıyı görüntüleme hakkında bilgi edinin.
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
ms.openlocfilehash: c578007a79991c165ab6a88848c5428fe4e6e5e3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122025127"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>Nasıl yapılır: XML düzenleyicisinden XSLT dönüşümü yürütme

XML Düzenleyicisi bir XSLT stil sayfasını bir XML belgesi ile ilişkilendirmenize, dönüştürmeyi gerçekleştirmenize ve çıktıyı görüntülemenize imkan tanır. XSLT dönüşümünde elde edilen çıktı yeni bir belge penceresinde görüntülenir.

**Output** özelliği, çıktının dosya adını belirtir. **Output** özelliği boşsa, geçici dizininizde bir dosya adı oluşturulur. Dosya uzantısı, `xsl:output` Stil sayfanızdaki öğesine dayalıdır ve olabilir.*XML*,. *txt* veya. *htm*.

**Output** özelliği ile bir dosya adı belirtiyorsa. *htm* veya. *HTML* UZANTıSı, XSLT çıktısı bir Web tarayıcısı kullanılarak önizlenebilir. Diğer tüm dosya uzantıları, Visual Studio tarafından seçilen varsayılan düzenleyici kullanılarak açılır. Örneğin, dosya uzantısı ise. *xml*, Visual Studio xml düzenleyicisini kullanır.

## <a name="execute-an-xslt-transformation-from-an-xml-file"></a>XML dosyasından XSLT dönüşümü yürütme

1. XML düzenleyicisinde bir XML belgesi açın.

2. XSLT stil sayfasını XML belgesiyle ilişkilendirin.

    - `xml-stylesheet`XML belgesine bir işleme yönergesi ekleyin. Örneğin, belge giriş satırına aşağıdaki satırı ekleyin: `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>`

       -veya-

    - **Özellikler** PENCERESINI kullanarak XSLT stil sayfasını ekleyin. Düzenleyicide XML dosyası açıkken, düzenleyicide herhangi bir yere sağ tıklayın ve **Özellikler**' i seçin. **Özellikler** penceresinde, **stil sayfası** alanına tıklayın ve ardından (...) düğmesini seçin. XSLT stil sayfasını seçin ve sonra **Aç**' ı seçin.

3. Menü çubuğunda,   >  **hata ayıklama olmadan XML Başlat XSLT**'yi seçin. Ya da **CTRL** + **alt** + **F5** tuşuna basın.

   XSLT dönüştürmesinin çıktısı yeni bir belge penceresinde görüntülenir.

   > [!NOTE]
   > XML belgesiyle ilişkili bir stil sayfası yoksa, bir iletişim kutusu sizden kullanılacak stil sayfasını sağlamanızı ister.

## <a name="execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>XSLT stil sayfasından XSLT dönüşümü yürütme

1. XML düzenleyicisinde bir XSLT stil sayfası açın.

2. Belge **özellikleri** penceresinin **GIRIŞ** alanında bir XML belgesi belirtin.

   > [!NOTE]
   > XML belgesi, dönüştürme için kullanılan giriş belgesidir. XSLT dönüşümü başlatıldığında bir belge belirtilmemişse, **Dosya Aç** iletişim kutusu görüntülenir ve o sırada bir belge belirtebilirsiniz.

3. Menü çubuğunda,   >  **hata ayıklama olmadan XML Başlat XSLT**'yi seçin. Ya da **CTRL** + **alt** + **F5** tuşuna basın.

   XSLT dönüştürmesinin çıktısı yeni bir belge penceresinde görüntülenir.

## <a name="specify-an-output-file-name"></a>Çıkış dosyası adı belirtin

XML ve XSL dosyaları için bir çıkış dosyası adı belirtebilirsiniz. **Özellikler** penceresini açın ve **Çıkış** alanında bir dosya adı belirtin.

## <a name="see-also"></a>Ayrıca bkz.

- [XML düzenleyicisi](../xml-tools/xml-editor.md)
