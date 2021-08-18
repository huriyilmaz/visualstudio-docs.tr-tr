---
title: Yer işareti denetimi
description: Yer İşareti denetimi benzersiz bir adı olan, olayları ortaya çıkaran ve verilere bağlanan bir yer işareti olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.Bookmark
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- bookmarks, controlling
- Bookmark control, data binding
- Bookmark control, events
- Bookmark control
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 054019a9c683924d27963a8be6d67679c8feb65d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122047224"
---
# <a name="bookmark-control"></a>Yer işareti denetimi
  Denetim, <xref:Microsoft.Office.Tools.Word.Bookmark> benzersiz bir adı olan, olayları ortaya çıkaran ve verilere bağlanan bir yer işaretidir. Yer işareti, Word belgesinde bir öğeyi veya konumu işaretlemek için yer Microsoft Office kullanılabilir. Denetim, <xref:Microsoft.Office.Tools.Word.Bookmark> bir nesnesi ve <xref:Microsoft.Office.Interop.Word.Bookmark> nesnesinin <xref:Microsoft.Office.Interop.Word.Range> birleşimidir.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Belge düzeyindeki projelerde, tasarım <xref:Microsoft.Office.Tools.Word.Bookmark> zamanında veya çalışma zamanında belgenize denetimler ekleyebilirsiniz. Eklenti VSTO içinde, çalışma zamanında herhangi bir <xref:Microsoft.Office.Tools.Word.Bookmark> açık belgeye denetim ekleyebilirsiniz. Daha fazla bilgi için [bkz. Nasıl kullanılır: Word belgelerine Yer İşareti denetimleri ekleme.](../vsto/how-to-add-bookmark-controls-to-word-documents.md)

## <a name="bind-data-to-the-control"></a>Denetime veri bağlama
 Denetim <xref:Microsoft.Office.Tools.Word.Bookmark> basit veri bağlamayı destekler. Yer işareti özelliği kullanılarak bir veri kaynağına <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> bağlanmalıdır. Yer işaretinin varsayılan veri bağlama özelliği <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> özelliğidir.

 Bağlı veri kümesinde veriler güncelleştirildiğinde denetim <xref:Microsoft.Office.Tools.Word.Bookmark> değişiklikleri gösterir.

 Belge düzeyindeki projelerde, Veri Kaynakları penceresini kullanarak verileri yer işaretlerine **de bekleyebilirsiniz.** Daha fazla bilgi için, [bkz. How to: Populate documents with data from objects](../vsto/how-to-populate-documents-with-data-from-objects.md).

## <a name="formatting"></a>Biçimlendirme
 bir denetimine uygulanan <xref:Microsoft.Office.Interop.Word.Bookmark> biçimlendirme bir denetime <xref:Microsoft.Office.Tools.Word.Bookmark> uygulanabilir. Bu biçimlendirme yazı tiplerini, girintileri, boşlukları, numaralamayı ve stilleri içerir.

## <a name="assign-text-to-the-bookmark"></a>Yer işaretine metin atama
 Bir nesne ile denetim <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType> arasındaki ek <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> bir fark, yer işaretine metin atandığı zaman nasıl davrandığıdır. Metni sıfır uzunluklu bir değere atarsanız, metin yer işaretinin sağ bölümüne eklenir ve <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType> yer işareti sıfır uzunlukta kalır. Ancak, sıfır uzunluklu bir metne metin atarsanız, metin yer işaretine eklenir ve yer işaretinin uzunluğu eklenen toplam <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> karakter sayısına genişler.

 Denetimin <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> özelliği de <xref:Microsoft.Office.Tools.Word.Bookmark.Text?displayProperty=nameWithType> vardır. Bu özellik, bir denetimin özelliği veya bir nesnenin özelliği üzerinde kullanılabilen <xref:Microsoft.Office.Interop.Word.Range.Text?displayProperty=nameWithType> <xref:Microsoft.Office.Tools.Word.Bookmark.Range?displayProperty=nameWithType> <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> <xref:Microsoft.Office.Interop.Word.Bookmark.Range?displayProperty=nameWithType> özellikten <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType> farklıdır.

|Text Özelliği|Açıklama|
|-------------------|-----------------|
|<xref:Microsoft.Office.Tools.Word.Bookmark.Text?displayProperty=nameWithType>|Bu özelliği kullanarak yer işareti içinde metin görüntüleniyor ve yer işareti belgede bırakılacak. Yer işaretine metin atama, yer işareti aralığını genişleterek yer işaretini silemez.<br /><br /> Örneğin, `Bookmark1.Text = "Hello world"` metni yer işaretine ekler ve yer işaretini olduğu gibi bırakır.|
|<xref:Microsoft.Office.Interop.Word.Range.Text?displayProperty=nameWithType>|Yer işareti konumda metin görüntülemek ve yer işaretini otomatik olarak silmek için bu özelliği kullanın. Örneğin, `Bookmark1.Range.Text = "Hello world"` metni yer işaretine ekler ve yer işaretini siler.|

## <a name="rename-the-control-at-design-time"></a>Denetimi tasarım zamanında yeniden adlandırma
 Belge düzeyindeki projelerde, Araç Kutusundan belgenize bir denetim sürüklerken Visual Studio otomatik olarak <xref:Microsoft.Office.Tools.Word.Bookmark> bir ad oluşturulur.  Özellikler penceresinde denetimin adını **değiştirebilirsiniz.**

## <a name="overlapping-controls"></a>Çakışan denetimler
 Yer işareti denetimleri birbiriyle çakışabilir. Aynı metin birden fazla yer işareti tarafından paylaşılır. Çakışan yer işaretlerinden biri için yeni metin atadığınız zaman, yalnızca yeni metni içerir ve yer işaretleri artık çakışmaz. Diğer yer işareti artık yalnızca çakışan özgün yer işaretleri arasında paylaşılmaan metni içerir.

 Aşağıdaki tabloda "Bu örnek metindir" cümlesini gösterir. çakışan iki yer işareti tarafından paylaşılır:

|Yer işareti|Metin|
|--------------|----------|
|Çakışan yer işaretleri|[bu {örnek] metindir.}|
|Bookmark1|Bu örnek|
|Bookmark2|örnek metin.|

 Yeni "Bu değiştirmedir" metnini atarsanız Bookmark1 için yer işaretleri çakışmaz ve Bookmark2 yalnızca Bookmark1'in ilk parçası olan metni korur.

|Yer işareti|Metin|
|--------------|----------|
|İki ayrı yer işareti|[bu değiştirmedir] { text.}|
|Bookmark1|Bu, değiştirmedir|
|Bookmark2|Metin.|

Başka bir yer işareti içeren bir yer işaretinin metnini değiştirirsiniz, iç yer işareti silinmez. Ancak iç yer işareti boş bir yer işareti olur ve dış yer işaretinin sonuna taşınır.

Aşağıdaki tabloda "Bu örnek metindir" cümlesini gösterir. başka bir yer işareti içinde yer alan bir yer işareti tarafından paylaşılır:

|Yer işareti|Metin|
|--------------|----------|
|Çakışan yer işaretleri|[bu {sample} metnidir.]|
|Bookmark1|Bu örnek metindir.|
|Bookmark2|örnek|

 Yeni "Bu değiştirmedir" metnini atarsanız Bookmark1 için yer işaretleri artık çakışmaz ve Bookmark2, Bookmark1'in sonunda bulunan boş bir yer işareti olur.

|Yer işareti|Metin|
|--------------|----------|
|İki ayrı yer işareti|[bu değiştirmedir.]{}|
|Bookmark1|Bu değiştirmedir.|
|Bookmark2|*\<empty>*|

## <a name="events"></a>Ekinlikler

Denetim için aşağıdaki olaylar <xref:Microsoft.Office.Tools.Word.Bookmark> kullanılabilir:

- <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Word.Bookmark.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Word.Bookmark.Deselected>

- <xref:System.ComponentModel.IComponent.Disposed>

- <xref:Microsoft.Office.Tools.Word.Bookmark.Selected>

- <xref:Microsoft.Office.Tools.Word.Bookmark.SelectionChange>

## <a name="see-also"></a>Ayrıca bkz.

- [Genişletilmiş nesneleri kullanarak Word'i otomatikleştirme](../vsto/automating-word-by-using-extended-objects.md)
- [Nasıl kullanılır: Word belgelerine Yer İşareti denetimleri ekleme](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Adım adım kılavuz: Yer işaretleri için kısayol menüleri oluşturma](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)
- [Veri çözümlerinin denetimlerini Office bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Konak öğelerinin ve konak denetimlerinin programlı sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)