---
title: Genişletilmiş nesneleri kullanarak Word 'Ü otomatikleştirme
description: Visual Studio 'da Word çözümleri geliştirirken, çözümlerinizde konak öğelerini ve konak denetimlerini nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], automating
- extended objects [Office development in Visual Studio], Word
- automation [Office development in Visual Studio], Word
- host items [Office development in Visual Studio], Word
- automating Word
- controls [Office development in Visual Studio], Word host controls
- host controls, Word
- host controls [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], host controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 39ac9d50d0f75f595568c66b02bda1c5ed46a3d6
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844458"
---
# <a name="automate-word-by-using-extended-objects"></a>Genişletilmiş nesneleri kullanarak Word 'Ü otomatikleştirme
  Visual Studio 'da Word çözümleri geliştirirken, çözümlerinizde *konak öğelerini* ve *konak denetimini* kullanabilirsiniz. Bunlar, ve nesneleri gibi, Word nesne modelinde (yani, Word için birincil birlikte çalışma derlemesi tarafından sunulan nesne modelinde) bazı yaygın kullanılan nesneleri genişleten nesnelerdir <xref:Microsoft.Office.Interop.Word.Document> <xref:Microsoft.Office.Interop.Word.ContentControl> . Genişletilmiş nesneler, temel aldığı Word nesneleri gibi davranır, ancak nesnelere ek olaylar ve veri bağlama özellikleri ekler.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Konak öğeleri ve konak denetimleri hem VSTO eklentileri hem de belge düzeyi özelleştirmelerinde kullanılabilir, ancak bunların kullanılabileceği bağlam her bir çözüm türü için farklılık açabilir. Daha fazla bilgi için bkz. [konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md).

## <a name="document-host-item"></a>Belge konak öğesi
 Word projeleri, <xref:Microsoft.Office.Tools.Word.Document> ana bilgisayar öğesine erişmenizi sağlar. <xref:Microsoft.Office.Tools.Word.Document>Konak öğesi, konak denetimleri ve Windows Forms denetimleri de dahil olmak üzere diğer denetimler için bir kapsayıcı görevi görür ve yüzeyinde denetimlerle ilgili bilgileri saklar. <xref:Microsoft.Office.Tools.Word.Document>Konak öğesi ayrıca <xref:Microsoft.Office.Interop.Word.Document> , Word nesne modelinde karşılık gelen sınıf olan sınıf ile aynı üyelerin çoğunu sağlar.

 Daha fazla bilgi için bkz. [belge konak öğesi](../vsto/document-host-item.md).

## <a name="word-host-controls"></a>Word konak denetimleri
 Word için belgeler oluşturmanıza, düzenlemenize ve otomatikleştirmenize yardımcı olan birkaç konak denetimi vardır. İşlevlerinin çoğu, verileri içeri aktarmayı, sunmayı ve korumayı içerir. Bu konak denetimleri, yerel sözcük nesne modelindeki karşılıkları olmayan olaylar ve veri bağlama özellikleri sağlar.

 Belge düzeyi projelerinde, tasarım zamanında belgenize herhangi bir konak denetimi ekleyebilir veya çalışma zamanında içerik denetimleri ve yer işareti denetimleri ekleyebilirsiniz. VSTO eklenti projelerinde, çalışma zamanında herhangi bir açık belgeye içerik denetimleri ve yer işareti denetimleri ekleyebilirsiniz.

 Word projelerinde kullanabileceğiniz konak denetimleri hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [İçerik denetimleri](../vsto/content-controls.md)

- [Yer işareti denetimi](../vsto/bookmark-control.md)

- [XMLNode denetimi](../vsto/xmlnode-control.md)

- [XMLNodes denetimi](../vsto/xmlnodes-control.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Word belgelerine içerik denetimleri ekleme](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Nasıl yapılır: Word belgelerine yer Işareti denetimleri ekleme](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Nasıl yapılır: Word belgelerine XMLNode denetimleri ekleme](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)
- [Nasıl yapılır: Word belgelerine XMLNodes denetimleri ekleme](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)
- [Nasıl yapılır: yer Işareti denetimlerini yeniden boyutlandırma](../vsto/how-to-resize-bookmark-controls.md)
- [İzlenecek yol: içerik denetimlerini kullanarak şablon oluşturma](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)
- [İzlenecek yol: içerik denetimlerini özel XML bölümlerine bağlama](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)
- [İzlenecek yol: yer işaretleri için kısayol menüleri oluşturma](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)
- [Word çözümleri](../vsto/word-solutions.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [VSTO Eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
