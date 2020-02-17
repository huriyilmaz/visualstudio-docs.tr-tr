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
ms.openlocfilehash: dd3ccd23775c93fb7222960c4db3ae5d35eb349f
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77275497"
---
# <a name="common-msbuild-project-properties"></a>Ortak MSBuild proje özellikleri
Aşağıdaki tabloda, Visual Studio proje dosyalarında tanımlanan veya MSBuild 'in sağladığı *. targets* dosyalarına eklenen sık kullanılan özellikler listelenmiştir.

 Visual Studio 'daki proje dosyaları ( *. csproj*, *. vbproj*, *. vcxproj*ve diğerleri), IDE kullanarak bir proje oluşturduğunuzda çalıştırılan MSBuild xml kodunu içerir. Projeler genellikle derleme işlemlerini tanımlamak için bir veya daha fazla *. targets* dosyasını içeri aktarır. Daha fazla bilgi için bkz. [MSBuild. targets dosyaları](../msbuild/msbuild-dot-targets-files.md).

## <a name="list-of-common-properties-and-parameters"></a>Ortak özellikler ve parametrelerin listesi

| Özellik veya parametre adı | Açıklama |
|------------------------------------| - |
| Adtiontalbpaths | Derleyicilerin başvuru derlemelerini arayacağı ek klasörleri belirtir. |
| AddModules | Derleyicinin, belirtilen dosyalardaki tüm tür bilgilerini derlediğiniz proje için kullanılabilir hale getirmesine neden olur. Bu özellik `/addModules` derleyici anahtarıyla eşdeğerdir. |
| ALToolPath | *Al. exe* ' nin bulunabileceği yol. Bu özellik, farklı bir sürümün kullanımını etkinleştirmek için *al. exe* ' nin geçerli sürümünü geçersiz kılar. |
| ApplicationIcon | Bir Win32 simgesi olarak katıştırmak üzere derleyiciye geçirilecek *. ico* simge dosyası. Özelliği, `/win32icon` derleyici anahtarıyla eşdeğerdir. |
| ApplicationManifest | Dış Kullanıcı hesabı denetimi (UAC) bildirim bilgilerini oluşturmak için kullanılan dosyanın yolunu belirtir. Yalnızca [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]hedefleyen Visual Studio projeleri için geçerlidir.<br /><br /> Çoğu durumda, bildirim katıştırılır. Ancak kayıt ücretsiz COM veya [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtımı kullanırsanız, bildirim, uygulama Derlemeleriyle birlikte yüklenen bir dış dosya olabilir. Daha fazla bilgi için bu konudaki NoWin32Manifest özelliğine bakın. |
| AssemblyOriginatorKeyFile | Derlemeyi ( *. snk* veya *. pfx*) imzalamak için kullanılan dosyayı belirtir ve derlemeyi imzalamak için kullanılan gerçek anahtarı oluşturmak için [ResolveKeySource görevine](../msbuild/resolvekeysource-task.md) geçirilir. |
| AssemblySearchPaths | Derleme zamanı başvuru derleme çözümlemesi sırasında aranacak konumların listesi. Daha önce listelenen yollar daha sonraki girişlerden daha öncelikli olduğundan, yolların bu listede görünme sırası anlamlı. |
| AssemblyName | Proje derlendikten sonra nihai çıkış derlemesinin adı. |
| BaseAddress | Ana çıkış derlemesinin temel adresini belirtir. Bu özellik `/baseaddress` derleyici anahtarıyla eşdeğerdir. |
| BaseIntermediateOutputPath | Yapılandırmaya özgü tüm ara çıkış klasörlerinin oluşturulduğu en üst düzey klasör. Varsayılan değer: `obj\`. Aşağıdaki kod bir örnektir: `<BaseIntermediateOutputPath>c:\xyz\obj\</BaseIntermediateOutputPath>` |
| BaseOutputPath | Çıkış dosyası için temel yolu belirtir. Ayarlanırsa, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] `OutputPath = $(BaseOutputPath)\$(Configuration)\`kullanacaktır. Örnek sözdizimi: `<BaseOutputPath>c:\xyz\bin\</BaseOutputPath>` |
| BuildInParallel | Multi-proc [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] kullanıldığında, proje başvurularının paralel olarak oluşturulup temizlenmediğini belirten bir Boolean değer. Varsayılan değer `true`, bu, sistemin birden çok çekirdeği veya işlemciyi varsa, bu projelerin paralel olarak derlenme anlamına gelir. |
| BuildProjectReferences | Proje başvurularının [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]tarafından oluşturulup oluşturulmayacağını gösteren Boolean bir değer. Projenizi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] tümleşik geliştirme ortamında (IDE) oluşturuyorsanız, aksi takdirde `true` otomatik olarak `false` olarak ayarlayın. başvurulan projelerin güncel olup olmadığını kontrol etmekten kaçınmak için, komut satırında `-p:BuildProjectReferences=false` belirtilebilir. |
| CleanFile | "Temiz önbellek" olarak kullanılacak dosyanın adı. Temizleme önbelleği, temizleme işlemi sırasında silinecek oluşturulan dosyaların bir listesidir. Dosya, yapı işlemi tarafından ara çıkış yoluna konur.<br /><br /> Bu özellik yalnızca yol bilgilerine sahip olmayan dosya adlarını belirtir. |
| Sayfasının | Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfasını belirtir. Bu özellik `/codepage` derleyici anahtarıyla eşdeğerdir. |
| CompilerResponseFile | Derleyici görevlerine geçirilebilecek, isteğe bağlı bir yanıt dosyası. |
| Yapılandırma | Oluşturmakta olduğunuz yapılandırma, "Debug" veya "Release" olabilir. |
| CscToolPath | *CSC. exe*' nin yolu [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] derleyicisidir. |
| CustomBeforeMicrosoftCommonTargets | Ortak hedefler içeri aktarmadan önce otomatik olarak içeri aktarılacak bir proje dosyasının veya hedef dosyanın adı. |
| DebugSymbols | Sembolün derleme tarafından oluşturulup oluşturulmayacağını gösteren bir Boolean değer.<br /><br /> Komut satırında **-p:DebugSymbols = false** ayarı, program veritabanı ( *. pdb*) sembol dosyalarının oluşturulmasını devre dışı bırakır. |
| DebugType | Oluşturulmasını istediğiniz hata ayıklama bilgileri düzeyini tanımlar. Geçerli değerler şunlardır "Full," "pdbonly," "taşınabilir", "Embedded" ve "none". |
| Definesabitleri | Koşullu derleyici sabitlerini tanımlar. Sembol/değer çiftleri noktalı virgülle ayrılır ve aşağıdaki sözdizimi kullanılarak belirtilir:<br /><br /> *symbol1 = değer1; symbol2 = değer2*<br /><br /> Özelliği, `/define` derleyici anahtarıyla eşdeğerdir. |
| DefineDebug | Hata ayıklama sabitinin tanımlanmasını isteyip istemediğinizi belirten bir Boole değeri. |
| DefineTrace | Izleme sabitinin tanımlanmasını isteyip istemediğinizi belirten bir Boole değeri. |
| DelaySign | Derlemeyi tam imzalamak yerine gecikmeye mi işaret etmek istediğinizi belirten Boolean bir değer. |
| Olmayan | Derleyicinin özdeş girdiler için özdeş derlemeler üretmesi gerekip gerekmediğini belirten bir Boolean değer. Bu parametre, *Vbc. exe* ve *CSC. exe* derleyicilerinin `/deterministic` anahtarına karşılık gelir. |
| Disableduyarılar | Belirtilen uyarıları bastırır. Uyarı tanımlayıcısının yalnızca sayısal kısmı belirtilmelidir. Birden çok uyarı noktalı virgülle ayrılır. Bu parametre, *Vbc. exe* derleyicisinin `/nowarn` anahtarına karşılık gelir. |
| DisableFastUpToDateCheck | Yalnızca [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] için geçerli olan bir Boole değeri. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Yapı Yöneticisi, bir projenin güncel olup olmadığını anlamak için FastUpToDateCheck adlı bir işlem kullanır. Bu işlem, bunu anlamak için [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] kullanmaktan daha hızlıdır. DisableFastUpToDateCheck özelliğinin `true` olarak ayarlanması, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] derleme yöneticisini atlayıp projenin güncel olup olmadığını belirlemede [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] kullanmaya zorlamanızı sağlar. |
| Belgetationfile | XML belge dosyası olarak oluşturulan dosyanın adı. Bu ad yalnızca dosya adını içerir ve yol bilgilerine sahip değildir. |
| ErrorReport | Derleyici görevinin iç derleyici hatalarını nasıl rapor etmesi gerektiğini belirtir. Geçerli değerler "Prompt", "send" veya "none" değerleridir. Bu özellik `/errorreport` derleyici anahtarıyla eşdeğerdir. |
| ExcludeDeploymentUrl | [GenerateDeploymentManifest görevi](../msbuild/generatedeploymentmanifest-task.md) , proje dosyası aşağıdaki öğelerden herhangi birini içeriyorsa dağıtım bildirimine bir deploymentProvider etiketi ekler:<br /><br /> -UpdateUrl<br />-InstallUrl<br />-PublishUrl<br /><br /> Ancak, ExcludeDeploymentUrl kullanarak, yukarıdaki URL 'Lerden herhangi biri belirtilmiş olsa bile, dağıtım bildirimine deploymentProvider etiketinin eklenmesini engelleyebilirsiniz. Bunu yapmak için, aşağıdaki özelliği proje dosyanıza ekleyin:<br /><br /> `<ExcludeDeploymentUrl>true</ExcludeDeploymentUrl>` <br /><br />**Note:**  ExcludeDeploymentUrl [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE 'de gösterilmez ve yalnızca proje dosyasını el ile düzenleyerek ayarlanabilir. Bu özelliğin ayarlanması [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]içinde yayımlamayı etkilemez; diğer bir deyişle, deploymentProvider etiketi yine PublishUrl tarafından belirtilen URL 'ye eklenecektir. |
| Dosya hizalaması | Çıktı dosyasının bölümlerinin hizalanın bayt cinsinden sayısını belirtir. Geçerli değerler 512, 1024, 2048, 4096, 8192. Bu özellik `/filealignment` derleyici anahtarıyla eşdeğerdir. |
| FrameworkPathOverride | *Mscorlib. dll* ve *Microsoft. VisualBasic. dll*dosyasının konumunu belirtir. Bu parametre, *Vbc. exe* derleyicisinin `/sdkpath` anahtarıyla eşdeğerdir. |
| GenerateDocumentation | (C#, Visual Basic) Yapı tarafından belgelerin oluşturulup oluşturulmayacağını gösteren bir Boolean parametresi. `true`, derleme belge bilgilerini oluşturur ve bir *. xml* dosyasına, derleme görevinin oluşturduğu yürütülebilir dosyanın veya kitaplığın adıyla birlikte koyar. |
| GenerateSerializationAssemblies | XML serileştirme derlemelerinin, açık, otomatik veya kapalı olarak ayarlanabileceği *SGen. exe*tarafından oluşturulup oluşturulmayacağını gösterir. Bu özellik yalnızca .NET Framework hedef derlemeler için kullanılır. .NET Standard veya .NET Core Derlemeleriyle ilgili XML serileştirme derlemeleri oluşturmak için *Microsoft. XmlSerializer. Generator* NuGet paketine başvurun. |
| IntermediateOutputPath | Yol belirtilmediyse `BaseIntermediateOutputPath`türetilen tam ara çıkış yolu. Örneğin, *\obj\debug\\* . |
| KeyContainerName | Tanımlayıcı ad anahtar kapsayıcısının adı. |
| Keyorigınatorfile | Tanımlayıcı ad anahtar dosyasının adı. |
| ModuleAssemblyName | Derlenen modülün içine dahil edilecek derlemenin adı. Özelliği, `/moduleassemblyname` derleyici anahtarıyla eşdeğerdir. |
| Msbuildprojeclarsionspath | Proje uzantılarının bulunduğu yolu belirtir. Varsayılan olarak, `BaseIntermediateOutputPath`ile aynı değeri alır. |
| NoLogo | Derleyici logosunun kapatılmasını isteyip istemediğinizi belirten bir Boole değeri. Bu özellik `/nologo` derleyici anahtarıyla eşdeğerdir. |
| NoStdLib | Standart kitaplığa (*mscorlib. dll*) başvurulmaya engellenip engellenmeyeceğini belirten bir Boole değeri. Varsayılan değer: `false`. |
| NoVBRuntimeReference | [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] çalışma zamanının (*Microsoft. VisualBasic. dll*) projeye başvuru olarak eklenmesi gerekip gerekmediğini belirten bir Boolean değer. |
| NoWin32Manifest | Kullanıcı hesabı denetimi (UAC) bildirim bilgisinin uygulamanın yürütülebilir dosyasına katıştırılacağını belirten bir Boole değeri. Yalnızca [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]hedefleyen Visual Studio projeleri için geçerlidir. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ve kayıtsız COM kullanılarak dağıtılan projelerde, bu öğe yok sayılır. `False` (varsayılan değer), Kullanıcı hesabı denetimi (UAC) bildirim bilgisinin uygulamanın yürütülebilir dosyasına katıştırılacağını belirtir. `True`, UAC bildirim bilgilerinin gömülmeyeceğini belirtir.<br /><br /> Bu özellik yalnızca [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]hedefleyen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projeleri için geçerlidir. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ve kayıtsız COM kullanılarak dağıtılan projelerde, bu özellik yok sayılır.<br /><br /> Yalnızca uygulamanın yürütülebilir dosyasına herhangi bir bildirim bilgisini eklemek [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] istemiyorsanız NoWin32Manifest eklemeniz gerekir; Bu işleme *sanallaştırma*olarak adlandırılır. Sanallaştırmayı kullanmak için `<NoWin32Manifest>` ile birlikte `<ApplicationManifest>` aşağıdaki şekilde ayarlayın:<br /><br /> -[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projeleri için `<ApplicationManifest>` düğümünü kaldırın. ([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projelerinde, bir `<ApplicationManifest>` düğümü varken `<NoWin32Manifest>` yoksayılır.)<br />-[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projeleri için `<ApplicationManifest>` `False` ve `True``<NoWin32Manifest>` olarak ayarlayın. ([!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projelerinde, `<ApplicationManifest>` geçersiz kılmalar `<NoWin32Manifest>`.)<br /> Bu özellik *Vbc. exe*' nin `/nowin32manifest` derleyici anahtarıyla eşdeğerdir. |
| İyileştirme | `true`olarak ayarlandığında derleyici iyileştirmelerini sağlayan bir Boole değeri. Bu özellik `/optimize` derleyici anahtarıyla eşdeğerdir. |
| OptionCompare | Dize karşılaştırmalarının nasıl yapılacağını belirtir. Geçerli değerler şunlardır "binary" veya "Text." Bu özellik *Vbc. exe*' nin `/optioncompare` derleyici anahtarıyla eşdeğerdir. |
| OptionExplicit | `true`olarak ayarlandığında, kaynak koddaki değişkenlerin açık bildirimini gerektiren bir Boole değeri. Bu özellik `/optionexplicit` derleyici anahtarıyla eşdeğerdir. |
| OptionInfer | `true`olarak ayarlandığında değişkenlerin tür çıkarımını sağlayan bir Boole değeri. Bu özellik `/optioninfer` derleyici anahtarıyla eşdeğerdir. |
| OptionStrict | `true`olarak ayarlanmış bir Boole değeri, derleme görevinin örtük tür dönüştürücülerini zorlamak için katı tür semantiğini zorlamasına neden olur. Bu özellik *Vbc. exe* derleyicisinin `/optionstrict` anahtarıyla eşdeğerdir. |
| OutDir | Proje veya çözüm için son çıkış konumunu gösterir. Bir çözüm oluştururken, OutDir birden fazla proje çıkışını tek bir konumda toplamak için kullanılabilir. Ayrıca, OutDir başvuruları çözümlemek için kullanılan AssemblySearchPaths 'a dahildir. Örneğin, *bin\Debug*. |
| OutputPath | Proje dizinine göre çıkış dizininin yolunu belirtir, örneğin, *bin\Debug*. |
| #B2 | Çıktı dosyasının dosya biçimini belirtir. Bu parametre aşağıdaki değerlerden birine sahip olabilir:<br /><br /> Kitaplığı. Bir kod kitaplığı oluşturur. (Varsayılan değer.)<br />Exe. Bir konsol uygulaması oluşturur.<br />Birimi. Bir modül oluşturur.<br />Winexe. Windows tabanlı bir program oluşturur.<br /><br /> Bu özellik *Vbc. exe* derleyicisinin `/target` anahtarıyla eşdeğerdir. |
| OverwriteReadOnlyFiles | Derlemeyi salt okuma dosyalarının üzerine yazmak veya bir hata tetiklemeyi etkinleştirmek isteyip istemediğinizi belirten bir Boole değeri. |
| PathMap | Derleyici tarafından giden kaynak yol adlarına fiziksel yolların nasıl eşleneceğini belirtir. Bu özellik, *CSC. exe* derleyicisinin `/pathmap` anahtarıyla eşdeğerdir. |
| Pdbdosya | Yayma yaptığınız *. pdb* dosyasının dosya adı. Bu özellik, *CSC. exe* derleyicisinin `/pdb` anahtarıyla eşdeğerdir. |
| Platform | İçin oluşturmakta olduğunuz işletim sistemi. Geçerli değerler şunlardır "Any CPU", "x86" ve "x64". |
| ProcessorArchitecture | Derleme başvuruları çözümlendiğinde kullanılan işlemci mimarisi. Geçerli değerler şunlardır "MSIL," "x86," "amd64" veya "ia64." |
| ProduceOnlyReferenceAssembly | Derleyiciye derlenen kod yerine yalnızca bir başvuru derlemesi yaymasını bildiren bir Boole değeri. `ProduceReferenceAssembly`ile birlikte kullanılamaz.  Bu özellik *Vbc. exe* ve *CSC. exe* derleyicilerinin `/refonly` anahtarına karşılık gelir. |
| ProduceReferenceAssembly | `true` olarak ayarlandığında geçerli derleme için [başvuru derlemelerinin](/dotnet/standard/assembly/reference-assemblies) üretimini sağlayan bir Boole değeri. Bu özellik kullanılırken `Deterministic` `true` olmalıdır. Bu özellik *Vbc. exe* ve *CSC. exe* derleyicilerinin `/refout` anahtarına karşılık gelir. |
| RemoveIntegerChecks | Tamsayı taşma hata denetimlerinin devre dışı bırakılıp başlatılmayacağını belirten bir Boole değeri. Varsayılan değer: `false`. Bu özellik *Vbc. exe* derleyicisinin `/removeintchecks` anahtarıyla eşdeğerdir. |
| RootNamespace | Gömülü bir kaynağı ad yazdığınızda kullanılacak kök ad alanı. Bu ad alanı, gömülü kaynak bildirim adının bir parçasıdır. |
| Satellite_AlgorithmId | Uydu derlemeleri oluşturulurken kullanılacak *al. exe* karma algoritmasının kimliği. |
| Satellite_BaseAddress | Kültüre özgü uydu derlemeleri `CreateSatelliteAssemblies` hedefi kullanılarak oluşturulduğunda kullanılacak temel adres. |
| Satellite_CompanyName | Uydu derleme oluşturma sırasında *al. exe* ' ye geçirilecek şirket adı. |
| Satellite_Configuration | Uydu derleme oluşturma sırasında *al. exe* ' ye geçirilecek yapılandırma adı. |
| Satellite_Description | Uydu derleme oluşturma sırasında *al. exe* ' ye geçirilecek açıklama metni. |
| Satellite_EvidenceFile | Belirtilen dosyayı, "Security. kanıt" Kaynak adına sahip uydu derlemesine gömer. |
| Satellite_FileVersion | Uydu derlemesindeki dosya sürümü alanı için bir dize belirtir. |
| Satellite_Flags | Uydu derlemesindeki Flags alanı için bir değer belirtir. |
| Satellite_GenerateFullPaths | Derleme görevinin bir hata iletisinde bildirilen tüm dosyalar için mutlak yollar kullanmasına neden olur. |
| Satellite_LinkResource | Belirtilen kaynak dosyalarını bir uydu derlemesine bağlar. |
| Satellite_MainEntryPoint | Bir modül, uydu derleme oluşturma sırasında yürütülebilir bir dosyaya dönüştürüldüğünde giriş noktası olarak kullanılacak yöntemin tam nitelikli adını (yani, Class. yöntemi) belirtir. |
| Satellite_ProductName | Uydu derlemesindeki ürün alanı için bir dize belirtir. |
| Satellite_ProductVersion | Uydu derlemesinde ProductVersion alanı için bir dize belirtir. |
| Satellite_TargetType | Uydu derleme çıkış dosyasının dosya biçimini "Library," "exe" veya "Win" olarak belirtir. Varsayılan değer "Library" dir. |
| Satellite_Title | Uydu derlemesinde başlık alanı için bir dize belirtir. |
| Satellite_Trademark | Uydu derlemesindeki ticari marka alanı için bir dize belirtir. |
| Satellite_Version | Uydu derlemesinin sürüm bilgilerini belirtir. |
| Satellite_Win32Icon | Uydu derlemesine bir *. ico* simge dosyası ekler. |
| Satellite_Win32Resource | Uydu derlemesine bir Win32 kaynağı ( *. res* dosyası) ekler. |
| SGenToolPath | Geçerli *SGen. exe* sürümü geçersiz kılındığında *SGen. exe* ' nin nereden alınacağını belirten isteğe bağlı bir araç yolu. Bu özellik yalnızca .NET Framework için kullanılır.|
| SGenUseProxyTypes | Proxy türlerinin *SGen. exe*tarafından oluşturulup oluşturulmayacağını gösteren bir Boolean değer. Bu yalnızca *GenerateSerializationAssemblies* on olarak ayarlandığında ve yalnızca .NET Framework için geçerlidir.<br /><br /> SGen hedefi, UseProxyTypes bayrağını ayarlamak için bu özelliği kullanır. Bu özellik varsayılan olarak true değerini alır ve bunu değiştirmek için bir kullanıcı arabirimi yoktur. Web hizmeti olmayan türler için serileştirme derlemesini oluşturmak üzere, bu özelliği proje dosyasına ekleyin ve *Microsoft. Common. targets* veya  *C#/vb.exe*'i içeri aktarmadan önce false olarak ayarlayın. |
| StartupObject | Ana yöntemi veya alt ana yordamı içeren sınıfı veya modülü belirtir. Bu özellik `/main` derleyici anahtarıyla eşdeğerdir. |
| SubsystemVersion | Oluşturulan yürütülebilir dosyanın kullanabileceği alt sistemin en düşük sürümünü belirtir. Bu özellik `/subsystemversion` derleyici anahtarıyla eşdeğerdir. Bu özelliğin varsayılan değeri hakkında daha fazla bilgi için bkz. [/subsystemversion (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/subsystemversion) veya [/subsystemversion (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/subsystemversion-compiler-option). |
| TargetCompactFramework | Oluşturmakta olduğunuz uygulamayı çalıştırmak için gereken .NET Compact Framework sürümü. Bunu belirtmek, başka türlü başvuramayacak bazı Framework derlemelerine başvurmanıza olanak sağlar. |
| TargetFrameworkVersion | Oluşturmakta olduğunuz uygulamayı çalıştırmak için gereken .NET Framework sürümü. Bunu belirtmek, başka türlü başvuramayacak bazı Framework derlemelerine başvurmanıza olanak sağlar. |
| TreatWarningsAsErrors | `true`, tüm uyarıların hata olarak işlenmesine neden olan bir Boole parametresi. Bu parametre `/nowarn` derleyici anahtarıyla eşdeğerdir. |
| UseHostCompilerIfAvailable | `true`, derleme görevinin varsa işlem içi derleyici nesnesini kullanmasına neden olan bir Boole parametresi. Bu parametre yalnızca [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]tarafından kullanılır. |
| Utf8Output | `true`, derleyici çıkışını UTF-8 kodlaması kullanarak günlüğe kaydettiğini belirten bir Boole parametresi. Bu parametre `/utf8Output` derleyici anahtarıyla eşdeğerdir. |
| VbcToolPath | Geçerli *Vbc. exe* sürümü geçersiz kılındığında *Vbc. exe* için başka bir konum belirten isteğe bağlı bir yol. |
| Vbcayrıntı düzeyi | [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] derleyicisinin çıkışının ayrıntı düzeyini belirtir. Geçerli değerler şunlardır "sessiz," "normal" (varsayılan değer) veya "ayrıntılıdır." |
| VisualStudioVersion | Bu projenin çalıştığı kabul edileceği Visual Studio sürümünü belirtir. Bu özellik belirtilmezse, MSBuild bunu makul bir varsayılan değere ayarlar.<br /><br /> Bu özellik, derleme için kullanılan hedef kümesini belirtmek için çeşitli proje türlerinde kullanılır. `ToolsVersion` bir proje için 4,0 veya üzeri bir değere ayarlanırsa, kullanılacak alt araç takımını belirlemek için `VisualStudioVersion` kullanılır. Daha fazla bilgi için bkz. [araç takımı (araçları sürümü)](../msbuild/msbuild-toolset-toolsversion.md). |
| WarningsAsErrors | Hata olarak değerlendirmek için uyarıların listesini belirtir. Bu parametre `/warnaserror` derleyici anahtarıyla eşdeğerdir. |
| Warninggözetimi Taserrors | Hata olarak değerlendirilmediğini belirten uyarıların bir listesini belirtir. Bu parametre `/warnaserror` derleyici anahtarıyla eşdeğerdir. |
| Win32Manifest | Son derlemeye katıştırılması gereken bildirim dosyasının adı. Bu parametre `/win32Manifest` derleyici anahtarıyla eşdeğerdir. |
| Win32Resource | Son derlemeye katıştırılacak Win32 kaynağının dosya adı. Bu parametre `/win32resource` derleyici anahtarıyla eşdeğerdir. |

## <a name="see-also"></a>Ayrıca bkz.
- [Ortak MSBuild proje öğeleri](../msbuild/common-msbuild-project-items.md)
