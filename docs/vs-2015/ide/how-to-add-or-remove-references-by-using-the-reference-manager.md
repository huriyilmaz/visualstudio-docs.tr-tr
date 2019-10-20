---
title: "Nasıl yapılır: başvuru Yöneticisi 'ni kullanarak başvuru ekleme veya kaldırma | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ReferenceManager
helpviewer_keywords:
- Visual C# projects, references
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
ms.assetid: 1aabb520-99b0-46c6-9368-21b4d84793eb
caps.latest.revision: 48
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 04b6573b6cd04b5a061a40025a9872d9972e35cb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645477"
---
# <a name="how-to-add-or-remove-references-by-using-the-reference-manager"></a>Nasıl Yapılır: Başvuru Yöneticisi'ni Kullanarak Başvuru Ekleme veya Kaldırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sizin, Microsoft veya başka bir şirketinizin geliştirdiği bileşenlere başvurular eklemek ve bunları yönetmek için **başvuru Yöneticisi** iletişim kutusunu kullanabilirsiniz. Bir Evrensel Windows uygulaması geliştiriyorsanız, projeniz otomatik olarak doğru Windows SDK dll 'Lerine başvurur. Bir .NET uygulaması geliştiriyorsanız, projeniz mscorlib. dll dosyasına otomatik olarak başvurur. Bazı .NET API 'Leri, el ile eklemeniz gereken bileşenlerde kullanıma sunulur. COM bileşenlerine veya özel bileşenlere yapılan başvuruların el ile eklenmesi gerekir.

## <a name="adding-and-removing-a-reference"></a>Başvuru Ekleme ve Kaldırma

#### <a name="to-add-a-reference"></a>Başvuru eklemek için

1. **Çözüm Gezgini**, Başvurular düğümüne sağ tıklayın ve **Başvuru Ekle**' yi seçin.

2. Eklenecek başvuruları belirtin ve sonra **Tamam** düğmesini seçin.

   **Başvuru Yöneticisi** açılır ve gruba göre kullanılabilir başvuruları listeler. Aşağıdaki grupların hangilerinin görüneceğini proje türü belirler:

- Derlemeler; Çerçeve ve Uzantılar alt grupları ile.

- Çözüm; Projeler alt grubu ile.

- Windows; Çekirdek ve Uzantılar alt grupları ile. **Nesne tarayıcısı**kullanarak Windows SDK veya uzantı SDK 'lerinde başvuruları inceleyebilirsiniz.

- Gözat; En Son alt grubu ile.

## <a name="assemblies-tab"></a>Derlemeler sekmesi
 **Derlemeler** sekmesi, başvuru için kullanılabilen tüm .NET Framework derlemeleri listeler. GAC içindeki derlemeler çalışma zamanı ortamının bir parçası olduğundan, **derlemeler** sekmesi genel derleme ÖNBELLEĞINDEN (GAC) herhangi bir derlemeyi listeetmez. GAC'de kayıtlı bir derlemeye başvuru içeren bir uygulamayı dağıtır ya da kopyalarsanız, derleme 'Yereli Kopyala' ayarına bakılmaksızın uygulama ile birlikte dağıtılmaz veya kopyalanmaz. Daha fazla bilgi için bkz. [Proje başvuruları](http://go.microsoft.com/fwlink/?LinkId=238512).

 EnvDTE ad alanlarının herhangi birine (EnvDTE, EnvDTE80, EnvDTE90, EnvDTE90a veya EnvDTE100) el ile bir başvuru eklediğinizde, Özellikler penceresinde başvurunun 'Birlikte Çalışma Türlerini Katıştır' özelliğini False olarak ayarlayın. Bu özelliğin True olarak ayarlanması, katıştırılamayan belirli EnvDTE özellikleri nedeniyle derleme sorunlarına yol açabilir.

 Tüm masaüstü projeleri, mscorlib öğesine örtük bir başvuru içerir. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projeler Microsoft. VisualBasic 'e örtülü bir başvuru içerir. @No__t_0, tüm projeler, başvurular listesinden kaldırılsa bile, System. Core 'a örtük bir başvuru içerir.

 Bir proje türü derlemeleri desteklemiyorsa, sekme **başvuru Yöneticisi** iletişim kutusunda görünmez.

 Derlemeler sekmesi iki alt sekmeden oluşur:

1. Çerçeve, hedef alınan Çerçeveyi oluşturan tüm derlemeleri listeler.

   - Projeniz hedeflenen Çerçevenin bir Profilini hedef aldığında, tanıtılan derlemeler Tam Çerçeve içindedir ve Çerçeve listesinde numaralandırılır. Tanıtılan derlemeler, projenin hedeflenen Çerçeve profilindeki mevcut derlemelerden ayırt edilmelerini sağlamak için gri renktedir. Örneğin, bir proje .NET Framework 4 İstemcisi'ni hedef alıyorsa, Çerçeve listesi .NET Framework 4 kaynaklı tanıtılan derlemeleri gösterir. Kullanıcı tanıtılan bir derlemeyi eklediğinde, **başvuru Yöneticisi** iletişim kutusu kapatıldıktan sonra, proje .NET Framework 4 ' e yeniden hedeflenecek ve tanıtılan derleme eklenecek şekilde bildirilir.

   - @No__t_0 uygulamalar için projeler, proje oluşturma sırasında hedeflenen [!INCLUDE[net_win8_profile](../includes/net-win8-profile-md.md)] tüm derlemelere yönelik başvuruları içerir. Yönetilen projelerde, **Çözüm Gezgini** ' deki başvurular klasörü altındaki salt okunurdur bir düğüm, tüm Framework başvurusunu gösterir. Buna göre, Çerçeve sekmesi, Çerçeve kaynaklı derlemelerin hiçbirini numaralandırmaz ve bunun yerine şu iletiyi görüntüler: "Tüm Framework derlemelerine zaten başvurulmuş. Lütfen Framework içindeki başvuruları araştırmak için Nesne Tarayıcısı kullanın. " Masaüstü projeleri için, Framework sekmesi hedeflenen çerçeveden derlemeleri sıralar ve kullanıcının, uygulamanın gerektirdiği başvuruları eklemesi gerekir.

2. Uzantılar, harici bileşen ve denetim satıcılarının hedeflenen Çerçeveyi genişletmek için geliştirdiği tüm derlemeleri listeler. Kullanıcı uygulamasının amacına bağlı olarak, bu derlemelere gerek duyulabilir.

   - Uzantılar, aşağıdaki konumlarda kayıtlı derlemeleri numaralandırmak suretiyle doldurulur:

       ```
       32-bit machine:
       HKEY_CURRENT_USER\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]
       HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]
       64-bit machine:
       HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]
       HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]
       And older versions of the [Target Framework Identifier]
       ```

        Örneğin, bir proje 32 bitlik bir makinede .NET Framework 4 ' ü hedefliyorsa, uzantılar \Microsoft \\. NETFramework\v4.0\AssemblyFoldersEx \\, \Microsoft \\. NETFramework\v3.5\ altında kayıtlı derlemeleri numaralandırır. AssemblyFoldersEx \\, \Microsoft \\. Netframework\v3,\assemblyfoldersex \\ ve \Microsoft \\. NETFramework\v2.0\AssemblyFoldersEx \\.

   Listedeki bazı bileşenler, projenizin [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] sürümüne bağlı olarak gösterilmeyebilir. Bu durum aşağıdaki koşullarda oluşabilir:

- .NET Framework son sürümünü kullanan bir bileşen, .NET Framework önceki bir sürümünü hedefleyen bir proje ile uyumsuzdur.

     Bir proje için hedef .NET Framework sürümünün nasıl değiştirileceği hakkında bilgi için bkz. [nasıl yapılır: .NET Framework bir sürümünü hedefleme](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

- @No__t_0 kullanan bir bileşen, [!INCLUDE[net_v45](../includes/net-v45-md.md)] hedefleyen bir projeyle uyumsuzdur.

     Yeni bir uygulama oluşturduğunuzda, bazı projeler varsayılan olarak [!INCLUDE[net_v45](../includes/net-v45-md.md)] hedefleyin. Daha fazla bilgi için bkz. [.NET Framework Istemci profili](https://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1).

- Aynı çözümdeki başka bir projenin çıktılarına dosya başvuruları eklemekten kaçının, çünkü bunu yapmak derleme hatalarına neden olabilir. Bunun yerine, projeden projeye başvurular oluşturmak için **Başvuru Ekle** Iletişim kutusunun **Projeler** sekmesini kullanın. Bu, projelerinizde oluşturduğunuz sınıf kitaplıklarının daha iyi yönetimini etkinleştirerek takım geliştirmeyi kolaylaştırır. Daha fazla bilgi için bkz. [Hatalı başvuruların sorunlarını giderme](../ide/troubleshooting-broken-references.md).

- > [!NOTE]
    > Visual Studio 2015 ' de, bir projenin .NET Framework hedef sürümü 4,5 ise ve diğer projenin hedef sürümü sürüm 2, 3, 3,5 veya 4,0 ise, proje başvurusu yerine bir dosya başvurusu oluşturulur.

#### <a name="to-display-an-assembly-in-the-add-reference-dialog-box"></a>Başvuru Ekle iletişim kutusunda bir derlemeyi göstermek için

- Derlemeyi aşağıdaki konumlardan birine taşıyın veya kopyalayın:

  - Geçerli proje dizini. (Bu derlemeleri, **tarayıcı** sekmesini kullanarak bulabilirsiniz.)

  - Aynı çözümdeki diğer proje dizinleri. ( **Projeler** sekmesini kullanarak bu derlemeleri bulabilirsiniz.)

    \- veya-

- Görüntülenecek derlemelerin konumunu belirten bir kayıt defteri anahtarı ayarlayın:

   32 bitlik bir işletim sistemi için aşağıdaki kayıt defteri anahtarlarından birini ekleyin.

  - [HKEY_CURRENT_USER\SOFTWARE\Microsoft \\. NETFramework \\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies] @ = "*AssemblyLocation*"

  - [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft \\. NETFramework \\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies] @ = "*AssemblyLocation*"

    64 bitlik bir işletim sistemi için, 32 bit kayıt defteri kovanında aşağıdaki kayıt defteri anahtarlarından birini ekleyin.

  - [HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft \\. NETFramework \\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies] @ = "*AssemblyLocation*"

  - [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft \\. NETFramework \\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies] @ = "*AssemblyLocation*"

    *VersionMinimum* , uygulanan en düşük .NET Framework sürümüdür. *VersionMinimum* değeri v 3.0 Ise, AssemblyFoldersEx içinde belirtilen klasörler, .NET Framework 3,0 ve üstünü hedefleyen projeler için geçerlidir.

    *AssemblyLocation* , **Başvuru Ekle** iletişim kutusunda görünmesini istediğiniz derlemelerin dizinidir, örneğin, C:\MyAssemblies \\.

    HKEY_LOCAL_MACHINE düğümü altında kayıt defteri anahtarı oluşturmak, tüm kullanıcıların **Başvuru Ekle** iletişim kutusunda belirtilen konumdaki derlemeleri görmesini sağlar. HKEY_CURRENT_USER düğümü altında kayıt defteri anahtarı oluşturulması yalnızca geçerli kullanıcının ayarını etkiler.

    **Başvuru Ekle** iletişim kutusunu tekrar açın. Derlemeler **.net** sekmesinde görünmelidir. Aksi takdirde, derlemelerin belirtilen *AssemblyLocation* dizininde bulunduğundan emin olun, Visual Studio 'yu yeniden başlatın ve yeniden deneyin.

## <a name="com-tab"></a>COM sekmesi
 COM sekmesi, başvuru için kullanılabilen tüm COM bileşenlerini listeler. Dahili bildirim içeren kayıtlı bir COM DLL öğesine başvuru eklemek isterseniz, önce DLL kaydını silin. Aksi takdirde, Visual Studio, derleme başvurusunu yerel bir DLL olarak değil, bir ActiveX Denetimi olarak ekler.

 Bir proje türü COM 'u desteklemiyorsa, sekme **başvuru Yöneticisi** iletişim kutusunda görünmez.

## <a name="solution-tab"></a>Çözüm sekmesi
 Çözüm sekmesi, geçerli çözüm içindeki tüm uyumlu projeleri Projeler alt sekmesinde listeler.

 Bir proje, farklı bir .NET Framework sürümünü hedef alan başka bir projeye başvuruda bulunabilir. Örneğin, [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] hedefleyen, ancak .NET Framework 2 için oluşturulmuş bir derlemeye başvuran bir proje oluşturabilirsiniz. Ancak, .NET Framework 2 projesi bir [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] projesine başvuramaz. Daha fazla bilgi için bkz. [belirli bir .NET Framework sürümünü hedefleme](../ide/targeting-a-specific-dotnet-framework-version.md).

 @No__t_0 hedefleyen bir proje, [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] hedefleyen bir proje ile uyumsuzdur.

 @No__t_0, bir proje .NET Framework 4 ' ü hedefliyorsa ve başka bir proje daha önceki bir sürümü hedefliyorsa, proje başvurusu yerine bir dosya başvurusu oluşturulur.

 @No__t_0 hedefleyen bir proje, .NET Framework hedefleyen bir projeye bir proje başvurusu ekleyemez ve tam tersi de geçerlidir.

## <a name="windows-tab"></a>Windows sekmesi
 Windows sekmesi, Windows işletim sisteminin çalıştığı platformlara özgü tüm SDK'ları listeler.

 Visual Studio'da bir WinMD dosyasını iki şekilde oluşturabilirsiniz:

- **uygulama tarafından yönetilen projeler [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]** : [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulama projeleri, proje özellikleri &#124; çıkış türü = winmd dosyası ayarlayarak winmd ikililerini çıktısını alabilir. WinMD dosya adı, içinde varolan tüm alan adlarının üst küme alan adı olmalıdır. Örneğin, bir proje A.B ve A.B.C ad alanlarından oluşuyorsa, çıktısı verilen WinMD için olası adlar A.winmd ve A.B.winmd olur. Bir Kullanıcı projedeki ad alanları kümesinden birleştirilmemiş &#124; bir proje özellikleri derleme adı &#124; veya proje özellikleri ad alanı değeri girerse veya bir proje içinde bir üst küme ad alanı yoksa, bir derleme uyarısı oluşturulur: ' a. winmd ' bir Bu derleme için geçerli. winmd dosya adı. Bir Windows Meta Veri dosyası içindeki tüm türler, dosya adının bir alt ad alanında mevcut olmalıdır. Dosya adının alt ad alanında mevcut olmayan türler çalışma zamanında bulunamaz. Bu derlemede, en küçük ortak ad alanı 'CSWSClassLibrary1'dir. Masaüstü Visual Basic veya görsel C# proje yalnızca birinci taraf wınmds olarak bilinen [!INCLUDE[win8](../includes/win8-md.md)] SDK 'ları kullanılarak oluşturulan wınmds 'yi kullanabilir ve WinMDs oluşturmazlar.

- **uygulama yerel projelerini [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]** : yerel bir WinMD dosyası yalnızca meta verilerden oluşur. Uygulaması ayrı bir DLL dosyası içinde var olur. **Yeni proje** iletişim kutusunda Windows çalışma zamanı bileşen proje şablonunu seçerek veya boş bir projeden başlayıp ve proje özelliklerini bir WinMD dosyası oluşturacak şekilde değiştirerek, yerel ikili dosyalar üretebilir. Proje kopuk ad alanlarından oluşuyorsa, bir yapı hatası kullanıcıya ad alanlarını birleştirmesi veya MSMerge aracını çalıştırması gerektiğini söyler.

  Windows sekmesi iki alt gruptan oluşur.

### <a name="core-subgroup"></a>Çekirdek Alt Grubu
 Çekirdek alt grubu, hedeflenen Windows sürümü için SDK içindeki tüm WinMD'leri (Windows Çalışma Zaman öğeleri için) listeler.

 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulama projeleri, proje oluşturma sırasında varsayılan olarak [!INCLUDE[win8](../includes/win8-md.md)] SDK 'sında tüm Wınmds başvuruları içerir. Yönetilen projelerde, **Çözüm Gezgini** ' deki başvurular klasörü altındaki salt okunurdur bir düğüm, tüm [!INCLUDE[win8](../includes/win8-md.md)] SDK 'nın başvurusunu gösterir. Buna uygun olarak, başvuru yöneticisindeki çekirdek alt grubu [!INCLUDE[win8](../includes/win8-md.md)] SDK 'daki derlemelerin hiçbirini numaralandırmaz ve bunun yerine bir ileti görüntüler: "Windows SDK zaten Başvurulmuş. Lütfen Windows SDK'sındaki başvuruları araştırmak için Nesne Gezgini'ni kullanın.”

 Masaüstü projelerinde, varsayılan olarak çekirdek alt grubu görünmez. Proje düğümü için kısayol menüsünü açıp, **Projeyi Kaldır**' ı seçip, aşağıdaki kod parçacığını ekleyerek ve projeyi yeniden açarak Windows çalışma zamanı ekleyebilirsiniz (proje düğümünde projeyi **yeniden yükle**' yi seçin). **Başvuru Yöneticisi** iletişim kutusunu çağırdığınızda, çekirdek alt grubu görünür.

```
<PropertyGroup>
  <TargetPlatformVersion>8.0</TargetPlatformVersion>
</PropertyGroup>
```

 Bu alt grup üzerinde **Windows** onay kutusunu seçtiğinizden emin olun. Bundan sonra Windows Çalışma Zamanı öğelerini kullanabilmeniz gerekir. Bununla birlikte, Windows Çalışma Zamanı'nın IEnumerable gibi bazı standart sınıfları ve arabirimleri (Windows Çalışma Zamanı kitaplıklarının her yerinde kullanılan) tanımladığı System.Runtime öğesini de eklemek isteyeceksiniz. System. Runtime ekleme hakkında daha fazla bilgi için bkz. [yönetilen masaüstü uygulamaları ve Windows çalışma zamanı](https://msdn.microsoft.com/library/windows/apps/jj856306.aspx#consuming_standard_windows_runtime_types).

### <a name="extensions-subgroup"></a>Uzantılar Alt Grubu
 Uzantılar, hedeflenen Windows platformunu genişleten kullanıcı SDK'larını listeler. Bu sekme yalnızca [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulama projeleri için görüntülenir. Masaüstü projeleri yalnızca birinci taraf .winmd dosyalarını kullanabildiğinden, bu sekmeyi göstermezler.

 SDK, Visual Studio'nun tek bir bileşen olarak kabul ettiği dosyalar topluluğudur. Uzantılar sekmesinde, **başvuru Yöneticisi** iletişim kutusunun çağrıldığı proje Için uygulanan SDK 'lar tek girdi olarak listelenir. Bir projeye eklendiğinde, SDK içeriğinin tümü Visual Studio tarafından kullanılır; öyle ki kullanıcının IntelliSense, araç kutusu, tasarımcılar, Nesne Tarayıcısı, yapı, dağıtım, hata ayıklama ve paketleme içinde SDK içeriğinden faydalanmak için başka hiçbir işlem yapmasına gerek kalmaz. SDK 'larınızı Uzantılar sekmesinde görüntüleme hakkında daha fazla bilgi için bkz. [yazılım geliştirme seti oluşturma](../extensibility/creating-a-software-development-kit.md).

> [!NOTE]
> Proje başka bir SDK'ya bağımlı olan bir SDK'ya başvuruda bulunursa, kullanıcı ikinci SDK için el ile bir başvuru eklemediği sürece Visual Studio ikinci SDK'yı kullanmaz. Bir Kullanıcı **Uzantılar** SEKMESINDE bir SDK seçtiğinde, **başvuru Yöneticisi** iletişim kutusu kullanıcının SDK 'nın adını ve sürümünü değil ayrıntı bölmesinde SDK BAĞıMLıLıKLARıNıN adını değil, SDK bağımlılıklarını belirlemesine yardımcı olur. Kullanıcı bağımlılıkları fark etmez ve yalnızca SDK'yı eklerse, MSBuild kullanıcıdan bağımlılıkları eklemesini ister.

 Bir proje türü **uzantıları**desteklemiyorsa, sekme **başvuru Yöneticisi** iletişim kutusunda görünmez.

## <a name="browse-button"></a>Gözat düğmesi
 Dosya sistemindeki bir bileşene gitmek için, **Araştır** düğmesini kullanabilirsiniz.

 Bir proje, farklı bir .NET Framework sürümünü hedef alan başka bir bileşene başvuruda bulunabilir. Örneğin, .NET Framework 2'yi hedefleyen bir bileşene başvuruda bulunan .NET Framework 4 İstemci Profili'ni hedef alan bir uygulama oluşturabilirsiniz. Daha fazla bilgi için bkz. [belirli bir .NET Framework sürümünü hedefleme](../ide/targeting-a-specific-dotnet-framework-version.md).

 Aynı çözümdeki başka bir projenin çıktılarına dosya başvuruları eklemekten kaçınmalısınız; bu taktik derleme hatalarına neden olabilir. Bunun yerine, projeden projeye başvurular oluşturmak için **başvuru Yöneticisi** Iletişim kutusunun **çözüm** sekmesini kullanın. Bu taktik, projelerinizde oluşturduğunuz sınıf kitaplıklarının daha iyi yönetimine olanak tanıyarak takım geliştirmeyi kolaylaştırır. Daha fazla bilgi için bkz. [Hatalı başvuruların sorunlarını giderme](../ide/troubleshooting-broken-references.md).

 Bir SDK'ye göz atamaz ve projenize ekleyemezsiniz. Yalnızca bir dosyaya (örneğin, bir derleme veya .winmd) göz atabilir ve bu dosyayı projenize ekleyebilirsiniz.

 Bir WinMD 'ye dosya başvurusu yaparken, beklenen Düzen *filename*. winmd, *filename*. dll ve *filename*. pri dosyalarının tümünün birbirlerine yerleştirilme halidir. Aşağıdaki senaryolarda bir WinMD'ye başvuruda bulunursanız, proje çıkış dizinine eksik bir dosya kümesi kopyalanır ve sonuç olarak, derleme ve çalışma zamanı hataları meydana gelir.

- **Yerel bileşen**: yerel bir proje, her ayrık ad alanı kümesi ve uygulamadan oluşan bir dll Için bir WinMD oluşturur. WinMD'ler ayrı adlara sahip olur. MSBuild bu yerel bileşen dosyasına başvururken, benzemeyecek şekilde adlandırılmış WinMD'lerin tek bir bileşen oluşturduğunu algılamaz. Sonuç olarak, yalnızca aynı *filename*. dll ve *filename*. winmd adlı bir ad gönderilir ve çalışma zamanı hataları oluşur. Bu sorunu geçici bir çözümle aşmak için bir Uzantı SDK oluşturun. Daha fazla bilgi için bkz. [yazılım geliştirme seti oluşturma](../extensibility/creating-a-software-development-kit.md).

- **Denetimleri**kullanma: en azından bir XAML denetimi *dosya adı*. winmd, *filename*. dll, *filename*. pri, *XamlName*. xaml ve bir *ImageName*. jpg bilgisinden oluşur. Proje oluşturulduğunda, dosya başvurusuyla ilişkili kaynak dosyaları projenin çıkış dizinine kopyalanmaz ve yalnızca *filename*. winmd, *filename*. dll ve *filename*. pri kopyalanır. Kullanıcıya *XamlName*. xaml ve *ImageName*. jpg kaynaklarının eksik olduğunu bildirmek için bir yapı hatası kaydedilir. Başarılı olması için, kullanıcının bu kaynak dosyaları oluşturma ve hata ayıklama/çalışma zamanı için proje çıkış dizinine el ile kopyalaması gerekir. Bu sorunu geçici olarak çözmek için, [yazılım geliştirme seti oluşturma](../extensibility/creating-a-software-development-kit.md) veya proje dosyasını düzenleme bölümündeki adımları Izleyerek bir uzantı SDK 'sı oluşturun ve aşağıdaki özelliği ekleyin:

    ```
    <PropertyGroup>
    <GenerateLibraryOutput>True</GenerateLibraryOutput>
    </PropertyGroup>
    ```

    > [!NOTE]
    > Özelliği eklerseniz, yapı daha yavaş çalışabilir.

## <a name="recent"></a>En Son
 Derlemeler, COM, Windows ve Gözat'ın her biri, bir En Son sekmesini destekler ve bu sekme projelere yakın zamanda eklenmiş bileşenlerin listesini numaralandırır.

## <a name="search"></a>Ara
 **Başvuru Yöneticisi** iletişim kutusundaki arama çubuğu, odağa sahip olan sekmenin üzerinde çalışır. Örneğin, **çözüm** sekmesi odağa karşın bir Kullanıcı arama çubuğuna "sistem" yazdığında, çözüm "sistem" içeren bir proje adından oluşmadığı sürece arama hiçbir sonuç döndürmez.

## <a name="see-also"></a>Ayrıca Bkz.
 Nib nasıl yapılır: [bir projedeki başvuruları yöneten](../ide/managing-references-in-a-project.md) [Başvuru Ekle Iletişim kutusunu kullanarak başvuru ekleme veya kaldırma](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)
