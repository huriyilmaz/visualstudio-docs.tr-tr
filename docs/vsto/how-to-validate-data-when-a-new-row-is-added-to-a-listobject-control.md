---
title: ListObject denetimine yeni satır eklendiği zaman verileri doğrulama
description: ListObject denetimine Visual Studio yeni bir satır eklendiği zaman verileri doğrulamak için Visual Studio'i nasıl kullanabileceğiniz hakkında bilgi öğrenin.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 0b9b70630708ebc558a798371a6d39ff30aed6f9
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726708"
---
# <a name="how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control"></a>Nasıl kullanılır: ListObject denetimine yeni bir satır eklendiği zaman verileri doğrulama
  Kullanıcılar, verilere bağlı bir <xref:Microsoft.Office.Tools.Excel.ListObject> denetime yeni satırlar ekleyebilir. Değişiklikleri veri kaynağına işlemeden önce kullanıcının verilerini doğruabilirsiniz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="data-validation"></a>Veri doğrulama
 Verilere bağlı bir <xref:Microsoft.Office.Tools.Excel.ListObject> satıra her satır ekleniyorsa, <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> olay ortaya çıkar. Veri doğrulamanızı gerçekleştirmek için bu olayı işebilirsiniz. Örneğin, uygulamanıza yalnızca 18 ile 65 yaş arasındaki çalışanların veri kaynağına eklenebiliyor olması gerekiyorsa, satır eklenmeden önce girilen yaş aralığının bu aralıkta olduğunu doğrulayın.

> [!NOTE]
> İstemciye ek olarak sunucuda her zaman kullanıcı girişini de denetlemeniz gerekir. Daha fazla bilgi için [bkz. İstemci uygulamalarının güvenliğini sağlama.](/dotnet/framework/data/adonet/secure-client-applications)

### <a name="to-validate-data-when-a-new-row-is-added-to-data-bound-listobject"></a>Veriye bağlı ListObject nesnesine yeni bir satır eklendiği zaman verileri doğrulamak için

1. Kimlik ve sınıf düzeyinde <xref:System.Data.DataTable> değişkenler oluşturun.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet8":::

2. Yeni bir oluşturun ve sınıfın olay işleyicisinde (belge düzeyi projesinde) veya <xref:System.Data.DataTable> `Startup` `Sheet1` sınıfına (VSTO Eklenti `ThisAddIn` projesinde) örnek sütunlar ve veriler ekleyin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet9":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet9":::

3. Girilen yaş `list1_BeforeAddDataBoundRow` aralığının kabul edilebilir aralıkta olup olmadığını kontrol etmek için olay işleyiciye kod ekleyin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet10":::

## <a name="compile-the-code"></a>Kodu derleme
 Bu kod örneği, bu kodun göründüğü çalışma <xref:Microsoft.Office.Tools.Excel.ListObject> sayfasında adlı bir var olan bir `list1` dosyanız olduğunu varsayıyor.

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma zamanında Word Excel ve VSTO çalışma kitaplarını genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Belgelerde Office denetimler](../vsto/controls-on-office-documents.md)
- [Çalışma zamanında Office için denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [ListObject denetimi](../vsto/listobject-control.md)
- [Genişletilmiş Excel kullanarak nesneleri otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md)
- [Nasıl kullanılır: ListObject sütunlarını veriyle eşleme](../vsto/how-to-map-listobject-columns-to-data.md)
