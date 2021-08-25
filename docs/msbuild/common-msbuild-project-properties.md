---
title: Ortak MSBuild Project Özellikleri | Microsoft Docs
description: Proje dosyalarında tanımlan MSBuild veya proje dosyalarında kullanılana ya da bu dosyaların sağladığı .targets dosyalarına dahil olan yaygın MSBuild öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 55d2ecda1619f187f1a1fdd0854eb1e3dd1d7fb8
ms.sourcegitcommit: 92cfc4b09f2f1847fb3af72521e304af9a3c35b6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2021
ms.locfileid: "122765482"
---
# <a name="common-msbuild-project-properties"></a>Yaygın MSBuild proje özellikleri

Aşağıdaki tabloda, proje dosyalarında tanımlanan veya Visual Studio *.targets* dosyalarına dahil edilen sık kullanılan MSBuild listele.

 Visual Studio Project *(.csproj*, *.vbproj*, *.vcxproj* ve diğerleri) MSBuild dosyaları, IDE kullanarak bir proje derlemek için çalışan MSBuild XML kodu içerir. Projeler genellikle derleme işlemlerini tanımlamak için bir veya daha fazla *.targets* dosyası içeri aktarıyor. Daha fazla bilgi için [bkz. MSBuild .targets dosyaları.](../msbuild/msbuild-dot-targets-files.md)

## <a name="list-of-common-properties-and-parameters"></a>Ortak özellikler ve parametrelerin listesi

| Özellik veya parametre adı | Project türleri | Description |
|------------------------------------| - | - |
| AdditionalLibPaths | .NET | Derleyicilerin başvuru derlemelerini araması gereken ek klasörleri belirtir. |
| AddModules | .NET | Derleyicinin, belirtilen dosyalardan gelen tüm tür bilgilerini derleyeni proje için kullanılabilir hale yüklemesini sağlar. Bu özellik, derleyici `/addModules` anahtarına eşdeğerdir. |
| ALToolPath | .NET | Bu *AL.exe* yolu. Bu özellik, farklı bir sürümün *AL.exe* için geçerli sürümü geçersiz kılar. |
| ApplicationIcon | .NET | Win32 simgesi olarak eklemek için derleyiciye geçecek *.ico* simge dosyası. özelliği derleyici `/win32icon` anahtarına eşdeğerdir. |
| ApplicationManifest | Tümü | Dış Kullanıcı Hesabı Denetimi (UAC) bildirim bilgilerini oluşturmak için kullanılan dosyanın yolunu belirtir. Yalnızca Vista'Visual Studio hedef alan tüm Windows için geçerlidir.<br /><br /> Çoğu durumda bildirim ekli olur. Ancak, KayıtSız COM veya ClickOnce kullanıyorsanız, bildirim uygulama derlemeleriniz ile birlikte yüklenmiş bir dış dosya olabilir. Daha fazla bilgi için bu konudaki NoWin32Manifest özelliğine bakın. |
| AssemblyOriginatorKeyFile | .NET | Derlemeyi imzalamak için kullanılan dosyayı (*.snk* veya *.pfx*) belirtir ve derlemeyi imzalamak için kullanılan gerçek anahtarı oluşturmak için [ResolveKeySource](../msbuild/resolvekeysource-task.md) görevine geçirilen dosyayı belirtir. |
| AssemblySearchPaths | .NET | Derleme zamanı başvuru derleme çözümlemesi sırasında aranacak konumların listesi. Yolların bu listede görünme sırası anlamlıdır çünkü daha önce listelenen yollar sonraki girişlere göre önceliklidir. |
| Assemblyname | .NET | Proje yapıldıktan sonra son çıkış derlemenin adı. |
| Baseaddress | .NET | Ana çıkış derlemenin temel adresini belirtir. Bu özellik, derleyici `/baseaddress` anahtarına eşdeğerdir. |
| BaseIntermediateOutputPath | Tümü | Tüm yapılandırmaya özgü ara çıkış klasörlerinin oluşturul bulunduğu üst düzey klasör. `obj\` varsayılan değerdir. Aşağıdaki kod bir örnektir: `<BaseIntermediateOutputPath>c:\xyz\obj\</BaseIntermediateOutputPath>` |
| BaseOutputPath | Tümü | Çıkış dosyasının temel yolunu belirtir. Ayarlanırsa, MSBuild `OutputPath = $(BaseOutputPath)\$(Configuration)\` kullanır. Örnek söz dizimi: `<BaseOutputPath>c:\xyz\bin\</BaseOutputPath>` |
| BuildInParallel | Tümü | Multi-Proc MSBuild kullanılırken proje başvurularını paralel olarak mı yoksa paralel olarak mı MSBuild boole değeri. Varsayılan değer, sistemin birden çok çekirdeği veya işlemcisi varsa projelerin paralel olarak inşa `true` edilecekleri anlamına gelir. |
| BuildProjectReferences | Tümü | Proje başvurularını bir uygulama tarafından yapılıp yapıl olmadığını gösteren bir boole MSBuild. Projenizi `false` tümleşik geliştirme ortamında (IDE) Visual Studio ise otomatik olarak `true` olarak ayarlayın. `-p:BuildProjectReferences=false` başvurulan projelerin güncel olup olamaması için komut satırına belirtilebilir. |
| CleanFile | Tümü | "Temiz önbellek" olarak kullanılacak dosyanın adı. Temiz önbellek, temizleme işlemi sırasında silinecek oluşturulan dosyaların listesidir. Dosya, derleme işlemi tarafından ara çıkış yoluna kondur.<br /><br /> Bu özellik yalnızca yol bilgisi olan dosya adlarını belirtir. |
| Codepage | .NET | Derlemede tüm kaynak kodu dosyaları için kullanılan kod sayfasını belirtir. Bu özellik, derleyici `/codepage` anahtarına eşdeğerdir. |
| CompilerResponseFile | .NET | Derleyici görevlerine geçirilen isteğe bağlı bir yanıt dosyası. |
| Yapılandırma | Tümü | Genellikle veya olarak, ancak çözüm `Debug` ve `Release` proje düzeylerinde yapılandırılabilir olan, ancak sizin için yapılandıran yapılandırma. |
| CscToolPath | C# | C# *derleyicisi* csc.exeyolu. |
| CustomBeforeMicrosoftCommonTargets | Tümü | Ortak hedefler içeri aktarmadan önce otomatik olarak içeri aktar edilecek proje dosyasının veya hedef dosyasının adı. |
| DebugSymbols | Tümü | Sembollerin derleme tarafından oluşturulıp oluşturula olmadığını gösteren bir boole değeri.<br /><br /> Komut **satırı üzerinde -p:DebugSymbols=false** ayarı, program veritabanı (*.pdb*) sembol dosyalarının neslini devre dışı bırakır. |
| DebugType | Tümü | Oluşturmak istediğiniz hata ayıklama bilgileri düzeyini tanımlar. Geçerli değerler "full", "pdbonly", "portable", "embedded" ve "none" değerleridir. |
| DefineConstants | .NET | Koşullu derleyici sabitlerini tanımlar. Sembol/değer çiftleri noktalı virgülle ayrılır ve aşağıdaki söz dizimi kullanılarak belirtilir:<br /><br /> *symbol1 = değer1; symbol2 = değer2*<br /><br /> Özelliği, `/define` derleyici anahtarıyla eşdeğerdir. |
| DefineDebug | Tümü |  Hata ayıklama sabitinin tanımlanmasını isteyip istemediğinizi belirten bir Boole değeri. |
| DefineTrace | Tümü | Izleme sabitinin tanımlanmasını isteyip istemediğinizi belirten bir Boole değeri. |
| DelaySign | .NET | Derlemeyi tam imzalamak yerine gecikmeye mi işaret etmek istediğinizi belirten Boolean bir değer. |
| Belirlenimci | .NET | Derleyicinin özdeş girdiler için özdeş derlemeler üretmesi gerekip gerekmediğini belirten bir Boolean değer. Bu parametre, `/deterministic` derleyicilerin anahtarına karşılık gelir. |
| DisableFastUpToDateCheck | Tümü | yalnızca Visual Studio için geçerli olan bir boole değeri. Visual Studio yapı yöneticisi, bir projenin güncel olup olmadığını anlamak için fastuptodatecheck adlı bir işlem kullanır. bu işlem, bunu anlamak için MSBuild kullanmaktan daha hızlıdır. disablefastuptodatecheck özelliğinin olarak ayarlanması, `true` Visual Studio yapı yöneticisini atlayıp projenin güncel olup olmadığını belirlemede MSBuild kullanmaya zorlamanızı sağlar. |
| Belgetationfile | .NET | XML belge dosyası olarak oluşturulan dosyanın adı. Bu ad yalnızca dosya adını içerir ve yol bilgilerine sahip değildir. |
| ErrorReport | .NET | Derleyici görevinin iç derleyici hatalarını nasıl rapor etmesi gerektiğini belirtir. Geçerli değerler "Prompt", "send" veya "none" değerleridir. Bu özellik, `/errorreport` derleyici anahtarıyla eşdeğerdir. |
| ExcludeDeploymentUrl | .NET | [GenerateDeploymentManifest görevi](../msbuild/generatedeploymentmanifest-task.md) , proje dosyası aşağıdaki öğelerden herhangi birini içeriyorsa dağıtım bildirimine bir deploymentProvider etiketi ekler:<br /><br /> -UpdateUrl<br />-InstallUrl<br />-PublishUrl<br /><br /> Ancak, ExcludeDeploymentUrl kullanarak, yukarıdaki URL 'Lerden herhangi biri belirtilmiş olsa bile, dağıtım bildirimine deploymentProvider etiketinin eklenmesini engelleyebilirsiniz. Bunu yapmak için, aşağıdaki özelliği proje dosyanıza ekleyin:<br /><br /> `<ExcludeDeploymentUrl>true</ExcludeDeploymentUrl>` <br /><br />**Note:**  excludedeploymenturl Visual Studio ıde 'de gösterilmez ve yalnızca proje dosyasını el ile düzenleyerek ayarlanabilir. Bu özelliğin ayarlanması Visual Studio içinde yayımlamayı etkilemez; diğer bir deyişle, deploymentProvider etiketi yine PublishUrl tarafından belirtilen URL 'ye eklenecektir. |
| Dosya hizalaması | .NET | Çıktı dosyasının bölümlerinin hizalanın bayt cinsinden sayısını belirtir. Geçerli değerler 512, 1024, 2048, 4096, 8192. Bu özellik, `/filealignment` derleyici anahtarıyla eşdeğerdir. |
| FrameworkPathOverride | Visual Basic | *mscorlib.dll* ve *microsoft.visualbasic.dll* konumunu belirtir. Bu parametre `/sdkpath` *vbc.exe* derleyicisinin anahtarıyla eşdeğerdir. |
| GenerateDocumentation | .NET | Yapı tarafından belgelerin oluşturulup oluşturulmayacağını gösteren bir Boolean parametresi. `true`Derleme, belge bilgilerini oluşturur ve yapı görevinin oluşturduğu yürütülebilir dosyanın veya kitaplığın adıyla birlikte bir *.xml* dosyasına koyar. |
| GenerateFullPaths | C# | [-Fullpaths](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option) derleyici seçeneğini kullanarak çıkışta dosya adları için tam yollar oluşturun. |
| GenerateSerializationAssemblies | .NET | XML serileştirme derlemelerinin *SGen.exe* tarafından oluşturulup oluşturulmayacağını, otomatik veya kapalı olarak ayarlanamayacağını gösterir. bu özellik yalnızca .NET Framework hedef derlemeler için kullanılır. .NET Standard veya .net Core derlemeleri için XML serileştirme derlemeleri oluşturmak için, *Microsoft.Xmlserileştirici. Generator* NuGet paketine başvurun. |
| IntermediateOutputPath | Tümü | Yol belirtilmemişse tam ara çıkış yolu öğesinden türetilir `BaseIntermediateOutputPath` . Örneğin, *obj\Debug \\*. |
| KeyContainerName | Tümü | Tanımlayıcı ad anahtar kapsayıcısının adı. |
| Keyorigınatorfile | Tümü | Tanımlayıcı ad anahtar dosyasının adı. |
| ModuleAssemblyName | .NET | Derlenen modülün içine dahil edilecek derlemenin adı. Özelliği, `/moduleassemblyname` derleyici anahtarıyla eşdeğerdir. |
| Msbuildprojeclarsionspath | Tümü | Proje uzantılarının bulunduğu yolu belirtir. Varsayılan olarak, bu değeri ile aynı şekilde alır `BaseIntermediateOutputPath` . |
| NoLogo | Tümü | Derleyici logosunun kapatılmasını isteyip istemediğinizi belirten bir Boole değeri. Bu özellik, `/nologo` derleyici anahtarıyla eşdeğerdir. |
| NoStdLib | .NET | Standart kitaplığa (*mscorlib.dll*) başvurulmaya engellenip engellenmeyeceğini belirten bir Boole değeri. `false` varsayılan değerdir. |
| NoVBRuntimeReference | Visual Basic | Visual Basic çalışma zamanının (*Microsoft.VisualBasic.dll*) projeye başvuru olarak dahil edilip edilmeyeceğini belirten bir boole değeri. |
| NoWarn | .NET | Belirtilen uyarıları bastırır. Uyarı tanımlayıcısının yalnızca sayısal kısmı belirtilmelidir. Birden çok uyarı noktalı virgülle ayrılır. Bu parametre, `/nowarn` derleyicilerin anahtarına karşılık gelir. |
| NoWin32Manifest | .NET | Kullanıcı hesabı denetimi (UAC) bildirim bilgisinin uygulamanın yürütülebilir dosyasına katıştırılacağını belirten bir Boole değeri. yalnızca Windows Vista 'yı hedefleyen Visual Studio projeleri için geçerlidir. ClickOnce ve COM Registration-Free kullanılarak dağıtılan projelerde, bu öğe yok sayılır. `False` (varsayılan değer) Kullanıcı hesabı denetimi (UAC) bildirim bilgisinin uygulamanın yürütülebilir dosyasına katıştırılacağını belirtir. `True` UAC bildirim bilgilerinin gömülmeyeceğini belirtir.<br /><br /> bu özellik yalnızca Windows Vista 'yı hedefleyen Visual Studio projeler için geçerlidir. ClickOnce ve COM Registration-Free kullanılarak dağıtılan projelerde, bu özellik yok sayılır.<br /><br /> yalnızca uygulamanın yürütülebilir dosyasına herhangi bir bildirim bilgisini eklemek Visual Studio istemiyorsanız NoWin32Manifest eklemeniz gerekir; Bu işleme *sanallaştırma* olarak adlandırılır. Sanallaştırmayı kullanmak için `<ApplicationManifest>` ile birlikte `<NoWin32Manifest>` aşağıdaki şekilde ayarlayın:<br /><br /> -Visual Basic projeleri için `<ApplicationManifest>` düğümünü kaldırın. (Visual Basic projelerinde, `<NoWin32Manifest>` bir `<ApplicationManifest>` düğüm varken yoksayılır.)<br />-C# projeleri için, `<ApplicationManifest>` `False` ve olarak ayarlayın `<NoWin32Manifest>` `True` . (C# projelerinde, `<ApplicationManifest>` geçersiz kılmalar `<NoWin32Manifest>` .)<br /> Bu özellik `/nowin32manifest` *vbc.exe* derleyici anahtarıyla eşdeğerdir. |
| İyileştirme | .NET | Olarak ayarlandığında `true` derleyici iyileştirmelerini sağlayan bir Boole değeri. Bu özellik, `/optimize` derleyici anahtarıyla eşdeğerdir. |
| OptionCompare | VisualBasic | Dize karşılaştırmalarının nasıl yapılacağını belirtir. Geçerli değerler şunlardır "binary" veya "Text." Bu özellik `/optioncompare` *vbc.exe* derleyici anahtarıyla eşdeğerdir. |
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
| Removeıntegerdenetimleri | Visual Basic | Tamsayı taşma hata denetimlerinin devre dışı bırakılıp başlatılmayacağını belirten bir Boole değeri. `false` varsayılan değerdir. Bu özellik `/removeintchecks` *vbc.exe* derleyicisinin anahtarıyla eşdeğerdir. |
| RootNamespace | Tümü | Gömülü bir kaynağı ad yazdığınızda kullanılacak kök ad alanı. Bu ad alanı, gömülü kaynak bildirim adının bir parçasıdır. |
| Satellite_AlgorithmId | .NET | Uydu derlemeleri oluşturulurken kullanılacak *AL.exe* karma algoritma kimliği. |
| Satellite_BaseAddress | .NET | Kültüre özgü uydu derlemeleri hedef kullanılarak oluşturulduğunda kullanılacak temel adres `CreateSatelliteAssemblies` . |
| Satellite_CompanyName | .NET | Uydu derleme oluşturma sırasında *AL.exe* şirket adı. |
| Satellite_Configuration | .NET | Uydu derleme oluşturma sırasında *AL.exe* yapılandırma adı. |
| Satellite_Description | .NET | Uydu derlemesi oluşturma sırasında *AL.exe* için açıklama metni. |
| Satellite_EvidenceFile | .NET | Belirtilen dosyayı "Security.Evidence" kaynak adına sahip uydu derlemeye katıştırır. |
| Satellite_FileVersion | .NET | Uydu derlemesinde Dosya Sürümü alanı için bir dize belirtir. |
| Satellite_Flags | .NET | Uydu derlemesinde Flags alanı için bir değer belirtir. |
| Satellite_GenerateFullPaths | .NET | Derleme görevinin bir hata iletisinde bildirilen tüm dosyalar için mutlak yolları kullanmasını sağlar. |
| Satellite_LinkResource | .NET | Belirtilen kaynak dosyalarını bir uydu derlemeye bağlar. |
| Satellite_MainEntryPoint | .NET | Bir modül uydu derlemesi oluşturma sırasında yürütülebilir bir dosyaya dönüştürülürken giriş noktası olarak kullanmak için yönteminin tam adını (yani class.method) belirtir. |
| Satellite_ProductName | .NET | Uydu derlemesinde Product alanı için bir dize belirtir. |
| Satellite_ProductVersion | .NET | Uydu derlemesinde ProductVersion alanı için bir dize belirtir. |
| Satellite_TargetType | .NET | Uydu derleme çıkış dosyasının dosya biçimini "kitaplık," "exe" veya "win" olarak belirtir. Varsayılan değer "kitaplık"tır. |
| Satellite_Title | .NET | Uydu derlemesinde Title alanı için bir dize belirtir. |
| Satellite_Trademark | .NET | Uydu derlemesinde Ticari Marka alanı için bir dize belirtir. |
| Satellite_Version | .NET | Uydu derlemesi için sürüm bilgilerini belirtir. |
| Satellite_Win32Icon | .NET | Uydu *derlemeye bir .ico* simge dosyası ekler. |
| Satellite_Win32Resource | .NET | Uydu derlemesine bir Win32 kaynağı (*.res* dosyası) ekler. |
| SGenToolPath | .NET | Geçerli sürümünün geçersiz kılınma durumuna *SGen.exe* isteğe bağlı bir *araçSGen.exe* yolu. |
| SGenUseProxyTypes | .NET | Ara sunucu türlerinin tarafından oluşturulıp oluşturulmay gerektiğini belirten bir boole *değeri* SGen.exe. Bu yalnızca *GenerateSerializationAssemblies* açık olarak ayarlanırken geçerlidir.<br /><br /> SGen hedefi, UseProxyTypes bayrağını ayarlamak için bu özelliği kullanır. Bu özellik varsayılan olarak true'ya sahip olur ve bunu değiştirmek için bir kullanıcı arabirimi yoktur. Web hizmeti olmayan türler için serileştirme derlemesi oluşturmak için, bu özelliği proje dosyasına ekleyin ve *Microsoft.Common.Targets* veya *C#/VB.targets'i* içeri aktarmadan önce false olarak ayarlayın. |
| SkipInvalidConfigurations | Tümü | olduğunda, geçersiz platform ve yapılandırma birleşimleri üzerinde bir uyarı üretir, ancak derlemeyi başarısız olmaz; tanımsız `true` `false` olduğunda veya tanımlanmamış olduğunda (varsayılan), bir hata üretir. |
| StartupObject | .NET | Main yöntemini veya Sub Main yordamını içeren sınıfı veya modülü belirtir. Bu özellik, derleyici `/main` anahtarına eşdeğerdir. |
| SubsystemVersion | .NET | Oluşturulan yürütülebilir dosyanın kullanabileceği alt sistemin en düşük sürümünü belirtir. Bu özellik, derleyici `/subsystemversion` anahtarına eşdeğerdir. Bu özelliğin varsayılan değeri hakkında bilgi için bkz. [/subsystemversion (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/subsystemversion) veya [/subsystemversion (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/subsystemversion-compiler-option). |
| TargetCompactFramework | .NET | Uygulamanın .NET Compact Framework uygulamayı çalıştırmak için gereken sürüm. Bunun belirterek, aksi takdirde başvuramayabilecek belirli çerçeve derlemelerine başvurasınız. |
| TargetFrameworkVersion | .NET | Uygulamanın .NET Framework uygulamayı çalıştırmak için gereken sürümü. Bunun belirterek, aksi takdirde başvuramayabilecek belirli çerçeve derlemelerine başvurasınız. |
| TreatWarningsAsErrors | .NET | varsa, tüm uyarıların hata olarak kabul edilirse neden olduğu bir boole `true` parametresi. Bu parametre, derleyici `/nowarn` anahtarına eşdeğerdir. |
| UseHostCompilerIfAvailable | .NET | varsa, derleme görevinin işlem içinde derleyici nesnesini kullanmalarına neden olan bir boole `true` parametresi. Bu parametre yalnızca Visual Studio. |
| Utf8Output | .NET | ise, derleyici çıkışını UTF-8 kodlamasını kullanarak günlüğe kaydeden bir boole `true` parametresi. Bu parametre, derleyici `/utf8Output` anahtarına eşdeğerdir. |
| VbcToolPath | Visual Basic | Geçerli sürümü geçersiz kılınmış olduğunda *vbc.exe* konum belirten *isteğevbc.exe* yolu. |
| VbcVerbosity | Visual Basic | Derleyicinin çıkışının ayrıntılı Visual Basic belirtir. Geçerli değerler şunlardır "sessiz," "normal" (varsayılan değer) veya "ayrıntılıdır." |
| VisualStudioVersion | Tümü | bu projenin çalışıyor olarak değerlendirilmesi gereken Visual Studio sürümünü belirtir. bu özellik belirtilmezse, MSBuild makul bir varsayılan değere ayarlar.<br /><br /> Bu özellik, derleme için kullanılan hedef kümesini belirtmek için çeşitli proje türlerinde kullanılır. `ToolsVersion`Bir proje için 4,0 veya üzeri bir değere ayarlanırsa, `VisualStudioVersion` hangi alt araç takımını kullanacağınızı belirtmek için kullanılır. Daha fazla bilgi için bkz. [araç takımı (araçları sürümü)](../msbuild/msbuild-toolset-toolsversion.md). |
| WarningsAsErrors | .NET | Hata olarak değerlendirmek için uyarıların listesini belirtir. Bu parametre, `/warnaserror` derleyici anahtarıyla eşdeğerdir. |
| Warninggözetimi Taserrors | .NET | Hata olarak değerlendirilmediğini belirten uyarıların bir listesini belirtir. Bu parametre, `/warnaserror` derleyici anahtarıyla eşdeğerdir. |
| Win32Manifest | .NET | Son derlemeye katıştırılması gereken bildirim dosyasının adı. Bu parametre, `/win32Manifest` derleyici anahtarıyla eşdeğerdir. |
| Win32Resource | .NET | Son derlemeye katıştırılacak Win32 kaynağının dosya adı. Bu parametre, `/win32resource` derleyici anahtarıyla eşdeğerdir. |

## <a name="see-also"></a>Ayrıca bkz.

- [Yaygın MSBuild proje öğeleri](../msbuild/common-msbuild-project-items.md)
- [Yaygın MSBuild öğesi meta verileri](common-msbuild-item-metadata.md)
- [MSBuild Ayrılmış ve Iyi bilinen Özellikler](msbuild-reserved-and-well-known-properties.md)
- [.net SDK projeleri için MSBuild başvurusu](/dotnet/core/project-sdk/msbuild-props)
