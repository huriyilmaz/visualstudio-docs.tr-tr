---
title: Çalışma zamanında & Excel çalışma kitaplarını VSTO word belgeleri genişletme
description: Word belgelerini özelleştirmek ve çalışma VSTO çeşitli yollarla özelleştirmek için Excel eklentiyi kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- GetVstoObject method
- application-level add-ins [Office development in Visual Studio], adding controls to documents
- host items [Office development in Visual Studio], creating at run time in add-ins
- application-level add-ins [Office development in Visual Studio], extending Word documents
- application-level add-ins [Office development in Visual Studio], extending Excel workbooks
- controls [Office development in Visual Studio], adding at run time
- HasVstoObject method
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 9eee0002f426fb1134370b1f7bd8a90fdea79b14
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122047016"
---
# <a name="extend-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time"></a>Çalışma zamanında word Excel ve VSTO çalışma kitaplarını genişletme
  Word belgelerini özelleştirmek VSTO ve çalışma kitaplarını aşağıdaki yollarla Excel bir eklenti kullanabilirsiniz:

- Herhangi bir açık belgeye veya çalışma sayfasına yönetilen denetimler ekleyin.

- Excel çalışma sayfasındaki mevcut bir liste nesnesini olayları ortaya çıkaran ve Windows Forms veri bağlama modeli kullanılarak <xref:Microsoft.Office.Tools.Excel.ListObject> verilere bağlanılan genişletilmiş bir çalışma sayfasına dönüştürebilirsiniz.

- Belirli belgeler, çalışma kitapları ve çalışma sayfaları için Word Excel uygulama düzeyinde olaylara erişin.

  Bu işlevi kullanmak için çalışma zamanında belgeyi veya çalışma kitabını genişleten bir nesne oluşturursanız.

  **Aşağıdakiler için geçerlidir:** Bu makaledeki bilgiler, VSTO uygulamaları için eklenti projelerinde geçerlidir: Excel Word. Daha fazla bilgi için [bkz. Uygulama ve Office tarafından kullanılabilen özellikler.](../vsto/features-available-by-office-application-and-project-type.md)

## <a name="generate-extended-objects-in-vsto-add-ins"></a>Eklentilerde genişletilmiş VSTO oluşturma
 *Genişletilmiş nesneler,* Word veya Excel nesne modellerinde (yerel nesne nesneleri olarak adlandırılan) var olan nesnelere işlevsellik ek olarak Office için Visual Studio Araçları çalışma zamanı tarafından sağlanan *Office örnekleridir.* Word veya Excel için genişletilmiş nesne oluşturmak üzere yöntemini `GetVstoObject` kullanın. Belirtilen bir Word veya Excel için yöntemini ilk kez çağırarak, belirtilen nesneyi `GetVstoObject` genişleten yeni bir nesne döndürür. yöntemini her çağırarak aynı Word veya Excel belirttiğinizde, aynı genişletilmiş nesneyi döndürür.

 Genişletilmiş nesnenin türü, yerel Office nesnesinin türüyle aynı adı içerir, ancak tür veya ad <xref:Microsoft.Office.Tools.Excel> alanı içinde <xref:Microsoft.Office.Tools.Word> tanımlanır. Örneğin, bir nesneyi genişletmek `GetVstoObject` için yöntemini <xref:Microsoft.Office.Interop.Word.Document> çağırsanız, yöntemi bir nesnesi <xref:Microsoft.Office.Tools.Word.Document> döndürür.

 Yöntemlerin `GetVstoObject` öncelikli olarak Eklenti projelerinde VSTO amaçlanan yöntemlerdir. Bu yöntemleri belge düzeyi projelerde de kullanabilirsiniz, ancak bunlar farklı davranır ve daha az kullanım içerir.

 Genişletilmiş bir nesnenin belirli bir yerel nesne için zaten oluşturulmuş olup olmadığını belirlemek Office yöntemini `HasVstoObject` kullanın. Daha fazla bilgi için [bkz. Bir Office genişletilmiş olup olmadığını belirleme.](#HasVstoObject)

### <a name="generate-host-items"></a>Konak öğeleri oluşturma
 Bir belge düzeyi nesnesini (yani , veya ) genişletmek için öğesini kullanırsanız, `GetVstoObject` döndürülen nesne konak öğesi olarak <xref:Microsoft.Office.Interop.Excel.Workbook> <xref:Microsoft.Office.Interop.Excel.Worksheet> <xref:Microsoft.Office.Interop.Word.Document> *çağrılır.* Konak öğesi, diğer genişletilmiş nesneler ve denetimler de dahil olmak üzere diğer nesneleri içere bir tür. Word veya Excel birincil birlikte çalışma derlemesinde karşılık gelen türe benzer, ancak ek özellikleri vardır. Konak öğeleri hakkında daha fazla bilgi için bkz. [Konak öğelerine ve konak denetimlerine genel bakış.](../vsto/host-items-and-host-controls-overview.md)

 Bir konak öğesi oluşturmanın ardından belgeye, çalışma kitabına veya çalışma sayfasına yönetilen denetimler eklemek için bunu kullanabilirsiniz. Daha fazla bilgi için [bkz. Belgelere ve çalışma sayfalarına yönetilen denetimler ekleme.](#AddControls)

#### <a name="to-generate-a-host-item-for-a-word-document"></a>Word belgesi için konak öğesi oluşturmak için

- Aşağıdaki kod örneği, etkin belge için bir konak öğesinin nasıl oluşturulmakta olduğunu gösterir.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet8":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet8":::

#### <a name="to-generate-a-host-item-for-an-excel-workbook"></a>Bir çalışma kitabı için konak Excel oluşturmak için

- Aşağıdaki kod örneği, etkin çalışma kitabı için bir konak öğesi oluşturmayı gösterir.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs" id="Snippet2":::

#### <a name="to-generate-a-host-item-for-an-excel-worksheet"></a>Bir çalışma sayfası için konak Excel oluşturmak için

- Aşağıdaki kod örneği, bir projede etkin çalışma sayfası için bir konak öğesi oluşturmayı gösterir.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs" id="Snippet1":::

### <a name="generate-listobject-host-controls"></a>ListObject konak denetimleri oluşturma
 bir genişletmek için `GetVstoObject` yöntemini <xref:Microsoft.Office.Interop.Excel.ListObject> kullanırken, yöntemi bir <xref:Microsoft.Office.Tools.Excel.ListObject> döndürür. <xref:Microsoft.Office.Tools.Excel.ListObject>, özgün 'nin tüm özelliklerine <xref:Microsoft.Office.Interop.Excel.ListObject> sahiptir. Ayrıca ek işlevlere de sahip olur ve Windows Forms veri bağlama modeli kullanılarak verilere bağlanabilirsiniz. Daha fazla bilgi için bkz. [ListObject denetimi.](../vsto/listobject-control.md)

#### <a name="to-generate-a-host-control-for-a-listobject"></a>ListObject için konak denetimi oluşturmak için

- Aşağıdaki kod örneği, bir projesinde etkin <xref:Microsoft.Office.Tools.Excel.ListObject> çalışma sayfasında ilk için bir oluşturma <xref:Microsoft.Office.Interop.Excel.ListObject> adımlarını gösterir.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb" id="Snippet3":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs" id="Snippet3":::

### <a name="add-managed-controls-to-documents-and-worksheets"></a><a name="AddControls"></a> Belgelere ve çalışma sayfalarına yönetilen denetimler ekleme
 bir veya <xref:Microsoft.Office.Tools.Word.Document> ekleyebilirsiniz <xref:Microsoft.Office.Tools.Excel.Worksheet> sonra bu genişletilmiş nesneleri temsil belge veya çalışma sayfasına denetimler ekleyebilirsiniz. Denetim eklemek için veya `Controls` özelliğini <xref:Microsoft.Office.Tools.Word.Document> <xref:Microsoft.Office.Tools.Excel.Worksheet> kullanın. Daha fazla bilgi için [bkz. Çalışma zamanında Office belgelerine denetim ekleme.](../vsto/adding-controls-to-office-documents-at-run-time.md)

 Formlar denetimleri Windows konak denetimleri *eklersiniz.* Konak denetimi, Tarafından sağlanan ve Word veya birincil birlikte çalışma derlemesinde karşılık gelen [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] bir denetimi Excel denetimdir. Konak denetimi, temel alınan yerel nesnedeki tüm davranışları Office gösterir. Ayrıca olayları da oluşturur ve Windows Forms veri bağlama modelini kullanarak verilere bağlanabilirsiniz. Daha fazla bilgi için bkz. [Konak öğelerine ve konak denetimlerine genel bakış.](../vsto/host-items-and-host-controls-overview.md)

> [!NOTE]
> Bir çalışma sayfası veya bir belgeye bir veya denetimi, bir çalışma sayfası eklentisinde VSTO <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> <xref:Microsoft.Office.Tools.Word.XMLNode> <xref:Microsoft.Office.Tools.Word.XMLNodes> ekamazsınız. Bu konak denetimleri program aracılığıyla ek olamaz. Daha fazla bilgi için [bkz. Konak öğelerinin ve konak denetimlerinin programlı sınırlamaları.](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)

### <a name="persist-and-remove-controls"></a>Denetimleri kalıcı olarak kaldırma ve kaldırma
 Bir belgeye veya çalışma sayfasına yönetilen denetimler eklerken, belge kaydedilsin ve sonra kapatıldıklarında denetimler kalıcı olmaz. Tüm konak denetimleri kaldırılarak yalnızca temel alınan yerel Office nesneleri geride bırakılacaktır. Örneğin, bir <xref:Microsoft.Office.Tools.Excel.ListObject> <xref:Microsoft.Office.Interop.Excel.ListObject> olur. Tüm Windows Forms denetimleri de kaldırılır, ActiveX sarmalayıcılar belgede geride bırakılmıştır. Denetimleri temizlemek veya belge bir VSTO yeniden oluşturmak için eklentinize kod eklemeniz gerekir. Daha fazla bilgi için [bkz. Dinamik denetimleri belgelerde Office.](../vsto/persisting-dynamic-controls-in-office-documents.md)

## <a name="access-application-level-events-on-documents-and-workbooks"></a>Belgelerde ve çalışma kitaplarında uygulama düzeyinde olaylara erişme
 Yerel Word ve Excel nesne modellerinde bazı belge, çalışma kitabı ve çalışma sayfası olayları yalnızca uygulama düzeyinde yükseltildi. Örneğin, bir belge Word'de açıldığında olay ortaya çıkar, ancak bu <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> olay sınıfı yerine sınıfında <xref:Microsoft.Office.Interop.Word.Application> <xref:Microsoft.Office.Interop.Word.Document> tanımlanır.

 VSTO Eklentiniz içinde yalnızca yerel Office nesneleri kullanıyorsanız, bu uygulama düzeyi olayları işlemeli ve ardından olayı yükselten belgenin özelleştirmiş olduğunu belirlemek için ek kod yazmanız gerekir. Konak öğeleri bu olayları belge düzeyinde sağlar, böylece belirli bir belgenin olaylarını işlemesi daha kolay olur. Bir konak öğesi oluşturabilirsiniz ve ardından bu konak öğesi için olayı işebilirsiniz.

### <a name="example-that-uses-native-word-objects"></a>Yerel Word nesneleri kullanan örnek
 Aşağıdaki kod örneği, Word belgeleri için uygulama düzeyinde bir olayın nasıl işlen bir olduğunu gösteriyor. yöntemi `CreateDocument` yeni bir belge oluşturur ve ardından bu belgenin <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> kaydedilene bir olay işleyicisi tanımlar. Olay, nesnesi için yükseltilmiş uygulama düzeyinde bir olaydır ve olay işleyicisi kaydedilen belgeyi temsil ettiğini belirlemek için parametresini <xref:Microsoft.Office.Interop.Word.Application> `Doc` `document1` `document1` nesnesiyle karşılaştırmalı.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet12":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet12":::

### <a name="examples-that-use-a-host-item"></a>Konak öğesi kullanan örnekler
 Aşağıdaki kod örnekleri, bir konak öğesinin olaylarını <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> işerek bu işlemi <xref:Microsoft.Office.Tools.Word.Document> basitleştirir. Bu örneklerde yöntemi nesnesini genişleten bir oluşturur ve ardından belgenin kaydedilene `CreateDocument2` <xref:Microsoft.Office.Tools.Word.Document> bir olay `document2` <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> işleyicisi tanımlar. Olay işleyicisi yalnızca kaydedilirken çağrılır ve hangi belgenin kayded edildiğini doğrulamak için ek bir çalışma yapmadan kaydetme `document2` eylemini iptal edebilir.

 Aşağıdaki kod örneği bu görevi gösterir.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet13":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet13":::

## <a name="determine-whether-an-office-object-has-been-extended"></a><a name="HasVstoObject"></a>Bir Office genişletilmiş olup olmadığını belirleme
 Genişletilmiş bir nesnenin belirli bir yerel nesne için zaten oluşturulmuş olup olmadığını belirlemek Office yöntemini `HasVstoObject` kullanın. Genişletilmiş bir **nesne** zaten oluşturulmuşsa bu yöntem true döndürür.

 `Globals.Factory.HasVstoMethod` yöntemini kullanın. Genişletilmiş bir nesne için test Excel veya gibi yerel Word veya Excel <xref:Microsoft.Office.Interop.Word.Document> <xref:Microsoft.Office.Interop.Excel.Worksheet> nesnesini iletir.

 yöntemi, yalnızca belirtilen bir nesnede genişletilmiş bir nesne `HasVstoObject` Office çalıştırmak istediğiniz zaman kullanışlıdır. Örneğin, belgeyi kaydedilmeden önce bir belgeden yönetilen denetimleri kaldırmak için olayı ele alan bir Word VSTO Eklentiniz varsa, belgenin genişletilip genişletil olmadığını belirlemek için <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> `HasVstoObject` yöntemini kullanın. Belge genişletilmasa, yönetilen denetimlere sahip olamaz ve olay işleyicisi belgede denetimleri temizlemeye çalışmadan geri dönebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Program VSTO Eklentileri](../vsto/programming-vsto-add-ins.md)
- [Çalışma zamanında Office denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Konak öğelerine ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Office örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)
