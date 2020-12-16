---
title: Outlook nesne modeline genel bakış
description: Microsoft Outlook için VSTO eklentileri geliştirmek üzere Outlook nesne modeli tarafından sunulan nesnelerle nasıl etkileşim kurabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.OutlookAddin
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], object model overview
- object models [Office development in Visual Studio], Office
- objects [Office development in Visual Studio], Office object models
- object models [Office development in Visual Studio], Outlook
- Office object models
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 83ada85ba346e83e5bc5ebc01e91b11be0e844e1
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528059"
---
# <a name="outlook-object-model-overview"></a>Outlook nesne modeline genel bakış
  Outlook Microsoft Office için VSTO eklentileri geliştirmek üzere Outlook nesne modeli tarafından sunulan nesnelerle etkileşim kurabilirsiniz. Outlook nesne modeli, Kullanıcı arabirimindeki öğeleri temsil eden sınıflar ve arabirimler sağlar. Örneğin, <xref:Microsoft.Office.Interop.Outlook.Application> nesnesi tüm uygulamayı temsil ediyorsa, <xref:Microsoft.Office.Interop.Outlook.Folder> nesnesi e-posta iletileri veya diğer öğeleri içeren bir klasörü temsil eder ve <xref:Microsoft.Office.Interop.Outlook.MailItem> nesne bir e-posta iletisini temsil eder.

 Bu konuda Outlook nesne modelindeki bazı ana nesnelere ilişkin kısa bir genel bakış sunulmaktadır. Tüm Outlook nesne modeli hakkında daha fazla bilgi sağlayabileceğiniz kaynaklar için bkz. [Outlook nesne modeli belgelerini kullanma](#refdoc).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="access-objects-in-an-outlook-project"></a>Outlook projesindeki nesnelere erişme
 Outlook, etkileşime girebilmeniz için birçok nesne sağlar. Nesne modelini etkin bir şekilde kullanmak için aşağıdaki üst düzey nesneler hakkında bilgi sahibi olmanız gerekir:

- <xref:Microsoft.Office.Interop.Outlook.Application>

- <xref:Microsoft.Office.Interop.Outlook.Explorer>

- <xref:Microsoft.Office.Interop.Outlook.Inspector>

- <xref:Microsoft.Office.Interop.Outlook.Folder>

- <xref:Microsoft.Office.Interop.Outlook.MailItem>

- <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>

- <xref:Microsoft.Office.Interop.Outlook.TaskItem>

- <xref:Microsoft.Office.Interop.Outlook.ContactItem>

### <a name="application-object"></a>Uygulama nesnesi
 <xref:Microsoft.Office.Interop.Outlook.Application>Nesnesi Outlook uygulamasını temsil eder ve Outlook nesne modelindeki en üst düzey nesnedir. Bu nesnenin en önemli üyelerinden bazıları şunlardır:

- E-posta iletisi, görev veya randevu gibi yeni bir öğe oluşturmak için kullanabileceğiniz [CreateItem](/previous-versions/office/developer/office-2003/aa220082(v=office.11)) yöntemi.

- <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A>Outlook Kullanıcı arabirimindeki (UI) bir klasörün içeriğini görüntüleyen Windows 'a erişmek için kullanabileceğiniz özelliği.

- <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A>Bir e-posta iletisi veya toplantı isteği gibi tek bir öğenin içeriğini görüntüleyen Windows 'a erişmek için kullanabileceğiniz özelliği.

  Nesnenin bir örneğini almak için <xref:Microsoft.Office.Interop.Outlook.Application> , projenizdeki sınıfının uygulama alanını kullanın `ThisAddIn` . Daha fazla bilgi için bkz. [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).

> [!NOTE]
> Outlook nesne modeli koruyucusu tarafından engellenen Özellikler ve Yöntemler kullandığınızda güvenlik uyarılarından kaçınmak için, sınıfının uygulama alanından Outlook nesneleri alın `ThisAddIn` . Daha fazla bilgi için bkz. [Office çözümleri Için belirli güvenlik konuları](../vsto/specific-security-considerations-for-office-solutions.md).

### <a name="explorer-object"></a>Gezgin nesnesi
 <xref:Microsoft.Office.Interop.Outlook.Explorer>Nesnesi, e-posta iletileri, görevler veya randevular gibi öğeleri içeren bir klasörün içeriğini görüntüleyen bir pencereyi temsil eder. <xref:Microsoft.Office.Interop.Outlook.Explorer>Nesnesi, pencereyi değiştirmek için kullanabileceğiniz yöntemleri ve özellikleri ve pencere değiştiğinde oluşturulan olayları içerir.

 Bir nesne almak için aşağıdakilerden <xref:Microsoft.Office.Interop.Outlook.Explorer> birini yapın:

- <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> <xref:Microsoft.Office.Interop.Outlook.Application> Outlook 'taki tüm nesnelere erişmek için nesnesinin özelliğini kullanın <xref:Microsoft.Office.Interop.Outlook.Explorer> .

- <xref:Microsoft.Office.Interop.Outlook._Application.ActiveExplorer%2A> <xref:Microsoft.Office.Interop.Outlook.Application> <xref:Microsoft.Office.Interop.Outlook.Explorer> Şu anda odağa sahip olan öğesini almak için nesnesinin yöntemini kullanın.

- `GetExplorer` <xref:Microsoft.Office.Interop.Outlook.Folder> Geçerli klasöre ulaşmak için nesnesinin yöntemini kullanın <xref:Microsoft.Office.Interop.Outlook.Explorer> .

### <a name="inspector-object"></a>Inspector nesnesi
 <xref:Microsoft.Office.Interop.Outlook.Inspector>Nesnesi, e-posta iletisi, görev veya randevu gibi tek bir öğe görüntüleyen bir pencereyi temsil eder. <xref:Microsoft.Office.Interop.Outlook.Inspector>Nesnesi, pencereyi değiştirmek için kullanabileceğiniz yöntemleri ve özellikleri ve pencere değiştiğinde oluşturulan olayları içerir.

 Bir nesne almak için aşağıdakilerden <xref:Microsoft.Office.Interop.Outlook.Inspector> birini yapın:

- <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> <xref:Microsoft.Office.Interop.Outlook.Application> Outlook 'taki tüm nesnelere erişmek için nesnesinin özelliğini kullanın <xref:Microsoft.Office.Interop.Outlook.Inspector> .

- <xref:Microsoft.Office.Interop.Outlook._Application.ActiveInspector%2A> <xref:Microsoft.Office.Interop.Outlook.Application> <xref:Microsoft.Office.Interop.Outlook.Inspector> Şu anda odağa sahip olan öğesini almak için nesnesinin yöntemini kullanın.

- `GetInspector` <xref:Microsoft.Office.Interop.Outlook.MailItem> İle Ilişkili olan Inspector 'ı almak için, veya gibi belirli bir öğenin yöntemini kullanın <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> .

### <a name="folder-object"></a>Klasör nesnesi
 <xref:Microsoft.Office.Interop.Outlook.Folder>Nesnesi e-posta iletileri, kişiler, görevler ve diğer öğeleri içeren bir klasörü temsil eder. Outlook, 16 varsayılan <xref:Microsoft.Office.Interop.Outlook.Folder> nesne sağlar.

 Varsayılan <xref:Microsoft.Office.Interop.Outlook.Folder> nesneler, numaralandırma değerleri tarafından tanımlanır <xref:Microsoft.Office.Interop.Outlook.OlDefaultFolders> . Örneğin,

 Microsoft. Office. Interop. Outlook. OlDefaultFolders. olFolderInbox, Outlook 'taki **gelen kutusu** klasörüne karşılık gelir.

 Bir varsayılana nasıl erişekullanacağınızı <xref:Microsoft.Office.Interop.Outlook.Folder> ve yeni bir oluşturma örneği için <xref:Microsoft.Office.Interop.Outlook.Folder> bkz. [nasıl yapılır: program aracılığıyla özel klasör öğeleri oluşturma](../vsto/how-to-programmatically-create-custom-folder-items.md).

### <a name="mailitem-object"></a>MailItem nesnesi
 <xref:Microsoft.Office.Interop.Outlook.MailItem>Nesne bir e-posta iletisini temsil eder. <xref:Microsoft.Office.Interop.Outlook.MailItem> nesneler genellikle **gelen kutusu**, **Gönderilen öğeler** ve **Giden kutusu** gibi klasörlerdir. <xref:Microsoft.Office.Interop.Outlook.MailItem> , e-posta iletileri oluşturmak ve göndermek için kullanılabilen özellikleri ve yöntemleri sunar.

 E-posta iletisinin nasıl oluşturulacağını gösteren bir örnek için bkz. [nasıl yapılır: program aracılığıyla e-posta öğesi oluşturma](../vsto/how-to-programmatically-create-an-e-mail-item.md).

### <a name="appointmentitem-object"></a>Randevutmentıtem nesnesi
 <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>Nesne bir toplantıyı, tek seferlik randevuyu veya **Takvim** klasöründeki bir yinelenen randevuyu veya toplantıyı temsil eder. <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>Nesnesi, Toplantı isteklerini yanıtlama veya iletme, konum ve saat gibi toplantı ayrıntılarını belirten özellikler gibi eylemleri gerçekleştiren yöntemleri içerir.

 Bir randevunun nasıl oluşturulduğunu gösteren bir örnek için bkz. [nasıl yapılır: program aracılığıyla toplantı isteği oluşturma](../vsto/how-to-programmatically-create-a-meeting-request.md).

### <a name="taskitem-object"></a>TaskItem nesnesi
 <xref:Microsoft.Office.Interop.Outlook.TaskItem>Nesne, belirtilen bir zaman çerçevesinde gerçekleştirilecek bir görevi temsil eder. <xref:Microsoft.Office.Interop.Outlook.TaskItem> nesneler, **Görevler** klasöründe bulunur.

 Bir görev oluşturmak için, nesnesinin [CreateItem](/previous-versions/office/developer/office-2003/aa220082(v=office.11)) yöntemini kullanın <xref:Microsoft.Office.Interop.Outlook.Application> ve <xref:Microsoft.Office.Interop.Outlook.OlItemType.olTaskItem> parametresi için değeri geçirin.

### <a name="contactitem-object"></a>İlgili kişi TItem nesnesi
 <xref:Microsoft.Office.Interop.Outlook.ContactItem>Nesnesi **kişiler** klasöründeki bir kişiyi temsil eder. <xref:Microsoft.Office.Interop.Outlook.ContactItem> nesneler, açık adresler, e-posta adresleri ve telefon numaraları gibi temsil ettikleri kişilerin çeşitli iletişim bilgilerini içerir.

 Yeni bir kişinin nasıl oluşturulacağını gösteren bir örnek için bkz. [nasıl yapılır: program aracılığıyla Outlook kişilerine giriş ekleme](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md). Var olan bir kişinin nasıl aranacağını gösteren bir örnek için bkz. [nasıl yapılır: program aracılığıyla belirli bir kişi arama](../vsto/how-to-programmatically-search-for-a-specific-contact.md).

## <a name="use-the-outlook-object-model-documentation"></a><a name="refdoc"></a> Outlook nesne modeli belgelerini kullanma
 Outlook nesne modeli hakkında tüm bilgiler için, Outlook birincil birlikte çalışma derlemesi (PIA) başvurusuna ve VBA nesne modeli başvurusuna başvurabilirsiniz.

### <a name="primary-interop-assembly-reference"></a>Birincil birlikte çalışma derleme başvurusu
 Outlook PIA başvurusu, Outlook 2010 için birincil birlikte çalışma derlemelerindeki türleri belgeler. Daha fazla bilgi için bkz. [Outlook 2010 birincil birlikte çalışma derleme başvurusu](/previous-versions/office/developer/office-2010/bb652780(v=office.14)).

 Bu belge, PIA 'ların tüm türleri için bilgi sağlamaya ek olarak, ortak Outlook Otomasyonu görevlerine yönelik PIA ve kod örneklerinin yapısı hakkında ek bilgiler de sağlar.

### <a name="vba-object-model-reference"></a>VBA nesne modeli başvurusu
 VBA nesne modeli başvurusu, Outlook nesne modelini Visual Basic for Applications (VBA) koduna açık olarak belgeler. Daha fazla bilgi için bkz. [Outlook 2010 nesne modeli başvurusu](/office/vba/api/overview/Outlook/object-model).

 VBA nesne modeli başvurusundaki tüm nesneler ve Üyeler Outlook PIA içindeki türlere ve üyelere karşılık gelir. Örneğin, VBA nesne modeli başvurusundaki Inspector nesnesi <xref:Microsoft.Office.Interop.Outlook.Inspector> Outlook PIA içindeki nesneye karşılık gelir. VBA nesne modeli başvurusu birçok özellik, yöntem ve olay için kod örnekleri sağlasa da, bunları Visual Studio kullanarak oluşturduğunuz bir Outlook VSTO Add-In projesinde kullanmak istiyorsanız bu başvurudaki VBA kodunu Visual Basic veya Visual C# ' ye çevirmeniz gerekir.

### <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Kişi öğeleriyle çalışma](../vsto/working-with-contact-items.md)|Kişilerle ilgili görevlerin nasıl gerçekleştirileceğini gösteren konular sağlar.|
|[Posta öğeleriyle çalışma](../vsto/working-with-mail-items.md)|Posta öğeleriyle görevlerin nasıl gerçekleştirileceğini gösteren konular sağlar.|
|[Klasörlerle çalışma](../vsto/working-with-folders.md)|Klasörler ile görevlerin nasıl gerçekleştirileceğini gösteren konular sağlar.|
|[Takvim öğeleriyle çalışma](../vsto/working-with-calendar-items.md)|Takvim öğeleriyle görevlerin nasıl gerçekleştirileceğini gösteren konular sağlar.|
|[Nasıl yapılır: program aracılığıyla geçerli Outlook öğesini belirleme](../vsto/how-to-programmatically-determine-the-current-outlook-item.md)|Geçerli klasörün adının ve seçili öğeyle ilgili bazı bilgilerin nasıl görüntüleneceğini gösterir.|
