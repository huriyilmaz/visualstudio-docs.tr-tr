---
title: Office birincil birlikte çalışma derlemeleri
description: bir Office projesinden bir Microsoft Office uygulamasının özelliklerine erişmek için birincil birlikte çalışma derlemesini (pıa) nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020, devdivchpfy22
ms.date: 12/23/2021
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
ms.openlocfilehash: 8eec52171cca2894d797548203ff2d8b82322c2d
ms.sourcegitcommit: ffd1bea76b51fd6b43d484a30bbd1e674f0ae49b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/27/2021
ms.locfileid: "135563735"
---
# <a name="office-primary-interop-assemblies"></a>Office birincil birlikte çalışma derlemeleri

bir Office projesinden bir Microsoft Office uygulamasının özelliklerini kullanmak için, uygulama için birincil birlikte çalışma derlemesini (pıa) kullanmanız gerekir. pıa, yönetilen kodun bir Microsoft Office uygulamasının COM tabanlı nesne modeliyle etkileşime geçmesini sağlar.

[!include[Add-ins note](includes/addinsnote.md)]

yeni bir Office projesi oluşturduğunuzda, Visual Studio projeyi derlemek için gerekli olan pıa 'lara başvurular ekler. bazı senaryolarda, diğer pıa 'lara başvuru eklemeniz gerekebilir (örneğin, Microsoft Office Excel için bir projede bir Microsoft Office kelime özelliği kullanabilirsiniz).

bu makalede Office projelerinde Microsoft Office pıa kullanmanın aşağıdaki yönleri açıklanmaktadır:

- [Projeleri derlemek ve çalıştırmak için birincil birlikte çalışma derlemelerini ayırın](#separateassemblies)

- [tek bir projede birden çok Microsoft Office uygulamasının özelliklerini kullanma](#usingfeatures)

- [Microsoft Office uygulamaları için birincil birlikte çalışma derlemelerinin tam listesi](#pialist)

Birincil birlikte çalışma derlemeleri hakkında daha fazla bilgi için bkz. [birincil birlikte çalışma derlemeleri](/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).

<a name="separateassemblies"></a>

## <a name="separate-primary-interop-assemblies-to-build-and-run-projects"></a>Projeleri derlemek ve çalıştırmak için birincil birlikte çalışma derlemelerini ayırın

Visual Studio, geliştirme bilgisayarında farklı pıa kümelerini kullanır. Bu farklı derleme kümeleri aşağıdaki konumlarda bulunur:

- Program dosyaları dizinindeki bir klasör

  Bu derlemeler kümesi, kod yazdığınızda ve proje oluşturduğunuzda kullanılır. Visual Studio bu derlemeleri otomatik olarak yüklüyor.

- Genel derleme önbelleği

  Bu derlemeler kümesi, projeleri çalıştırdığınızda veya hata ayıkladığınızda olduğu gibi bazı geliştirme görevleri sırasında kullanılır. Visual Studio bu derlemeleri yükleyip kaydetmez; bunu kendiniz yapmanız gerekir.

### <a name="primary-interop-assemblies-in-the-program-files-directory"></a>Program Files dizinindeki birincil birlikte çalışma derlemeleri

PIA 'ler, Visual Studio yüklerken genel derleme önbelleğinin dışında dosya sistemindeki bir konuma otomatik olarak eklenir. yeni bir proje oluşturduğunuzda, Visual Studio otomatik olarak bu pıa kopyalarına başvuruları projenize ekler. Visual Studio, projenizi geliştirirken ve oluştururken tür başvurularını çözümlemek için genel derleme önbelleğindeki derlemeler yerine pıa 'lerin bu kopyalarını kullanır.

PIA 'lerin farklı sürümleri genel derleme önbelleğinde kaydettirilirse, birkaç geliştirme sorununa sahip olabilirsiniz. PIA 'ların eklenen kopyaları bu sorunlardan kaçınmak için size yardımcı olur.

Visual Studio 2017 ve üzeri için, pıa 'ların bu kopyaları geliştirme bilgisayarındaki aşağıdaki paylaşılan konumlara yüklenir:

- `%ProgramFiles%\Microsoft Visual Studio\Shared\Visual Studio Tools for Office\PIA\`

- (veya `%ProgramFiles(x86)%\Microsoft Visual Studio\Shared\Visual Studio Tools for Office\PIA\` 64 bit işletim sistemlerinde)

> [!NOTE]
> daha eski Visual Studio sürümleri için bu pıa 'ler, bu Visual Studio sürümünün klasörü altındaki Office için Visual Studio Araçları \pıa klasörüne yüklenir `%ProgramFiles%` .
> Örneğin: `%ProgramFiles(x86)%\Microsoft Visual Studio 14.0\Visual Studio Tools for Office\PIA\`

### <a name="primary-interop-assemblies-in-the-global-assembly-cache"></a>Genel derleme önbelleğindeki birincil birlikte çalışma derlemeleri

Belirli geliştirme görevlerini gerçekleştirmek için, PIA 'lar geliştirme bilgisayarındaki genel derleme önbelleğinde yüklü ve kayıtlı olmalıdır. genellikle, geliştirme bilgisayarına Office yüklediğinizde pıa 'ler otomatik olarak yüklenir. daha fazla bilgi için bkz. [Office çözümleri geliştirmek için bir bilgisayarı yapılandırma](../vsto/configuring-a-computer-to-develop-office-solutions.md).

Office pıa 'ler, Office çözümlerini çalıştırmak için son kullanıcı bilgisayarlarında gerekli değildir. daha fazla bilgi için bkz. [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md).

<a name="usingfeatures"></a>

## <a name="use-features-of-multiple-microsoft-office-applications-in-a-single-project"></a>tek bir projede birden çok Microsoft Office uygulamasının özelliklerini kullanma

Visual Studio içindeki her Office proje şablonu, tek bir Microsoft Office uygulamasıyla çalışmak üzere tasarlanmıştır. çoklu Microsoft Office uygulamalarında özellikleri kullanmak veya Visual Studio bir proje olmayan bir uygulama veya bileşendeki özellikleri kullanmak için, gerekli pıa 'lara bir başvuru eklemeniz gerekir.

çoğu durumda, dizin altında Visual Studio tarafından yüklenen pıa 'lara başvuru eklemeniz gerekir `%ProgramFiles(x86)%\Microsoft Visual Studio\Shared\Visual Studio Tools for Office\PIA\` . Derlemelerin bu sürümleri, **başvuru Yöneticisi** Iletişim kutusunun **Framework** sekmesinde görünür. daha fazla bilgi için bkz. [nasıl yapılır: uygulamaları birincil birlikte çalışma derlemeleriyle hedefleme Office](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md).

PIA 'leri genel derleme önbelleğine yükleyip kaydettirdiyseniz, derlemelerin bu sürümleri **başvuru Yöneticisi** Iletişim kutusunun **com** sekmesinde görünür. Bunları kullandığınızda oluşabilecek bazı geliştirme sorunları olduğundan, derlemelerin bu sürümlerine başvurular eklemekten kaçının. Örneğin, genel derleme önbelleğinde PIA 'ların farklı sürümlerini kaydettirdiyseniz, **başvuru Yöneticisi** Iletişim kutusunun **com** sekmesinde derlemenin farklı bir sürümünü belirtseniz bile, projeniz son olarak kaydedilmiş derlemenin sürümüne otomatik olarak bağlanır.

> [!NOTE]
> Bazı derlemeler, bunlara başvuran bir derleme eklendiğinde projeye otomatik olarak eklenir. örneğin, `Office.dll` `Microsoft.Vbe.Interop.dll` Word, Excel, Outlook, Microsoft Forms veya Graph derlemelerine bir başvuru eklediğinizde, ve derlemelerine yapılan başvurular otomatik olarak eklenir.

<a name="pialist"></a>

## <a name="primary-interop-assemblies-for-microsoft-office-applications"></a>Microsoft Office uygulamaları için birincil birlikte çalışma derlemeleri

Aşağıdaki tabloda, ve için kullanılabilen birincil birlikte çalışma derlemeleri listelenmektedir [!INCLUDE[Office_16_short](../vsto/includes/office-16-short-md.md)] [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] .

<br/>

|uygulama veya bileşen Office|Birincil birlikte çalışma derleme adı|
|-------------------------------------|-----------------------------------|
|Microsoft Access 14,0 nesne kitaplığı<br /><br /> Microsoft Access 15,0 nesne kitaplığı|Microsoft.Office.Interop.Access.dll|
|Microsoft Office 14,0 Access Database Engine nesne kitaplığı<br /><br /> Microsoft Office 15,0 Access Database Engine nesne kitaplığı|Microsoft.Office.Interop.Access.Dao.dll|
|Microsoft Excel 14,0 nesne kitaplığı<br /><br /> Microsoft Excel 15,0 nesne kitaplığı|[Microsoft.Office.Interop.Excel.dll](/dotnet/api/microsoft.office.interop.excel?view=excel-pia&preserve-view=true)|
|Microsoft Graph 14,0 nesne kitaplığı (grafikler için PowerPoint, erişim ve Word tarafından kullanılır)<br /><br /> Microsoft Graph 15,0 nesne kitaplığı|Microsoft.Office.Interop.Graph.dll|
|Microsoft InfoPath 2,0 tür kitaplığı (yalnızca InfoPath 2007 için)|[Microsoft.Office.Interop.InfoPath.dll](/dotnet/api/microsoft.office.interop.infopath?view=infopath-form&preserve-view=true)|
|Microsoft InfoPath XML birlikte çalışma derlemesi (yalnızca InfoPath 2007 için)|Microsoft.Office.Interop.InfoPath.Xml.dll|
|Microsoft Office 14,0 nesne kitaplığı (Office paylaşılan işlevler)<br /><br /> Microsoft Office 15,0 nesne kitaplığı (Office paylaşılan işlevler)|office.dll|
|Microsoft Office Outlook görünüm denetimi (Web, gelen kutunuza erişmek için Web sayfalarında ve uygulamalarda kullanılabilir)|Microsoft.Office.Interop.OutlookViewCtl.dll|
|Microsoft Outlook 14,0 nesne kitaplığı<br /><br /> Microsoft Outlook 15,0 nesne kitaplığı|[Microsoft.Office.Interop.Outlook.dll](/dotnet/api/microsoft.office.interop.outlook?view=outlook-pia&preserve-view=true)|
|Microsoft PowerPoint 14,0 nesne kitaplığı<br /><br /> Microsoft PowerPoint 15,0 nesne kitaplığı|Microsoft.Office.Interop.PowerPoint.dll|
|Microsoft Project 14,0 nesne kitaplığı<br /><br /> Microsoft Project 15,0 nesne kitaplığı|[Microsoft.Office.Interop.MSProject.dll](/dotnet/api/microsoft.office.interop.msproject?view=office-project-server&preserve-view=true)|
|Microsoft Publisher 14,0 nesne kitaplığı<br /><br /> Microsoft Publisher 15,0 nesne kitaplığı|Microsoft.Office.Interop.Publisher.dll|
|Microsoft SharePoint tasarımcısı 14,0 Web nesnesi başvuru kitaplığı|Microsoft.Office.Interop.SharePointDesigner.dll|
|Microsoft SharePoint tasarımcısı 14,0 sayfa nesnesi başvuru kitaplığı|Microsoft.Office.Interop.SharePointDesignerPage.dll|
|Microsoft Akıllı Etiketler 2,0 tür kitaplığı **Note:**  akıllı etiketler ve ' de kullanım dışıdır [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)] .|Microsoft.Office.Interop.SmartTag.dll|
|Microsoft Visio 14,0 tür kitaplığı<br /><br /> Microsoft Visio 15,0 tür kitaplığı|Microsoft.Office.Interop.Visio.dll|
|Microsoft Visio 14,0 Web türü kitaplığı olarak kaydet<br /><br /> Microsoft Visio 15,0 Web türü kitaplığı olarak kaydet|Microsoft.Office.Interop.Visio.SaveAsWeb.dll|
|Microsoft Visio 14,0 çizim denetim türü kitaplığı<br /><br /> Microsoft Visio 15,0 çizim denetim türü kitaplığı|Microsoft.Office.Interop.VisOcx.dll|
|Microsoft Word 14.0 Nesne Kitaplığı<br /><br /> Microsoft Word 15.0 Nesne Kitaplığı|[Microsoft.Office.Interop.Word.dll](/dotnet/api/microsoft.office.interop.word?view=word-pia&preserve-view=true)|
|Microsoft Visual Basic for Applications Genişletilebilirlik 5.3|Microsoft.Vbe.Interop.dll|

### <a name="binding-redirect-assemblies"></a>Yeniden yönlendirme derlemelerini bağlama

Office PIA'larını genel derleme önbelleğine yükleyerek (Office ile veya PIA'lar için yeniden dağıtılabilir paketi yükleyerek) kaydederek bağlama yeniden yönlendirme derlemeleri de yalnızca genel derleme önbelleğine yüklenir. Bu derlemeler, birincil birlikte çalışma derlemelerinin doğru sürümünün çalışma zamanında yüklendiğinden emin olur.

Örneğin, bir derlemeye başvuran bir çözüm aynı birincil birlikte çalışma derlemesi sürümüne sahip bir bilgisayarda çalıştırıldısa, bağlama yeniden yönlendirme derlemesi çalışma zamanının birincil birlikte çalışma derlemesi [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] sürümünü [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] yüklemesini ister.

Daha fazla bilgi için [bkz. Nasıl kullanılır: Otomatik bağlama yeniden yönlendirmesini etkinleştirme ve devre dışı bırakma.](/dotnet/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection)

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl kullanılır: Birincil Office derlemeleri aracılığıyla uygulamaları hedefle](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Excel modeline genel bakış](../vsto/excel-object-model-overview.md)
- [InfoPath çözümleri](../vsto/infopath-solutions.md)
- [Outlook modeline genel bakış](../vsto/outlook-object-model-overview.md)
- [PowerPoint çözümleri](../vsto/powerpoint-solutions.md)
- [Project çözümleri](../vsto/project-solutions.md)
- [Visio modeline genel bakış](../vsto/visio-object-model-overview.md)
- [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md)
- [Geliştirme aşamasında &#40;Office başvuru Visual Studio&#41;](../vsto/general-reference-office-development-in-visual-studio.md)
