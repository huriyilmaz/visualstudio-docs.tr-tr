---
title: Ortak MSBuild proje özellikleri | Microsoft Docs
ms.date: 01/18/2018
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- msbuild, common properties
- msbuild, project file properties
- ExcludeDeploymentUrl property
- project file properties (MSBuild)
ms.assetid: 9857505d-ae15-42f1-936d-6cd7fb9dd276
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 08c790af5504c902bf5fe37d2cddba9b9f63aa40
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "87425374"
---
# <a name="common-msbuild-project-properties"></a>Yaygın MSBuild proje özellikleri

Aşağıdaki tabloda, Visual Studio proje dosyalarında tanımlanan veya MSBuild 'in sağladığı *. targets* dosyalarına eklenen sık kullanılan özellikler listelenmiştir.

 Visual Studio 'daki proje dosyaları (*. csproj*, *. vbproj*, *. vcxproj*ve diğerleri), IDE kullanarak bir proje oluşturduğunuzda çalıştırılan MSBuild xml kodunu içerir. Projeler genellikle derleme işlemlerini tanımlamak için bir veya daha fazla *. targets* dosyasını içeri aktarır. Daha fazla bilgi için bkz. [MSBuild. targets dosyaları](../msbuild/msbuild-dot-targets-files.md).

## <a name="list-of-common-properties-and-parameters"></a>Ortak özellikler ve parametrelerin listesi

| Özellik veya parametre adı | Proje türleri | Description |
|------------------------------------| - | - |
| Adtiontalbpaths | .NET | Derleyicilerin başvuru derlemelerini arayacağı ek klasörleri belirtir. |
| AddModules | .NET | Derleyicinin, belirtilen dosyalardaki tüm tür bilgilerini derlediğiniz proje için kullanılabilir hale getirmesine neden olur. Bu özellik, `/addModules` derleyici anahtarıyla eşdeğerdir. |
| ALToolPath | .NET | *AL.exe* bulunabileceği yol. Bu özellik, farklı bir sürümün kullanımını etkinleştirmek için geçerli *AL.exe* sürümünü geçersiz kılar. |
| ApplicationIcon | .NET | Bir Win32 simgesi olarak katıştırmak üzere derleyiciye geçirilecek *. ico* simge dosyası. Özelliği, `/win32icon` derleyici anahtarıyla eşdeğerdir. |
| ApplicationManifest | Tümü | Dış Kullanıcı hesabı denetimi (UAC) bildirim bilgilerini oluşturmak için kullanılan dosyanın yolunu belirtir. Yalnızca Windows Vista 'Yı hedefleyen Visual Studio projeleri için geçerlidir.<br /><br /> Çoğu durumda, bildirim katıştırılır. Ancak kayıt ücretsiz COM veya ClickOnce dağıtımını kullanıyorsanız, bildirim, uygulama Derlemeleriyle birlikte yüklenen bir dış dosya olabilir. Daha fazla bilgi için bu konudaki NoWin32Manifest özelliğine bakın. |
| AssemblyOriginatorKeyFile | .NET | Derlemeyi (*. snk* veya *. pfx*) imzalamak için kullanılan dosyayı belirtir ve derlemeyi imzalamak için kullanılan gerçek anahtarı oluşturmak için [ResolveKeySource görevine](../msbuild/resolvekeysource-task.md) geçirilir. |
| AssemblySearchPaths | .NET | Derleme zamanı başvuru derleme çözümlemesi sırasında aranacak konumların listesi. Daha önce listelenen yollar daha sonraki girişlerden daha öncelikli olduğundan, yolların bu listede görünme sırası anlamlı. |
| AssemblyName | .NET | Proje derlendikten sonra nihai çıkış derlemesinin adı. |
| BaseAddress | .NET | Ana çıkış derlemesinin temel adresini belirtir. Bu özellik, `/baseaddress` derleyici anahtarıyla eşdeğerdir. |
| Baseıntermediateoutputpath | Tümü | Yapılandırmaya özgü tüm ara çıkış klasörlerinin oluşturulduğu en üst düzey klasör. Varsayılan değer: `obj\`. Aşağıdaki kod bir örnektir: `<BaseIntermediateOutputPath>c:\xyz\obj\</BaseIntermediateOutputPath>` |
| BaseOutputPath | Tümü | Çıkış dosyası için temel yolu belirtir. Ayarlanırsa, MSBuild kullanır `OutputPath = $(BaseOutputPath)\$(Configuration)\` . Örnek sözdizimi: `<BaseOutputPath>c:\xyz\bin\</BaseOutputPath>` |
| BuildInParallel | Tümü | Multi-proc MSBuild kullanılırken proje başvurularının paralel olarak oluşturulup temizlenmediğini belirten bir Boolean değer. Varsayılan değer `true` , bu, sistemin birden çok çekirdeği veya işlemciyi varsa, projenin paralel olarak derlenme anlamına gelir. |
| BuildProjectReferences | Tümü | Proje başvurularının MSBuild tarafından oluşturulup oluşturulmayacağını gösteren bir Boolean değer. `false`Projenizi Visual Studio tümleşik geliştirme ortamında (IDE) oluşturuyorsanız, `true` Aksi takdirde olarak ayarlayın. `-p:BuildProjectReferences=false` , başvurulan projelerin güncel olup olmadığını kontrol etmekten kaçınmak için komut satırında belirtilebilir. |
| CleanFile | Tümü | "Temiz önbellek" olarak kullanılacak dosyanın adı. Temizleme önbelleği, temizleme işlemi sırasında silinecek oluşturulan dosyaların bir listesidir. Dosya, yapı işlemi tarafından ara çıkış yoluna konur.<br /><br /> Bu özellik yalnızca yol bilgilerine sahip olmayan dosya adlarını belirtir. |
| Sayfasının | .NET | Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfasını belirtir. Bu özellik, `/codepage` derleyici anahtarıyla eşdeğerdir. |
| CompilerResponseFile | .NET | Derleyici görevlerine geçirilebilecek, isteğe bağlı bir yanıt dosyası. |
| Yapılandırma | Tümü | Oluşturduğunuz `Debug` `Release` ve genellikle çözüm ve proje düzeylerinde yapılandırılabilen yapılandırma. |
| CscToolPath | C# | *csc.exe*yolu, C# derleyicisidir. |
| CustomBeforeMicrosoftCommonTargets | Tümü | Ortak hedefler içeri aktarmadan önce otomatik olarak içeri aktarılacak bir proje dosyasının veya hedef dosyanın adı. |
| DebugSymbols | Tümü | Sembolün derleme tarafından oluşturulup oluşturulmayacağını gösteren bir Boolean değer.<br /><br /> Komut satırında **-p:DebugSymbols = false** ayarı, program veritabanı (*. pdb*) sembol dosyalarının oluşturulmasını devre dışı bırakır. |
| DebugType | Tümü | Oluşturulmasını istediğiniz hata ayıklama bilgileri düzeyini tanımlar. Geçerli değerler şunlardır "Full," "pdbonly," "taşınabilir", "Embedded" ve "none". |
| Definesabitleri | .NET | Koşullu derleyici sabitlerini tanımlar. Sembol/değer çiftleri noktalı virgülle ayrılır ve aşağıdaki sözdizimi kullanılarak belirtilir:<br /><br /> *symbol1 = değer1; symbol2 = değer2*<br /><br /> Özelliği, `/define` derleyici anahtarıyla eşdeğerdir. |
| DefineDebug | Tümü |  Hata ayıklama sabitinin tanımlanmasını isteyip istemediğinizi belirten bir Boole değeri. |
| DefineTrace | Tümü | Izleme sabitinin tanımlanmasını isteyip istemediğinizi belirten bir Boole değeri. |
| DelaySign | .NET | Derlemeyi tam imzalamak yerine gecikmeye mi işaret etmek istediğinizi belirten Boolean bir değer. |
| Belirlenimci | .NET | Derleyicinin özdeş girdiler için özdeş derlemeler üretmesi gerekip gerekmediğini belirten bir Boolean değer. Bu parametre, `/deterministic` derleyicilerin anahtarına karşılık gelir. |
| DisableFastUpToDateCheck | Tümü | Yalnızca Visual Studio için geçerli olan bir Boole değeri. Visual Studio derleme Yöneticisi, bir projenin güncel olması için yeniden oluşturulması gerekip gerekmediğini öğrenmek için FastUpToDateCheck adlı bir işlem kullanır. Bu işlem, bunu anlamak için MSBuild kullanmaktan daha hızlıdır. DisableFastUpToDateCheck özelliğinin olarak ayarlanması, `true` Visual Studio yapı yöneticisini atlayıp projenin güncel olup olmadığını belirlemede MSBuild 'i kullanmaya zorlamanızı sağlar. |
| Belgetationfile | .NET | XML belge dosyası olarak oluşturulan dosyanın adı. Bu ad yalnızca dosya adını içerir ve yol bilgilerine sahip değildir. |
| ErrorReport | .NET | Derleyici görevinin iç derleyici hatalarını nasıl rapor etmesi gerektiğini belirtir. Geçerli değerler "Prompt", "send" veya "none" değerleridir. Bu özellik, `/errorreport` derleyici anahtarıyla eşdeğerdir. |
| ExcludeDeploymentUrl | .NET | [GenerateDeploymentManifest görevi](../msbuild/generatedeploymentmanifest-task.md) , proje dosyası aşağıdaki öğelerden herhangi birini içeriyorsa dağıtım bildirimine bir deploymentProvider etiketi ekler:<br /><br /> -UpdateUrl<br />-InstallUrl<br />-PublishUrl<br /><br /> Ancak, ExcludeDeploymentUrl kullanarak, yukarıdaki URL 'Lerden herhangi biri belirtilmiş olsa bile, dağıtım bildirimine deploymentProvider etiketinin eklenmesini engelleyebilirsiniz. Bunu yapmak için, aşağıdaki özelliği proje dosyanıza ekleyin:<br /><br /> `<ExcludeDeploymentUrl>true</ExcludeDeploymentUrl>` <br /><br />**Note:**  ExcludeDeploymentUrl, Visual Studio IDE 'de gösterilmez ve yalnızca proje dosyasını el ile düzenleyerek ayarlanabilir. Bu özelliğin ayarlanması, Visual Studio içinde yayımlamayı etkilemez; diğer bir deyişle, deploymentProvider etiketi yine PublishUrl tarafından belirtilen URL 'ye eklenecektir. |
| Dosya hizalaması | .NET | Çıktı dosyasının bölümlerinin hizalanın bayt cinsinden sayısını belirtir. Geçerli değerler 512, 1024, 2048, 4096, 8192. Bu özellik, `/filealignment` derleyici anahtarıyla eşdeğerdir. |
| FrameworkPathOverride | Visual Basic | *mscorlib.dll* ve *microsoft.visualbasic.dll*konumunu belirtir. Bu parametre `/sdkpath` *vbc.exe* derleyicisinin anahtarıyla eşdeğerdir. |
| GenerateDocumentation | .NET | Yapı tarafından belgelerin oluşturulup oluşturulmayacağını gösteren bir Boolean parametresi. `true`Derleme, belge bilgilerini oluşturur ve bir *. xml* dosyasına, derleme görevinin oluşturduğu yürütülebilir dosyanın veya kitaplığın adıyla birlikte koyar. |
| GenerateFullPaths | C# | [-Fullpaths](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option) derleyici seçeneğini kullanarak çıkışta dosya adları için tam yollar oluşturun. |
| GenerateSerializationAssemblies | .NET | XML serileştirme derlemelerinin *SGen.exe*tarafından oluşturulup oluşturulmayacağını, otomatik veya kapalı olarak ayarlanamayacağını gösterir. Bu özellik yalnızca .NET Framework hedef derlemeler için kullanılır. .NET Standard veya .NET Core derlemeleri için XML serileştirme derlemeleri oluşturmak için, *Microsoft.Xmlserileştirici. Generator* NuGet paketine başvurun. |
| IntermediateOutputPath | Tümü | Yol belirtilmemişse tam ara çıkış yolu öğesinden türetilir `BaseIntermediateOutputPath` . Örneğin, *\obj\debug \\ *. |
| KeyContainerName | Tümü | Tanımlayıcı ad anahtar kapsayıcısının adı. |
| Keyorigınatorfile | Tümü | Tanımlayıcı ad anahtar dosyasının adı. |
| ModuleAssemblyName | .NET | Derlenen modülün içine dahil edilecek derlemenin adı. Özelliği, `/moduleassemblyname` derleyici anahtarıyla eşdeğerdir. |
| Msbuildprojeclarsionspath | Tümü | Proje uzantılarının bulunduğu yolu belirtir. Varsayılan olarak, bu değeri ile aynı şekilde alır `BaseIntermediateOutputPath` . |
| NoLogo | Tümü | Derleyici logosunun kapatılmasını isteyip istemediğinizi belirten bir Boole değeri. Bu özellik, `/nologo` derleyici anahtarıyla eşdeğerdir. |
| NoStdLib | .NET | Standart kitaplığa (*mscorlib.dll*) başvurulmaya engellenip engellenmeyeceğini belirten bir Boole değeri. Varsayılan değer: `false`. |
| NoVBRuntimeReference | Visual Basic | Visual Basic çalışma zamanının (*Microsoft.VisualBasic.dll*) projeye başvuru olarak dahil edilip edilmeyeceğini belirten bir Boole değeri. |
| NoWarn | .NET | Belirtilen uyarıları bastırır. Uyarı tanımlayıcısının yalnızca sayısal kısmı belirtilmelidir. Birden çok uyarı noktalı virgülle ayrılır. Bu parametre, `/nowarn` derleyicilerin anahtarına karşılık gelir. |
| NoWin32Manifest | .NET | Kullanıcı hesabı denetimi (UAC) bildirim bilgisinin uygulamanın yürütülebilir dosyasına katıştırılacağını belirten bir Boole değeri. Yalnızca Windows Vista 'Yı hedefleyen Visual Studio projeleri için geçerlidir. ClickOnce ve kayıtsız COM kullanılarak dağıtılan projelerde, bu öğe yok sayılır. `False` (varsayılan değer) Kullanıcı hesabı denetimi (UAC) bildirim bilgisinin uygulamanın yürütülebilir dosyasına katıştırılacağını belirtir. `True` UAC bildirim bilgilerinin gömülmeyeceğini belirtir.<br /><br /> Bu özellik yalnızca Windows Vista 'Yı hedefleyen Visual Studio projeleri için geçerlidir. ClickOnce ve kayıtsız COM kullanılarak dağıtılan projelerde, bu özellik yok sayılır.<br /><br /> Yalnızca Visual Studio 'Nun uygulamanın yürütülebilir dosyasına herhangi bir bildirim bilgisini katıştırmayı istemiyorsanız NoWin32Manifest eklemeniz gerekir; Bu işleme *sanallaştırma*olarak adlandırılır. Sanallaştırmayı kullanmak için `<ApplicationManifest>` ile birlikte `<NoWin32Manifest>` aşağıdaki şekilde ayarlayın:<br /><br /> -Visual Basic projeleri için `<ApplicationManifest>` düğümünü kaldırın. (Visual Basic projelerinde, `<NoWin32Manifest>` bir `<ApplicationManifest>` düğüm varken yoksayılır.)<br />-C# projeleri için, `<ApplicationManifest>` `False` ve olarak ayarlayın `<NoWin32Manifest>` `True` . (C# projelerinde, `<ApplicationManifest>` geçersiz kılmalar `<NoWin32Manifest>` .)<br /> Bu özellik `/nowin32manifest` *vbc.exe*derleyici anahtarıyla eşdeğerdir. |
| İyileştirme | .NET | Olarak ayarlandığında `true` derleyici iyileştirmelerini sağlayan bir Boole değeri. Bu özellik, `/optimize` derleyici anahtarıyla eşdeğerdir. |
| OptionCompare | VisualBasic | Dize karşılaştırmalarının nasıl yapılacağını belirtir. Geçerli değerler şunlardır "binary" veya "Text." Bu özellik `/optioncompare` *vbc.exe*derleyici anahtarıyla eşdeğerdir. |
| OptionExplicit | Visual Basic | Olarak ayarlandığında `true` , kaynak koddaki değişkenlerin açık bildirimini gerektiren Boolean bir değer. Bu özellik, `/optionexplicit` derleyici anahtarıyla eşdeğerdir. |
| OptionInfer | Visual Basic | Olarak ayarlandığında `true` değişkenlerin tür çıkarımını sağlayan bir Boole değeri. Bu özellik, `/optioninfer` derleyici anahtarıyla eşdeğerdir. |
| OptionStrict | Visual Basic | Olarak ayarlandığında `true` , derleme görevinin örtük tür semantiğini zorlamak için katı tür semantiğini zorlamasına neden olan bir Boole değeri. Bu özellik `/optionstrict` *vbc.exe* derleyicisinin anahtarıyla eşdeğerdir. |
| OutDir | Tümü | Proje veya çözüm için son çıkış konumunu gösterir. Bir çözüm oluştururken, OutDir birden fazla proje çıkışını tek bir konumda toplamak için kullanılabilir. Ayrıca, OutDir başvuruları çözümlemek için kullanılan AssemblySearchPaths 'a dahildir. Örneğin, *bin\Debug*. |
| OutputPath | Tümü | Proje dizinine göre çıkış dizininin yolunu belirtir, örneğin, *bin\Debug*. |
| #B2 | Tümü |  Çıktı dosyasının dosya biçimini belirtir. Bu parametre aşağıdaki değerlerden birine sahip olabilir:<br /><br /> Kitaplığı. Bir kod kitaplığı oluşturur. (Varsayılan değer.)<br />Exe. Bir konsol uygulaması oluşturur.<br />Birimi. Bir modül oluşturur.<br />Winexe. Windows tabanlı bir program oluşturur.<br /><br /> C# ve Visual Basic için bu özellik anahtar ile eşdeğerdir `/target` . |
| OverwriteReadOnlyFiles | Tümü | Derlemeyi salt okuma dosyalarının üzerine yazmak veya bir hata tetiklemeyi etkinleştirmek isteyip istemediğinizi belirten bir Boole değeri. |
| PathMap | .NET | Derleyici tarafından giden kaynak yol adlarına fiziksel yolların nasıl eşleneceğini belirtir. Bu özellik, `/pathmap` derleyicilerin anahtarıyla eşdeğerdir. |
| Pdbdosya | .NET | Yayma yaptığınız *. pdb* dosyasının dosya adı. Bu özellik `/pdb` *csc.exe* derleyicisinin anahtarıyla eşdeğerdir. |
| Platform | Tümü | İçin oluşturmakta olduğunuz işletim sistemi. .NET Framework derlemeleri için örnekler şunlardır "Any CPU", "x86" ve "x64". |
| ProcessorArchitecture | .NET | Derleme başvuruları çözümlendiğinde kullanılan işlemci mimarisi. Geçerli değerler şunlardır "MSIL," "x86," "amd64" veya "ia64." |
| ProduceOnlyReferenceAssembly | .NET | Derleyiciye derlenen kod yerine yalnızca bir başvuru derlemesi yaymasını bildiren bir Boole değeri. İle birlikte kullanılamaz `ProduceReferenceAssembly` .  Bu özellik `/refonly` *vbc.exe* ve *csc.exe* derleyicilerinin anahtarına karşılık gelir. |
| ProduceReferenceAssembly | .NET | `true`Geçerli derleme için [başvuru derlemelerinin](/dotnet/standard/assembly/reference-assemblies) üretimini sağlamak üzere ayarlandığında ayarlanmış bir Boole değeri. `Deterministic``true`Bu özellik kullanılırken olmalıdır. Bu özellik `/refout` *vbc.exe* ve *csc.exe* derleyicilerinin anahtarına karşılık gelir. |
| Removeıntegerdenetimleri | Visual Basic | Tamsayı taşma hata denetimlerinin devre dışı bırakılıp başlatılmayacağını belirten bir Boole değeri. Varsayılan değer: `false`. Bu özellik `/removeintchecks` *vbc.exe* derleyicisinin anahtarıyla eşdeğerdir. |
| RootNamespace | Tümü | Gömülü bir kaynağı ad yazdığınızda kullanılacak kök ad alanı. Bu ad alanı, gömülü kaynak bildirim adının bir parçasıdır. |
| Satellite_AlgorithmId | .NET | Uydu derlemeleri oluşturulurken kullanılacak *AL.exe* karma algoritma kimliği. |
| Satellite_BaseAddress | .NET | Kültüre özgü uydu derlemeleri hedef kullanılarak oluşturulduğunda kullanılacak temel adres `CreateSatelliteAssemblies` . |
| Satellite_CompanyName | .NET | Uydu derleme oluşturma sırasında *AL.exe* geçirilecek şirket adı. |
| Satellite_Configuration | .NET | Uydu derleme oluşturma sırasında *AL.exe* geçirilecek yapılandırma adı. |
| Satellite_Description | .NET | Uydu derleme oluşturma sırasında *AL.exe* geçirilecek açıklama metni. |
| Satellite_EvidenceFile | .NET | Belirtilen dosyayı, "Security. kanıt" Kaynak adına sahip uydu derlemesine gömer. |
| Satellite_FileVersion | .NET | Uydu derlemesindeki dosya sürümü alanı için bir dize belirtir. |
| Satellite_Flags | .NET | Uydu derlemesindeki Flags alanı için bir değer belirtir. |
| Satellite_GenerateFullPaths | .NET | Derleme görevinin bir hata iletisinde bildirilen tüm dosyalar için mutlak yollar kullanmasına neden olur. |
| Satellite_LinkResource | .NET | Belirtilen kaynak dosyalarını bir uydu derlemesine bağlar. |
| Satellite_MainEntryPoint | .NET | Bir modül, uydu derleme oluşturma sırasında yürütülebilir bir dosyaya dönüştürüldüğünde giriş noktası olarak kullanılacak yöntemin tam nitelikli adını (yani, Class. yöntemi) belirtir. |
| Satellite_ProductName | .NET | Uydu derlemesindeki ürün alanı için bir dize belirtir. |
| Satellite_ProductVersion | .NET | Uydu derlemesinde ProductVersion alanı için bir dize belirtir. |
| Satellite_TargetType | .NET | Uydu derleme çıkış dosyasının dosya biçimini "Library," "exe" veya "Win" olarak belirtir. Varsayılan değer "Library" dir. |
| Satellite_Title | .NET | Uydu derlemesinde başlık alanı için bir dize belirtir. |
| Satellite_Trademark | .NET | Uydu derlemesindeki ticari marka alanı için bir dize belirtir. |
| Satellite_Version | .NET | Uydu derlemesinin sürüm bilgilerini belirtir. |
| Satellite_Win32Icon | .NET | Uydu derlemesine bir *. ico* simge dosyası ekler. |
| Satellite_Win32Resource | .NET | Uydu derlemesine bir Win32 kaynağı (*. res* dosyası) ekler. |
| SGenToolPath | .NET | Geçerli *SGen.exe* sürümü geçersiz kılındığında *SGen.exe* nereden alınacağını belirten isteğe bağlı bir araç yolu. |
| SGenUseProxyTypes | .NET | Proxy türlerinin *SGen.exe*tarafından oluşturulup oluşturulmayacağını gösteren Boolean bir değer. Bu yalnızca *GenerateSerializationAssemblies* on olarak ayarlandığında geçerlidir.<br /><br /> SGen hedefi, UseProxyTypes bayrağını ayarlamak için bu özelliği kullanır. Bu özellik varsayılan olarak true değerini alır ve bunu değiştirmek için bir kullanıcı arabirimi yoktur. Web hizmeti olmayan türler için serileştirme derlemesini oluşturmak için, bu özelliği proje dosyasına ekleyin ve *Microsoft. Common. targets* veya *C#/vb.exe*' i içeri aktarmadan önce false olarak ayarlayın. |
| Skipınvalidconfigurations | Tümü | Ne zaman `true` , geçersiz platform ve yapılandırma birleşimleri üzerinde bir uyarı oluştur, ancak derlemeyi başarısız yap; ne zaman `false` veya tanımsız (varsayılan), bir hata oluşturur. |
| StartupObject | .NET | Ana yöntemi veya alt ana yordamı içeren sınıfı veya modülü belirtir. Bu özellik, `/main` derleyici anahtarıyla eşdeğerdir. |
| SubsystemVersion | .NET | Oluşturulan yürütülebilir dosyanın kullanabileceği alt sistemin en düşük sürümünü belirtir. Bu özellik, `/subsystemversion` derleyici anahtarıyla eşdeğerdir. Bu özelliğin varsayılan değeri hakkında daha fazla bilgi için bkz. [/subsystemversion (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/subsystemversion) veya [/subsystemversion (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/subsystemversion-compiler-option). |
| TargetCompactFramework | .NET | Oluşturmakta olduğunuz uygulamayı çalıştırmak için gereken .NET Compact Framework sürümü. Bunu belirtmek, başka türlü başvuramayacak bazı Framework derlemelerine başvurmanıza olanak sağlar. |
| TargetFrameworkVersion | .NET | Oluşturmakta olduğunuz uygulamayı çalıştırmak için gereken .NET Framework sürümü. Bunu belirtmek, başka türlü başvuramayacak bazı Framework derlemelerine başvurmanıza olanak sağlar. |
| TreatWarningsAsErrors | .NET | `true`Tüm uyarıların hata olarak işlenmesine neden olan bir Boole parametresi. Bu parametre, `/nowarn` derleyici anahtarıyla eşdeğerdir. |
| UseHostCompilerIfAvailable | .NET | Varsa, derleme görevinin, varsa `true` işlem içi derleyici nesnesini kullanmasına neden olan bir Boole parametresi. Bu parametre yalnızca Visual Studio tarafından kullanılır. |
| Utf8Output | .NET | `true`, Derleyici ÇıKıŞıNı UTF-8 kodlaması kullanarak günlüğe kaydeden bir Boolean parametresi. Bu parametre, `/utf8Output` derleyici anahtarıyla eşdeğerdir. |
| VbcToolPath | Visual Basic | Geçerli *vbc.exe* sürümü geçersiz kılındığında *vbc.exe* başka bir konum belirten isteğe bağlı bir yol. |
| Vbcayrıntı düzeyi | Visual Basic | Visual Basic derleyicisinin çıkışının ayrıntı düzeyini belirtir. Geçerli değerler şunlardır "sessiz," "normal" (varsayılan değer) veya "ayrıntılıdır." |
| VisualStudioVersion | Tümü | Bu projenin çalıştığı kabul edileceği Visual Studio sürümünü belirtir. Bu özellik belirtilmezse, MSBuild bunu makul bir varsayılan değere ayarlar.<br /><br /> Bu özellik, derleme için kullanılan hedef kümesini belirtmek için çeşitli proje türlerinde kullanılır. `ToolsVersion`Bir proje için 4,0 veya üzeri bir değere ayarlanırsa, `VisualStudioVersion` hangi alt araç takımını kullanacağınızı belirtmek için kullanılır. Daha fazla bilgi için bkz. [araç takımı (araçları sürümü)](../msbuild/msbuild-toolset-toolsversion.md). |
| WarningsAsErrors | .NET | Hata olarak değerlendirmek için uyarıların listesini belirtir. Bu parametre, `/warnaserror` derleyici anahtarıyla eşdeğerdir. |
| Warninggözetimi Taserrors | .NET | Hata olarak değerlendirilmediğini belirten uyarıların bir listesini belirtir. Bu parametre, `/warnaserror` derleyici anahtarıyla eşdeğerdir. |
| Win32Manifest | .NET | Son derlemeye katıştırılması gereken bildirim dosyasının adı. Bu parametre, `/win32Manifest` derleyici anahtarıyla eşdeğerdir. |
| Win32Resource | .NET | Son derlemeye katıştırılacak Win32 kaynağının dosya adı. Bu parametre, `/win32resource` derleyici anahtarıyla eşdeğerdir. |

## <a name="see-also"></a>Ayrıca bkz.

- [Yaygın MSBuild proje öğeleri](../msbuild/common-msbuild-project-items.md)
- [Yaygın MSBuild öğesi meta verileri](common-msbuild-item-metadata.md)
- [MSBuild ayrılmış ve Iyi bilinen Özellikler](msbuild-reserved-and-well-known-properties.md)
