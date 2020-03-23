---
title: Ortak MSBuild Proje Özellikleri | Microsoft Dokümanlar
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
ms.openlocfilehash: ece57a102851efe0198f8993b60dba8e0eae6dec
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634428"
---
# <a name="common-msbuild-project-properties"></a>Ortak MSBuild proje özellikleri

Aşağıdaki tablo, Visual Studio proje dosyalarında tanımlanan veya MSBuild'in sağladığı *.targets* dosyalarına dahil edilen sık kullanılan özellikleri listeler.

 Visual Studio'daki proje dosyaları (*.csproj*, *.vbproj*, *.vcxproj*, ve diğerleri) IDE kullanarak bir proje oluşturduğunuzda çalışan MSBuild XML kodu içerir. Projeler genellikle yapı işlemini tanımlamak için bir veya daha fazla *.hedef* dosyasını içe aktarın. Daha fazla bilgi için [MSBuild .targets dosyalarına](../msbuild/msbuild-dot-targets-files.md)bakın.

## <a name="list-of-common-properties-and-parameters"></a>Ortak özellikler ve parametreler listesi

| Özellik veya parametre adı | Açıklama |
|------------------------------------| - |
| Ek Libpaths | Derleyicilerin başvuru derlemelerini araması gereken ek klasörleri belirtir. |
| Katma Modüller | Derleyicinin, derlediğiniz projeiçin belirtilen dosyalardaki tüm tür bilgilerini kullanılabilir hale getirmelerine neden olur. Bu özellik derleyici `/addModules` anahtarına eşdeğerdir. |
| ALToolPath | *AL.exe'nin* bulunduğu yol. Bu özellik, farklı bir sürümün kullanımını etkinleştirmek için *AL.exe'nin* geçerli sürümünü geçersiz kılar. |
| Uygulamaİk İkonisi | *.ico* simgesi dosyası, Win32 simgesi olarak katıştırmak üzere derleyiciye geçer. Özellik derleyici anahtarına `/win32icon` eşdeğerdir. |
| Başvuru Bildirimi | Dış Kullanıcı Hesabı Denetimi (UAC) bildirim bilgileri oluşturmak için kullanılan dosyanın yolunu belirtir. Yalnızca Windows Vista'yı hedefleyen Visual Studio projeleri için geçerlidir.<br /><br /> Çoğu durumda, bildirim katıştırılmış. Ancak, Kayıt Ücretsiz COM veya ClickOnce dağıtım kullanırsanız, o zaman bildirim uygulama derlemeleri ile birlikte yüklenmiş harici bir dosya olabilir. Daha fazla bilgi için bu konuda NoWin32Manifest özelliğine bakın. |
| AssemblyOriginatorKeyFile | Derlemeyi imzalamak için kullanılan dosyayı *(.snk* veya *.pfx)* belirtir ve derlemeyi imzalamak için kullanılan gerçek anahtarı oluşturmak için [ResolveKeySource görevine](../msbuild/resolvekeysource-task.md) geçirilir. |
| AssemblySearchPaths | Yapı zamanı başvuru derleme çözümü sırasında aranacak yerlerin listesi. Daha önce listelenen yollar sonraki girişlerden önce geldiği için, bu listede yolların görünme sırası anlamlıdır. |
| Assemblyname | Proje yapıldıktan sonra son çıktı derlemesinin adı. |
| Baseaddress | Ana çıktı derlemesinin temel adresini belirtir. Bu özellik derleyici `/baseaddress` anahtarına eşdeğerdir. |
| BaseIntermediateOutputPath | Yapılandırmaya özgü tüm ara çıktı klasörlerinin oluşturulduğu üst düzey klasör. Varsayılan değer: `obj\`. Aşağıdaki kod bir örnektir:`<BaseIntermediateOutputPath>c:\xyz\obj\</BaseIntermediateOutputPath>` |
| BaseOutputPath | Çıktı dosyasının temel yolunu belirtir. Ayarlanırsa, MSBuild kullanır. `OutputPath = $(BaseOutputPath)\$(Configuration)\` Örnek sözdizimi:`<BaseOutputPath>c:\xyz\bin\</BaseOutputPath>` |
| YapıParalel | Multi-Proc MSBuild kullanıldığında proje başvurularının paralel olarak oluşturulup oluşturulmadığını veya temizlenip temizlenmediğini gösteren bir boolean değeri. Varsayılan `true`değer, sistemin birden çok çekirdek veya işlemcisi varsa projelerin paralel olarak oluşturulacağı anlamına gelir. |
| YapıProje Referansları | Proje başvurularının MSBuild tarafından oluşturulup oluşturulmadığını gösteren bir boolean değeri. Aksi `true` takdirde `false` projenizi Visual Studio entegre geliştirme ortamında (IDE) oluşturuyorsanız otomatik olarak ayarlayın. `-p:BuildProjectReferences=false`başvurulan projelerin güncel olup olmadığını kontrol etmekten kaçınmak için komut satırında belirtilebilir. |
| CleanFile | "Temiz önbellek" olarak kullanılacak dosyanın adı. Temiz önbellek, temizleme işlemi sırasında silinecek oluşturulan dosyaların listesidir. Dosya, yapı işlemi tarafından ara çıktı yoluna konur.<br /><br /> Bu özellik, yalnızca yol bilgisi olmayan dosya adlarını belirtir. |
| Codepage | Derlemedeki tüm kaynak kod dosyaları için kullanılacak kod sayfasını belirtir. Bu özellik derleyici `/codepage` anahtarına eşdeğerdir. |
| DerleyiciYanıtDosyası | Derleyici görevlerine geçirilebilen isteğe bağlı yanıt dosyası. |
| Yapılandırma | "Hata Ayıklama" veya "Sürüm" olarak inşa ettiğiniz yapılandırma. |
| CscToolPath | *csc.exe*yolu , C# derleyicisi. |
| CustomBeforeMicrosoftCommonTargets | Ortak hedefler içe aktarmadan önce otomatik olarak aktalanacak proje dosyası veya hedef dosyasının adı. |
| Hata Ayıklama Sembolleri | Sembollerin yapı tarafından oluşturulup oluşturulmadığını gösteren bir boolean değeri.<br /><br /> Ayar **-p:Hata Ayıklama=komut** satırında yanlış program veritabanı (*.pdb*) sembol dosyaları nın oluşturma devre dışı. |
| Hata Ayıklama Türü | Oluşturulmasını istediğiniz hata ayıklama bilgi düzeyini tanımlar. Geçerli değerler "tam", "pdbonly", "taşınabilir", "gömülü" ve "hiçbiri" dir. |
| DefineConstants | Koşullu derleyici sabitlerini tanımlar. Sembol/değer çiftleri yarı kolonlarla ayrılır ve aşağıdaki sözdizimi kullanılarak belirtilir:<br /><br /> *symbol1 = değer1 ; symbol2 = değer2*<br /><br /> Özellik derleyici anahtarına `/define` eşdeğerdir. |
| DefineDebug | Hata Ayıklama sabitinin tanımlı olmasını isteyip istemediğinizi belirten bir boolean değeri. |
| DefineTrace | TRACE sabitinin tanımlanmasını isteyip istemediğinizi belirten bir boolean değeri. |
| DelaySign | Derlemeyi tam imzalamak yerine geciktirmek isteyip istemediğinizi belirten bir boolean değeri. |
| Belirlenimci | Derleyicinin aynı girişler için aynı derlemeleri üretip üretmemesi gerektiğini gösteren bir boolean değeri. Bu parametre `/deterministic` *vbc.exe* ve *csc.exe* derleyicilerinin anahtarına karşılık gelir. |
| Engelli Uyarılar | Belirtilen uyarıları bastırır. Uyarı tanımlayıcısının yalnızca sayısal bölümü belirtilmelidir. Birden çok uyarı yarım kolon ile ayrılır. Bu parametre `/nowarn` *vbc.exe* derleyicisinin anahtarına karşılık gelir. |
| Devre Dışı AtılabilirFastUpToDateCheck | Yalnızca Visual Studio için geçerli olan bir boolean değeri. Visual Studio yapı yöneticisi, bir projenin güncel olması için yeniden oluşturulması gerekip gerekmediğini belirlemek için FastUpToDateCheck adlı bir işlem kullanır. Bu işlem, bunu belirlemek için MSBuild'i kullanmaktan daha hızlıdır. Visual Studio yapı yöneticisini atlatır `true` ve projenin güncel olup olmadığını belirlemek için MSBuild'i kullanmaya zorlamanızı sağlamak için DisableFastUpToDateCheck özelliğini ayarlamak. |
| DokümantasyonDosyası | XML belge dosyası olarak oluşturulan dosyanın adı. Bu ad yalnızca dosya adını içerir ve yol bilgisi yoktur. |
| Hata Raporu | Derleyici görevinin iç derleyici hatalarını nasıl bildirmesi gerektiğini belirtir. Geçerli değerler "istemi", "gönderme" veya "hiçbiri" olarak adlandırılır. Bu özellik derleyici `/errorreport` anahtarına eşdeğerdir. |
| DeploymentUrl hariç | Project dosyası aşağıdaki öğelerden herhangi birini içeriyorsa, [DeploymentManifest'in oluşturma görevi](../msbuild/generatedeploymentmanifest-task.md) dağıtım bildirimine dağıtım Sağlayıcısı etiketi ekler:<br /><br /> - Güncelleme Url<br />- InstallUrl<br />- YayınUrl<br /><br /> Ancak, Dışlanan Url'yi kullanarak, yukarıdaki URL'lerden herhangi biri belirtilmiş olsa bile dağıtım Sağlayıcısı etiketinin dağıtım bildirimine eklenmesini engelleyebilirsiniz. Bunu yapmak için proje dosyanıza aşağıdaki özelliği ekleyin:<br /><br /> `<ExcludeDeploymentUrl>true</ExcludeDeploymentUrl>` <br /><br />**Not:**  ExcludeDeploymentUrl Visual Studio IDE'de açıklanmaz ve yalnızca proje dosyasını el ile düzenleyerek ayarlanabilir. Bu özelliğin ayarlanması Visual Studio içinde yayımlamayı etkilemez; diğer bir de dağıtımSağlayıcı etiketi PublishUrl tarafından belirtilen URL'ye eklenir. |
| Dosya Hizalama | Çıktı dosyasının bölümlerini hizalamanın baytlar halinde olduğunu belirtir. Geçerli değerler 512, 1024, 2048, 4096, 8192'dir. Bu özellik derleyici `/filealignment` anahtarına eşdeğerdir. |
| FrameworkPathOverride | *mscorlib.dll* ve *microsoft.visualbasic.dll'nin*yerini belirtir. Bu parametre `/sdkpath` *vbc.exe* derleyicisinin anahtarına eşdeğerdir. |
| Dokümantasyon Oluşturma | (C#, Visual Basic) Belgelemenin yapı tarafından oluşturulup oluşturulmadığını gösteren bir boolean parametresi. `true`Yapı, belge bilgilerini oluşturur ve yapı görevinin oluşturduğu yürütülebilir dosya veya kitaplığın adı ile birlikte bir *.xml* dosyasına koyar. |
| FullPaths oluşturma | (C#) [-fullpaths](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option) derleyici seçeneğini kullanarak çıktıdaki dosya adları için tam yollar oluşturun. |
| OluşturmaSerializationAssemblies | XML serileştirme derlemelerinin, üzerinde, otomatik veya kapalı olarak ayarlanabilen *SGen.exe*tarafından oluşturulup oluşturulmayacağını gösterir. Bu özellik yalnızca .NET Framework'ü hedefleyen derlemeler için kullanılır. .NET Standard veya .NET Core derlemeleri için XML serileştirme derlemeleri oluşturmak için *Microsoft.XmlSerializer.Generator* NuGet paketine başvurun. |
| IntermediateOutputPath | Türetilen tam ara çıkış `BaseIntermediateOutputPath`yolu , eğer yol belirtilmemişse. Örneğin, *\obj\debug\\*. |
| KeyContainerName | Güçlü ad anahtar kapsayıcısının adı. |
| KeyOriginatorFile | Güçlü ad anahtarı dosyasının adı. |
| ModülMontaj Adı | Derlenen modülün dahil ediletilecek derlemenin adı. Özellik derleyici anahtarına `/moduleassemblyname` eşdeğerdir. |
| MSBuildProjectExtensionsPath | Proje uzantılarının bulunduğu yolu belirtir. Varsayılan olarak, bu `BaseIntermediateOutputPath`aynı değeri alır. |
| NoLogo | Derleyici logosunun kapatılıp kapatılmak istemediğinibelirten bir boolean değeri. Bu özellik derleyici `/nologo` anahtarına eşdeğerdir. |
| NoStdLib | Standart kitaplık *(mscorlib.dll)* başvurmaktan kaçınıp kaçınmayacağını gösteren bir boolean değeri. Varsayılan değer: `false`. |
| NoVBRuntimeBaşvuru | Visual Basic çalışma zamanının *(Microsoft.VisualBasic.dll)* projeye başvuru olarak dahil edilip edilmemesi gerektiğini belirten bir boolean değeri. |
| NoWin32Manifesto | Kullanıcı Hesabı Denetimi 'nin (UAC) bildirim bilgilerinin uygulamanın yürütülebilir insine katıştırılıp yerleştirilmeyeceğini gösteren bir boolean değeri. Yalnızca Windows Vista'yı hedefleyen Visual Studio projeleri için geçerlidir. ClickOnce ve Registration-Free COM kullanılarak dağıtılan projelerde bu öğe yoksayılır. `False`(varsayılan değer) Kullanıcı Hesabı Denetimi (UAC) bildirim bilgilerinin uygulamanın yürütülebilir olacağını belirtir. `True`UAC bildirim bilgilerinin katışmaması gerektiğini belirtir.<br /><br /> Bu özellik yalnızca Windows Vista'yı hedefleyen Visual Studio projeleri için geçerlidir. ClickOnce ve Registration-Free COM kullanılarak dağıtılan projelerde, bu özellik yoksayılır.<br /><br /> Yalnızca Visual Studio'nun uygulamanın yürütülebilir insine herhangi bir bildirim bilgisi gömmesini istemiyorsanız NoWin32Manifest eklemeniz gerekir; bu işleme *sanallaştırma*denir. Sanallaştırmayı kullanmak `<ApplicationManifest>` için aşağıdaki `<NoWin32Manifest>` gibi birlikte ayarlanır:<br /><br /> - Visual Basic projeleri `<ApplicationManifest>` için düğümü çıkarın. (Visual Basic projelerinde, `<NoWin32Manifest>` bir `<ApplicationManifest>` düğüm olduğunda yoksayılır.)<br />- C# projeleri `<ApplicationManifest>` `False` için, `<NoWin32Manifest>` `True`ayarlanır ve . (C# projelerinde, `<ApplicationManifest>` `<NoWin32Manifest>`geçersiz kılar .)<br /> Bu özellik `/nowin32manifest` *vbc.exe*derleyici anahtarına eşdeğerdir. |
| İyileştirme | Bir boolean değeri, `true`derleyici optimizasyonları sağlar, ayarlanır. Bu özellik derleyici `/optimize` anahtarına eşdeğerdir. |
| SeçenekKarşılaştır | Dize karşılaştırmalarının nasıl yapıldığını belirtir. Geçerli değerler "ikili" veya "metin" dir. Bu özellik `/optioncompare` *vbc.exe*derleyici anahtarına eşdeğerdir. |
| SeçenekAçık | `true`Ayarlandığında, kaynak kodundaki değişkenlerin açık bir şekilde bildirgesini gerektiren bir boolean değeri. Bu özellik derleyici `/optionexplicit` anahtarına eşdeğerdir. |
| OptionInfer | Bir boolean değeri, `true`değişkenlerin tür çıkarım sağlayan ayarlanır. Bu özellik derleyici `/optioninfer` anahtarına eşdeğerdir. |
| OptionStrict | Bir boolean değeri, `true`ne zaman ayarlandığında, örtük tür dönüşümleri kısıtlamak için sıkı tür semantik zorlamak için yapı görevi neden olur. Bu özellik `/optionstrict` *vbc.exe* derleyicisinin anahtarına eşdeğerdir. |
| Outdir | Proje veya çözüm için son çıktı konumunu gösterir. Bir çözüm alırken, OutDir birden çok proje çıktısını tek bir konumda toplamak için kullanılabilir. Buna ek olarak, OutDir başvuruları çözmek için kullanılan AssemblySearchPaths dahildir. Örneğin, *bin\Debug*. |
| Outputpath | Örneğin, proje dizinine göre çıktı dizinine giden yolu *belirtir.* |
| Çıktı Türü | Çıktı dosyasının dosya biçimini belirtir. Bu parametre aşağıdaki değerlerden birine sahip olabilir:<br /><br /> - Kütüphane. Bir kod kitaplığı oluşturur. (Varsayılan değer.)<br />- Exe. Bir konsol uygulaması oluşturur.<br />- Modül. Bir modül oluşturur.<br />- Winexe. Windows tabanlı bir program oluşturur.<br /><br /> Bu özellik `/target` *vbc.exe* derleyicisinin anahtarına eşdeğerdir. |
| OverwriteReadOnlyFiles | Yapının salt okunur dosyalarının üzerine yazılmasını veya bir hatayı tetiklemesini etkinleştirmek isteyip istemediğinizi belirten bir boolean değeri. |
| Yol Haritası | Derleyici tarafından kaynak yol adları çıktısı için fiziksel yolların nasıl eşlenecek olduğunu belirtir. Bu özellik `/pathmap` *csc.exe* derleyicisinin anahtarına eşdeğerdir. |
| PdbDosya | Yaydığınız *.pdb* dosyasının dosya adı. Bu özellik `/pdb` *csc.exe* derleyicisinin anahtarına eşdeğerdir. |
| Platform | İnşa ettiğiniz işletim sistemi. Geçerli değerler "Herhangi bir CPU", "x86" ve "x64" dir. |
| ProcessorArchitecture | Derleme başvuruları çözüldüğünde kullanılan işlemci mimarisi. Geçerli değerler "msil", "x86", "amd64" veya "ia64" dir. |
| ProduceOnlyReferenceAssembly | Derleyiciye derlenmiş kod yerine yalnızca bir başvuru derlemesi yörelemasını söyleyen bir boolean değeri. `ProduceReferenceAssembly`ile birlikte kullanılamaz.  Bu özellik *vbc.exe* ve *csc.exe* derleyicilerinin `/refonly` geçişine karşılık gelir. |
| Üretim Referans Montajı | Geçerli derleme için `true` referans [derlemelerinin](/dotnet/standard/assembly/reference-assemblies) üretilmesini sağlayacak şekilde ayarlandığında bir boolean değeri. `Deterministic`bu `true` özelliği kullanırken olmalıdır. Bu özellik *vbc.exe* ve *csc.exe* derleyicilerinin `/refout` geçişine karşılık gelir. |
| RemoveIntegerChecks | Tamsayı taşma hata denetimlerinin devre dışı bırakılıp atılmayacağını gösteren bir boolean değeri. Varsayılan değer: `false`. Bu özellik `/removeintchecks` *vbc.exe* derleyicisinin anahtarına eşdeğerdir. |
| RootNamespace | Katıştırılmış bir kaynak adlandırdığınızda kullanılacak kök ad alanı. Bu ad alanı, katıştırılmış kaynak bildirimi adının bir parçasıdır. |
| Satellite_AlgorithmId | Uydu derlemeleri oluşturulduğunda kullanılacak *AL.exe* karma algoritmasının kimliği. |
| Satellite_BaseAddress | Kültüre özel uydu derlemeleri `CreateSatelliteAssemblies` hedef kullanılarak inşa edildiğinde kullanılacak temel adres. |
| Satellite_CompanyName | Şirket adı uydu montaj üretimi sırasında *AL.exe'ye* geçecek. |
| Satellite_Configuration | Uydu montaj ı üretimi sırasında *AL.exe'ye* geçecek yapılandırma adı. |
| Satellite_Description | Uydu montajı üretimi sırasında *AL.exe'ye* geçecek açıklama metni. |
| Satellite_EvidenceFile | "Security.Evidence" kaynak adı olan uydu derlemesi için belirtilen dosyayı embeds. |
| Satellite_FileVersion | Uydu derlemesinde Dosya Sürümü alanı için bir dize belirtir. |
| Satellite_Flags | Uydu derlemesinde Bayraklar alanı için bir değer belirtir. |
| Satellite_GenerateFullPaths | Yapı görevinin hata iletisinde bildirilen dosyalar için mutlak yolları kullanmasına neden olur. |
| Satellite_LinkResource | Belirtilen kaynak dosyalarını uydu derlemesine bağlar. |
| Satellite_MainEntryPoint | Uydu montajı üretimi sırasında bir modül çalıştırılabilir bir dosyaya dönüştürüldüğünde, giriş noktası olarak kullanılacak yöntemin tam nitelikli adını (diğer bir şekilde class.method) belirtir. |
| Satellite_ProductName | Uydu derlemesinde Ürün alanı için bir dize belirtir. |
| Satellite_ProductVersion | Uydu derlemesinde ProductVersion alanı için bir dize belirtir. |
| Satellite_TargetType | Uydu derleme çıktısı dosyasının dosya biçimini "kitaplık", "exe" veya "kazan" olarak belirtir. Varsayılan değer "kitaplık" olur. |
| Satellite_Title | Uydu derlemesinde Başlık alanı için bir dize belirtir. |
| Satellite_Trademark | Uydu derlemesinde Ticari Marka alanı için bir dize belirtir. |
| Satellite_Version | Uydu montajı için sürüm bilgilerini belirtir. |
| Satellite_Win32Icon | Uydu montajına *.ico* simgesi dosyası ekler. |
| Satellite_Win32Resource | Uydu derlemesine Win32 kaynağı *(.res* dosyası) ekler. |
| Sgentoolpath | *SGen.exe'nin* geçerli sürümü geçersiz kılındığında *SGen.exe'nin* nereden alınacağını gösteren isteğe bağlı bir araç yolu. Bu özellik yalnızca .NET Framework için kullanılır.|
| SgenuseProxyTürleri | Proxy türlerinin *SGen.exe*tarafından oluşturulup oluşturulmaması gerektiğini belirten bir boolean değeri. Bu yalnızca *GenerateSerializationAssemblies'in* a)'ya ayarlandığında ve yalnızca .NET Framework için geçerlidir.<br /><br /> SGen hedefi, UseProxyTypes bayrağını ayarlamak için bu özelliği kullanır. Bu özellik varsayılan olarak true'dur ve bunu değiştirmek için ui yoktur. Web hizmeti olmayan türler için serileştirme derlemesi oluşturmak için, bu özelliği proje dosyasına ekleyin ve *Microsoft.Common.Targets* veya *C#/VB.targets'ı*içeri aktarmadan önce yanlış olarak ayarlayın. |
| Başlangıç Nesnesi | Ana yöntem veya Alt Ana yordamı içeren sınıfı veya modülü belirtir. Bu özellik derleyici `/main` anahtarına eşdeğerdir. |
| Alt SistemSürüm | Oluşturulan yürütülebilir dosyanın kullanabileceği alt sistemin minimum sürümünü belirtir. Bu özellik derleyici `/subsystemversion` anahtarına eşdeğerdir. Bu özelliğin varsayılan değeri hakkında bilgi için bkz: [/subsystemversion (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/subsystemversion) veya [/subsystemversion (C# derleyici seçenekleri).](/dotnet/csharp/language-reference/compiler-options/subsystemversion-compiler-option) |
| HedefKompakt Çerçeve | İnşa ettiğiniz uygulamayı çalıştırmak için gereken .NET Compact Framework sürümü. Bunu belirtmek, aksi takdirde başvuruda bulunamadığınız belirli çerçeve derlemelerine başvurmanızı sağlar. |
| TargetFrameworkVersion | İnşa ettiğiniz uygulamayı çalıştırmak için gereken .NET Framework sürümü. Bunu belirtmek, aksi takdirde başvuruda bulunamadığınız belirli çerçeve derlemelerine başvurmanızı sağlar. |
| Uyarıları Tedavi EtmeHataları | Tüm uyarıların hata olarak `true`ele alınmasına neden olan bir boolean parametresi. Bu parametre derleyici `/nowarn` anahtarına eşdeğerdir. |
| UseHostCompilerIfAvailable | Varsa, `true`yapı görevinin işlem içi derleyici nesnesini kullanmasına neden olan bir boolean parametresi. Bu parametre yalnızca Visual Studio tarafından kullanılır. |
| Utf8Çıktı | UtF-8 kodlaması `true`kullanarak derleyici çıktısını kaydeden bir boolean parametresi. Bu parametre derleyici `/utf8Output` anahtarına eşdeğerdir. |
| VbcToolPath | *Vbc.exe'nin* geçerli sürümü geçersiz kılındığında vbc.exe için başka bir konumu gösteren isteğe bağlı bir yol. *vbc.exe* |
| VbcVerbosity | Visual Basic derleyicisinin çıktısının ayrıntılılığını belirtir. Geçerli değerler "Sessiz", "Normal" (varsayılan değer) veya "Verbose" olarak adlandırılır. |
| Visualstudioversion | Visual Studio'nun bu projenin yürütülmüş olarak kabul edilmesi gereken sürümünü belirtir. Bu özellik belirtilmemişse, MSBuild onu makul bir varsayılan değere ayarlar.<br /><br /> Bu özellik, yapı için kullanılan hedef kümesini belirtmek için çeşitli proje türlerinde kullanılır. `ToolsVersion` Bir proje için 4.0 veya daha `VisualStudioVersion` yüksek olarak ayarlanmışsa, hangi alt araç kümesinin kullanılacağını belirtmek için kullanılır. Daha fazla bilgi için [Toolset (ToolsVersion) bakın.](../msbuild/msbuild-toolset-toolsversion.md) |
| WarningsAsErrors | Hata olarak ele almak için bir uyarı listesi belirtir. Bu parametre derleyici `/warnaserror` anahtarına eşdeğerdir. |
| WarningsNotasErrors | Hata olarak kabul edilmeyen uyarıların listesini belirtir. Bu parametre derleyici `/warnaserror` anahtarına eşdeğerdir. |
| Win32Manifesto | Son derlemeye katışdırılması gereken bildirim dosyasının adı. Bu parametre derleyici `/win32Manifest` anahtarına eşdeğerdir. |
| Win32Kaynak | Win32 kaynağının dosya adı son derlemeye katıştırılmak üzere. Bu parametre derleyici `/win32resource` anahtarına eşdeğerdir. |

## <a name="see-also"></a>Ayrıca bkz.

- [Ortak MSBuild proje öğeleri](../msbuild/common-msbuild-project-items.md)
