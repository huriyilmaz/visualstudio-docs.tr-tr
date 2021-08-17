---
title: 'Nasıl gösterilir: Eylemler bölmeleri üzerinde denetim düzenini yönetme'
description: Kullanıcı denetimlerini düzgün bir şekilde yığma kodu yazarak eylem bölmeleri üzerinde denetim düzenini nasıl yönetebilirsiniz?
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], control layout
- controls [Office development in Visual Studio], layout on actions panes
- smart documents [Office development in Visual Studio], control layout
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 65da62970b798e2a6f608a72199f5c05d2179175
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122106308"
---
# <a name="how-to-manage-control-layout-on-actions-panes"></a>Nasıl gösterilir: Eylemler bölmeleri üzerinde denetim düzenini yönetme
  Eylemler bölmesi varsayılan olarak bir belgenin veya çalışma sayfasının sağ tarafından yerleştirildi; ancak, sola, üst veya alta yerleştir olabilir. Birden çok kullanıcı denetimi kullanıyorsanız, kullanıcı denetimlerini eylemler bölmesinde düzgün bir şekilde yığacak kodlar yazabilirsiniz. Daha fazla bilgi için bkz. [Eylemler bölmesine genel bakış.](../vsto/actions-pane-overview.md)

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Denetimlerin yığın sırası, eylemler bölmesinin dikey veya yatay olarak sabitlenme durumuna bağlıdır.

> [!NOTE]
> Kullanıcı çalışma zamanında eylemler bölmesini yeniden boyutlandırıyorsa, denetimleri eylemler bölmesiyle yeniden boyutlandırmak için ayarlayın. Denetimleri eylemler <xref:System.Windows.Forms.Control.Anchor%2A> bölmesine sabitlerken Windows Forms denetimi özelliğini kullanabilirsiniz. Daha fazla bilgi için, [bkz. How to: Anchor controls on Windows Forms](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms).

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [bkz. IDE'Visual Studio kişiselleştirme.](../ide/personalizing-the-visual-studio-ide.md)

## <a name="to-set-the-stack-order-of-the-actions-pane-controls"></a>Eylemler bölmesi denetimlerinin yığın sıralamalarını ayarlamak için

1. Microsoft Office Word için birden çok kullanıcı denetimine veya iç içe geçmiş eylemler bölmesi denetimine sahip eylemler bölmesi içeren belge düzeyinde bir proje açın. Daha fazla bilgi için [bkz. Nasıl kullanılır: Word belgelerine](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)veya çalışma kitaplarını Excel bölmesi ekleme.

2. Içinde **ThisDocument.cs veya** **ThisDocument.vb'ye** **sağ Çözüm Gezgini** ve ardından Kodu **Görüntüle'ye tıklayın.**

3. Eylemler <xref:Microsoft.Office.Tools.ActionsPane.OrientationChanged> bölmesinin olay işleyicisinde, eylemler bölmesinin yönünün yatay olup değildir.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet30":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet30":::

4. Yönlendirme yataysa, eylem bölmesi denetimlerini soldan yığabilirsiniz; aksi takdirde, bunları en üstten yığabilirsiniz.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet31":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet31":::

5. C# içinde, olay işleyicisi için bir olay `ActionsPane` <xref:Microsoft.Office.Tools.Word.Document.Startup> işleyicisi eklemeniz gerekir. Olay işleyicileri oluşturma hakkında daha fazla bilgi için [bkz. Nasıl oluşturulur: Office projelerinde olay işleyicileri oluşturma.](../vsto/how-to-create-event-handlers-in-office-projects.md)

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet32":::

6. Projeyi çalıştırın ve eylemler bölmesi belgenin en üstüne yerleştirildiyken eylemler bölmesi denetimlerinin soldan sağa yığılmış olduğunu ve eylemler bölmesi belgenin sağ tarafına yerleştirildiklerinden denetimlerin üstten aşağıya yığılmış olduğunu doğrulayın.

## <a name="example"></a>Örnek
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet29":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet29":::

## <a name="compile-the-code"></a>Kodu derleme
 Bu örnek şunları gerektirir:

- Birden çok kullanıcı denetimi veya iç içe geçmiş eylemler bölmesi denetimi içeren eylemler bölmesine sahip bir Word belge düzeyi projesi.

## <a name="see-also"></a>Ayrıca bkz.
- [Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md)
- [Nasıl kullanılır: Word belgelerine veya çalışma kitaplarını Excel bölmesi ekleme](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Nasıl kullanılır: Word Belgelerine veya çalışma kitaplarını Excel bölmesi ekleme](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Adım adım kılavuz: Eylemler bölmesinden belgeye metin ekleme](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [Adım adım kılavuz: Eylemler bölmesinden belgeye metin ekleme](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
