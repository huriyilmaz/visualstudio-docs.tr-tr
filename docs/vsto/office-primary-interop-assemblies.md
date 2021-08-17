---
title: Office birincil birlikte çalışma derlemeleri
description: Bir Microsoft Office projesinden bir uygulamanın özelliklerine erişmek için birincil birlikte çalışma derlemesini (PIA) Office öğrenin.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies
- assemblies [Office development in Visual Studio], primary interop assemblies
- Office primary interop assemblies
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: d6f610e9cd1667b84f382f7b1f48c231a69ec44797bafc343f11a7c508636df1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121394178"
---
# <a name="office-primary-interop-assemblies"></a>Office birincil birlikte çalışma derlemeleri

Bir Office projesinden bir Microsoft Office uygulamasının özelliklerini kullanmak için, uygulamanın birincil birlikte çalışma derlemesini (PIA) kullansanız gerekir. PIA, yönetilen kodun bir uygulamanın COM tabanlı Microsoft Office modeliyle etkileşim kurmalarına olanak sağlar.

[!include[Add-ins note](includes/addinsnote.md)]

Yeni bir proje Office, Visual Studio oluşturmak için gereken PIA'lara başvurular ekler. Bazı senaryolarda, ek PIA'lara başvurular eklemeniz (örneğin, Microsoft Office Word özelliğini bir projesinde Microsoft Office Excel).

Bu konuda, Office projelerinde Microsoft Office PIA'larını kullanmanın Office açıklanmıştır:

- [Projeleri derlemek ve çalıştırmak için birincil birlikte çalışma derlemelerini ayırma](#separateassemblies)

- [Tek bir projede birden Microsoft Office uygulamanın özelliklerini kullanma](#usingfeatures)

- [Özel uygulamalar için birincil birlikte çalışma derlemelerinin Microsoft Office listesi](#pialist)

Birincil birlikte çalışma derlemeleri hakkında daha fazla bilgi için bkz. [Birincil birlikte çalışma derlemeleri.](/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100))

<a name="separateassemblies"></a>

## <a name="separate-primary-interop-assemblies-to-build-and-run-projects"></a>Projeleri derlemek ve çalıştırmak için birincil birlikte çalışma derlemelerini ayırma

Visual Studio bilgisayarda farklı PIA kümeleri kullanır. Bu farklı derleme kümeleri aşağıdaki konumlardadır:

- Program dosyaları dizinindeki bir klasör

  Derlemelerin bu kopyaları, kod yazmanız ve proje derlemek için kullanılır. Visual Studio derlemeleri otomatik olarak yüklemez.

- Genel derleme önbelleği

  Derlemelerin bu kopyaları, projeleri çalıştırma veya projelerde hata ayıklama gibi bazı geliştirme görevleri sırasında kullanılır. Visual Studio derlemeleri yüklemez ve kaydetmez; Bunu kendiniz yapmak gerekir.

### <a name="primary-interop-assemblies-in-the-program-files-directory"></a>Program dosyaları dizininde birincil birlikte çalışma derlemeleri

Bu dosyaları Visual Studio, PIA'lar genel derleme önbelleğinin dışında, dosya sisteminde bir konuma otomatik olarak yüklenir. Yeni bir proje oluştururken, Visual Studio piA'ların bu kopyalarına otomatik olarak başvurular ekler. Visual Studio, projenizi geliştirirken ve derlemenize tür başvurularını çözümlemek için genel derleme önbelleğinde derlemeler yerine PIA'ların bu kopyalarını kullanır.

PIA'ların bu kopyaları, Visual Studio sürümleri genel derleme önbelleğine kaydedilene kadar ortaya çıkabilir çeşitli geliştirme sorunlarından kaçınmanıza yardımcı olur.

2017'Visual Studio başlayarak, piA'ların bu kopyaları geliştirme bilgisayarında aşağıdaki paylaşılan konumlara yüklenir:

- `%ProgramFiles%\Microsoft Visual Studio\Shared\Visual Studio Tools for Office\PIA\`

- (veya `%ProgramFiles(x86)%\Microsoft Visual Studio\Shared\Visual Studio Tools for Office\PIA\` 64 bit işletim sistemlerinde)

> [!NOTE]
> Önceki sürümler Visual Studio, bu PIA'lar söz Office için Visual Studio Araçları\PIA klasörüne, söz `%ProgramFiles%` Visual Studio.
> Örneğin: `%ProgramFiles(x86)%\Microsoft Visual Studio 14.0\Visual Studio Tools for Office\PIA\`

### <a name="primary-interop-assemblies-in-the-global-assembly-cache"></a>Genel derleme önbelleğinde birincil birlikte çalışma derlemeleri

Belirli geliştirme görevlerini gerçekleştirmek için PIA'ların geliştirme bilgisayarına yüklenmiş ve genel derleme önbelleğine kayıtlı olması gerekir. PiA'lar genellikle geliştirme bilgisayarına Office otomatik olarak yüklenir. Daha fazla bilgi için, [bkz. Configure a computer to develop Office .](../vsto/configuring-a-computer-to-develop-office-solutions.md)

Bu Office çözümlerini çalıştırmak için son kullanıcı bilgisayarlarında farklı PIA'lar Office gerekmez. Daha fazla bilgi için, [bkz. Tasarım ve Office çözümleri.](../vsto/designing-and-creating-office-solutions.md)

<a name="usingfeatures"></a>

## <a name="use-features-of-multiple-microsoft-office-applications-in-a-single-project"></a>Tek bir projede birden Microsoft Office uygulamanın özelliklerini kullanma

Office proje şablonu Visual Studio tek bir uygulamayla çalışacak şekilde Microsoft Office tasarlanmıştır. Birden çok Microsoft Office uygulamasındaki özellikleri kullanmak veya Visual Studio'de projesiz bir uygulamada veya bileşende özellikleri kullanmak için, gerekli PIA'lara bir başvuru eklemeniz gerekir.

Çoğu durumda, dizin altındaki bir kullanıcı tarafından yüklenmiş PIA'lara Visual Studio eklemeniz `%ProgramFiles(x86)%\Microsoft Visual Studio\Shared\Visual Studio Tools for Office\PIA\` gerekir. Derlemelerin bu sürümleri Başvuru Yöneticisi **iletişim** kutusunun Framework **sekmesinde** görünür. Daha fazla bilgi için [bkz. Nasıl Office derlemeleri aracılığıyla uygulamaları hedefleme.](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)

PIA'ları genel derleme önbelleğine yüklemiş ve kaydettiyebilirsiniz; derlemelerin bu sürümleri Başvuru Yöneticisi iletişim kutusunun **COM** **sekmesinde** görünür. Derlemelerin bu sürümlerine başvuru eklemekten kaçınmanız gerekir çünkü bunları kullanırken ortaya çıkabilir bazı geliştirme sorunları vardır. Örneğin, genel derleme önbelleğinde FARKLı PIA'ların sürümlerini kaydettiyebilirsiniz, Başvuru Yöneticisi iletişim kutusunun **COM** sekmesinde derlemenin farklı bir sürümünü belirtse bile projeniz en son kaydedilen derlemenin sürümüne otomatik olarak bağlanacaktır. 

> [!NOTE]
> Bazı derlemeler, bu derlemelere başvurulan bir derleme ekleniyorsa projeye otomatik olarak eklenir. Örneğin, Word, Excel, Outlook, Microsoft Forms veya Graph derlemelerine bir başvuru Graph ve `Office.dll` `Microsoft.Vbe.Interop.dll` derlemelerine başvurular otomatik olarak eklenir.

<a name="pialist"></a>

## <a name="primary-interop-assemblies-for-microsoft-office-applications"></a>Uygulama derlemeleri için birincil birlikte Microsoft Office derlemeleri

Aşağıdaki tabloda , ve için kullanılabilen birincil birlikte çalışma derlemeleri [!INCLUDE[Office_16_short](../vsto/includes/office-16-short-md.md)] [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] listele türetir. [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]

<br/>

|Office uygulama veya bileşen oluşturma|Birincil birlikte çalışma derleme adı|
|-------------------------------------|-----------------------------------|
|Microsoft Access 14.0 Nesne Kitaplığı<br /><br /> Microsoft Access 15.0 Nesne Kitaplığı|Microsoft.Office.Interop.Access.dll|
|Microsoft Office 14.0 Access Veritabanı Altyapısı Nesne Kitaplığı<br /><br /> Microsoft Office 15.0 Access Veritabanı Altyapısı Nesne Kitaplığı|Microsoft.Office.Interop.Access.Dao.dll|
|Microsoft Excel 14.0 Nesne Kitaplığı<br /><br /> Microsoft Excel 15.0 Nesne Kitaplığı|[Microsoft.Office.Interop.Excel.dll](/dotnet/api/microsoft.office.interop.excel?view=excel-pia&preserve-view=true)|
|Microsoft Graph 14.0 Nesne Kitaplığı (PowerPoint, Access ve Word tarafından graflar için kullanılır)<br /><br /> Microsoft Graph 15.0 Nesne Kitaplığı|Microsoft.Office.Interop.Graph.dll|
|Microsoft InfoPath 2.0 Tür Kitaplığı (yalnızca InfoPath 2007 için)|[Microsoft.Office.Interop.InfoPath.dll](/dotnet/api/microsoft.office.interop.infopath?view=infopath-form&preserve-view=true)|
|Microsoft InfoPath XML Birlikte Çalışma Derlemesi (yalnızca InfoPath 2007 için)|Microsoft.Office.Interop.InfoPath.Xml.dll|
|Microsoft Office 14.0 Nesne Kitaplığı (Office işlevselliği)<br /><br /> Microsoft Office 15.0 Nesne Kitaplığı (Office işlevselliği)|office.dll|
|Microsoft Office Outlook Görünüm Denetimi (Gelen Kutunuza erişmek için Web sayfalarında ve uygulamalarda kullanılabilir)|Microsoft.Office.Interop.OutlookViewCtl.dll|
|Microsoft Outlook 14.0 Nesne Kitaplığı<br /><br /> Microsoft Outlook 15.0 Nesne Kitaplığı|[Microsoft.Office.Interop.Outlook.dll](/dotnet/api/microsoft.office.interop.outlook?view=outlook-pia&preserve-view=true)|
|Microsoft PowerPoint 14.0 Nesne Kitaplığı<br /><br /> Microsoft PowerPoint 15.0 Nesne Kitaplığı|Microsoft.Office.Interop.PowerPoint.dll|
|Microsoft Project 14.0 Nesne Kitaplığı<br /><br /> Microsoft Project 15.0 Nesne Kitaplığı|[Microsoft.Office.Interop.MSProject.dll](/dotnet/api/microsoft.office.interop.msproject?view=office-project-server&preserve-view=true)|
|Microsoft Publisher 14.0 Nesne Kitaplığı<br /><br /> Microsoft Publisher 15.0 Nesne Kitaplığı|Microsoft.Office.Interop.Publisher.dll|
|Microsoft SharePoint Designer 14.0 Web Nesnesi Başvuru Kitaplığı|Microsoft.Office.Interop.SharePointDesigner.dll|
|Microsoft SharePoint Tasarımcısı 14.0 Sayfa Nesnesi Başvuru Kitaplığı|Microsoft.Office.Interop.SharePointDesignerPage.dll|
|Microsoft Akıllı Etiketler 2.0 Tür Kitaplığı **Not:**  ve içinde akıllı etiketler kullanım [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)] dışıdır.|Microsoft.Office.Interop.SmartTag.dll|
|Microsoft Visio 14.0 Tür Kitaplığı<br /><br /> Microsoft Visio 15.0 Tür Kitaplığı|Microsoft.Office.Interop.Visio.dll|
|Microsoft Visio 14.0 Web Türü Kitaplığı Olarak Kaydet<br /><br /> Microsoft Visio 15.0 Web Türü Kitaplığı Olarak Kaydet|Microsoft.Office.Interop.Visio.SaveAsWeb.dll|
|Microsoft Visio 14.0 Çizim Denetim Türü Kitaplığı<br /><br /> Microsoft Visio 15.0 Çizim Denetim Türü Kitaplığı|Microsoft.Office.Interop.VisOcx.dll|
|Microsoft Word 14.0 Nesne Kitaplığı<br /><br /> Microsoft Word 15,0 nesne kitaplığı|[Microsoft.Office.Interop.Word.dll](/dotnet/api/microsoft.office.interop.word?view=word-pia&preserve-view=true)|
|Microsoft Visual Basic for Applications genişletilebilirliği 5,3|Microsoft.Vbe.Interop.dll|

### <a name="binding-redirect-assemblies"></a>Bağlama yeniden yönlendirme derlemeleri

Office pıa 'leri genel derleme önbelleğine yükleyip kaydettiğinizde (Office ya da pıa 'lar için yeniden dağıtılabilir paketi yüklediğinizde), bağlama yeniden yönlendirme derlemeleri de yalnızca genel derleme önbelleğine yüklenir. Bu derlemeler, çalışma zamanında birincil birlikte çalışma derlemelerinin doğru sürümünün yüklendiğinden emin olmanıza yardımcı olur.

Örneğin, bir derlemeye başvuran bir çözüm [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] aynı birincil birlikte çalışma derlemesinin sürümüne sahip olan bir bilgisayarda çalıştığında, bağlama yeniden yönlendirme derlemesi [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] çalışma zamanına [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] birincil birlikte çalışma derlemesinin sürümünü yüklemesini söyler.

Daha fazla bilgi için bkz. [nasıl yapılır: otomatik bağlama yeniden yönlendirmeyi etkinleştirme ve devre dışı bırakma](/dotnet/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection).

## <a name="see-also"></a>Ayrıca bkz.

- [nasıl yapılır: birincil birlikte çalışma bütünleştirilmiş kodları aracılığıyla Office uygulamalarını hedefleme](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Excel nesne modeline genel bakış](../vsto/excel-object-model-overview.md)
- [InfoPath çözümleri](../vsto/infopath-solutions.md)
- [Outlook nesne modeline genel bakış](../vsto/outlook-object-model-overview.md)
- [PowerPoint çözümleri](../vsto/powerpoint-solutions.md)
- [Project çözümleri](../vsto/project-solutions.md)
- [Visio nesne modeline genel bakış](../vsto/visio-object-model-overview.md)
- [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md)
- [genel başvuru &#40;Office geliştirme Visual Studio&#41;](../vsto/general-reference-office-development-in-visual-studio.md)
