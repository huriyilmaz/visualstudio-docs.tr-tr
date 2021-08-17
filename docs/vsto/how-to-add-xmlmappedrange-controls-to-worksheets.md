---
title: 'Nasıl yapılır: çalışma sayfalarına XMLMappedRange denetimleri ekleme'
description: bir XML öğesini Microsoft Office Excel bir hücreye eşlediğinizde Visual Studio otomatik olarak çalışma sayfanıza bir xmlmappedrange denetimi ekleyen bir bilgi edinin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 8fa5b3037b29cf15537215c9bf623c57ac8a119d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122106334"
---
# <a name="how-to-add-xmlmappedrange-controls-to-worksheets"></a>Nasıl yapılır: çalışma sayfalarına XMLMappedRange denetimleri ekleme
  bir XML öğesini Microsoft Office Excel bir hücreyle eşleştirdiğinizde, Visual Studio otomatik olarak <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> çalışma sayfanıza bir denetim ekler.

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

4. **xml kaynağı** görev bölmesinde, **xml Haritalar**' ye tıklayın.

5. **XML Haritalar** iletişim kutusunda **ekle**' ye tıklayın.

     **XML kaynağı** iletişim kutusu görüntülenir.

6. **XML kaynağı** iletişim kutusundan bir XML şeması seçin ve **Aç**' a tıklayın.

     şema **XML Haritalar** iletişim kutusuna eklenir.

7. **XML Haritalar** iletişim kutusunda **tamam**' a tıklayın.

8. **XML kaynağı** görev bölmesindeki bir öğeyi çalışma sayfasındaki bir hücreye sürükleyin.

     Bir <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> oluşturulur ve projeye eklenir.

    > [!NOTE]
    > Bir üst öğeyi **XML kaynağı** görev bölmesinden sürüklerseniz bir <xref:Microsoft.Office.Tools.Excel.ListObject> denetim oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.
- [XmlMappedRange denetimi](../vsto/xmlmappedrange-control.md)
- [genişletilmiş nesneleri kullanarak Excel otomatikleştirin](../vsto/automating-excel-by-using-extended-objects.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Nasıl yapılır: şemaları Visual Studio içindeki çalışma sayfalarına eşleme](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
