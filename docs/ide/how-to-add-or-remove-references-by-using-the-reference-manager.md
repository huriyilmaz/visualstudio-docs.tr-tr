---
title: Başvuru Yöneticisi'ne başvuru ekleme
description: Geliştirilmiş bileşenlere başvuru eklemek ve yönetmek için Başvuru Yöneticisi iletişim kutusunu kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 08/02/2019
ms.topic: how-to
f1_keywords:
- VS.ReferenceManager
helpviewer_keywords:
- C# projects, references
- references [Visual Studio], adding
- assemblies [Visual Studio], references
- Visual Basic projects, references
- project references, adding
- referencing components, adding references
- project references, removing
- referencing assemblies
- referencing components, removing references
- references [Visual Studio], removing
- referencing components, assemblies not listed
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 553e116bf7592534e993f5c400b813abbc62ffe5bb2a3e727c8ca0699da74481
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121387726"
---
# <a name="how-to-add-or-remove-references-by-using-the-reference-manager"></a>Nasıl: Başvuru Yöneticisi'ni kullanarak başvuru ekleme veya kaldırma

Sizin, Microsoft'un veya başka bir şirketin geliştirdiği bileşenlere başvurular eklemek ve yönetmek için Başvuru Yöneticisi iletişim kutusunu kullanabilirsiniz. Universal Windows uygulaması geliştiriyorsanız projeniz otomatik olarak tüm doğru SDK WINDOWS başvurur. Bir .NET uygulaması geliştiriyorsanız projeniz otomatik olarak *mscorlib.dll.* Bazı .NET API'leri el ile eklemeniz gereken bileşenlerde ortaya çıkar. COM bileşenlerine veya özel bileşenlere başvurular el ile eklenmiştir.

## <a name="reference-manager-dialog-box"></a>Başvuru Yöneticisi iletişim kutusu

Başvuru Yöneticisi iletişim kutusu, proje türüne bağlı olarak sol tarafta farklı kategoriler gösterir:

- **Derlemeler,** **Çerçeve** ve **Uzantılar** alt grupları ile

- **COM,** başvuru için kullanılabilen tüm COM bileşenlerini listeler

- **Projeler**

- **Paylaşılan Projeler**

- **Windows,** Çekirdek **ve** **Uzantılar alt** gruplarıyla. Object Browser'ı kullanarak Windows SDK'sı veya uzantı SDK'ları'nda başvuruları **keşfedebilirsiniz.**

- **Göz atma,** **Son kullanılan alt** grupla
 
    > [!NOTE]
    > C++ projeleri **geliştiriyorsanız** Başvuru Yöneticisi iletişim kutusunda Gözat seçeneğini görmeyebilirsiniz.

## <a name="add-a-reference"></a>Başvuru ekleme

1. Bu **Çözüm Gezgini,** Başvurular veya **Bağımlılıklar düğümüne sağ** **tıklayın ve Başvuru** Ekle'yi **seçin.** Ayrıca proje düğümüne sağ tıklar ve Başvuru **Ekle'yi de**  >  **seçersiniz.**

   **Başvuru Yöneticisi** açılır ve kullanılabilir başvuruları gruba göre listeler.

2. Eklemek istediğiniz başvuruları belirtin ve tamam'ı **seçin.**

## <a name="assemblies-tab"></a>Derlemeler sekmesi

Derlemeler **sekmesi,** başvuru için kullanılabilen tüm .NET derlemelerini listeler. GAC'de derlemeler çalışma zamanı ortamının bir parçası olduğundan, Derlemeler sekmesi genel derleme önbelleğinden (GAC) derlemeleri listelemektedir.  GAC'de kayıtlı bir derlemeye başvuru içeren bir uygulamayı dağıtır veya kopyalarsanız, Derleme Yereli Kopyala ayarına bakılmaksızın uygulamayla birlikte dağıtilmez **veya kopyalanmaz.** Daha fazla bilgi için [bkz. Projedeki başvuruları yönetme.](../ide/managing-references-in-a-project.md)

EnvDTE ad alanlarından herhangi biri ( , , , veya ) için el ile bir başvuru eklerken, Özellikler penceresinde başvurusunu Birlikte Çalışma Türleri Ekle <xref:EnvDTE> özelliğini False <xref:EnvDTE80> <xref:EnvDTE90> <xref:EnvDTE90a> <xref:EnvDTE100>  **olarak** ayarlayın.  Bu özelliğin **True olarak** ayarlandırarak, katıştırılamayacak bazı EnvDTE özellikleri nedeniyle derleme sorunlarına neden olabilir.

Tüm masaüstü projeleri **mscorlib** için örtülü bir başvuru içerir. Visual Basic projeleri için örtülü bir başvuru <xref:Microsoft.VisualBasic> içerir. Tüm projeler, başvuru listesinden kaldırılmış olsa bile **System.Core** için örtülü bir başvuru içerir.

Proje türü derlemeleri desteklemezse, Başvuru Yöneticisi iletişim kutusunda sekme görünmez.

Derlemeler **sekmesi** iki alt sekmeden oluşur:

1. **Framework** hedeflenen çerçeveyi oluşturan tüm derlemeleri listeler.

   .NET Core veya Universal Windows Platform'u hedeflemeen projeler için **Framework** sekmesi hedeflenen çerçeveden derlemeleri numaralandırdı. Kullanıcının uygulamanın gerektirdiği tüm başvuruları eklemesi gerekir.

   Evrensel Windows projeleri varsayılan olarak hedeflenen çerçevedeki tüm derlemelere başvurular içerir. Yönetilen projelerde, Çözüm Gezgini'daki **Başvurular** klasörünün **altındaki** salt okunur bir düğüm, çerçevenin tamamına başvuruyu gösterir. Buna uygun olarak, **Framework** sekmesi çerçevedeki derlemelerin herhangi birini numaralandırmaz ve bunun yerine şu iletiyi görüntüler: "Tüm Framework derlemelerine zaten başvurıldı. Lütfen Framework'te başvuruları keşfetmek için Object Browser'i kullanın".

2. **Uzantılar,** dış bileşen ve denetim satıcılarının hedeflenen çerçeveyi genişletmek için geliştirdiği tüm derlemeleri listeler. Kullanıcı uygulamasının amacına bağlı olarak, bu derlemelere gerek duyulabilir.

   **Uzantılar,** aşağıdaki konumlarda kayıtlı derlemeler numaralara kaydederek doldurulur:

   32 bit makine:
   - `HKEY_CURRENT_USER\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`
   - `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`

   64 bit makine:
   - `HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`
   - `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`

   Ve [Target Framework Identifier] 'ın eski sürümleri

   Örneğin, bir proje 32 bit makinede .NET Framework 4'ü **hedeflerse,** Uzantılar *\Microsoft \. NETFramework\v4.0\AssemblyFoldersEx*, *\Microsoft \. NETFramework\v3.5\AssemblyFoldersEx*, *\Microsoft \. NETFramework\v3.0\AssemblyFoldersEx* ve *\Microsoft \. NETFramework\v2.0\AssemblyFoldersEx* altında kayıtlı derlemeleri numaralandırdı.

Projenizin çerçeve sürümüne bağlı olarak, listede bazı bileşenler gösterilmeyebilirsiniz. Bu durum aşağıdaki koşullarda oluşabilir:

- Son çerçeve sürümünü kullanan bir bileşen, önceki bir sürümü hedef alan bir projeyle uyumsuzdur.

   Bir projenin hedef çerçeve sürümünü değiştirme hakkında bilgi için bkz. [Çerçeve hedeflemeye genel bakış.](visual-studio-multi-targeting-overview.md)

- .NET Framework 4 kullanan bir bileşen, 4.5'i .NET Framework bir projeyle uyumsuzdur.

Bunu yapmak derleme hatalarına neden olduğundan, aynı çözümdeki başka bir projenin çıkışlarına dosya başvuruları eklemekten kaçınmanız gerekir. Bunun yerine, **projeden** projeye **başvurular oluşturmak** için Başvuru Ekle iletişim kutusunun Projeler sekmesini kullanın. Bu, projeleriniz içinde oluşturmakta olduğu sınıf kitaplıklarının daha iyi yönetimini sağlayarak takım geliştirmeyi kolaylaştırır. Daha fazla bilgi için [bkz. Bozuk başvurularla ilgili sorunları giderme.](../ide/troubleshooting-broken-references.md)

> [!NOTE]
> Visual Studio 2015 veya sonraki bir sürümde, bir projenin hedef çerçeve sürümü .NET Framework 4.5 veya sonraki bir sürümse ve diğer projenin hedef sürümü .NET Framework 2, 3, 3.5 veya 4.0 ise proje başvurusu yerine bir dosya başvurusu oluşturulur.

### <a name="to-display-an-assembly-in-the-add-reference-dialog-box"></a>Bir derlemeyi Başvuru Ekle iletişim kutusunda görüntülemek için

- Derlemeyi aşağıdaki konumlardan birini taşıma veya kopyalama:

  - Geçerli proje dizini. (Gözat sekmesini kullanarak bu **derlemeleri** bulabilirsiniz.)

  - Aynı çözümde yer alan diğer proje dizinleri. (Bu derlemeleri Projeler sekmesini kullanarak **bulabilirsiniz.)**

  \- veya -

- Görüntülemek için derlemelerin konumunu belirten bir kayıt defteri anahtarı ayarlayın:

  32 bit işletim sistemi için aşağıdaki kayıt defteri anahtarlarından birini ekleyin.

  - `[HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  - `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  64 bit işletim sistemi için, 32 bit kayıt defteri kovanının içinde aşağıdaki kayıt defteri anahtarlarından birini ekleyin.

  - `[HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  - `[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  *\<VersionMinimum\>* , geçerli olan en düşük çerçeve sürümüdür. *\<VersionMinimum\>* v3.0 ise *AssemblyFoldersEx* içinde belirtilen klasörler, 3.0 ve sonraki bir .NET Framework projelere uygulanır.

  *\<AssemblyLocation\>*, Başvuru Ekle iletişim kutusunda görünmesini istediğiniz  derlemelerin dizinidir, *örneğin, C:\MyAssemblies*.

  Düğümün altında kayıt defteri anahtarının oluşturulması, tüm kullanıcıların Başvuru Ekle iletişim kutusunda `HKEY_LOCAL_MACHINE` belirtilen konumda **derlemeleri görmelerini** sağlar. Düğüm altında kayıt defteri `HKEY_CURRENT_USER` anahtarının oluşturulması yalnızca geçerli kullanıcının ayarını etkiler.

  Başvuru **Ekle iletişim** kutusunu yeniden açın. Derlemelerin **.NET** sekmesinde görünmesi gerekir. Yoksa, derlemelerin belirtilen *AssemblyLocation* dizininde olduğundan emin olun, Visual Studio yeniden başlatın ve yeniden deneyin.

## <a name="projects-tab"></a>Projeler sekmesi

Projeler **sekmesi,** geçerli çözüm içindeki tüm uyumlu projeleri Çözüm **alt** sekmesinde listeler.

Bir proje farklı bir çerçeve sürümünü hedef alan başka bir projeye başvurur. Örneğin, .NET Framework 4'ü hedef alan ancak .NET Framework 2 için oluşturulacak bir derlemeye başvuran bir proje oluşturabilirsiniz. Ancak, .NET Framework 2 projesi bir .NET Framework 4 projesine başvuramaz. Daha fazla bilgi için [bkz. Çerçeve hedeflemeye genel bakış.](../ide/visual-studio-multi-targeting-overview.md)

> [!NOTE]
> .NET Framework 4'ü hedef alan bir proje, .NET Framework 4 İstemci Profilini hedef alan bir projeyle uyumsuzdur.

## <a name="shared-projects-tab"></a>Paylaşılan Projeler sekmesi

Başvuru Yöneticisi iletişim kutusunun Paylaşılan Projeler **sekmesinde paylaşılan** bir projeye başvuru ekleyin. [Paylaşılan Projeler,](/xamarin/cross-platform/app-fundamentals/shared-projects?tabs=windows) bir dizi farklı uygulama projesi tarafından başvurulan ortak kod yazmana izin verir.

## <a name="universal-windows-tab"></a>Evrensel Windows sekmesi

**Evrensel Windows** sekmesi, işletim sistemlerinin üzerinde çalıştırıldıkları platformlara özgü Windows TÜM SDK'leri listeler.
Bu sekmenin iki alt grubu vardır: **Çekirdek** ve **Uzantılar.**

### <a name="core-subgroup"></a>Çekirdek alt grubu

Evrensel Windows uygulama projelerinin varsayılan olarak Universal Windows SDK'sı başvurusu vardır. Buna uygun **olarak,** Başvuru  Yöneticisi'nde Çekirdek alt grubu Universal Windows SDK'sı derlemelerinin herhangi birini numaralandırmaz.

### <a name="extensions-subgroup"></a>Uzantılar alt grubu

**Uzantılar,** hedeflenen Windows platformunu genişleten kullanıcı WINDOWS listeler.

SDK, Visual Studio'nun tek bir bileşen olarak kabul ettiği dosyalar topluluğudur. Uzantılar **sekmesinde,** Başvuru Yöneticisi iletişim kutusunun çağrıldığında projeye uygulanacak OLAN SDK'ler tek girişler olarak listelenir. Bir projeye ekildiğinde, kullanıcının IntelliSense, araç kutusu, tasarımcılar, Nesne Tarayıcısı, derleme, dağıtım, hata ayıklama ve paketleme'de SDK içeriklerini kullanmak için başka bir işlem yapmak zorunda kalmay için tüm SDK içeriği Visual Studio tarafından kullanılır.

Uzantılar sekmesinde SDK'nızı görüntüleme hakkında **bilgi için** [bkz. Yazılım Geliştirme Seti Oluşturma.](../extensibility/creating-a-software-development-kit.md)

> [!NOTE]
> Proje başka bir SDK'ya bağlı bir SDK'ya başvurursa, Visual Studio SDK'ya el ile başvuru eklemedikçe ikinci SDK'yı tüketmezsiniz. Kullanıcı Uzantılar sekmesinde bir  SDK'yı seçerken, Başvuru Yöneticisi iletişim kutusu ayrıntılar bölmesindeki bağımlılıkları listeleerek SDK bağımlılıklarını tanımlamanıza yardımcı olur.

Bir proje türü uzantıları desteklemiyorsa, bu sekme başvuru Yöneticisi iletişim kutusunda görünmez.

## <a name="com-tab"></a>COM sekmesi

**Com** sekmesi, başvuru için KULLANıLABILEN tüm com bileşenlerini listeler. Dahili bildirim içeren kayıtlı bir COM DLL öğesine başvuru eklemek isterseniz, önce DLL kaydını silin. aksi takdirde Visual Studio, derleme başvurusunu yerel bir DLL yerine bir ActiveX denetimi olarak ekler.

Bir proje türü COM 'u desteklemiyorsa, sekme başvuru Yöneticisi iletişim kutusunda görünmez.

## <a name="browse"></a>Gözat

Dosya sistemindeki bir bileşene gitmek için, **Araştır** düğmesini kullanabilirsiniz.

Proje, farklı bir Framework sürümünü hedefleyen bir bileşene başvurabilir. örneğin, .NET Framework 4,7 ' i hedefleyen, ancak .NET Framework 4 ' ü hedefleyen bir bileşene başvuran bir uygulama oluşturabilirsiniz. Daha fazla bilgi için bkz. [Çerçeve hedefleme genel bakış](../ide/visual-studio-multi-targeting-overview.md).

Aynı çözümdeki başka bir projenin çıktılarına dosya başvuruları eklemekten kaçının, çünkü bu durum derleme hatalarına neden olabilir. Bunun yerine, projeden projeye başvurular oluşturmak için başvuru Yöneticisi iletişim kutusunun **çözüm** sekmesini kullanın. Bu, projelerinizde oluşturduğunuz sınıf kitaplıklarının daha iyi yönetimini etkinleştirerek takım geliştirmeyi kolaylaştırır. Daha fazla bilgi için bkz. [Hatalı başvuruların sorunlarını giderme](../ide/troubleshooting-broken-references.md).

Bir SDK 'ya gözatamazsınız ve projenize ekleyemezsiniz. Yalnızca bir dosyaya (örneğin, bir derleme veya *. winmd*) gidebilir ve bu dosyayı projenize ekleyebilirsiniz.

Bir WinMD 'ye dosya başvurusu yaparken, beklenen Düzen *\<FileName> . winmd*, *\<FileName>.dll* ve *\<FileName> . pri* dosyalarının tümünün birbirine yerleştirilme halidir. Aşağıdaki senaryolarda bir WinMD'ye başvuruda bulunursanız, proje çıkış dizinine eksik bir dosya kümesi kopyalanır ve sonuç olarak, derleme ve çalışma zamanı hataları meydana gelir.

- **Yerel bileşen**: yerel bir proje, her ayrık ad alanı kümesi ve uygulamadan oluşan bir dll Için bir WinMD oluşturur. WinMD'ler ayrı adlara sahip olur. bu yerel bileşen dosyasına başvurulduğunda MSBuild, benzer şekilde adlandırılmış wınmds 'nin bir bileşen yapmasını tanımaz. Sonuç olarak, yalnızca aynı *\<FileName>.dll* ve *\<FileName> . winmd* adlı tek bir kopyalama yapılır ve çalışma zamanı hataları oluşur. Bu sorunu geçici olarak çözmek için bir uzantı SDK 'Sı oluşturun. Daha fazla bilgi için bkz. [yazılım geliştirme seti oluşturma](../extensibility/creating-a-software-development-kit.md).

- **Denetimleri** kullanma: en azından, XAML denetimi bir *\<FileName> . winmd*, *\<FileName>.dll*, *\<FileName> . pri*, *\<XamlName> . xaml* ve bir *\<ImageName>.jpg* oluşur. Proje oluşturulduğunda, dosya başvurusuyla ilişkili kaynak dosyaları projenin çıkış dizinine kopyalanmaz ve yalnızca *\<FileName> . winmd*, *\<FileName>.dll* ve *\<FileName> . pri* kopyalanır. Kullanıcıya Resources *\<XamlName> . xaml* ve *\<ImageName>.jpg* eksik olduğunu bildirmek için bir yapı hatası kaydedilir. Başarılı olması için, kullanıcının bu kaynak dosyaları oluşturma ve hata ayıklama/çalışma zamanı için proje çıkış dizinine el ile kopyalaması gerekir. Bu sorunu geçici olarak çözmek için, [yazılım geliştirme seti oluşturma](../extensibility/creating-a-software-development-kit.md) ' daki adımları izleyerek bir uzantı SDK 'sı oluşturun ya da aşağıdaki özelliği eklemek için proje dosyasını düzenleyin:

    ```xml
    <PropertyGroup>
       <GenerateLibraryOutput>True</GenerateLibraryOutput>
    </PropertyGroup>
    ```

    > [!NOTE]
    > Özelliği eklerseniz, yapı daha yavaş çalışabilir.

## <a name="recent"></a>En Son

**derlemeler**, **COM**, **Windows** **ve en son bir sekmeye** **gözatıp** , en son projelere eklenen bileşenlerin listesini numaralandırır.

## <a name="search"></a>Arayın

Başvuru Yöneticisi iletişim kutusundaki arama çubuğu, odağa sahip olan sekmenin üzerinde çalışır. Örneğin, **çözüm** sekmesi odağa karşın bir Kullanıcı arama çubuğuna "sistem" yazdığında, çözüm "sistem" içeren bir proje adından oluşmadığı sürece arama hiçbir sonuç döndürmez.

## <a name="see-also"></a>Ayrıca bkz.

- [Bir projedeki başvuruları yönetme](../ide/managing-references-in-a-project.md)
