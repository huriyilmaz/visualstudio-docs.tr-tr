---
title: Program VSTO Eklentileri
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 93470ebcea306d3cea762d60e061994b2bf27cc8
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301708"
---
# <a name="program-vsto-add-ins"></a>Program VSTO Eklentileri
  VsTO Eklentisi oluşturarak bir Microsoft Office uygulamasını genişletdiğinizde, `ThisAddIn` projenizde doğrudan sınıfa karşı kod yazarsınız. Bu sınıfı, Microsoft Office ana bilgisayar uygulamasının nesne modeline erişmek, uygulamanın kullanıcı arabirimini (UI) özelleştirmek ve VSTO Eklentinizdeki nesneleri diğer Office çözümlerine maruz bırakmak gibi görevleri gerçekleştirmek için kullanabilirsiniz.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

 VSTO Eklenti projelerinde kod yazmanın bazı yönleri Visual Studio'daki diğer proje türlerinden farklıdır. Bu farklılıkların çoğu, Office nesnesi modellerinin yönetilen koda maruz kalmasından kaynaklanır. Daha fazla bilgi için [bkz.](../vsto/writing-code-in-office-solutions.md)

 Visual Studio'daki Office geliştirme araçlarını kullanarak oluşturabileceğiniz VSTO Eklentileri ve diğer çözüm türleri hakkında genel bilgi [için, VSTO&#41;&#40;Office çözümleri geliştirme genel bakış ](../vsto/office-solutions-development-overview-vsto.md)bölümüne bakın.

## <a name="use-the-thisaddin-class"></a>ThisAddIn sınıfını kullanma
 `ThisAddIn` VSTO Eklenti kodunuzu sınıfta yazmaya başlayabilirsiniz. Visual Studio bu sınıfı, VSTO Eklenti projenizdeki [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] *ThisAddIn.vb* (in) veya *ThisAddIn.cs* (C#) kod dosyasında otomatik olarak oluşturur. Microsoft [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Office uygulaması VSTO Eklentinizi yüklendiğinde bu sınıfı otomatik olarak anında karşılar.

 `ThisAddIn` Sınıfta iki varsayılan olay işleyicisi vardır. VSTO Eklentisi yüklendiğinde kodu çalıştırmak için olay `ThisAddIn_Startup` işleyicisine kod ekleyin. VSTO Eklentisi kaldırılmadan hemen önce kodu çalıştırmak için `ThisAddIn_Shutdown` olay işleyicisine kod ekleyin. Bu olay işleyicileri hakkında daha fazla bilgi için [Office projelerindeki Etkinlikler'e](../vsto/events-in-office-projects.md)bakın.

> [!NOTE]
> Outlook'ta, varsayılan `ThisAddIn_Shutdown` olarak, VSTO Eklentisi yüklendiğinde olay işleyicisi her zaman çağrılmaz. Daha fazla bilgi için [Bkz. Office projelerindeki Etkinlikler.](../vsto/events-in-office-projects.md)

### <a name="access-the-object-model-of-the-host-application"></a>Ana bilgisayar uygulamasının nesne modeline erişin
 Ana bilgisayar uygulamasının nesne modeline `Application` erişmek için `ThisAddIn` sınıfın alanını kullanın. Bu alan, ana bilgisayar uygulamasının geçerli örneğini temsil eden bir nesne döndürür. Aşağıdaki tabloda, her VSTO Eklenti `Application` projesinde alanın iade değerinin türü listelenir.

|Ana bilgisayar uygulaması|İade değeri türü|
|----------------------|-----------------------|
|Microsoft Office Excel|<xref:Microsoft.Office.Interop.Excel.Application>|
|Microsoft Office Bilgi Yolu|<xref:Microsoft.Office.Interop.InfoPath.Application>|
|Microsoft Office Outlook|<xref:Microsoft.Office.Interop.Outlook.Application>|
|Microsoft Office PowerPoint|[Uygulama](/previous-versions/office/developer/office-2010/ff764034(v=office.14))|
|Microsoft Office Projesi|Microsoft.Office.Interop.MSProject.Application|
|Microsoft Office Visio|Microsoft.Office.Interop.Visio.Application|
|Microsoft Office Word|<xref:Microsoft.Office.Interop.Word.Application>|

 Aşağıdaki kod örneği, Microsoft `Application` Office Excel için VSTO Eklentisinde yeni bir çalışma kitabı oluşturmak için alanın nasıl kullanılacağını gösterir. Bu `ThisAddIn` örnek, sınıftan çalıştırılmak üzere tasarlanmıştır.

```vb
Dim newWorkbook As Excel.Workbook = Me.Application.Workbooks.Add()
```

```csharp
Excel.Workbook newWorkbook = this.Application.Workbooks.Add(System.Type.Missing);
```

 Aynı şeyi `ThisAddIn` sınıfın dışından yapmak için `Globals` `ThisAddIn` nesneyi sınıfa erişmek için kullanın. `Globals` Nesne hakkında daha fazla bilgi için Office [projelerindeki nesnelere Genel erişim](../vsto/global-access-to-objects-in-office-projects.md)konusuna bakın.

```vb
Dim newWorkbook As Excel.Workbook = Globals.ThisAddIn.Application.Workbooks.Add()
```

```csharp
Excel.Workbook newWorkbook = Globals.ThisAddIn.Application.Workbooks.Add(System.Type.Missing);
```

 Belirli Microsoft Office uygulamalarının nesne modelleri hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [Excel nesne modeline genel bakış](../vsto/excel-object-model-overview.md)

- [Word nesnesi modeline genel bakış](../vsto/word-object-model-overview.md)

- [Outlook nesne modeline genel bakış](../vsto/outlook-object-model-overview.md)

- [InfoPath çözümleri](../vsto/infopath-solutions.md)

- [PowerPoint çözümleri](../vsto/powerpoint-solutions.md)

- [Proje çözümleri](../vsto/project-solutions.md)

- [Visio nesne modeline genel bakış](../vsto/visio-object-model-overview.md)

### <a name="access-a-document-when-the-office-application-starts"></a><a name="AccessingDocuments"></a>Office uygulaması başlatıldığında belgeye erişin
 Tüm [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] uygulamalar başlattığınızda bir belgeyi otomatik olarak açmaz [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] ve başlattığınızda hiçbir uygulama belgeyi açmaz. Bu nedenle, kod bir `ThisAdd-In_Startup` belgenin açık olmasını gerektiriyorsa, olay işleyicisine kod eklemeyin. Bunun yerine, bu kodu, bir kullanıcı bir belge oluşturduğunda veya açtığında Office uygulamasının oluşturduğu bir olaya ekleyin. Bu şekilde, kodunuz üzerinde işlem gerçekleştirmeden önce bir belgenin açık olduğunu garanti edebilirsiniz.

 Aşağıdaki kod örneği Word'de bir belgeyle yalnızca kullanıcı bir belge oluşturduğunda veya varolan bir belgeaçtığında çalışır.

 [!code-csharp[Trin_WordAddIn_Menus#3](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#3)]
 [!code-vb[Trin_WordAddIn_Menus#3](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#3)]

### <a name="thisaddin-members-to-use-for-other-tasks"></a>ThisAddIn üyeleri diğer görevler için kullanmak
 Aşağıdaki tabloda diğer ortak görevler açıklanır `ThisAddIn` ve görevleri gerçekleştirmek için sınıfın hangi üyelerini kullanabileceğinizi gösterir.

|Görev|Kullanılacak üye|
|----------|-------------------|
|VSTO Eklentisi yüklendiğinde VSTO Eklentisini başlatmakodu çalıştırın.|Yönteme `ThisAddIn_Startup` kod ekleyin. Bu, olayın varsayılan olay <xref:Microsoft.Office.Tools.AddInBase.Startup> işleyicisidir. Daha fazla bilgi için [Bkz. Office projelerindeki Etkinlikler.](../vsto/events-in-office-projects.md)|
|VSTO Eklentisi kaldırılmadan önce VSTO Eklentisi tarafından kullanılan kaynakları temizlemek için kod çalıştırın.|Yönteme `ThisAddIn_Shutdown` kod ekleyin. Bu, olayın varsayılan olay <xref:Microsoft.Office.Tools.AddInBase.Shutdown> işleyicisidir. Daha fazla bilgi için [Bkz. Office projelerindeki Etkinlikler.](../vsto/events-in-office-projects.md) **Not:**  Outlook'ta, varsayılan `ThisAddIn_Startup` olarak, VSTO Eklentisi yüklendiğinde olay işleyicisi her zaman çağrılmaz. Daha fazla bilgi için [Bkz. Office projelerindeki Etkinlikler.](../vsto/events-in-office-projects.md)|
|Özel bir görev bölmesi görüntüleyin.|`CustomTaskPanes` Alanı kullan. Daha fazla bilgi için [bkz.](../vsto/custom-task-panes.md)|
|VSTO Eklentinizdeki nesneleri diğer Microsoft Office çözümlerine gösterin.|<xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> Yöntemi geçersiz kılın. Daha fazla bilgi için, [diğer Office çözümlerinden VSTO Eklentileri'ndeki Arama koduna](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)bakın.|
|Genişletilebilirlik arabirimi uygulayarak Microsoft Office sistemindeki bir özelliği özelleştirin.|Arabirimi <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> uygulayan bir sınıfın örneğini döndürmek için yöntemi geçersiz kılın. Daha fazla bilgi için, [genişletilebilirlik arabirimleri kullanarak Kullanıcı Arabirimi özelliklerini özelleştir'e](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)bakın. **Not:**  Şerit u-u-larını özelleştirmek için <xref:Microsoft.Office.Tools.AddInBase.CreateRibbonExtensibilityObject%2A> yöntemi de geçersiz kılabilirsiniz.|

### <a name="understand-the-design-of-the-thisaddin-class"></a>ThisAddIn sınıfının tasarımını anlama
 Hedef projelerde [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], <xref:Microsoft.Office.Tools.AddIn> bir arayüzdür. Sınıf `ThisAddIn` sınıftan <xref:Microsoft.Office.Tools.AddInBase> türetilmiştir. Bu taban sınıf, üyelerine yapılan tüm <xref:Microsoft.Office.Tools.AddIn> [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]çağrıları, 'deki arabirimin dahili uygulamasına yönlendirir.

 Outlook için VSTO Eklenti projelerinde `ThisAddIn` sınıf, .NET `Microsoft.Office.Tools.Outlook.OutlookAddIn` Framework 3.5'i hedefleyen projelerdeki sınıftan ve ..'yi <xref:Microsoft.Office.Tools.Outlook.OutlookAddInBase> [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]hedefleyen projelerden türetilmiştir. Bu temel sınıflar form bölgelerini desteklemek için bazı ek işlevler sağlar. Form bölgeleri hakkında daha fazla bilgi için [bkz.](../vsto/creating-outlook-form-regions.md)

## <a name="customize-the-user-interface-of-microsoft-office-applications"></a>Microsoft Office uygulamalarının kullanıcı arabirimini özelleştirme
 VSTO Eklentisi kullanarak Microsoft Office uygulamalarının kullanıcı arasını programlı olarak özelleştirebilirsiniz. Örneğin, şeridi özelleştirebilir, özel bir görev bölmesi görüntüleyebilir veya Outlook'ta özel bir form bölgesi oluşturabilirsiniz. Daha fazla bilgi için Bkz. [Office Kullanıcı Arabirimi özelleştirmesi.](../vsto/office-ui-customization.md)

 Visual Studio, özel görev bölmeleri, şerit özelleştirmeleri ve Outlook form bölgeleri oluşturmak için kullanabileceğiniz tasarımcılar ve sınıflar sağlar. Bu tasarımcılar ve sınıflar, bu özellikleri özelleştirme işlemini basitleştirmeye yardımcı olur. Daha fazla bilgi için bkz: [Özel görev bölmeleri,](../vsto/custom-task-panes.md) [Şerit Tasarımcısı](../vsto/ribbon-designer.md)ve Outlook form [bölgeleri oluştur.](../vsto/creating-outlook-form-regions.md)

 Bu özelliklerden birini sınıflar ve tasarımcılar tarafından desteklenmeyen bir şekilde özelleştirmek istiyorsanız, VSTO Eklentinizde *genişletilebilirlik arabirimi* uygulayarak bu özellikleri de özelleştirebilirsiniz. Daha fazla bilgi için, [genişletilebilirlik arabirimleri kullanarak Kullanıcı Arabirimi özelliklerini özelleştir'e](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)bakın.

 Ayrıca, belgelerin ve çalışma kitaplarının davranışını genişleten ana bilgisayar öğeleri oluşturarak Word belgelerinin ve Excel çalışma kitaplarının web'sini değiştirebilirsiniz. Bu, belgelere ve çalışma sayfalarına yönetilen denetimler eklemenize olanak tanır. Daha fazla bilgi için, [çalışma zamanında VSTO Eklentilerinde Word belgelerini ve Excel çalışma kitaplarını genişlet'e](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)bakın.

## <a name="call-code-in-vsto-add-ins-from-other-solutions"></a>VsTO Eklentilerinde diğer çözümlerden çağrı kodu
 VSTO Eklentinizdeki nesneleri diğer Office çözümleri de dahil olmak üzere diğer çözümlere maruz bırakabilirsiniz. Bu, VSTO Eklentiniz diğer çözümleri kullanmak istediğiniz bir hizmet sağlıyorsa yararlıdır. Örneğin, Microsoft Office Excel için bir web hizmetinden finansal veriler üzerinde hesaplamalar gerçekleştiren bir VSTO Eklentiniz varsa, diğer çözümler bu hesaplamaları çalışma zamanında Excel VSTO Eklentisi'ne çağırarak gerçekleştirebilir.

 Daha fazla bilgi için, [diğer Office çözümlerinden VSTO Eklentileri'ndeki Arama koduna](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümleri geliştirin](../vsto/developing-office-solutions.md)
- [Word belgelerini ve Excel çalışma kitaplarını vsto eklentilerinde çalışma zamanında genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Diğer Office çözümlerinden VSTO Eklentilerinde arama kodu](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Walkthrough: VBA'dan VSTO Eklentisi'nde arama kodu](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)
- [Genişletilebilirlik arabirimleri kullanarak AraBirimi özelliklerini özelleştirin](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)
- [Nasıl yapılır: Visual Studio'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)
- [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md)
