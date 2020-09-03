---
title: 'Nasıl yapılır: çalışma sayfalarına XMLMappedRange denetimleri ekleme'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLMappedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1d69e705e8f537ba3636422ad6883a7633e03322
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544891"
---
# <a name="how-to-add-xmlmappedrange-controls-to-worksheets"></a>Nasıl yapılır: çalışma sayfalarına XMLMappedRange denetimleri ekleme
  Bir XML öğesini Microsoft Office Excel içindeki bir hücreyle eşleştirdiğinizde, Visual Studio otomatik olarak <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> çalışma sayfanıza bir denetim ekler.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>Denetim, **araç kutusu** veya **veri kaynakları** penceresinde kullanılamaz. Ayrıca, <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> programlı olarak denetim oluşturamazsınız.

## <a name="to-add-an-xmlmappedrange-control-to-a-worksheet"></a>Bir çalışma sayfasına XMLMappedRange denetimi eklemek için

1. Visual Studio tasarımcısında Excel çalışma kitabını açın.

2. Denetimi eklemek istediğiniz çalışma sayfasını açın.

3. **Geliştirici** sekmesinde **kaynak**' a tıklayın.

    > [!NOTE]
    > **Geliştirici** sekmesi şeritte görünür değilse, etkinleştirmeniz gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: Şeritte Geliştirici sekmesini gösterme](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

     **XML kaynağı** görev bölmesi görüntülenir.

4. **XML kaynağı** görev bölmesinde, **XML eşlemeleri**' ne tıklayın.

5. **XML eşlemeleri** Iletişim kutusunda **Ekle**' ye tıklayın.

     **XML kaynağı** iletişim kutusu görüntülenir.

6. **XML kaynağı** iletişim kutusundan bir XML şeması seçin ve **Aç**' a tıklayın.

     Şema, **XML eşlemeleri** iletişim kutusuna eklenir.

7. **XML eşlemeleri** Iletişim kutusunda **Tamam**' a tıklayın.

8. **XML kaynağı** görev bölmesindeki bir öğeyi çalışma sayfasındaki bir hücreye sürükleyin.

     Bir <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> oluşturulur ve projeye eklenir.

    > [!NOTE]
    > Bir üst öğeyi **XML kaynağı** görev bölmesinden sürüklerseniz bir <xref:Microsoft.Office.Tools.Excel.ListObject> denetim oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.
- [XmlMappedRange denetimi](../vsto/xmlmappedrange-control.md)
- [Genişletilmiş nesneleri kullanarak Excel 'i otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Nasıl yapılır: şemaları Visual Studio içindeki çalışma sayfalarına eşleme](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
