---
title: Office çözümleriyle ilgili sorunları giderme
description: Uygulama geliştirme sırasında ortaya çıkabilir hataları nasıl giderebilir ve Microsoft Office çözümlerini Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: troubleshooting
f1_keywords:
- VST.Project.DesignerDisabled
- VST.Designer.CannotActivate
- VST.Project.ExcelBusy
- VST.SelectDocWizard.AlreadyCustomized
- VST.SelectDocWizard.DocPath
- VST.Project.CannotOpen
- VST.Designer.ErrorsOccurred
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- troubleshooting [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: d5959df0d24db2807bead8331d04befb7f769ae8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122099496"
---
# <a name="troubleshoot-errors-in-office-solutions"></a>Office çözümleriyle ilgili sorunları giderme
  Aşağıdaki görevleri gerçekleştirirken, aşağıdaki görevleri gerçekleştirirken aşağıdaki Office çözümler geliştirirken sorunlarla Visual Studio:

- [Projeleri oluşturma, yükseltme ve açma](#creating)

- [Tasarımcıları kullanma](#designers)

- [Kod yazma](#code)

- [Projeleri derleme](#building)

- [Projelerde hata ayıklama](#debugging)

## <a name="create-upgrade-and-open-projects"></a><a name="creating"></a> Proje oluşturma, yükseltme ve açma
 Yeni projeler oluşturma veya açma sırasında aşağıdaki hatalarla Office karşılaşabilirsiniz.

### <a name="the-project-cannot-be-created"></a>Proje oluşturulamıyor
 Office projesini oluşturma veya açmaya Visual Studio hata oluştu ama Visual Studio nedenini belirlemek için yeterli bilgiye sahip değildi. Projenizi kapatmayı, Visual Studio ve yeniden başlatmayı deneyin.

 Belge düzeyinde bir proje oluşturmaya çalışıyorsanız, yeni projede belgeyle aynı adla başka bir belge zaten Excel veya Word'de açık olabilir. Excel veya Word'Excel diğer tüm örneklerinin kapalı olduğundan emin olun.

### <a name="control-properties-are-lost-when-you-create-a-new-project-based-on-a-document-from-an-existing-project"></a>Mevcut projeden bir belgeyi temel alan yeni bir proje ekleyebilirsiniz, denetim özellikleri kaybolur
 Mevcut bir projeden Office yeni bir proje temel alan yeni bir proje ekleyebilirsiniz, belgede yer alan denetimlerin özellikleri yeni projeye kopyalanmaz. Önceden var olan denetimlerin özelliklerini el ile sıfırlamanız gerekir. Alternatif olarak, yeni proje oluşturmak yerine mevcut projenin bir kopyasını oluşturarak veya mevcut projeyi yeni çözüme yükerek (tasarımcıda) ve mevcut belgeden denetimleri kopyalayıp yeni belgeye yapıştırarak denetim özelliklerini koruyabilirsiniz.

### <a name="errors-when-you-create-an-excel-workbook-project-based-on-an-existing-workbook"></a>Mevcut çalışma kitabını temel alan Excel çalışma kitabı projesi oluşturma hataları
 Mevcut bir çalışma kitabını Excel yeni bir çalışma kitabı projesi oluşturmanız, aşağıdaki hataların bir birleşimini görebilir.

 Şu Excel: "Gizlilik uyarısı: Bu belgede makrolar, ActiveX denetimleri, XML genişletme paketi bilgileri veya Web bileşenleri yer almaktadır. Bunlar Belge Denetçisi tarafından kaldırılamaz kişisel bilgileri içerebilir."

 Şu Visual Studio: "Tasarımcı düzgün yüklenemedi."

 Bu hatalar, Belge Denetçisi kullanılarak kişisel bilgileri kaldırılmış bir çalışma kitabını temel alan bir proje oluşturma denemesi olabilir. Bu hatayı önlemek için projeyi oluşturmadan önce aşağıdaki adımları gerçekleştirin.

1. Çalışma kitabını Excel'de açın.

2. Bu Excel Güven Merkezi'nde açın.

3. Gizlilik **Seçenekleri sekmesinde,** Kişisel bilgileri **dosya özelliklerinden kaldır'ın kaydet onay kutusunun** işaretini kaldırın.

4. Çalışma kitabını kaydedin ve çalışma kitabını Excel.

### <a name="cannot-open-a-project-after-migration"></a>Geçiş sonrasında proje açamaz
 Bir Office çözümü Microsoft Office 2010'a geçirildikten sonra, proje yalnızca 2007 Microsoft Office sistemi yüklü olan bir geliştirme Microsoft Office açılamıyor. Aşağıdaki hataları görebilir.

 "Çözümde bir veya daha fazla proje doğru yüklenmedi. Ayrıntılar için lütfen Çıkış Penceresi bakın."

 "Bu proje türüyle ilişkili uygulama bu bilgisayara yüklenmemiş olduğundan proje oluşturulamaz. Bu proje türüyle Microsoft Office uygulamanın yüklemesi gerekir."

 Bu sorunu çözmek için *.vbproj veya* *.csproj dosyasını* düzenleyin. Bir Word projesi için HostPackage="{763FDC83-64E5-4651-AC9B-28C4FEB985A1}" yerine HostPackage="{6CE98B71-D55A-4305-87A8-0D6E368D9600}". Bir Excel projesinde HostPackage="{B284B16A-C42C-4438-BDCD-B72F4AC43CFB}" yerine HostPackage="{825100CF-0BA7-47EA-A084-DCF3308DAF74}" ifadesini kullanın. Bir Outlook projesinde HostPackage="{D2B20FF5-A6E5-47E1-90E8-463C6860CB05}" yerine HostPackage="{20A848B8-E01F-4801-962E-25DB0FF57389}".

 Alternatif olarak, geçirilen projelerin yalnızca 2010'Microsoft Office yüklü geliştirme bilgisayarlarında açıldığından emin olun.

### <a name="errors-in-upgraded-office-2003-document-level-projects-that-contain-windows-forms-controls"></a>Windows Forms Office 2003 belge düzeyi projelerinde yükseltilen hatalar
 Microsoft Office 2003 belge düzeyi projesini yükselter ve belge Windows Forms denetimlerini içeriyorsa, yükseltilen proje derleme veya çalışma zamanı hatalarına sahip olabilir. Bu sorunu önlemek için projeyi yükseltmeden önce Visual Studio 2005 Office İkinci Sürüm Çalışma Zamanı'nın geliştirme bilgisayarına yükleyin. Çalışma zamanının bu sürümü, Office İkinci Sürüm Çalışma Zamanı [(VSTO 2005 SE) (x86) için Microsoft Visual Studio 2005](https://www.microsoft.com/download/details.aspx?id=2392)Araçları'nda Microsoft İndirme Merkezi'nden yeniden dağıtılabilir paket olarak kullanılabilir.

 Projeyi yükseltmeyi bitirdikten sonra, Visual Studio 2005 Tools for Office Second Edition Runtime'ı, başka bir yazılım çözümü tarafından kullanılmazsa geliştirme bilgisayardan Office edebilirsiniz.

## <a name="use-the-designers"></a><a name="designers"></a> Tasarımcıları kullanma
 Belge düzeyindeki projelerde belge, çalışma kitabı veya çalışma sayfası tasarımcısıyla birlikte çalışıyorsanız aşağıdaki hatalarla karşılaşabilirsiniz.

### <a name="designer-failed-to-load-correctly"></a>Tasarımcı düzgün yüklenemedi
 Visual Studio durumda tasarımcı açamaz:

- Excel veya Word zaten açık ve kalıcı bir iletişim kutusu görüntüleniyor. Tasarımcıyı açmak için, word veya Word Excel de açık bir kalıcı iletişim kutusu olup ola ve açık kalıcı iletişim kutularını kapat onay kutusunu işaretleyin. Açık kalıcı iletişim kutusu yoksa, Excel veya Word yanıt vermeden önce başka bir eylem gerekebilir.

- Proje şu anda hata ayıklaması yapılıyor. Tasarımcıyı açmak için hata ayıklamayı durdurun veya bitirin.

- Geliştirme Excel VSTO yüklü olan bir eklenti, uygulama başlatıldığında bir iletişim Excel görüntüleniyor. Belge düzeyi Excel bir proje oluşturmak için önce eklentiyi devre dışı VSTO gerekir.

### <a name="controls-appear-as-black-rectangles-on-the-document-or-worksheet"></a>Denetimler belge veya çalışma sayfasında siyah dikdörtgenler olarak görünür
 Denetimleri bir belge veya çalışma sayfasında gruplarsanız Visual Studio artık tanımazsınız. Özellikler penceresinde gruplenmiş denetimlere **erişilemez** ve bunlar belge veya çalışma sayfasında siyah dikdörtgenler olarak görünür. İşlevselliklerini geri yüklemek için denetimlerin grubunu çöz gerekir.

### <a name="controls-on-a-word-template-are-not-visible-in-visual-studio"></a>Bir Word şablonunda denetimler şablonda Visual Studio
 Visual Studio tasarımcısında bir Word şablonu açarsanız, şablonda metinle aynı satırda yer alan denetimler görünür durumda olmayacaktır. Bunun nedeni, Visual Studio Word şablonlarını **Normal görünümde açmasıdır.** Denetimleri görüntülemek için Görünüm menüsüne tıklayın, **Word** Görünümü'Microsoft Office **üzerine gelin** ve ardından Yazdırma Düzeni'ne **tıklayın.**

### <a name="insert-clip-art-command-does-nothing-in-the-visual-studio-designer"></a>Küçük resim ekle komutu, küçük resim tasarımcısında Visual Studio yok
 Görsel Excel veya Word Visual Studio açık olduğunda, şeritteki Çizimler  sekmesindeki Küçük  Resim düğmesine tıklamak Küçük Resim görev **bölmesini** açmaz. Küçük resim eklemek için, Visual Studio'nin dışında ana proje klasöründeki *(\bin* klasöründeki kopya değil) çalışma kitabının veya belgenin kopyasını açmanız, küçük resmi eklemeniz ve ardından çalışma kitabını veya belgeyi kaydetmeniz gerekir.

## <a name="write-code"></a><a name="code"></a> Kod yazma
 Farklı projelerde kod yazarken aşağıdaki hatalarla Office karşılaşabilirsiniz.

### <a name="some-events-of-office-objects-are-not-accessible-when-using-c"></a>C kullanılırken Office nesnelerinin bazı olaylarına erişilemiyor\#
 Bazı durumlarda, visual C# projesinde bir Office birincil birlikte çalışma derlemesi (PIA) türünün belirli bir örneğinin olayına erişmeye çalışsanız aşağıdakine benzer bir derleyici hatasıyla karşınıza çıktı.

 "'Microsoft arasındaki belirsizlik. Office. Birlikte çalış -abilir -lik. Excel._Application.NewWorkbook' ve 'Microsoft. Office. Birlikte çalış -abilir -lik. Excel. AppEvents_Event.NewWorkbook'"

 Bu hata, nesnenin başka bir özelliği veya yöntemiyle aynı adı alan bir olaya erişmeye çalıştığı anlamına gelir. Olayına erişmek için nesnesini olay arabirimine *attırabilirsiniz.*

 Office Olaylara sahip PIA türleri iki arabirim kullanır: tüm özelliklere ve yöntemlere sahip çekirdek arabirim ve nesne tarafından ortaya konulan olayları içeren bir olay arabirimi. Bu olay arabirimleri, ve gibi *_Event* event *n* _Event adlandırma kuralı nesne adını <xref:Microsoft.Office.Interop.Excel.AppEvents_Event> <xref:Microsoft.Office.Interop.Word.ApplicationEvents2_Event> kullanır. Bir nesnede bulmasını beklediğiniz bir olaya erişe değil, nesneyi olay arabirimine atabilirsiniz.

 Örneğin, <xref:Microsoft.Office.Interop.Excel.Application> nesnelerin bir olayı <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook> ve özelliği <xref:Microsoft.Office.Interop.Excel._Application.NewWorkbook%2A> vardır. Olayı işlemek <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook> için <xref:Microsoft.Office.Interop.Excel.Application> arabirimine <xref:Microsoft.Office.Interop.Excel.AppEvents_Event> atarak. Aşağıdaki kod örneğinde, bunu belge düzeyi projesinde nasıl gerçekleştirebilirsiniz? Excel.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingExcelCS/ThisWorkbook.cs" id="Snippet1":::

 Office PIA'larında olay arabirimleri hakkında daha fazla bilgi için bkz. Birincil birlikte çalışma derlemeleri için [Office arabirimlere genel bakış.](/previous-versions/office/office-12//ms247299(v=office.12))

### <a name="cannot-reference-office-pia-classes-in-projects-that-target-the-net_v40_short-or-the-net_v45"></a>veya Office projelerde PIA sınıflarına [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] başvurulamaz[!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]
 veya hedefli [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] projelerde, bir piA'da tanımlanan bir sınıfa [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] Office kod varsayılan olarak derlanmaz. PIA'larda sınıflar, ve gibi adlandırma kuralı *objectname* Sınıfını <xref:Microsoft.Office.Interop.Word.DocumentClass> <xref:Microsoft.Office.Interop.Excel.WorkbookClass> kullanır. Örneğin, bir Word VSTO Eklenti projesinden aşağıdaki kod derlanmaz.

```vb
Dim document As Word.DocumentClass = Globals.ThisAddIn.Application.ActiveDocument
```

```csharp
Word.DocumentClass document = (Word.DocumentClass) Globals.ThisAddIn.Application.ActiveDocument;
```

 Bu kod aşağıdaki derleme hatalarına neden olur:

- Visual Basic: "Derlemesi No-PIA modu kullanılarak bağlanarak 'DocumentClass' sınıfına başvuruya izin verilmiyor."

- Visual C#: "'Microsoft.Office.Interop.Word.DocumentClass' birlikte çalışma türü katıştırılamaz. Bunun yerine uygun arabirimi kullanın."

  Bu hatayı çözmek için kodu ilgili arabirime başvurarak değiştirebilirsiniz. Örneğin, bir nesneye başvuru <xref:Microsoft.Office.Interop.Word.DocumentClass> yapmak yerine arabirimin bir örneğine <xref:Microsoft.Office.Interop.Word.Document> başvurun.

```vb
Dim document As Word.Document = Globals.ThisAddIn.Application.ActiveDocument
```

```csharp
Word.Document document = Globals.ThisAddIn.Application.ActiveDocument;
```

 veya hedefini hedef alan projeler, varsayılan olarak tüm birlikte çalışma türlerini Office [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] otomatik olarak eklenir. Katıştırılmış birlikte çalışma türleri özelliği sınıflarla değil yalnızca arabirimlerle çalışma nedeniyle bu derleme hatası oluşur. Office PIA'larında arabirimler ve sınıflar hakkında daha fazla bilgi için bkz. Birincil birlikte çalışma derlemeleri için [Office arabirimlere genel bakış.](/previous-versions/office/office-12/ms247299(v=office.12)) Office projelerinde katıştırılmış birlikte çalışma türleri özelliği hakkında daha fazla bilgi için bkz. Office [oluşturma.](../vsto/designing-and-creating-office-solutions.md)

### <a name="references-to-office-classes-are-not-recognized"></a>Sınıflara Office başvurular tanınmıyor
 Uygulama gibi bazı sınıf adları ve gibi birden çok ad alanı <xref:Microsoft.Office.Interop.Word> <xref:System.Windows.Forms> içindedir. Bu nedenle, proje **şablonlarının** üst kısmında yer alan Using deyimini içeri aktarmalar, bir /  shorthand qualifying sabiti içerir, örneğin:

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs" id="Snippet2":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb" id="Snippet2":::

 deyimini kullanan İçeri Aktarmalar'ın bu kullanımı, Word veya Office niteleyicisi ile Excel  /  ayırmanızı gerektirir, örneğin:

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs" id="Snippet3":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb" id="Snippet3":::

 Uygun olmayan bir bildirim kullanırsanız hata alır, örneğin:

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs" id="Snippet4":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb" id="Snippet4":::

 Word veya Excel ad alanını içeri aktardınız ve içindeki tüm sınıflara erişiminiz olmasına rağmen ad alanı belirsizliklerini kaldırmak için word veya Excel tüm türleri tam olarak uygun hale Excel gerekir.

## <a name="build-projects"></a><a name="building"></a> Projeleri derleme
 Yeni projeler derleme sırasında aşağıdaki hatalarla Office karşılaşabilirsiniz.

### <a name="cannot-build-a-document-level-project-that-is-based-on-a-document-with-restricted-permissions"></a>Kısıtlı izinlere sahip bir belgeyi temel alan belge düzeyinde proje derleme
 Visual Studio kısıtlı izinlere sahipse belge düzeyinde projeler derlemeniz yasaktır. Projeniz kısıtlı izinlere sahip bir belge içeriyorsa proje derlanmaz ve Hata Listesi penceresinde aşağıdaki **iletiyi alırsınız.**

 "Özelleştirme eklenemedi."

 Kısıtlı izinlere sahip bir belge eklemek için, çözümü geliştirirken ve hazırlarken kısıtlanmamış bir belge kullanın. Ardından, çözümü yayımladikten sonra belgeye yayımlama konumda kısıtlı izinleri uygulayabilirsiniz.

### <a name="compiler-errors-occur-after-a-namedrange-control-is-deleted"></a>NamedRange denetimi silindikten sonra derleyici hataları oluşuyor
 Tasarımcıda etkin çalışma sayfası olmayan bir çalışma sayfasından denetim silersiniz, otomatik olarak oluşturulan kod projenize kaldırılamaz ve derleyici <xref:Microsoft.Office.Tools.Excel.NamedRange> hataları oluşabilir. Kodun kaldırılmış olduğundan emin olmak için denetimi içeren çalışma sayfasını seçerek denetimi silmeden önce etkin çalışma sayfası <xref:Microsoft.Office.Tools.Excel.NamedRange> olarak seçmeniz gerekir. Denetimi sildikten sonra otomatik olarak oluşturulan kod silinmezse, çalışma sayfasını etkinleştirerek ve çalışma sayfasının değiştirilmiş olarak işaretlenene kadar değişiklik yaparak tasarımcının kodu silmesini silebilirsiniz. Projeyi yeniden 7.000.000'e kadar olan tüm kodlar kaldırılır.

## <a name="debug-projects"></a><a name="debugging"></a> Projelerde hata ayıklama
 Projelerde hata ayıklarken aşağıdaki hatalarla Office karşılaşabilirsiniz.

### <a name="prompt-to-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>Geliştirme bilgisayarına bir çözüm yayımlar ve yüklenirken kaldırma istemi görüntülenir
 Bir çözümde hata Office ayıklarsanız aşağıdaki hatayı alabilirsiniz.

 "Başka bir sürüm şu anda yüklü olduğundan ve bu konumdan yükseltileyemeye sahip olduğundan özelleştirme yükilemiyor."

 Bu hata, geliştirme bilgisayarınızda daha önce Office çözümü yayımlamış ve yüklemiş olduğunu gösterir. İletinin görünmesini önlemek için, çözümde hata ayıklamadan önce çözümü bilgisayarda yüklü programlar listesinden kaldırın. Alternatif olarak, yayımlanan çözümün yüklemesini test etmek için geliştirme bilgisayarınızda başka bir kullanıcı hesabı oluşturabilirsiniz.

### <a name="document-level-projects-created-at-unc-network-locations-do-not-run-from-visual-studio"></a>UNC ağ konumlarında oluşturulan belge düzeyi projeler, ağ Visual Studio
 Excel veya Word için UNC ağ konumu için belge düzeyinde bir proje ekleyebilirsiniz. Belgenin konumunu Excel veya Word'de güvenilir konumlar listesine eklemeniz gerekir. Aksi takdirde, Visual Studio'da projeyi çalıştırmaya veya projenin hata ayıklaması yapmaya çalışsanız özelleştirme Visual Studio. Güvenilen konumlar hakkında daha fazla bilgi için [bkz. Belgelere güven izni ver.](../vsto/granting-trust-to-documents.md)

### <a name="threads-are-not-stopped-correctly-after-debugging"></a>Hata ayıklamadan sonra iş parçacıkları doğru durdurulamıyor
 Office projelerini Visual Studio hata ayıklayıcının programı doğru kapatmasını sağlayan bir iş parçacığı adlandırma kuralını izleyin. Çözümünüzde iş parçacıkları sanız, hata ayıklamayı durduran bu iş VSTA_ doğru iş parçacıklarının iş olduğundan emin olmak için her bir iş parçacığını ön eke sahip olarak adlandırabilirsiniz. Örneğin, bir ağ olayı için beklemesi gereken bir iş parçacığının `Name` özelliğini VSTA_NetworkListener. 

### <a name="cannot-run-or-debug-any-office-solution-on-the-development-computer"></a>Geliştirme bilgisayarda herhangi bir Office çözümü çalıştıramaz veya hata ayıklayamaz
 Geliştirme bilgisayarınızda bir Office proje çalıştıramaz veya geliştireyebilirsiniz, aşağıdaki hata iletisini alabilirsiniz.

 "Uygulama etki alanı oluşturulamay nedeniyle özelleştirme yüklenemedi."

 Visual Studio çözümlerini yüklemeden önce derlemeleri önbelleğe .NET Framework için Fusion'Office kullanır. Bu Visual Studio Fusion önbelleğine yazamaya devam etmek ve yeniden denemek. Daha fazla bilgi için [bkz. Gölge kopya derlemeleri.](/dotnet/framework/app-domains/shadow-copy-assemblies)

### <a name="error-when-stopping-the-debugger-in-a-document-level-project-after-using-edit-and-continue"></a>Düzenle ve Devam'ı kullanmanın ardından belge düzeyi projesinde hata ayıklayıcı durduruluyorken hata oluştu
 Proje kesme **modundayken** Excel veya Word belge düzeyi projesinde kodda değişiklik yapmak için Düzenle ve Devam'ı kullanırsanız, hata ayıklayıcıyı daha sonra durdurursanız aşağıdaki hata iletisinin yer alan bir iletişim kutusuyla karşılaşabilirsiniz. 

 "Sürecin geçerli durumda sonlandırıcısı, veri kaybı ve sistem kararsızlığı da dahil olmak üzere, insağlanmamış sonuçlara neden olabilir."

 İletişim kutusunda **Evet veya** **Hayır'a** tıklar Visual Studio, Excel veya Word işlemini sonlandırılır ve hata ayıklayıcıyı durdurur. Bu iletişim kutusunu görüntülemeden projede hata ayıklamayı durdurmak için hata ayıklayıcıyı Excel veya Word'den doğrudan Visual Studio.

## <a name="see-also"></a>Ayrıca bkz.
- [Office sorunlarını giderme](../vsto/troubleshooting-office-solutions.md)
- [Çözüm Office sorunlarını giderme](../vsto/troubleshooting-office-solution-security.md)
- [Çözüm Office sorunlarını giderme](../vsto/troubleshooting-office-solution-deployment.md)
- [Visual Studio giderme](/troubleshoot/visualstudio/welcome-visual-studio/)
