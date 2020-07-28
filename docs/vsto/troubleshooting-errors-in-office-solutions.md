---
title: Office çözümlerinde hata giderme sorunları
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4f0d4eee6714d29a1609f6f6531ab18c132d5527
ms.sourcegitcommit: 9a7fb8556a5f3dbb4459122fefc7e7a8dfda753a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234698"
---
# <a name="troubleshoot-errors-in-office-solutions"></a>Office çözümlerinde hata giderme sorunları
  Visual Studio 'da Office çözümleri geliştirirken aşağıdaki görevleri gerçekleştirirken sorunlarla karşılaşabilirsiniz:

- [Projeleri oluşturun, yükseltin ve açın](#creating)

- [Tasarımcıları kullanma](#designers)

- [Kod yazma](#code)

- [Yapı projeleri](#building)

- [Hata ayıklama projeleri](#debugging)

## <a name="create-upgrade-and-open-projects"></a><a name="creating"></a>Projeleri oluşturun, yükseltin ve açın
 Office projelerini oluştururken veya açtığınızda aşağıdaki hatalarla karşılaşabilirsiniz.

### <a name="the-project-cannot-be-created"></a>Proje oluşturulamıyor
 Bir Office projesi oluşturmaya veya açmaya çalışırken bir hata oluştu, ancak Visual Studio nedenini öğrenmek için yeterli bilgi yoktu. Projenizi kapatmayı, Visual Studio 'dan çıkmak ve yeniden başlatmayı deneyin.

 Belge düzeyi projesi oluşturmaya çalışıyorsanız, yeni projedeki belgeyle aynı ada sahip başka bir belge zaten Excel veya Word 'de açık olabilir. Tüm Excel veya Word örneklerinin kapalı olduğundan emin olun.

### <a name="control-properties-are-lost-when-you-create-a-new-project-based-on-a-document-from-an-existing-project"></a>Mevcut bir projeden bir belgeyi temel alan yeni bir proje oluşturduğunuzda denetim özellikleri kaybolur
 Varolan bir projeden bir belgeyi temel alan yeni bir Office projesi oluşturursanız, belgedeki denetimlerin özellikleri yeni projeye kopyalanmaz. Önceden varolan denetimlerin özelliklerini el ile sıfırlamanız gerekir. Alternatif olarak, yeni bir proje oluşturmak yerine mevcut projenin bir kopyasını oluşturarak veya var olan projeyi yeni çözüme yükleyerek (tasarımcıda) ve denetimleri kopyalayıp yeni belgeye yapıştırarak denetim özelliklerini koruyabilirsiniz.

### <a name="errors-when-you-create-an-excel-workbook-project-based-on-an-existing-workbook"></a>Var olan bir çalışma kitabına dayalı bir Excel çalışma kitabı projesi oluşturduğunuzda oluşan hatalar
 Var olan bir çalışma kitabını temel alan yeni bir Excel çalışma kitabı projesi oluşturursanız, aşağıdaki hataların bir bileşimini görebilirsiniz.

 Excel 'den: "Gizlilik Uyarısı: Bu belge makrolar, ActiveX denetimleri, XML genişletme paketi bilgileri veya Web bileşenleri içerir. Bunlar belge denetçisi tarafından kaldırılamayan kişisel bilgileri içerebilir. "

 Visual Studio 'dan: "tasarımcı doğru şekilde yüklenemedi."

 Bu hatalar, kendi kişisel bilgileri olan bir çalışma kitabını temel alan bir projeyi belge denetçisi kullanılarak oluşturmaya çalıştığınızda meydana gelir. Bu hatayı önlemek için, projeyi oluşturmadan önce aşağıdaki adımları gerçekleştirin.

1. Çalışma kitabını Excel'de açın.

2. Excel 'de güven merkezini açın.

3. **Gizlilik seçenekleri** sekmesinde, **kaydederken kişisel bilgileri dosya özelliklerinden kaldır** onay kutusunun işaretini kaldırın.

4. Çalışma kitabını kaydedin ve Excel 'i kapatın.

### <a name="cannot-open-a-project-after-migration"></a>Geçişten sonra proje açılamaz
 Office çözümü Microsoft Office 2010 ' e geçirildikten sonra, proje yalnızca 2007 Microsoft Office sistemi yüklü olan bir geliştirme bilgisayarında açılamaz. Aşağıdaki hataları görebilirsiniz.

 "Çözümdeki bir veya daha fazla proje doğru şekilde yüklenmedi. Ayrıntılar için lütfen Çıkış Penceresi bakın. "

 "Bu proje türüyle ilişkili uygulama bu bilgisayarda yüklü olmadığından Proje oluşturulamıyor. Bu proje türüyle ilişkilendirilmiş Microsoft Office uygulamayı yüklemelisiniz. "

 Bu sorunu çözmek için *. vbproj* veya *. csproj* dosyasını düzenleyin. Bir Word projesi için HostPackage = "{763FDC83-64E5-4651-AC9B-28C4FEB985A1}" öğesini HostPackage = "{6CE98B71-D55A-4305-87A8-0D6E368D9600}" ile değiştirin. Bir Excel projesi için HostPackage = "{B284B16A-C42C-4438-BDCD-B72F4AC43CFB}" öğesini HostPackage = "{825100CF-0BA7-47ea-A084-DCF3308DADF74}" ile değiştirin. Bir Outlook projesi için HostPackage = "{D2B20FF5-A6E5-47E1-90E8-463C6860CB05}" öğesini HostPackage = "{20A848B8-E01F-4801-962E-25DB0FF57389}" ile değiştirin.

 Alternatif olarak, geçirilen projelerin yalnızca Microsoft Office 2010 zaten yüklü olan geliştirme bilgisayarlarında açıldığından emin olun.

### <a name="errors-in-upgraded-office-2003-document-level-projects-that-contain-windows-forms-controls"></a>Windows Forms denetimleri içeren yükseltilen Office 2003 belge düzeyi projelerindeki hatalar
 Bir Microsoft Office 2003 belge düzeyi projesi yükseltirseniz ve belge Windows Forms denetimleri içeriyorsa, yükseltilen proje derleme veya çalışma zamanı hatalarına sahip olabilir. Bu sorundan kaçınmak için, projeyi yükseltmeden önce geliştirme bilgisayarına Visual Studio 2005 Tools for Office Second Edition çalışma zamanını yükleyin. Çalışma zamanının bu sürümü, [Office Ikinci sürüm çalışma zamanı (VSTO 2005 de) (x86) için Microsoft Visual Studio 2005 araçlarında](https://www.microsoft.com/download/details.aspx?id=2392)Microsoft İndirme Merkezi 'nden yeniden dağıtılabilir bir paket olarak sunulmaktadır.

 Projeyi yükseltmeyi tamamladıktan sonra, diğer Office çözümleri tarafından kullanılmıyorsa Office Second Edition çalışma zamanı için Visual Studio 2005 araçları 'nı geliştirme bilgisayarından kaldırabilirsiniz.

## <a name="use-the-designers"></a><a name="designers"></a>Tasarımcıları kullanma
 Belge düzeyi projelerde belge, çalışma kitabı veya çalışma sayfası tasarımcısı ile çalışırken aşağıdaki hatalarla karşılaşabilirsiniz.

### <a name="designer-failed-to-load-correctly"></a>Tasarımcı doğru şekilde yüklenemedi
 Visual Studio aşağıdaki durumlarda tasarımcıyı açamıyor:

- Excel veya Word zaten açık ve kalıcı bir iletişim kutusu görüntülüyor. Tasarımcıyı açmak için, Excel veya Word 'Ün kalıcı iletişim kutusu açık olup olmadığını denetleyin ve açık kalıcı iletişim kutularını kapatın. Hiçbir kalıcı iletişim kutusu açık değilse, Excel veya Word 'e yanıt vermeden önce başka bir işlem yapmanız gerekebilir.

- Projede Şu anda hata ayıklıyor. Tasarımcıyı açmak için, hata ayıklamayı durdurun veya sona erdirin.

- Geliştirme bilgisayarında yüklü bir Excel VSTO eklentisi, Excel başladığında bir iletişim kutusu görüntülüyor. Excel belge düzeyi projesi oluşturmak için önce VSTO eklentisini devre dışı bırakmanız gerekir.

### <a name="controls-appear-as-black-rectangles-on-the-document-or-worksheet"></a>Denetimler belge veya çalışma sayfasında siyah dikdörtgenler olarak görünür
 Denetimleri bir belge veya çalışma sayfasında gruplandırdıysanız, Visual Studio artık denetimleri tanımaz. Gruplanmış denetimlere **Özellikler** penceresinden erişilemez ve belge veya çalışma sayfasında siyah dikdörtgenler olarak görünürler. İşlevlerini geri yüklemek için denetimlerin grubunu çözmeniz gerekir.

### <a name="controls-on-a-word-template-are-not-visible-in-visual-studio"></a>Word şablonundaki Denetimler Visual Studio 'da görünmez
 Visual Studio tasarımcısında bir Word şablonu açarsanız, şablonda metinle birlikte olmayan denetimler görünür olmayabilir. Bunun nedeni, Visual Studio 'Nun **normal** görünümde Word şablonlarını açmasıdır. Denetimleri görüntülemek için **Görünüm** menüsüne tıklayın, **Microsoft Office Word görünümü** ' ne gelin ve ardından **yazdırma düzeni**' ne tıklayın.

### <a name="insert-clip-art-command-does-nothing-in-the-visual-studio-designer"></a>Küçük resim Ekle komutu Visual Studio tasarımcısında hiçbir şey yapmaz
 Excel veya Word Visual Studio tasarımcısında açıldığında, Şeritteki **çizimler** sekmesinde bulunan **küçük resim** düğmesine tıklamak, **küçük resim** görev bölmesini açmaz. Küçük resim eklemek için, Visual Studio dışında ana proje klasöründeki ( *\Bin* klasöründe olan kopya değil) çalışma kitabının veya belgenin kopyasını açmanız, küçük resmi eklemeniz ve sonra çalışma kitabını veya belgeyi kaydetmeniz gerekir.

## <a name="write-code"></a><a name="code"></a>Kod Yaz
 Office projelerinde kod yazdığınızda aşağıdaki hatalarla karşılaşabilirsiniz.

### <a name="some-events-of-office-objects-are-not-accessible-when-using-c"></a>C kullanırken Office nesnelerinin bazı olaylarına erişilemez\#
 Bazı durumlarda, bir Visual C# projesinde Office birincil birlikte çalışma derlemesi (PIA) türünün bir örneğinin belirli bir olayına erişmeye çalıştığınızda aşağıdakine benzer bir derleyici hatası görebilirsiniz.

 "' Microsoft. Office. Interop. Excel. _Application. NewWorkbook ' ve ' Microsoft. Office. Interop. Excel. AppEvents_Event. NewWorkbook '" arasındaki belirsizlik

 Bu hata, nesnenin başka bir özelliği veya yöntemiyle aynı ada sahip bir olaya erişmeye çalıştığınız anlamına gelir. Olaya erişmek için, nesneyi *olay arabirimine*atamalısınız.

 Olayları olan Office PIA türleri iki arabirim uygular: tüm özellikleri ve yöntemleri içeren bir çekirdek arabirim ve nesne tarafından açığa çıkarılan olayları içeren bir olay arabirimi. Bu olay arabirimleri, ve gibi, *ObjectName*olayları*n*_Event adlandırma kuralını kullanır <xref:Microsoft.Office.Interop.Excel.AppEvents_Event> <xref:Microsoft.Office.Interop.Word.ApplicationEvents2_Event> . Bir nesne üzerinde bulmayı düşündüğünüz bir olaya erişemiyorsanız, nesneyi olay arabirimine atayın.

 Örneğin, <xref:Microsoft.Office.Interop.Excel.Application> nesneler bir <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook> olaya ve bir özelliğe sahiptir <xref:Microsoft.Office.Interop.Excel._Application.NewWorkbook%2A> . Olayı işlemek için <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook> , <xref:Microsoft.Office.Interop.Excel.Application> <xref:Microsoft.Office.Interop.Excel.AppEvents_Event> arabirimini arabirimine atayın. Aşağıdaki kod örneği, Excel için belge düzeyindeki bir projede bunun nasıl yapılacağını göstermektedir.

 [!code-csharp[Trin_VstcoreTroubleshootingExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingExcelCS/ThisWorkbook.cs#1)]

 Office PIA 'leri içindeki olay arabirimleri hakkında daha fazla bilgi için bkz. [Office birincil birlikte çalışma derlemelerindeki sınıflara ve arabirimlere genel bakış](/previous-versions/office/office-12//ms247299(v=office.12)).

### <a name="cannot-reference-office-pia-classes-in-projects-that-target-the-net_v40_short-or-the-net_v45"></a>Veya öğesini hedefleyen projelerde Office PIA sınıflarına başvuramaz [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)][!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]
 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]Ya da [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] ' i hedefleyen projelerde, BIR Office PIA ' de tanımlanan bir sınıfa başvuruda bulunan kod varsayılan olarak derlenmeyecektir. PIA 'ler içindeki sınıflar, ve gibi adlandırma kuralı *ObjectName*sınıfını kullanır <xref:Microsoft.Office.Interop.Word.DocumentClass> <xref:Microsoft.Office.Interop.Excel.WorkbookClass> . Örneğin, bir Word VSTO eklenti projesinden aşağıdaki kod derlenmeyecektir.

```vb
Dim document As Word.DocumentClass = Globals.ThisAddIn.Application.ActiveDocument
```

```csharp
Word.DocumentClass document = (Word.DocumentClass) Globals.ThisAddIn.Application.ActiveDocument;
```

 Bu kod aşağıdaki derleme hatalarına neden olur:

- Visual Basic: "' DocumentClass ' sınıfına yönelik başvuruya, derlemesi hiçbir PIA modu kullanılarak bağlandığında izin verilmez."

- Visual C#: "Microsoft.Office.Interop.Word.DocumentClass ' birlikte çalışma türü Katıştırılamaz. Bunun yerine uygulanabilir arabirimi kullanın. "

  Bu hatayı çözmek için, kodu bunun yerine karşılık gelen arabirime başvuracak şekilde değiştirin. Örneğin, bir nesneye başvurmak yerine <xref:Microsoft.Office.Interop.Word.DocumentClass> , <xref:Microsoft.Office.Interop.Word.Document> bunun yerine arabirimin örneğine başvurun.

```vb
Dim document As Word.Document = Globals.ThisAddIn.Application.ActiveDocument
```

```csharp
Word.Document document = Globals.ThisAddIn.Application.ActiveDocument;
```

 Veya öğesini hedefleyen projeler [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , varsayılan olarak tüm birlikte çalışma türlerini Office PIA 'ları 'ndan otomatik olarak katıştırın. Bu derleme hatası, gömülü birlikte çalışma türleri özelliği sınıflarla değil arabirimlerle birlikte çalışacağından oluşur. Office PIA 'Ları içindeki arabirimler ve sınıflar hakkında daha fazla bilgi için bkz. [Office birincil birlikte çalışma derlemelerindeki sınıflara ve arabirimlere genel bakış](/previous-versions/office/office-12/ms247299(v=office.12)). Office projelerinde gömülü birlikte çalışma türleri özelliği hakkında daha fazla bilgi için bkz. [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md).

### <a name="references-to-office-classes-are-not-recognized"></a>Office sınıflarına yönelik başvurular tanınmıyor
 Örneğin, uygulama gibi bazı sınıf adları, ve gibi birden çok ad alanında <xref:Microsoft.Office.Interop.Word> bulunur <xref:System.Windows.Forms> . Bu nedenle, **Imports** / proje şablonlarının en üstündeki Imports**using** deyimleri, bir kısayol niteleyen sabiti içerir, örneğin:

 [!code-csharp[Trin_VstcoreTroubleshootingWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs#2)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb#2)]

 **Imports** / **using** ifadesinin bu kullanımı, Office sınıflarının başvurularını Word veya Excel niteleyicisi ile ayırmanızı gerektirir, örneğin:

 [!code-csharp[Trin_VstcoreTroubleshootingWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs#3)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb#3)]

 Nitelenmemiş bir bildirim kullanırsanız hata alırsınız, örneğin:

 [!code-csharp[Trin_VstcoreTroubleshootingWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs#4)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb#4)]

 Word veya Excel ad alanını içeri aktarmış olsanız ve içindeki tüm sınıflara erişebilseniz de, ad alanı belirsizi kaldırmak için Word veya Excel ile tüm türleri tamamen nitelemeniz gerekir.

## <a name="build-projects"></a><a name="building"></a>Yapı projeleri
 Office projelerini oluştururken aşağıdaki hatalarla karşılaşabilirsiniz.

### <a name="cannot-build-a-document-level-project-that-is-based-on-a-document-with-restricted-permissions"></a>Kısıtlanmış izinlere sahip bir belgeyi temel alan belge düzeyi projesi oluşturulamaz
 Belge sınırlı izinlere sahipse, Visual Studio belge düzeyinde projeler derlenemez. Projeniz sınırlı izinlere sahip bir belge içeriyorsa, proje derlenmez ve **hata listesi** penceresinde aşağıdaki iletiyi alırsınız.

 "Özelleştirme eklenemedi."

 Sınırlı izinlere sahip bir belge eklemek istiyorsanız, çözümü geliştirirken ve oluştururken kısıtlanmamış bir belge kullanın. Ardından, çözümü yayımladıktan sonra, yayımlama konumundaki belgeye kısıtlı izinleri uygulayın.

### <a name="compiler-errors-occur-after-a-namedrange-control-is-deleted"></a>NamedRange denetimi silindikten sonra derleyici hataları oluşur
 <xref:Microsoft.Office.Tools.Excel.NamedRange>Tasarımcıda etkin çalışma sayfası olmayan bir çalışma sayfasından bir denetimi silerseniz, otomatik olarak oluşturulan kod projenizden kaldırılmayabilir ve derleyici hataları oluşabilir. Kodun kaldırıldığından emin olmak için, <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimi silmeden önce etkin çalışma sayfası yapmak üzere denetimi içeren çalışma sayfasını her zaman seçmelisiniz. Denetimi sildiğinizde otomatik olarak oluşturulan kod silinmemişse, tasarımcı 'nın çalışma sayfasını etkinleştirerek ve çalışma sayfasının değiştirilmiş olarak işaretlendiğinden bir değişiklik yaparak kodu silmesine neden olabilirsiniz. Projeyi yeniden oluşturduğunuzda kod kaldırılır.

## <a name="debug-projects"></a><a name="debugging"></a>Hata ayıklama projeleri
 Office projelerinde hata ayıklarken aşağıdaki hatalarla karşılaşabilirsiniz.

### <a name="prompt-to-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>Geliştirme bilgisayarında bir çözüm yayımladığınızda ve yüklediğinizde yüklemeyi kaldırma istemi görüntülenir
 Bir Office çözümünde hata ayıklarken, aşağıdaki hatayı görebilirsiniz.

 "Şu anda başka bir sürüm yüklü olduğundan ve bu konumdan yükseltilemediğinden özelleştirme yüklenemiyor."

 Bu hata, Office çözümünü geliştirme bilgisayarınızda daha önce yayımladığınızdan ve yüklediğiniz anlamına gelir. İletinin görünmesini engellemek için, çözümü hata ayıklamadan önce bilgisayardaki yüklü programlar listesinden kaldırın. Alternatif olarak, yayımlanan çözümü yüklemeyi test etmek için geliştirme bilgisayarınızda başka bir kullanıcı hesabı da oluşturabilirsiniz.

### <a name="document-level-projects-created-at-unc-network-locations-do-not-run-from-visual-studio"></a>UNC ağ konumlarında oluşturulan belge düzeyi projeler Visual Studio 'dan çalıştırılmadı
 Bir UNC ağ konumunda Excel veya Word için belge düzeyi projesi oluşturursanız, belgenin konumunu Excel veya Word 'deki güvenilir konumlar listesine eklemeniz gerekir. Aksi takdirde, Visual Studio 'da Projeyi çalıştırmaya veya hata ayıklamanıza çalıştığınızda özelleştirme yüklenmez. Güvenilen konumlar hakkında daha fazla bilgi için bkz. [belgelere güven verme](../vsto/granting-trust-to-documents.md).

### <a name="threads-are-not-stopped-correctly-after-debugging"></a>Hata ayıkladıktan sonra iş parçacıkları doğru şekilde durdurulmaz
 Visual Studio 'da Office projeleri, hata ayıklayıcının programı doğru şekilde kapatmasını sağlayan bir iş parçacığı adlandırma kuralı izler. Çözümünüzde iş parçacıkları oluşturursanız, hata ayıklamayı durdurduğunuzda bu iş parçacıklarının doğru şekilde işlendiğinden emin olmak için her bir iş parçacığını önek VSTA_ olarak adlandırın. Örneğin, `Name` bir ağ olayını bekleyen bir iş parçacığının özelliğini **VSTA_NetworkListener**olarak ayarlayabilirsiniz.

### <a name="cannot-run-or-debug-any-office-solution-on-the-development-computer"></a>Geliştirme bilgisayarında herhangi bir Office çözümü çalıştırılamaz veya hata ayıklaması yapılamaz
 Geliştirme bilgisayarınızda bir Office projesi çalıştıramayabilir veya geliştirirseniz, aşağıdaki hata iletisini görebilirsiniz.

 "Uygulama etki alanı oluşturulamadığından özelleştirme yüklenemedi."

 Visual Studio, Office çözümlerini yüklemeden önce derlemeleri önbelleğe almak için .NET Framework derleme yükleyicisini Fusion kullanır. Visual Studio 'Nun Fusion önbelleğine yazabildiğinden emin olun ve yeniden deneyin. Daha fazla bilgi için bkz. [gölge kopya derlemeleri](/dotnet/framework/app-domains/shadow-copy-assemblies).

### <a name="error-when-stopping-the-debugger-in-a-document-level-project-after-using-edit-and-continue"></a>Düzenle ve devam et kullandıktan sonra belge düzeyindeki bir projede hata ayıklayıcı durdurulurken hata oluştu
 Proje kesme modundayken Excel veya Word için belge düzeyindeki bir projedeki kodda değişiklik yapmak üzere **Düzenle** ve **devam et** ' i kullanırsanız, hata ayıklayıcıyı durdurduktan sonra aşağıdaki hata iletisiyle bir iletişim kutusu görebilirsiniz.

 "İşlemin geçerli durumunda sonlandırılması, veri kaybı ve sistem kararsızlığına dahil olmak üzere istenmeyen sonuçlara neden olabilir."

 İletişim kutusunda **Evet** veya **Hayır** ' a tıkladığınızda, Visual Studio Excel veya Word işlemini sonlandırır ve hata ayıklayıcıyı durdurur. Bu iletişim kutusunu görüntülemeden projenin hata ayıklamasını durdurmak için, Visual Studio 'da hata ayıklayıcıyı durdurmak yerine Excel veya Word 'den doğrudan çıkın.

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümlerinde sorun giderme](../vsto/troubleshooting-office-solutions.md)
- [Office çözüm güvenliği sorunlarını giderme](../vsto/troubleshooting-office-solution-security.md)
- [Office çözüm dağıtımı sorunlarını giderme](../vsto/troubleshooting-office-solution-deployment.md)
- [Visual Studio sorunlarını giderme](/troubleshoot/visualstudio/welcome-visual-studio/)
