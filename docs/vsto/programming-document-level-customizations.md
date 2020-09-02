---
title: Program belge düzeyi özelleştirmeleri
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7d1908f72bce01956bbb2eeb62bb9bbc30a64b0d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71254028"
---
# <a name="program-document-level-customizations"></a>Program belge düzeyi özelleştirmeleri
  Belge düzeyi özelleştirmesi kullanarak Microsoft Office Word veya Excel Microsoft Office genişlettiğinizde, aşağıdaki görevleri gerçekleştirebilirsiniz:

- Nesne modelini kullanarak uygulamayı otomatikleştirin.

- Belge yüzeyine denetimler ekleyin.

- Özelleştirme derlemesinden belgedeki Visual Basic for Applications (VBA) kodunu çağırın.

- VBA 'dan özelleştirme derlemesinde kodu çağırın.

- Microsoft Office yüklü olmayan bir sunucuda olduğu sırada belgenin belirli yönlerini yönetin.

- Uygulamanın kullanıcı arabirimini (UI) özelleştirin.

  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

  Belge düzeyi projelerde kod yazmanın bazı yönleri, Visual Studio 'daki diğer proje türlerinden farklıdır. Bu farklılıkların birçoğu, Office nesne modellerinin yönetilen koda sunulma yoludur. Daha fazla bilgi için bkz. [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md).

  Belge düzeyi özelleştirmeleri ve Visual Studio 'da Office geliştirme araçları 'nı kullanarak oluşturabileceğiniz diğer çözüm türleri hakkında genel bilgi için bkz. [Office çözümleri geliştirmeye genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

## <a name="use-the-generated-classes-in-document-level-projects"></a>Belge düzeyi projelerde oluşturulan sınıfları kullanma
 Belge düzeyi projesi oluşturduğunuzda, Visual Studio projede kodunuzu yazmaya başlamak için kullanabileceğiniz bir sınıfı otomatik olarak oluşturur. Visual Studio Word ve Excel için farklı sınıflar oluşturur:

- Word için belge düzeyi projelerinde, sınıfı `ThisDocument` Varsayılan olarak çağrılır.

- Excel için belge düzeyi projeleri birden çok oluşturulmuş sınıfa sahiptir: biri çalışma kitabının kendisi için, diğeri her çalışma sayfası için. Varsayılan olarak, bu sınıflar aşağıdaki adlara sahiptir:

  - `ThisWorkbook`

  - `Sheet1`

  - `Sheet2`

  - `Sheet3`

  Oluşturulan sınıf, belge açıldığında veya kapandığında çağrılan olay işleyicilerini içerir. Belge açıldığında kodu çalıştırmak için `Startup` olay işleyicisine kod ekleyin. Belge kapatılmadan hemen önce kodu çalıştırmak için, `Shutdown` olay işleyicisine kod ekleyin. Daha fazla bilgi için bkz. [Office Projelerindeki Olaylar](../vsto/events-in-office-projects.md).

### <a name="understand-the-design-of-the-generated-classes"></a>Oluşturulan sınıfların tasarımını anlama
 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]Veya ' i hedefleyen projelerde, [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] içindeki konak öğesi türleri [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] arayüzlerdir, bu nedenle oluşturulan sınıflar bunlardan uygulanmasını türetemez. Bunun yerine, oluşturulan sınıflar üyelerinin çoğunu aşağıdaki temel sınıflardan türetir:

- `ThisDocument`: türetiliyor <xref:Microsoft.Office.Tools.Word.DocumentBase> .

- `ThisWorkbook`: türetiliyor <xref:Microsoft.Office.Tools.Excel.WorkbookBase> .

- `Sheet`*n*: öğesinden türetilir <xref:Microsoft.Office.Tools.Excel.WorksheetBase> .

  Bu temel sınıflar, üyelerine tüm çağrıları, içindeki karşılık gelen konak öğesi arabirimlerinin iç uygulamalarına yönlendirir [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Örneğin, <xref:Microsoft.Office.Tools.Word.DocumentBase.Protect%2A> sınıfının yöntemini çağırırsanız `ThisDocument` , <xref:Microsoft.Office.Tools.Word.DocumentBase> sınıfı bu çağrıyı içindeki arabirimin iç uygulamasına yönlendirir <xref:Microsoft.Office.Tools.Word.Document> [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

## <a name="access-the-object-model-of-the-host-application"></a>Ana bilgisayar uygulamasının nesne modeline erişin
 Konak uygulamasının nesne modeline erişmek için, projenizde oluşturulan sınıfın üyelerini kullanın. Bu sınıfların her biri Excel veya Word nesne modelindeki bir nesneye karşılık gelir ve aynı özelliklerin, yöntemlerin ve olayların çoğunu içerir. Örneğin, `ThisDocument` Word için belge düzeyi projesindeki sınıf, <xref:Microsoft.Office.Interop.Word.Document> Word nesne modelindeki nesne ile aynı üyelerin çoğunu sağlar.

 Aşağıdaki kod örneği, Word için belge düzeyi özelleştirmenin parçası olan belgeyi kaydetmek için Word nesne modelinin nasıl kullanılacağını gösterir. Bu örnek sınıfından çalıştırılmak üzere tasarlanmıştır `ThisDocument` .

```vb
Me.Save()
```

```csharp
this.Save();
```

 Sınıfın dışından aynı şeyi yapmak için, `ThisDocument` `Globals` sınıfına erişmek için nesnesini kullanın `ThisDocument` . Örneğin, Eylemler bölmesi Kullanıcı arabirimine bir **Kaydet** düğmesi eklemek istiyorsanız, bu kodu bir eylemler bölmesi kod dosyasına ekleyebilirsiniz.

```vb
Globals.ThisDocument.Save()
```

```csharp
Globals.ThisDocument.Save();
```

 Sınıf, `ThisDocument` üyelerinin çoğunu konak öğesinden edindiği için <xref:Microsoft.Office.Tools.Word.Document> , `Save` Bu kodda çağrılan yöntem aslında <xref:Microsoft.Office.Tools.Word.Document.Save%2A> <xref:Microsoft.Office.Tools.Word.Document> ana öğe öğesinin yöntemidir. Bu yöntem, <xref:Microsoft.Office.Interop.Word._Document.Save%2A> <xref:Microsoft.Office.Interop.Word.Document> Word nesne modelindeki nesnesinin yöntemine karşılık gelir.

 Word ve Excel 'in nesne modellerini kullanma hakkında daha fazla bilgi için bkz. [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md) ve [Excel nesne modeline genel bakış](../vsto/excel-object-model-overview.md).

 Nesnesi hakkında daha fazla bilgi için `Globals` bkz. [Office Projelerindeki Nesnelere Genel erişim](../vsto/global-access-to-objects-in-office-projects.md).

## <a name="add-controls-to-documents"></a>Belgelere denetim ekleme
 Belgenin Kullanıcı arabirimini özelleştirmek için belge yüzeyine Windows Forms denetimleri veya *konak denetimleri* ekleyebilirsiniz. Farklı denetim kümelerini birleştirerek ve kod yazarken, denetimleri verilere bağlayabilir, kullanıcıdan bilgi toplayabilir ve kullanıcı eylemlerine yanıt verebilirsiniz.

 Konak denetimleri, Word ve Excel nesne modelindeki bazı nesneleri genişleten sınıflardır. Örneğin, <xref:Microsoft.Office.Tools.Excel.ListObject> konak denetimi Excel 'deki tüm işlevlerini sağlar <xref:Microsoft.Office.Interop.Excel.ListObject> . Ancak, <xref:Microsoft.Office.Tools.Excel.ListObject> konak denetiminde ek olaylar ve veri bağlama özellikleri de bulunur.

 Daha fazla bilgi için bkz. [konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md) ve [Office belgelerindeki Windows Forms denetimlerine genel bakış](../vsto/windows-forms-controls-on-office-documents-overview.md).

## <a name="combine-vba-and-document-level-customizations"></a>VBA ve belge düzeyi özelleştirmelerini birleştirme
 Belge düzeyinde özelleştirmenin parçası olan bir belgede VBA kodunu kullanabilirsiniz. Belgedeki VBA kodunu özelleştirme derlemesinden çağırabilirsiniz ve ayrıca projenizi özelleştirme derlemesindeki kodu çağırmak için belgede VBA kodunu etkinleştirecek şekilde yapılandırabilirsiniz.

 Daha fazla bilgi için bkz. [VBA ve belge düzeyi özelleştirmelerini birleştirme](../vsto/combining-vba-and-document-level-customizations.md).

## <a name="manage-documents-on-a-server"></a>Bir sunucudaki belgeleri yönetme
 Belge düzeyi özelleştirmelerinin birçok farklı yönlerini, Microsoft Office Word veya Microsoft Office Excel yüklü olmayan bir sunucuda yönetebilirsiniz. Örneğin, belgenin veri önbelleğindeki verilere erişebilir ve verileri değiştirebilirsiniz. Ayrıca, belgeyle ilişkili özelleştirme derlemesini de yönetebilirsiniz. Örneğin, belgenin kodunuzu çalıştırmaması için derlemeyi belgeden program aracılığıyla kaldırabilir veya bir belgeye program aracılığıyla bir derlemeyi ekleyebilirsiniz.

 Daha fazla bilgi için, bkz. [ServerDocument sınıfını kullanarak bir sunucudaki belgeleri yönetme](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).

## <a name="customize-the-user-interface-of-microsoft-office-applications"></a>Microsoft Office uygulamalarının Kullanıcı arabirimini özelleştirme
 Belge düzeyi özelleştirmesi kullanarak Word ve Excel 'in Kullanıcı arabirimini aşağıdaki yollarla özelleştirebilirsiniz:

- Belge yüzeyine konak denetimleri veya Windows Forms denetimleri ekleyin.

   Daha fazla bilgi için bkz. [genişletilmiş nesneleri kullanarak Word 'Ü otomatikleştirme](../vsto/automating-word-by-using-extended-objects.md), [genişletilmiş nesneleri kullanarak Excel 'ı otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md)ve [Office belgelerindeki Windows Forms denetimleri genel bakış](../vsto/windows-forms-controls-on-office-documents-overview.md).

- Belgeye bir eylemler bölmesi ekleyin.

   Daha fazla bilgi için bkz. [eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md).

- Şerite özel sekmeler ekleyin.

   Daha fazla bilgi için bkz. [Şerit 'e genel bakış](../vsto/ribbon-overview.md).

- Şeritteki yerleşik bir sekmeye özel gruplar ekleyin.

   Daha fazla bilgi için bkz. [nasıl yapılır: yerleşik bir sekmeyi özelleştirme](../vsto/how-to-customize-a-built-in-tab.md).

  Microsoft Office uygulamalarının Kullanıcı arabirimini özelleştirme hakkında daha fazla bilgi için bkz. [OFFICE UI özelleştirmesi](../vsto/office-ui-customization.md).

## <a name="get-extended-objects-from-native-office-objects-in-document-level-customizations"></a>Belge düzeyi özelleştirmelerde yerel Office nesnelerinden genişletilmiş nesneleri Al
 Office olayları için pek çok olay işleyicisi, olayı oluşturan çalışma kitabını, çalışma sayfasını veya belgeyi temsil eden yerel bir Office nesnesi alır. Bazı durumlarda, yalnızca belge düzeyi özelleştirmesindeki çalışma kitabı veya belge olayı harekete çıktığında bazı kodları çalıştırmak isteyebilirsiniz. Örneğin, Excel için belge düzeyi özelleştirmesinde, Kullanıcı özelleştirilmiş çalışma kitabındaki çalışma sayfalarından birini etkinleştirdiğinde, ancak kullanıcı aynı anda açık olan başka bir çalışma kitabındaki çalışma sayfasını etkinleştirdiğinde, bazı kodları çalıştırmak isteyebilirsiniz.

 Yerel bir Office nesneniz varsa, bu nesnenin bir belge düzeyi özelleştirmesinde *konak öğesine* veya *konak denetimine* genişletilmiş olup olmadığını test edebilirsiniz. Konak öğeleri ve konak denetimleri, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Word veya Excel nesne modelleriyle ( *yerel Office nesneleri*olarak adlandırılır) yerel olarak var olan nesnelere işlev ekleyen, tarafından sunulan türlerdir. Toplu olarak, ana bilgisayar öğelerine ve konak denetimlerine de *Genişletilmiş nesneler*denir. Konak öğeleri ve konak denetimleri hakkında daha fazla bilgi için bkz. [konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md).

## <a name="understand-the-getvstoobject-and-hasvstoobject-methods"></a>GetVstoObject ve HasVstoObject yöntemlerini anlayın
 Yerel bir Office nesnesini test etmek için, `HasVstoObject` projenizdeki ve `GetVstoObject` yöntemlerini kullanın:

- `HasVstoObject`Yerel Office nesnesinin özelleştirmenizin genişletilmiş bir nesne içerip içermediğini anlamak istiyorsanız yöntemini kullanın. Bu yöntem, yerel Office nesnesi genişletilmiş bir nesne içeriyorsa **true** , aksi durumda **false** değerini döndürür.

- `GetVstoObject`Yerel bir Office nesnesi için genişletilmiş nesneyi almak istiyorsanız yöntemini kullanın. Bu yöntem, <xref:Microsoft.Office.Tools.Excel.ListObject> <xref:Microsoft.Office.Tools.Excel.Workbook> <xref:Microsoft.Office.Tools.Excel.Worksheet> <xref:Microsoft.Office.Tools.Word.Document> belirtilen yerel Office nesnesinde bir,, veya nesnesi döndürür. Aksi takdirde `GetVstoObject` , **null**döndürür. Örneğin, `GetVstoObject` <xref:Microsoft.Office.Tools.Word.Document> <xref:Microsoft.Office.Interop.Word.Document> nesne Word belge projenizde belge için temeldeki nesnese, yöntemi döndürür.

  Belge düzeyi projelerinde, `GetVstoObject` <xref:Microsoft.Office.Tools.Excel.Workbook> <xref:Microsoft.Office.Tools.Excel.Worksheet> çalışma zamanında yeni, veya konak öğesi oluşturmak için yöntemini kullanamazsınız <xref:Microsoft.Office.Tools.Word.Document> . Bu yöntemi yalnızca, tasarım zamanında projenizde oluşturulan mevcut konak öğelerine erişmek için kullanabilirsiniz. Çalışma zamanında yeni konak öğeleri oluşturmak istiyorsanız, bir VSTO eklentisi projesi geliştirmeniz gerekir. Daha fazla bilgi için bkz. [konak öğeleri ve konak denetimleri Için programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md) ve [çalışma zamanında VSTO Eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="use-the-getvstoobject-and-hasvstoobject-methods"></a>GetVstoObject ve HasVstoObject yöntemlerini kullanma
 Ve yöntemini çağırmak için, `HasVstoObject` `GetVstoObject` `Globals.Factory.GetVstoObject` veya `Globals.Factory.HasVstoObject` yöntemini kullanın ve <xref:Microsoft.Office.Interop.Word.Document> test etmek Istediğiniz yerel sözcüğü ya da Excel nesnesini (veya gibi <xref:Microsoft.Office.Interop.Excel.Worksheet> ) geçirin.

## <a name="see-also"></a>Ayrıca bkz.
- [Office belgelerindeki denetimler](../vsto/controls-on-office-documents.md)
- [VBA ve belge düzeyi özelleştirmelerini birleştirme](../vsto/combining-vba-and-document-level-customizations.md)
- [ServerDocument sınıfını kullanarak bir sunucudaki belgeleri yönetme](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md)
