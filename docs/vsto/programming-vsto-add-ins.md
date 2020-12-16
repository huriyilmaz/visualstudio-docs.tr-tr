---
title: Program VSTO eklentileri
description: Microsoft Office ana bilgisayar uygulamasının nesne modeline erişim gibi görevleri gerçekleştirmek için ThisAddIn sınıfını nasıl kullanabileceğinizi öğrenin.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7c3a4b14a1935d1d276f0884234fcd121b838f39
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525110"
---
# <a name="program-vsto-add-ins"></a>Program VSTO eklentileri
  Bir Microsoft Office uygulamasını bir VSTO eklentisi oluşturarak genişlettiğinizde, doğrudan projenizdeki sınıfa karşı kod yazarsınız `ThisAddIn` . Bu sınıfı, Microsoft Office ana bilgisayar uygulamasının nesne modeline erişim, uygulamanın kullanıcı arabirimini (UI) özelleştirme ve VSTO eklentiinizdeki nesneleri diğer Office çözümlerine sunma gibi görevleri gerçekleştirmek için kullanabilirsiniz.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

 VSTO eklenti projelerinde kod yazmanın bazı yönleri, Visual Studio 'daki diğer proje türlerinden farklıdır. Bu farklılıkların birçoğu, Office nesne modellerinin yönetilen koda sunulma yoludur. Daha fazla bilgi için bkz. [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md).

 Visual Studio 'da Office geliştirme araçları 'nı kullanarak, VSTO eklentileri ve oluşturabileceğiniz diğer çözüm türleri hakkında genel bilgi için bkz. [Office çözümleri geliştirmeye genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

## <a name="use-the-thisaddin-class"></a>ThisAddIn sınıfını kullanma
 Sınıfında VSTO eklenti kodunuzu yazmaya başlayabilirsiniz `ThisAddIn` . Visual Studio bu sınıfı otomatik olarak VSTO eklenti projenizdeki *ThisAddIn. vb* (in [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ) veya *ThisAddIn.cs* (C#) kod dosyasında oluşturur. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Microsoft Office UYGULAMASı VSTO eklentinizi yüklediğinde, bu sınıfı otomatik olarak başlatır.

 Sınıfında iki varsayılan olay işleyicisi vardır `ThisAddIn` . VSTO eklentisi yüklendiğinde kodu çalıştırmak için `ThisAddIn_Startup` olay işleyicisine kod ekleyin. VSTO eklentisi kaldırılmadan hemen önce kodu çalıştırmak için `ThisAddIn_Shutdown` olay işleyicisine kod ekleyin. Bu olay işleyicileri hakkında daha fazla bilgi için bkz. [Office Projelerindeki Olaylar](../vsto/events-in-office-projects.md).

> [!NOTE]
> Outlook 'ta, varsayılan olarak, `ThisAddIn_Shutdown` VSTO eklentisi kaldırıldığında olay işleyicisi her zaman çağrılmaz. Daha fazla bilgi için bkz. [Office Projelerindeki Olaylar](../vsto/events-in-office-projects.md).

### <a name="access-the-object-model-of-the-host-application"></a>Ana bilgisayar uygulamasının nesne modeline erişin
 Konak uygulamasının nesne modeline erişmek için, `Application` sınıfının alanını kullanın `ThisAddIn` . Bu alan, ana bilgisayar uygulamasının geçerli örneğini temsil eden bir nesne döndürür. Aşağıdaki tabloda, `Application` her VSTO eklenti projesindeki alan için dönüş değerinin türü listelenmektedir.

|Konak uygulaması|Dönüş değeri türü|
|----------------------|-----------------------|
|Microsoft Office Excel|<xref:Microsoft.Office.Interop.Excel.Application>|
|InfoPath Microsoft Office|<xref:Microsoft.Office.Interop.InfoPath.Application>|
|Outlook 'U Microsoft Office|<xref:Microsoft.Office.Interop.Outlook.Application>|
|Microsoft Office PowerPoint|[Uygulama](/previous-versions/office/developer/office-2010/ff764034(v=office.14))|
|Microsoft Office projesi|Microsoft. Office. Interop. MSProject. Application|
|Microsoft Office Visio|Microsoft. Office. Interop. Visio. Application|
|Microsoft Office sözcük|<xref:Microsoft.Office.Interop.Word.Application>|

 Aşağıdaki kod örneği, `Application` Microsoft Office Excel için BIR VSTO eklentisi içinde yeni bir çalışma kitabı oluşturmak için alanını nasıl kullanacağınızı gösterir. Bu örnek sınıfından çalıştırılmak üzere tasarlanmıştır `ThisAddIn` .

```vb
Dim newWorkbook As Excel.Workbook = Me.Application.Workbooks.Add()
```

```csharp
Excel.Workbook newWorkbook = this.Application.Workbooks.Add(System.Type.Missing);
```

 Sınıfın dışından aynı şeyi yapmak için, `ThisAddIn` `Globals` sınıfına erişmek için nesnesini kullanın `ThisAddIn` . Nesnesi hakkında daha fazla bilgi için `Globals` bkz. [Office Projelerindeki Nesnelere Genel erişim](../vsto/global-access-to-objects-in-office-projects.md).

```vb
Dim newWorkbook As Excel.Workbook = Globals.ThisAddIn.Application.Workbooks.Add()
```

```csharp
Excel.Workbook newWorkbook = Globals.ThisAddIn.Application.Workbooks.Add(System.Type.Missing);
```

 Belirli Microsoft Office uygulamalarının nesne modelleri hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [Excel nesne modeline genel bakış](../vsto/excel-object-model-overview.md)

- [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md)

- [Outlook nesne modeline genel bakış](../vsto/outlook-object-model-overview.md)

- [InfoPath çözümleri](../vsto/infopath-solutions.md)

- [PowerPoint çözümleri](../vsto/powerpoint-solutions.md)

- [Proje çözümleri](../vsto/project-solutions.md)

- [Visio nesne modeline genel bakış](../vsto/visio-object-model-overview.md)

### <a name="access-a-document-when-the-office-application-starts"></a><a name="AccessingDocuments"></a> Office uygulaması başladığında bir belgeye erişin
 Tüm [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] uygulamalar, başlatıldığında bir belgeyi otomatik olarak açmaz ve [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] uygulamayı başlattığınızda herhangi bir belgeyi açmayın. Bu nedenle, `ThisAdd-In_Startup` kod bir belgenin açık olmasını gerektiriyorsa olay işleyicisine kod eklemeyin. Bunun yerine, bir Kullanıcı bir belge oluşturduğunda veya açtığında Office uygulamasının oluşturduğu bir olaya bu kodu ekleyin. Bu şekilde, kodunuzun üzerinde işlem gerçekleştirmeden önce bir belgenin açık olduğunu garanti edebilirsiniz.

 Aşağıdaki kod örneği, yalnızca Kullanıcı bir belge oluşturduğunda veya var olan bir belgeyi açtığında Word 'deki bir belge ile birlikte kullanılır.

 [!code-csharp[Trin_WordAddIn_Menus#3](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#3)]
 [!code-vb[Trin_WordAddIn_Menus#3](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#3)]

### <a name="thisaddin-members-to-use-for-other-tasks"></a>Diğer görevler için kullanılacak ThisAddIn üyeleri
 Aşağıdaki tabloda, diğer ortak görevler açıklanmakta ve bu, hangi sınıf üyelerini `ThisAddIn` görevleri gerçekleştirmek için kullanabileceğiniz gösterilmektedir.

|Görev|Kullanılacak üye|
|----------|-------------------|
|VSTO eklentisi yüklendiğinde VSTO eklentisini başlatmak için kodu çalıştırın.|Yöntemine kod ekleyin `ThisAddIn_Startup` . Bu olay için varsayılan olay işleyicisidir <xref:Microsoft.Office.Tools.AddInBase.Startup> . Daha fazla bilgi için bkz. [Office Projelerindeki Olaylar](../vsto/events-in-office-projects.md).|
|VSTO eklentisi kaldırılmadan önce VSTO eklentisi tarafından kullanılan kaynakları temizlemek için kodu çalıştırın.|Yöntemine kod ekleyin `ThisAddIn_Shutdown` . Bu olay için varsayılan olay işleyicisidir <xref:Microsoft.Office.Tools.AddInBase.Shutdown> . Daha fazla bilgi için bkz. [Office Projelerindeki Olaylar](../vsto/events-in-office-projects.md). **Note:**  Outlook 'ta, varsayılan olarak, `ThisAddIn_Shutdown` VSTO eklentisi kaldırıldığında olay işleyicisi her zaman çağrılmaz. Daha fazla bilgi için bkz. [Office Projelerindeki Olaylar](../vsto/events-in-office-projects.md).|
|Özel bir görev bölmesi görüntüleyin.|Alanını kullanın `CustomTaskPanes` . Daha fazla bilgi için bkz. [özel görev bölmeleri](../vsto/custom-task-panes.md).|
|VSTO eklentiinizdeki nesneleri diğer Microsoft Office çözümlerine sunun.|Yöntemini geçersiz kılın <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> . Daha fazla bilgi için bkz. [VSTO eklentilerindeki kodu diğer Office Çözümlerinden çağırma](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).|
|Genişletilebilirlik arabirimini uygulayarak Microsoft Office sisteminde bir özelliği özelleştirin.|<xref:Microsoft.Office.Tools.AddInBase.RequestService%2A>Arabirimini uygulayan bir sınıfın örneğini döndürmek için yöntemini geçersiz kılın. Daha fazla bilgi için bkz. [genişletilebilirlik arabirimlerini kullanarak Kullanıcı arabirimi özelliklerini özelleştirme](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md). **Note:**  Şerit kullanıcı arabirimini özelleştirmek için yöntemini de geçersiz kılabilirsiniz <xref:Microsoft.Office.Tools.AddInBase.CreateRibbonExtensibilityObject%2A> .|

### <a name="understand-the-design-of-the-thisaddin-class"></a>ThisAddIn sınıfının tasarımını anlama
 Öğesini hedefleyen projelerde [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] <xref:Microsoft.Office.Tools.AddIn> bir arabirimdir. `ThisAddIn`Sınıf sınıfından türetilir <xref:Microsoft.Office.Tools.AddInBase> . Bu temel sınıf <xref:Microsoft.Office.Tools.AddIn> , içindeki içindeki arayüzün iç uygulamasına yapılan tüm çağrıları yeniden yönlendirir [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

 Outlook için VSTO eklentisi projelerinde, `ThisAddIn` sınıfı, `Microsoft.Office.Tools.Outlook.OutlookAddIn` .NET Framework 3,5 ' i ve ' ı hedefleyen projelerdeki ' i hedefleyen projelerdeki sınıfından türetilir <xref:Microsoft.Office.Tools.Outlook.OutlookAddInBase> [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Bu temel sınıflar, form bölgelerini desteklemek için bazı ek işlevler sağlar. Form bölgeleri hakkında daha fazla bilgi için bkz. [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md).

## <a name="customize-the-user-interface-of-microsoft-office-applications"></a>Microsoft Office uygulamalarının Kullanıcı arabirimini özelleştirme
 VSTO eklentisini kullanarak Microsoft Office uygulamalarının Kullanıcı arabirimini programlı bir şekilde özelleştirebilirsiniz. Örneğin, şeridi özelleştirebilir, özel bir görev bölmesi görüntüleyebilir veya Outlook 'ta özel bir form bölgesi oluşturabilirsiniz. Daha fazla bilgi için bkz. [OFFICE UI özelleştirmesi](../vsto/office-ui-customization.md).

 Visual Studio, özel görev bölmeleri, Şerit özelleştirmeleri ve Outlook form bölgeleri oluşturmak için kullanabileceğiniz tasarımcılar ve sınıflar sağlar. Bu tasarımcılar ve sınıflar, bu özellikleri özelleştirme sürecini basitleştirmeye yardımcı olur. Daha fazla bilgi için bkz. [özel görev bölmeleri](../vsto/custom-task-panes.md), [Şerit Tasarımcısı](../vsto/ribbon-designer.md)ve [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md).

 Bu özelliklerden birini sınıflar ve tasarımcılar tarafından desteklenmeyen bir şekilde özelleştirmek istiyorsanız, VSTO eklentiinizdeki *genişletilebilirlik arabirimini* uygulayarak da bu özellikleri özelleştirebilirsiniz. Daha fazla bilgi için bkz. [genişletilebilirlik arabirimlerini kullanarak Kullanıcı arabirimi özelliklerini özelleştirme](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md).

 Ayrıca, belge ve çalışma kitaplarının davranışını genişleten konak öğeleri oluşturarak Word belgelerinin ve Excel çalışma kitaplarının Kullanıcı arabirimini de değiştirebilirsiniz. Bu, belgelere ve çalışma sayfalarına yönetilen denetimler eklemenize olanak sağlar. Daha fazla bilgi için bkz. [çalışma ZAMANıNDA VSTO Eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="call-code-in-vsto-add-ins-from-other-solutions"></a>Diğer çözümlerdeki VSTO eklentilerindeki kodu çağırma
 VSTO eklentiinizdeki nesneleri diğer Office çözümleri de dahil olmak üzere diğer çözümlere kullanıma sunabilirsiniz. Bu, VSTO eklentisinin diğer çözümlerin kullanmasını sağlamak istediğiniz bir hizmet sağlıyorsa yararlı olur. Örneğin, bir Web hizmetinden finans verilerinde hesaplamalar gerçekleştiren Microsoft Office Excel için bir VSTO eklentileriniz varsa, diğer çözümler çalışma zamanında Excel VSTO eklentisini çağırarak bu hesaplamaları gerçekleştirebilir.

 Daha fazla bilgi için bkz. [VSTO eklentilerindeki kodu diğer Office Çözümlerinden çağırma](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümleri geliştirme](../vsto/developing-office-solutions.md)
- [VSTO Eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Diğer Office çözümlerindeki VSTO eklentilerindeki kodu çağırma](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [İzlenecek yol: bir VSTO eklentisinde VBA 'dan kod çağırma](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)
- [Genişletilebilirlik arabirimlerini kullanarak Kullanıcı arabirimi özelliklerini özelleştirme](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)
- [Nasıl yapılır: Visual Studio 'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)
- [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md)
