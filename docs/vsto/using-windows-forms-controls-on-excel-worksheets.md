---
title: Excel çalışma sayfalarında Windows Forms denetimleri kullanma
description: Windows Forms denetimleri ekleyeceğiniz şekilde Microsoft Excel çalışma kitaplarınıza Windows Forms denetimleri nasıl ekleyebileceğiniz hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Windows Forms controls [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], Window Forms controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 015fffa51358c3a7a13d98950392d0749560c089
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526519"
---
# <a name="use-windows-forms-controls-on-excel-worksheets"></a>Excel çalışma sayfalarında Windows Forms denetimleri kullanma
  Microsoft Office Excel çalışma kitaplarına Windows Forms denetimleri eklediğiniz gibi Windows Forms denetimleri ekleyebilirsiniz. Belgelerde denetimlerle çalışma hakkında genel bilgi için bkz. [Office belgelerindeki Windows Forms denetimleri genel bakış](../vsto/windows-forms-controls-on-office-documents-overview.md).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="control-considerations-for-excel"></a>Excel için denetim konuları
 Excel 'e özgü bazı önemli noktalar vardır.

### <a name="match-control-size-to-cell-size"></a>Denetim boyutunu hücre boyutuyla Eşleştir
 Üst hücrenin boyutu değiştirildiğinde denetimi otomatik olarak yeniden boyutlandırılacak şekilde ayarlayabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: çalışma sayfası hücreleri içinde denetimleri yeniden boyutlandırma](../vsto/how-to-resize-controls-within-worksheet-cells.md).

### <a name="add-components-that-are-shared-by-all-worksheets"></a>Tüm çalışma sayfaları tarafından paylaşılan bileşenleri ekleme
 Çalışma sayfaları yerine tüm çalışma sayfaları arasında paylaştırmak istediğiniz bileşenleri <xref:System.Data.DataSet> (örneğin, çalışma sayfası tasarımcısına) ekleyebilirsiniz. Bileşen, bileşen tepsisinde görünür.

### <a name="formula-for-embedding-controls"></a>Denetimleri katıştırma formülü
 Excel 'de bir denetim seçtiğinizde, **Formül çubuğuna** **= embed ("WinForms. Control. Host", "")** görürsünüz. Bu metin gereklidir ve silinmemelidir.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: çalışma sayfası hücreleri içinde denetimleri yeniden boyutlandırma](../vsto/how-to-resize-controls-within-worksheet-cells.md)
- [Nasıl yapılır: yazdırırken çalışma sayfalarında denetimleri gizleme](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [İzlenecek yol: CheckBox denetimlerini kullanarak çalışma sayfası biçimlendirmesini değiştirme](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)
- [İzlenecek yol: düğme kullanarak çalışma sayfasındaki metin kutusunda metin görüntüleme](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)
- [İzlenecek yol: radyo düğmelerini kullanarak çalışma sayfasındaki bir grafiği güncelleştirme](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)
