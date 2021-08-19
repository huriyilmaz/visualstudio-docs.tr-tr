---
title: Çalışma Windows Formlar denetimlerini Excel kullanma
description: Windows Forms'Windows denetimler eklerken olduğu Microsoft Excel çalışma kitaplarınıza form formlarına nasıl Windows öğrenin.
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 98a48f2c1f67c8758f9d5019e01f711192ab59b3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122082718"
---
# <a name="use-windows-forms-controls-on-excel-worksheets"></a>Çalışma Windows Formlar denetimlerini Excel kullanma
  Formlar Windows formlarına, Microsoft Office Excel formlara denetimler ekley istediğiniz şekilde Windows abilirsiniz. Belgeler üzerinde denetimlerle çalışma hakkında genel bilgi için bkz. [Windows forms denetimlerine Office genel bakış.](../vsto/windows-forms-controls-on-office-documents-overview.md)

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="control-considerations-for-excel"></a>Denetimle ilgili dikkat edilmesi gerekenler Excel
 Belirli konulara özgü birkaç önemli nokta Excel.

### <a name="match-control-size-to-cell-size"></a>Denetim boyutunu hücre boyutuyla eşleşme
 Üst hücrenin boyutu değiştirilirken denetimi otomatik olarak yeniden boyutlandırılmak için ayarlayın. Daha fazla bilgi için [bkz. Nasıl ekleyebilirsiniz: Çalışma sayfası hücrelerinde denetimleri yeniden boyutlandırma.](../vsto/how-to-resize-controls-within-worksheet-cells.md)

### <a name="add-components-that-are-shared-by-all-worksheets"></a>Tüm çalışma sayfaları tarafından paylaşılan bileşenleri ekleme
 Gibi tüm çalışma sayfaları arasında paylaşmak istediğiniz bileşenleri çalışma sayfaları yerine Çalışma Kitabı <xref:System.Data.DataSet> Tasarımcısı'nda ekleyebilirsiniz. Bileşen, bileşen tepsisinde görünür.

### <a name="formula-for-embedding-controls"></a>Ekleme denetimleri için formül
 Denetim çubuğundan bir denetim Excel Formül Çubuğunda **=EMBED("WinForms.Control.Host","")** **ifadesinin yer alır.** Bu metin gereklidir ve silinmemelidir.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl olur: Çalışma sayfası hücrelerinde denetimleri yeniden boyutlandırma](../vsto/how-to-resize-controls-within-worksheet-cells.md)
- [Nasıl olur: Yazdırma sırasında çalışma sayfaları denetimlerini gizleme](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [Adım adım kılavuz: CheckBox denetimlerini kullanarak çalışma sayfası biçimlendirmesini değiştirme](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)
- [Adım adım kılavuz: Düğme kullanarak çalışma sayfasındaki metin kutusunda metin görüntüleme](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)
- [Adım adım kılavuz: Radyo düğmelerini kullanarak çalışma sayfasındaki grafiği güncelleştirme](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)
