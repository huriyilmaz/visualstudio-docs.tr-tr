---
title: ortak MSBuild Project özellikleri | Microsoft Docs
description: proje dosyalarında tanımlanabilir veya kullanılabilir olan veya MSBuild tarafından sağlanan. targets dosyalarına dahil olabilecek ortak MSBuild proje özellikleri hakkında bilgi edinin.
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
ms.openlocfilehash: 28ce682f6ea5070f0551f10a521e4874a38ed40c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122055074"
---
# <a name="common-msbuild-project-properties"></a>Yaygın MSBuild proje özellikleri

aşağıdaki tabloda Visual Studio proje dosyalarında tanımlanan veya MSBuild tarafından sağlanan *. targets* dosyalarına eklenen sık kullanılan özellikler listelenmiştir.

 Visual Studio (*. csproj*, *. vbproj*, *. vcxproj* ve diğerleri) Project dosyaları, ıde kullanarak bir proje oluşturduğunuzda çalışan MSBuild XML kodu içerir. Projeler genellikle derleme işlemlerini tanımlamak için bir veya daha fazla *. targets* dosyasını içeri aktarır. daha fazla bilgi için bkz [. MSBuild. targets dosyaları](../msbuild/msbuild-dot-targets-files.md).

## <a name="list-of-common-properties-and-parameters"></a>Ortak özellikler ve parametrelerin listesi

| Özellik veya parametre adı | Project türleri | Açıklama |
|------------------------------------| - | - |
| Adtiontalbpaths | .NET | Derleyicilerin başvuru derlemelerini arayacağı ek klasörleri belirtir. |
| AddModules | .NET | Derleyicinin, belirtilen dosyalardaki tüm tür bilgilerini derlediğiniz proje için kullanılabilir hale getirmesine neden olur. Bu özellik, `/addModules` derleyici anahtarıyla eşdeğerdir. |
| ALToolPath | .NET | *AL.exe* bulunabileceği yol. Bu özellik, farklı bir sürümün kullanımını etkinleştirmek için geçerli *AL.exe* sürümünü geçersiz kılar. |
| ApplicationIcon | .NET | Bir Win32 simgesi olarak katıştırmak üzere derleyiciye geçirilecek *. ico* simge dosyası. Özelliği, `/win32icon` derleyici anahtarıyla eşdeğerdir. |
| ApplicationManifest | Tümü | Dış Kullanıcı hesabı denetimi (UAC) bildirim bilgilerini oluşturmak için kullanılan dosyanın yolunu belirtir. yalnızca Windows Vista 'yı hedefleyen Visual Studio projeleri için geçerlidir.<br /><br /> Çoğu durumda, bildirim katıştırılır. ancak kayıt ücretsiz COM veya ClickOnce dağıtımı kullanırsanız, bildirim, uygulama derlemeleriyle birlikte yüklenen bir dış dosya olabilir. Daha fazla bilgi için bu konudaki NoWin32Manifest özelliğine bakın. |
| AssemblyOriginatorKeyFile | .NET | Derlemeyi (*. snk* veya *. pfx*) imzalamak için kullanılan dosyayı belirtir ve derlemeyi imzalamak için kullanılan gerçek anahtarı oluşturmak için [ResolveKeySource görevine](../msbuild/resolvekeysource-task.md) geçirilir. |
| AssemblySearchPaths | .NET | Derleme zamanı başvuru derleme çözümlemesi sırasında aranacak konumların listesi. Daha önce listelenen yollar daha sonraki girişlerden daha öncelikli olduğundan, yolların bu listede görünme sırası anlamlı. |
| AssemblyName | .NET | Proje derlendikten sonra nihai çıkış derlemesinin adı. |
| BaseAddress | .NET | Ana çıkış derlemesinin temel adresini belirtir. Bu özellik, `/baseaddress` derleyici anahtarıyla eşdeğerdir. |
| Baseıntermediateoutputpath | Tümü | Yapılandırmaya özgü tüm ara çıkış klasörlerinin oluşturulduğu en üst düzey klasör. `obj\` varsayılan değerdir. Aşağıdaki kod bir örnektir: `<BaseIntermediateOutputPath>c:\xyz\obj\</BaseIntermediateOutputPath>` |
| BaseOutputPath | Tümü | Çıkış dosyası için temel yolu belirtir. ayarlanırsa, MSBuild kullanacaktır `OutputPath = $(BaseOutputPath)\$(Configuration)\` . Örnek sözdizimi: `<BaseOutputPath>c:\xyz\bin\</BaseOutputPath>` |
| BuildInParallel | Tümü | Multi-Proc MSBuild kullanıldığında, proje başvurularının paralel olarak oluşturulup temizlenmediğini belirten bir boolean değer. Varsayılan değer `true` , bu, sistemin birden çok çekirdeği veya işlemciyi varsa, projenin paralel olarak derlenme anlamına gelir. |
| BuildProjectReferences | Tümü | Proje başvurularının MSBuild tarafından oluşturulup oluşturulmayacağını gösteren Boolean bir değer. `false`projenizi Visual Studio tümleşik geliştirme ortamında (ıde) oluşturuyorsanız, `true` aksi takdirde olarak ayarlayın. `-p:BuildProjectReferences=false` , başvurulan projelerin güncel olup olmadığını kontrol etmekten kaçınmak için komut satırında belirtilebilir. |
| CleanFile | Tümü | "Temiz önbellek" olarak kullanılacak dosyanın adı. Temizleme önbelleği, temizleme işlemi sırasında silinecek oluşturulan dosyaların bir listesidir. Dosya, yapı işlemi tarafından ara çıkış yoluna konur.<br /><br /> Bu özellik yalnızca yol bilgilerine sahip olmayan dosya adlarını belirtir. |
| Sayfasının | .NET | Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfasını belirtir. Bu özellik, `/codepage` derleyici anahtarıyla eşdeğerdir. |
| CompilerResponseFile | .NET | Derleyici görevlerine geçirilebilecek, isteğe bağlı bir yanıt dosyası. |
| Yapılandırma | Tümü | Oluşturduğunuz `Debug` `Release` ve genellikle çözüm ve proje düzeylerinde yapılandırılabilen yapılandırma. |
| CscToolPath | C# | *csc.exe* yolu, C# derleyicisidir. |
| CustomBeforeMicrosoftCommonTargets | Tümü | Ortak hedefler içeri aktarmadan önce otomatik olarak içeri aktarılacak bir proje dosyasının veya hedef dosyanın adı. |
| DebugSymbols | Tümü | Sembolün derleme tarafından oluşturulup oluşturulmayacağını gösteren bir Boolean değer.<br /><br /> Komut satırında **-p:DebugSymbols = false** ayarı, program veritabanı (*. pdb*) sembol dosyalarının oluşturulmasını devre dışı bırakır. |
| DebugType | Tümü | Oluşturulmasını istediğiniz hata ayıklama bilgileri düzeyini tanımlar. Geçerli değerler şunlardır "Full," "pdbonly," "taşınabilir", "Embedded" ve "none". |
| Definesabitleri | .NET | Koşullu derleyici sabitlerini tanımlar. Sembol/değer çiftleri noktalı virgülle ayrılır ve aşağıdaki sözdizimi kullanılarak belirtilir:<br /><br /> *symbol1 = value1 ; symbol2 = value2*<br /><br /> özelliği derleyici `/define` anahtarına eşdeğerdir. |
| DefineDebug | Tümü |  DEBUG sabiti'nin tanımlanmış olup olmadığını gösteren bir boole değeri. |
| DefineTrace | Tümü | TRACE sabiti'nin tanımlanmış olup olmadığını belirten bir boole değeri. |
| DelaySign | .NET | Derlemeyi tam imzalamak yerine geciktirmek isteyip istemediklerini belirten bir boole değeri. |
| Belirlenimci | .NET | Derleyicinin aynı girişler için aynı derlemeler üretip üretmeyeceklerini belirten bir boole değeri. Bu parametre, `/deterministic` derleyicilerin anahtarına karşılık gelen bir parametredir. |
| DisableFastUpToDateCheck | Tümü | Yalnızca Visual Studio. Derleme Visual Studio yöneticisi, bir projenin güncel olması için yeniden oluşturulmuş olup olmadığını belirlemek için FastUpToDateCheck adlı bir işlem kullanır. Bu işlem, bunu belirlemek için MSBuild daha hızlıdır. DisableFastUpToDateCheck özelliğini olarak ayarlayarak Visual Studio yöneticisini atlayarak projenin güncel olup olmadığını belirlemek için MSBuild özelliğini kullanmaya `true` zorlar. |
| BelgelerDosyası | .NET | XML belge dosyası olarak oluşturulan dosyanın adı. Bu ad yalnızca dosya adını içerir ve yol bilgisi yoktur. |
| ErrorReport | .NET | Derleyici görevinin iç derleyici hatalarını nasıl bildirmesi gerektiğini belirtir. Geçerli değerler "istem", "gönderme" veya "yok" şeklindedir. Bu özellik, derleyici `/errorreport` anahtarına eşdeğerdir. |
| ExcludeDeploymentUrl | .NET | Proje dosyası aşağıdaki öğelerden birini içerirse [GenerateDeploymentManifest](../msbuild/generatedeploymentmanifest-task.md) görevi dağıtım bildirimine bir deploymentProvider etiketi ekler:<br /><br /> - UpdateUrl<br />- InstallUrl<br />- PublishUrl<br /><br /> Ancak ExcludeDeploymentUrl kullanarak yukarıdaki URL'lerden herhangi biri belirtilmiş olsa bile deploymentProvider etiketinin dağıtım bildirimine eklenmesini önleyebilirsiniz. Bunu yapmak için proje dosyanıza aşağıdaki özelliği ekleyin:<br /><br /> `<ExcludeDeploymentUrl>true</ExcludeDeploymentUrl>` <br /><br />**Not:**  ExcludeDeploymentUrl, Visual Studio IDE'de açık değildir ve yalnızca proje dosyası el ile düzenleyerek ayarlanabilir. Bu özelliğin ayarı, bu özelliğin Visual Studio; diğer bir ifadeyle deploymentProvider etiketi PublishUrl tarafından belirtilen URL'ye eklenmeye devam ediyor. |
| FileAlignment | .NET | Çıkış dosyasının bölümlerinin nereye hizalanması için bayt cinsinden belirtir. Geçerli değerler: 512, 1024, 2048, 4096, 8192. Bu özellik, derleyici `/filealignment` anahtarına eşdeğerdir. |
| FrameworkPathOverride | Visual Basic | uygulama vemscorlib.dll *konumunu* *microsoft.visualbasic.dll.* Bu parametre, `/sdkpath` derleyicinin anahtar *vbc.exe* eşdeğerdir. |
| GenerateDocumentation | .NET | Belgelerin derleme tarafından oluşturulıp oluşturulma olmadığını gösteren bir boole parametresi. ise, derleme belge bilgileri üretir ve bunu derleme.xmlyürütülebilir dosyanın veya kitaplığın adıyla birlikte bir `true` dosyanın içinde  koyar. |
| GenerateFullPaths | C# | [-fullpaths](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option) derleyici seçeneğini kullanarak çıkışta dosya adlarına ilişkin tam yollar oluşturma. |
| GenerateSerializationAssemblies | .NET | XML serileştirme derlemelerinin açık, otomatik veya *kapalıSGen.exe* tarafından oluşturulıp oluşturulamayacaklarını gösterir. Bu özellik yalnızca bu özelliği hedef alan derlemeler .NET Framework kullanılır. .NET Standard veya .NET Core derlemeleri için XML serileştirme derlemeleri oluşturmak için, *Microsoft.XmlSerializer.Generator* NuGet bakın. |
| IntermediateOutputPath | Tümü | hiçbir yol belirtilmezse, 'den `BaseIntermediateOutputPath` türetilen tam ara çıkış yolu. Örneğin, *\obj\debug \\*. |
| KeyContainerName | Tümü | Strong-name anahtar kapsayıcının adı. |
| KeyOriginatorFile | Tümü | Strong-name anahtar dosyasının adı. |
| ModuleAssemblyName | .NET | Derlenmiş modülün dahil etmek olduğu derlemenin adı. özelliği derleyici `/moduleassemblyname` anahtarına eşdeğerdir. |
| MSBuildProjectExtensionsPath | Tümü | Proje uzantılarının bulunduğu yolu belirtir. Varsayılan olarak, ile aynı değeri `BaseIntermediateOutputPath` alır. |
| NoLogo | Tümü | Derleyici logosunun kapalı olup olmadığını gösteren bir boole değeri. Bu özellik, derleyici `/nologo` anahtarına eşdeğerdir. |
| NoStdLib | .NET | Standart kitapla (mscorlib.dll) başvurmaktan kaçınıp kaçınılması gerekip gerek *mscorlib.dll.* `false` varsayılan değerdir. |
| NoVBRuntimeReference | Visual Basic | Visual Basic çalışma zamanının (Microsoft.VisualBasic.dll) projeye *başvuru* olarak dahil edilecek olup olmadığını belirten bir boole değeri. |
| NoWarn | .NET | Belirtilen uyarıları bastırıyor. Uyarı tanımlayıcısının yalnızca sayısal bölümü belirtilmelidir. Birden çok uyarı noktalı virgülle ayrılır. Bu parametre, `/nowarn` derleyicilerin anahtarına karşılık gelen bir parametredir. |
| NoWin32Manifest | .NET | Kullanıcı Hesabı Denetimi (UAC) bildirim bilgisinin uygulamanın yürütülebilir dosyasına ekli olup olmadığını belirten boole değeri. Yalnızca Vista'Visual Studio hedef alan Windows için geçerlidir. COM ve ClickOnce Registration-Free dağıtılan projelerde bu öğe yoksayılır. `False` (varsayılan değer), Kullanıcı Hesabı Denetimi (UAC) bildirim bilgisinin uygulamanın yürütülebilir dosyasına ekli olacağını belirtir. `True` UAC bildirim bilgisinin ekli olmadığını belirtir.<br /><br /> Bu özellik yalnızca Vista'yı Visual Studio projeleri için Windows geçerlidir. COM'da ClickOnce Registration-Free dağıtılan projelerde bu özellik yoksayılır.<br /><br /> NoWin32Manifest'i yalnızca uygulamanın yürütülebilir dosyasına Visual Studio eklemek istemiyorsanız eklemeniz gerekir; Bu işlem sanallaştırma olarak *bilinir.* Sanallaştırmayı kullanmak için `<ApplicationManifest>` aşağıdakiyle birlikte `<NoWin32Manifest>` ayarlayın:<br /><br /> - Visual Basic için düğümü `<ApplicationManifest>` kaldırın. (Visual Basic, bir düğüm `<NoWin32Manifest>` mevcut olduğunda `<ApplicationManifest>` yoksayılır.)<br />- C# projeleri için ve `<ApplicationManifest>` olarak `False` `<NoWin32Manifest>` `True` ayarlayın. (C# projelerinde geçersiz `<ApplicationManifest>` `<NoWin32Manifest>` kılar.)<br /> Bu özellik, `/nowin32manifest`vbc.exe'nin *derleyici anahtarına eşdeğerdir.* |
| İyileştirme | .NET | olarak ayarlanırken derleyici iyileştirmelerini sağlayan bir boole `true` değeri. Bu özellik, derleyici `/optimize` anahtarına eşdeğerdir. |
| OptionCompare | VisualBasic | Dize karşılaştırmaların nasıl yapılır olduğunu belirtir. Geçerli değerler "ikili" veya "text" değerleridir. Bu özellik, `/optioncompare`vbc.exe'nin *derleyici anahtarına eşdeğerdir.* |
| OptionExplicit | Visual Basic | olarak ayarlanırken kaynak kodda değişkenlerin açık bildirimini gerektiren bir boole `true` değeri. Bu özellik, derleyici `/optionexplicit` anahtarına eşdeğerdir. |
| OptionInfer | Visual Basic | olarak ayarlandırarak değişkenlerin tür `true` çıkarımlarını sağlayan bir boole değeri. Bu özellik, derleyici `/optioninfer` anahtarına eşdeğerdir. |
| OptionStrict | Visual Basic | olarak ayarlanan boole değeri, yapı görevinin örtülü tür dönüştürmelerini kısıtlamak için katı tür `true` semantiği zorlamalarına neden olur. Bu özellik,vbc.exe`/optionstrict` derleyicinin *anahtarına* eşdeğerdir. |
| Outdir | Tümü | Proje veya çözüm için son çıkış konumunu gösterir. Bir çözüm oluştururken, Tek bir konumda birden çok proje çıkışı toplamak için OutDir kullanılabilir. Ayrıca OutDir, başvuruları çözümlemek için kullanılan AssemblySearchPaths içinde yer almaktadır. Örneğin, *bin\Debug*. |
| Outputpath | Tümü | Proje dizinine göre çıkış dizininin yolunu belirtir; örneğin, *bin\Debug*. |
| OutputType | Tümü |  Çıktı dosyasının dosya biçimini belirtir. Bu parametre aşağıdaki değerlerden birini kullanabilir:<br /><br /> - Kitaplık. Bir kod kitaplığı oluşturur. (Varsayılan değer.)<br />- Exe. Bir konsol uygulaması oluşturur.<br />- Modül. Bir modül oluşturur.<br />- Winexe. Windows tabanlı bir program oluşturur.<br /><br /> C# ve Visual Basic, bu özellik anahtara `/target` eşdeğerdir. |
| OverwriteReadOnlyFiles | Tümü | Derlemenin salt okunur dosyaların üzerine yazarak veya bir hata tetiklemek için etkinleştirmek isteyip istemediğinizi belirten boole değeri. |
| Yol Haritası | .NET | Fiziksel yolların derleyici tarafından çıkış olarak kaynak yol adlarına nasıl eşlen olduğunu belirtir. Bu özellik, `/pathmap` derleyicilerin anahtarına eşdeğerdir. |
| PdbFile | .NET | Yaydığı *.pdb* dosyasının dosya adı. Bu özellik,csc.exe`/pdb` derleyicinin *anahtarına* eşdeğerdir. |
| Platform | Tümü | Üzerinde üzerinde çalışma yapılan işletim sistemi. Derlemelere .NET Framework "Herhangi bir CPU", "x86" ve "x64" örnekleridir. |
| ProcessorArchitecture | .NET | Derleme başvuruları çözümlenirken kullanılan işlemci mimarisi. Geçerli değerler : "msil," "x86," "amd64," veya "ia64." |
| ProduceOnlyReferenceAssembly | .NET | Derleyiciye derlenmiş kod yerine yalnızca bir başvuru derlemesi yayması talimatı olan boole değeri. ile birlikte `ProduceReferenceAssembly` kullanılamaz.  Bu özellik,vbc.exe`/refonly` ve *csc.exe* karşılık gelen  anahtardır. |
| ProduceReferenceAssembly | .NET | olarak ayarlanırken geçerli derleme için başvuru `true` derlemelerinin [üretime olanak sağlayan](/dotnet/standard/assembly/reference-assemblies) bir boole değeri. `Deterministic` , bu `true` özelliği kullanırken olması gerekir. Bu özellik,vbc.exe`/refout` ve *csc.exe* karşılık gelen  anahtardır. |
| RemoveIntegerChecks | Visual Basic | Tamsayı taşması hata denetimlerini devre dışı bırakmanın gerekip gerek olmadığını belirten bir boole değeri. `false` varsayılan değerdir. Bu özellik,vbc.exe`/removeintchecks` derleyicinin *anahtarına* eşdeğerdir. |
| RootNamespace | Tümü | Ekli bir kaynağın adını verirken kullanmak için kök ad alanı. Bu ad alanı, ekli kaynak bildirimi adının bir parçası. |
| Satellite_AlgorithmId | .NET | Uydu derlemeleri *AL.exe* için karma algoritmasının kimliği. |
| Satellite_BaseAddress | .NET | Hedef kullanılarak kültüre özgü uydu derlemeleri derlemeleri için temel `CreateSatelliteAssemblies` adres. |
| Satellite_CompanyName | .NET | Uydu derleme oluşturma sırasında *AL.exe* şirket adı. |
| Satellite_Configuration | .NET | Uydu derleme oluşturma sırasında *AL.exe* yapılandırma adı. |
| Satellite_Description | .NET | Uydu derlemesi oluşturma sırasında *AL.exe* için açıklama metni. |
| Satellite_EvidenceFile | .NET | Belirtilen dosyayı "Security.Evidence" kaynak adına sahip uydu derlemeye katıştırır. |
| Satellite_FileVersion | .NET | Uydu derlemesinde Dosya Sürümü alanı için bir dize belirtir. |
| Satellite_Flags | .NET | Uydu derlemesinde Flags alanı için bir değer belirtir. |
| Satellite_GenerateFullPaths | .NET | Derleme görevinin bir hata iletisinde bildirilen tüm dosyalar için mutlak yolları kullanmasını sağlar. |
| Satellite_LinkResource | .NET | Belirtilen kaynak dosyalarını bir uydu derlemeye bağlar. |
| Satellite_MainEntryPoint | .NET | Bir modül uydu derleme oluşturma sırasında yürütülebilir bir dosyaya dönüştür olduğunda giriş noktası olarak kullanmak için yönteminin tam adını (yani class.method) belirtir. |
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
| SkipInvalidConfigurations | Tümü | olduğunda, geçersiz platform ve yapılandırma birleşimleri üzerinde bir uyarı üretir, ancak derlemeyi başarısız olmaz; tanımsız `true` `false` olduğunda veya tanımsız olduğunda (varsayılan), bir hata üretir. |
| StartupObject | .NET | Main yöntemini veya Sub Main yordamını içeren sınıfı veya modülü belirtir. Bu özellik, derleyici `/main` anahtarına eşdeğerdir. |
| SubsystemVersion | .NET | Oluşturulan yürütülebilir dosyanın kullanabileceği alt sistemin en düşük sürümünü belirtir. Bu özellik, derleyici `/subsystemversion` anahtarına eşdeğerdir. Bu özelliğin varsayılan değeri hakkında bilgi için bkz. [/subsystemversion (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/subsystemversion) veya [/subsystemversion (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/subsystemversion-compiler-option). |
| TargetCompactFramework | .NET | Uygulamanın .NET Compact Framework uygulamayı çalıştırmak için gereken sürüm. Bunun belirterek, aksi takdirde başvuramayabilecek belirli çerçeve derlemelerine başvurasınız. |
| TargetFrameworkVersion | .NET | Uygulamanın .NET Framework uygulamayı çalıştırmak için gereken sürümü. Bunun belirterek, aksi takdirde başvuramayabilecek belirli çerçeve derlemelerine başvurasınız. |
| TreatWarningsAsErrors | .NET | varsa, tüm uyarıların hata olarak kabul edilirse neden olduğu bir boole `true` parametresi. Bu parametre, derleyici `/nowarn` anahtarına eşdeğerdir. |
| UseHostCompilerIfAvailable | .NET | varsa, derleme görevinin işlem içinde derleyici nesnesini kullanmalarına neden olan bir boole `true` parametresi. Bu parametre yalnızca Visual Studio. |
| Utf8Output | .NET | ise, `true` UTF-8 kodlamasını kullanarak derleyici çıkışını günlüğe kaydeden bir boole parametresi. Bu parametre, derleyici `/utf8Output` anahtarına eşdeğerdir. |
| VbcToolPath | Visual Basic | Geçerli sürümü geçersiz kılınmış olduğunda *vbc.exe* konum belirten *isteğevbc.exe* yol. |
| VbcVerbosity | Visual Basic | Derleyicinin çıkışının ayrıntılı Visual Basic belirtir. Geçerli değerler "Sessiz", "Normal" (varsayılan değer) veya "Ayrıntılı" değerlerdir. |
| Visualstudioversion | Tümü | Bu projenin Visual Studio olarak kabul edilen uygulamanın sürümünü belirtir. Bu özellik belirtilmezse, MSBuild makul bir varsayılan değere ayarlar.<br /><br /> Bu özellik, derleme için kullanılan hedef kümesi belirtmek için çeşitli proje türlerinde kullanılır. Bir proje için 4.0 veya daha yüksek bir değere ayarlanırsa, kullanılacak alt `ToolsVersion` araç takımı belirtmek için `VisualStudioVersion` kullanılır. Daha fazla bilgi için [bkz. Araç Kümesi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md). |
| WarningsAsErrors | .NET | Hata olarak davranan uyarıların listesini belirtir. Bu parametre, derleyici `/warnaserror` anahtarına eşdeğerdir. |
| WarningsNotAsErrors | .NET | Hata olarak kabul edilen uyarıların listesini belirtir. Bu parametre, derleyici `/warnaserror` anahtarına eşdeğerdir. |
| Win32Manifest | .NET | Son derlemeye ekli olması gereken bildirim dosyasının adı. Bu parametre, derleyici `/win32Manifest` anahtarına eşdeğerdir. |
| Win32Kaynak | .NET | Son derlemeye katıştıracak Win32 kaynağının dosya adı. Bu parametre, derleyici `/win32resource` anahtarına eşdeğerdir. |

## <a name="see-also"></a>Ayrıca bkz.

- [Yaygın MSBuild proje öğeleri](../msbuild/common-msbuild-project-items.md)
- [Yaygın MSBuild öğesi meta verileri](common-msbuild-item-metadata.md)
- [MSBuild Ayrılmış ve İyi Bilinen Özellikler](msbuild-reserved-and-well-known-properties.md)
- [MSBuild SDK projeleri için başvuru](/dotnet/core/project-sdk/msbuild-props)
