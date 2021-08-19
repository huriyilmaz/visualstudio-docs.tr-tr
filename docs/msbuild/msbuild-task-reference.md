---
title: MSBuild Görev Başvurusu | Microsoft Docs
description: Derleme işlemi sırasında çalışan kod sağlayan MSBuild görevler hakkında bilgi öğrenin.
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
ms.openlocfilehash: 9c5dea7c359de1c6bb07b9d8f6a60625e87029e8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122143072"
---
# <a name="msbuild-task-reference"></a>MSBuild görev başvurusu

Görevler, derleme işlemi sırasında çalışan kodu sağlar. Aşağıdaki listede yer alan görevler, aşağıdaki MSBuild. C++ iş yükü yüklenirken, C++ projelerini derlemek için kullanılan ek görevler kullanılabilir. Daha fazla bilgi için bkz. [C++ görevleri.](../msbuild/msbuild-tasks-specific-to-visual-cpp.md)

Bu bölümdeki konu başlıklarında listelenen parametrelere ek olarak, her görev de aşağıdaki parametrelere sahip olur:

| Parametre | Açıklama |
|-------------------| - |
| `Condition` | İsteğe `String` bağlı parametre.<br /><br /> MSBuild `Boolean` altyapısının bu görevin yürütülecek olup olmadığını belirlemek için kullandığı ifade. MSBuild tarafından desteklenen koşullar hakkında bilgi için bkz. [Koşullar.](../msbuild/msbuild-conditions.md) |
| `ContinueOnError` | İsteğe bağlı parametre. Aşağıdaki değerlerden birini içerebilir:<br /><br /> -   **WarnAndContinue veya** **true**. Bir görev başarısız olduğunda, [Target](../msbuild/target-element-msbuild.md) öğesinde ve derlemede sonraki görevler yürütülebilir ve görevdeki tüm hatalar uyarı olarak kabul edilir.<br />-   **ErrorAndContinue**. Bir görev başarısız olduğunda, öğesinde ve derlemede sonraki görevler yürütülebilir ve görevdeki tüm `Target` hatalar hata olarak kabul edilir.<br />-   **ErrorAndStop** veya **false** (varsayılan). Bir görev başarısız olduğunda, öğesinde ve derlemede kalan görevler yürütülmez ve tüm öğe ile `Target` `Target` derlemenin başarısız olduğu kabul edilir.<br /><br /> 4.5'.NET Framework önceki sürümler yalnızca ve `true` değerlerini `false` destekler.<br /><br /> Daha fazla bilgi için, [bkz. How to: Ignore errors in tasks](../msbuild/how-to-ignore-errors-in-tasks.md). |

## <a name="in-this-section"></a>Bu bölümde

- [Görev temel sınıfı](../msbuild/task-base-class.md)

 sınıfından türetilen görevlere birkaç parametre <xref:Microsoft.Build.Utilities.Task> ekler. Doğrudan kullanılmaya yönelik değildir.

- [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md)

 sınıfından türetilen görevlere birkaç parametre <xref:Microsoft.Build.Tasks.TaskExtension> ekler. Doğrudan kullanılmaya yönelik değildir.

- [ToolTaskExtension temel sınıfı](../msbuild/tooltaskextension-base-class.md)

 sınıfından türetilen görevlere birkaç parametre <xref:Microsoft.Build.Tasks.ToolTaskExtension> ekler. Doğrudan kullanılmaya yönelik değildir.

- [AL (Derleme Bağlayıcı) görevi](../msbuild/al-assembly-linker-task.md)

 Modül veya kaynak dosyası olan bir veya daha fazla dosyadan bildirimle bir derleme oluşturur.

- [AspNetCompiler görevi](../msbuild/aspnetcompiler-task.md)

 Uygulamaları *aspnet_compiler.exe* derlemek için bir yardımcı program olan ASP.NET sarmalar.

- [AssignCulture görevi](../msbuild/assignculture-task.md)

 Öğelere kültür tanımlayıcıları atar.

- [AssignProjectConfiguration görevi](../msbuild/assignprojectconfiguration-task.md)

 Yapılandırma dizelerinin listesini kabul eder ve bunları belirtilen projelere atar.

- [AssignTargetPath görevi](../msbuild/assigntargetpath-task.md)

 Dosya listesini kabul eder ve `<TargetPath>` önceden belirtilmemişse öznitelikler ekler.

- [CallTarget görevi](../msbuild/calltarget-task.md)

 Proje dosyasında bir hedef çağırır.

- [CombinePath görevi](../msbuild/combinepath-task.md)

 Belirtilen yolları tek bir yolda birleştirir.

- [ConvertToAbsolutePath görevi](../msbuild/converttoabsolutepath-task.md)

 Göreli bir yolu veya başvuruyı mutlak yola dönüştürür.

- [Kopyalama görevi](../msbuild/copy-task.md)

 Dosyaları yeni bir konuma kopyalar.

- [CreateCSharpManifestResourceName görevi](../msbuild/createcsharpmanifestresourcename-task.md)

 Belirli bir *.resx* dosya adı veya başka bir kaynaktan C# stili bir bildirim adı oluşturur.

- [CreateItem görevi](../msbuild/createitem-task.md)

 Giriş öğelerinden öğe koleksiyonlarını doldurmak, öğelerin bir listeden diğerine kopyalanır.

- [CreateProperty görevi](../msbuild/createproperty-task.md)

 Giriş değerlerinden özellikleri tamamlar ve değerlerin bir özellikten veya dizeden diğerine kopyalanır.

- [CreateVisualBasicManifestResourceName görevi](../msbuild/createvisualbasicmanifestresourcename-task.md)

 Belirli Visual Basic *.resx* dosya adı veya başka bir kaynaktan bir bildirim adı oluşturur.

- [Csc görevi](../msbuild/csc-task.md)

 Yürütülebilir dosyalar, dinamik bağlantı kitaplıkları veya kod modülleri üretmek için Visual C# derleyiciyi çağırır.

- [Silme görevi](../msbuild/delete-task.md)

 Belirtilen dosyaları siler.

- [DownloadFile görevi](../msbuild/downloadfile-task.md)

 Belirtilen konuma bir dosya indirir.

- [Hata görevi](../msbuild/error-task.md)

 Bir derlemeyi durdurur ve değerlendirilen koşullu deyime göre bir hatayı günlüğe kaydeder.

- [Yürütme görevi](../msbuild/exec-task.md)

 Belirtilen programı veya komutu belirtilen bağımsız değişkenlerle çalıştırır.

- [FindAppConfigFile görevi](../msbuild/findappconfigfile-task.md)

 Sağlanan *app.config* varsa, bir dosya bulur.

- [FindInList görevi](../msbuild/findinlist-task.md)

 Belirtilen listede eşleşen itemspec'e sahip bir öğe bulur.

- [FindUnderPath görevi](../msbuild/findunderpath-task.md)

 Belirtilen öğe koleksiyonunda hangi öğelerin belirtilen klasörde ve tüm alt klasörlerde mevcut olduğunu belirler.

- [FormatUrl görevi](../msbuild/formaturl-task.md)

 BIR URL'yi doğru URL biçimine dönüştürür.

- [FormatVersion görevi](../msbuild/formatversion-task.md)

 Sürüm numarasına düzeltme numarasını ekler.

- [GenerateApplicationManifest görevi](../msbuild/generateapplicationmanifest-task.md)

 Uygulama bildirimi ClickOnce yerel bir bildirim üretir.

- [GenerateBootstrapper görevi](../msbuild/generatebootstrapper-task.md)

 Bir uygulamayı ve bunun önkoşullarını algılamak, indirmek ve yüklemek için otomatik bir yol sağlar.

- [GenerateDeploymentManifest görevi](../msbuild/generatedeploymentmanifest-task.md)

 Bir dağıtım ClickOnce bildirimi üretir.

- [GenerateResource görevi](../msbuild/generateresource-task.md)

 .resx *.txt* *ve .resx* dosyalarını ortak dil çalışma zamanı ikili *.resources dosyalarına* dönüştürür.

- [GenerateTrustInfo görevi](../msbuild/generatetrustinfo-task.md)

 Uygulama güvenini temel bildirimden ve ve `TargetZone` parametrelerinden `ExcludedPermissions` üretir.

- [GetAssemblyIdentity görevi](../msbuild/getassemblyidentity-task.md)

 Belirtilen dosyalardan derleme kimliklerini almak ve kimlik bilgilerini çıkarmak.

- [GetFileHash görevi](../msbuild/getfilehash-task.md)

 Bir dosyanın veya dosya kümesi içeriğinin sağlama toplamlarını hesaplama.

- [GetFrameworkPath görevi](../msbuild/getframeworkpath-task.md)

 Uygulama derlemelerinin yolunu .NET Framework.

- [GetFrameworkSdkPath görevi](../msbuild/getframeworksdkpath-task.md)

 Windows Software Development Kit(SDK) yolunu alır.

- [GetReferenceAssemblyPaths görevi](../msbuild/getreferenceassemblypaths-task.md)

 Çeşitli çerçevelerin başvuru derleme yollarını döndürür.

- [LC görevi](../msbuild/lc-task.md)

 Bir *.licx* dosyasından .license dosyası üretir. 

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

 Belirtilen derleme içindeki meta verileri okur ve gerekli girdileri kayıt defterine ekler.

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

 Belirtilen derlemede türler için bir XML serileştirme derlemesi oluşturur.

- [SignFile görevi](../msbuild/signfile-task.md)

 Belirtilen sertifikayı kullanarak belirtilen dosyayı imzalar.

- [Dokunma görevi](../msbuild/touch-task.md)

 Dosyaların erişim ve değişiklik zamanlarını ayarlar.

- [UnregisterAssembly görevi](../msbuild/unregisterassembly-task.md)

 Com birlikte çalışma amacıyla belirtilen derlemeleri geri alma.

- [Unzip görevi](../msbuild/unzip-task.md)

 Belirtilen konuma *.zip* arşivini açar.

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
