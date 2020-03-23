---
title: Başvuru Yöneticisi'ne referans ekleme
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595316"
---
# <a name="how-to-add-or-remove-references-by-using-the-reference-manager"></a>Nasıl adlandırılır: Başvuru Yöneticisi'ni kullanarak referans ekleme veya kaldırma

Sizin, Microsoft'un veya başka bir şirketin geliştirdiği bileşenlere başvurular eklemek ve yönetmek için Başvuru Yöneticisi iletişim kutusunu kullanabilirsiniz. Bir Evrensel Windows uygulaması geliştiriyorsanız, projeniz tüm doğru Windows SDK DLL'lerine otomatik olarak başvurur. Bir .NET uygulaması geliştiriyorsanız, projeniz otomatik olarak *mscorlib.dll'ye*başvurur. Bazı .NET API'leri, el ile eklemeniz gereken bileşenlerde açığa alınır. COM bileşenlerine veya özel bileşenlere yapılan başvurular el ile eklenmeli.

## <a name="reference-manager-dialog-box"></a>Başvuru Yöneticisi iletişim kutusu

Başvuru Yöneticisi iletişim kutusu, proje türüne bağlı olarak sol tarafta farklı kategoriler gösterir:

- **Çerçeve** ve Uzantıları alt grupları ile **derlemeler** **Extensions**

- **COM,** başvuru için kullanılabilen tüm COM bileşenlerini listeler

- **Projeler**

- **Paylaşılan Projeler**

- **Windows**, **Çekirdek** ve **Uzantıları** alt grupları ile. **Nesne**Tarayıcısı'nı kullanarak Windows SDK veya uzantı SDK'sındaki başvuruları keşfedebilirsiniz.

- **Gözat**, **Son** alt grup ile

## <a name="add-a-reference"></a>Referans ekleme

1. **Çözüm Gezgini'nde,** **Başvurular** veya **Bağımlılıklar** düğümüne sağ tıklayın ve **Kaynak Ekle'yi**seçin. Ayrıca proje düğümüne sağ tıklayıp**Referans** **Ekle'yi** > seçebilirsiniz.

   **Başvuru Yöneticisi,** kullanılabilir başvuruları grup olarak açar ve listeler.

2. Eklemek için başvuruları belirtin ve sonra **Tamam'ı**seçin.

## <a name="assemblies-tab"></a>Derlemeler sekmesi

**Derlemeler** sekmesi, başvuru için kullanılabilen tüm .NET derlemelerini listeler. **Derlemeler** sekmesi, GAC'deki derlemeler çalışma zamanı ortamının bir parçası olduğundan, genel derleme önbelleğinden (GAC) herhangi bir derlemeyi listelemiyor. GAC'de kayıtlı bir derlemeye başvuru içeren bir uygulamayı dağıtAbilir veya kopyalarsanız, Derleme **Yerel Kopyala** ayarından bağımsız olarak uygulamayla birlikte dağıtılamaz veya kopyalanamaz. Daha fazla bilgi için [bkz.](../ide/managing-references-in-a-project.md)

EnvDTE ad alanlarından herhangi biri için el<xref:EnvDTE>ile <xref:EnvDTE80> <xref:EnvDTE90>bir <xref:EnvDTE90a>başvuru <xref:EnvDTE100>eklediğinizde ( , , , , , veya ), **Özellikler** penceresinde **False'a** yapılan başvurunun **Embed Interop Türleri** özelliğini ayarlayın. Bu özelliği **True** olarak ayarlamak, katıştırılmış olamaz bazı EnvDTE özellikleri nedeniyle yapı sorunlarına neden olabilir.

Tüm masaüstü projeleri **mscorlib**için örtülü bir referans içerir. Visual Basic projeleri için <xref:Microsoft.VisualBasic>örtük bir başvuru içerir. Tüm projeler, başvuru listesinden kaldırılmış olsa bile **System.Core'a**örtülü bir başvuru içerir.

Proje türü derlemeleri desteklemiyorsa, sekme Başvuru Yöneticisi iletişim kutusunda görünmez.

**Derlemeler** sekmesi iki alt sekmeden oluşur:

1. **Çerçeve,** hedeflenen çerçeveyi oluşturan tüm derlemeleri listeler.

   .NET Core veya Evrensel Windows Platformu'nu hedeflemeyen projeler için **Framework** sekmesi, derlemeleri hedeflenen çerçeveden toplar. Kullanıcı, uygulamanın gerektirdiği başvuruları eklemelidir.

   Evrensel Windows projeleri varsayılan olarak hedeflenen çerçevedeki tüm derlemelere başvurular içerir. Yönetilen projelerde, **Çözüm Gezgini'ndeki** **Başvurular** klasörü altındaki salt okunur düğüm, tüm çerçeveye başvuruyu gösterir. Buna göre, **Framework** sekmesi çerçeveden derlemelerin hiçbirini sayısallandırmaz ve bunun yerine aşağıdaki iletiyi görüntüler: "Tüm Framework derlemeleri zaten başvurulmaktadır. Çerçevedeki referansları keşfetmek için lütfen Nesne Tarayıcısı'nı kullanın".

2. **Uzantılar,** bileşenlerin ve denetimlerin dış satıcılarının hedeflenen çerçeveyi genişletmek için geliştirdiği tüm derlemeleri listeler. Kullanıcı uygulamasının amacına bağlı olarak, bu derlemelere gerek duyulabilir.

   **Uzantılar,** aşağıdaki konumlarda kayıtlı olan derlemeleri numaralandırarak doldurulur:

   32 bit makine:
   - `HKEY_CURRENT_USER\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`
   - `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`

   64 bit makine:
   - `HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`
   - `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`

   Ve [Hedef Çerçeve Tanımlayıcısı] eski sürümleri

   Örneğin, bir proje 32 bit lik bir makinede .NET Framework 4'ü hedefliyorsa, **Uzantılar** *\Microsoft\.NETFramework\v4.0\AssemblyFoldersEx*, *\Microsoft\.NETFramework\v3.5\AssemblyFoldersEx*, *\Microsoft\.NETFramework\v3.0\AssemblyFoldersEx*ve *\Microsoft\.NETFramework\v2.0\AssemblyFoldersEx*altında kayıtlı derlemeleri numaralandırır.

Projenizin çerçeve sürümüne bağlı olarak listedeki bazı bileşenler gösterilmeyebilir. Bu, aşağıdaki koşullar altında oluşabilir:

- Son çerçeve sürümünü kullanan bir bileşen, önceki bir sürümü hedefleyen bir projeyle uyumsuzdur.

   Bir projenin hedef çerçeve sürümünün nasıl değiştirilenhakkında bilgi için [bkz.](visual-studio-multi-targeting-overview.md)

- .NET Framework 4 kullanan bir bileşen, .NET Framework 4.5'i hedefleyen bir projeyle uyumsuzdur.

Bunu yapmak derleme hatalarına neden olabileceğinden, aynı çözümdeki başka bir projenin çıktılarına dosya başvuruları eklemekten kaçınmalısınız. Bunun yerine, projeden projeye başvurular oluşturmak için **Başvuru Ekle** iletişim kutusunun **Projeler** sekmesini kullanın. Bu, projelerinizde oluşturduğunuz sınıf kitaplıklarının daha iyi yönetilmesini sağlayarak ekip geliştirmeyi kolaylaştırır. Daha fazla bilgi için [bozuk başvuruları Giderme Sorunu'na](../ide/troubleshooting-broken-references.md)bakın.

> [!NOTE]
> Visual Studio 2015 veya sonraki sürümlerde, bir projenin hedef çerçeve sürümü .NET Framework 4.5 veya sonraki ise proje başvurusu yerine bir dosya başvurusu oluşturulur ve diğer projenin hedef sürümü .NET Framework 2, 3, 3.5 veya 4.0'dır.

### <a name="to-display-an-assembly-in-the-add-reference-dialog-box"></a>Başvuru Ekle iletişim kutusunda bir derleme görüntülemek için

- Derlemeyi aşağıdaki konumlardan birine taşıyın veya kopyalayın:

  - Geçerli proje dizini. **(Gözat** sekmesini kullanarak bu derlemeleri bulabilirsiniz.)

  - Aynı çözümdeki diğer proje dizinleri. (Projeler sekmesini kullanarak bu **Projects** derlemeleri bulabilirsiniz.)

  \-veya -

- Görüntülemek için derlemelerin konumunu belirten bir kayıt defteri anahtarı ayarlayın:

  32 bit işletim sistemi için aşağıdaki kayıt defteri anahtarlarından birini ekleyin.

  - `[HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  - `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  64 bit işletim sistemi için, 32 bit kayıt defteri kovanına aşağıdaki kayıt defteri anahtarlarından birini ekleyin.

  - `[HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  - `[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  *VersionMinimum\> geçerli olan en düşük çerçeve sürümüdür. \<* *VersionMinimum\> v3.0 ise, AssemblyFoldersEx'te belirtilen klasörler .NET Framework 3.0 ve sonraki projeleri hedefleyen projeler için geçerlidir. \<* *AssemblyFoldersEx*

  AssemblyLocation, *\> Kaynak Ekle iletişim kutusunda görünmesini istediğiniz derlemelerin dizinidir( örneğin, C:\MyAssemblies. \<* **Add Reference** *C:\MyAssemblies*

  Düğüm altında `HKEY_LOCAL_MACHINE` kayıt defteri anahtarı oluşturmak, tüm kullanıcıların **Başvuru Ekle** iletişim kutusunda belirtilen konumdaki derlemeleri görmesini sağlar. `HKEY_CURRENT_USER` Düğüm altında kayıt defteri anahtarı oluşturma geçerli kullanıcı için yalnızca ayarı etkiler.

  Başvuru **Ekle** iletişim kutusunu yeniden açın. Derlemeler **.NET** sekmesinde görünmelidir. Yoksa, derlemelerin belirtilen *AssemblyLocation* dizininde bulunduğundan emin olun, Visual Studio'yu yeniden başlatın ve yeniden deneyin.

## <a name="projects-tab"></a>Projeler sekmesi

**Projeler** sekmesi, **çözüm** alt sekmesinde geçerli çözüm deki tüm uyumlu projeleri listeler.

Proje, farklı bir çerçeve sürümünü hedefleyen başka bir projeye başvuruyapabilir. Örneğin, .NET Framework 4'e yönelik ancak .NET Framework 2 için oluşturulmuş bir derlemeye başvuran bir proje oluşturabilirsiniz. Ancak,.NET Framework 2 projesi bir .NET Framework 4 projesine başvuru yapamaz. Daha fazla bilgi için çerçeve [hedefleme genel bakış'a](../ide/visual-studio-multi-targeting-overview.md)bakın.

> [!NOTE]
> .NET Framework 4'e yönelik bir proje, .NET Framework 4 İstemci Profilini hedefleyen bir projeyle uyumsuzdur.

## <a name="shared-projects-tab"></a>Paylaşılan Projeler sekmesi

Başvuru Yöneticisi iletişim kutusunun **Paylaşılan Projeler** sekmesinde paylaşılan bir projeye başvuru ekleyin. [Paylaşılan Projeler,](/xamarin/cross-platform/app-fundamentals/shared-projects?tabs=windows) bir dizi farklı uygulama projesitarafından başvurulan ortak kodu yazmanıza izin sağlar.

## <a name="universal-windows-tab"></a>Evrensel Windows sekmesi

**Evrensel Windows** sekmesi, Windows işletim sistemlerinin çalıştığı platformlara özgü tüm SDK'ları listeler.
Bu sekmede iki alt grup vardır: **Çekirdek** ve **Uzantılar.**

### <a name="core-subgroup"></a>Çekirdek alt grup

Evrensel Windows uygulama projelerinde varsayılan olarak Evrensel Windows SDK'ya başvuru vardır. Buna göre, **Başvuru Yöneticisi'ndeki** **Çekirdek** alt grubu Evrensel Windows SDK'daki derlemelerin hiçbirini numarasılmaz.

### <a name="extensions-subgroup"></a>Uzantıları alt grubu

**Uzantılar,** hedeflenen Windows platformlarını genişleten kullanıcı SDK'larını listeler.

SDK, Visual Studio'nun tek bir bileşen olarak kabul ettiği dosyalar topluluğudur. **Uzantılar** sekmesinde, Başvuru Yöneticisi iletişim kutusunun çağrıldığı projeye uygulanan SDK'lar tek giriş olarak listelenir. Bir projeye eklendiğinde, Tüm SDK içeriği Visual Studio tarafından tüketilir, bu nedenle kullanıcının IntelliSense, araç kutusu, tasarımcılar, Object Browser, build, deployment, debugging ve paketlemedeki SDK içeriğinden yararlanmak için başka eylemlerde olması gerekmez.

SDK'nızı **Uzantılar** sekmesinde nasıl görüntüleneceksiniz hakkında bilgi [için](../extensibility/creating-a-software-development-kit.md)bkz.

> [!NOTE]
> Bir proje başka bir SDK'ya bağlı bir SDK'ya başvuruyorsa, ikinci SDK'ya el ile bir başvuru eklemediğiniz sürece Visual Studio ikinci SDK'yı kullanmaz. Bir kullanıcı **Uzantılar** sekmesinde bir SDK seçtiğinde, Başvuru Yöneticisi iletişim kutusu ayrıntılar bölmesinde herhangi bir bağımlılık ları listeleyerek SDK bağımlılıklarını belirlemenize yardımcı olur.

Proje türü uzantıları desteklemiyorsa, bu sekme Başvuru Yöneticisi iletişim kutusunda görünmez.

## <a name="com-tab"></a>COM sekmesi

**COM** sekmesi, başvuru için kullanılabilen tüm COM bileşenlerini listeler. Dahili bildirim içeren kayıtlı bir COM DLL öğesine başvuru eklemek isterseniz, önce DLL kaydını silin. Aksi takdirde, Visual Studio montaj başvurusunu yerel dll yerine ActiveX denetimi olarak ekler.

Proje türü COM'u desteklemiyorsa, sekme Başvuru Yöneticisi iletişim kutusunda görünmez.

## <a name="browse"></a>Göz at

Dosya sistemindeki bir bileşene göz atmak için **Gözat** düğmesini kullanabilirsiniz.

Proje, farklı bir çerçeve sürümünü hedefleyen bir bileşene başvuruyapabilir. Örneğin, .NET Framework 4.7'yi hedefleyen ancak .NET Framework 4'e başvuran bir bileşene başvuran bir uygulama oluşturabilirsiniz. Daha fazla bilgi için çerçeve [hedefleme genel bakış'a](../ide/visual-studio-multi-targeting-overview.md)bakın.

Bu taktik derleme hatalarına neden olabileceğinden, aynı çözümde başka bir projenin çıktılarına dosya başvuruları eklemekten kaçının. Bunun yerine, projeden projeye başvurular oluşturmak için Başvuru Yöneticisi iletişim kutusunun **Çözüm** sekmesini kullanın. Bu, projelerinizde oluşturduğunuz sınıf kitaplıklarının daha iyi yönetilmesini sağlayarak ekip geliştirmeyi kolaylaştırır. Daha fazla bilgi için [bozuk başvuruları Giderme Sorunu'na](../ide/troubleshooting-broken-references.md)bakın.

Bir SDK'ya göz atanın ve projenize ekemezsiniz. Yalnızca bir dosyaya (örneğin, derleme veya *.winmd)* göz atabilir ve projenize ekleyebilirsiniz.

Bir WinMD için bir dosya başvurusu yaparken, beklenen düzen * \<FileName>.winmd*, * \<FileName>.dll*ve * \<FileName>.pri* dosyaları nın yan yana yerleştirilmesidir. Aşağıdaki senaryolarda bir WinMD'ye başvuruda bulunursanız, proje çıkış dizinine eksik bir dosya kümesi kopyalanır ve sonuç olarak, derleme ve çalışma zamanı hataları meydana gelir.

- **Yerel bileşen:** yerel bir proje, her ayrık ad alanı kümesi için bir WinMD ve uygulamadan oluşan bir DLL oluşturur. WinMD'ler ayrı adlara sahip olur. Bu yerel bileşen dosyasına başvururken, MSBuild farklı adlandırılmış WinMD'lerin tek bir bileşen oluşturduğunu tanımaz. Sonuç olarak, yalnızca aynı adı verilen * \<FileName>.dll* ve * \<FileName>.winmd* kopyalanır ve çalışma zamanı hataları oluşur. Bu sorunu çözmek için bir uzantı SDK oluşturun. Daha fazla bilgi için [bkz.](../extensibility/creating-a-software-development-kit.md)

- **Tüketen kontroller**: en azından, bir XAML kontrol * \<filename>.winmd,* * \<FileName>.dll,* * \<FileName>.pri,* * \<XamlName>.xaml*ve * \<imagename>.jpg*oluşur. Proje oluşturulduğunda, dosya başvurusuyla ilişkili kaynak dosyaları projenin çıktı dizinine kopyalanmayacak ve yalnızca * \<FileName>.winmd*, * \<FileName>.dll* ve * \<FileName>.pri* kopyalanır. * \<XamlName>.xaml* ve * \<ImageName>.jpg* kaynaklarının eksik olduğunu kullanıcıya bildirmek için bir yapı hatası kaydedilir. Başarılı olması için, kullanıcının bu kaynak dosyaları oluşturma ve hata ayıklama/çalışma zamanı için proje çıkış dizinine el ile kopyalaması gerekir. Bu sorunu çözmek için, [Yazılım Geliştirme Kiti Oluştur'daki](../extensibility/creating-a-software-development-kit.md) adımları izleyerek bir uzantı SDK oluşturun veya aşağıdaki özelliği eklemek için proje dosyasını düzenleyin:

    ```xml
    <PropertyGroup>
       <GenerateLibraryOutput>True</GenerateLibraryOutput>
    </PropertyGroup>
    ```

    > [!NOTE]
    > Özelliği eklerseniz, yapı daha yavaş çalışabilir.

## <a name="recent"></a>En Son

**Derlemeler**, **COM**, **Windows**ve **Gözat** her destek son projelere eklenen bileşenlerin listesini listeler **Yeni** sekmesi.

## <a name="search"></a>Search

Başvuru Yöneticisi iletişim kutusundaki arama çubuğu, odakta bulunan sekme üzerinden çalışır. Örneğin, **çözüm** sekmesi odaktayken bir kullanıcı arama çubuğuna "Sistem" yazarsa, çözüm "Sistem" içeren bir proje adından oluştuğu sürece arama sonuç döndürmez.

## <a name="see-also"></a>Ayrıca bkz.

- [Bir projedeki başvuruları yönetme](../ide/managing-references-in-a-project.md)
