---
title: Belge konak öğesi
description: Belge konak öğesinin, Word için birincil birlikte çalışma derlemesinde Belge türünü genişleten bir tür olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio]
- documents [Office development in Visual Studio], document host items
- document host items
- Word [Office development in Visual Studio], Word documents
- Word [Office development in Visual Studio]
- Word documents
- host items [Office development in Visual Studio], Document
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 4bfb1ce70bddec5a92c48dde6f67256f1a9b63e2391701a6e33ebeb1b5591276
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121268397"
---
# <a name="document-host-item"></a>Belge konak öğesi
  Konak <xref:Microsoft.Office.Tools.Word.Document> öğesi, Word için birincil birlikte çalışma <xref:Microsoft.Office.Interop.Word.Document> derlemesi türünü genişleten bir tür. Konak öğesi bir nesneyle aynı özellikleri, yöntemleri ve olayların hepsini sağlar, ancak ek olayları da açığa çıkarır ve konak denetimleri ve Formlar denetimleri için kapsayıcı <xref:Microsoft.Office.Tools.Word.Document> <xref:Microsoft.Office.Interop.Word.Document> olarak Windows davranır.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Belge düzeyi projelerde, projeniz içinde <xref:Microsoft.Office.Tools.Word.Document> belgeyi temsil eden varsayılan bir konak öğesi vardır. Eklenti VSTO içinde, çalışma zamanında <xref:Microsoft.Office.Tools.Word.Document> konak öğeleri oluşturabilirsiniz.

## <a name="understand-the-document-host-item-in-document-level-projects"></a>Belge düzeyi projelerinde belge konak öğesini anlama
 Projenizin belgeye erişmek için sınıfını `ThisDocument` kullanın. Belge düzeyi proje ekleyebilirsiniz, Visual Studio Word ve özelleştirme kodunuz arasındaki iletişim `ThisDocument` bağlantısı olarak hizmet verecek sınıfı üretir. sınıfı, belge açıldığında veya kapatılan kod çalıştırma gibi temel görevleri gerçekleştirmek için konak öğesinin `ThisDocument` <xref:Microsoft.Office.Tools.Word.Document> üyelerine erişmenizi sağlar. Belgeye denetim eklemek için sınıfını da kullanabilirsiniz. Farklı denetim kümelerini birleştirerek ve kod yazarak, denetimleri verilere bağlayabilirsiniz, kullanıcıdan bilgi toplayabilirsiniz ve kullanıcı eylemlerini yanıtlayabilirsiniz. Daha fazla bilgi için [bkz. Program belge düzeyi özelleştirmeleri.](../vsto/programming-document-level-customizations.md)

 sınıfı, `ThisDocument` projenize kod yazmaya başlarınızı sağlayan bir konum sağlar. sınıfı Word için birincil birlikte çalışma derlemesinde nesneyle aynı özellikleri, yöntemleri ve olayları sağladığı için, Word nesne modeline erişmek için de <xref:Microsoft.Office.Interop.Word.Document> `ThisDocument` kullanabilirsiniz. Daha fazla bilgi için bkz. [Word nesne modeline genel bakış.](../vsto/word-object-model-overview.md)

### <a name="limitations-of-the-document-host-item-in-document-level-projects"></a>Belge düzeyindeki projelerde belge konak öğesinin sınırlamaları
 Belge düzeyi proje yalnızca bir konak <xref:Microsoft.Office.Tools.Word.Document> öğesi (yani sınıfı) `ThisDocument` içerebilir. Tasarım zamanında projenize yeni konak öğeleri ekamazsınız ve çalışma zamanında belge düzeyi özelleştirmeden <xref:Microsoft.Office.Tools.Word.Document> <xref:Microsoft.Office.Tools.Word.Document> yeni konak öğeleri oluşturamazsınız.

 Çalışma zamanında yeni bir Word belgesi ekleyebilirsiniz. <xref:Microsoft.Office.Interop.Word.Document> Bir konak öğesi olduğundan, herhangi bir konak denetimi içere Windows Forms denetimleri içeramaz. Çalışma zamanında belge oluşturma hakkında daha fazla bilgi için [bkz. Nasıl kullanılır: Program aracılığıyla yeni belgeler oluşturma.](../vsto/how-to-programmatically-create-new-documents.md)

## <a name="understand-document-host-items-in-application-level-projects"></a>Uygulama düzeyindeki projelerde belge konak öğelerini anlama
 Eklenti VSTO içinde, Word'de açık olan herhangi bir belge için çalışma zamanında <xref:Microsoft.Office.Tools.Word.Document> bir konak öğesi oluşturabilirsiniz. İlişkili belgeye denetim eklemek veya nesnelerde mevcut olan olayları işlemek için konak <xref:Microsoft.Office.Tools.Word.Document> öğesini <xref:Microsoft.Office.Interop.Word.Document> kullanabilirsiniz.

 Konak öğesi <xref:Microsoft.Office.Tools.Word.Document> oluşturmak için yöntemini `GetVstoObject` kullanın. Daha fazla bilgi için bkz. Word belgelerini genişletme Excel çalışma VSTO çalışma [kitaplarını çalışma zamanında genişletme.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Konak öğelerine ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Genişletilmiş nesneleri kullanarak Word'i otomatikleştirme](../vsto/automating-word-by-using-extended-objects.md)
- [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md)
- [Konak öğelerinin ve konak denetimlerinin programlı sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Çalışma zamanında Word Excel ve VSTO çalışma kitaplarını genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
