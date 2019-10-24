---
title: MSBuild görev başvurusu | Microsoft Docs
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00af44212dd142dd94629f886a50b9646488af3b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747278"
---
# <a name="msbuild-task-reference"></a>MSBuild görev başvurusu

Görevler, derleme işlemi sırasında çalışan kodu sağlar. Aşağıdaki listede yer alan görevler [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] eklenmiştir. @No__t_0 yüklendiğinde, [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] projeleri oluşturmak için kullanılan ek görevler vardır. Daha fazla bilgi için bkz [ C++ . görevler](../msbuild/msbuild-tasks-specific-to-visual-cpp.md).

Bu bölümdeki konularda listelenen parametrelere ek olarak, her görev aşağıdaki parametrelere de sahiptir:

| Parametre | Açıklama |
|-------------------| - |
| `Condition` | İsteğe bağlı `String` parametresi.<br /><br /> @No__t_1 altyapısının bu görevin yürütülüp yürütülmeyeceğini belirlemede kullandığı `Boolean` ifadesi. @No__t_0 tarafından desteklenen koşullar hakkında daha fazla bilgi için bkz. [koşullar](../msbuild/msbuild-conditions.md). |
| `ContinueOnError` | İsteğe bağlı parametre. , Aşağıdaki değerlerden birini içerebilir:<br /><br /> -   **WarnAndContinue** ya da **true**. Bir görev başarısız olduğunda, [hedef](../msbuild/target-element-msbuild.md) öğe ve yapı içindeki sonraki görevler yürütülmeye devam eder ve görevdeki tüm hatalar uyarı olarak kabul edilir.<br />-   **Errportadcontinue**. Bir görev başarısız olduğunda, `Target` öğesi ve derleme içindeki sonraki görevler yürütülmeye devam eder ve görevdeki tüm hatalar hata olarak değerlendirilir.<br />-   **Errportadstop** veya **false** (varsayılan). Bir görev başarısız olduğunda, `Target` öğesi ve derleme içindeki kalan görevler yürütülmez ve tüm `Target` öğesi ve derleme başarısız olduğu kabul edilir.<br /><br /> 4,5 öncesindeki .NET Framework sürümleri yalnızca `true` ve `false` değerlerini destekliyordu.<br /><br /> Daha fazla bilgi için bkz. [nasıl yapılır: görevlerdeki hataları yoksayma](../msbuild/how-to-ignore-errors-in-tasks.md). |

## <a name="in-this-section"></a>Bu bölümde

- [Görev temel sınıfı](../msbuild/task-base-class.md)

 @No__t_0 sınıfından türetilen görevlere birkaç parametre ekler.

- [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md)

 @No__t_0 sınıfından türetilen görevlere birkaç parametre ekler.

- [ToolTaskExtension temel sınıfı](../msbuild/tooltaskextension-base-class.md)

 @No__t_0 sınıfından türetilen görevlere birkaç parametre ekler.

- [AL (derleme bağlayıcı) görevi](../msbuild/al-assembly-linker-task.md)

 Modüller ya da kaynak dosyaları olan bir veya daha fazla dosyadan bildirime sahip bir derleme oluşturur.

- [AspNetCompiler görevi](../msbuild/aspnetcompiler-task.md)

 ASP.NET uygulamalarını önceden derlemeye yönelik bir yardımcı program olan *aspnet_compiler. exe*' yi kaydırır.

- [Atama kültür görevi](../msbuild/assignculture-task.md)

 Öğelere kültür tanımlayıcıları atar.

- [Atama ProjectConfiguration görevi](../msbuild/assignprojectconfiguration-task.md)

 Yapılandırma dizeleri listesini kabul eder ve bunları belirtilen projelere atar.

- [Atamatargetpath görevi](../msbuild/assigntargetpath-task.md)

 Dosya listesini kabul eder ve önceden belirtilmediyse `<TargetPath>` öznitelikleri ekler.

- [CallTarget görevi](../msbuild/calltarget-task.md)

 Proje dosyasında bir hedef çağırır.

- [CombinePath görevi](../msbuild/combinepath-task.md)

 Belirtilen yolları tek bir yol olarak birleştirir.

- [ConvertToAbsolutePath görevi](../msbuild/converttoabsolutepath-task.md)

 Göreli bir yolu veya başvuruyu mutlak bir yola dönüştürür.

- [Görevi Kopyala](../msbuild/copy-task.md)

 Dosyaları yeni bir konuma kopyalar.

- [CreateCSharpManifestResourceName görevi](../msbuild/createcsharpmanifestresourcename-task.md)

 Verilen bir *. resx* dosya adından veya başka bir kaynaktan [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] stili bir bildirim adı oluşturur.

- [CreateItem görevi](../msbuild/createitem-task.md)

 Öğe koleksiyonlarını giriş öğelerinden doldurur ve öğelerin bir listeden diğerine kopyalanmasını sağlar.

- [CreateProperty görevi](../msbuild/createproperty-task.md)

 Değerleri giriş değerlerinden doldurur ve değerlerin bir özellikten veya dizeden diğerine kopyalanmasını sağlar.

- [CreateVisualBasicManifestResourceName görevi](../msbuild/createvisualbasicmanifestresourcename-task.md)

 Verilen bir *. resx* dosya adından veya başka bir kaynaktan [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] stili bir bildirim adı oluşturur.

- [Csc görevi](../msbuild/csc-task.md)

 Yürütülebilir dosyalar, C# dinamik bağlantı kitaplıkları veya kod modülleri oluşturmak için Visual derleyicisini çağırır.

- [Görevi Sil](../msbuild/delete-task.md)

 Belirtilen dosyaları siler.

- [DownloadFile görevi](../msbuild/downloadfile-task.md)

 Belirtilen konuma bir dosya indirir.

- [Hata görevi](../msbuild/error-task.md)

 Bir derlemeyi durdurup değerlendirilen bir koşullu ifadeye göre bir hata kaydeder.

- [Exec görevi](../msbuild/exec-task.md)

 Belirtilen program veya komutu belirtilen bağımsız değişkenlerle çalıştırır.

- [FindAppConfigFile Görevi](../msbuild/findappconfigfile-task.md)

 Varsa, belirtilen listelerdeki *app. config* dosyasını bulur.

- [FindInList görevi](../msbuild/findinlist-task.md)

 Eşleşen itemspec içeren, belirtilen listedeki bir öğeyi bulur.

- [FindUnderPath görevi](../msbuild/findunderpath-task.md)

 Belirtilen öğe koleksiyonundaki hangi öğelerin belirtilen klasörde ve tüm alt klasörlerinde var olduğunu belirler.

- [FormatUrl görevi](../msbuild/formaturl-task.md)

 URL 'YI doğru URL biçimine dönüştürür.

- [FormatVersion görevi](../msbuild/formatversion-task.md)

 Sürüm numarasına Düzeltme numarasını ekler.

- [GenerateApplicationManifest görevi](../msbuild/generateapplicationmanifest-task.md)

 Bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama bildirimi veya yerel bildirim oluşturur.

- [GenerateBootstrapper görevi](../msbuild/generatebootstrapper-task.md)

 Bir uygulamayı ve önkoşullarını tespit etmek, indirmek ve yüklemek için otomatikleştirilmiş bir yol sağlar.

- [GenerateDeploymentManifest görevi](../msbuild/generatedeploymentmanifest-task.md)

 Bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtım bildirimi oluşturur.

- [GenerateResource Görevi](../msbuild/generateresource-task.md)

 *. Txt* ve *. resx* dosyalarını ortak dil çalışma zamanı ikili *. resources* dosyalarına dönüştürür.

- [GenerateTrustInfo görevi](../msbuild/generatetrustinfo-task.md)

 Temel bildirimden ve `TargetZone` ve `ExcludedPermissions` parametrelerinden uygulama güvenini oluşturur.

- [GetAssemblyIdentity görevi](../msbuild/getassemblyidentity-task.md)

 Belirtilen dosyalardaki derleme kimliklerini alır ve kimlik bilgilerini çıkarır.

- [GetFileHash görevi](../msbuild/getfilehash-task.md)

 Bir dosyanın veya dosya kümesinin içeriklerinin sağlama toplamlarını hesaplar.

- [GetFrameworkPath Görevi](../msbuild/getframeworkpath-task.md)

 .NET Framework derlemelerinin yolunu alır.

- [GetFrameworkSdkPath görevi](../msbuild/getframeworksdkpath-task.md)

 @No__t_0 yolunu alır.

- [GetReferenceAssemblyPaths görevi](../msbuild/getreferenceassemblypaths-task.md)

 Çeşitli çerçevelerin başvuru derleme yollarını döndürür.

- [LC görevi](../msbuild/lc-task.md)

 *. Licx* dosyasından bir *. License* dosyası oluşturur.

- [MakeDir görevi](../msbuild/makedir-task.md)

 Dizinler ve gerekirse herhangi bir üst dizin oluşturur.

- [İleti görevi](../msbuild/message-task.md)

 Derleme sırasında bir iletiyi günlüğe kaydeder.

- [Görevi taşı](../msbuild/move-task.md)

 Dosyaları yeni bir konuma taşıın.

- [MSBuild görevi](../msbuild/msbuild-task.md)

 Başka bir [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projesinden projeler [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] oluşturur.

- [ReadLinesFromFile Görevi](../msbuild/readlinesfromfile-task.md)

 Bir metin dosyasından öğelerin listesini okur.

- [RegisterAssembly görevi](../msbuild/registerassembly-task.md)

 Belirtilen derleme içindeki meta verileri okur ve gerekli girdileri kayıt defterine ekler.

- [RemoveDir Görevi](../msbuild/removedir-task.md)

 Belirtilen dizinleri ve tüm dosyalarını ve alt dizinlerini kaldırır.

- [Removeyinelemeler görevi](../msbuild/removeduplicates-task.md)

 Belirtilen öğe koleksiyonundan yinelenen öğeleri kaldırır.

- [RequiresFramework35SP1Assembly görevi](../msbuild/requiresframework35sp1assembly-task.md)

 Uygulamanın .NET Framework 3,5 SP1 gerektirip gerektirmediğini belirler.

- ResGen görevi

 Kullanımdan kalktı. *. Txt* ve *. resx* dosyalarını ortak dil çalışma zamanı ikili *. resources* dosyalarına dönüştürmek için [GenerateResource görev](../msbuild/generateresource-task.md) görevini kullanın.

- [ResolveAssemblyReference görevi](../msbuild/resolveassemblyreference-task.md)

 Belirtilen derlemelere bağlı tüm derlemeleri belirler.

- [ResolveComReference görevi](../msbuild/resolvecomreference-task.md)

 Bir veya daha fazla tür kitaplığı adının veya *. tlb* dosyasının bir listesini alır ve bu tür kitaplıklarını disk üzerindeki konumlara çözümler.

- [ResolveKeySource görevi](../msbuild/resolvekeysource-task.md)

 Tanımlayıcı ad anahtar kaynağını belirler

- [ResolveManifestFiles görevi](../msbuild/resolvemanifestfiles-task.md)

 Derleme işlemindeki aşağıdaki öğeleri bildirim oluşturma için dosyalara çözümler: oluşturulan öğeler, bağımlılıklar, uydu, içerik, hata ayıklama sembolleri ve belgeler.

- [ResolveNativeReference görevi](../msbuild/resolvenativereference-task.md)

 Yerel başvuruları çözümler.

- [ResolveNonMSBuildProjectOutput görevi](../msbuild/resolvenonmsbuildprojectoutput-task.md)

 MSBuild olmayan proje başvuruları için çıkış dosyalarını belirler.

- [SGen görevi](../msbuild/sgen-task.md)

 Belirtilen derlemedeki türler için bir XML serileştirme bütünleştirilmiş kodu oluşturur.

- [SignFile görevi](../msbuild/signfile-task.md)

 Belirtilen sertifikayı kullanarak belirtilen dosyayı imzalar.

- [Dokunma görevi](../msbuild/touch-task.md)

 Dosyaların erişim ve değiştirme zamanlarını ayarlar.

- [UnregisterAssembly görevi](../msbuild/unregisterassembly-task.md)

 Belirtilen derlemelerin COM birlikte çalışma amacıyla kaydını siler.

- [Sıkıştırılmış görev](../msbuild/unzip-task.md)

 Belirtilen konuma bir *. zip* arşivi olarak UnZIP.

- [UpdateManifest görevi](../msbuild/updatemanifest-task.md)

 Bir bildirimde seçili özellikleri güncelleştirir ve yeniden imzalar.

- [Vbc görevi](../msbuild/vbc-task.md)

 Yürütülebilir dosyalar, dinamik bağlantı kitaplıkları veya kod modülleri oluşturmak için Visual Basic derleyicisini çağırır..

- [VerifyFileHash görevi](../msbuild/verifyfilehash-task.md)

 Bir dosyanın beklenen dosya karmasıyla eşleştiğini doğrular.

- [Uyarı görevi](../msbuild/warning-task.md)

 Değerlendirilen bir koşullu ifadeye dayanan bir derleme sırasında bir uyarı kaydeder.

- [Writecobirleştirme görevi](../msbuild/writecodefragment-task.md)

 Belirtilen üretilen kod parçasını kullanarak geçici bir kod dosyası oluşturur. Dosyayı silmez.

- [WriteLinesToFile Görevi](../msbuild/writelinestofile-task.md)

 Belirtilen öğeleri belirtilen metin dosyasına yazar.

- [XmlPeek görevi](../msbuild/xmlpeek-task.md)

 XML dosyasından XPath sorgusuyla belirtilen değerleri döndürür.

- [XmlPoke Görevi](../msbuild/xmlpoke-task.md)

 Bir XPath sorgusu tarafından belirtilen değerleri bir XML dosyasına ayarlar.

- [XslTransformation görevi](../msbuild/xsltransformation-task.md)

 *Genişletilebilir Stil sayfası dil dönüşümü* (XSLT) veya derlenen XSLT kullanarak bir XML girişini dönüştürür ve çıkış cihazına veya bir dosyaya çıktılar verir.

- [ZipDirectory görevi](../msbuild/zipdirectory-task.md)

 Bir dizinin içeriğinden bir *. zip* arşivi oluşturur.

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [Görev yazma](../msbuild/task-writing.md)
- [Görevler](../msbuild/msbuild-tasks.md)