---
title: Office birincil birlikte çalışma derlemeleri
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f4677cd2d178781d79b11ac3b1010a76fd6fcf00
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985710"
---
# <a name="office-primary-interop-assemblies"></a>Office birincil birlikte çalışma derlemeleri

Office projesinden bir Microsoft Office uygulamasının özelliklerini kullanmak için, uygulama için birincil birlikte çalışma derlemesini (PIA) kullanmanız gerekir. PIA, yönetilen kodun bir Microsoft Office uygulamasının COM tabanlı nesne modeliyle etkileşime geçmesini sağlar.

[!include[Add-ins note](includes/addinsnote.md)]

Yeni bir Office projesi oluşturduğunuzda, Visual Studio, projeyi derlemek için gerekli olan PIA 'lara başvurular ekler. Bazı senaryolarda, ek PIA 'lara başvurular eklemeniz gerekebilir (örneğin, bir projede Microsoft Office Excel için bir Microsoft Office Word özelliği kullanmak istiyorsanız).

Bu konuda Office projelerinde Microsoft Office PIA kullanmanın aşağıdaki yönleri açıklanmaktadır:

- [Projeleri derlemek ve çalıştırmak için birincil birlikte çalışma derlemelerini ayırın](#separateassemblies)

- [Tek bir projede birden çok Microsoft Office uygulamasının özelliklerini kullanma](#usingfeatures)

- [Microsoft Office uygulamaları için birincil birlikte çalışma derlemelerinin tam listesi](#pialist)

Birincil birlikte çalışma derlemeleri hakkında daha fazla bilgi için bkz. [birincil birlikte çalışma derlemeleri](/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).

<a name="separateassemblies"></a>

## <a name="separate-primary-interop-assemblies-to-build-and-run-projects"></a>Projeleri derlemek ve çalıştırmak için birincil birlikte çalışma derlemelerini ayırın

Visual Studio, geliştirme bilgisayarında farklı PIA kümelerini kullanır. Bu farklı derleme kümeleri aşağıdaki konumlarda bulunur:

- Program dosyaları dizinindeki bir klasör

  Derlemelerin bu kopyaları kod yazdığınızda ve proje oluşturduğunuzda kullanılır. Visual Studio bu derlemeleri otomatik olarak yüklenir.

- Genel derleme önbelleği

  Derlemelerin bu kopyaları, projeleri çalıştırdığınızda veya hata ayıkladığınızda olduğu gibi bazı geliştirme görevleri sırasında kullanılır. Visual Studio bu derlemeleri yüklemez ve kaydetmez; Bunu sizin yapmanız gerekir.

### <a name="primary-interop-assemblies-in-the-program-files-directory"></a>Program Files dizinindeki birincil birlikte çalışma derlemeleri

Visual Studio 'Yu yüklediğinizde, PIA 'ler, genel derleme önbelleğinin dışında dosya sistemindeki bir konuma otomatik olarak yüklenir. Yeni bir proje oluşturduğunuzda, Visual Studio PIA 'lerin bu kopyalarına otomatik olarak projenize başvurular ekler. Visual Studio, projenizi geliştirirken ve oluştururken tür başvurularını çözümlemek için genel derleme önbelleğindeki derlemeler yerine PIA 'lerin bu kopyalarını kullanır.

PIA 'ların bu kopyaları, Visual Studio 'nun farklı sürümleri genel derleme önbelleğine kaydedildiğinde oluşabilecek çeşitli geliştirme sorunlarından kaçınmaya yardımcı olur.

Visual Studio 2017 ' den itibaren, PIA 'ların bu kopyaları geliştirme bilgisayarındaki aşağıdaki paylaşılan konumlara yüklenir:

- `%ProgramFiles%\Microsoft Visual Studio\Shared\Visual Studio Tools for Office\PIA\`

- (veya 64 bit işletim sistemlerinde `%ProgramFiles(x86)%\Microsoft Visual Studio\Shared\Visual Studio Tools for Office\PIA\`)

> [!NOTE]
> Visual Studio 'nun eski sürümlerinde bu PIA 'ler, Visual Studio 'nun `%ProgramFiles%` klasörü altındaki Office\pıa için Visual Studio Araçları yüklenir.
> Örneğin: `%ProgramFiles(x86)%\Microsoft Visual Studio 14.0\Visual Studio Tools for Office\PIA\`

### <a name="primary-interop-assemblies-in-the-global-assembly-cache"></a>Genel derleme önbelleğindeki birincil birlikte çalışma derlemeleri

Belirli geliştirme görevlerini gerçekleştirmek için, PIA 'lar geliştirme bilgisayarındaki genel derleme önbelleğinde yüklü ve kayıtlı olmalıdır. Genellikle, geliştirme bilgisayarına Office yüklediğinizde PIA 'lar otomatik olarak yüklenir. Daha fazla bilgi için bkz. [Office çözümleri geliştirmek için bir bilgisayarı yapılandırma](../vsto/configuring-a-computer-to-develop-office-solutions.md).

Office PIA 'Ları, son kullanıcı bilgisayarlarında Office çözümlerini çalıştırmak için gerekli değildir. Daha fazla bilgi için bkz. [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md).

<a name="usingfeatures"></a>

## <a name="use-features-of-multiple-microsoft-office-applications-in-a-single-project"></a>Tek bir projede birden çok Microsoft Office uygulamasının özelliklerini kullanma

Visual Studio 'daki her Office proje şablonu, tek bir Microsoft Office uygulamayla çalışacak şekilde tasarlanmıştır. Çoklu Microsoft Office uygulamalarında özellikleri kullanmak veya Visual Studio 'da proje olmayan bir uygulama veya bileşendeki özellikleri kullanmak için, gerekli PIA 'lara bir başvuru eklemeniz gerekir.

Çoğu durumda, Visual Studio tarafından `%ProgramFiles(x86)%\Microsoft Visual Studio\Shared\Visual Studio Tools for Office\PIA\` dizininden yüklenen PIA 'lara başvuru eklemeniz gerekir. Derlemelerin bu sürümleri, **başvuru Yöneticisi** Iletişim kutusunun **Framework** sekmesinde görünür. Daha fazla bilgi için bkz. [nasıl yapılır: birincil birlikte çalışma Derlemeleriyle Office uygulamalarını hedefleme](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md).

PIA 'leri genel derleme önbelleğine yükleyip kaydettirmiş olmanız durumunda derlemelerin bu sürümleri **başvuru Yöneticisi** Iletişim kutusunun **com** sekmesinde görünür. Bunları kullandığınızda oluşabilecek bazı geliştirme sorunları olduğu için derlemelerin bu sürümlerine başvuru eklememelisiniz. Örneğin, genel derleme önbelleğinde PIA 'ların farklı sürümlerini kaydettirdiğiniz takdirde, proje, **com** üzerinde derlemenin farklı bir sürümünü belirtseniz bile, projeniz son kaydedilen derlemenin sürümüne otomatik olarak bağlanır. **başvuru Yöneticisi** iletişim kutusunun sekmesi.

> [!NOTE]
> Bazı derlemeler, bunlara başvuran bir derleme eklendiğinde projeye otomatik olarak eklenir. Örneğin, Word, Excel, Outlook, Microsoft Forms veya Graph derlemelerine bir başvuru eklediğinizde `Office.dll` ve `Microsoft.Vbe.Interop.dll` Derlemeleriyle ilgili başvurular otomatik olarak eklenir.

<a name="pialist"></a>

## <a name="primary-interop-assemblies-for-microsoft-office-applications"></a>Microsoft Office uygulamaları için birincil birlikte çalışma derlemeleri

Aşağıdaki tabloda [!INCLUDE[Office_16_short](../vsto/includes/office-16-short-md.md)], [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] ve [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]için kullanılabilen birincil birlikte çalışma derlemeleri listelenmektedir.

<br/>

|Office uygulaması veya bileşeni|Birincil birlikte çalışma derleme adı|
|-------------------------------------|-----------------------------------|
|Microsoft Access 14,0 nesne kitaplığı<br /><br /> Microsoft Access 15,0 nesne kitaplığı|Microsoft. Office. Interop. Access. dll|
|Microsoft Office 14,0 Access Database Engine nesne kitaplığı<br /><br /> Microsoft Office 15,0 Access Database Engine nesne kitaplığı|Microsoft. Office. Interop. Access. DAO. dll|
|Microsoft Excel 14,0 nesne kitaplığı<br /><br /> Microsoft Excel 15,0 nesne kitaplığı|[Microsoft. Office. Interop. Excel. dll](/dotnet/api/microsoft.office.interop.excel?view=excel-pia)|
|Microsoft Graph 14,0 nesne kitaplığı (grafikler için PowerPoint, Access ve Word tarafından kullanılır)<br /><br /> Microsoft Graph 15,0 nesne kitaplığı|Microsoft. Office. Interop. Graph. dll|
|Microsoft InfoPath 2,0 tür kitaplığı (yalnızca InfoPath 2007 için)|[Microsoft. Office. Interop. InfoPath. dll](/dotnet/api/microsoft.office.interop.infopath?view=infopath-form)|
|Microsoft InfoPath XML birlikte çalışma derlemesi (yalnızca InfoPath 2007 için)|Microsoft. Office. Interop. InfoPath. xml. dll|
|Microsoft Office 14,0 nesne kitaplığı (Office paylaşılan işlevselliği)<br /><br /> Microsoft Office 15,0 nesne kitaplığı (Office paylaşılan işlevselliği)|Office. dll|
|Outlook Görünüm denetimini Microsoft Office (Web sayfalarınızda ve uygulamalarda, gelen kutunuza erişmek için kullanılabilir)|Microsoft. Office. Interop. OutlookViewCtl. dll|
|Microsoft Outlook 14,0 nesne kitaplığı<br /><br /> Microsoft Outlook 15,0 nesne kitaplığı|[Microsoft. Office. Interop. Outlook. dll](/dotnet/api/microsoft.office.interop.outlook?view=outlook-pia)|
|Microsoft PowerPoint 14,0 nesne kitaplığı<br /><br /> Microsoft PowerPoint 15,0 nesne kitaplığı|Microsoft. Office. Interop. PowerPoint. dll|
|Microsoft Project 14,0 nesne kitaplığı<br /><br /> Microsoft Project 15,0 nesne kitaplığı|[Microsoft. Office. Interop. MSProject. dll](/dotnet/api/microsoft.office.interop.msproject?view=office-project-server)|
|Microsoft Publisher 14,0 nesne kitaplığı<br /><br /> Microsoft Publisher 15,0 nesne kitaplığı|Microsoft. Office. Interop. Publisher. dll|
|Microsoft SharePoint Designer 14,0 Web nesnesi başvuru kitaplığı|Microsoft. Office. Interop. SharePointDesigner. dll|
|Microsoft SharePoint Designer 14,0 sayfa nesne başvuru kitaplığı|Microsoft. Office. Interop. SharePointDesignerPage. dll|
|Microsoft Akıllı Etiketler 2,0 tür kitaplığı **Note:** akıllı etiketler [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] ve [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]kullanım dışıdır.|Microsoft. Office. Interop. SmartTag. dll|
|Microsoft Visio 14,0 tür kitaplığı<br /><br /> Microsoft Visio 15,0 tür kitaplığı|Microsoft. Office. Interop. Visio. dll|
|Microsoft Visio 14,0 Web türü kitaplığı olarak kaydet<br /><br /> Microsoft Visio 15,0 Web türü kitaplığı olarak kaydet|Microsoft. Office. Interop. Visio. SaveAsWeb. dll|
|Microsoft Visio 14,0 çizim denetim türü kitaplığı<br /><br /> Microsoft Visio 15,0 çizim denetim türü kitaplığı|Microsoft. Office. Interop. VisOcx. dll|
|Microsoft Word 14,0 nesne kitaplığı<br /><br /> Microsoft Word 15,0 nesne kitaplığı|[Microsoft. Office. Interop. Word. dll](/dotnet/api/microsoft.office.interop.word?view=word-pia)|
|Microsoft Visual Basic for Applications genişletilebilirliği 5,3|Microsoft. Vbe. Interop. dll|

### <a name="binding-redirect-assemblies"></a>Bağlama yeniden yönlendirme derlemeleri

Office PIA 'Ları genel derleme önbelleğine yükleyip kaydettiğinizde (Office ile veya PIA 'lar için yeniden dağıtılabilir paketi yükleyerek), bağlama yeniden yönlendirme derlemeleri de yalnızca genel derleme önbelleğine yüklenir. Bu derlemeler, çalışma zamanında birincil birlikte çalışma derlemelerinin doğru sürümünün yüklendiğinden emin olmanıza yardımcı olur.

Örneğin, bir [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] derlemesine başvuran bir çözüm aynı birincil birlikte çalışma derlemesinin [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] sürümüne sahip olan bir bilgisayarda çalıştığında, bağlama yeniden yönlendirme derlemesi, [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] çalışma zamanına birincil öğesinin [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] sürümünü yüklemesini bildirir. birlikte çalışma derlemesi.

Daha fazla bilgi için bkz. [nasıl yapılır: otomatik bağlama yeniden yönlendirmeyi etkinleştirme ve devre dışı bırakma](/dotnet/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection).

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: birincil birlikte çalışma Derlemeleriyle Office uygulamalarını hedefleme](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Excel nesne modeline genel bakış](../vsto/excel-object-model-overview.md)
- [InfoPath çözümleri](../vsto/infopath-solutions.md)
- [Outlook nesne modeline genel bakış](../vsto/outlook-object-model-overview.md)
- [PowerPoint çözümleri](../vsto/powerpoint-solutions.md)
- [Proje çözümleri](../vsto/project-solutions.md)
- [Visio nesne modeline genel bakış](../vsto/visio-object-model-overview.md)
- [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md)
- [Visual Studio &#40;'da Genel başvuru Office geliştirme&#41;](../vsto/general-reference-office-development-in-visual-studio.md)
