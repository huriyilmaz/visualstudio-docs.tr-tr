---
title: Yazılım geliştirme kiti oluşturma | Microsoft Docs
description: SDK 'ların genel altyapısı ve bir platform SDK 'sı ve uzantı SDK 'Sı oluşturma hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 08/31/2021
ms.topic: how-to
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 88a888bfcaa868fba0b259fbb7037d30f756784e
ms.sourcegitcommit: 8d529614652d902f265de4a6d9419bc0dfab97ee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2021
ms.locfileid: "123501606"
---
# <a name="create-a-software-development-kit"></a>Yazılım geliştirme seti oluşturma

Yazılım Geliştirme Seti (SDK), Visual Studio tek bir öğe olarak başvurkakabilmeniz için bir API koleksiyonudur. **Başvuru Yöneticisi** iletişim kutusu, projeyle ilgili olan tüm SDK 'ları listeler. Bir projeye SDK eklediğinizde, API 'Ler Visual Studio kullanılabilir.

İki tür SDK vardır:

- Platform SDK 'Ları, bir platform için uygulama geliştirmeye yönelik zorunlu bileşenlerdir. Örneğin, [!INCLUDE[win81](../debugger/includes/win81_md.md)] uygulama geliştirmek için SDK gereklidir [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] .

- Uzantı SDK 'Ları, platformu genişleten ancak bu platform için uygulama geliştirmeye yönelik zorunlu olmayan isteğe bağlı bileşenlerdir.

Aşağıdaki bölümlerde SDK 'ların genel altyapısı ve bir platform SDK 'sı ile Uzantı SDK 'Sı oluşturma açıklanır.

## <a name="platform-sdks"></a>Platform SDK 'Ları

Platform SDK 'Ları bir platforma yönelik uygulamalar geliştirmek için gereklidir. Örneğin, [!INCLUDE[win81](../debugger/includes/win81_md.md)] için uygulama geliştirmek için SDK gerekir [!INCLUDE[win81](../debugger/includes/win81_md.md)] .

### <a name="installation"></a>Yükleme

Tüm Platform SDK 'Ları, *Hklm\software\microsoft\microsoft SDK 'ları \\ [TPI] \v [TPV] \\ @InstallationFolder = [SDK root]* konumunda yüklenecektir. buna uygun olarak [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK, *hklm\software\microsoft\microsoft sdk 'leri \ Windows \v8.1*' de yüklüdür.

### <a name="layout"></a>Layout

Platform SDK 'Ları aşağıdaki düzene sahiptir:

```
\[InstallationFolder root]
            SDKManifest.xml
            \References
                  \[config]
                        \[arch]
            \DesignTime
                  \[config]
                        \[arch]
```

| Düğüm | Description |
|------------------------| - |
| *Başvurular* klasörü | İle kodlanması yapabilen API 'Leri içeren ikili dosyaları içerir. bunlar Windows meta veri (WinMD) dosyaları veya derlemeleri içerebilir. |
| *Tasarım zamanı* klasörü | Yalnızca çalıştırma öncesi/hata ayıklama zamanında gereken dosyaları içerir. bunlar XML docs, kitaplıklar, üst bilgiler, araç kutusu tasarım zamanı ikilileri, MSBuild yapıtlar ve benzeri olabilir.<br /><br /> XML belgeleri, ideal olarak *\Designtime* klasörüne yerleştirilecektir, ancak başvurular için xml belgeleri Visual Studio içindeki referans dosyası ile birlikte yerleştirilmeye devam edecektir. Örneğin, bir başvurunun XML belgesi <em>\ başvurular [ \\ config] \\ [Arch] \sample.dll</em> *\references [config] [Arch] \\ \\ \sample.xml* ve bu belgeye ait yerelleştirilmiş sürüm *\ başvurular \\ [config] \\ [Arch] \\ [locale] \sample.xml* olur. |
| *Yapılandırma* klasörü | Yalnızca üç klasör olabilir: *hata ayıklama*, *Perakende* ve *CommonConfiguration*. SDK yazarları, SDK tüketicisinin hedefleyecek yapılandırmadan bağımsız olarak, aynı SDK dosyaları kümesi tüketilmesi gerekiyorsa, dosyalarını *CommonConfiguration* altına yerleştirebilir. |
| *Mimari* klasörü | Desteklenen herhangi bir *mimari* klasörü bulunabilir. Visual Studio şu mimarileri destekler: x86, x64, ARM ve neutral. Note: Win32 ile x86 eşlenir ve eşlemeler ' ı nötr olarak eşleştirir.<br /><br /> MSBuild, Platform sdk 'ları için yalnızca *\CommonConfiguration\neutral* altında görünür. |
| *SDKManifest.xml* | bu dosya Visual Studio SDK 'nın nasıl kullanılacağını açıklar. İçin SDK bildirimine bakın [!INCLUDE[win81](../debugger/includes/win81_md.md)] :<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **DisplayName:** Nesne Tarayıcısı, gezinme listesinde görüntülenen değer.<br /><br /> **Platformıdentity:** bu özniteliğin varlığı, Visual Studio MSBuild ve SDK 'nın bir platform SDK olduğunu ve bundan eklenen başvuruların yerel olarak kopyalanmadığını belirtir.<br /><br /> **TargetFramework:** bu öznitelik, yalnızca bu özniteliğin değerinde belirtilen çerçeveleri hedefleyen projelerin SDK kullanmasını sağlamak için Visual Studio tarafından kullanılır.<br /><br /> **MinVSVersion:** bu öznitelik, yalnızca buna uygulanan sdk 'ları kullanmak için Visual Studio tarafından kullanılır.<br /><br /> **Başvuru:** Bu özniteliğin yalnızca denetimleri içeren başvurular için belirtilmesi gerekir. Bir başvurunun denetimler içerip içermediğini belirtme hakkında bilgi için aşağıya bakın. |

## <a name="extension-sdks"></a>Uzantı SDK 'Ları

Aşağıdaki bölümlerde Uzantı SDK 'Sı dağıtmak için yapmanız gerekenler açıklanır.

### <a name="installation"></a>Yükleme

Uzantı SDK 'Ları, belirli bir kullanıcı veya bir kayıt defteri anahtarı belirtmeden tüm kullanıcılar için yüklenebilir. Tüm kullanıcılar için bir SDK yüklemek için aşağıdaki yolu kullanın:

*% Program Files%\Microsoft SDK 'Ları \<target platform\> \v<Platform sürüm numarası \> \ extensionsdk 'ları*

Kullanıcıya özgü yükleme için aşağıdaki yolu kullanın:

*%USERPROFILE%\AppData\Local\Microsoft SDK 'Ları \<target platform\> \v<Platform sürüm numarası \> \ extensionsdk 'ları*

Farklı bir konum kullanmak istiyorsanız, iki işlemlerden birini yapmanız gerekir:

1. Bunu bir kayıt defteri anahtarında belirtin:

     **HKLM\Software\Microsoft\Microsoft SDK 'Ları \<target platform> \v<Platform sürüm numarası \> \ extensionsdk 'ları\<SDKName>\<SDKVersion>**\

     ve değerine sahip olan bir (default) alt anahtarı ekleyin `<path to SDK><SDKName><SDKVersion>` .

2. MSBuild özelliğini `SDKReferenceDirectoryRoot` proje dosyanıza ekleyin. Bu özelliğin değeri, başvurmak istediğiniz uzantı SDK 'larının bulunduğu, noktalı virgülle ayrılmış dizinlerin bir listesidir.

### <a name="installation-layout"></a>Yükleme düzeni

Uzantı SDK 'Ları aşağıdaki yükleme düzenine sahiptir:

```
\<ExtensionSDKs root>
           \<SDKName>
                 \<SDKVersion>
                        SDKManifest.xml
                        \References
                              \<config>
                                    \<arch>
                        \Redist
                              \<config>
                                    \<arch>
                        \DesignTime
                               \<config>
                                     \<arch>

```

1. \\<SDKName \> \\<sdkversion \> : Uzantı SDK 'sının adı ve sürümü, SDK kökünün yolundaki karşılık gelen klasör adlarından türetilir. MSBuild, SDK 'yi diskte bulmak için bu kimliği kullanır ve Visual Studio **özellikler** penceresinde ve **başvuru yöneticisi** iletişim kutusunda bu kimliği görüntüler.

2. *Başvurular* klasörü: API 'leri içeren ikili dosyalar. bunlar Windows meta veri (WinMD) dosyaları veya derlemeleri olabilir.

3. *Redist* klasörü: çalışma zamanı/hata ayıklama için gereken dosyalar ve kullanıcının uygulamasının bir parçası olarak paketlenmesi gerekir. Tüm ikili dosyalar *\redist \\<config \> \\ \><Arch* altına yerleştirilmelidir ve ikili adların benzersizlik sağlamak için aşağıdaki biçimi olmalıdır: *]* \<company> . \<product> . \<purpose> . \<extension> <em>. Örneğin, * Microsoft.Cpp.Build.dll</em>. Diğer SDK 'lardan dosya adlarıyla çakışelebilecek adlara sahip tüm dosyalar (örneğin, JavaScript, CSS, PRI, XAML, PNG ve jpg dosyaları), <em> \\ \> \\ \> \\ \> \* xaml denetimleriyle ilişkili dosyalar dışında \redist<config<Arch<SDKName altına yerleştirilmelidir. Bu dosyalar * \redist \\<config \> \\<Arch \> \\<ComponentName \> \\ altına yerleştirilmelidir</em>.

4. *Tasarım zamanı* klasörü: yalnızca ön çalıştırma/hata ayıklama sırasında gerekli olan ve kullanıcının uygulamasının bir parçası olarak paketlenmemelidir. bunlar XML belgeleri, kitaplıklar, üst bilgiler, araç kutusu tasarım zamanı ikilileri, MSBuild yapıtlar vb. olabilir. Yerel bir proje tarafından tüketimine yönelik herhangi bir SDK 'nın bir *SDKName. props* dosyası olması gerekir. Aşağıda bu dosya türünün bir örneği gösterilmektedir.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <PropertyGroup>
       <ExecutablePath>C:\Temp\ExecutablePath;$(ExecutablePath)</ExecutablePath>
       <IncludePath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\CommonConfiguration\Neutral\include;$(IncludePath)</IncludePath>
       <AssemblyReferencePath>C:\Temp\AssemblyReferencePath;(AssemblyReferencePath)</AssemblyReferencePath>
       <LibraryPath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\Debug\ARM;$(LibraryPath)</LibraryPath>
       <SourcePath>C:\Temp\SourcePath\X64;$(SourcePath)</SourcePath>
       <ExcludePath>C:\Temp\ExcludePath\X64;$(ExcludePath)</ExcludePath>
       <_PropertySheetDisplayName>DevILSDK, 1.0</_PropertySheetDisplayName>
     </PropertyGroup>
   </Project>

   ```

    XML başvuru belgeleri, başvuru dosyasının yanına yerleştirilir. Örneğin, *\references \\<config \> \\<Arch \>\sample.dll* bütünleştirilmiş kodu için XML başvuru belgesi, *\references \\<config \> \\<Arch \>\sample.xml* ve bu belgenin yerelleştirilmiş sürümü *\references<\\ config<\> \\ Arch \> \\<locale \>\sample.xml*.

5. *Yapılandırma* klasörü: üç alt klasör: *Hata Ayıkla*, *Perakende* ve *CommonConfiguration*. SDK yazarları, SDK tüketicisinin hedeflediği yapılandırmadan bağımsız olarak aynı SDK dosyaları kümesi tüketilmesi gerektiğinde dosyalarını *CommonConfiguration* altına yerleştirebilir.

6. *Mimari* klasörü: Şu mimariler desteklenir: x86, x64, ARM, nötr. Win32, x86 ile eşlenir ve eşlemeleri bağımsız olarak eşler.

### <a name="sdkmanifestxml"></a>SDKManifest.xml

*SDKManifest.xml* dosyası, Visual Studio SDK 'nın nasıl kullanılacağını açıklar. Aşağıda bir örnek verilmiştir:

```
<FileList DisplayName = "My SDK"
          ProductFamilyName = "My SDKs"
          TargetFramework = ".NETCore, version=v4.5.1; .NETFramework, version=v4.5.1"
          MinVSVersion = "14.0"
          MaxPlatformVersion = "8.1"
          AppliesTo = "WindowsAppContainer + WindowsXAML"
          SupportPrefer32Bit = "True"
          SupportedArchitectures = "x86;x64;ARM"
          SupportsMultipleVersions = "Error"
          CopyRedistToSubDirectory = "."
          DependsOn = "SDKB, version=2.0"
          MoreInfo = "https://msdn.microsoft.com/MySDK">
  <File Reference = "MySDK.Sprint.winmd" Implementation = "XNASprintImpl.dll">
    <Registration Type = "Flipper" Implementation = "XNASprintFlipperImpl.dll" />
    <Registration Type = "Flexer" Implementation = "XNASprintFlexerImpl.dll" />
    <ToolboxItems VSCategory = "Toolbox.Default" />
  </File>
</FileList>
```

Aşağıdaki liste, dosyanın öğelerini verir:

1. DisplayName: başvuru Yöneticisi, Çözüm Gezgini, Nesne Tarayıcısı ve Visual Studio Kullanıcı arabirimindeki diğer konumlarda görünen değer.

2. ProductFamilyName: Genel SDK ürün adı. Örneğin, [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] SDK "Microsoft. WinJS. 1.0" ve "Microsoft. WinJS. 2.0" olarak adlandırılmıştır. Bu, "Microsoft. WinJS" ADLı SDK ürünleri ailesine ait. bu öznitelik, Visual Studio ve MSBuild bu bağlantıyı yapmasına izin verir. Bu öznitelik yoksa, SDK adı ürün ailesi adı olarak kullanılır.

3. frameworkıdentity: bir veya daha fazla Windows bileşen kitaplığı üzerinde bir bağımlılık belirtir. Bu özniteliğin değeri, tüketen uygulamanın bildirimine konur. bu öznitelik yalnızca Windows bileşen kitaplıkları için geçerlidir.

4. TargetFramework: başvuru Yöneticisi 'nde ve araç kutusunda bulunan SDK 'Ları belirtir. bu, ".NET Framework, sürüm = v 2.0; gibi bir hedef çerçeve adları noktalı virgülle ayrılmış listesidir. .NET Framework, version = v 4.5.1 ". Aynı hedef Framework 'ün birkaç sürümü belirtilmişse, başvuru Yöneticisi filtreleme amacıyla belirtilen en düşük sürümü kullanır. örneğin, ".NET Framework, sürüm = v 2.0; .NET Framework, version = v 4.5.1 "belirtildiğinde, başvuru yöneticisi" .NET Framework, sürüm = v 2.0 "kullanacaktır. Belirli bir hedef çerçeve profili belirtilmişse, yalnızca bu profil başvuru Yöneticisi tarafından filtreleme amacıyla kullanılacaktır. örneğin, "Silverlight, version = v 4.0, profile = WindowsPhone" belirtildiğinde, başvuru yöneticisi yalnızca Windows Phone profilinde filtreler; tam Silverlight 4,0 Framework 'Ü hedefleyen bir proje, başvuru yöneticisinde SDK 'Yı görmez.

5. minvsversion: en düşük Visual Studio sürümü.

6. MaxPlatformVerson: Uzantı SDK 'sının çalışmayacak platform sürümlerini belirtmek için en fazla hedef platform sürümü kullanılmalıdır. örneğin, Microsoft Visual C++ çalışma zamanı paketi v 11.0 yalnızca Windows 8 projeleri tarafından başvurulmalıdır. Bu nedenle Windows 8 MaxPlatformVersion 8.0'dır. Bu, Başvuru Yöneticisi'nin bir Microsoft Visual C++ proje için Windows 8.1 Çalışma Zamanı Paketi'ni filtrele MSBuild bir proje ona başvurarak [!INCLUDE[win81](../debugger/includes/win81_md.md)] hataya neden olduğu anlamına gelir. Not: Bu öğe, 'den başlayarak de destekleni. [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]

7. AppliesTo: Başvuru Yöneticisi'nde kullanılabilir OLAN SDK'ları, proje türleri için geçerli Visual Studio belirtir. Dokuz değer tanınır: WindowsAppContainer, VisualC, VB, CSharp, WindowsXAML, JavaScript, Managed ve Native. SDK yazarı ve ("+') veya ("&#124;") kullanabilir, ("!") kullanmaz tam olarak SDK için geçerli proje türlerinin kapsamını belirtmek için işleçler.

    WindowsAppContainer, uygulamalar için projeleri [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] tanımlar.

8. SupportPrefer32Bit: Desteklenen değerler "True" ve "False" değerleridir. Varsayılan değer "True" şeklindedir. Değer "False" olarak ayarlanırsa, SDK'ya başvurulan projede Prefer32Bit etkinse MSBuild projeleri için bir hata (veya masaüstü projeleri için [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] uyarı) döndürür. Prefer32Bit hakkında daha fazla bilgi için [bkz. Derleme sayfası, Project Tasarımcısı (C#)](../ide/reference/build-page-project-designer-csharp.md) veya Derleme [sayfası, Project Tasarımcısı (Visual Basic).](../ide/reference/compile-page-project-designer-visual-basic.md)

9. SupportedArchitectures: SDK'nın desteklediği mimarilerin noktalı virgülle ayrılmış listesi. MSBuild, tüketen projede hedeflenen SDK mimarisi desteklenmiyorsa bir uyarı görüntüler. Bu öznitelik belirtilmezse, MSBuild hiçbir zaman bu tür bir uyarı görüntülemez.

10. SupportsMultipleVersions: Bu öznitelik **Hata** veya Uyarı olarak ayarlanırsa, MSBuild aynı projenin aynı SDK ailesinin birden çok sürümüne başvura olmadığını gösterir. Bu öznitelik yoksa veya İzin Ver olarak ayarlanırsa MSBuild bu tür bir hata veya uyarı görüntülemez.

11. AppX: Diskte bileşen kitaplığı için Windows paketlerinin yolunu belirtir. Bu değer, yerel hata ayıklama sırasında Windows kitaplığının kayıt bileşenine geçirilir. Dosya adı için adlandırma kuralı : *\<Company> . . . \<Product> . \<Architecture> \<Configuration> \<Version> . appx*. Yapılandırma ve Mimari, bileşen kitaplığı için geçerli yoksa öznitelik adı ve öznitelik Windows isteğe bağlıdır. Bu değer yalnızca bileşen kitaplıkları Windows geçerlidir.

12. CopyRedistToSubDirectory: *\redist* klasörünün altındaki dosyaların uygulama paketi köküne (Yani, Uygulama Paketi  Oluşturma sihirbazında  seçilen Paket konumu) ve çalışma zamanı düzeni köküne göre nereye kopyalandır gerektiğini belirtir. Varsayılan konum, uygulama paketinin ve **F5** düzeninin kökündedir.

13. DependsOn: Bu SDK'nın bağlı olduğu SDK'ları tanımlayan SDK kimliklerinin listesi. Bu öznitelik Başvuru Yöneticisi'nin ayrıntılar bölmesinde görünür.

14. MoreInfo: Yardım ve daha fazla bilgi sağlayan web sayfasının URL'si. Bu değer, Başvuru Yöneticisi'nin sağ bölmesindeki Daha Fazla Bilgi bağlantısında kullanılır.

15. Kayıt Türü: Uygulama bildiriminde WinMD kaydını belirtir ve buna bir uygulama DLL'si olan yerel WinMD için gereklidir.

16. Dosya Başvurusu: Yalnızca denetim içeren veya yerel WinMD'ler olan başvurular için belirtilir. Başvuruda denetimler olup olmadığını belirtme hakkında bilgi için aşağıdaki [Araç kutusu öğelerinin konumunu belirtme makalelerine](#ToolboxItems) bakın.

## <a name="specify-the-location-of-toolbox-items"></a><a name="ToolboxItems"></a> Araç kutusu öğelerinin konumunu belirtme

*SDKManifest.xml* şemasının **ToolBoxItems** öğesi, hem platform hem de uzantı SDK'lerinde araç kutusu öğelerinin denetim adlarını, kaynak derlemelerini ve araç kutusu sekme adlarını belirtir. Aşağıdaki örneklerde çeşitli senaryolar yer almaktadır. Bu, WinMD veya DLL başvuruları için geçerlidir.

Visual Studio 2019 ve önceki sürümlerinde, bildirimde araç kutusu denetim adlarını listelemek yerine SDK'Visual Studio derlemelerinde denetim türlerini dinamik olarak numaralandırmış olduğunu unutmayın. 2022'Visual Studio başlayarak bu artık desteklenmiyor; araç kutusu öğeleri, 'de açıkça *SDKManifest.xml.*

1. Denetimleri araç kutusu varsayılan kategorisine yer.

    ```xml
    <File Reference = "sample.winmd">
      <ToolboxItems VSCategory = "Toolbox.Default">
        <Item Type = "Namespace.ControlName1" />
        <Item Type = "Namespace.ControlName2" />
      </ToolboxItems>
    </File>
    ```

2. Denetimleri belirli bir kategori adının altına girin.

    ```xml
    <File Reference = "sample.winmd">
      <ToolboxItems VSCategory= "MyCategoryName">
        <Item Type = "Namespace.ControlName1" />
        <Item Type = "Namespace.ControlName2" />
      </ToolboxItems>
    </File>
    ```

3. Denetimleri belirli kategori adlarının altına yer.

    ```xml
    <File Reference = "sample.winmd">
      <ToolboxItems VSCategory = "Graph">
        <Item Type = "Namespace.ControlName1" />
      </ToolboxItems>
      <ToolboxItems VSCategory = "Data">
        <Item Type = "Namespace.ControlName2" />
      </ToolboxItems>
    </File>
    ```

4. Blend'de denetimleri farklı kategori adlarının altına Visual Studio.

    ```xml
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.
    <File Reference = "sample.winmd">
      <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">
        <Item Type = "Namespace.ControlName1" />
        <Item Type = "Namespace.ControlName2" />
      </ToolboxItems>
    </File>
    ```

5. Blend ve Visual Studio'da belirli denetimleri farklı şekilde Visual Studio.

    ```xml
    <File Reference = "sample.winmd">
      <ToolboxItems VSCategory = "Graph">
        <Item Type = "Namespace.ControlName1" />
      </ToolboxItems>
      <ToolboxItems BlendCategory = "Controls/sample/Graph">
        <Item Type = "Namespace.ControlName2" />
      </ToolboxItems>
    </File>
    ```

6. Belirli denetimleri numaradan seçin ve ortak yol Visual Studio veya yalnızca Tüm Denetimler Grubu'nda yer alan alt grubuna yer seçin.

    ```xml
    <File Reference = "sample.winmd">
      <ToolboxItems VSCategory = "Toolbox.Common">
        <Item Type = "Namespace.ControlName1" />
      </ToolboxItems>
      <ToolboxItems VSCategory = "Toolbox.All">
        <Item Type = "Namespace.ControlName2" />
      </ToolboxItems>
    </File>
    ```

7. Belirli denetimleri numaraya ayarlayın ve araç kutusunda yer almadan ChooseItems içinde yalnızca belirli bir kümeyi gösterir.

    ```xml
    <File Reference = "sample.winmd">
      <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">
        <Item Type = "Namespace.ControlName1" />
        <Item Type = "Namespace.ControlName2" />
      </ToolboxItems>
    </File>
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [Adım adım kılavuz: C++ kullanarak SDK oluşturma](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [Adım adım kılavuz: C# veya Visual Basic kullanarak SDK oluşturma](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Bir projedeki başvuruları yönetme](../ide/managing-references-in-a-project.md)
