---
title: Başvuru Yöneticisi 'ne başvurular ekleme
description: Geliştirilmiş bileşenlere başvurular eklemek ve bunları yönetmek için başvuru Yöneticisi iletişim kutusunu nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 08/30/2021
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
ms.openlocfilehash: aa958014557577f5b2d0fda851d643c914a6942d
ms.sourcegitcommit: 0c6cecf1b973a33003d924abeb382f23e62c134d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2021
ms.locfileid: "123230319"
---
# <a name="how-to-add-or-remove-references-by-using-the-reference-manager"></a>Nasıl yapılır: başvuru Yöneticisi 'ni kullanarak başvuru ekleme veya kaldırma

Sizin, Microsoft veya başka bir şirketinizin geliştirdiği bileşenlere başvurular eklemek ve bunları yönetmek için başvuru Yöneticisi iletişim kutusunu kullanabilirsiniz. bir evrensel Windows uygulaması geliştiriyorsanız, projeniz doğru Windows SDK dll 'lerine otomatik olarak başvurur. Bir .NET uygulaması geliştiriyorsanız, projeniz otomatik olarak *mscorlib.dll* başvurur. Bazı .NET API 'Leri, el ile eklemeniz gereken bileşenlerde kullanıma sunulur. COM bileşenlerine veya özel bileşenlere yapılan başvuruların el ile eklenmesi gerekir.

## <a name="reference-manager-dialog-box"></a>Başvuru Yöneticisi iletişim kutusu

Başvuru Yöneticisi iletişim kutusu, proje türüne bağlı olarak sol tarafta farklı kategoriler gösterir:

- **Derlemeler**, **çerçeve** ve **Uzantılar** alt grupları ile

- **Com** , başvuruda bulunan tüm com bileşenlerini listeler

- **Projeler**

- **Paylaşılan projeler**

- **Windows**, **çekirdek** ve **uzantılar** alt grupları ile. **Nesne Tarayıcısı** kullanarak Windows SDK veya uzantı sdk 'lerinde başvuruları inceleyebilirsiniz.

- **En son** alt grup ile **tarama**

    > [!NOTE]
    > C++ projeleri geliştiriyorsanız başvuru Yöneticisi iletişim kutusunda **gözatamıyorum** ' a bakabilirsiniz.

## <a name="add-a-reference"></a>Başvuru ekleme

::: moniker range="vs-2017"

1. **Çözüm Gezgini**, **Başvurular** veya **Bağımlılıklar** düğümüne sağ tıklayın ve **Başvuru Ekle**' yi seçin. Ayrıca, proje düğümüne sağ tıklayıp başvuru **Ekle**' yi seçebilirsiniz  >  .

   **Başvuru Yöneticisi** açılır ve gruba göre kullanılabilir başvuruları listeler.

2. Eklenecek başvuruları belirtin ve ardından **Tamam**' ı seçin.

::: moniker-end

::: moniker range=">=vs-2019"

1. **Çözüm Gezgini**, **başvurular** veya **bağımlılıklar** düğümüne sağ tıklayın ve **Project başvuru ekle**, **paylaşılan Project başvurusu ekle** ya da **COM başvurusu ekle**' yi seçin. (Proje düğümüne sağ tıklayıp, bu seçeneklerden birini seçmek için, açılan menüden **Ekle** ' yi seçebilirsiniz.)

   **Başvuru Yöneticisi** açılır ve gruba göre kullanılabilir başvuruları listeler.

2. Eklenecek başvuruları belirtin ve ardından **Tamam**' ı seçin.

::: moniker-end

## <a name="assemblies-tab"></a>Derlemeler sekmesi

**Derlemeler** sekmesi, başvuru için kullanılabilen tüm .NET derlemelerini listeler. GAC içindeki derlemeler çalışma zamanı ortamının bir parçası olduğundan, **derlemeler** sekmesi genel derleme ÖNBELLEĞINDEN (GAC) herhangi bir derlemeyi listeetmez. GAC 'de kayıtlı bir derlemeye başvuru içeren bir uygulama dağıtırsanız ya da kopyalarsanız, derleme **Yerel** ayarından bağımsız olarak uygulamayla birlikte dağıtılmaz veya kopyalanmaz. Daha fazla bilgi için bkz. [bir projedeki başvuruları yönetme](../ide/managing-references-in-a-project.md).

EnvDTE ad alanlarından herhangi birine (,,, veya) el ile bir başvuru eklediğinizde <xref:EnvDTE> <xref:EnvDTE80> <xref:EnvDTE90> <xref:EnvDTE90a> <xref:EnvDTE100> , **Özellikler** penceresinde başvurunun **birlikte çalışma türlerini katıştır** özelliğini **false** olarak ayarlayın. Bu özelliğin **true** olarak ayarlanması, katıştırılamayan belirli EnvDTE özellikleri nedeniyle derleme sorunlarına neden olabilir.

Tüm masaüstü projeleri **mscorlib**'e örtük bir başvuru içerir. Visual Basic projeler öğesine örtük bir başvuru içerir <xref:Microsoft.VisualBasic> . Tüm projeler, başvurular listesinden kaldırılsa bile, **System. Core**'a örtük bir başvuru içerir.

Bir proje türü derlemeleri desteklemiyorsa, sekme başvuru Yöneticisi iletişim kutusunda görünmez.

**Derlemeler** sekmesi iki alt sekmeden oluşur:

1. **Framework** hedeflenen Çerçeveyi oluşturan tüm derlemeleri listeler.

   .net Core veya Evrensel Windows Platformu hedeflenmiyor projeler için, **framework** sekmesi hedeflenen çerçeveden derlemeleri sıralar. Kullanıcının, uygulamanın gerektirdiği tüm başvuruları eklemesi gerekir.

   evrensel Windows projeleri, varsayılan olarak hedeflenen çerçevede bulunan tüm derlemelere başvurular içerir. Yönetilen projelerde, **Çözüm Gezgini** ' deki **Başvurular** klasörü altındaki salt okunurdur bir düğüm, tüm Framework başvurusunu gösterir. Buna uygun olarak, **Framework** sekmesi çerçeveden derlemelerin hiçbirini numaralandırmaz ve bunun yerine şu iletiyi görüntüler: "tüm Framework derlemelerine zaten başvuruluyor. Lütfen Framework 'teki başvuruları araştırmak için Nesne Tarayıcısı kullanın.

2. **Uzantılar** , bileşen ve denetimlerin dış satıcılarının hedeflenen Çerçeveyi genişletmek üzere geliştirildiği tüm derlemeleri listeler. Kullanıcı uygulamasının amacına bağlı olarak, bu derlemelere gerek duyulabilir.

   **Uzantılar** , aşağıdaki konumlarda kayıtlı olan derlemeler numaralandırılarak doldurulur:

   32 bit makine:
   - `HKEY_CURRENT_USER\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`
   - `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`

   64 bit makine:
   - `HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`
   - `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`

   Ve [hedef çerçeve tanımlayıcısı] daha eski sürümleri

   örneğin, bir proje 32 bitlik bir makinede .NET Framework 4 ' ü hedefliyorsa, **uzantılar** *\microsoft \. NETFramework\v4.0\AssemblyFoldersEx*, *\microsoft \. netframework\v3.5\assemblyfoldersex*, *\microsoft \. netframework\v3.0\assemblyfoldersex* ve *\microsoft \. netframework\v2.0\assemblyfoldersex* altında kayıtlı derlemeleri numaralandırır.

Listedeki bazı bileşenler, projenizin Framework sürümüne bağlı olarak gösterilmeyebilir. Bu durum aşağıdaki koşullarda oluşabilir:

- Son kullanılan Framework sürümünü kullanan bir bileşen, önceki bir sürümü hedefleyen bir proje ile uyumsuzdur.

   Bir proje için hedef Framework sürümünü değiştirme hakkında daha fazla bilgi için bkz. [framework hedefleme genel bakış](visual-studio-multi-targeting-overview.md).

- .NET Framework 4 kullanan bir bileşen, .NET Framework 4,5 ' i hedefleyen bir projeyle uyumsuzdur.

Aynı çözümdeki başka bir projenin çıktılarına dosya başvuruları eklemekten kaçının, çünkü bunu yapmak derleme hatalarına neden olabilir. Bunun yerine, projeden projeye başvurular oluşturmak için **Başvuru Ekle** Iletişim kutusunun **Projeler** sekmesini kullanın. Bu, projelerinizde oluşturduğunuz sınıf kitaplıklarının daha iyi yönetimini etkinleştirerek takım geliştirmeyi kolaylaştırır. Daha fazla bilgi için bkz. [Hatalı başvuruların sorunlarını giderme](../ide/troubleshooting-broken-references.md).

> [!NOTE]
> Visual Studio 2015 veya sonraki sürümlerde, bir projenin hedef framework sürümü 4,5 veya üzeri .NET Framework ve diğer projenin hedef sürümü .NET Framework 2, 3, 3,5 veya 4,0 ise, proje başvurusu yerine bir dosya başvurusu oluşturulur.

### <a name="to-display-an-assembly-in-the-add-reference-dialog-box"></a>Başvuru Ekle iletişim kutusunda bir derlemeyi göstermek için

- Derlemeyi aşağıdaki konumlardan birine taşıyın veya kopyalayın:

  - Geçerli proje dizini. (Bu derlemeleri, **tarayıcı** sekmesini kullanarak bulabilirsiniz.)

  - Aynı çözümdeki diğer proje dizinleri. ( **Projeler** sekmesini kullanarak bu derlemeleri bulabilirsiniz.)

  \- veya

- Görüntülenecek derlemelerin konumunu belirten bir kayıt defteri anahtarı ayarlayın:

  32 bitlik bir işletim sistemi için aşağıdaki kayıt defteri anahtarlarından birini ekleyin.

  - `[HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  - `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  64 bitlik bir işletim sistemi için, 32 bit kayıt defteri kovanında aşağıdaki kayıt defteri anahtarlarından birini ekleyin.

  - `[HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  - `[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  *\<VersionMinimum\>* , uygulanan en düşük çerçeve sürümüdür. *\<VersionMinimum\>* v 3.0 ise, *assemblyfoldersex* içinde belirtilen klasörler, .NET Framework 3,0 ve üstünü hedefleyen projeler için geçerlidir.

  *\<AssemblyLocation\>* , **Başvuru Ekle** iletişim kutusunda görünmesini istediğiniz derlemelerin dizinidir, örneğin, *C:\MyAssemblies*.

  Düğüm altında kayıt defteri anahtarı oluşturulması, `HKEY_LOCAL_MACHINE` tüm kullanıcıların **Başvuru Ekle** iletişim kutusunda belirtilen konumdaki derlemeleri görmesini sağlar. Düğüm altında kayıt defteri anahtarı oluşturulması `HKEY_CURRENT_USER` yalnızca geçerli kullanıcının ayarını etkiler.

  **Başvuru Ekle** iletişim kutusunu tekrar açın. Derlemeler **.net** sekmesinde görünmelidir. aksi takdirde, derlemelerin belirtilen *assemblylocation* dizininde bulunduğundan emin olun, Visual Studio yeniden başlatın ve yeniden deneyin.

## <a name="projects-tab"></a>Projeler sekmesi

**Projeler** sekmesi, geçerli çözüm içindeki tüm uyumlu projeleri **çözüm** alt sekmesinde listeler.

Proje, farklı bir Framework sürümünü hedefleyen başka bir projeye başvurabilir. örneğin, .NET Framework 4 ' ü hedefleyen ancak .NET Framework 2 için oluşturulmuş bir derlemeye başvuran bir proje oluşturabilirsiniz. ancak, .NET Framework 2 projesi bir .NET Framework 4 projesine başvuramaz. Daha fazla bilgi için bkz. [Çerçeve hedefleme genel bakış](../ide/visual-studio-multi-targeting-overview.md).

> [!NOTE]
> .NET Framework 4 ' ü hedefleyen bir proje, .NET Framework 4 istemci profilini hedefleyen bir projeyle uyumsuzdur.

## <a name="shared-projects-tab"></a>Paylaşılan projeler sekmesi

Başvuru Yöneticisi iletişim kutusunun **Paylaşılan projeler** sekmesinde paylaşılan bir projeye bir başvuru ekleyin. [Paylaşılan projeler](/xamarin/cross-platform/app-fundamentals/shared-projects?tabs=windows) , bir dizi farklı uygulama projesinin başvurduğu ortak kod yazmanızı sağlar.

## <a name="universal-windows-tab"></a>evrensel Windows sekmesi

**evrensel Windows** sekmesi, Windows işletim sistemlerinin çalıştırıldığı platformlara özgü tüm sdk 'ları listeler.
Bu sekmenin iki alt grupları vardır: **çekirdek** ve **Uzantılar**.

### <a name="core-subgroup"></a>Çekirdek alt grubu

evrensel Windows uygulama projelerinin varsayılan olarak evrensel Windows SDK bir başvurusu vardır. buna uygun olarak, **başvuru yöneticisindeki** **çekirdek** alt grubu, evrensel Windows SDK derlemelerin hiçbirini numaralandırmaz.

### <a name="extensions-subgroup"></a>Uzantılar alt grubu

**uzantılar** hedeflenen Windows platformunu genişleten kullanıcı sdk 'larını listeler.

SDK, Visual Studio'nun tek bir bileşen olarak kabul ettiği dosyalar topluluğudur. **Uzantılar** sekmesinde, başvuru Yöneticisi iletişim kutusunun çağrıldığı proje Için uygulanan SDK 'lar tek girdi olarak listelenir. bir projeye eklendiğinde, tüm sdk içeriği, kullanıcının ıntellisense, araç kutusu, tasarımcılar, Nesne Tarayıcısı, derleme, dağıtım, hata ayıklama ve paketleme içindeki SDK içeriğinden yararlanmak için başka bir eylem yapması gerekmez. Visual Studio tarafından kullanılır.

SDK 'larınızı **Uzantılar** sekmesinde görüntüleme hakkında daha fazla bilgi için bkz. [yazılım geliştirme seti oluşturma](../extensibility/creating-a-software-development-kit.md).

> [!NOTE]
> bir proje, başka bir sdk 'ya bağlı olan bir sdk 'ya başvuruyorsa ikinci sdk 'ya el ile bir başvuru eklemediğiniz takdirde Visual Studio ikinci sdk 'yı tüketmez. Bir Kullanıcı **Uzantılar** SEKMESINDE bir SDK seçtiğinde, başvuru Yöneticisi iletişim kutusu, Ayrıntılar bölmesindeki BAĞıMLıLıKLARı listeleyerek SDK bağımlılıklarını belirlemenize yardımcı olur.

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
