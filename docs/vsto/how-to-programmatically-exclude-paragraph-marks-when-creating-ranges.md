---
title: Aralıkları programlama yoluyla oluştururken paragraf işaretlerini hariç tut
description: Bir Microsoft Word belgesinde aralıklar oluştururken programlama yoluyla paragraf işaretlerini nasıl dışarıda bırakacağınızı öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], excluding paragraphs
- ranges, excluding paragraph marks in Word
- documents [Office development in Visual Studio], paragraph marks
- paragraphs, controlling structure
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 898eae77928908dfc077ddf80d2659328ec6475d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885488"
---
# <a name="how-to-programmatically-exclude-paragraph-marks-when-creating-ranges"></a>Nasıl yapılır: Aralık oluştururken program aracılığıyla paragraf işaretlerini hariç tutma
  <xref:Microsoft.Office.Interop.Word.Range>Paragrafı temel alan bir nesne oluşturduğunuzda, paragraf işaretleri gibi tüm yazdırılamayan karakterler aralığa dahil edilir. Kaynak paragraftan bir hedef paragrafa metin eklemek isteyebilirsiniz. Hedef paragrafı ayrı paragraflara bölmek istemiyorsanız, önce paragraf işaretini kaynak paragrafından kaldırmanız gerekir. Ayrıca, paragraf biçimlendirme bilgileri paragraf işareti içinde depolandığından, aralığı varolan bir paragrafa eklediğinizde bunu dahil etmek istemeyebilirsiniz.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Aşağıdaki örnek yordam iki dize değişkeni bildirir, etkin belgedeki birinci ve ikinci paragrafların içeriğini alır ve sonra içeriklerini değiştirir. Örnek daha sonra <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> yöntemi kullanarak ve paragrafın içine metin ekleyerek paragraf işaretçisini aralıktan kaldırmayı gösterir.

## <a name="to-control-paragraph-structure-when-inserting-text"></a>Metin eklerken paragraf yapısını denetlemek için

1. Birinci ve ikinci paragraflar için iki Aralık değişkeni oluşturun ve özelliğini kullanarak içeriklerini alın <xref:Microsoft.Office.Interop.Word.Range.Text%2A> .

     Aşağıdaki kod örneği, belge düzeyi özelleştirmesinde kullanılabilir.

     [!code-vb[Trin_VstcoreWordAutomation#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#27)]
     [!code-csharp[Trin_VstcoreWordAutomation#27](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#27)]

     Aşağıdaki kod örneği, uygulama düzeyinde bir VSTO eklentisi içinde kullanılabilir. Bu kod etkin belgeyi kullanır.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#27)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#27](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#27)]

2. <xref:Microsoft.Office.Interop.Word.Range.Text%2A>İki paragraf arasındaki metni değiştirerek özelliği atayın.

     [!code-vb[Trin_VstcoreWordAutomation#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#28)]
     [!code-csharp[Trin_VstcoreWordAutomation#28](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#28)]

3. Sonuçları bir ileti kutusunda göstermek için her aralığı sırasıyla seçin ve duraklatın.

     [!code-vb[Trin_VstcoreWordAutomation#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#29)]
     [!code-csharp[Trin_VstcoreWordAutomation#29](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#29)]

4. `firstRange`Yöntemi kullanarak, <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> paragraf işaretçisinin artık bir parçası kalmayacak şekilde ayarlayın `firstRange` .

     [!code-vb[Trin_VstcoreWordAutomation#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#30)]
     [!code-csharp[Trin_VstcoreWordAutomation#30](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#30)]

5. İlk paragraftaki metnin geri kalanını değiştirin ve aralığın özelliğine yeni bir dize atayarak <xref:Microsoft.Office.Interop.Word.Range.Text%2A> .

     [!code-vb[Trin_VstcoreWordAutomation#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#31)]
     [!code-csharp[Trin_VstcoreWordAutomation#31](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#31)]

6. İçindeki metni `secondRange` paragraf işareti dahil olmak üzere değiştirin.

     [!code-vb[Trin_VstcoreWordAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#32)]
     [!code-csharp[Trin_VstcoreWordAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#32)]

7. `firstRange`Sonuçları bir ileti kutusunda göstermek için seçin ve duraklatın, sonra ile aynısını yapın `secondRange` .

     `firstRange`Paragraf işaretini dışlamak için yeniden tanımlandı, paragrafın orijinal biçimlendirmesi korunur. Bununla birlikte, içindeki paragraf işaretinin üzerine bir cümle eklenmiştir `secondRange` ve ayrı paragraf kaldırılır.

     [!code-vb[Trin_VstcoreWordAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#33)]
     [!code-csharp[Trin_VstcoreWordAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#33)]

     Her iki aralığın da özgün içeriği dizeler olarak kaydedilir, bu sayede belgeyi özgün durumuna geri yükleyebilirsiniz.

8. Yalnızca `firstRange` <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> bir karakterlik konum için yöntemini kullanarak paragraf işaretini dahil etmek için.

     [!code-vb[Trin_VstcoreWordAutomation#34](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#34)]
     [!code-csharp[Trin_VstcoreWordAutomation#34](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#34)]

9. `secondRange` klasörünü silin. Bu, paragrafı üç özgün konumuna geri yükler.

     [!code-vb[Trin_VstcoreWordAutomation#35](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#35)]
     [!code-csharp[Trin_VstcoreWordAutomation#35](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#35)]

10. Özgün paragraf metnini içine geri yükleyin `firstRange` .

     [!code-vb[Trin_VstcoreWordAutomation#36](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#36)]
     [!code-csharp[Trin_VstcoreWordAutomation#36](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#36)]

11. <xref:Microsoft.Office.Interop.Word.Range.InsertAfter%2A> <xref:Microsoft.Office.Interop.Word.Range> İkinci paragrafın ikinci içeriğini eklemek için nesnesinin yöntemini kullanın `firstRange` ve ardından öğesini seçin `firstRange` .

     [!code-vb[Trin_VstcoreWordAutomation#37](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#37)]
     [!code-csharp[Trin_VstcoreWordAutomation#37](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#37)]

## <a name="document-level-customization-example"></a>Belge düzeyi özelleştirmesi örneği

### <a name="to-control-paragraph-structure-when-inserting-text-in-document-level-customizations"></a>Belge düzeyi özelleştirmelerine metin eklerken paragraf yapısını denetlemek için

1. Aşağıdaki örnek, belge düzeyi özelleştirmesi için tam yöntemi gösterir. Bu kodu kullanmak için `ThisDocument` projenizdeki sınıftan çalıştırın.

     [!code-vb[Trin_VstcoreWordAutomation#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#26)]
     [!code-csharp[Trin_VstcoreWordAutomation#26](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#26)]

## <a name="vsto-add-in-example"></a>VSTO eklentisi örneği

### <a name="to-control-paragraph-structure-when-inserting-text-in-a-vsto-add-in"></a>VSTO eklentideki metin eklerken paragraf yapısını denetlemek için

1. Aşağıdaki örnek, bir VSTO eklentisi için tam yöntemi gösterir. Bu kodu kullanmak için `ThisAddIn` projenizdeki sınıftan çalıştırın.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#26)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#26](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#26)]

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: belgelerde aralıkları program aracılığıyla genişletme](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Nasıl yapılır: belgelerde aralıkları veya seçimleri program aracılığıyla daraltma](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Nasıl yapılır: program aracılığıyla Word belgelerine metin ekleme](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Nasıl yapılır: Word belgelerinde aralıkları program aracılığıyla sıfırlama](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Nasıl yapılır: belgelerde aralıkları program aracılığıyla tanımlama ve seçme](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
