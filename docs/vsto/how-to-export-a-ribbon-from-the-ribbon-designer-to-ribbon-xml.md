---
title: "Nasıl yapılır: Şerit Tasarımcısından Şerit XML 'ine şerit aktarma"
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, XML
- customizing the Ribbon, XML
- Ribbon [Office development in Visual Studio], XML
- Ribbon [Office development in Visual Studio], exporting
- XML [Office development in Visual Studio], Ribbon
- Ribbon Designer [Office development in Visual Studio]
- exporting Ribbon
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cf3101a062fa8b30ae821bf6a157319b6f37862a
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/30/2020
ms.locfileid: "92298433"
---
# <a name="how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Nasıl yapılır: Şerit Tasarımcısından Şerit XML 'ine şerit aktarma
  **Şerit (görsel Tasarımcı)** öğesi, tüm olası Şerit özelleştirmesi türlerini desteklemiyor. Şeriti gelişmiş yöntemlerle özelleştirmek için, tasarımcıyı tasarımcıdan Şerit XML 'Ine aktarabilir ve XML 'i doğrudan düzenleyebilirsiniz.

> [!NOTE]
> Tüm özellik değerleri Şerit XML dosyasında görünmez. Daha fazla bilgi için bkz. [Şerit 'e genel bakış](../vsto/ribbon-overview.md).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Şerit Tasarımcısından Şerit XML 'ine bir şerit dışarı aktarmak için

1. **Çözüm Gezgini**' de şerit kodu dosyasına sağ tıklayın ve ardından **tasarımcıyı görüntüle**' ye tıklayın.

2. Şerit Tasarımcısına sağ tıklayın ve ardından **ŞERIDI XML 'e aktar**' a tıklayın.

     Visual Studio, projenize bir Şerit XML dosyası ve Şerit XML kodu dosyası ekler.

3. Şerit kod sınıfında, ile başlayan açıklamaları bulun `TODO:` .

4. Bu açıklamalarda kod bloğunu, geliştirmekte olduğunuz çözüm türüne bağlı olarak **ThisAddIn**, **ThisWorkbook**veya **ThisDocument** sınıfına kopyalayın.

     Bu kod, Microsoft Office uygulamasının özel şeritinizi bulmasını ve yüklemesini sağlar. Daha fazla bilgi için bkz. [ŞERIT XML](../vsto/ribbon-xml.md).

5. **ThisAddIn**, **ThisWorkbook**veya **ThisDocument** sınıfında, kod bloğunun açıklamasını kaldırın.

     Kodun açıklamasını belirledikten sonra, aşağıdaki örneğe benzemelidir. Bu örnekte, Şerit sınıfı çağırılır `MyRibbon` .

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]

6. Şerit XML kod dosyasına geçin ve `Ribbon Callbacks` bölgeyi bulun.

     Bu, bir düğmeye tıklanması gibi kullanıcı eylemlerini işlemek için geri çağırma yöntemleri yazacağınız yerdir.

7. Şerit Tasarımcı kodunda yazdığınız her olay işleyicisi için bir geri çağırma yöntemi oluşturun.

8. Olay işleyicilerinden tüm olay işleyici kodunuzu geri çağırma yöntemlerine taşıyın ve şerit genişletilebilirliği (RibbonX) programlama modeliyle çalışmak için kodu değiştirin.

     Geri çağırma yöntemlerini yazma ve RibbonX programlama modelini kullanma hakkında daha fazla bilgi için bkz. [RIBBON XML](../vsto/ribbon-xml.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Şerite genel bakış](../vsto/ribbon-overview.md)
- [Şerit Tasarımcısı](../vsto/ribbon-designer.md)
- [Şerit XML](../vsto/ribbon-xml.md)
- [İzlenecek yol: Şerit Tasarımcısını kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [İzlenecek yol: Şerit XML kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
