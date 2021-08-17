---
title: Program VSTO Eklentileri
description: Bu ana bilgisayar uygulamasının nesne modeline erişme gibi görevleri gerçekleştirmek için ThisAddIn sınıfını Microsoft Office öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.Addin
- VST.ProjectItem.AddinProject
- thisAddIn
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ICustomTaskPaneConsumer interface
- add-ins [Office development in Visual Studio], programming
- IRibbonExtensibility interface
- UI customizing [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], application-level add-ins
- programming [Office development in Visual Studio], application-level add-ins
- ThisAddIn class
- user interfaces [Office development in Visual Studio], customizing
- writing code for Office solutions
- host items [Office development in Visual Studio], AddIn
- application development [Office development in Visual Studio], application-level add-ins
- add-ins [Office development in Visual Studio], ThisAddIn class
- application-level add-ins [Office development in Visual Studio], ThisAddIn class
- FormRegionStartup interface
- ThisAddIn_Startup
- application-level add-ins [Office development in Visual Studio], programming
- ThisAddIn_Shutdown
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 7afd9532affc9a4d22c602a65faf7adc225dd41f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122025920"
---
# <a name="program-vsto-add-ins"></a>Program VSTO Eklentileri
  Bir uygulamanın Microsoft Office eklentisini oluşturarak VSTO doğrudan projenizin sınıfına `ThisAddIn` karşı kod yazarsiniz. Microsoft Office konak uygulamasının nesne modeline erişme, uygulamanın kullanıcı arabirimini (UI) özelleştirme ve VSTO Eklentisinde nesneleri diğer Office çözümlerine gösterme gibi görevleri gerçekleştirmek için bu sınıfı kullanabilirsiniz.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

 Eklenti projelerinde kod yazmanın VSTO yönleri, diğer proje türlerinden Visual Studio. Bu farklılıkların çoğu, nesne modellerinin yönetilen Office ortaya çıkarılama yol açtığı için ortaya çıkar. Daha fazla bilgi için [bkz. Çözümlerde Office yazma.](../vsto/writing-code-in-office-solutions.md)

 Visual Studio'daki Office geliştirme araçlarını kullanarak oluşturabilirsiniz VSTO Eklentileri ve diğer çözüm türleri hakkında genel bilgi için bkz. Office çözüm geliştirmeye [genel &#40;VSTO&#41;. ](../vsto/office-solutions-development-overview-vsto.md)

## <a name="use-the-thisaddin-class"></a>ThisAddIn sınıfını kullanma
 Sınıf içinde VSTO eklenti kodunuzu yazmaya `ThisAddIn` başlayabilirsiniz. Visual Studio bu sınıfı, VSTO Add-in projenizin *ThisAddIn.vb* [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] (içinde) veya *ThisAddIn.cs* (C#) kod dosyasında otomatik olarak VSTO olarak üretir. uygulama, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] uygulama eklentinizi yüklerken sizin Microsoft Office için bu VSTO örneğini sağlar.

 sınıfında iki varsayılan olay `ThisAddIn` işleyicisi vardır. Eklentinin yük VSTO kodu çalıştırmak için olay işleyiciye `ThisAddIn_Startup` kod ekleyin. Eklentinin yüklenmeden hemen VSTO çalıştırmak için olay işleyiciye `ThisAddIn_Shutdown` kod ekleyin. Bu olay işleyicileri hakkında daha fazla bilgi için [bkz. Office projelerinde olaylar.](../vsto/events-in-office-projects.md)

> [!NOTE]
> Bu Outlook, varsayılan olarak olay `ThisAddIn_Shutdown` işleyicisi, VSTO kaldırılmış olduğunda çağrılmaz. Daha fazla bilgi için [bkz. Office projelerinde olaylar.](../vsto/events-in-office-projects.md)

### <a name="access-the-object-model-of-the-host-application"></a>Konak uygulamanın nesne modeline erişme
 Konak uygulamanın nesne modeline erişmek için `Application` sınıfının alanını `ThisAddIn` kullanın. Bu alan, konak uygulamanın geçerli örneğini temsil eden bir nesne döndürür. Aşağıdaki tabloda, eklenti projesinde yer alan her bir `Application` alan için VSTO türü listele.

|Konak uygulaması|Dönüş değeri türü|
|----------------------|-----------------------|
|Microsoft Office Excel|<xref:Microsoft.Office.Interop.Excel.Application>|
|Microsoft Office ınfopath|<xref:Microsoft.Office.Interop.InfoPath.Application>|
|Microsoft Office Outlook|<xref:Microsoft.Office.Interop.Outlook.Application>|
|Microsoft Office PowerPoint|[Uygulama](/previous-versions/office/developer/office-2010/ff764034(v=office.14))|
|Microsoft Office Project|Microsoft. Office. Interop.MSProject.Application|
|Microsoft Office Visio|Microsoft. Office. Birlikte çalış -abilir -lik. Visio. Uygulama|
|Microsoft Office Kelime|<xref:Microsoft.Office.Interop.Word.Application>|

 Aşağıdaki kod örneğinde, yeni bir çalışma kitabı oluşturmak için alanı nasıl kullanabileceğiniz ve VSTO `Application` için Microsoft Office Excel. Bu örneğin sınıfından çalışması `ThisAddIn` amaçlanan bir örnektir.

```vb
Dim newWorkbook As Excel.Workbook = Me.Application.Workbooks.Add()
```

```csharp
Excel.Workbook newWorkbook = this.Application.Workbooks.Add(System.Type.Missing);
```

 Aynı şeyi sınıfı dışından yapmak `ThisAddIn` için, `Globals` sınıfına erişmek için nesnesini `ThisAddIn` kullanın. nesnesi hakkında daha fazla `Globals` bilgi için [bkz. Projelerde nesnelere Office.](../vsto/global-access-to-objects-in-office-projects.md)

```vb
Dim newWorkbook As Excel.Workbook = Globals.ThisAddIn.Application.Workbooks.Add()
```

```csharp
Excel.Workbook newWorkbook = Globals.ThisAddIn.Application.Workbooks.Add(System.Type.Missing);
```

 Belirli bir uygulamanın nesne modelleri hakkında daha fazla Microsoft Office için aşağıdaki konulara bakın:

- [Excel modeline genel bakış](../vsto/excel-object-model-overview.md)

- [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md)

- [Outlook modeline genel bakış](../vsto/outlook-object-model-overview.md)

- [InfoPath çözümleri](../vsto/infopath-solutions.md)

- [PowerPoint çözümleri](../vsto/powerpoint-solutions.md)

- [Project çözümleri](../vsto/project-solutions.md)

- [Visio modeline genel bakış](../vsto/visio-object-model-overview.md)

### <a name="access-a-document-when-the-office-application-starts"></a><a name="AccessingDocuments"></a>Uygulama başlatıldığında Office erişme
 Tüm uygulamalar, siz bunları başlatan bir belgeyi otomatik olarak açmaz ve [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] uygulamaları ilk başlatan uygulamaların hiçbiri bir belgeyi açmaz. Bu nedenle, kod bir belgenin açık olması gerektiriyorsa olay `ThisAdd-In_Startup` işleyiciye kod ekleme. Bunun yerine, kullanıcı belge oluşturduğunda veya açtığında Office uygulamanın oluşturduğu bir olayına bu kodu ekleyin. Bu şekilde, kodunuz üzerinde işlem gerçekleştirmeden önce belgenin açık olduğunu garanti ekleyebilirsiniz.

 Aşağıdaki kod örneği yalnızca kullanıcı bir belge oluşturduğunda veya mevcut bir belgeyi açtığında Word'de bir belgeyle çalışır.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs" id="Snippet3":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb" id="Snippet3":::

### <a name="thisaddin-members-to-use-for-other-tasks"></a>Diğer görevler için kullanmak üzere ThisAddIn üyeleri
 Aşağıdaki tabloda diğer ortak görevler açıklanmış ve görevleri gerçekleştirmek için `ThisAddIn` kullanabileceğiniz sınıf üyeleri açıklanmış olur.

|Görev|Kullanmak için üye|
|----------|-------------------|
|Eklentinin yük VSTO eklentiyi başlatmak VSTO kodu çalıştırın.|yöntemine kod `ThisAddIn_Startup` ekleyin. Bu, olay için varsayılan olay <xref:Microsoft.Office.Tools.AddInBase.Startup> işleyicidir. Daha fazla bilgi için [bkz. Office projelerinde olaylar.](../vsto/events-in-office-projects.md)|
|Eklentinin yüklenmeden önce VSTO tarafından kullanılan kaynakları temizlemek VSTO çalıştırın.|yöntemine kod `ThisAddIn_Shutdown` ekleyin. Bu, olay için varsayılan olay <xref:Microsoft.Office.Tools.AddInBase.Shutdown> işleyicidir. Daha fazla bilgi için [bkz. Office projelerinde olaylar.](../vsto/events-in-office-projects.md) **Not:**  Bu Outlook, varsayılan olarak olay `ThisAddIn_Shutdown` işleyicisi, VSTO kaldırılmış olduğunda çağrılmaz. Daha fazla bilgi için [bkz. Office projelerinde olaylar.](../vsto/events-in-office-projects.md)|
|Özel görev bölmesi görüntüleme.|alanını `CustomTaskPanes` kullanın. Daha fazla bilgi için [bkz. Özel görev bölmeleri.](../vsto/custom-task-panes.md)|
|Uygulama eklentinizin nesnelerini VSTO diğer çözümlerde Microsoft Office.|yöntemini geçersiz <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> kılın. Daha fazla bilgi için [bkz. Diğer VSTO çözümlerinden eklentilerde kod Office.](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)|
|Genişletilebilirlik arabirimini Microsoft Office sistemde bir özelliği özelleştirin.|Arabirimi <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> uygulayan bir sınıfın örneğini dönmek için yöntemini geçersiz kılın. Daha fazla bilgi için [bkz. Genişletilebilirlik arabirimlerini kullanarak kullanıcı arabirimi özelliklerini özelleştirme.](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md) **Not:**  Şerit kullanıcı arabirimini özelleştirmek için yöntemini de geçersiz <xref:Microsoft.Office.Tools.AddInBase.CreateRibbonExtensibilityObject%2A> kılebilirsiniz.|

### <a name="understand-the-design-of-the-thisaddin-class"></a>ThisAddIn sınıfının tasarımını anlama
 'i hedef alan [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] <xref:Microsoft.Office.Tools.AddIn> projelerde bir arabirimdir. `ThisAddIn`sınıfı sınıfından <xref:Microsoft.Office.Tools.AddInBase> türetildi. Bu temel sınıf, tüm çağrılarını üyelerine içinde arabiriminin iç <xref:Microsoft.Office.Tools.AddIn> uygulamasına yeniden [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] yönlendirer.

 VSTO için eklenti projelerinde, Outlook, `ThisAddIn` .NET Framework 3.5'i hedef alan projelerde sınıfından ve 'yi hedef alan projelerden `Microsoft.Office.Tools.Outlook.OutlookAddIn` <xref:Microsoft.Office.Tools.Outlook.OutlookAddInBase> türettir. [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] Bu temel sınıflar form bölgelerini desteklemek için bazı ek işlevler sağlar. Form bölgeleri hakkında daha fazla bilgi için [bkz. Form Outlook oluşturma.](../vsto/creating-outlook-form-regions.md)

## <a name="customize-the-user-interface-of-microsoft-office-applications"></a>Uygulama uygulamalarının kullanıcı Microsoft Office özelleştirme
 Yeni bir Eklenti kullanarak Microsoft Office kullanıcı arabirimini program aracılığıyla VSTO özelleştirebilirsiniz. Örneğin şeridi özelleştirilebilir, özel bir görev bölmesi ekleyebilirsiniz veya bu bölmede özel bir form bölgesi Outlook. Daha fazla bilgi için [bkz. Office kullanıcı arabirimi özelleştirmesi.](../vsto/office-ui-customization.md)

 Visual Studio, özel görev bölmeleri, şerit özelleştirmeleri ve form bölgelerini oluşturmak için kullanabileceğiniz Outlook sınıfları sağlar. Bu tasarımcılar ve sınıflar, bu özellikleri özelleştirme sürecini basitleştirmeye yardımcı olur. Daha fazla bilgi için [bkz. Özel görev bölmeleri,](../vsto/custom-task-panes.md) [Şerit Tasarımcısı](../vsto/ribbon-designer.md)ve [Form Outlook oluşturma.](../vsto/creating-outlook-form-regions.md)

 Bu özelliklerden birini sınıflar ve tasarımcılar tarafından desteklenen bir şekilde özelleştirmek istemiyorsanız, VSTO Eklentinizin genişletilebilirlik arabirimini kullanarak da bu özellikleri özelleştirebilirsiniz.  Daha fazla bilgi için [bkz. Genişletilebilirlik arabirimlerini kullanarak kullanıcı arabirimi özelliklerini özelleştirme.](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)

 Ayrıca, belgelerin ve çalışma kitaplarının davranışını genişleten konak öğeleri Excel Word belgelerinin kullanıcı arabirimini değiştirebilir ve çalışma kitaplarını değiştirebilirsiniz. Bu, belgelere ve çalışma sayfalarına yönetilen denetimler eklemenize olanak sağlar. Daha fazla bilgi için bkz. Word belgelerini genişletme Excel çalışma VSTO çalışma [kitaplarını çalışma zamanında genişletme.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

## <a name="call-code-in-vsto-add-ins-from-other-solutions"></a>Diğer çözümlerden VSTO eklentilerini kullanarak kod çağırma
 Uygulama eklentinizin nesnelerini VSTO çözümler de dahil olmak üzere diğer çözümlere Office sabilirsiniz. Bu, VSTO eklentinizin diğer çözümlerin kullanmalarını sağlamak istediğiniz bir hizmet sağladığında kullanışlıdır. Örneğin, web hizmetlerinden finansal veriler üzerinde hesaplamalar yapan VSTO Microsoft Office Excel için Excel VSTO Eklentiniz varsa, diğer çözümler çalışma zamanında Excel VSTO Eklentisini çağırarak bu hesaplamaları gerçekleştirebilirsiniz.

 Daha fazla bilgi için [bkz. Diğer VSTO çözümlerinden eklentilerde kod Office.](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Yeni Office geliştirme](../vsto/developing-office-solutions.md)
- [Çalışma zamanında Word Excel ve VSTO çalışma kitaplarını genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Diğer VSTO çözümlerinden eklentilerde kod Office çağırma](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Kılavuz: VBA'dan VSTO eklentisinde kod çağırma](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)
- [Kullanıcı arabirimi özelliklerini özelleştirme Genişletilebilirlik arabirimlerini kullanarak](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)
- [Nasıl Office: Visual Studio'da Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)
- [Kod yazma Office yazma](../vsto/writing-code-in-office-solutions.md)
