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
ms.openlocfilehash: 832d3938bee270511a23c73a2b8ee7195236c6cd
ms.sourcegitcommit: 1d44a5509772c3926f5ad13b1796485d6d8c441e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135963945"
---
# <a name="common-msbuild-project-properties"></a>Yaygın MSBuild proje özellikleri

aşağıdaki tabloda Visual Studio proje dosyalarında tanımlanan veya MSBuild tarafından sağlanan *. targets* dosyalarına eklenen sık kullanılan özellikler listelenmiştir.

 Visual Studio (*. csproj*, *. vbproj*, *. vcxproj* ve diğerleri) Project dosyaları, ıde kullanarak bir proje oluşturduğunuzda çalışan MSBuild XML kodu içerir. Projeler genellikle derleme işlemlerini tanımlamak için bir veya daha fazla *. targets* dosyasını içeri aktarır. daha fazla bilgi için bkz [. MSBuild. targets dosyaları](../msbuild/msbuild-dot-targets-files.md).

## <a name="list-of-common-properties-and-parameters"></a>Ortak özellikler ve parametrelerin listesi

| Özellik veya parametre adı | Project türleri | Description |
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
| DisableFastUpToDateCheck | Tümü | Yalnızca Visual Studio için geçerli olan bir boole değeri. Derleme Visual Studio yöneticisi, bir projenin güncel olması için yeniden oluşturulmuş olup olmadığını belirlemek için FastUpToDateCheck adlı bir işlem kullanır. Bu işlem, bunu belirlemek için MSBuild daha hızlıdır. DisableFastUpToDateCheck özelliğini olarak ayarlayarak Visual Studio yöneticisini atlayarak projenin güncel olup olmadığını belirlemek için MSBuild özelliğini kullanmaya `true` zorlar. |
| BelgelerDosyası | .NET | XML belge dosyası olarak oluşturulan dosyanın adı. Bu ad yalnızca dosya adını içerir ve yol bilgisi yoktur. |
| ErrorReport | .NET | Derleyici görevinin iç derleyici hatalarını nasıl bildirmesi gerektiğini belirtir. Geçerli değerler "istem", "gönderme" veya "yok" şeklindedir. Bu özellik, derleyici `/errorreport` anahtarına eşdeğerdir. |
| ExcludeDeploymentUrl | .NET | Proje dosyası aşağıdaki öğelerden birini içerirse [GenerateDeploymentManifest](../msbuild/generatedeploymentmanifest-task.md) görevi dağıtım bildirimine bir deploymentProvider etiketi ekler:<br /><br /> - UpdateUrl<br />- InstallUrl<br />- PublishUrl<br /><br /> Ancak ExcludeDeploymentUrl kullanarak yukarıdaki URL'lerden herhangi biri belirtilmiş olsa bile deploymentProvider etiketinin dağıtım bildirimine eklenmesini önleyebilirsiniz. Bunu yapmak için proje dosyanıza aşağıdaki özelliği ekleyin:<br /><br /> `<ExcludeDeploymentUrl>true</ExcludeDeploymentUrl>` <br /><br />**Not:**  ExcludeDeploymentUrl, Visual Studio IDE'de açık değildir ve yalnızca proje dosyası el ile düzenleyerek ayarlanabilir. Bu özelliğin ayarı, Visual Studio içinde yayımlamayı etkilemez; diğer bir ifadeyle deploymentProvider etiketi PublishUrl tarafından belirtilen URL'ye eklenmeye devam ediyor. |
| FileAlignment | .NET | Çıkış dosyasının bölümlerinin nereye hizalanması için bayt cinsinden belirtir. Geçerli değerler: 512, 1024, 2048, 4096, 8192. Bu özellik, derleyici `/filealignment` anahtarına eşdeğerdir. |
| FrameworkPathOverride | Visual Basic | uygulama vemscorlib.dll *konumunu* *microsoft.visualbasic.dll.* Bu parametre, `/sdkpath` derleyicinin anahtar *vbc.exe* eşdeğerdir. |
| GenerateDocumentation | .NET | Belgelerin derleme tarafından oluşturulıp oluşturulmay olmadığını gösteren bir boole parametresi. ise, derleme belge bilgileri üretir ve bunu derleme.xmlyürütülebilir dosyanın veya kitaplığın adıyla birlikte bir `true` dosyanın içinde  koyar. |
| GenerateFullPaths | C# | [-fullpaths](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option) derleyici seçeneğini kullanarak çıkışta dosya adlarına ilişkin tam yollar oluşturma. |
| GenerateSerializationAssemblies | .NET | XML serileştirme derlemelerinin açık, otomatik veya *kapalıSGen.exe* tarafından oluşturulıp oluşturulamayacaklarını gösterir. Bu özellik yalnızca bu özelliği hedef alan derlemeler .NET Framework kullanılır. .NET Standard veya .NET Core derlemeleri için XML serileştirme derlemeleri oluşturmak için *Microsoft.XmlSerializer.Generator* NuGet bakın. |
| IntermediateOutputPath | Tümü | hiçbir yol belirtilmezse, 'den `BaseIntermediateOutputPath` türetilen tam ara çıkış yolu. Örneğin, *obj\debug \\*. |
| KeyContainerName | Tümü | Strong-name anahtar kapsayıcının adı. |
| KeyOriginatorFile | Tümü | Strong-name anahtar dosyasının adı. |
| ModuleAssemblyName | .NET | Derlenmiş modülün dahil etmek olduğu derlemenin adı. özelliği derleyici `/moduleassemblyname` anahtarına eşdeğerdir. |
| MSBuildProjectExtensionsPath | Tümü | Proje uzantılarının bulunduğu yolu belirtir. Varsayılan olarak, ile aynı değeri `BaseIntermediateOutputPath` alır. |
| NoLogo | Tümü | Derleyici logosunun kapalı olup olmadığını gösteren bir boole değeri. Bu özellik, derleyici `/nologo` anahtarına eşdeğerdir. |
| NoStdLib | .NET | Standart kitapla (mscorlib.dll) başvurmaktan kaçınıp kaçınılması gerekip gerek *mscorlib.dll.* `false` varsayılan değerdir. |
| NoVBRuntimeReference | Visual Basic | Visual Basic çalışma zamanının (Microsoft.VisualBasic.dll) projeye *başvuru* olarak dahil edilecek olup olmadığını belirten bir boole değeri. |
| NoWarn | .NET | Belirtilen uyarıları bastırıyor. Uyarı tanımlayıcısının yalnızca sayısal bölümü belirtilmelidir. Birden çok uyarı noktalı virgülle ayrılır. Bu parametre, `/nowarn` derleyicilerin anahtarına karşılık gelen bir parametredir. |
| NoWin32Manifest | .NET | Kullanıcı Hesabı Denetimi (UAC) bildirim bilgisinin uygulamanın yürütülebilir dosyasına ekli olup olmadığını belirten boole değeri. Yalnızca Vista'yı Visual Studio projeleri için Windows geçerlidir. ClickOnce ve COM Registration-Free kullanılarak dağıtılan projelerde, bu öğe yok sayılır. `False` (varsayılan değer) Kullanıcı hesabı denetimi (UAC) bildirim bilgisinin uygulamanın yürütülebilir dosyasına katıştırılacağını belirtir. `True` UAC bildirim bilgilerinin gömülmeyeceğini belirtir.<br /><br /> bu özellik yalnızca Windows Vista 'yı hedefleyen Visual Studio projeler için geçerlidir. ClickOnce ve COM Registration-Free kullanılarak dağıtılan projelerde, bu özellik yok sayılır.<br /><br /> Visual Studio yalnızca uygulamanın yürütülebilir dosyasına herhangi bir bildirim bilgisi *katıştırmasını* istemiyorsanız NoWin32Manifest eklemeniz gerekir; bu işleme sanallaştırma olarak adlandırılır. Sanallaştırmayı kullanmak için `<ApplicationManifest>` ile birlikte `<NoWin32Manifest>` aşağıdaki şekilde ayarlayın:<br /><br /> -Visual Basic projeleri için `<ApplicationManifest>` düğümünü kaldırın. (Visual Basic projelerinde, `<NoWin32Manifest>` bir `<ApplicationManifest>` düğüm varken yoksayılır.)<br />-C# projeleri için, `<ApplicationManifest>` `False` ve olarak ayarlayın `<NoWin32Manifest>` `True` . (C# projelerinde, `<ApplicationManifest>` geçersiz kılmalar `<NoWin32Manifest>` .)<br /> Bu özellik `/nowin32manifest` *vbc.exe* derleyici anahtarıyla eşdeğerdir. |
| İyileştirme | .NET | Olarak ayarlandığında `true` derleyici iyileştirmelerini sağlayan bir Boole değeri. Bu özellik, `/optimize` derleyici anahtarıyla eşdeğerdir. |
| OptionCompare | VisualBasic | Dize karşılaştırmalarının nasıl yapılacağını belirtir. Geçerli değerler şunlardır "binary" veya "Text." Bu özellik `/optioncompare` *vbc.exe* derleyici anahtarıyla eşdeğerdir. |
| OptionExplicit | Visual Basic | Olarak ayarlandığında `true` , kaynak koddaki değişkenlerin açık bildirimini gerektiren Boolean bir değer. Bu özellik, `/optionexplicit` derleyici anahtarıyla eşdeğerdir. |
| OptionInfer | Visual Basic | Olarak ayarlandığında `true` değişkenlerin tür çıkarımını sağlayan bir Boole değeri. Bu özellik, `/optioninfer` derleyici anahtarıyla eşdeğerdir. |
| OptionStrict | Visual Basic | Olarak ayarlandığında `true` , derleme görevinin örtük tür semantiğini zorlamak için katı tür semantiğini zorlamasına neden olan bir Boole değeri. Bu özellik `/optionstrict` *vbc.exe* derleyicisinin anahtarıyla eşdeğerdir. |
| OutDir | Tümü | Proje veya çözüm için son çıkış konumunu gösterir. Bir çözüm oluştururken, OutDir birden fazla proje çıkışını tek bir konumda toplamak için kullanılabilir. Ayrıca, OutDir başvuruları çözümlemek için kullanılan AssemblySearchPaths 'a dahildir. Örneğin, *bin\Debug*. |
| OutputPath | Tümü | Proje dizinine göre çıkış dizininin yolunu belirtir, örneğin, *bin\Debug*. |
| #B2 | Tümü |  Çıktı dosyasının dosya biçimini belirtir. Bu parametre aşağıdaki değerlerden birine sahip olabilir:<br /><br /> Kitaplığı. Bir kod kitaplığı oluşturur. (Varsayılan değer.)<br />Exe. Bir konsol uygulaması oluşturur.<br />Birimi. Bir modül oluşturur.<br />Winexe. Windows tabanlı bir program oluşturur.<br /><br /> C# ve Visual Basic için bu özellik anahtar ile eşdeğerdir `/target` . Çıkış türü, ınınnby tarafından otomatik olarak geçersiz kılınamıyor. Bkz. [OUTPUTTYPE WPF ve WinForms uygulamaları Için winexe olarak ayarlanır](/dotnet/core/compatibility/sdk/5.0/automatically-infer-winexe-output-type). Ayarını olarak ayarlayarak devre dışı `DisableWinExeOutputInference` bırakın `true` . |
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
| SGenUseProxyTypes | .NET | Proxy türlerinin *SGen.exe* tarafından oluşturulup oluşturulmayacağını gösteren Boolean bir değer. Bu yalnızca *GenerateSerializationAssemblies* on olarak ayarlandığında geçerlidir.<br /><br /> SGen hedefi, UseProxyTypes bayrağını ayarlamak için bu özelliği kullanır. Bu özellik varsayılan olarak true değerini alır ve bunu değiştirmek için bir kullanıcı arabirimi yoktur. Web hizmeti olmayan türler için serileştirme derlemesini oluşturmak için, bu özelliği proje dosyasına ekleyin ve *Microsoft. Common. targets* veya *C#/vb.exe*' i içeri aktarmadan önce false olarak ayarlayın. |
| Skipınvalidconfigurations | Tümü | Ne zaman `true` , geçersiz platform ve yapılandırma birleşimleri üzerinde bir uyarı oluştur, ancak derlemeyi başarısız yap; ne zaman `false` veya tanımsız (varsayılan), bir hata oluşturur. |
| StartupObject | .NET | Ana yöntemi veya alt ana yordamı içeren sınıfı veya modülü belirtir. Bu özellik, `/main` derleyici anahtarıyla eşdeğerdir. |
| SubsystemVersion | .NET | Oluşturulan yürütülebilir dosyanın kullanabileceği alt sistemin en düşük sürümünü belirtir. Bu özellik, `/subsystemversion` derleyici anahtarıyla eşdeğerdir. bu özelliğin varsayılan değeri hakkında daha fazla bilgi için bkz. [/subsystemversion (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/subsystemversion) veya [/subsystemversion (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/subsystemversion-compiler-option). |
| TargetCompactFramework | .NET | Oluşturmakta olduğunuz uygulamayı çalıştırmak için gereken .NET Compact Framework sürümü. Bunu belirtmek, başka türlü başvuramayacak bazı Framework derlemelerine başvurmanıza olanak sağlar. |
| TargetFrameworkVersion | .NET | oluşturmakta olduğunuz uygulamayı çalıştırmak için gereken .NET Framework sürümü. Bunu belirtmek, başka türlü başvuramayacak bazı Framework derlemelerine başvurmanıza olanak sağlar. |
| TreatWarningsAsErrors | .NET | `true`Tüm uyarıların hata olarak işlenmesine neden olan bir Boole parametresi. Bu parametre, `/nowarn` derleyici anahtarıyla eşdeğerdir. |
| UseCommonOutputDirectory | .NET | `true`Bir Çözümdeki tüm derleme çıktılarının aynı çıkış dizinini kullanmasını istediğiniz zaman, olarak ayarlayabileceğiniz Boole özelliği. `true`Başvurulan projelerin çıktısı, bu bağımlılıkları kullanan projelere kopyalanmamışsa, genellikle bu ayar olduğu gibi olur `false` . Bu parametreyi öğesine ayarlamak `true` herhangi bir projenin gerçek çıkış dizinini değiştirmez; yine de gereken her proje için çıktı dizinini istenen ortak çıkış dizinine ayarlamanız gerekir.|
| UseHostCompilerIfAvailable | .NET | Varsa, derleme görevinin, varsa `true` işlem içi derleyici nesnesini kullanmasına neden olan bir Boole parametresi. Bu parametre yalnızca Visual Studio tarafından kullanılır. |
| Utf8Output | .NET | `true`, Derleyici ÇıKıŞıNı UTF-8 kodlaması kullanarak günlüğe kaydeden bir Boolean parametresi. Bu parametre, `/utf8Output` derleyici anahtarıyla eşdeğerdir. |
| VbcToolPath | Visual Basic | Geçerli *vbc.exe* sürümü geçersiz kılındığında *vbc.exe* başka bir konum belirten isteğe bağlı bir yol. |
| Vbcayrıntı düzeyi | Visual Basic | Visual Basic derleyicisinin çıkışının ayrıntı düzeyini belirtir. Geçerli değerler şunlardır "sessiz," "normal" (varsayılan değer) veya "ayrıntılıdır." |
| VisualStudioVersion | Tümü | bu projenin çalışıyor olarak değerlendirilmesi gereken Visual Studio sürümünü belirtir. bu özellik belirtilmezse, MSBuild makul bir varsayılan değere ayarlar.<br /><br /> Bu özellik, derleme için kullanılan hedef kümesini belirtmek için çeşitli proje türlerinde kullanılır. `ToolsVersion`Bir proje için 4,0 veya üzeri bir değere ayarlanırsa, `VisualStudioVersion` hangi alt araç takımını kullanacağınızı belirtmek için kullanılır. Daha fazla bilgi için bkz. [araç takımı (araçları sürümü)](../msbuild/msbuild-toolset-toolsversion.md). |
| WarningsAsErrors | .NET | Hata olarak değerlendirmek için uyarıların listesini belirtir. Bu parametre, `/warnaserror` derleyici anahtarıyla eşdeğerdir. |
| Warninggözetimi Taserrors | .NET | Hata olarak değerlendirilmediğini belirten uyarıların bir listesini belirtir. Bu parametre, `/warnaserror` derleyici anahtarıyla eşdeğerdir. |
| Win32Manifest | .NET | Son derlemeye katıştırılması gereken bildirim dosyasının adı. Bu parametre, `/win32Manifest` derleyici anahtarıyla eşdeğerdir. |
| Win32Resource | .NET | Son derlemeye katıştırılacak Win32 kaynağının dosya adı. Bu parametre, `/win32resource` derleyici anahtarıyla eşdeğerdir. |

.NET SDK projelerine özgü özellikler, örneğin `TargetFramework` , [Framework özelliklerinde](/dotnet/core/project-sdk/msbuild-props#framework-properties)belgelenmiştir.

## <a name="see-also"></a>Ayrıca bkz.

- [Yaygın MSBuild proje öğeleri](../msbuild/common-msbuild-project-items.md)
- [Yaygın MSBuild öğesi meta verileri](common-msbuild-item-metadata.md)
- [MSBuild ayrılmış ve iyi bilinen özellikler](msbuild-reserved-and-well-known-properties.md)
- [.net SDK projeleri için MSBuild başvurusu](/dotnet/core/project-sdk/msbuild-props)
