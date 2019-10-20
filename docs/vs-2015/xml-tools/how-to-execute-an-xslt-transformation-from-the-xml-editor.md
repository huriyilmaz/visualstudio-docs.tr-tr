---
title: 'Nasıl yapılır: XML düzenleyicisinden XSLT dönüştürmesi yürütme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4b305d88779603b374e5f95842d7a5271a657268
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666530"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>Nasıl yapılır: XML düzenleyicisinden XSLT dönüşümü yürütme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML Düzenleyicisi bir XSLT stil sayfasını bir XML belgesi ile ilişkilendirmenize, dönüştürmeyi gerçekleştirmenize ve çıktıyı görüntülemenize olanak sağlar. XSLT dönüşümünde elde edilen çıktı yeni bir belge penceresinde görüntülenir.

 **Output** özelliği, çıktının dosya adını belirtir. **Output** özelliği boşsa, geçici dizininizde bir dosya adı oluşturulur. Dosya uzantısı, stil sayfanızdaki `xsl:output` öğesine dayalıdır ve. xml,. txt veya. htm olabilir.

 **Output** özelliği. htm veya. html uzantılı bir dosya adı BELIRTIYORSA, XSLT çıkışının [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer kullanılarak önizlemesi yapılır. Diğer tüm dosya uzantıları, [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Studio tarafından seçilen varsayılan düzenleyici kullanılarak açılır. Örneğin, dosya uzantısı. xml ise, Visual Studio XML düzenleyicisini kullanır.

### <a name="to-execute-an-xslt-transformation-from-an-xml-document"></a>Bir XML belgesinden XSLT dönüşümünü yürütmek için

1. XML düzenleyicisinde bir XML belgesi açın.

2. XSLT stil sayfasını XML belgesiyle ilişkilendirin.

    - XML belgesine bir `xml-stylesheet` işleme yönergesi ekleyin. Örneğin, belge giriş satırına aşağıdaki satırı `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>` ekleyin.

         veya

    - **Özellikler** PENCERESINI kullanarak XSLT stil sayfasını ekleyin. Belge **Özellikleri penceresinde** **stil sayfası** alanı için **Araştır** düğmesine tıklayın, XSLT stil sayfasını seçin ve **Aç**' a tıklayın.

3. **XML Düzenleyicisi** araç çubuğundaki **showxsl çıkışı** düğmesine tıklayın.

    > [!NOTE]
    > XML belgesiyle ilişkili bir stil sayfası yoksa, bir iletişim kutusu sizden kullanılacak stil sayfasını sağlamanızı ister.
    >
    >  XSLT dönüşümünde elde edilen çıktı yeni bir belge penceresinde görüntülenir.

### <a name="to-execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>XSLT stil sayfasından XSLT dönüşümünü yürütmek için

1. XML düzenleyicisinde bir XSLT stil sayfası açın.

2. Belge **özellikleri** penceresinin **GIRIŞ** alanında bir XML belgesi belirtin.

    > [!NOTE]
    > XML belgesi, dönüştürme için kullanılan giriş belgesidir. XSLT dönüşümü başlatıldığında bir belge belirtilmemişse, **Dosya Aç** iletişim kutusu görüntülenir ve o sırada bir belge belirtebilirsiniz.

3. **XML Düzenleyicisi** araç çubuğundaki **showxslt çıkışı** düğmesine tıklayın.

     XSLT dönüşümünde elde edilen çıktı yeni bir belge penceresinde görüntülenir.

### <a name="to-provide-a-different-output-file-name"></a>Farklı bir çıkış dosyası adı sağlamak için

1. Belge **özellikleri** penceresinin **çıktı** alanında bir dosya adı belirtin.

2. **XML Düzenleyicisi** araç çubuğundaki **showxslt çıkışı** düğmesine tıklayın.

     XSLT dönüşümünde elde edilen çıktı yeni bir belge penceresinde görüntülenir ve çıkış penceresinde kullanılan Düzenleyici, **Çıkış** belgesi özelliğinin dosya uzantısına bağlıdır.

## <a name="see-also"></a>Ayrıca Bkz.
 [XML Düzenleyicisi](../xml-tools/xml-editor.md)
