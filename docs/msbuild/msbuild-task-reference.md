---
title: MSBuild Görev Başvurusu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: b3144b27-a426-4259-b8ae-5f7991b202b6
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cbec3c7c020bae0e94bc16bdb1fe9740a36a93ae
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "78865329"
---
# <a name="msbuild-task-reference"></a>MSBuild görev başvurusu

Görevler, yapı işlemi sırasında çalışan kodu sağlar. Aşağıdaki listedeki görevler MSBuild'e dahildir. C++ iş yükü yüklendiğinde, C++ projeleri oluşturmak için kullanılan ek görevler kullanılabilir. Daha fazla bilgi için [C++ görevlerine](../msbuild/msbuild-tasks-specific-to-visual-cpp.md)bakın.

Bu bölümdeki konularda listelenen parametrelere ek olarak, her görevin de aşağıdaki parametreleri vardır:

| Parametre | Açıklama |
|-------------------| - |
| `Condition` | İsteğe bağlı `String` parametre.<br /><br /> `Boolean` MSBuild altyapısının bu görevin yürütülüp yürütülmeyeceğini belirlemek için kullandığı ifade. MSBuild tarafından desteklenen koşullar hakkında bilgi için [Koşullar'a](../msbuild/msbuild-conditions.md)bakın. |
| `ContinueOnError` | İsteğe bağlı parametre. Aşağıdaki değerlerden birini içerebilir:<br /><br /> -   **WarnAndContinue** veya **doğru**. Bir görev başarısız olduğunda, [Hedef](../msbuild/target-element-msbuild.md) öğe ve yapısonraki görevler yürütmeye devam eder ve görevden gelen tüm hatalar uyarı olarak kabul edilir.<br />-   **HataandContinue**. Bir görev başarısız olduğunda, `Target` öğe ve yapı sonraki görevler yürütmeye devam eder ve görevden tüm hatalar hata olarak kabul edilir.<br />-   **ErrorAndStop** veya **false** (varsayılan). Bir görev başarısız olduğunda, `Target` öğe ve yapıda kalan görevler yürütülmez ve tüm `Target` öğe ve yapı başarısız olmuş olarak kabul edilir.<br /><br /> .NET Framework'ün 4.5'ten önceki `true` `false` sürümleri yalnızca değerleri ve değerleri desteklemişti.<br /><br /> Daha fazla bilgi için [bkz: Görevlerdeki hataları yoksay.](../msbuild/how-to-ignore-errors-in-tasks.md) |

## <a name="in-this-section"></a>Bu bölümde

- [Görev taban sınıfı](../msbuild/task-base-class.md)

 <xref:Microsoft.Build.Utilities.Task> Sınıftan türeyen görevlere çeşitli parametreler ekler. Doğrudan kullanılmak üzere tasarlanmamıştır.

- [Görev Uzantısı taban sınıfı](../msbuild/taskextension-base-class.md)

 <xref:Microsoft.Build.Tasks.TaskExtension> Sınıftan türeyen görevlere çeşitli parametreler ekler. Doğrudan kullanılmak üzere tasarlanmamıştır.

- [ToolTaskExtension taban sınıfı](../msbuild/tooltaskextension-base-class.md)

 <xref:Microsoft.Build.Tasks.ToolTaskExtension> Sınıftan türeyen görevlere çeşitli parametreler ekler. Doğrudan kullanılmak üzere tasarlanmamıştır.

- [AL (Derleme Bağlayıcısı) görevi](../msbuild/al-assembly-linker-task.md)

 Modül veya kaynak dosyaları olan bir veya daha fazla dosyadan bir bildirim içeren bir derleme oluşturur.

- [AspNetCompiler görevi](../msbuild/aspnetcompiler-task.md)

 *aspnet_compiler.exe,* ASP.NET uygulamaları önceden derlemek için bir yardımcı program sarar.

- [AtamaKültür görevi](../msbuild/assignculture-task.md)

 Öğelere kültür tanımlayıcıları atar.

- [AtamaProjectConfiguration görev](../msbuild/assignprojectconfiguration-task.md)

 Yapılandırma dizeleri listesini kabul eder ve bunları belirtilen projelere atar.

- [TargetPath görevini atayın](../msbuild/assigntargetpath-task.md)

 Dosyaların listesini kabul eder `<TargetPath>` ve zaten belirtilmemişse öznitelikler ekler.

- [CallTarget görevi](../msbuild/calltarget-task.md)

 Proje dosyasındaki bir hedefi çağırır.

- [CombinePath görevi](../msbuild/combinepath-task.md)

 Belirtilen yolları tek bir yolda birleştirir.

- [ConvertToAbsolutePath görevi](../msbuild/converttoabsolutepath-task.md)

 Göreceli bir yolu veya başvuruyciyi mutlak bir yola dönüştürür.

- [Görevi kopyalama](../msbuild/copy-task.md)

 Dosyaları yeni bir konuma kopyalar.

- [CreateCSharpManifestResourceName görevi](../msbuild/createcsharpmanifestresourcename-task.md)

 Belirli bir *.resx* dosya adından veya başka bir kaynaktan C# stili bir bildirim adı oluşturur.

- [CreateItem görevi](../msbuild/createitem-task.md)

 Giriş öğelerinden madde koleksiyonlarını doldurarak maddelerin bir listeden diğerine kopyalanmasına izin verir.

- [CreateProperty görevi](../msbuild/createproperty-task.md)

 Değerleri bir özellik veya dizeden diğerine kopyalanmasını sağlayan giriş değerlerinden özellikleri doldurur.

- [CreateVisualBasicManifestResourceName görevi](../msbuild/createvisualbasicmanifestresourcename-task.md)

 Belirli bir *.resx* dosya adından veya başka bir kaynaktan Visual Basic tarzı bir bildirim adı oluşturur.

- [Csc görevi](../msbuild/csc-task.md)

 Yürütülebilir, dinamik bağlantı kitaplıkları veya kod modülleri üretmek için Visual C# derleyicisini çağırır.

- [Görevi silme](../msbuild/delete-task.md)

 Belirtilen dosyaları siler.

- [DownloadFile görevi](../msbuild/downloadfile-task.md)

 Bir dosyayı belirtilen konuma karşı karşıdan yükler.

- [Hata görevi](../msbuild/error-task.md)

 Yapıyı durdurur ve değerlendirilmiş koşullu deyimi temel alan bir hatayı günlüğe kaydeder.

- [Exec görev](../msbuild/exec-task.md)

 Belirtilen programı veya komutu belirtilen bağımsız değişkenlerle çalıştırın.

- [FindAppConfigFile görevi](../msbuild/findappconfigfile-task.md)

 Varsa *app.config* dosyasını sağlanan listelerde bulur.

- [FindInList görevi](../msbuild/findinlist-task.md)

 Eşleşen madde spec olan belirli bir listede bir öğe bulur.

- [FindUnderPath görevi](../msbuild/findunderpath-task.md)

 Belirtilen madde koleksiyonundaki hangi öğelerin belirtilen klasörde ve tüm alt klasörlerinde bulunduğunu belirler.

- [FormatUrl görevi](../msbuild/formaturl-task.md)

 URL'yi doğru URL biçimine dönüştürür.

- [FormatVersion görevi](../msbuild/formatversion-task.md)

 Düzeltme numarasını sürüm numarasına ekler.

- [GenerateApplicationManifest görevi](../msbuild/generateapplicationmanifest-task.md)

 ClickOnce uygulama bildirimi veya yerel bir bildirim oluşturur.

- [GenerateBootstrapper görevi](../msbuild/generatebootstrapper-task.md)

 Bir uygulamayı ve ön koşulları algılamak, indirmek ve yüklemek için otomatik bir yol sağlar.

- [DeploymentManifest görev oluşturma](../msbuild/generatedeploymentmanifest-task.md)

 ClickOnce dağıtım bildirimi oluşturur.

- [Kaynak oluşturma görevi](../msbuild/generateresource-task.md)

 *.txt* ve *.resx* dosyalarını ortak dil çalışma zamanı ikili *.kaynaklar* dosyalarına dönüştürür.

- [GenerateTrustInfo görevi](../msbuild/generatetrustinfo-task.md)

 Temel bildirimden ve `TargetZone` `ExcludedPermissions` parametrelerden uygulama güvenini oluşturur.

- [GetAssemblyIdentity görevi](../msbuild/getassemblyidentity-task.md)

 Belirtilen dosyalardan derleme kimliklerini alır ve kimlik bilgilerini çıkarır.

- [GetFileHash görev](../msbuild/getfilehash-task.md)

 Bir dosyanın veya dosya kümesinin içeriğinin denetimlerini hesaplar.

- [GetFrameworkPath görevi](../msbuild/getframeworkpath-task.md)

 .NET Framework derlemelerine giden yolu alır.

- [GetFrameworkSdkPath görevi](../msbuild/getframeworksdkpath-task.md)

 Windows Yazılım Geliştirme Kiti'ne (SDK) giden yolu alır.

- [GetReferenceAssemblyPaths görev](../msbuild/getreferenceassemblypaths-task.md)

 Çeşitli çerçevelerin başvuru derleme yollarını döndürür.

- [LC görevi](../msbuild/lc-task.md)

 *Bir .licx* dosyasından *bir .license* dosyası oluşturur.

- [MakeDir görevi](../msbuild/makedir-task.md)

 Dizinler ve gerekirse herhangi bir üst dizin oluşturur.

- [İleti görevi](../msbuild/message-task.md)

 Yapı sırasında bir iletiyi günlüğe kaydeder.

- [Taşıma görevi](../msbuild/move-task.md)

 Dosyaları yeni bir konuma taşır.

- [MSBuild görevi](../msbuild/msbuild-task.md)

 Başka bir MSBuild projesinden MSBuild projeleri oluşturur.

- [ReadLinesFromFile görevi](../msbuild/readlinesfromfile-task.md)

 Metin dosyasından öğelerin listesini okur.

- [RegisterAssembly görevi](../msbuild/registerassembly-task.md)

 Belirtilen derleme içindeki meta verileri okur ve gerekli girişleri kayıt defterine ekler.

- [KaldırmaDir görevi](../msbuild/removedir-task.md)

 Belirtilen dizinleri ve tüm dosya larını ve alt dizinlerini kaldırır.

- [RemoveDuplicates görevi](../msbuild/removeduplicates-task.md)

 Yinelenen öğeleri belirtilen madde koleksiyonundan kaldırır.

- [RequiresFramework35SP1Assembly görevi](../msbuild/requiresframework35sp1assembly-task.md)

 Uygulamanın .NET Framework 3.5 SP1 gerekip gerekmediğini belirler.

- ResGen Görevi

 Kullanımdan kalktı. *.txt* ve *.resx* dosyalarını ortak dil çalışma zamanı ikili *.kaynaklar* dosyalarına dönüştürmek için [Kaynak Oluşturma görev](../msbuild/generateresource-task.md) görevini kullanın.

- [ResolveAssemblyReference görevi](../msbuild/resolveassemblyreference-task.md)

 Belirtilen derlemelere bağlı tüm derlemeleri belirler.

- [ResolveComReference görevi](../msbuild/resolvecomreference-task.md)

 Bir veya daha fazla tür kitaplık adlarının veya *.tlb* dosyalarının listesini alır ve bu tür kitaplıklarını diskteki konumlara giderir.

- [ResolveKeySource görevi](../msbuild/resolvekeysource-task.md)

 Güçlü ad anahtar kaynağını belirler

- [ManifestFiles görevini çözümle](../msbuild/resolvemanifestfiles-task.md)

 Yapı işleminde aşağıdaki öğeleri bildirim oluşturma dosyalarıyla giderir: yerleşik öğeler, bağımlılıklar, uydular, içerik, hata ayıklama sembolleri ve belgeler.

- [ResolveNativeReference görevi](../msbuild/resolvenativereference-task.md)

 Yerel başvuruları çözer.

- [ResolveNonMSBuildProjectOutput görevi](../msbuild/resolvenonmsbuildprojectoutput-task.md)

 MSBuild olmayan proje başvuruları için çıktı dosyalarını belirler.

- [SGen görevi](../msbuild/sgen-task.md)

 Belirtilen derlemedeki türler için bir XML serileştirme derlemesi oluşturur.

- [SignFile görevi](../msbuild/signfile-task.md)

 Belirtilen sertifikayı kullanarak belirtilen dosyayı işaretler.

- [Dokunma görevi](../msbuild/touch-task.md)

 Dosyaların erişim ve değişiklik saatlerini ayarlar.

- [UnregisterAssembly görevi](../msbuild/unregisterassembly-task.md)

 Com interop amaçları için belirtilen derlemeleri kayıt dışı kalır.

- [Zip'i açma görevi](../msbuild/unzip-task.md)

 Bir *.zip* arşivini belirtilen konuma ait olarak unzips.

- [UpdateManifest görevi](../msbuild/updatemanifest-task.md)

 Seçili özellikleri bir bildirimde güncelleştirir ve istifa eder.

- [Vbc görevi](../msbuild/vbc-task.md)

 Yürütülebilir, dinamik bağlantı kitaplıkları veya kod modülleri üretmek için Visual Basic derleyicisini çağırır...

- [VerifyFileHash görev](../msbuild/verifyfilehash-task.md)

 Bir dosyanın beklenen dosya karmaile eşleştiğini doğrular.

- [Uyarı görevi](../msbuild/warning-task.md)

 Değerlendirilmiş koşullu bir bildirime dayalı bir yapı sırasında bir uyarı yığlar.

- [WriteCodeFragment görevi](../msbuild/writecodefragment-task.md)

 Belirtilen oluşturulan kod parçasını kullanarak geçici bir kod dosyası oluşturur. Dosyayı silmez.

- [WriteLinesToFile görev](../msbuild/writelinestofile-task.md)

 Belirtilen öğeleri belirtilen metin dosyasına yazar.

- [XmlPeek görevi](../msbuild/xmlpeek-task.md)

 XML dosyasından XPath sorgusutarafından belirtilen değerleri döndürür.

- [XmlPoke görevi](../msbuild/xmlpoke-task.md)

 XPath sorgusunda belirtilen değerleri XML dosyasına ayarlar.

- [XslTransformation görevi](../msbuild/xsltransformation-task.md)

 *Genişletilebilir Stylesheet Language Transformation* (XSLT) veya derlenmiş XSLT ve çıktıları kullanarak bir XML girdisini bir çıktı aygıtına veya dosyaya dönüştürür.

- [ZipDirectory görev](../msbuild/zipdirectory-task.md)

 Bir dizinin içeriğinden *bir .zip* arşivi oluşturur.

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [Görev yazma](../msbuild/task-writing.md)
- [Görevler](../msbuild/msbuild-tasks.md)
