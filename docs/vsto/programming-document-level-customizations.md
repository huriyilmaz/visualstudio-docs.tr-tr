---
title: Program belge düzeyi özelleştirmeleri
description: Çeşitli görevleri gerçekleştirebilirsiniz Microsoft Word Excel düzeyi özelleştirme kullanarak bir belge düzeyi özelleştirmeyi veya belgeyi genişletmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- Sheet3
- thisWorkbook
- thisDocument
- Sheet1
- Sheet2
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ThisDocument class
- Sheet3 class
- ThisWorkbook class
- writing code for Office solutions
- programming [Office development in Visual Studio], document-level customizations
- Sheet1 class
- Office applications [Office development in Visual Studio], document-level customizations
- Sheet2 class
- document-level customizations [Office development in Visual Studio], programming
- application development [Office development in Visual Studio], document-level customizations
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 826a09804927d13757effdfa5b2e72c78232f3ca
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122046275"
---
# <a name="program-document-level-customizations"></a>Program belge düzeyi özelleştirmeleri
  Word'Microsoft Office veya Microsoft Office Excel düzeyi özelleştirme kullanarak genişleterek aşağıdaki görevleri gerçekleştirebilirsiniz:

- Nesne modelini kullanarak uygulamayı otomatikleştirin.

- Belgenin yüzeyine denetimler ekleyin.

- Özelleştirme Visual Basic for Applications belgesinde bir kod (VBA) çağrısı.

- VBA'dan özelleştirme derlemesinde kod çağırma.

- Belgenin belirli yönlerini, yüklü yüklü değil bir sunucudayken Microsoft Office yönetin.

- Uygulamanın kullanıcı arabirimini (UI) özelleştirin.

  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

  Belge düzeyi projelerde kod yazmanın bazı yönleri, belge düzeyindeki diğer proje Visual Studio. Bu farklılıkların çoğu, nesne modellerinin yönetilen Office ortaya çıkarılama yol açtığı için ortaya çıkar. Daha fazla bilgi için [bkz. Çözümlerde Office yazma.](../vsto/writing-code-in-office-solutions.md)

  belge düzeyi özelleştirmeler ve Visual Studio'daki Office geliştirme araçlarını kullanarak oluşturabilirsiniz diğer çözüm türleri hakkında genel bilgi için bkz. Office çözüm [geliştirmeye genel &#40;VSTO&#41;. ](../vsto/office-solutions-development-overview-vsto.md)

## <a name="use-the-generated-classes-in-document-level-projects"></a>Belge düzeyindeki projelerde oluşturulan sınıfları kullanma
 Belge düzeyi bir proje ekleyebilirsiniz Visual Studio projesinde kodunuzu yazmaya başlamak için kullanabileceğiniz bir sınıfı otomatik olarak üretir. Visual Studio Word ve Excel için farklı sınıflar Excel:

- Word için belge düzeyi projelerde sınıfı varsayılan olarak `ThisDocument` çağrılır.

- Bir çalışma kitabı için belge Excel birden çok sınıf vardır: biri çalışma kitabının kendisi için, biri de her çalışma sayfası için. Varsayılan olarak, bu sınıflar aşağıdaki adlara sahip olur:

  - `ThisWorkbook`

  - `Sheet1`

  - `Sheet2`

  - `Sheet3`

  Oluşturulan sınıf, belge açıldığında veya kapatılan olay işleyicilerini içerir. Belge açıldığında kodu çalıştırmak için olay işleyiciye `Startup` kod ekleyin. Belge kapatılana kadar kodu çalıştırmak için olay işleyiciye `Shutdown` kod ekleyin. Daha fazla bilgi için [bkz. Office projelerinde olaylar.](../vsto/events-in-office-projects.md)

### <a name="understand-the-design-of-the-generated-classes"></a>Oluşturulan sınıfların tasarımını anlama
 veya 'yi hedef alan projelerde, içinde konak öğesi türleri arabirimleridir, bu nedenle oluşturulan sınıflar kendi [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] uygulamalarını bunlardan türeyamaz. Bunun yerine, oluşturulan sınıflar üyelerinin çoğunu aşağıdaki temel sınıflardan türetir:

- `ThisDocument`: 'den <xref:Microsoft.Office.Tools.Word.DocumentBase> türeter.

- `ThisWorkbook`: 'den <xref:Microsoft.Office.Tools.Excel.WorkbookBase> türeter.

- `Sheet`*n*: 'den türetildi. <xref:Microsoft.Office.Tools.Excel.WorksheetBase>

  Bu temel sınıflar, üyelerine yapılan tüm çağrıları içinde karşılık gelen konak öğesi arabirimlerinin iç uygulamalarına yeniden [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] yönlendirmektedir. Örneğin, sınıfının yöntemini çağırsanız, sınıfı bu çağrıyı içinde <xref:Microsoft.Office.Tools.Word.DocumentBase.Protect%2A> `ThisDocument` <xref:Microsoft.Office.Tools.Word.DocumentBase> arabiriminin iç <xref:Microsoft.Office.Tools.Word.Document> uygulamasına yeniden yönlendirer. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]

## <a name="access-the-object-model-of-the-host-application"></a>Konak uygulamanın nesne modeline erişme
 Konak uygulamanın nesne modeline erişmek için projeniz içinde oluşturulan sınıfın üyelerini kullanın. Bu sınıfların her biri, Excel veya Word'Excel nesne modeline karşılık gelen ve aynı özelliklerin, yöntemlerin ve olayların çoğunu içerir. Örneğin, Word için belge düzeyi projesinde sınıfı, Word nesne modelinde nesnesiyle `ThisDocument` <xref:Microsoft.Office.Interop.Word.Document> aynı üyelerin çoğunu sağlar.

 Aşağıdaki kod örneği, Word için belge düzeyi özelleştirmenin bir parçası olan belgeyi kaydetmek üzere Word nesne modelinin nasıl kullanılagelmektedir. Bu örneğin sınıfından çalışması `ThisDocument` amaçlanan bir örnektir.

```vb
Me.Save()
```

```csharp
this.Save();
```

 Aynı şeyi sınıfı dışından yapmak `ThisDocument` için, `Globals` sınıfına erişmek için nesnesini `ThisDocument` kullanın. Örneğin, eylemler bölmesi kullanıcı arabirimine bir Kaydet düğmesi eklemek için bu kodu bir eylemler **bölmesi** kod dosyasına ekleyebilirsiniz.

```vb
Globals.ThisDocument.Save()
```

```csharp
Globals.ThisDocument.Save();
```

 sınıfı, üyelerinin çoğunu konak öğesinden edindir, bu kodda çağrılır yöntemi `ThisDocument` <xref:Microsoft.Office.Tools.Word.Document> gerçekten konak `Save` <xref:Microsoft.Office.Tools.Word.Document.Save%2A> öğesinin <xref:Microsoft.Office.Tools.Word.Document> yöntemidir. Bu <xref:Microsoft.Office.Interop.Word._Document.Save%2A> yöntem, Word nesne modelinde <xref:Microsoft.Office.Interop.Word.Document> nesnesinin yöntemine karşılık gelen.

 Word ve Excel nesne modellerini kullanma hakkında daha fazla bilgi için bkz. [Word](../vsto/word-object-model-overview.md) nesne modeline genel bakış [ve Excel modeline genel bakış.](../vsto/excel-object-model-overview.md)

 nesnesi hakkında daha fazla `Globals` bilgi için [bkz. Projelerde nesnelere Office.](../vsto/global-access-to-objects-in-office-projects.md)

## <a name="add-controls-to-documents"></a>Belgelere denetim ekleme
 Belgenin kullanıcı arabirimini özelleştirmek için, belge yüzeyine Windows Form denetimleri *veya konak denetimleri* ekleyebilirsiniz. Farklı denetim kümelerini birleştirerek ve kod yazarak, denetimleri verilere bağlayabilirsiniz, kullanıcıdan bilgi toplayabilirsiniz ve kullanıcı eylemlerini yanıtlayabilirsiniz.

 Konak denetimleri, Word'de bazı nesneleri genişleten ve nesne modelini Excel sınıflardır. Örneğin, konak denetimi içinde tüm <xref:Microsoft.Office.Tools.Excel.ListObject> işlevlerini sağlar <xref:Microsoft.Office.Interop.Excel.ListObject> Excel. Ancak konak <xref:Microsoft.Office.Tools.Excel.ListObject> denetiminde ek olaylar ve veri bağlama özellikleri de vardır.

 Daha fazla bilgi için [bkz. Konak öğelerine ve konak denetimlerine genel](../vsto/host-items-and-host-controls-overview.md) [bakış Windows belgelerine genel Office form denetimleri.](../vsto/windows-forms-controls-on-office-documents-overview.md)

## <a name="combine-vba-and-document-level-customizations"></a>VBA ve belge düzeyi özelleştirmelerini birleştirme
 VBA kodunu belge düzeyinde özelleştirmenin parçası olan bir belgede kullanabilirsiniz. Belgede VBA kodunu özelleştirme derlemesinde çağırabilir ve ayrıca projenizi, belgede VBA kodunu özelleştirme derlemesinde kod çağırarak etkinleştirecek şekilde yapılandırabilirsiniz.

 Daha fazla bilgi için [bkz. VBA ve belge düzeyinde özelleştirmeleri birleştirme.](../vsto/combining-vba-and-document-level-customizations.md)

## <a name="manage-documents-on-a-server"></a>Sunucu üzerinde belgeleri yönetme
 Word veya Microsoft Office yüklü olmayan bir sunucuda belge düzeyi özelleştirmelerin Microsoft Office Microsoft Office Excel yönetebilirsiniz. Örneğin, belgenin veri önbelleğinde verilere erişebilirsiniz ve verileri değiştirebilirsiniz. Belgeyle ilişkili özelleştirme derlemelerini de yönetebilirsiniz. Örneğin, belgenin artık kodunuzu çalıştırması için derlemeyi belgeden program aracılığıyla kaldırabilir veya bir derlemeyi bir belgeye program aracılığıyla ekleyebilirsiniz.

 Daha fazla bilgi için [bkz. ServerDocument sınıfını kullanarak bir sunucu üzerinde belgeleri yönetme.](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)

## <a name="customize-the-user-interface-of-microsoft-office-applications"></a>Uygulama uygulamalarının kullanıcı Microsoft Office özelleştirme
 Belge düzeyinde özelleştirme kullanarak Word kullanıcı arabirimini Excel kullanıcı arabirimini aşağıdaki yollarla özelleştirebilirsiniz:

- Belge yüzeyine konak denetimleri Windows form denetimleri ekleyin.

   Daha fazla bilgi için bkz. Genişletilmiş [](../vsto/automating-excel-by-using-extended-objects.md)nesneleri kullanarak [Word'Excel](../vsto/automating-word-by-using-extended-objects.md)otomatikleştirme, genişletilmiş nesneleri kullanarak Windows formlarını otomatikleştirme ve [Office belgelerine genel bakış.](../vsto/windows-forms-controls-on-office-documents-overview.md)

- Belgeye bir eylemler bölmesi ekleyin.

   Daha fazla bilgi için bkz. [Eylemler bölmesine genel bakış.](../vsto/actions-pane-overview.md)

- Şerite özel sekmeler ekleyin.

   Daha fazla bilgi için bkz. [Şerit'e genel bakış.](../vsto/ribbon-overview.md)

- Şeritteki yerleşik bir sekmeye özel gruplar ekleyin.

   Daha fazla bilgi için [bkz. Nasıl yapılacaklar: Yerleşik sekmeyi özelleştirme.](../vsto/how-to-customize-a-built-in-tab.md)

  Uygulama kullanıcı arabirimini özelleştirme hakkında daha fazla bilgi Microsoft Office [bkz. Office kullanıcı arabirimi özelleştirmesi.](../vsto/office-ui-customization.md)

## <a name="get-extended-objects-from-native-office-objects-in-document-level-customizations"></a>Belge düzeyinde özelleştirmelerde yerel Office nesnelerinin genişletilmiş nesnelerini al
 Olay oluşturma olaylarını Office olay işleyicileri, olayı Office çalışma kitabını, çalışma sayfasını veya belgeyi temsil eden yerel bir nesne alır. Bazı durumlarda, yalnızca belge düzeyinde özelleştirmesi yapılan çalışma kitabı veya belge olayı başlattıysa bazı kodlar çalıştırmak istiyor olabilir. Örneğin, Excel için belge düzeyinde bir özelleştirmede, kullanıcı özelleştirilmiş çalışma kitabındaki çalışma sayfalarından birini etkinleştirse de, kullanıcı aynı anda açık olan başka bir çalışma kitabında çalışma sayfasını etkinleştirse bile bazı kodlar çalıştırmak istemeyebilirsiniz.

 Yerel bir Office nesneniz olduğunda, bu nesnenin belge düzeyi özelleştirmede  bir konak  öğesi veya konak denetimine genişletildi olup olmadığını test edersiniz. Konak öğeleri ve konak denetimleri, Word veya Excel nesne modellerinde yerel olarak var olan nesnelere [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] işlev Office tarafından sağlanan *türlerdir.* Toplu olarak, konak öğeleri ve konak denetimleri genişletilmiş nesneler *olarak da çağrılır.* Konak öğeleri ve konak denetimleri hakkında daha fazla bilgi için bkz. [Konak öğeleri ve konak denetimlerine genel bakış.](../vsto/host-items-and-host-controls-overview.md)

## <a name="understand-the-getvstoobject-and-hasvstoobject-methods"></a>GetVstoObject ve HasVstoObject yöntemlerini anlama
 Yerel bir Office test etmek için projenizin `HasVstoObject` ve `GetVstoObject` yöntemlerini kullanın:

- Yerel uygulama nesnesinin özelleştirmede genişletilmiş bir Office olup olmadığını `HasVstoObject` belirlemek için yöntemini kullanın. Bu yöntem, **yerel** nesnesinde genişletilmiş Office varsa true, aksi takdirde **false** döndürür.

- Yerel bir Office nesnesi için genişletilmiş `GetVstoObject` nesneyi almak Office kullanın. Bu yöntem, belirtilen yerel nesnede varsa , , <xref:Microsoft.Office.Tools.Excel.ListObject> <xref:Microsoft.Office.Tools.Excel.Workbook> Office nesnesi <xref:Microsoft.Office.Tools.Excel.Worksheet> <xref:Microsoft.Office.Tools.Word.Document> döndürür. Aksi takdirde, `GetVstoObject` **null döndürür.** Örneğin yöntemi, belirtilen word belge projenizin belge için temel alınan nesne `GetVstoObject` ise bir <xref:Microsoft.Office.Tools.Word.Document> <xref:Microsoft.Office.Interop.Word.Document> döndürür.

  Belge düzeyindeki projelerde, çalışma zamanında yeni bir , veya konak `GetVstoObject` öğesi oluşturmak için yöntemini <xref:Microsoft.Office.Tools.Excel.Workbook> <xref:Microsoft.Office.Tools.Excel.Worksheet> <xref:Microsoft.Office.Tools.Word.Document> kullanılamaz. Bu yöntemi yalnızca tasarım zamanında projeniz içinde oluşturulan mevcut konak öğelerine erişmek için kullanabilirsiniz. Çalışma zamanında yeni konak öğeleri oluşturmak için, yeni bir eklenti VSTO geliştirmeniz gerekir. Daha fazla bilgi için [bkz. Konak](../vsto/programmatic-limitations-of-host-items-and-host-controls.md) öğelerinin ve konak denetimlerinin programlı sınırlamaları ve Çalışma zamanında Excel'VSTO çalışma kitaplarını [genişletme.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

## <a name="use-the-getvstoobject-and-hasvstoobject-methods"></a>GetVstoObject ve HasVstoObject yöntemlerini kullanma
 ve yöntemini çağırarak veya yöntemini kullanın ve test etmek istediğiniz yerel Word veya Excel nesnesini `HasVstoObject` `GetVstoObject` `Globals.Factory.GetVstoObject` `Globals.Factory.HasVstoObject` (veya <xref:Microsoft.Office.Interop.Word.Document> <xref:Microsoft.Office.Interop.Excel.Worksheet> gibi) iletir.

## <a name="see-also"></a>Ayrıca bkz.
- [Belgelerde Office denetimler](../vsto/controls-on-office-documents.md)
- [VBA ve belge düzeyi özelleştirmelerini birleştirme](../vsto/combining-vba-and-document-level-customizations.md)
- [ServerDocument sınıfını kullanarak bir sunucu üzerinde belgeleri yönetme](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Kod yazma Office yazma](../vsto/writing-code-in-office-solutions.md)
