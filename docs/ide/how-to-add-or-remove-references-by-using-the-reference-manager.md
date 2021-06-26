---
title: Başvuru Yöneticisi 'ne başvurular ekleme
description: Geliştirilmiş bileşenlere başvurular eklemek ve bunları yönetmek için başvuru Yöneticisi iletişim kutusunu nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 08/02/2019
ms.topic: how-to
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
ms.workload:
- multiple
ms.openlocfilehash: 552ec8364bb58b72199bacecca99283303eb174c
ms.sourcegitcommit: d3658667e768d7516cbf4461ec47bf24c8fcb7e6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112924922"
---
# <a name="how-to-add-or-remove-references-by-using-the-reference-manager"></a>Nasıl yapılır: başvuru Yöneticisi 'ni kullanarak başvuru ekleme veya kaldırma

Sizin, Microsoft veya başka bir şirketinizin geliştirdiği bileşenlere başvurular eklemek ve bunları yönetmek için başvuru Yöneticisi iletişim kutusunu kullanabilirsiniz. Bir Evrensel Windows uygulaması geliştiriyorsanız, projeniz otomatik olarak doğru Windows SDK dll 'Lerine başvurur. Bir .NET uygulaması geliştiriyorsanız, projeniz otomatik olarak *mscorlib.dll* başvurur. Bazı .NET API 'Leri, el ile eklemeniz gereken bileşenlerde kullanıma sunulur. COM bileşenlerine veya özel bileşenlere yapılan başvuruların el ile eklenmesi gerekir.

## <a name="reference-manager-dialog-box"></a>Başvuru Yöneticisi iletişim kutusu

Başvuru Yöneticisi iletişim kutusu, proje türüne bağlı olarak sol tarafta farklı kategoriler gösterir:

- **Derlemeler**, **çerçeve** ve **Uzantılar** alt grupları ile

- **Com** , başvuruda bulunan tüm com bileşenlerini listeler

- **Projeler**

- **Paylaşılan projeler**

- **Windows**, **çekirdek** ve **Uzantılar** alt grupları ile. **Nesne tarayıcısı** kullanarak Windows SDK veya uzantı SDK 'lerinde başvuruları inceleyebilirsiniz.

- **En son** alt grup ile **tarama**
 
    > [!NOTE]
    > C++ projeleri geliştiriyorsanız başvuru Yöneticisi iletişim kutusunda **gözatamıyorum** ' a bakabilirsiniz.

## <a name="add-a-reference"></a>Başvuru ekleme

1. **Çözüm Gezgini**, **Başvurular** veya **Bağımlılıklar** düğümüne sağ tıklayın ve **Başvuru Ekle**' yi seçin. Ayrıca, proje düğümüne sağ tıklayıp başvuru **Ekle**' yi seçebilirsiniz  >  .

   **Başvuru Yöneticisi** açılır ve gruba göre kullanılabilir başvuruları listeler.

2. Eklenecek başvuruları belirtin ve ardından **Tamam**' ı seçin.

## <a name="assemblies-tab"></a>Derlemeler sekmesi

**Derlemeler** sekmesi, başvuru için kullanılabilen tüm .NET derlemelerini listeler. GAC içindeki derlemeler çalışma zamanı ortamının bir parçası olduğundan, **derlemeler** sekmesi genel derleme ÖNBELLEĞINDEN (GAC) herhangi bir derlemeyi listeetmez. GAC 'de kayıtlı bir derlemeye başvuru içeren bir uygulama dağıtırsanız ya da kopyalarsanız, derleme **Yerel** ayarından bağımsız olarak uygulamayla birlikte dağıtılmaz veya kopyalanmaz. Daha fazla bilgi için bkz. [bir projedeki başvuruları yönetme](../ide/managing-references-in-a-project.md).

EnvDTE ad alanlarından herhangi birine (,,, veya) el ile bir başvuru eklediğinizde <xref:EnvDTE> <xref:EnvDTE80> <xref:EnvDTE90> <xref:EnvDTE90a> <xref:EnvDTE100> , **Özellikler** penceresinde başvurunun **birlikte çalışma türlerini katıştır** özelliğini **false** olarak ayarlayın. Bu özelliğin **true** olarak ayarlanması, katıştırılamayan belirli EnvDTE özellikleri nedeniyle derleme sorunlarına neden olabilir.

Tüm masaüstü projeleri **mscorlib**'e örtük bir başvuru içerir. Visual Basic projeler öğesine örtük bir başvuru içerir <xref:Microsoft.VisualBasic> . Tüm projeler, başvurular listesinden kaldırılsa bile, **System. Core**'a örtük bir başvuru içerir.

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

   Örneğin, bir proje 32 bitlik bir makinede .NET Framework 4 ' ü hedefliyorsa, **Uzantılar** *\Microsoft \. NETFramework\v4.0\AssemblyFoldersEx*, *\Microsoft \. Netframework\v3.5\assemblyfoldersex*, *\Microsoft \. Netframework\v3.0\assemblyfoldersex* ve *\Microsoft \. netframework\v2.0\assemblyfoldersex* altında kayıtlı derlemeleri numaralandırır.

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

  \- veya

- Görüntülenecek derlemelerin konumunu belirten bir kayıt defteri anahtarı ayarlayın:

  32 bitlik bir işletim sistemi için aşağıdaki kayıt defteri anahtarlarından birini ekleyin.

  - `[HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  - `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  64 bitlik bir işletim sistemi için, 32 bit kayıt defteri kovanında aşağıdaki kayıt defteri anahtarlarından birini ekleyin.

  - `[HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  - `[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  *\<VersionMinimum\>* , uygulanan en düşük çerçeve sürümüdür. *\<VersionMinimum\>* V 3.0 ise, *AssemblyFoldersEx* içinde belirtilen klasörler, .NET Framework 3,0 ve üstünü hedefleyen projeler için geçerlidir.

  *\<AssemblyLocation\>* , **Başvuru Ekle** iletişim kutusunda görünmesini istediğiniz derlemelerin dizinidir, örneğin, *C:\MyAssemblies*.

  Düğüm altında kayıt defteri anahtarı oluşturulması, `HKEY_LOCAL_MACHINE` tüm kullanıcıların **Başvuru Ekle** iletişim kutusunda belirtilen konumdaki derlemeleri görmesini sağlar. Düğüm altında kayıt defteri anahtarı oluşturulması `HKEY_CURRENT_USER` yalnızca geçerli kullanıcının ayarını etkiler.

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

Proje türü uzantıları desteklemezse, Başvuru Yöneticisi iletişim kutusunda bu sekme görünmez.

## <a name="com-tab"></a>COM sekmesi

**COM sekmesi,** başvuru için kullanılabilen tüm COM bileşenlerini listeler. Dahili bildirim içeren kayıtlı bir COM DLL öğesine başvuru eklemek isterseniz, önce DLL kaydını silin. Aksi Visual Studio derleme başvurularını yerel DLL yerine ActiveX denetimi olarak ekler.

Bir proje türü COM'yi desteklemezse, Başvuru Yöneticisi iletişim kutusunda sekme görünmez.

## <a name="browse"></a>Gözat

Dosya sisteminde **bir** bileşene göz atmak için Gözat düğmesini kullanabilirsiniz.

Proje, farklı bir çerçeve sürümünü hedef alan bir bileşene başvurur. Örneğin, 4.7'ye .NET Framework ancak 4'ü hedef alan bir bileşene .NET Framework oluşturabilirsiniz. Daha fazla bilgi için [bkz. Çerçeve hedeflemeye genel bakış.](../ide/visual-studio-multi-targeting-overview.md)

Bu taktik derleme hatalarına neden olduğundan, aynı çözümdeki başka bir projenin çıkışlarına dosya başvuruları eklemekten kaçının. Bunun yerine, **projeden** projeye başvurular oluşturmak için Başvuru Yöneticisi iletişim kutusunun Çözüm sekmesini kullanın. Bu, projeleriniz içinde oluşturdukları sınıf kitaplıklarının daha iyi yönetimini sağlayarak takım geliştirmeyi kolaylaştırır. Daha fazla bilgi için [bkz. Bozuk başvurularla ilgili sorunları giderme.](../ide/troubleshooting-broken-references.md)

Bir SDK'ya göz atabilir ve bunu projenize ekliyebilirsiniz. Bir dosyaya (örneğin, bir derleme veya *.winmd) göz atabilir* ve bunu projenize eklersiniz.

Bir WinMD'ye dosya başvurusu yaparken beklenen *\<FileName> düzen, .winmd*, *\<FileName>.dll* ve *\<FileName> .pri* dosyalarının birlikte yerleştirilmiş olmasıdır. Aşağıdaki senaryolarda bir WinMD'ye başvuruda bulunursanız, proje çıkış dizinine eksik bir dosya kümesi kopyalanır ve sonuç olarak, derleme ve çalışma zamanı hataları meydana gelir.

- **Yerel bileşen:** Yerel bir proje, her ayrık ad alanı kümesi için bir WinMD ve uygulamadan oluşan bir DLL oluşturur. WinMD'ler ayrı adlara sahip olur. MsBuild, bu yerel bileşen dosyasına başvurulurken, farklı olarak adlandırılmış WinMD'ler tek bir bileşen olduğunu tanımaz. Sonuç olarak, yalnızca aynı adlı *\<FileName>.dll* *\<FileName> ve .winmd* kopyalanır ve çalışma zamanı hataları oluşur. Bu sorunu gidermek için bir uzantı SDK'sı oluşturun. Daha fazla bilgi için [bkz. Yazılım Geliştirme Seti Oluşturma.](../extensibility/creating-a-software-development-kit.md)

- **Denetimleri tüketen:** XAML denetimi en azından *\<FileName> bir .winmd*, *\<FileName>.dll*, *\<FileName> .pri*, *\<XamlName> .xaml* ve bir *\<ImageName>.jpg.* Proje yerleşik olduğunda, dosya başvurusuyla ilişkili kaynak dosyaları projenin çıkış dizinine kopyalanmaz ve yalnızca *\<FileName> .winmd*, *\<FileName>.dll* *\<FileName> ve .pri* kopyalanır. Kullanıcıya *\<XamlName> .xaml* ve.jpgkaynaklarının eksik *\<ImageName> olduğunu bildirmek için bir derleme* hatası günlüğe kaydedilir. Başarılı olması için, kullanıcının bu kaynak dosyaları oluşturma ve hata ayıklama/çalışma zamanı için proje çıkış dizinine el ile kopyalaması gerekir. Bu sorunu gidermek için Yazılım Geliştirme Seti Oluşturma'daki adımları kullanarak bir uzantı SDK'sı oluşturun veya aşağıdaki özelliği eklemek için proje dosyasını düzenleyin: [](../extensibility/creating-a-software-development-kit.md)

    ```xml
    <PropertyGroup>
       <GenerateLibraryOutput>True</GenerateLibraryOutput>
    </PropertyGroup>
    ```

    > [!NOTE]
    > Özelliği eklerseniz, yapı daha yavaş çalışabilir.

## <a name="recent"></a>En Son

**Derlemeler,** **COM**, **Windows** ve  **Gözat** her biri, projelere son eklenen bileşenlerin listesini listeleen Bir Son Kullanılan sekmesini destekler.

## <a name="search"></a>Arayın

Başvuru Yöneticisi iletişim kutusundaki arama çubuğu, odakta olan sekme üzerinde çalışır. Örneğin, Çözüm sekmesi odaktayken bir kullanıcı arama  çubuğuna "Sistem" yazsa, çözüm "Sistem" içeren bir proje adı içerdiği sürece arama herhangi bir sonuç dönmez.

## <a name="see-also"></a>Ayrıca bkz.

- [Bir projedeki başvuruları yönetme](../ide/managing-references-in-a-project.md)
