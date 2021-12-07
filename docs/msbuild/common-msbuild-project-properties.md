---
title: Ortak MSBuild Project Özellikleri | Microsoft Docs
description: Proje dosyalarında tanımlan MSBuild veya proje dosyalarında kullanılmaktadır ya da proje tarafından kullanılan .targets dosyalarına dahil olan yaygın MSBuild öğrenin.
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
ms.openlocfilehash: 92bd5e084cf12e99f57cc02074287bf776506335
ms.sourcegitcommit: 7a300823cf1bd3355be03bde561cf2777bc09eae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2021
ms.locfileid: "133977893"
---
# <a name="common-msbuild-project-properties"></a>Yaygın MSBuild proje özellikleri

Aşağıdaki tabloda, proje dosyalarında tanımlanan veya Visual Studio *.targets* dosyalarına dahil edilen sık kullanılan MSBuild listele.

 Visual Studio Project *(.csproj*, *.vbproj*, *.vcxproj* ve diğerleri) MSBuild dosyaları, IDE kullanarak bir proje derlemek için çalışan bir XML kodu içerir. Projeler genellikle derleme işlemlerini tanımlamak için bir veya daha fazla *.targets* dosyası içeri aktarıyor. Daha fazla bilgi için [bkz. MSBuild .targets dosyaları.](../msbuild/msbuild-dot-targets-files.md)

## <a name="list-of-common-properties-and-parameters"></a>Ortak özellikler ve parametrelerin listesi

| Özellik veya parametre adı | Project türleri | Description |
|------------------------------------| - | - |
| AdditionalLibPaths | .NET | Derleyicilerin başvuru derlemelerini araması gereken ek klasörleri belirtir. |
| AddModules | .NET | Derleyicinin, belirtilen dosyalardan gelen tüm tür bilgilerini derleyeni proje için kullanılabilir hale yüklemesini sağlar. Bu özellik, derleyici `/addModules` anahtarına eşdeğerdir. |
| ALToolPath | .NET | Bu *AL.exe* yolu. Bu özellik, farklı bir sürümün *AL.exe* için geçerli sürümü geçersiz kılar. |
| ApplicationIcon | .NET | Win32 simgesi olarak eklemek için derleyiciye geçecek *.ico* simge dosyası. özelliği derleyici `/win32icon` anahtarına eşdeğerdir. |
| ApplicationManifest | Tümü | Dış Kullanıcı Hesabı Denetimi (UAC) bildirim bilgilerini oluşturmak için kullanılan dosyanın yolunu belirtir. Yalnızca Vista'Visual Studio hedef alan Windows için geçerlidir.<br /><br /> Çoğu durumda bildirim ekli olur. Ancak, KayıtSız COM veya ClickOnce kullanıyorsanız, bildirim uygulama derlemeleriniz ile birlikte yüklenmiş bir dış dosya olabilir. Daha fazla bilgi için bu konudaki NoWin32Manifest özelliğine bakın. |
| AssemblyOriginatorKeyFile | .NET | Derlemeyi imzalamak için kullanılan dosyayı (*.snk* veya *.pfx*) belirtir ve derlemeyi imzalamak için kullanılan gerçek anahtarı oluşturmak için [ResolveKeySource](../msbuild/resolvekeysource-task.md) görevine geçirilen dosyayı belirtir. |
| AssemblySearchPaths | .NET | Derleme zamanı başvuru derleme çözümlemesi sırasında aranacak konumların listesi. Yolların bu listede görünme sırası anlamlıdır çünkü daha önce listelenen yollar sonraki girişlere göre önceliklidir. |
| Assemblyname | .NET | Proje yapıldıktan sonra son çıkış derlemenin adı. |
| Baseaddress | .NET | Ana çıkış derlemenin temel adresini belirtir. Bu özellik, derleyici `/baseaddress` anahtarına eşdeğerdir. |
| BaseIntermediateOutputPath | Tümü | Tüm yapılandırmaya özgü ara çıkış klasörlerinin oluşturul bulunduğu üst düzey klasör. `obj\` varsayılan değerdir. Aşağıdaki kod bir örnektir: `<BaseIntermediateOutputPath>c:\xyz\obj\</BaseIntermediateOutputPath>` |
| BaseOutputPath | Tümü | Çıkış dosyasının temel yolunu belirtir. Ayarlanırsa, MSBuild `OutputPath = $(BaseOutputPath)\$(Configuration)\` kullanır. Örnek söz dizimi: `<BaseOutputPath>c:\xyz\bin\</BaseOutputPath>` |
| BuildInParallel | Tümü | Multi-Proc MSBuild kullanılırken proje başvurularını paralel olarak mı yoksa paralel olarak mı MSBuild boole değeri. Varsayılan değer, sistemin birden çok çekirdeği veya işlemcisi varsa projelerin paralel olarak inşa `true` edilecekleri anlamına gelir. |
| BuildProjectReferences | Tümü | Proje başvurularını uygulama tarafından yapılıp yapıl olmadığını gösteren bir boole MSBuild. Projenizi `false` tümleşik geliştirme ortamında (IDE) Visual Studio otomatik olarak `true` olarak ayarlayın. `-p:BuildProjectReferences=false` , başvurulan projelerin güncel olduğunu denetlemeyi önlemek için komut satırına belirtilebilir. |
| CleanFile | Tümü | "Temiz önbellek" olarak kullanılacak dosyanın adı. Temiz önbellek, temizleme işlemi sırasında silinecek oluşturulan dosyaların listesidir. Dosya, derleme işlemi tarafından ara çıkış yoluna kondur.<br /><br /> Bu özellik yalnızca yol bilgisi olan dosya adlarını belirtir. |
| Codepage | .NET | Derlemede tüm kaynak kodu dosyaları için kullanılan kod sayfasını belirtir. Bu özellik, derleyici `/codepage` anahtarına eşdeğerdir. |
| CompilerResponseFile | .NET | Derleyici görevlerine geçirilen isteğe bağlı bir yanıt dosyası. |
| Yapılandırma | Tümü | Genellikle veya olarak, ancak çözüm `Debug` ve `Release` proje düzeylerinde yapılandırılabilir olan, ancak sizin için yapılandıran yapılandırma. |
| CscToolPath | C# | C# *derleyicisi* csc.exeyolu. |
| CustomBeforeMicrosoftCommonTargets | Tümü | Ortak hedefler içeri aktarmadan önce otomatik olarak içeri aktar edilecek bir proje dosyasının veya hedef dosyasının adı. |
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
| ExcludeDeploymentUrl | .NET | [GenerateDeploymentManifest görevi](../msbuild/generatedeploymentmanifest-task.md) , proje dosyası aşağıdaki öğelerden herhangi birini içeriyorsa dağıtım bildirimine bir deploymentProvider etiketi ekler:<br /><br /> -UpdateUrl<br />-InstallUrl<br />-PublishUrl<br /><br /> Ancak, ExcludeDeploymentUrl kullanarak, yukarıdaki URL 'Lerden herhangi biri belirtilmiş olsa bile, dağıtım bildirimine deploymentProvider etiketinin eklenmesini engelleyebilirsiniz. Bunu yapmak için, aşağıdaki özelliği proje dosyanıza ekleyin:<br /><br /> `<ExcludeDeploymentUrl>true</ExcludeDeploymentUrl>` <br /><br />**Note:**  excludedeploymenturl Visual Studio ıde 'de gösterilmez ve yalnızca proje dosyasını el ile düzenleyerek ayarlanabilir. bu özelliğin ayarlanması Visual Studio içinde yayımlamayı etkilemez; diğer bir deyişle, deploymentProvider etiketi publishurl tarafından belirtilen URL 'ye de eklenecektir. |
| Dosya hizalaması | .NET | Çıktı dosyasının bölümlerinin hizalanın bayt cinsinden sayısını belirtir. Geçerli değerler 512, 1024, 2048, 4096, 8192. Bu özellik, `/filealignment` derleyici anahtarıyla eşdeğerdir. |
| FrameworkPathOverride | Visual Basic | *mscorlib.dll* ve *microsoft.visualbasic.dll* konumunu belirtir. Bu parametre `/sdkpath` *vbc.exe* derleyicisinin anahtarıyla eşdeğerdir. |
| GenerateDocumentation | .NET | Yapı tarafından belgelerin oluşturulup oluşturulmayacağını gösteren bir Boolean parametresi. `true`Derleme, belge bilgilerini oluşturur ve yapı görevinin oluşturduğu yürütülebilir dosyanın veya kitaplığın adıyla birlikte bir *.xml* dosyasına koyar. |
| GenerateFullPaths | C# | [-Fullpaths](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option) derleyici seçeneğini kullanarak çıkışta dosya adları için tam yollar oluşturun. |
| GenerateSerializationAssemblies | .NET | XML serileştirme derlemelerinin *SGen.exe* tarafından oluşturulup oluşturulmayacağını, otomatik veya kapalı olarak ayarlanamayacağını gösterir. bu özellik yalnızca .NET Framework hedef derlemeler için kullanılır. .NET Standard veya .net Core derlemeleriyle ilgili XML serileştirme derlemeleri oluşturmak için *Microsoft. XmlSerializer. Generator* NuGet paketine başvurun. |
| IntermediateOutputPath | Tümü | Yol belirtilmemişse tam ara çıkış yolu öğesinden türetilir `BaseIntermediateOutputPath` . Örneğin, *obj\Debug \\*. |
| KeyContainerName | Tümü | Tanımlayıcı ad anahtar kapsayıcısının adı. |
| Keyorigınatorfile | Tümü | Tanımlayıcı ad anahtar dosyasının adı. |
| ModuleAssemblyName | .NET | Derlenen modülün içine dahil edilecek derlemenin adı. Özelliği, `/moduleassemblyname` derleyici anahtarıyla eşdeğerdir. |
| Msbuildprojeclarsionspath | Tümü | Proje uzantılarının bulunduğu yolu belirtir. Varsayılan olarak, bu değeri ile aynı şekilde alır `BaseIntermediateOutputPath` . |
| NoLogo | Tümü | Derleyici logosunun kapatılmasını isteyip istemediğinizi belirten bir Boole değeri. Bu özellik, `/nologo` derleyici anahtarıyla eşdeğerdir. |
| NoStdLib | .NET | Standart kitaplığa (*mscorlib.dll*) başvurulmaya engellenip engellenmeyeceğini belirten bir Boole değeri. `false` varsayılan değerdir. |
| NoVBRuntimeReference | Visual Basic | Visual Basic çalışma zamanının (*Microsoft.VisualBasic.dll*) projeye başvuru olarak dahil edilip edilmeyeceğini belirten bir boole değeri. |
| NoWarn | .NET | Belirtilen uyarıları bastırır. Uyarı tanımlayıcısının yalnızca sayısal kısmı belirtilmelidir. Birden çok uyarı noktalı virgülle ayrılır. Bu parametre, `/nowarn` derleyicilerin anahtarına karşılık gelir. |
| NoWin32Manifest | .NET | Kullanıcı hesabı denetimi (UAC) bildirim bilgisinin uygulamanın yürütülebilir dosyasına katıştırılacağını belirten bir Boole değeri. yalnızca Windows Vista 'yı hedefleyen Visual Studio projeleri için geçerlidir. COM'da ClickOnce Registration-Free dağıtılan projelerde bu öğe yoksayılır. `False` (varsayılan değer), Kullanıcı Hesabı Denetimi (UAC) bildirim bilgisinin uygulamanın yürütülebilir dosyasına ekli olacağını belirtir. `True` UAC bildirim bilgisinin ekli olmadığını belirtir.<br /><br /> Bu özellik yalnızca Vista'yı Visual Studio projeleri için Windows geçerlidir. COM'da ClickOnce ve Registration-Free dağıtılan projelerde bu özellik yoksayılır.<br /><br /> NoWin32Manifest'i yalnızca uygulamanın yürütülebilir dosyasına bildirim Visual Studio eklemek istemiyorsanız eklemeniz gerekir; bu işlem sanallaştırma olarak *bilinir.* Sanallaştırmayı kullanmak için `<ApplicationManifest>` aşağıdakiyle birlikte `<NoWin32Manifest>` ayarlayın:<br /><br /> - Visual Basic için düğümü `<ApplicationManifest>` kaldırın. (Visual Basic, bir düğüm `<NoWin32Manifest>` mevcut olduğunda `<ApplicationManifest>` yoksayılır.)<br />- C# projeleri için ve `<ApplicationManifest>` olarak `False` `<NoWin32Manifest>` `True` ayarlayın. (C# projelerinde geçersiz `<ApplicationManifest>` `<NoWin32Manifest>` kılar.)<br /> Bu özellik, `/nowin32manifest`vbc.exe'nin *derleyici anahtarına eşdeğerdir.* |
| İyileştirme | .NET | olarak ayarlanırken derleyici iyileştirmelerini sağlayan bir boole `true` değeri. Bu özellik, derleyici `/optimize` anahtarına eşdeğerdir. |
| OptionCompare | VisualBasic | Dize karşılaştırmaların nasıl yapılır olduğunu belirtir. Geçerli değerler "ikili" veya "text" değerleridir. Bu özellik, `/optioncompare`vbc.exe'nin *derleyici anahtarına eşdeğerdir.* |
| OptionExplicit | Visual Basic | olarak ayarlanırken kaynak kodda değişkenlerin açık bildirimini gerektiren bir boole `true` değeri. Bu özellik, derleyici `/optionexplicit` anahtarına eşdeğerdir. |
| OptionInfer | Visual Basic | olarak ayarlandırarak değişkenlerin tür `true` çıkarımlarını sağlayan bir boole değeri. Bu özellik, derleyici `/optioninfer` anahtarına eşdeğerdir. |
| OptionStrict | Visual Basic | olarak ayarlanan boole değeri, yapı görevinin örtülü tür dönüştürmelerini kısıtlamak için katı tür `true` semantiği zorlamalarına neden olur. Bu özellik, `/optionstrict` derleyicinin anahtar *vbc.exe* eşdeğerdir. |
| Outdir | Tümü | Proje veya çözüm için son çıkış konumunu gösterir. Bir çözüm oluştururken, OutDir tek bir konumda birden çok proje çıkışı toplamak için kullanılabilir. Ayrıca OutDir, başvuruları çözümlemek için kullanılan AssemblySearchPaths içinde yer almaktadır. Örneğin, *bin\Debug*. |
| Outputpath | Tümü | Proje dizinine göre çıkış dizininin yolunu belirtir; örneğin, *bin\Debug*. |
| OutputType | Tümü |  Çıktı dosyasının dosya biçimini belirtir. Bu parametre aşağıdaki değerlerden birini kullanabilir:<br /><br /> - Kitaplık. Bir kod kitaplığı oluşturur. (Varsayılan değer.)<br />- Exe. Bir konsol uygulaması oluşturur.<br />- Modül. Bir modül oluşturur.<br />- Winexe. Windows tabanlı bir program oluşturur.<br /><br /> C# ve Visual Basic, bu özellik anahtara `/target` eşdeğerdir. |
| OverwriteReadOnlyFiles | Tümü | Derlemenin salt okunur dosyaların üzerine yazarak veya bir hata tetiklemek için etkinleştirmek isteyip istemediğinizi belirten boole değeri. |
| Yol Haritası | .NET | Fiziksel yolların derleyici tarafından çıkış olarak kaynak yol adlarına nasıl eşlen olduğunu belirtir. Bu özellik, `/pathmap` derleyicilerin anahtarına eşdeğerdir. |
| PdbFile | .NET | Yaydığı *.pdb* dosyasının dosya adı. Bu özellik, `/pdb` derleyicinin anahtar *csc.exe* eşdeğerdir. |
| Platform | Tümü | Üzerinde üzerinde çalışma yapılan işletim sistemi. Derlemelere .NET Framework "Any CPU", "x86" ve "x64" şeklindedir. |
| ProcessorArchitecture | .NET | Derleme başvuruları çözümlenirken kullanılan işlemci mimarisi. Geçerli değerler :"msil," "x86," "amd64," veya "ia64." |
| ProduceOnlyReferenceAssembly | .NET | Derleyiciye derlenmiş kod yerine yalnızca bir başvuru derlemesi yayması talimatı olan boole değeri. ile birlikte `ProduceReferenceAssembly` kullanılamaz.  Bu özellik,vbc.exe`/refonly` ve *csc.exe* karşılık gelen  anahtardır. |
| ProduceReferenceAssembly | .NET | olarak ayarlanırken geçerli derleme için başvuru `true` derlemelerinin [üretime olanak sağlayan](/dotnet/standard/assembly/reference-assemblies) bir boole değeri. `Deterministic` , bu `true` özelliği kullanırken olması gerekir. Bu özellik,vbc.exe`/refout` ve *csc.exe* karşılık gelen  anahtardır. |
| RemoveIntegerChecks | Visual Basic | Tamsayı taşması hata denetimlerini devre dışı bırakıp devre dışı bırakmamanızı belirten bir boole değeri. `false` varsayılan değerdir. Bu özellik, `/removeintchecks` derleyicinin anahtar *vbc.exe* eşdeğerdir. |
| RootNamespace | Tümü | Ekli bir kaynağın adını verirken kullanmak için kök ad alanı. Bu ad alanı, ekli kaynak bildirimi adının bir parçası. |
| Satellite_AlgorithmId | .NET | Uydu derlemeleri *oluşturulduğundaAL.exe* karma algoritmasının kimliği. |
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
| TargetCompactFramework | .NET | Uygulamanın .NET Compact Framework uygulamayı çalıştırmak için gereken sürümü. Bunun belirterek, aksi takdirde başvuramayabilecek belirli çerçeve derlemelerine başvurasınız. |
| TargetFrameworkVersion | .NET | Uygulamanın .NET Framework uygulamayı çalıştırmak için gereken sürümü. Bunun belirterek, aksi takdirde başvuramayabilecek belirli çerçeve derlemelerine başvurasınız. |
| TreatWarningsAsErrors | .NET | varsa, tüm uyarıların hata olarak kabul edilirse neden olduğu bir boole `true` parametresi. Bu parametre, derleyici `/nowarn` anahtarına eşdeğerdir. |
| UseCommonOutputDirectory | .NET | Bir çözümde tüm derleme çıkışlarını aynı çıkış dizinini kullanmak istediğinizde ayar kullanabileceğiniz bir boole `true` özelliği. başvurulan projelerin çıktısı bu bağımlılıkları kullanan projelere kopyalanmazsa, normalde bu ayar olduğunda `true` olduğu gibi `false` olur. Bu parametre olarak ayarlamak hiçbir projenin gerçek çıkış dizinini değiştirmez; yine de çıkış dizinini, bunu gerektiren her proje için istenen ortak çıkış `true` dizinine ayarlamanız gerekir.|
| UseHostCompilerIfAvailable | .NET | varsa, derleme görevinin işlem içinde derleyici nesnesini kullanmalarına neden olan bir boole `true` parametresi. Bu parametre yalnızca Visual Studio. |
| Utf8Output | .NET | ise, `true` UTF-8 kodlamasını kullanarak derleyici çıkışını günlüğe kaydeden bir boole parametresi. Bu parametre, derleyici `/utf8Output` anahtarına eşdeğerdir. |
| VbcToolPath | Visual Basic | Geçerli *vbc.exe* sürümü geçersiz kılındığında *vbc.exe* başka bir konum belirten isteğe bağlı bir yol. |
| Vbcayrıntı düzeyi | Visual Basic | Visual Basic derleyicisinin çıkışının ayrıntı düzeyini belirtir. Geçerli değerler şunlardır "sessiz," "normal" (varsayılan değer) veya "ayrıntılıdır." |
| VisualStudioVersion | Tümü | bu projenin çalışıyor olarak değerlendirilmesi gereken Visual Studio sürümünü belirtir. bu özellik belirtilmezse, MSBuild makul bir varsayılan değere ayarlar.<br /><br /> Bu özellik, derleme için kullanılan hedef kümesini belirtmek için çeşitli proje türlerinde kullanılır. `ToolsVersion`Bir proje için 4,0 veya üzeri bir değere ayarlanırsa, `VisualStudioVersion` hangi alt araç takımını kullanacağınızı belirtmek için kullanılır. Daha fazla bilgi için bkz. [araç takımı (araçları sürümü)](../msbuild/msbuild-toolset-toolsversion.md). |
| WarningsAsErrors | .NET | Hata olarak değerlendirmek için uyarıların listesini belirtir. Bu parametre, `/warnaserror` derleyici anahtarıyla eşdeğerdir. |
| Warninggözetimi Taserrors | .NET | Hata olarak değerlendirilmediğini belirten uyarıların bir listesini belirtir. Bu parametre, `/warnaserror` derleyici anahtarıyla eşdeğerdir. |
| Win32Manifest | .NET | Son derlemeye katıştırılması gereken bildirim dosyasının adı. Bu parametre, `/win32Manifest` derleyici anahtarıyla eşdeğerdir. |
| Win32Resource | .NET | Son derlemeye katıştırılacak Win32 kaynağının dosya adı. Bu parametre, `/win32resource` derleyici anahtarıyla eşdeğerdir. |

## <a name="see-also"></a>Ayrıca bkz.

- [Yaygın MSBuild proje öğeleri](../msbuild/common-msbuild-project-items.md)
- [Yaygın MSBuild öğesi meta verileri](common-msbuild-item-metadata.md)
- [MSBuild ayrılmış ve iyi bilinen özellikler](msbuild-reserved-and-well-known-properties.md)
- [.net SDK projeleri için MSBuild başvurusu](/dotnet/core/project-sdk/msbuild-props)
