---
title: MSBuild Görev başvurusu | Microsoft Docs
description: yapı işlemi sırasında çalışan kodu sağlayan MSBuild eklenen görevler hakkında bilgi edinin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 5f6d8c4d7907da705de8f204f93c007c13b2e67749f3bc089fc48ee674909a8b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121397520"
---
# <a name="msbuild-task-reference"></a>MSBuild görev başvurusu

Görevler, derleme işlemi sırasında çalışan kodu sağlar. Aşağıdaki listede yer alan görevler MSBuild eklenmiştir. C++ iş yükü yüklendiğinde, C++ projelerini derlemek için kullanılan ek görevler vardır. Daha fazla bilgi için bkz. [C++ görevleri](../msbuild/msbuild-tasks-specific-to-visual-cpp.md).

Bu bölümdeki konularda listelenen parametrelere ek olarak, her görev aşağıdaki parametrelere de sahiptir:

| Parametre | Açıklama |
|-------------------| - |
| `Condition` | İsteğe bağlı `String` parametre.<br /><br /> `Boolean`MSBuild altyapısının bu görevin yürütülüp yürütülmeyeceğini belirlemede kullandığı bir ifade. MSBuild tarafından desteklenen koşullar hakkında daha fazla bilgi için bkz. [koşullar](../msbuild/msbuild-conditions.md). |
| `ContinueOnError` | İsteğe bağlı parametre. , Aşağıdaki değerlerden birini içerebilir:<br /><br /> -   **WarnAndContinue** veya **true**. Bir görev başarısız olduğunda, [hedef](../msbuild/target-element-msbuild.md) öğe ve yapı içindeki sonraki görevler yürütülmeye devam eder ve görevdeki tüm hatalar uyarı olarak kabul edilir.<br />-   **Errportadcontinue**. Bir görev başarısız olduğunda, öğedeki sonraki görevler `Target` ve derleme yürütülmeye devam eder ve görevdeki tüm hatalar hata olarak değerlendirilir.<br />-   **Errportadstop** veya **false** (varsayılan). Bir görev başarısız olduğunda, öğe ve yapı içindeki kalan görevler `Target` yürütülmez ve tüm `Target` öğe ve derleme başarısız olarak kabul edilir.<br /><br /> 4,5 ' den önceki .NET Framework sürümleri yalnızca `true` ve değerlerini destekliyordu `false` .<br /><br /> Daha fazla bilgi için bkz. [nasıl yapılır: görevlerdeki hataları yoksayma](../msbuild/how-to-ignore-errors-in-tasks.md). |

## <a name="in-this-section"></a>Bu bölümde

- [Görev temel sınıfı](../msbuild/task-base-class.md)

 Sınıfından türetilen görevlere birkaç parametre ekler <xref:Microsoft.Build.Utilities.Task> . Doğrudan kullanılmaya yönelik değildir.

- [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md)

 Sınıfından türetilen görevlere birkaç parametre ekler <xref:Microsoft.Build.Tasks.TaskExtension> . Doğrudan kullanılmaya yönelik değildir.

- [ToolTaskExtension temel sınıfı](../msbuild/tooltaskextension-base-class.md)

 Sınıfından türetilen görevlere birkaç parametre ekler <xref:Microsoft.Build.Tasks.ToolTaskExtension> . Doğrudan kullanılmaya yönelik değildir.

- [AL (Derleme Bağlayıcı) görevi](../msbuild/al-assembly-linker-task.md)

 Modüller ya da kaynak dosyaları olan bir veya daha fazla dosyadan bildirime sahip bir derleme oluşturur.

- [AspNetCompiler görevi](../msbuild/aspnetcompiler-task.md)

 ASP.NET uygulamaları önceden derlemeye yönelik bir yardımcı program olan *aspnet_compiler.exe* sarmalanmış.

- [AssignCulture görevi](../msbuild/assignculture-task.md)

 Öğelere kültür tanımlayıcıları atar.

- [AssignProjectConfiguration görevi](../msbuild/assignprojectconfiguration-task.md)

 Yapılandırma dizeleri listesini kabul eder ve bunları belirtilen projelere atar.

- [AssignTargetPath görevi](../msbuild/assigntargetpath-task.md)

 Dosya listesini kabul eder ve `<TargetPath>` henüz belirtilmemişse öznitelikleri ekler.

- [CallTarget görevi](../msbuild/calltarget-task.md)

 Proje dosyasında bir hedef çağırır.

- [CombinePath görevi](../msbuild/combinepath-task.md)

 Belirtilen yolları tek bir yol olarak birleştirir.

- [ConvertToAbsolutePath görevi](../msbuild/converttoabsolutepath-task.md)

 Göreli bir yolu veya başvuruyu mutlak bir yola dönüştürür.

- [Kopyalama görevi](../msbuild/copy-task.md)

 Dosyaları yeni bir konuma kopyalar.

- [CreateCSharpManifestResourceName görevi](../msbuild/createcsharpmanifestresourcename-task.md)

 Verilen *. resx* dosya adından veya diğer kaynaklardan C# stili bir bildirim adı oluşturur.

- [CreateItem görevi](../msbuild/createitem-task.md)

 Öğe koleksiyonlarını giriş öğelerinden doldurur ve öğelerin bir listeden diğerine kopyalanmasını sağlar.

- [CreateProperty görevi](../msbuild/createproperty-task.md)

 Değerleri giriş değerlerinden doldurur ve değerlerin bir özellikten veya dizeden diğerine kopyalanmasını sağlar.

- [CreateVisualBasicManifestResourceName görevi](../msbuild/createvisualbasicmanifestresourcename-task.md)

 verilen bir *. resx* dosya adından veya başka bir kaynaktan Visual Basic stili bir bildirim adı oluşturur.

- [Csc görevi](../msbuild/csc-task.md)

 Yürütülebilir dosyalar, dinamik bağlantı kitaplıkları veya kod modülleri oluşturmak için Visual C# derleyicisini çağırır.

- [Silme görevi](../msbuild/delete-task.md)

 Belirtilen dosyaları siler.

- [DownloadFile görevi](../msbuild/downloadfile-task.md)

 Belirtilen konuma bir dosya indirir.

- [Hata görevi](../msbuild/error-task.md)

 Bir derlemeyi durdurup değerlendirilen bir koşullu ifadeye göre bir hata kaydeder.

- [Yürütme görevi](../msbuild/exec-task.md)

 Belirtilen program veya komutu belirtilen bağımsız değişkenlerle çalıştırır.

- [FindAppConfigFile görevi](../msbuild/findappconfigfile-task.md)

 Varsa, belirtilen listelerdeki *app.config* dosyasını bulur.

- [FindInList görevi](../msbuild/findinlist-task.md)

 Eşleşen itemspec içeren, belirtilen listedeki bir öğeyi bulur.

- [FindUnderPath görevi](../msbuild/findunderpath-task.md)

 Belirtilen öğe koleksiyonundaki hangi öğelerin belirtilen klasörde ve tüm alt klasörlerinde var olduğunu belirler.

- [FormatUrl görevi](../msbuild/formaturl-task.md)

 URL 'YI doğru URL biçimine dönüştürür.

- [FormatVersion görevi](../msbuild/formatversion-task.md)

 Sürüm numarasına Düzeltme numarasını ekler.

- [GenerateApplicationManifest görevi](../msbuild/generateapplicationmanifest-task.md)

 bir ClickOnce uygulama bildirimi veya yerel bildirim oluşturur.

- [GenerateBootstrapper görevi](../msbuild/generatebootstrapper-task.md)

 Bir uygulamayı ve önkoşullarını tespit etmek, indirmek ve yüklemek için otomatikleştirilmiş bir yol sağlar.

- [GenerateDeploymentManifest görevi](../msbuild/generatedeploymentmanifest-task.md)

 bir ClickOnce dağıtım bildirimi oluşturur.

- [GenerateResource görevi](../msbuild/generateresource-task.md)

 *.txt* ve *. resx* dosyalarını ortak dil çalışma zamanı ikili *. resources* dosyalarına dönüştürür.

- [GenerateTrustInfo görevi](../msbuild/generatetrustinfo-task.md)

 Temel bildirimden ve ve parametrelerinden uygulama güvenini oluşturur `TargetZone` `ExcludedPermissions` .

- [GetAssemblyIdentity görevi](../msbuild/getassemblyidentity-task.md)

 Belirtilen dosyalardaki derleme kimliklerini alır ve kimlik bilgilerini çıkarır.

- [GetFileHash görevi](../msbuild/getfilehash-task.md)

 Bir dosyanın veya dosya kümesinin içeriklerinin sağlama toplamlarını hesaplar.

- [GetFrameworkPath görevi](../msbuild/getframeworkpath-task.md)

 .NET Framework derlemelerinin yolunu alır.

- [GetFrameworkSdkPath görevi](../msbuild/getframeworksdkpath-task.md)

 Windows yazılım geliştirme seti (SDK) yolunu alır.

- [GetReferenceAssemblyPaths görevi](../msbuild/getreferenceassemblypaths-task.md)

 Çeşitli çerçevelerin başvuru derleme yollarını döndürür.

- [LC görevi](../msbuild/lc-task.md)

 Bir *.licx* dosyasından bir .license dosyası üretir. 

- [MakeDir görevi](../msbuild/makedir-task.md)

 Dizinler ve gerekirse herhangi bir üst dizin oluşturur.

- [İleti görevi](../msbuild/message-task.md)

 Derleme sırasında bir iletiyi günlüğe kaydeder.

- [Taşıma görevi](../msbuild/move-task.md)

 Dosyaları yeni bir konuma taşır.

- [MSBuild görevi](../msbuild/msbuild-task.md)

 Başka bir MSBuild projeden bir MSBuild derlemesi.

- [ReadLinesFromFile görevi](../msbuild/readlinesfromfile-task.md)

 Bir metin dosyasındaki öğelerin listesini okur.

- [RegisterAssembly görevi](../msbuild/registerassembly-task.md)

 Belirtilen derleme içindeki meta verileri okur ve kayıt defterine gerekli girişleri ekler.

- [RemoveDir görevi](../msbuild/removedir-task.md)

 Belirtilen dizinleri ve tüm dosyalarını ve alt dizinlerini kaldırır.

- [RemoveDuplicates görevi](../msbuild/removeduplicates-task.md)

 Belirtilen öğe koleksiyonundan yinelenen öğeleri kaldırır.

- [RequiresFramework35SP1Assembly görevi](../msbuild/requiresframework35sp1assembly-task.md)

 Uygulamanın 3.5 SP1 .NET Framework gerekip gerek olmadığını belirler.

- ResGen Görevi

 Kullanımdan kalktı. [GenerateResource görev görevini](../msbuild/generateresource-task.md) kullanarak .txtve *.resx* dosyalarını ortak dil çalışma zamanı ikili .resources dosyalarına *ve dosyalarına dönüştürebilirsiniz.*

- [ResolveAssemblyReference görevi](../msbuild/resolveassemblyreference-task.md)

 Belirtilen derlemelere bağımlı olan tüm derlemeleri belirler.

- [ResolveComReference görevi](../msbuild/resolvecomreference-task.md)

 Bir veya daha fazla tür kitaplığı adı veya *.tlb* dosyası listesini alır ve bu tür kitaplıklarını diskte konumlara çözümler.

- [ResolveKeySource görevi](../msbuild/resolvekeysource-task.md)

 Güçlü ad anahtar kaynağını belirler

- [ResolveManifestFiles görevi](../msbuild/resolvemanifestfiles-task.md)

 Derleme sürecindeki aşağıdaki öğeleri bildirim oluşturma dosyalarına çözümler: derleme öğeleri, bağımlılıklar, uydular, içerik, hata ayıklama sembolleri ve belgeler.

- [ResolveNativeReference görevi](../msbuild/resolvenativereference-task.md)

 Yerel başvuruları çözümler.

- [ResolveNonMSBuildProjectOutput görevi](../msbuild/resolvenonmsbuildprojectoutput-task.md)

 Proje dışı başvurular için çıkış MSBuild belirler.

- [SGen görevi](../msbuild/sgen-task.md)

 Belirtilen derlemede türleri için bir XML serileştirme derlemesi oluşturur.

- [SignFile görevi](../msbuild/signfile-task.md)

 Belirtilen sertifikayı kullanarak belirtilen dosyayı imzalar.

- [Dokunma görevi](../msbuild/touch-task.md)

 Dosyaların erişim ve değişiklik zamanlarını ayarlar.

- [UnregisterAssembly görevi](../msbuild/unregisterassembly-task.md)

 Belirtilen derlemeleri COM birlikte çalışma amaçlarıyla geri alma.

- [Unzip görevi](../msbuild/unzip-task.md)

 Bir dosya *.zip* belirtilen konuma açar.

- [UpdateManifest görevi](../msbuild/updatemanifest-task.md)

 Bir bildirimde seçili özellikleri güncelleştirme ve yeniden atama.

- [Vbc görevi](../msbuild/vbc-task.md)

 Yürütülebilir Visual Basic, dinamik bağlantı kitaplıkları veya kod modülleri üretmek için Visual Basic derleyiciyi çağırır.

- [VerifyFileHash görevi](../msbuild/verifyfilehash-task.md)

 Bir dosyanın beklenen dosya karmasıyla eş olduğunu doğrular.

- [Uyarı görevi](../msbuild/warning-task.md)

 Değerlendirilen koşullu deyimi temel alan bir derleme sırasında bir uyarıyı günlüğe kaydeder.

- [WriteCodeFragment görevi](../msbuild/writecodefragment-task.md)

 Belirtilen oluşturulan kod parçasını kullanarak geçici bir kod dosyası üretir. Dosyayı silemez.

- [WriteLinesToFile görevi](../msbuild/writelinestofile-task.md)

 Belirtilen öğeleri belirtilen metin dosyasına yazar.

- [XmlPeek görevi](../msbuild/xmlpeek-task.md)

 Xml dosyasından XPath sorgusu tarafından belirtilen değerleri döndürür.

- [XmlPoke görevi](../msbuild/xmlpoke-task.md)

 Değerleri bir XPath sorgusu tarafından belirtilen şekilde bir XML dosyasına ayarlar.

- [XslTransformation görevi](../msbuild/xsltransformation-task.md)

 Xml girişini bir Genişletilebilir *Stil* Sayfası Dil Dönüşümü (XSLT) veya derlenmiş XSLT kullanarak ve çıkışları bir çıkış cihazına veya dosyaya dönüştürer.

- [ZipDirectory görevi](../msbuild/zipdirectory-task.md)

 Dizinin *.zip* bir arşiv oluşturur.

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [Görev yazma](../msbuild/task-writing.md)
- [Görevler](../msbuild/msbuild-tasks.md)
