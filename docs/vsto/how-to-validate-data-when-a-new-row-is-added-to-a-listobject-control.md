---
title: ListObject denetimine yeni satır eklendiğinde verileri doğrula
description: Bir ListObject denetimine yeni bir satır eklendiğinde verileri doğrulamak için Visual Studio 'Yu nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], validating data
- ListObject control, new row
- ListObject control, validating data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a7002cdc0787850fc7be5a782f3cf3a2101d7593
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825725"
---
# <a name="how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control"></a>Nasıl yapılır: ListObject denetimine yeni bir satır eklendiğinde verileri doğrulama
  Kullanıcılar <xref:Microsoft.Office.Tools.Excel.ListObject> , verilere bağlanan bir denetime yeni satırlar ekleyebilir. Veri kaynağına değişiklikleri uygulamadan önce kullanıcının verilerini doğrulayabilirsiniz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="data-validation"></a>Veri doğrulama
 Veriye bağlanan bir satır öğesine her eklendiğinde <xref:Microsoft.Office.Tools.Excel.ListObject> <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> olay tetiklenir. Bu olayı, veri doğrulamayı gerçekleştirmek için işleyebilirsiniz. Örneğin, uygulamanız yalnızca 18 yaş ve 65 yaşar arasındaki çalışanların veri kaynağına eklenebildiğini gerektiriyorsa, girilen yaş satırı, satır eklenmeden önce bu aralıkta yer aldığından emin olun.

> [!NOTE]
> İstemciye ek olarak sunucu üzerinde kullanıcı girişini her zaman denetlemeniz gerekir. Daha fazla bilgi için bkz. [güvenli istemci uygulamaları](/dotnet/framework/data/adonet/secure-client-applications).

### <a name="to-validate-data-when-a-new-row-is-added-to-data-bound-listobject"></a>Veri bağlantılı ListObject 'e yeni bir satır eklendiğinde verileri doğrulamak için

1. KIMLIĞI ve sınıf düzeyinde değişken oluşturun <xref:System.Data.DataTable> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet8":::

2. Yeni bir oluşturun <xref:System.Data.DataTable> ve `Startup` sınıfın olay işleyicisine `Sheet1` (belge düzeyi projesinde) veya `ThisAddIn` sınıfa (VSTO eklenti projesinde) örnek sütunlar ve veriler ekleyin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet9":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet9":::

3. `list1_BeforeAddDataBoundRow`Girilen yaş kabul edilebilir aralık dahilinde olup olmadığını denetlemek için olay işleyicisine kod ekleyin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet10":::

## <a name="compile-the-code"></a>Kodu derle
 Bu kod örneği <xref:Microsoft.Office.Tools.Excel.ListObject> `list1` , bu kodun göründüğü çalışma sayfasında var olan bir ada sahip olduğunuzu varsayar.

## <a name="see-also"></a>Ayrıca bkz.
- [VSTO Eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Office belgelerindeki denetimler](../vsto/controls-on-office-documents.md)
- [Çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [ListObject denetimi](../vsto/listobject-control.md)
- [Genişletilmiş nesneleri kullanarak Excel 'i otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md)
- [Nasıl yapılır: ListObject sütunlarını verilerle eşleme](../vsto/how-to-map-listobject-columns-to-data.md)
