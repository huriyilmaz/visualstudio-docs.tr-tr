---
title: Yazılım Geliştirme Seti oluşturma | Microsoft Docs
description: SDK'ların genel altyapısı ve platform SDK'sı ile uzantı SDK'sı oluşturma hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: b0543b280142747c9fdfdb9f6dfee87bb2f83da35b3f4ad539b685dd878ad1e8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121293566"
---
# <a name="create-a-software-development-kit"></a>Yazılım geliştirme seti oluşturma

Yazılım geliştirme seti (SDK), bir api koleksiyonudur ve bu koleksiyonda tek öğe olarak başvurabilirsiniz Visual Studio. Başvuru **Yöneticisi** iletişim kutusunda, projeyle ilgili tüm SDK'ler liste olur. Bir projeye SDK eklerken API'ler Visual Studio.

İki tür SDK vardır:

- Platform SDK'ları, bir platform için uygulama geliştirmeye yönelik zorunlu bileşenlerdir. Örneğin, uygulama [!INCLUDE[win81](../debugger/includes/win81_md.md)] geliştirmek için SDK [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] gereklidir.

- Uzantı SDK'leri, platformu genişleten isteğe bağlı bileşenlerdir ancak bu platform için uygulama geliştirmek için zorunlu değildir.

Aşağıdaki bölümlerde SDK'ların genel altyapısı ve bir platform SDK'sı ile uzantı SDK'sı oluşturma açıklanmaktadır.

## <a name="platform-sdks"></a>Platform SDK'ları

Platform için uygulama geliştirmek için platform SDK'leri gereklidir. Örneğin, [!INCLUDE[win81](../debugger/includes/win81_md.md)] için uygulama geliştirmek için SDK [!INCLUDE[win81](../debugger/includes/win81_md.md)] gereklidir.

### <a name="installation"></a>Yükleme

Tüm platform SDK'ları *HKLM\Software\Microsoft\Microsoft SDK'ları \\ [TPI]\v[TPV] \\ @InstallationFolder = [SDK root] dizinine yüklenir.* Buna uygun [!INCLUDE[win81](../debugger/includes/win81_md.md)] olarak, SDK *HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1 dizinine yüklenir.*

### <a name="layout"></a>Layout

Platform SDK'leri aşağıdaki düzendedir:

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

| Düğüm | Açıklama |
|------------------------| - |
| *Başvurular* klasörü | Kodlandırılarak API'ler içeren ikili dosyaları içerir. Bunlar meta Windows (WinMD) dosyalarını veya derlemelerini içerebilir. |
| *DesignTime* klasörü | Yalnızca çalıştırma öncesi/hata ayıklama zamanında gereken dosyaları içerir. Bunlar XML belgeleri, kitaplıklar, üst bilgiler, Araç Kutusu tasarım zamanı ikili dosyaları, MSBuild yapıtları vb. içerebilir<br /><br /> XML belgeleri ideal olarak *\DesignTime* klasörüne yerleştirilir, ancak başvurular için XML belgeleri, belgelerde başvuru dosyasıyla birlikte yerleştiril Visual Studio. Örneğin,<em>bir başvuru \References \\ [config] \\ [arch] \sample.dll</em> için XML belgesi *\References \\ [config] \\ [arch] \sample.xml* ve bu belgedeki yerelleştirilmiş sürüm *\References \\ [config] \\ \\ [arch] [locale]\sample.xml* olur. |
| *Yapılandırma* klasörü | Yalnızca üç klasör *olabilir:* Hata Ayıklama, *Perakende ve* *CommonConfiguration*. SDK tüketicisi tarafından hedeflene yapılandırmadan bağımsız olarak aynı SDK dosyası kümesi tüketilmesi gerekirse, SDK yazarları dosyalarını *CommonConfiguration* altına yer yer almaktadır. |
| *Mimari* klasörü | Desteklenen herhangi *bir mimari* klasörü olabilir. Visual Studio şu mimarileri destekler: x86, x64, ARM ve nötr. Not: Win32 x86 ile eşler ve AnyCPU nötr olarak eşler.<br /><br /> MSBuild Platform SDK'leri *için yalnızca \CommonConfiguration\n* altta görünüyor. |
| *SDKManifest.xml* | Bu dosyada, Visual Studio SDK'yı nasıl tüketmesi gerektiği açıklanmıştır. için SDK Bildirimi'ne [!INCLUDE[win81](../debugger/includes/win81_md.md)] bakın:<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **DisplayName:** Object Browser'ın Gözat listesinde görüntülene değer.<br /><br /> **PlatformIdentity:** Bu özniteliğin varlığı Visual Studio MSBuild SDK'nın bir platform SDK'sı olduğunu ve bu öznitelikten eklenen başvuruların yerel olarak kopyalanmaması gerektiğini söyler.<br /><br /> **TargetFramework:** Bu öznitelik, Visual Studio yalnızca bu özniteliğin değerinde belirtilen aynı Çerçeveleri hedef alan projelerin SDK'yı tüketemesi için kullanılır.<br /><br /> **MinVSVersion:** Bu öznitelik, Visual Studio yalnızca buna geçerli OLAN SDK'ları tüketmek için kullanılır.<br /><br /> **Başvuru:** Bu öznitelik yalnızca denetim içeren başvurular için belirtilmelidir. Başvuruda denetim olup olmadığını belirtme hakkında bilgi için aşağıya bakın. |

## <a name="extension-sdks"></a>Uzantı SDK'ları

Aşağıdaki bölümlerde, bir uzantı SDK'sı dağıtmak için ne ihtiyacınız olduğu açıklanmaktadır.

### <a name="installation"></a>Yükleme

Uzantı SDK'leri, kayıt defteri anahtarı belirtmeden belirli bir kullanıcı veya tüm kullanıcılar için yükleyebilir. Tüm kullanıcılara bir SDK yüklemek için aşağıdaki yolu kullanın:

*%Program Files%\Microsoft SDKs \<target platform\> \v<platform sürüm numarası \> \ExtensionSDKs*

Kullanıcıya özgü yükleme için aşağıdaki yolu kullanın:

*%USERPROFILE%\AppData\Local\Microsoft SDKs \<target platform\> \v<platform sürüm numarası \> \ExtensionSDKs*

Farklı bir konum kullanmak istediğiniz iki şey vardır:

1. Bunu bir kayıt defteri anahtarında belirtin:

     **HKLM\Software\Microsoft\Microsoft SDKs \<target platform> \v<platform sürüm numarası \> \ExtensionSDKs\<SDKName>\<SDKVersion>**\

     ve değerine sahip bir (Varsayılan) alt anahtar `<path to SDK><SDKName><SDKVersion>` ekleyin.

2. MSBuild proje `SDKReferenceDirectoryRoot` dosyanıza ekleyin. Bu özelliğin değeri, başvuru yapmak istediğiniz Uzantı SDK'lerinin bulunduğu noktalı virgülle ayrılmış dizin listesidir.

### <a name="installation-layout"></a>Yükleme düzeni

Uzantı SDK'leri aşağıdaki yükleme düzenine sahiptir:

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

1. \\<SDKName<SDKVersion: Uzantı SDK'sı adı ve sürümü, SDK kökü yolundaki ilgili klasör \> \\ \> adlarından türetildi. MSBuild SDK'yı diskte bulmak için bu kimliği kullanır ve Visual Studio Özellikler  penceresinde ve Başvuru Yöneticisi iletişim **kutusunda** görüntülenir.

2. *References* klasörü: API'leri içeren ikili dosyalar. Bunlar meta Windows (WinMD) dosyaları veya derlemeleri olabilir.

3. *Redist* klasörü: Çalışma zamanı/hata ayıklama için gereken ve kullanıcının uygulamasının bir parçası olarak paketlenebilecek dosyalar. Tüm ikili dosyalar *\redist \\<config \> \\<arkın \>* altına yerleştirilmeli ve ikili adların benzersiz olmasını sağlamak için aşağıdaki biçime sahip olmalıdır: *]* \<company> . \<product> \<purpose> . \<extension> <em>. Örneğin, *Microsoft.Cpp.Build.dll.</em> Diğer SDK'lardan dosya adlarına sahip olan tüm dosyalar (örneğin, javascript, css, pri, xaml, png ve jpg dosyaları), XAML denetimleriyle ilişkili dosyalar dışında <em>\redist<config<arch<sdkname altına \\ yerleştirilsin. \> \\ \> \\ \> \* Bu dosyalar * \redist ve config<altına<\\ \> \\ bileşen<\> \\ yerleştirilsin. \> \\ </em>

4. *DesignTime* klasörü: Yalnızca ön çalıştırma/hata ayıklama zamanında gereken ve kullanıcının uygulamasının bir parçası olarak pakete dahil olmaması gereken dosyalar. Bunlar XML belgeleri, kitaplıklar, üst bilgiler, araç kutusu tasarım zamanı ikili dosyaları, MSBuild yapıtları vb. olabilir. Yerel bir proje tarafından kullanılmak üzere tasarlanmış tüm SDK'ların bir *SDKName.props dosyası* olması gerekir. Aşağıda, bu tür bir dosyanın bir örneği ve ardından bir örnek ve ardından yer alan bir örnek ve sonra da bu dosyanın bir örneği ve ardından bu dosyanın bir örneği ve

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

    XML başvuru belgeleri başvuru dosyasıyla birlikte yerleştirilir. Örneğin, *\References<config<arch \\ \> \\ \>\sample.dll* derlemesi için XML başvuru belgesi *\References \\<config<arch \> \\ \>\sample.xml* ve bu belgenin yerelleştirilmiş sürümü *\References \\<config<arch<yerel \> \\ \> \\ \>\sample.xml'dır.*

5. *Yapılandırma* klasörü: üç alt klasör: *Hata ayıklama,* *Perakende* ve *CommonConfiguration*. SDK yazarları, SDK tüketicisi tarafından hedeflenen yapılandırmadan bağımsız olarak aynı SDK dosyası kümesi tüketilmesi gerektiği zaman *dosyalarını CommonConfiguration* altına yerlerinden yer almaktadır.

6. *Mimari* klasörü: Aşağıdaki mimariler de desteklemektedir: x86, x64, ARM, nötr. Win32 x86 ile eşler ve AnyCPU nötr olarak eşler.

### <a name="sdkmanifestxml"></a>SDKManifest.xml

SDKManifest.xml dosyası, sdk'Visual Studio nasıl tüketilmesi gerektiğini açıklar. Aşağıda bir örnek verilmiştir:

```
<FileList>
DisplayName = "My SDK"
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

1. DisplayName: Başvuru Yöneticisi'nde, Çözüm Gezgini, Object Browser'da ve kullanıcı arabiriminde diğer konumlarda görünen Visual Studio.

2. ProductFamilyName: Genel SDK ürün adı. Örneğin SDK, aynı SDK ürün ailesi olan [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] "Microsoft.WinJS.1.0" ve "Microsoft.WinJS.2.0" olarak adlandırılır. Bu öznitelik, Visual Studio bağlantı MSBuild izin verir. Bu öznitelik yoksa, ürün ailesi adı olarak SDK Adı kullanılır.

3. FrameworkIdentity: Bir veya daha fazla bileşen kitaplığına Windows belirtir. Bu özniteliğin değeri, tüketen uygulamanın bildirimine yer alır. Bu öznitelik yalnızca bileşen kitaplıkları Windows geçerlidir.

4. TargetFramework: Başvuru Yöneticisi'nde ve araç kutusunda bulunan SDK'leri belirtir. Bu, ".NET Framework, version=v2.0; .NET Framework, version=v4.5.1". Aynı hedef çerçevenin birkaç sürümü belirtilirse, Başvuru Yöneticisi filtreleme amacıyla belirtilen en düşük sürümü kullanır. Örneğin, ".NET Framework, version=v2.0; .NET Framework, version=v4.5.1" belirtilirse, Başvuru Yöneticisi ".NET Framework, version=v2.0" kullanır. Belirli bir hedef çerçeve profili belirtilirse, filtreleme amacıyla yalnızca bu profil Başvuru Yöneticisi tarafından kullanılır. Örneğin, "Silverlight, version=v4.0, profile=WindowsPhone" belirtilirse, Başvuru Yöneticisi yalnızca Windows Phone filtreler; Tam Silverlight 4.0 Framework'ü hedef alan bir proje, Başvuru Yöneticisi'nde SDK'yı görmüyor.

5. MinVSVersion: En düşük Visual Studio sürümü.

6. MaxPlatformVerson: Uzantı SDK'nızı kullanmayacak platform sürümlerini belirtmek için en yüksek hedef platform sürümü kullanılmalıdır. Örneğin, Microsoft Visual C++ Çalışma Zamanı Paketi v11.0'a yalnızca Windows 8 gerekir. Bu nedenle Windows 8 MaxPlatformVersion 8.0'dır. Bu, Başvuru Yöneticisi'nin bir Windows 8.1 proje için Microsoft Visual C++ Çalışma Zamanı Paketi'ni filtrele MSBuild proje ona başvurarak [!INCLUDE[win81](../debugger/includes/win81_md.md)] hataya neden olduğu anlamına gelir. Not: Bu öğe, 'den başlayarak de destekleni. [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]

7. AppliesTo: Başvuru Yöneticisi'nde kullanılabilir OLAN SDK'ları, proje türleri için geçerli Visual Studio belirtir. Dokuz değer tanınır: WindowsAppContainer, VisualC, VB, CSharp, WindowsXAML, JavaScript, Managed ve Native. SDK yazarı (" +') veya ("&#124;" kullanabilir), ("!") tam olarak SDK için geçerli proje türlerinin kapsamını belirtmek için işleçler.

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

SDKManifest.xmlşemasının **ToolBoxItems** öğesi, hem platform hem de uzantı SDK'larında araç kutusu öğelerinin kategorisini ve konumunu belirtir.  Aşağıdaki örneklerde, farklı konumların nasıl belirtn olduğu gösterir. Bu, WinMD veya DLL başvuruları için geçerlidir.

1. Denetimleri araç kutusu varsayılan kategorisine yer.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Default"/>
    </File>
    ```

2. Denetimleri belirli bir kategori adının altına girin.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory= "MyCategoryName"/>
    </File>
    ```

3. Denetimleri belirli kategori adlarının altına yer.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems VSCategory = "Data">
        <ToolboxItems />
    </File>
    ```

4. Blend'de denetimleri farklı kategori adlarının altına Visual Studio.

    ```xml
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">
        <ToolboxItems />
    </File>
    ```

5. Blend'de belirli denetimleri farklı şekilde numara Visual Studio.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems BlendCategory = "Controls/sample/Graph">
        <ToolboxItems/>
    </File>
    ```

6. Belirli denetimleri numaradan seçin ve ortak yol Visual Studio veya yalnızca Tüm Denetimler Grubu'nda yer alan alt grubuna yer seçin.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Common">
        <ToolboxItems />
        <ToolboxItems VSCategory = "Toolbox.All">
        <ToolboxItems />
    </File>
    ```

7. Belirli denetimleri numaraya ayarlayın ve araç kutusunda olmadan ChooseItems içinde yalnızca belirli bir kümeyi gösterir.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">
        <ToolboxItems />
    </File>
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [Adım adım kılavuz: C++ kullanarak SDK oluşturma](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [Adım adım kılavuz: C# veya Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Bir projedeki başvuruları yönetme](../ide/managing-references-in-a-project.md)
