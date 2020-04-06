---
title: Yazılım Geliştirme Kiti Oluşturma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f7cf6cf092edf96280c566018231cc00d34c0994
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739596"
---
# <a name="create-a-software-development-kit"></a>Yazılım geliştirme kiti oluşturma

Yazılım geliştirme kiti (SDK), Visual Studio'da tek bir öğe olarak başvuruda bulunabileceğiniz API'ler topluluğudur. **Başvuru Yöneticisi** iletişim kutusu, projeyle ilgili tüm SDK'ları listeler. Bir projeye Bir SDK eklediğinizde, API'ler Visual Studio'da kullanılabilir.

İki tür SDK vardır:

- Platform SDK'ları, bir platform için uygulama geliştirmek için zorunlu bileşenlerdir. Örneğin, [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK'nın uygulama [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] geliştirmesi gerekir.

- Uzantılı SDK'lar, bir platformu genişleten ancak bu platform için uygulama geliştirmek için zorunlu olmayan isteğe bağlı bileşenlerdir.

Aşağıdaki bölümlerde SDK'ların genel altyapısı ve bir platform SDK ve uzantı SDK nasıl oluşturulacağını açıklanmaktadır.

## <a name="platform-sdks"></a>Platform SDK'ları

Platform SDK'ları bir platform için uygulama geliştirmek için gereklidir. Örneğin, [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK için uygulamalar geliştirmek [!INCLUDE[win81](../debugger/includes/win81_md.md)]için gereklidir.

### <a name="installation"></a>Yükleme

Tüm platform SDK'ları *HKLM\Software\Microsoft\Microsoft SDKs\\[TPI]\v[TPV]\\ @InstallationFolder = [SDK kökü]* adresinde yüklenir. Buna göre, [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK *HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1*adresinde yüklenir.

### <a name="layout"></a>Düzen

Platform SDK'ları aşağıdaki düzene sahiptir:

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

| Node | Açıklama |
|------------------------| - |
| *Referanslar* klasörü | Karşı kodlanabilen API'ler içeren ikili ler içerir. Bunlar Windows Metadata (WinMD) dosyalarını veya derlemelerini içerebilir. |
| *DesignTime* klasörü | Yalnızca ön çalıştırma/hata ayıklama zamanında gereken dosyaları içerir. Bunlar XML dokümanları, kitaplıklar, üstbilgi, Araç Kutusu tasarım-zaman ikilileri, MSBuild yapıları ve benzeri<br /><br /> XML dokümanları, ideal olarak *\DesignTime* klasörüne yerleştirilir, ancak referanslar için XML dokümanları Visual Studio'daki başvuru dosyasının yanına yerleştirilmeye devam eder. Örneğin, bir başvuru için XML doc<em>\\\References\\[config] [arch]\sample.dll</em> *\\\References [config]\\[arch]\sample.xml*olacak ve bu dokümanın yerelleştirilmiş sürümü *\References\\[config]\\[arch]\\[locale]\sample.xml olacaktır.* |
| *Yapılandırma* klasörü | Yalnızca üç klasör olabilir: *Hata Ayıklama*, *Perakende* ve *Yaygın Yapılandırma*. SDK yazarları, SDK tüketicisinin hedefalacağı yapılandırmadan bağımsız olarak, aynı SDK dosyaları kümesinin tüketilmesi durumunda dosyalarını *CommonConfiguration'a* yerleyebilir. |
| *Mimari* klasörü | Desteklenen herhangi bir *mimari* klasör var olabilir. Visual Studio aşağıdaki mimarileri destekler: x86, x64, ARM ve nötr. Not: Win32 haritalar x86 ve AnyCPU haritalar nötr.<br /><br /> MSBuild yalnızca Platform SDK'ları için *\CommonConfiguration\neutral* altında görünür. |
| *SDKManifest.xml* | Bu dosya, Visual Studio'nun SDK'yı nasıl tüketmesi gerektiğini açıklar. Için SDK Manifest [!INCLUDE[win81](../debugger/includes/win81_md.md)]bak:<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **Ekran Adı:** Nesne Tarayıcısının Gözat listesinde görüntülenebilen değeri.<br /><br /> **PlatformKimliği:** Bu özniteliğin varlığı Visual Studio ve MSBuild'e SDK'nın bir platform SDK olduğunu ve eklenen referansların yerel olarak kopyalanmaması gerektiğini söyler.<br /><br /> **Hedef Çerçevesi:** Bu öznitelik Visual Studio tarafından yalnızca bu öznitelik değerinde belirtilen aynı Çerçeveleri hedefleyen projelerin SDK'yı tüketebilmesini sağlamak için kullanılır.<br /><br /> **MinVSVersion:** Bu öznitelik Visual Studio tarafından yalnızca ona uygulanan SDK'ları tüketmek için kullanılır.<br /><br /> **Başvuru:** Bu öznitelik yalnızca denetimleri içeren başvurular için belirtilmelidir. Başvurunun denetimleri bulunup içermediğini nasıl belirtinebilirsiniz hakkında bilgi için aşağıya bakın. |

## <a name="extension-sdks"></a>Uzantı SDK'ları

Aşağıdaki bölümlerde bir uzantı SDK dağıtmak için yapmanız gerekenler açıklayınız.

### <a name="installation"></a>Yükleme

Uzantı SDK'ları, bir kayıt defteri anahtarı belirtmeden belirli bir kullanıcı veya tüm kullanıcılar için yüklenebilir. Tüm kullanıcılar için bir SDK yüklemek için aşağıdaki yolu kullanın:

*%Program Dosyaları%\Microsoft SDKs\<\>hedef platform \v\><platform sürüm numarası \ExtensionSDKs*

Kullanıcıya özel bir yükleme için aşağıdaki yolu kullanın:

*%USERPROFILE%\AppData\Local\Microsoft SDKs\<hedef\>platformu \v\><platformu sürüm numarası \ExtensionSDKs*

Farklı bir konum kullanmak istiyorsanız, iki şeyden birini yapmanız gerekir:

1. Kayıt defteri anahtarında belirtin:

     **HKLM\Software\Microsoft\Microsoft\<SDKs hedef platform>\v\><platform sürüm\<numarası \ExtensionSDKs SDKName>\<SDKVersion>**\

     ve değeri .'ye `<path to SDK><SDKName><SDKVersion>`sahip bir (Varsayılan) alt anahtar ekleyin

2. MSBuild özelliğini `SDKReferenceDirectoryRoot` proje dosyanıza ekleyin. Bu özelliğin değeri, başvurmak istediğiniz Uzantı SDK'larının bulunduğu yarı sütunlu sınırlı dizinler listesidir.

### <a name="installation-layout"></a>Yükleme düzeni

Uzantı SDK'ları aşağıdaki yükleme düzenine sahiptir:

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

1. \\<SDKName\> \\<\>SDKVersion : SDK uzantısı adı ve sürümü SDK köküne giden yolda ilgili klasör adlarından türetilmiştir. MSBuild diskte SDK'yı bulmak için bu kimliği kullanır ve Visual Studio bu kimliği **Özellikler** penceresinde ve **Başvuru Yöneticisi** iletişim kutusunda görüntüler.

2. *Başvurular* klasörü: API'ler içeren ikili. Bunlar Windows Metadata (WinMD) dosyaları veya derlemeleri olabilir.

3. *Redist* klasörü: çalışma zamanı/hata ayıklama için gerekli olan ve kullanıcının uygulamasının bir parçası olarak paketlenmiş olması gereken dosyalar. Tüm ikililer *\redist\\<config\> \\<\>kemerin*altına yerleştirilmeli ve ikili adlar teklik sağlamak için aşağıdaki biçime sahip olmalıdır: *]*\<şirket>. \<ürün>. \<amaç>. \<uzantısı><em>. Örneğin, *Microsoft.Cpp.Build.dll</em>. XAML denetimleri ile <em>ilişkili dosyalar dışında\\ \redist<config\> \\<arch\> \\<sdkname'nin\> \* altına diğer SDK'lardan (javascript, css, pri, xaml, png ve jpg dosyaları) gelen dosya adlarıyla çakışabilecek adlara sahip tüm dosyalar yerleştirilmelidir. Bu dosyalar *\redist\\<\> \\ config<\> \\ arch<\>componentname altına yerleştirilmelidir.</em>

4. *DesignTime* klasörü: yalnızca ön çalıştırma/hata ayıklama süresinde gerekli olan ve kullanıcının uygulamasının bir parçası olarak paketlenmemiş dosyalar. Bunlar XML dokümanları, kitaplıklar, üstbilgi, araç kutusu tasarım zamanı ikilileri, MSBuild yapıları vb. olabilir. Yerel bir proje tarafından tüketilen herhangi bir SDK'nın bir *SDKName.props* dosyası olmalıdır. Aşağıda bu tür bir dosya örneği gösterilmektedir.

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

    XML başvuru belgeleri başvuru dosyasının yanına yerleştirilir. Örneğin, *\Başvurular\\ \> \\<config<arch\>\sample.dll* derlemesi için XML başvuru belgesi *\Başvurular\\<config\> \\<arch\>\sample.xml*ve bu dokümanın yerelleştirilmiş sürümü *\References\\<config\> \\<arch\> \\<yerele \sample.xml\>*.

5. *Yapılandırma* klasörü: üç alt klasör: *Hata Ayıklama*, *Perakende*ve *CommonConfiguration*. SDK yazarları, SDK tüketicisi tarafından hedeflenen yapılandırmadan bağımsız olarak, aynı SDK dosyaları kümesi nin tüketilmesi gerektiğinde dosyalarını *CommonConfiguration'a* yerleyebilir.

6. *Mimari* klasörü: aşağıdaki mimarileri desteklenir: x86, x64, ARM, nötr. Win32 haritalar x86 ve AnyCPU haritalar nötr.

### <a name="sdkmanifestxml"></a>SDKManifest.xml

*SDKManifest.xml* dosyası, Visual Studio'nun SDK'yı nasıl tüketmesi gerektiğini açıklar. Aşağıda bir örnek verilmiştir:

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

Aşağıdaki liste dosyanın öğelerini verir:

1. DisplayName: Visual Studio kullanıcı arabiriminde Referans Yöneticisi, Solution Explorer, Object Browser ve diğer konumlarda görünen değer.

2. ÜrünFamilyName: Genel SDK ürün adı. Örneğin, [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] SDK,SDK'nın adı "Microsoft.WinJS.1.0" ve "Microsoft.WinJS.2.0", SDK ürünleri ailesine ait "Microsoft.WinJS". Bu öznitelik Visual Studio ve MSBuild bu bağlantıyı yapmak için izin verir. Bu öznitelik yoksa, SDK Adı ürün soyadı adı olarak kullanılır.

3. FrameworkIdentity: Bir veya daha fazla Windows bileşen kitaplıklarına bağımlılık belirtir. Bu özniteliğin değeri, tüketen uygulamanın bildirimine konur. Bu öznitelik yalnızca Windows bileşen kitaplıkları için geçerlidir.

4. TargetFramework: Başvuru Yöneticisi'nde ve araç kutusunda bulunan SDK'ları belirtir. Bu hedef çerçeve monikers bir yarı kolon-delimited listesi, örneğin ".NET Framework, sürüm=v2.0; .NET Framework, version=v4.5.1". Aynı hedef çerçevenin birkaç sürümü belirtilirse, Başvuru Yöneticisi filtreleme amacıyla en düşük belirtilen sürümü kullanır. Örneğin, ".NET Framework, version=v2.0; .NET Framework, version=v4.5.1" belirtilmişse, Başvuru Yöneticisi ".NET Framework, version=v2.0" kullanır. Belirli bir hedef çerçeve profili belirtilirse, yalnızca bu profil Filtreleme amacıyla Başvuru Yöneticisi tarafından kullanılır. Örneğin, "Silverlight, version=v4.0, profile=WindowsPhone" belirtildiğinde, Başvuru Yöneticisi yalnızca Windows Phone profilinde filtrelenir; Silverlight 4.0 Framework'ün tamamını hedefleyen bir proje Referans Yöneticisi'nde SDK'yı görmez.

5. MinVSVersion: Minimum Visual Studio sürümü.

6. MaxPlatformVerson: Uzantı SDK'nızın çalışmayacağı platform sürümlerini belirtmek için maksimum hedef platform sürümü kullanılmalıdır. Örneğin, Microsoft Visual C++ Runtime Paketi v11.0 yalnızca Windows 8 projeleri tarafından başvurulmalıdır. Böylece, Windows 8 projenin MaxPlatformVersion 8.0 olduğunu. Bu, Başvuru Yöneticisi'nin Bir Windows 8.1 projesi için Microsoft Visual C++ Çalışma Süresi Paketini filtrelemesi ve MSBuild'in proje [!INCLUDE[win81](../debugger/includes/win81_md.md)] başvuruyaptığında hata yaptığı anlamına gelir. Not: Bu öğe ' [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]den başlayarak desteklenir.

7. AapplyTo: Geçerli Visual Studio proje türlerini belirterek Referans Yöneticisi'nde bulunan SDK'ları belirtir. Dokuz değer tanınır: WindowsAppContainer, VisualC, VB, CSharp, WindowsXAML, JavaScript, Yönetilen ve Yerel. SDK yazarı kullanabilir ve ("+'), ya da ("&#124;"), değil ("!")) operatörler SDK için geçerli proje türlerinin tam kapsamını tam olarak belirtmek için.

    WindowsAppContainer, uygulamalar [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] için projeleri tanımlar.

8. SupportPrefer32Bit: Desteklenen değerler "True" ve "False"dur. Varsayılan değer "True"dur. Değer "False" olarak ayarlanmışsa, SDK'ya başvuran proje Prefer32Bit etkinleştirilmişse, MSBuild projeler için [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] bir hata (veya masaüstü projeleri için bir uyarı) döndürür. Prefer32Bit hakkında daha fazla bilgi için Yapı [sayfası, Proje Tasarımcısı (C#)](../ide/reference/build-page-project-designer-csharp.md) veya [Derleme sayfasına, Project Designer 'a (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md)bakın.

9. Desteklenen Mimariler: SDK'nın desteklediği yarı sütunlu mimarilistesi. TÜKETEN projede hedeflenen SDK mimarisi desteklenmezse MSBuild bir uyarı görüntüler. Bu öznitelik belirtilmemişse, MSBuild bu tür bir uyarı yı görüntülemez.

10. MultipleVersions destekler: Bu öznitelik **Hata** veya **Uyarı**olarak ayarlanırsa, MSBuild aynı projenin aynı SDK ailesinin birden fazla sürümüne başvurulamayacağını gösterir. Bu öznitelik yoksa veya **İzin Vermek**için ayarlanmışsa, MSBuild bu tür bir hata veya uyarı görüntülemez.

11. AppX: Diskteki Windows bileşen kitaplığı için uygulama paketlerine giden yolu belirtir. Bu değer, yerel hata ayıklama sırasında Windows bileşen kitaplığı kayıt bileşenine geçirilir. Dosya adı için adlandırma kuralı * \<Şirket\<>' dir. Ürün>. \<Mimarlık>. \<Yapılandırma>. Sürüm \<>.appx*. Yapılandırma ve Mimari, Windows bileşen kitaplığı için geçerli değilse öznitelik adı ve öznitelik değeri isteğe bağlıdır. Bu değer yalnızca Windows bileşen kitaplıkları için geçerlidir.

12. CopyRedistToSubDirectory: *\redist* klasörün altındaki dosyaların uygulama paketi köküne (diğer bir **deyişle, Uygulama Paketi Oluştur** sihirbazında seçilen **Paket konumu)** ve çalışma zamanı düzen köküne göre kopyalanması gereken yeri belirtir. Varsayılan konum, uygulama paketinin ve **F5** düzeninin köküdür.

13. Bağımlı: Bu SDK'nın bağlı olduğu SDK'ları tanımlayan SDK kimliklerinin listesi. Bu öznitelik, Başvuru Yöneticisi'nin ayrıntı bölmesinde görünür.

14. MoreInfo: Yardım ve daha fazla bilgi sağlayan web sayfasının URL'si. Bu değer, Başvuru Yöneticisi'nin sağ bölmesindeki Daha Fazla Bilgi bağlantısında kullanılır.

15. Kayıt Türü: Uygulama bildiriminde WinMD kaydını belirtir ve dll uygulamasıolan yerel WinMD için gereklidir.

16. Dosya Başvurusu: Yalnızca denetim içeren veya yerel WinMD'ler olan başvurular için belirtilir. Başvurunun denetimleri bulunup içermediğini nasıl belirtinebilirsiniz hakkında [bilgi](#ToolboxItems) için bkz.

## <a name="specify-the-location-of-toolbox-items"></a><a name="ToolboxItems"></a>Araç kutusu öğelerinin konumunu belirtin

*SDKManifest.xml* şemasının **ToolBoxItems** öğesi, araç kutusu öğelerinin kategorisini ve konumunu hem platformda hem de uzantılı SDKK'larda belirtir. Aşağıdaki örnekler, farklı konumların nasıl belirtilen gösteriş olduğunu gösterir. Bu, WinMD veya DLL başvuruları için geçerlidir.

1. Denetimleri araç kutusu varsayılan kategorisinde yerleştirin.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Default"/>
    </File>
    ```

2. Denetimleri belirli bir kategori adı altında yerleştirin.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory= "MyCategoryName"/>
    </File>
    ```

3. Denetimleri belirli kategori adları altında yerleştirin.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems VSCategory = "Data">
        <ToolboxItems />
    </File>
    ```

4. Blend ve Visual Studio'da denetimleri farklı kategori adları altında yerleştirin.

    ```xml
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">
        <ToolboxItems />
    </File>
    ```

5. Blend ve Visual Studio'da belirli denetimleri farklı şekilde sayısala.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems BlendCategory = "Controls/sample/Graph">
        <ToolboxItems/>
    </File>
    ```

6. Belirli denetimleri sıralayın ve Visual Studio Ortak Yolu'nun altına veya yalnızca Tüm Denetimler Grubu'na yerleştirin.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Common">
        <ToolboxItems />
        <ToolboxItems VSCategory = "Toolbox.All">
        <ToolboxItems />
    </File>
    ```

7. Belirli denetimleri sayısalhale getirin ve araç kutusunda olmadan SelectItems'ta yalnızca belirli bir kümeyi gösterin.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">
        <ToolboxItems />
    </File>
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [Walkthrough: C++ kullanarak bir SDK oluşturma](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [Walkthrough: C# veya Visual Basic kullanarak Bir SDK oluşturma](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Bir projedeki başvuruları yönetme](../ide/managing-references-in-a-project.md)
