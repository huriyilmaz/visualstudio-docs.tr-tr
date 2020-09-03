---
title: Ortak MSBuild proje özellikleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
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
caps.latest.revision: 39
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1eb56d1334eb18dd5872457d032e5780a3f75eb3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65698715"
---
# <a name="common-msbuild-project-properties"></a>Yaygın MSBuild Proje Özellikleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aşağıdaki tabloda, Visual Studio proje dosyalarında tanımlanan veya MSBuild 'in sağladığı. targets dosyalarına eklenen sık kullanılan özellikler listelenmiştir.  
  
 Visual Studio 'daki proje dosyaları (. csproj,. vbproj, vcxproj ve diğerleri), IDE kullanarak bir proje oluşturduğunuzda çalıştırılan MSBuild XML kodunu içerir. Projeler genellikle derleme işlemlerini tanımlamak için bir veya daha fazla. targets dosyasını içeri aktarır. Daha fazla bilgi için bkz [.. Hedef dosyaları](../msbuild/msbuild-dot-targets-files.md).  
  
## <a name="list-of-common-properties-and-parameters"></a>Ortak Özellikler ve Parametreler listesi  
  
|Özellik veya parametre adı|Description|  
|--------------------------------|-----------------|  
|Adtiontalbpaths|Derleyicilerin başvuru derlemelerini arayacağı ek klasörleri belirtir.|  
|AddModules|Derleyicinin, belirtilen dosyalardaki tüm tür bilgilerini derlediğiniz proje için kullanılabilir hale getirmesine neden olur. Bu özellik, `/addModules` derleyici anahtarıyla eşdeğerdir.|  
|ALToolPath|AL.exe bulunabileceği yol. Bu özellik, farklı bir sürümün kullanımını etkinleştirmek için geçerli AL.exe sürümünü geçersiz kılar.|  
|ApplicationIcon|Bir Win32 simgesi olarak katıştırmak üzere derleyiciye geçirilecek. ico simge dosyası. Özelliği, `/win32icon` derleyici anahtarıyla eşdeğerdir.|  
|ApplicationManifest|Dış Kullanıcı hesabı denetimi (UAC) bildirim bilgilerini oluşturmak için kullanılan dosyanın yolunu belirtir. Yalnızca Visual Studio projeleri hedefleme için geçerlidir [!INCLUDE[windowsver](../includes/windowsver-md.md)] .<br /><br /> Çoğu durumda, bildirim katıştırılır. Ancak kayıt ücretsiz COM veya [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtım kullanıyorsanız, bildirim, uygulama Derlemeleriyle birlikte yüklenen bir dış dosya olabilir. Daha fazla bilgi için bu konudaki NoWin32Manifest özelliğine bakın.|  
|AssemblyOriginatorKeyFile|Derlemeyi (. snk veya. pfx) imzalamak için kullanılan dosyayı belirtir ve derlemeyi imzalamak için kullanılan gerçek anahtarı oluşturmak için [ResolveKeySource görevine](../msbuild/resolvekeysource-task.md) geçirilir.|  
|AssemblySearchPaths|Derleme zamanı başvuru derleme çözümlemesi sırasında aranacak konumların listesi. Daha önce listelenen yollar daha sonraki girişlerden daha öncelikli olduğundan, yolların bu listede görünme sırası anlamlı.|  
|AssemblyName|Proje derlendikten sonra nihai çıkış derlemesinin adı.|  
|BaseAddress|Ana çıkış derlemesinin temel adresini belirtir. Bu özellik, `/baseaddress` derleyici anahtarıyla eşdeğerdir.|  
|BaseOutputPath|Çıkış dosyası için temel yolu belirtir. Ayarlanırsa, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] kullanılır `OutputPath = $(BaseOutputPath)\$(Configuration)\` . Örnek sözdizimi: `<BaseOutputPath>c:\xyz\bin\</BaseOutputPath>`|  
|Baseıntermediateoutputpath|Yapılandırmaya özgü tüm ara çıkış klasörlerinin oluşturulduğu en üst düzey klasör. Varsayılan değer: `obj\`. Aşağıdaki kod bir örnektir: `<BaseIntermediateOutputPath>c:\xyz\obj\</BaseIntermediateOutputPath>`|  
|BuildInParallel|Birden çok proc kullanıldığında, proje başvurularının paralel olarak oluşturulup temizlenmediğini belirten bir Boolean değer [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] . Varsayılan değer `true` , bu, sistemin birden çok çekirdeği veya işlemciyi varsa, projenin paralel olarak derlenme anlamına gelir.|  
|BuildProjectReferences|Proje başvurularının tarafından oluşturulup oluşturulmayacağını gösteren bir Boolean değer [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] . `false`Projenizi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tümleşik geliştirme ORTAMıNDA (IDE) oluşturuyorsanız, `true` Aksi takdirde ayarlayın.|  
|CleanFile|"Temiz önbellek" olarak kullanılacak dosyanın adı. Temizleme önbelleği, temizleme işlemi sırasında silinecek oluşturulan dosyaların bir listesidir. Dosya, yapı işlemi tarafından ara çıkış yoluna konur.<br /><br /> Bu özellik yalnızca yol bilgilerine sahip olmayan dosya adlarını belirtir.|  
|Sayfasının|Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfasını belirtir. Bu özellik, `/codepage` derleyici anahtarıyla eşdeğerdir.|  
|CompilerResponseFile|Derleyici görevlerine geçirilebilecek, isteğe bağlı bir yanıt dosyası.|  
|Yapılandırma|Oluşturmakta olduğunuz yapılandırma, "Debug" veya "Release" olabilir.|  
|CscToolPath|csc.exe, [!INCLUDE[csprcs](../includes/csprcs-md.md)] derleyicisinin yolu.|  
|CustomBeforeMicrosoftCommonTargets|Ortak hedefler içeri aktarmadan önce otomatik olarak içeri aktarılacak bir proje dosyasının veya hedef dosyanın adı.|  
|DebugSymbols|Sembolün derleme tarafından oluşturulup oluşturulmayacağını gösteren bir Boolean değer.<br /><br /> Komut satırında **/p: DebugSymbols = false** ayarı program veritabanı (. pdb) sembol dosyalarının oluşturulmasını devre dışı bırakır.|  
|Definesabitleri|Koşullu derleyici sabitlerini tanımlar. Sembol/değer çiftleri noktalı virgülle ayrılır ve aşağıdaki sözdizimi kullanılarak belirtilir:<br /><br /> *symbol1 = değer1; symbol2 = değer2*<br /><br /> Özelliği, `/define` derleyici anahtarıyla eşdeğerdir.|  
|DefineDebug|Hata ayıklama sabitinin tanımlanmasını isteyip istemediğinizi belirten bir Boole değeri.|  
|DefineTrace|Izleme sabitinin tanımlanmasını isteyip istemediğinizi belirten bir Boole değeri.|  
|DebugType|Oluşturulmasını istediğiniz hata ayıklama bilgileri düzeyini tanımlar. Geçerli değerler şunlardır "Full," "pdbonly" ve "none".|  
|DelaySign|Derlemeyi tam imzalamak yerine gecikmeye mi işaret etmek istediğinizi belirten Boolean bir değer.|  
|Disableduyarılar|Belirtilen uyarıları bastırır. Uyarı tanımlayıcısının yalnızca sayısal kısmı belirtilmelidir. Birden çok uyarı noktalı virgülle ayrılır. Bu parametre `/nowarn` vbc.exe derleyicisinin anahtarına karşılık gelir.|  
|DisableFastUpToDateCheck|Yalnızca için geçerli olan bir Boole değeri [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Yapı Yöneticisi, bir projenin güncel olması için yeniden oluşturulması gerekip gerekmediğini öğrenmek Için FastUpToDateCheck adlı bir işlem kullanır. Bu işlem, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] bunu anlamak için kullanmaktan daha hızlıdır. DisableFastUpToDateCheck özelliğinin olarak ayarlanması, `true` [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] yapı yöneticisini atlayıp [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projenin güncel olup olmadığını belirlemede kullanılmasını zorlamanızı sağlar.|  
|Belgetationfile|XML belge dosyası olarak oluşturulan dosyanın adı. Bu ad yalnızca dosya adını içerir ve yol bilgilerine sahip değildir.|  
|ErrorReport|Derleyici görevinin iç derleyici hatalarını nasıl rapor etmesi gerektiğini belirtir. Geçerli değerler "Prompt", "send" veya "none" değerleridir. Bu özellik, `/errorreport` derleyici anahtarıyla eşdeğerdir.|  
|ExcludeDeploymentUrl|[GenerateDeploymentManifest görevi](../msbuild/generatedeploymentmanifest-task.md) , proje dosyası aşağıdaki öğelerden herhangi birini içeriyorsa dağıtım bildirimine bir deploymentProvider etiketi ekler:<br /><br /> -UpdateUrl<br />-InstallUrl<br />-PublishUrl<br /><br /> Ancak, ExcludeDeploymentUrl kullanarak, yukarıdaki URL 'Lerden herhangi biri belirtilmiş olsa bile, dağıtım bildirimine deploymentProvider etiketinin eklenmesini engelleyebilirsiniz. Bunu yapmak için, aşağıdaki özelliği proje dosyanıza ekleyin:<br /><br /> `<ExcludeDeploymentUrl>true</ExcludeDeploymentUrl>`**Note:**  ExcludeDeploymentUrl, IDE 'de gösterilmez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ve yalnızca proje dosyasını el ile düzenleyerek ayarlanabilir. Bu özelliğin ayarlanması içindeki yayımlamayı etkilemez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ; Yani, deploymentProvider etiketi PublishUrl tarafından BELIRTILEN URL 'ye eklenecektir.|  
|Dosya hizalaması|Çıktı dosyasının bölümlerinin hizalanın bayt cinsinden sayısını belirtir. Geçerli değerler 512, 1024, 2048, 4096, 8192. Bu özellik, `/filealignment` derleyici anahtarıyla eşdeğerdir.|  
|FrameworkPathOverride|mscorlib.dll ve microsoft.visualbasic.dll konumunu belirtir. Bu parametre `/sdkpath` vbc.exe derleyicisinin anahtarıyla eşdeğerdir.|  
|GenerateDocumentation|Yapı tarafından belgelerin oluşturulup oluşturulmayacağını gösteren bir Boolean parametresi. `true`Derleme, belge bilgilerini oluşturur ve bir. xml dosyasına, derleme görevinin oluşturduğu yürütülebilir dosyanın veya kitaplığın adıyla birlikte koyar.|  
|IntermediateOutputPath|Yol belirtilmemişse tam ara çıkış yolu öğesinden türetilir `BaseIntermediateOutputPath` . Örneğin, \obj\debug \\ . Bu özellik geçersiz kılınırsa, ayarın `BaseIntermediateOutputPath` hiçbir etkisi olmaz.|  
|KeyContainerName|Tanımlayıcı ad anahtar kapsayıcısının adı.|  
|Keyorigınatorfile|Tanımlayıcı ad anahtar dosyasının adı.|  
|NoWin32Manifest|Derleyicinin çıkış derlemesinde varsayılan Win32 bildirimini oluşturup oluşturmayacağını belirler. Varsayılan değeri, `false` varsayılan Win32 bildiriminin tüm uygulamalar için oluşturulduğu anlamına gelir. Bu özellik `/nowin32manifest` vbc.exe derleyici anahtarıyla eşdeğerdir.|  
|ModuleAssemblyName|Derlenen modülün içine dahil edilecek derlemenin adı. Özelliği, `/moduleassemblyname` derleyici anahtarıyla eşdeğerdir.|  
|NoLogo|Derleyici logosunun kapatılmasını isteyip istemediğinizi belirten bir Boole değeri. Bu özellik, `/nologo` derleyici anahtarıyla eşdeğerdir.|  
|NoStdLib|Standart kitaplığa (mscorlib.dll) başvurulmaya engellenip engellenmeyeceğini belirten bir Boole değeri. Varsayılan değer: `false`.|  
|NoVBRuntimeReference|[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]Çalışma zamanının (Microsoft.VisualBasic.dll) projeye başvuru olarak dahil edilip edilmeyeceğini belirten bir Boole değeri.|  
|NoWin32Manifest|Kullanıcı hesabı denetimi (UAC) bildirim bilgisinin uygulamanın yürütülebilir dosyasına katıştırılacağını belirten bir Boole değeri. Yalnızca Visual Studio projeleri hedefleme için geçerlidir [!INCLUDE[windowsver](../includes/windowsver-md.md)] . [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Ve KAYıTSıZ com kullanılarak dağıtılan projelerde, bu öğe yok sayılır. `False` (varsayılan değer) Kullanıcı hesabı denetimi (UAC) bildirim bilgisinin uygulamanın yürütülebilir dosyasına katıştırılacağını belirtir. `True` UAC bildirim bilgilerinin gömülmeyeceğini belirtir.<br /><br /> Bu özellik yalnızca [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hedefleme projeleri için geçerlidir [!INCLUDE[windowsver](../includes/windowsver-md.md)] . [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Ve KAYıTSıZ com kullanılarak dağıtılan projelerde, bu özellik yok sayılır.<br /><br /> Yalnızca [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uygulamanın yürütülebilir dosyasına herhangi bir bildirim bilgisini eklemek Istemiyorsanız nowin32manifest eklemeniz gerekir; bu işleme *sanallaştırma*olarak adlandırılır. Sanallaştırmayı kullanmak için `<ApplicationManifest>` ile birlikte `<NoWin32Manifest>` aşağıdaki şekilde ayarlayın:<br /><br /> - [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] Projeler için `<ApplicationManifest>` düğümü kaldırın. ( [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] Projelerde, `<NoWin32Manifest>` bir düğüm varken yok sayılır `<ApplicationManifest>` .)<br />- [!INCLUDE[csprcs](../includes/csprcs-md.md)] Projeler için ve olarak `<ApplicationManifest>` ayarlanır `False` `<NoWin32Manifest>` `True` . ( [!INCLUDE[csprcs](../includes/csprcs-md.md)] Projelerde, `<ApplicationManifest>` geçersiz kılmalar `<NoWin32Manifest>` .)|  
|İyileştirme|Olarak ayarlandığında `true` derleyici iyileştirmelerini sağlayan bir Boole değeri. Bu özellik, `/optimize` derleyici anahtarıyla eşdeğerdir.|  
|OptionCompare|Dize karşılaştırmalarının nasıl yapılacağını belirtir. Geçerli değerler şunlardır "binary" veya "Text." Bu özellik `/optioncompare` vbc.exe derleyici anahtarıyla eşdeğerdir.|  
|OptionExplicit|Olarak ayarlandığında `true` , kaynak koddaki değişkenlerin açık bildirimini gerektiren Boolean bir değer. Bu özellik, `/optionexplicit` derleyici anahtarıyla eşdeğerdir.|  
|OptionInfer|Olarak ayarlandığında `true` değişkenlerin tür çıkarımını sağlayan bir Boole değeri. Bu özellik, `/optioninfer` derleyici anahtarıyla eşdeğerdir.|  
|OptionStrict|Olarak ayarlandığında `true` , derleme görevinin örtük tür semantiğini zorlamak için katı tür semantiğini zorlamasına neden olan bir Boole değeri. Bu özellik `/optionstrict` vbc.exe derleyicisinin anahtarıyla eşdeğerdir.|  
|OutputPath|"Bin\Debug" gibi, proje dizinine göre çıkış dizininin yolunu belirtir.|  
|#B2|Çıktı dosyasının dosya biçimini belirtir. Bu parametre aşağıdaki değerlerden birine sahip olabilir:<br /><br /> Kitaplığı. Bir kod kitaplığı oluşturur. (Varsayılan değer.)<br />Exe. Bir konsol uygulaması oluşturur.<br />Birimi. Bir modül oluşturur.<br />Winexe. Windows tabanlı bir program oluşturur.<br /><br /> Bu özellik `/target` vbc.exe derleyicisinin anahtarıyla eşdeğerdir.|  
|OverwriteReadOnlyFiles|Derlemeyi salt okuma dosyalarının üzerine yazmak veya bir hata tetiklemeyi etkinleştirmek isteyip istemediğinizi belirten bir Boole değeri.|  
|Pdbdosya|Yayma yaptığınız. pdb dosyasının dosya adı. Bu özellik `/pdb` csc.exe derleyicisinin anahtarıyla eşdeğerdir.|  
|Platform|İçin oluşturmakta olduğunuz işletim sistemi. Geçerli değerler şunlardır "Any CPU", "x86" ve "x64".|  
|Removeıntegerdenetimleri|Tamsayı taşma hata denetimlerinin devre dışı bırakılıp başlatılmayacağını belirten bir Boole değeri. Varsayılan değer: `false`. Bu özellik `/removeintchecks` vbc.exe derleyicisinin anahtarıyla eşdeğerdir.|  
|SGenUseProxyTypes|Proxy türlerinin SGen.exe tarafından oluşturulup oluşturulmayacağını gösteren Boolean bir değer.<br /><br /> SGen hedefi, UseProxyTypes bayrağını ayarlamak için bu özelliği kullanır. Bu özellik varsayılan olarak true değerini alır ve bunu değiştirmek için bir kullanıcı arabirimi yoktur. Web hizmeti olmayan türler için serileştirme derlemesini oluşturmak için, bu özelliği proje dosyasına ekleyin ve Microsoft. Common. targets veya C#/vb.exe ' i içeri aktarmadan önce false olarak ayarlayın.|  
|SGenToolPath|Geçerli SGen.exe sürümü geçersiz kılındığında SGen.exe nereden alınacağını belirten isteğe bağlı bir araç yolu.|  
|StartupObject|Ana yöntemi veya alt ana yordamı içeren sınıfı veya modülü belirtir. Bu özellik, `/main` derleyici anahtarıyla eşdeğerdir.|  
|ProcessorArchitecture|Derleme başvuruları çözümlendiğinde kullanılan işlemci mimarisi. Geçerli değerler şunlardır "MSIL," "x86," "amd64" veya "ia64."|  
|RootNamespace|Gömülü bir kaynağı ad yazdığınızda kullanılacak kök ad alanı. Bu ad alanı, gömülü kaynak bildirim adının bir parçasıdır.|  
|Satellite_AlgorithmId|Uydu derlemeleri oluşturulurken kullanılacak AL.exe karma algoritma KIMLIĞI.|  
|Satellite_BaseAddress|Kültüre özgü uydu derlemeleri hedef kullanılarak oluşturulduğunda kullanılacak temel adres `CreateSatelliteAssemblies` .|  
|Satellite_CompanyName|Uydu derleme oluşturma sırasında AL.exe geçirilecek şirket adı.|  
|Satellite_Configuration|Uydu derleme oluşturma sırasında AL.exe geçirilecek yapılandırma adı.|  
|Satellite_Description|Uydu derleme oluşturma sırasında AL.exe geçirilecek açıklama metni.|  
|Satellite_EvidenceFile|Belirtilen dosyayı, "Security. kanıt" Kaynak adına sahip uydu derlemesine gömer.|  
|Satellite_FileVersion|Uydu derlemesindeki dosya sürümü alanı için bir dize belirtir.|  
|Satellite_Flags|Uydu derlemesindeki Flags alanı için bir değer belirtir.|  
|Satellite_GenerateFullPaths|Derleme görevinin bir hata iletisinde bildirilen tüm dosyalar için mutlak yollar kullanmasına neden olur.|  
|Satellite_LinkResource|Belirtilen kaynak dosyalarını bir uydu derlemesine bağlar.|  
|Satellite_MainEntryPoint|Bir modül, uydu derleme oluşturma sırasında yürütülebilir bir dosyaya dönüştürüldüğünde giriş noktası olarak kullanılacak yöntemin tam nitelikli adını (yani, Class. yöntemi) belirtir.|  
|Satellite_ProductName|Uydu derlemesindeki ürün alanı için bir dize belirtir.|  
|Satellite_ProductVersion|Uydu derlemesinde ProductVersion alanı için bir dize belirtir.|  
|Satellite_TargetType|Uydu derleme çıkış dosyasının dosya biçimini "Library," "exe" veya "Win" olarak belirtir. Varsayılan değer "Library" dir.|  
|Satellite_Title|Uydu derlemesinde başlık alanı için bir dize belirtir.|  
|Satellite_Trademark|Uydu derlemesindeki ticari marka alanı için bir dize belirtir.|  
|Satellite_Version|Uydu derlemesinin sürüm bilgilerini belirtir.|  
|Satellite_Win32Icon|Uydu derlemesine bir. ico simge dosyası ekler.|  
|Satellite_Win32Resource|Uydu derlemesine bir Win32 kaynağı (. res dosyası) ekler.|  
|SubsystemVersion|Oluşturulan yürütülebilir dosyanın kullanabileceği alt sistemin en düşük sürümünü belirtir. Bu özellik, `/subsystemversion` derleyici anahtarıyla eşdeğerdir. Bu özelliğin varsayılan değeri hakkında daha fazla bilgi için bkz. [/subsystemversion (Visual Basic)](https://msdn.microsoft.com/library/08be22b2-f447-4cd3-8203-120b1b920b54) veya [/subsystemversion (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/a99fce81-9d92-4813-9874-bee777041445).|  
|TargetCompactFramework|Oluşturmakta olduğunuz uygulamayı çalıştırmak için gereken .NET Compact Framework sürümü. Bunu belirtmek, başka türlü başvuramayacak bazı Framework derlemelerine başvurmanıza olanak sağlar.|  
|TargetFrameworkVersion|[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]Oluşturmakta olduğunuz uygulamayı çalıştırmak için gereken sürümü. Bunu belirtmek, başka türlü başvuramayacak bazı Framework derlemelerine başvurmanıza olanak sağlar.|  
|TreatWarningsAsErrors|`true`Tüm uyarıların hata olarak işlenmesine neden olan bir Boole parametresi. Bu parametre, `/nowarn` derleyici anahtarıyla eşdeğerdir.|  
|UseHostCompilerIfAvailable|Varsa, derleme görevinin, varsa `true` işlem içi derleyici nesnesini kullanmasına neden olan bir Boole parametresi. Bu parametre yalnızca tarafından kullanılır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|Utf8Output|`true`, Derleyici ÇıKıŞıNı UTF-8 kodlaması kullanarak günlüğe kaydeden bir Boolean parametresi. Bu parametre, `/utf8Output` derleyici anahtarıyla eşdeğerdir.|  
|VbcToolPath|Geçerli vbc.exe sürümü geçersiz kılındığında vbc.exe başka bir konum belirten isteğe bağlı bir yol.|  
|Vbcayrıntı düzeyi|Derleyicinin çıkışının ayrıntı düzeyini belirtir [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] . Geçerli değerler şunlardır "sessiz," "normal" (varsayılan değer) veya "ayrıntılıdır."|  
|VisualStudioVersion|Bu projenin çalıştığı kabul edileceği Visual Studio sürümünü belirtir. Bu özellik belirtilmezse, MSBuild bunu makul bir varsayılan değere ayarlar.<br /><br /> Bu özellik, derleme için kullanılan hedef kümesini belirtmek için çeşitli proje türlerinde kullanılır. `ToolsVersion`Bir proje için 4,0 veya üzeri bir değere ayarlanırsa, `VisualStudioVersion` hangi alt araç takımını kullanacağınızı belirtmek için kullanılır. Daha fazla bilgi için bkz. [araç takımı (araçları sürümü)](../msbuild/msbuild-toolset-toolsversion.md).|  
|WarningsAsErrors|Hata olarak değerlendirmek için uyarıların listesini belirtir. Bu parametre, `/warnaserror` derleyici anahtarıyla eşdeğerdir.|  
|Warninggözetimi Taserrors|Hata olarak değerlendirilmediğini belirten uyarıların bir listesini belirtir. Bu parametre, `/warnaserror` derleyici anahtarıyla eşdeğerdir.|  
|Win32Manifest|Son derlemeye katıştırılması gereken bildirim dosyasının adı. Bu parametre, `/win32Manifest` derleyici anahtarıyla eşdeğerdir.|  
|Win32Resource|Son derlemeye katıştırılacak Win32 kaynağının dosya adı. Bu parametre, `/win32resource` derleyici anahtarıyla eşdeğerdir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ortak MSBuild proje öğeleri](../msbuild/common-msbuild-project-items.md)
