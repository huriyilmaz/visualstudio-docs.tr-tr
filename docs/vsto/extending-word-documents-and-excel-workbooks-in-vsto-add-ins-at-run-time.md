---
title: çalışma zamanında VSTO eklentilerindeki Word belgeleri & Excel çalışma kitaplarını genişletme
description: Word belgelerini ve Excel çalışma kitaplarını çeşitli yollarla özelleştirmek için bir VSTO eklentisi kullanabileceğinizi öğrenin.
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
ms.openlocfilehash: 9dd9a3d46823ed53310b355fc8d122c5f64d1234d584cd85b8a7c43959ff4c4a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121352090"
---
# <a name="extend-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time"></a>Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında VSTO eklentilerde genişletme
  Word belgelerini ve Excel çalışma kitaplarını aşağıdaki yollarla özelleştirmek için bir VSTO eklentisi kullanabilirsiniz:

- Yönetilen denetimleri herhangi bir açık belge veya çalışma sayfasına ekleyin.

- Excel çalışma sayfasındaki var olan bir liste nesnesini <xref:Microsoft.Office.Tools.Excel.ListObject> , olayları ortaya çıkaran ve Windows Forms veri bağlama modeli kullanılarak verilere bağlanabilen bir genişletmeye dönüştürür.

- Word tarafından sunulan ve belirli belgeler, çalışma kitapları ve çalışma sayfaları için Excel uygulama düzeyindeki olaylara erişin.

  Bu işlevi kullanmak için, çalışma zamanında belgeyi veya çalışma kitabını genişleten bir nesne oluşturursunuz.

  **Uygulama hedefi:** bu makaledeki bilgiler, aşağıdaki uygulamalar için VSTO eklenti projelerine yöneliktir: Excel ve Word. daha fazla bilgi için bkz. [Office uygulama ve proje türü tarafından kullanılabilen özellikler](../vsto/features-available-by-office-application-and-project-type.md).

## <a name="generate-extended-objects-in-vsto-add-ins"></a>VSTO eklentilerinde genişletilmiş nesneler oluşturma
 *genişletilmiş nesneler* , sözcük veya Excel nesne modelleriyle ( *yerel Office nesneleri* olarak adlandırılır) yerel olarak var olan nesnelere işlevsellik ekleyen Office için Visual Studio Araçları çalışma zamanı tarafından verilen türlerin örnekleridir. bir kelime veya Excel nesnesi için genişletilmiş bir nesne oluşturmak için `GetVstoObject` yöntemini kullanın. `GetVstoObject`belirtilen bir kelime veya Excel nesnesi için yöntemi ilk kez çağırdığınızda, belirtilen nesneyi genişleten yeni bir nesne döndürür. yöntemini her çağırdığınızda ve aynı kelimeyi veya Excel nesnesini belirttiğinizde, aynı genişletilmiş nesneyi döndürür.

 genişletilmiş nesnenin türü, yerel Office nesnesinin türüyle aynı ada sahiptir, ancak tür <xref:Microsoft.Office.Tools.Excel> veya <xref:Microsoft.Office.Tools.Word> ad alanında tanımlanır. Örneğin, `GetVstoObject` bir nesneyi genişletmek için yöntemini çağırırsanız <xref:Microsoft.Office.Interop.Word.Document> , yöntemi bir <xref:Microsoft.Office.Tools.Word.Document> nesnesi döndürür.

 `GetVstoObject`yöntemler öncelikle VSTO eklenti projelerinde kullanılmak üzere tasarlanmıştır. Bu yöntemleri belge düzeyi projelerde da kullanabilirsiniz, ancak bunları farklı şekilde ve daha az kullanımlar vardır.

 bir genişletilmiş nesnenin belirli bir yerel Office nesnesi için önceden oluşturulup oluşturulmayacağını anlamak için `HasVstoObject` yöntemini kullanın. daha fazla bilgi için, bkz. [bir Office nesnesinin genişletilmiş olup olmadığını belirleme](#HasVstoObject).

### <a name="generate-host-items"></a>Konak öğeleri Oluştur
 `GetVstoObject`Belge düzeyi nesnesini (yani,, veya) genişletmek için kullandığınızda, <xref:Microsoft.Office.Interop.Excel.Workbook> <xref:Microsoft.Office.Interop.Excel.Worksheet> <xref:Microsoft.Office.Interop.Word.Document> döndürülen nesneye bir *konak öğesi* denir. Konak öğesi, diğer Genişletilmiş nesneler ve denetimler de dahil olmak üzere diğer nesneleri içerebilen bir türdür. sözcük veya Excel birincil birlikte çalışma derlemesinde karşılık gelen türe benzer, ancak ek özelliklere sahiptir. Konak öğeleri hakkında daha fazla bilgi için bkz. [konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md).

 Bir konak öğesi oluşturduktan sonra, belgeye, çalışma kitabına veya çalışma sayfasına yönetilen denetimler eklemek için onu kullanabilirsiniz. Daha fazla bilgi için bkz. [belgelere ve çalışma sayfalarına yönetilen denetimler ekleme](#AddControls).

#### <a name="to-generate-a-host-item-for-a-word-document"></a>Bir Word belgesi için bir konak öğesi oluşturmak için

- Aşağıdaki kod örneğinde, etkin belge için bir konak öğesinin nasıl oluşturulacağı gösterilmektedir.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet8":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet8":::

#### <a name="to-generate-a-host-item-for-an-excel-workbook"></a>Excel çalışma kitabı için bir konak öğesi oluşturmak için

- Aşağıdaki kod örneğinde, etkin çalışma kitabı için bir konak öğesinin nasıl oluşturulacağı gösterilmektedir.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs" id="Snippet2":::

#### <a name="to-generate-a-host-item-for-an-excel-worksheet"></a>Excel çalışma sayfasına yönelik bir konak öğesi oluşturmak için

- Aşağıdaki kod örneğinde, bir projedeki etkin çalışma sayfası için bir konak öğesinin nasıl oluşturulacağı gösterilmektedir.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs" id="Snippet1":::

### <a name="generate-listobject-host-controls"></a>ListObject konak denetimleri oluştur
 `GetVstoObject`Öğesini genişletmek için yöntemini kullandığınızda <xref:Microsoft.Office.Interop.Excel.ListObject> yöntemi bir döndürür <xref:Microsoft.Office.Tools.Excel.ListObject> . , <xref:Microsoft.Office.Tools.Excel.ListObject> Orijinalin tüm özelliklerine sahiptir <xref:Microsoft.Office.Interop.Excel.ListObject> . ayrıca, ek işlevlere sahiptir ve Windows Forms veri bağlama modeli kullanılarak verilere bağlanabilir. Daha fazla bilgi için bkz. [ListObject denetimi](../vsto/listobject-control.md).

#### <a name="to-generate-a-host-control-for-a-listobject"></a>Bir ListObject için konak denetimi oluşturmak için

- Aşağıdaki kod örneği, bir <xref:Microsoft.Office.Tools.Excel.ListObject> <xref:Microsoft.Office.Interop.Excel.ListObject> projedeki etkin çalışma sayfasında ilki için nasıl oluşturulacağını gösterir.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb" id="Snippet3":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs" id="Snippet3":::

### <a name="add-managed-controls-to-documents-and-worksheets"></a><a name="AddControls"></a> Belgelere ve çalışma sayfalarına yönetilen denetimler ekleme
 Ya da oluşturduktan sonra <xref:Microsoft.Office.Tools.Word.Document> <xref:Microsoft.Office.Tools.Excel.Worksheet> , belgeye veya çalışma sayfasına bu genişletilmiş nesnelerin temsil ettiği denetimleri ekleyebilirsiniz. Denetim eklemek için, `Controls` veya özelliğini kullanın <xref:Microsoft.Office.Tools.Word.Document> <xref:Microsoft.Office.Tools.Excel.Worksheet> . daha fazla bilgi için bkz. [çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).

 Windows Forms denetimleri veya *konak denetimleri* ekleyebilirsiniz. konak denetimi, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Word veya Excel birincil birlikte çalışma derlemesinde karşılık gelen bir denetimi sarmalayan tarafından sağlanmış bir denetimdir. ana bilgisayar denetimi, temel alınan yerel Office nesnesinin tüm davranışlarını ortaya koyar. ayrıca, olaylar oluşturur ve Windows Forms veri bağlama modeli kullanılarak verilere bağlanabilir. Daha fazla bilgi için bkz. [konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md).

> [!NOTE]
> <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> <xref:Microsoft.Office.Tools.Word.XMLNode> VSTO eklentisi kullanarak bir çalışma sayfasına veya bir belgeye bir denetim ekleyemezsiniz <xref:Microsoft.Office.Tools.Word.XMLNodes> . Bu konak denetimleri program aracılığıyla eklenemez. Daha fazla bilgi için bkz. [konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

### <a name="persist-and-remove-controls"></a>Kalıcı ve kaldırma denetimleri
 Yönetilen denetimleri bir belgeye veya çalışma sayfasına eklediğinizde, belge kaydedilip kapatıldığında denetimler kalıcı olmaz. tüm konak denetimleri, yalnızca temel alınan yerel Office nesnelerinin arkasında bırakılması için kaldırılır. Örneğin, bir <xref:Microsoft.Office.Tools.Excel.ListObject> olur <xref:Microsoft.Office.Interop.Excel.ListObject> . tüm Windows Forms denetimleri de kaldırılır, ancak denetimlerin ActiveX sarmalayıcıları belgede geride bırakılır. denetimleri temizlemek için VSTO eklentiye kod eklemeniz veya belgeyi bir dahaki sefer açıldığında denetimlerin yeniden oluşturulması gerekir. daha fazla bilgi için bkz. [Office belgelerinde dinamik denetimleri kalıcı hale](../vsto/persisting-dynamic-controls-in-office-documents.md)getirme.

## <a name="access-application-level-events-on-documents-and-workbooks"></a>Belgeler ve çalışma kitaplarında uygulama düzeyi olaylara erişme
 yerel sözcük ve Excel nesne modelleriyle bazı belge, çalışma kitabı ve çalışma sayfası olayları yalnızca uygulama düzeyinde oluşturulur. Örneğin, <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> bir belge Word 'de açıldığında olay tetiklenir, ancak bu olay sınıf <xref:Microsoft.Office.Interop.Word.Application> yerine sınıfında tanımlanır <xref:Microsoft.Office.Interop.Word.Document> .

 VSTO eklentiinizdeki yalnızca yerel Office nesneleri kullandığınızda, bu uygulama düzeyindeki olayları uygulamanız ve sonra olayı oluşturan belgenin özelleştirildiği bir belge olup olmadığını anlamak için ek kod yazmanız gerekir. Konak öğeleri, bu olayları belge düzeyinde sağlar, böylece belirli bir belge için olayları işlemek daha kolay olur. Bir konak öğesi oluşturabilir ve ardından bu konak öğesi için olayı işleyebilirsiniz.

### <a name="example-that-uses-native-word-objects"></a>Yerel Word nesneleri kullanan örnek
 Aşağıdaki kod örneği, Word belgeleri için uygulama düzeyindeki bir olayın nasıl işleneceğini gösterir. `CreateDocument`Yöntemi yeni bir belge oluşturur ve sonra <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> Bu belgenin kaydedilmesini engelleyen bir olay işleyicisini tanımlar. Olay, nesne için oluşturulan uygulama düzeyi olayıdır <xref:Microsoft.Office.Interop.Word.Application> ve olay işleyicisi, `Doc` `document1` `document1` Kaydedilen belgeyi temsil edip etmediğini tespit etmek için parametresini nesnesiyle karşılaştırmalıdır.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet12":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet12":::

### <a name="examples-that-use-a-host-item"></a>Konak öğesi kullanan örnekler
 Aşağıdaki kod örnekleri, <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> bir konak öğesinin olayını işleyerek bu işlemi basitleştirir <xref:Microsoft.Office.Tools.Word.Document> . `CreateDocument2`Bu örneklerdeki yöntemi nesnesini genişleten bir oluşturur <xref:Microsoft.Office.Tools.Word.Document> `document2` ve sonra <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> belgenin kaydedilmesini önleyen bir olay işleyicisi tanımlar. Olay işleyicisi yalnızca `document2` kaydedildiğinde çağrılır ve hangi belgenin kaydedildiğini doğrulamak için ek bir iş yapmadan Kaydet eylemini iptal edebilir.

 Aşağıdaki kod örneği bu görevi gösterir.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet13":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet13":::

## <a name="determine-whether-an-office-object-has-been-extended"></a><a name="HasVstoObject"></a>Office nesne uzatılmadığını belirleme
 bir genişletilmiş nesnenin belirli bir yerel Office nesnesi için önceden oluşturulup oluşturulmayacağını anlamak için `HasVstoObject` yöntemini kullanın. Bu yöntem, genişletilmiş bir nesne zaten oluşturulmuşsa **true** değerini döndürür.

 `Globals.Factory.HasVstoMethod` yöntemini kullanın. <xref:Microsoft.Office.Interop.Word.Document> <xref:Microsoft.Office.Interop.Excel.Worksheet> genişletilmiş bir nesne için test etmek istediğiniz bir veya gibi yerel sözcüğü veya Excel nesnesini geçirin.

 `HasVstoObject`yöntemi yalnızca belirtilen bir Office nesnesi genişletilmiş bir nesne olduğunda çalıştırmak istediğinizde yararlıdır. örneğin, <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> bir belgenin kaydedilmeden önce yönetilen denetimleri kaldırmak için olayını işleyen bir Word VSTO eklentisi varsa, `HasVstoObject` belgenin genişletilip genişletilmediğini anlamak için yöntemini kullanın. Belge genişletilmemişse, yönetilen denetimleri olamaz ve olay işleyicisi belgedeki denetimleri temizlemeye çalışmak zorunda kalmadan dönebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md)
- [çalışma zamanında Office belgelere denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)
