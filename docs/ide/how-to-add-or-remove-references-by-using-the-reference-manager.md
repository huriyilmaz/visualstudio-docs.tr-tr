---
title: Başvuru Yöneticisi 'ne başvurular ekleme
ms.date: 08/02/2019
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dfad622a7587246836161cd79bb5b759151df1ef
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595316"
---
# <a name="how-to-add-or-remove-references-by-using-the-reference-manager"></a>Nasıl yapılır: başvuru Yöneticisi 'ni kullanarak başvuru ekleme veya kaldırma

Sizin, Microsoft veya başka bir şirketinizin geliştirdiği bileşenlere başvurular eklemek ve bunları yönetmek için başvuru Yöneticisi iletişim kutusunu kullanabilirsiniz. Bir Evrensel Windows uygulaması geliştiriyorsanız, projeniz otomatik olarak doğru Windows SDK dll 'Lerine başvurur. Bir .NET uygulaması geliştiriyorsanız, projeniz *mscorlib. dll*dosyasına otomatik olarak başvurur. Bazı .NET API 'Leri, el ile eklemeniz gereken bileşenlerde kullanıma sunulur. COM bileşenlerine veya özel bileşenlere yapılan başvuruların el ile eklenmesi gerekir.

## <a name="reference-manager-dialog-box"></a>Başvuru Yöneticisi iletişim kutusu

Başvuru Yöneticisi iletişim kutusu, proje türüne bağlı olarak sol tarafta farklı kategoriler gösterir:

- **Derlemeler**, **çerçeve** ve **Uzantılar** alt grupları ile

- **Com** , başvuruda bulunan tüm com bileşenlerini listeler

- **Projeler**

- **Paylaşılan Projeler**

- **Windows**, **çekirdek** ve **Uzantılar** alt grupları ile. **Nesne tarayıcısı**kullanarak Windows SDK veya uzantı SDK 'lerinde başvuruları inceleyebilirsiniz.

- **En son** alt grup ile **tarama**

## <a name="add-a-reference"></a>Başvuru ekleme

1. **Çözüm Gezgini**, **Başvurular** veya **Bağımlılıklar** düğümüne sağ tıklayın ve **Başvuru Ekle**' yi seçin. Proje düğümüne sağ tıklayıp > **başvuru** **Ekle** ' yi de seçebilirsiniz.

   **Başvuru Yöneticisi** açılır ve gruba göre kullanılabilir başvuruları listeler.

2. Eklenecek başvuruları belirtin ve ardından **Tamam**' ı seçin.

## <a name="assemblies-tab"></a>Derlemeler sekmesi

**Derlemeler** sekmesi, başvuru için kullanılabilen tüm .NET derlemelerini listeler. GAC içindeki derlemeler çalışma zamanı ortamının bir parçası olduğundan, **derlemeler** sekmesi genel derleme ÖNBELLEĞINDEN (GAC) herhangi bir derlemeyi listeetmez. GAC 'de kayıtlı bir derlemeye başvuru içeren bir uygulama dağıtırsanız ya da kopyalarsanız, derleme **Yerel** ayarından bağımsız olarak uygulamayla birlikte dağıtılmaz veya kopyalanmaz. Daha fazla bilgi için bkz. [bir projedeki başvuruları yönetme](../ide/managing-references-in-a-project.md).

EnvDTE ad alanlarının herhangi birine (<xref:EnvDTE>, <xref:EnvDTE80>, <xref:EnvDTE90>, <xref:EnvDTE90a>veya <xref:EnvDTE100>) el ile bir başvuru eklediğinizde, **Özellikler** penceresinde başvurunun **birlikte çalışma türlerini katıştır** özelliğini **false** olarak ayarlayın. Bu özelliğin **true** olarak ayarlanması, katıştırılamayan belirli EnvDTE özellikleri nedeniyle derleme sorunlarına neden olabilir.

Tüm masaüstü projeleri **mscorlib**'e örtük bir başvuru içerir. Visual Basic projeler <xref:Microsoft.VisualBasic>örtük bir başvuru içerir. Tüm projeler, başvurular listesinden kaldırılsa bile, **System. Core**'a örtük bir başvuru içerir.

Bir proje türü derlemeleri desteklemiyorsa, sekme başvuru Yöneticisi iletişim kutusunda görünmez.

**Derlemeler** sekmesi iki alt sekmeden oluşur:

1. **Framework** hedeflenen Çerçeveyi oluşturan tüm derlemeleri listeler.

   .NET Core veya Evrensel Windows Platformu hedeflenmiyor projeler için, **Framework** sekmesi hedeflenen çerçeveden derlemeleri sıralar. Kullanıcının, uygulamanın gerektirdiği tüm başvuruları eklemesi gerekir.

   Evrensel Windows projeleri, varsayılan olarak hedeflenen çerçevede bulunan tüm derlemelere başvurular içerir. Yönetilen projelerde, **Çözüm Gezgini** ' deki **Başvurular** klasörü altındaki salt okunurdur bir düğüm, tüm Framework başvurusunu gösterir. Buna uygun olarak, **Framework** sekmesi çerçeveden derlemelerin hiçbirini numaralandırmaz ve bunun yerine şu iletiyi görüntüler: "tüm Framework derlemelerine zaten başvuruluyor. Lütfen Framework 'teki başvuruları araştırmak için Nesne Tarayıcısı kullanın.

2. **Uzantılar** , bileşen ve denetimlerin dış satıcılarının hedeflenen Çerçeveyi genişletmek üzere geliştirildiği tüm derlemeleri listeler. Kullanıcı uygulamasının amacına bağlı olarak, bu derlemelere gerek duyulabilir.

   **Uzantılar** , aşağıdaki konumlarda kayıtlı olan derlemeler numaralandırılarak doldurulur:

   32 bit makine:
   - `HKEY_CURRENT_USER\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`
   - `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`

   64 bit makine:
   - `HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`
   - `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`

   Ve [hedef çerçeve tanımlayıcısı] daha eski sürümleri

   Örneğin, bir proje 32 bitlik bir makinede .NET Framework 4 ' ü hedefliyorsa, **Uzantılar** *\Microsoft\.NETFramework\v4.0\AssemblyFoldersEx*, *\Microsoft\.netframework\v3.5\assemblyfoldersex*, *\Microsoft\.netframework\v3,\assemblyfoldersex*ve *\Microsoft\.netframework\v2.0\assemblyfoldersex*altında kayıtlı derlemeleri numaralandırır.

Listedeki bazı bileşenler, projenizin Framework sürümüne bağlı olarak gösterilmeyebilir. Bu durum aşağıdaki koşullarda oluşabilir:

- Son kullanılan Framework sürümünü kullanan bir bileşen, önceki bir sürümü hedefleyen bir proje ile uyumsuzdur.

   Bir proje için hedef Framework sürümünü değiştirme hakkında daha fazla bilgi için bkz. [framework hedefleme genel bakış](visual-studio-multi-targeting-overview.md).

- .NET Framework 4 kullanan bir bileşen, .NET Framework 4,5 ' i hedefleyen bir projeyle uyumsuzdur.

Aynı çözümdeki başka bir projenin çıktılarına dosya başvuruları eklemekten kaçının, çünkü bunu yapmak derleme hatalarına neden olabilir. Bunun yerine, projeden projeye başvurular oluşturmak için **Başvuru Ekle** Iletişim kutusunun **Projeler** sekmesini kullanın. Bu, projelerinizde oluşturduğunuz sınıf kitaplıklarının daha iyi yönetimini etkinleştirerek takım geliştirmeyi kolaylaştırır. Daha fazla bilgi için bkz. [Hatalı başvuruların sorunlarını giderme](../ide/troubleshooting-broken-references.md).

> [!NOTE]
> Visual Studio 2015 veya sonraki sürümlerde, bir projenin hedef Framework sürümü .NET Framework 4,5 veya üzeri ise ve diğer projenin hedef sürümü .NET Framework 2, 3, 3,5 veya 4,0 ise, proje başvurusu yerine bir dosya başvurusu oluşturulur.

### <a name="to-display-an-assembly-in-the-add-reference-dialog-box"></a>Başvuru Ekle iletişim kutusunda bir derlemeyi göstermek için

- Derlemeyi aşağıdaki konumlardan birine taşıyın veya kopyalayın:

  - Geçerli proje dizini. (Bu derlemeleri, **tarayıcı** sekmesini kullanarak bulabilirsiniz.)

  - Aynı çözümdeki diğer proje dizinleri. ( **Projeler** sekmesini kullanarak bu derlemeleri bulabilirsiniz.)

  \- veya -

- Görüntülenecek derlemelerin konumunu belirten bir kayıt defteri anahtarı ayarlayın:

  32 bitlik bir işletim sistemi için aşağıdaki kayıt defteri anahtarlarından birini ekleyin.

  - `[HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  - `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  64 bitlik bir işletim sistemi için, 32 bit kayıt defteri kovanında aşağıdaki kayıt defteri anahtarlarından birini ekleyin.

  - `[HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  - `[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  *\<VersionMinimum\>* , uygulanan en düşük çerçeve sürümüdür. *\<VersionMinimum\>* v 3.0 Ise, *AssemblyFoldersEx* içinde belirtilen klasörler .NET Framework 3,0 ve üstünü hedefleyen projeler için geçerlidir.

  *\<AssemblyLocation\>* , **Başvuru Ekle** iletişim kutusunda görünmesini istediğiniz derlemelerin dizinidir, örneğin, *C:\MyAssemblies*.

  `HKEY_LOCAL_MACHINE` düğümü altında kayıt defteri anahtarı oluşturmak, tüm kullanıcıların **Başvuru Ekle** iletişim kutusunda belirtilen konumdaki derlemeleri görmesini sağlar. `HKEY_CURRENT_USER` düğümü altında kayıt defteri anahtarı oluşturmak yalnızca geçerli kullanıcının ayarını etkiler.

  **Başvuru Ekle** iletişim kutusunu tekrar açın. Derlemeler **.net** sekmesinde görünmelidir. Aksi takdirde, derlemelerin belirtilen *AssemblyLocation* dizininde bulunduğundan emin olun, Visual Studio 'yu yeniden başlatın ve yeniden deneyin.

## <a name="projects-tab"></a>Projeler sekmesi

**Projeler** sekmesi, geçerli çözüm içindeki tüm uyumlu projeleri **çözüm** alt sekmesinde listeler.

Proje, farklı bir Framework sürümünü hedefleyen başka bir projeye başvurabilir. Örneğin, .NET Framework 4 ' ü hedefleyen ancak .NET Framework 2 için oluşturulmuş bir derlemeye başvuran bir proje oluşturabilirsiniz. Ancak, .NET Framework 2 projesi bir .NET Framework 4 projesine başvuramaz. Daha fazla bilgi için bkz. [Çerçeve hedefleme genel bakış](../ide/visual-studio-multi-targeting-overview.md).

> [!NOTE]
> .NET Framework 4 ' ü hedefleyen bir proje, .NET Framework 4 Istemci profilini hedefleyen bir projeyle uyumsuzdur.

## <a name="shared-projects-tab"></a>Paylaşılan projeler sekmesi

Başvuru Yöneticisi iletişim kutusunun **Paylaşılan projeler** sekmesinde paylaşılan bir projeye bir başvuru ekleyin. [Paylaşılan projeler](/xamarin/cross-platform/app-fundamentals/shared-projects?tabs=windows) , bir dizi farklı uygulama projesinin başvurduğu ortak kod yazmanızı sağlar.

## <a name="universal-windows-tab"></a>Evrensel Windows sekmesi

**Evrensel Windows** sekmesi, Windows işletim sistemlerinin çalıştırıldığı platformlara özgü tüm SDK 'ları listeler.
Bu sekmenin iki alt grupları vardır: **çekirdek** ve **Uzantılar**.

### <a name="core-subgroup"></a>Çekirdek alt grubu

Evrensel Windows uygulaması projelerinin varsayılan olarak Evrensel Windows SDK başvurusu vardır. Buna uygun olarak, **başvuru yöneticisindeki** **çekirdek** alt grubu, Evrensel Windows SDK derlemelerin hiçbirini numaralandırmaz.

### <a name="extensions-subgroup"></a>Uzantılar alt grubu

**Uzantılar** , hedeflenen Windows platformunu genişleten Kullanıcı SDK 'larını listeler.

SDK, Visual Studio'nun tek bir bileşen olarak kabul ettiği dosyalar topluluğudur. **Uzantılar** sekmesinde, başvuru Yöneticisi iletişim kutusunun çağrıldığı proje Için uygulanan SDK 'lar tek girdi olarak listelenir. Bir projeye eklendiğinde, tüm SDK içeriği Visual Studio tarafından, kullanıcının IntelliSense, araç kutusu, tasarımcılar, Nesne Tarayıcısı, derleme, dağıtım, hata ayıklama ve paketleme içindeki SDK içeriğinden yararlanmak için başka bir eylem yapması gerekmez.

SDK 'larınızı **Uzantılar** sekmesinde görüntüleme hakkında daha fazla bilgi için bkz. [yazılım geliştirme seti oluşturma](../extensibility/creating-a-software-development-kit.md).

> [!NOTE]
> Bir proje, başka bir SDK 'ya bağlı olan bir SDK 'ya başvuruyorsa, ikinci SDK 'ya el ile bir başvuru eklemediğiniz takdirde Visual Studio ikinci SDK 'yı tüketmez. Bir Kullanıcı **Uzantılar** SEKMESINDE bir SDK seçtiğinde, başvuru Yöneticisi iletişim kutusu, Ayrıntılar bölmesindeki BAĞıMLıLıKLARı listeleyerek SDK bağımlılıklarını belirlemenize yardımcı olur.

Bir proje türü uzantıları desteklemiyorsa, bu sekme başvuru Yöneticisi iletişim kutusunda görünmez.

## <a name="com-tab"></a>COM sekmesi

**Com** sekmesi, başvuru için KULLANıLABILEN tüm com bileşenlerini listeler. Dahili bildirim içeren kayıtlı bir COM DLL öğesine başvuru eklemek isterseniz, önce DLL kaydını silin. Aksi halde, Visual Studio derleme başvurusunu yerel bir DLL yerine ActiveX denetimi olarak ekler.

Bir proje türü COM 'u desteklemiyorsa, sekme başvuru Yöneticisi iletişim kutusunda görünmez.

## <a name="browse"></a>Gözat

Dosya sistemindeki bir bileşene gitmek için, **Araştır** düğmesini kullanabilirsiniz.

Proje, farklı bir Framework sürümünü hedefleyen bir bileşene başvurabilir. Örneğin, .NET Framework 4,7 ' i hedefleyen, ancak .NET Framework 4 ' ü hedefleyen bir bileşene başvuran bir uygulama oluşturabilirsiniz. Daha fazla bilgi için bkz. [Çerçeve hedefleme genel bakış](../ide/visual-studio-multi-targeting-overview.md).

Aynı çözümdeki başka bir projenin çıktılarına dosya başvuruları eklemekten kaçının, çünkü bu durum derleme hatalarına neden olabilir. Bunun yerine, projeden projeye başvurular oluşturmak için başvuru Yöneticisi iletişim kutusunun **çözüm** sekmesini kullanın. Bu, projelerinizde oluşturduğunuz sınıf kitaplıklarının daha iyi yönetimini etkinleştirerek takım geliştirmeyi kolaylaştırır. Daha fazla bilgi için bkz. [Hatalı başvuruların sorunlarını giderme](../ide/troubleshooting-broken-references.md).

Bir SDK 'ya gözatamazsınız ve projenize ekleyemezsiniz. Yalnızca bir dosyaya (örneğin, bir derleme veya *. winmd*) gidebilir ve bu dosyayı projenize ekleyebilirsiniz.

Bir WinMD 'ye dosya başvurusu yaparken, beklenen Düzen *\<dosya adının >. winmd*, *\<filename >. dll*ve *\<filename >. pri* dosyalarının tümünün birbirlerine yerleştirilme halidir. Aşağıdaki senaryolarda bir WinMD'ye başvuruda bulunursanız, proje çıkış dizinine eksik bir dosya kümesi kopyalanır ve sonuç olarak, derleme ve çalışma zamanı hataları meydana gelir.

- **Yerel bileşen**: yerel bir proje, her ayrık ad alanı kümesi ve uygulamadan oluşan bir dll Için bir WinMD oluşturur. WinMD'ler ayrı adlara sahip olur. Bu yerel bileşen dosyasına başvurulduğunda, MSBuild, benzer şekilde adlandırılmış Wınmds 'nin bir bileşen yapmasını tanımaz. Sonuç olarak, yalnızca aynı ada sahip *\<filename >. dll* ve *\<filename >. winmd* kopyalanabilir ve çalışma zamanı hataları oluşur. Bu sorunu geçici olarak çözmek için bir uzantı SDK 'Sı oluşturun. Daha fazla bilgi için bkz. [yazılım geliştirme seti oluşturma](../extensibility/creating-a-software-development-kit.md).

- **Denetimleri**kullanma: bir XAML denetimi, en azından bir *\<dosya adı >. winmd*, *\<dosya adı >. dll*, *\<filename >. PRI*, *\<XamlName >. xaml*ve *\<ImageName >. jpg*' den oluşur. Proje yapılandırıldığında, dosya başvurusuyla ilişkili kaynak dosyaları projenin çıkış dizinine kopyalanmaz ve yalnızca *\<dosya adı >. winmd* *\<filename >. dll* ve *\<filename >. pri* kopyalanır. Kullanıcıyı *\<XamlName >. xaml* ve *\<ImageName >. jpg* eksik olduğunu bildirmek için bir derleme hatası günlüğe kaydedilir. Başarılı olması için, kullanıcının bu kaynak dosyaları oluşturma ve hata ayıklama/çalışma zamanı için proje çıkış dizinine el ile kopyalaması gerekir. Bu sorunu geçici olarak çözmek için, [yazılım geliştirme seti oluşturma](../extensibility/creating-a-software-development-kit.md) ' daki adımları izleyerek bir uzantı SDK 'sı oluşturun ya da aşağıdaki özelliği eklemek için proje dosyasını düzenleyin:

    ```xml
    <PropertyGroup>
       <GenerateLibraryOutput>True</GenerateLibraryOutput>
    </PropertyGroup>
    ```

    > [!NOTE]
    > Özelliği eklerseniz, yapı daha yavaş çalışabilir.

## <a name="recent"></a>En Son

**Derlemeler**, **com**, **Windows** **ve en son bir sekmeye** **gözatıp** , son olarak projelere eklenen bileşenlerin listesini numaralandırır.

## <a name="search"></a>Ara

Başvuru Yöneticisi iletişim kutusundaki arama çubuğu, odağa sahip olan sekmenin üzerinde çalışır. Örneğin, **çözüm** sekmesi odağa karşın bir Kullanıcı arama çubuğuna "sistem" yazdığında, çözüm "sistem" içeren bir proje adından oluşmadığı sürece arama hiçbir sonuç döndürmez.

## <a name="see-also"></a>Ayrıca bkz.

- [Bir projedeki başvuruları yönetme](../ide/managing-references-in-a-project.md)
