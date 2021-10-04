---
title: Office çözümlerinde hata giderme
description: Visual Studio Microsoft Office çözümleri geliştirirken oluşabilecek hataların nasıl giderileceği hakkında bilgi edinin.
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
ms.openlocfilehash: 7b1059f1771445aba63de0d461a453dfe26a32c0
ms.sourcegitcommit: 541871db9065c4fb1b21c24f980c563991b183c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129431152"
---
# <a name="troubleshoot-errors-in-office-solutions"></a>Office çözümlerinde hata giderme
  Visual Studio Office çözüm geliştirirken aşağıdaki görevleri gerçekleştirirken sorunlarla karşılaşabilirsiniz:

- [Projeleri oluşturun, yükseltin ve açın](#creating)

- [Tasarımcıları kullanma](#designers)

- [Kod yazma](#code)

- [Yapı projeleri](#building)

- [Hata ayıklama projeleri](#debugging)

## <a name="create-upgrade-and-open-projects"></a><a name="creating"></a> Projeleri oluşturun, yükseltin ve açın
 Office projeleri oluştururken veya açtığınızda aşağıdaki hatalarla karşılaşabilirsiniz.

### <a name="the-project-cannot-be-created"></a>Proje oluşturulamıyor
 bir Office projesi oluşturmaya veya açmaya çalışırken bir hata oluştu, ancak Visual Studio nedeni belirlemede yeterli bilgi yoktu. projenizi kapatmayı, Visual Studio çıkmadan ve yeniden başlatmayı deneyin.

 belge düzeyi projesi oluşturmaya çalışıyorsanız, yeni projedeki belgeyle aynı ada sahip başka bir belge Excel veya Word 'de zaten açık olabilir. tüm Excel veya sözcük örneklerinin kapalı olduğundan emin olun.

### <a name="control-properties-are-lost-when-you-create-a-new-project-based-on-a-document-from-an-existing-project"></a>Mevcut bir projeden bir belgeyi temel alan yeni bir proje oluşturduğunuzda denetim özellikleri kaybolur
 varolan bir projeden bir belgeyi temel alan yeni bir Office projesi oluşturursanız, belgedeki tüm denetimlerin özellikleri yeni projeye kopyalanmaz. Önceden varolan denetimlerin özelliklerini el ile sıfırlamanız gerekir. Alternatif olarak, yeni bir proje oluşturmak yerine mevcut projenin bir kopyasını oluşturarak veya var olan projeyi yeni çözüme yükleyerek (tasarımcıda) ve denetimleri kopyalayıp yeni belgeye yapıştırarak denetim özelliklerini koruyabilirsiniz.

### <a name="errors-when-you-create-an-excel-workbook-project-based-on-an-existing-workbook"></a>var olan bir çalışma kitabına göre Excel çalışma kitabı projesi oluşturduğunuzda oluşan hatalar
 var olan bir çalışma kitabına göre yeni bir Excel çalışma kitabı projesi oluşturursanız, aşağıdaki hataların bir bileşimini görebilirsiniz.

 Excel: "gizlilik uyarısı: bu belge makrolar, ActiveX denetimleri, XML genişletme paketi bilgileri veya Web bileşenleri içerir. Bunlar belge denetçisi tarafından kaldırılamayan kişisel bilgileri içerebilir. "

 Visual Studio: "tasarımcı doğru şekilde yüklenemedi."

 Bu hatalar, kendi kişisel bilgileri olan bir çalışma kitabını temel alan bir projeyi belge denetçisi kullanılarak oluşturmaya çalıştığınızda meydana gelir. Bu hatayı önlemek için, projeyi oluşturmadan önce aşağıdaki adımları gerçekleştirin.

1. Çalışma kitabını Excel'de açın.

2. Excel, güven merkezini açın.

3. **Gizlilik seçenekleri** sekmesinde, **kaydederken kişisel bilgileri dosya özelliklerinden kaldır** onay kutusunun işaretini kaldırın.

4. Çalışma kitabını kaydedin ve Excel kapatın.

### <a name="cannot-open-a-project-after-migration"></a>Geçişten sonra proje açılamaz
 bir Office çözümü Microsoft Office 2010 ' e geçirildikten sonra, proje yalnızca 2007 Microsoft Office sistemi yüklü olan bir geliştirme bilgisayarında açılamaz. Aşağıdaki hataları görebilirsiniz.

 "Çözümdeki bir veya daha fazla proje doğru şekilde yüklenmedi. Ayrıntılar için lütfen Çıkış Penceresi bakın. "

 "Bu proje türüyle ilişkili uygulama bu bilgisayarda yüklü olmadığından Proje oluşturulamıyor. bu proje türüyle ilişkilendirilmiş Microsoft Office uygulamayı yüklemelisiniz. "

 Bu sorunu çözmek için *. vbproj* veya *. csproj* dosyasını düzenleyin. Bir Word projesi için HostPackage = "{763FDC83-64E5-4651-AC9B-28C4FEB985A1}" öğesini HostPackage = "{6CE98B71-D55A-4305-87A8-0D6E368D9600}" ile değiştirin. bir Excel projesi için hostpackage = "{B284B16A-C42C-4438-bdcd-B72F4AC43CFB}" öğesini hostpackage = "{825100cf-0ba7-47ea-a084-dcf3308dadf74}" ile değiştirin. bir Outlook projesi için hostpackage = "{D2B20FF5-A6E5-47E1-90E8-463C6860CB05}" öğesini hostpackage = "{20a848b8-e01f-4801-962e-25db0ff57389}" ile değiştirin.

 alternatif olarak, geçirilen projelerin yalnızca Microsoft Office 2010 zaten yüklü olan geliştirme bilgisayarlarında açıldığından emin olun.

### <a name="errors-in-upgraded-office-2003-document-level-projects-that-contain-windows-forms-controls"></a>yükseltilen Office 2003 Windows Forms denetimleri içeren belge düzeyi projelerdeki hatalar
 bir Microsoft Office 2003 belge düzeyi projesi yükseltirseniz ve belge Windows Forms denetimleri içeriyorsa, yükseltilen proje derleme veya çalışma zamanı hatalarına sahip olabilir. bu sorundan kaçınmak için, projeyi yükseltmeden önce geliştirme bilgisayarında Office ikinci sürüm çalışma zamanı için Visual Studio 2005 araçlarını yükleyin. çalışma zamanının bu sürümü, Office ikinci sürüm çalışma zamanı (VSTO 2005 SE) (x86) için Microsoft Visual Studio 2005 araçlarında Microsoft indirme merkezi 'nden yeniden dağıtılabilir bir paket olarak sunulmaktadır.

 projeyi yükseltmeyi tamamladıktan sonra, başka bir Office çözümü tarafından kullanılmıyorsa, Office ikinci sürüm çalışma zamanı için Visual Studio 2005 araçlarını geliştirme bilgisayarından kaldırabilirsiniz.

## <a name="use-the-designers"></a><a name="designers"></a> Tasarımcıları kullanma
 Belge düzeyi projelerde belge, çalışma kitabı veya çalışma sayfası tasarımcısı ile çalışırken aşağıdaki hatalarla karşılaşabilirsiniz.

### <a name="designer-failed-to-load-correctly"></a>Tasarımcı doğru şekilde yüklenemedi
 Visual Studio aşağıdaki durumlarda tasarımcıyı açamıyor:

- Excel veya Word zaten açık ve kalıcı iletişim kutusu görüntülüyor. tasarımcıyı açmak için, Excel veya Word 'ün kalıcı iletişim kutusu açık olup olmadığını denetleyin ve açık kalıcı iletişim kutularını kapatın. açık kalıcı iletişim kutusu yoksa, Excel veya sözcük yanıt vermeden önce bazı başka eylemler gerekebilir.

- Projede Şu anda hata ayıklıyor. Tasarımcıyı açmak için, hata ayıklamayı durdurun veya sona erdirin.

- geliştirme bilgisayarında yüklü bir Excel VSTO eklentisi, Excel başladığında bir iletişim kutusu görüntülüyor. Excel belge düzeyi projesi oluşturmak için, önce VSTO eklentisini devre dışı bırakmanız gerekir.

### <a name="controls-appear-as-black-rectangles-on-the-document-or-worksheet"></a>Denetimler belge veya çalışma sayfasında siyah dikdörtgenler olarak görünür
 denetimleri bir belge veya çalışma sayfasında gruplandırdıysanız, Visual Studio artık denetimleri tanımaz. Gruplanmış denetimlere **Özellikler** penceresinden erişilemez ve belge veya çalışma sayfasında siyah dikdörtgenler olarak görünürler. İşlevlerini geri yüklemek için denetimlerin grubunu çözmeniz gerekir.

### <a name="controls-on-a-word-template-are-not-visible-in-visual-studio"></a>Bir Word şablonundaki Denetimler Visual Studio görünmüyor
 Visual Studio tasarımcısında bir Word şablonu açarsanız, şablonda metinle birlikte olmayan denetimler görünür olmayabilir. bunun nedeni Visual Studio Word şablonlarının **Normal** görünümde açılmasıdır. denetimleri görüntülemek için **görünüm** menüsüne tıklayın, **Microsoft Office Word görünümü** ' ne gelin ve ardından **yazdırma düzeni**' ne tıklayın.

### <a name="insert-clip-art-command-does-nothing-in-the-visual-studio-designer"></a>küçük resim ekle komutu Visual Studio tasarımcısında hiçbir şey yapmaz
 Visual Studio tasarımcısında Excel veya Word açıkken, şeritteki **çizimler** sekmesinde bulunan **clip art** düğmesine tıklamak, **küçük resim** görev bölmesini açmaz. küçük resim eklemek için, ana proje klasöründe bulunan ( *\bin* klasöründe olan kopya değil) çalışma kitabının veya belgenin kopyasını Visual Studio, klip resmini ekleyin ve ardından çalışma kitabını veya belgeyi kaydetmelisiniz.

## <a name="write-code"></a><a name="code"></a> Kod Yaz
 Office projelerine kod yazdığınızda aşağıdaki hatalarla karşılaşabilirsiniz.

### <a name="some-events-of-office-objects-are-not-accessible-when-using-c"></a>C kullanırken Office nesnelerinin bazı olaylarına erişilemez\#
 bazı durumlarda, bir Visual C# projesinde Office birincil birlikte çalışma derlemesi (pıa) türünün bir örneğinin belirli bir olayına erişmeye çalıştığınızda aşağıdakine benzer bir derleyici hatası görebilirsiniz.

 ' Microsoft arasında belirsizlik. Office. Derlemesinde. Excel ._Application. newworkbook ' ve ' Microsoft. Office. Derlemesinde. Excel. AppEvents_Event. NewWorkbook ' "

 Bu hata, nesnenin başka bir özelliği veya yöntemiyle aynı ada sahip bir olaya erişmeye çalıştığınız anlamına gelir. Olaya erişmek için, nesneyi *olay arabirimine* atamalısınız.

 Office Olay içeren PIA türleri iki arabirim uygular: tüm özellikleri ve yöntemleri içeren bir çekirdek arabirim ve nesne tarafından açığa çıkarılan olayları içeren bir olay arabirimi. Bu olay arabirimleri, ve gibi, *ObjectName* olayları *n* _Event adlandırma kuralını kullanır <xref:Microsoft.Office.Interop.Excel.AppEvents_Event> <xref:Microsoft.Office.Interop.Word.ApplicationEvents2_Event> . Bir nesne üzerinde bulmayı düşündüğünüz bir olaya erişemiyorsanız, nesneyi olay arabirimine atayın.

 Örneğin, <xref:Microsoft.Office.Interop.Excel.Application> nesneler bir <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook> olaya ve bir özelliğe sahiptir <xref:Microsoft.Office.Interop.Excel._Application.NewWorkbook%2A> . Olayı işlemek için <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook> , <xref:Microsoft.Office.Interop.Excel.Application> <xref:Microsoft.Office.Interop.Excel.AppEvents_Event> arabirimini arabirimine atayın. Aşağıdaki kod örneği, Excel için belge düzeyi bir projede bunun nasıl yapılacağını gösterir.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingExcelCS/ThisWorkbook.cs" id="Snippet1":::

 Office pıa 'leri içindeki olay arabirimleri hakkında daha fazla bilgi için, bkz. [Office birincil birlikte çalışma derlemelerinde sınıflara ve arabirimlere genel bakış](/previous-versions/office/office-12//ms247299(v=office.12)).

### <a name="cannot-reference-office-pia-classes-in-projects-that-target-the-net_v40_short-or-the-net_v45"></a>veya öğesini hedefleyen projelerde Office pıa sınıflarına başvuramaz [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)][!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]
 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]veya [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] ' i hedefleyen projelerde, bir Office pıa ' de tanımlanan bir sınıfa başvuruda bulunan kod, varsayılan olarak derlenmeyecektir. PIA 'ler içindeki sınıflar, ve gibi adlandırma kuralı *ObjectName* sınıfını kullanır <xref:Microsoft.Office.Interop.Word.DocumentClass> <xref:Microsoft.Office.Interop.Excel.WorkbookClass> . örneğin, bir Word VSTO eklentisi projesinin aşağıdaki kodu derlenmeyecektir.

```vb
Dim document As Word.DocumentClass = Globals.ThisAddIn.Application.ActiveDocument
```

```csharp
Word.DocumentClass document = (Word.DocumentClass) Globals.ThisAddIn.Application.ActiveDocument;
```

 Bu kod aşağıdaki derleme hatalarına neden olur:

- Visual Basic: "' documentclass ' sınıfına yönelik başvuruya, derlemesi hiçbir pıa modu kullanılarak bağlandığında izin verilmez."

- Visual C#: "birlikte çalışma türü" Microsoft. Office. Interop. Word. DocumentClass ' Katıştırılamaz. Bunun yerine uygulanabilir arabirimi kullanın. "

  Bu hatayı çözmek için, kodu bunun yerine karşılık gelen arabirime başvuracak şekilde değiştirin. Örneğin, bir nesneye başvurmak yerine <xref:Microsoft.Office.Interop.Word.DocumentClass> , <xref:Microsoft.Office.Interop.Word.Document> bunun yerine arabirimin örneğine başvurun.

```vb
Dim document As Word.Document = Globals.ThisAddIn.Application.ActiveDocument
```

```csharp
Word.Document document = Globals.ThisAddIn.Application.ActiveDocument;
```

 veya öğesini hedefleyen projeler [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , varsayılan olarak Office pıa 'lerden tüm birlikte çalışma türlerini otomatik olarak katıştırın. Bu derleme hatası, gömülü birlikte çalışma türleri özelliği sınıflarla değil arabirimlerle birlikte çalışacağından oluşur. Office pıa 'ları içindeki arabirimler ve sınıflar hakkında daha fazla bilgi için bkz. [Office birincil birlikte çalışma derlemelerindeki sınıflara ve arabirimlere genel bakış](/previous-versions/office/office-12/ms247299(v=office.12)). Office projelerindeki gömülü birlikte çalışma türleri özelliği hakkında daha fazla bilgi için bkz. [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md).

### <a name="references-to-office-classes-are-not-recognized"></a>Office sınıflarına başvurular tanınmıyor
 Örneğin, uygulama gibi bazı sınıf adları, ve gibi birden çok ad alanında <xref:Microsoft.Office.Interop.Word> bulunur <xref:System.Windows.Forms> . Bu nedenle, proje **şablonlarının** üst kısmında yer alan Using deyimini içeri aktarmalar, bir /  shorthand qualifying sabiti içerir, örneğin:

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs" id="Snippet2":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb" id="Snippet2":::

 deyimini kullanarak İçeri Aktarmalar'ın bu kullanımı, word veya Office niteleyicisi ile Excel  /  ayırmanızı gerektirir, örneğin:

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs" id="Snippet3":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb" id="Snippet3":::

 Uygun olmayan bir bildirim kullanırsanız hata alır, örneğin:

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs" id="Snippet4":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb" id="Snippet4":::

 Word veya Excel ad alanını içeri aktardınız ve içindeki tüm sınıflara erişiminiz olmasına rağmen ad alanı belirsizliklerini kaldırmak için Word veya Excel tüm türleri tam olarak uygun hale Excel gerekir.

## <a name="build-projects"></a><a name="building"></a> Projeleri derleme
 Yeni projeler derleme sırasında aşağıdaki hatalarla Office karşılaşabilirsiniz.

### <a name="cannot-build-a-document-level-project-that-is-based-on-a-document-with-restricted-permissions"></a>Kısıtlı izinlere sahip bir belgeyi temel alan belge düzeyinde proje derleme
 Visual Studio kısıtlı izinlere sahipse belge düzeyinde projeler derlemez. Projeniz kısıtlı izinlere sahip bir belge içeriyorsa proje derlanmaz ve Hata Listesi penceresinde aşağıdaki **iletiyi alırsınız.**

 "Özelleştirme eklenemedi."

 Kısıtlı izinlere sahip bir belge eklemek için, çözümü geliştirirken ve hazırlarken kısıtlanmamış bir belge kullanın. Ardından, çözümü yayımladikten sonra belgeye yayımlama konumda kısıtlı izinleri uygulayabilirsiniz.

### <a name="compiler-errors-occur-after-a-namedrange-control-is-deleted"></a>NamedRange denetimi silindikten sonra derleyici hataları oluşuyor
 Tasarımcıda etkin çalışma sayfası olmayan bir çalışma sayfasından denetim silersiniz, otomatik olarak oluşturulan kod projenize kaldırılamaz ve derleyici <xref:Microsoft.Office.Tools.Excel.NamedRange> hataları oluşabilir. Kodun kaldırılmış olduğundan emin olmak için denetimi içeren çalışma sayfasını her zaman seçerek denetimi silmeden önce etkin çalışma <xref:Microsoft.Office.Tools.Excel.NamedRange> sayfası olarak seçmeniz gerekir. Denetimi sildikten sonra otomatik olarak oluşturulan kod silinmezse, çalışma sayfasını etkinleştirerek ve çalışma sayfasının değiştirilmiş olarak işaretlenene kadar değişiklik yaparak tasarımcının kodu silmesini silebilirsiniz. Projeyi yeniden 7.000.000'e kadar olan tüm kodlar kaldırılır.

## <a name="debug-projects"></a><a name="debugging"></a> Projelerde hata ayıklama
 Projelerde hata ayıklarken aşağıdaki hatalarla Office karşılaşabilirsiniz.

### <a name="prompt-to-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>Geliştirme bilgisayarına bir çözüm yayımlar ve yüklenirken kaldırma istemi görüntülenir
 Bir çözümde hata Office ayıklarsanız aşağıdaki hatayı alabilirsiniz.

 "Başka bir sürüm şu anda yüklü olduğundan ve bu konumdan yükseltileyene kadar özelleştirme yükilemiyor."

 Bu hata, geliştirme bilgisayarınızda daha önce Office çözümü yayımlamış ve yüklemiş olduğunu gösterir. İletinin görünmesini önlemek için, çözümde hata ayıklamadan önce çözümü bilgisayarda yüklü programlar listesinden kaldırın. Alternatif olarak, yayımlanan çözümün yüklemesini test etmek için geliştirme bilgisayarınızda başka bir kullanıcı hesabı oluşturabilirsiniz.

### <a name="document-level-projects-created-at-unc-network-locations-do-not-run-from-visual-studio"></a>UNC ağ konumlarında oluşturulan belge düzeyi projeler ağdan Visual Studio
 Excel veya Word için UNC ağ konumu için belge düzeyinde bir proje oluşturmanız gerekirse, belgenin konumunu Excel veya Word'de güvenilen konumlar listesine eklemeniz gerekir. Aksi takdirde, Visual Studio'da projeyi çalıştırmaya veya projenin hata ayıklaması yapmaya çalışsanız özelleştirme Visual Studio. Güvenilen konumlar hakkında daha fazla bilgi için [bkz. Belgelere güven izni ver.](../vsto/granting-trust-to-documents.md)

### <a name="threads-are-not-stopped-correctly-after-debugging"></a>Hata ayıklamadan sonra iş parçacıkları doğru durdurulamıyor
 Office projelerini Visual Studio hata ayıklayıcının programı doğru kapatmasını sağlayan bir iş parçacığı adlandırma kuralını izleyin. Çözümünüzde iş parçacıkları sanız, hata ayıklamayı durdursanız bu iş VSTA_ doğru iş parçacıklarının iş olduğundan emin olmak için her bir iş parçacığını ön ekini kullanarak adlandırabilirsiniz. Örneğin, bir ağ olayı için beklemesi gereken bir iş parçacığının `Name` özelliğini VSTA_NetworkListener. 

### <a name="cannot-run-or-debug-any-office-solution-on-the-development-computer"></a>Geliştirme bilgisayarda herhangi bir Office çözümü çalıştıramaz veya hata ayıklayamaz
 Geliştirme bilgisayarınızda bir Office proje çalıştıramaz veya geliştireyebilirsiniz, aşağıdaki hata iletisini alabilirsiniz.

 "Uygulama etki alanı oluşturulamay olduğundan özelleştirme yüklenemedi."

 Visual Studio çözümlerini yüklemeden önce derlemeleri önbelleğe .NET Framework derleme yükleyicisi Fusion'Office kullanır. Fusion önbelleğine Visual Studio emin olmak ve yeniden denemek. Daha fazla bilgi için [bkz. Gölge kopya derlemeleri.](/dotnet/framework/app-domains/shadow-copy-assemblies)

### <a name="error-when-stopping-the-debugger-in-a-document-level-project-after-using-edit-and-continue"></a>Düzenle ve Devam'ı kullanmanın ardından belge düzeyi projesinde hata ayıklayıcı durduruluyorken hata oluştu
 Proje kesme **modundayken** Excel veya Word'e yönelik belge düzeyi projelerde kodda değişiklik yapmak için Düzenle ve Devam'ı kullanırsanız, hata ayıklayıcıyı daha sonra durdurursanız aşağıdaki hata iletisinin yer alan bir iletişim kutusuyla karşılaşabilirsiniz. 

 "Sürecin geçerli durumda sonlandırıcısı, veri kaybı ve sistem kararsızlığı da dahil olmak üzere, insağlanmamış sonuçlara neden olabilir."

 İletişim kutusunda **Evet veya** **Hayır'a** tıklar Visual Studio, Excel veya Word işlemini sonlandırılır ve hata ayıklayıcıyı durdurur. Bu iletişim kutusunu görüntülemeden projede hata ayıklamayı durdurmak için, Excel veya Word'den çıkış yapmak yerine doğrudan hata ayıklayıcıyı Visual Studio.

## <a name="see-also"></a>Ayrıca bkz.
- [Sorun Office giderme](../vsto/troubleshooting-office-solutions.md)
- [Çözüm Office sorunlarını giderme](../vsto/troubleshooting-office-solution-security.md)
- [Çözüm Office sorunlarını giderme](../vsto/troubleshooting-office-solution-deployment.md)
- [Visual Studio giderme](/troubleshoot/visualstudio/welcome-visual-studio/)
