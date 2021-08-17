---
title: GenerateDeploymentManifest Görev | Microsoft Docs
description: MSBuild GenerateDeploymentManifest görevini kullanarak bir dağıtım bildirimi ClickOnce öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateDeploymentManifest
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateDeploymentManifest task
- GenerateDeploymentManifest task [MSBuild]
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 06b40841507812d7d2892a57f24995f580c8be9a3e79c52286835336f462390f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121427840"
---
# <a name="generatedeploymentmanifest-task"></a>GenerateDeploymentManifest görevi

Bir dağıtım ClickOnce bildirimi üretir. Bir ClickOnce dağıtım bildirimi, dağıtım için benzersiz bir kimlik tanımlayarak, yükleme veya çevrimiçi mod gibi dağıtım özelliklerini belirleyerek, uygulama güncelleştirme ayarlarını ve güncelleştirme konumlarını belirterek ve ilgili uygulama bildirimini ClickOnce dağıtımını açıklar.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda görevin parametreleri açık `GenerateDeploymentManifest` almaktadır.

| Parametre | Açıklama |
|--------------------------| - |
| `AssemblyName` | İsteğe `String` bağlı parametre.<br /><br /> Oluşturulan `Name` bildirim için derleme kimliğinin alanını belirtir. Bu parametre belirtilmezse, adı veya `EntryPoint` parametrelerinden `InputManifest` belirtilir. Ad anılamazsa görev bir hata verir. |
| `AssemblyVersion` | İsteğe `String` bağlı parametre.<br /><br /> Oluşturulan `Version` bildirim için derleme kimliğinin alanını belirtir. Bu parametre belirtilmezse, görev "1.0.0.0" değerini kullanır. |
| `CreateDesktopShortcut` | İsteğe `Boolean` bağlı parametre.<br /><br /> True ise, uygulama yüklemesi sırasında masaüstünde ClickOnce oluşturulur. |
| `DeploymentUrl` | İsteğe `String` bağlı parametre.<br /><br /> Uygulamanın güncelleştirme konumunu belirtir. Bu parametre belirtilmezse, uygulama için hiçbir güncelleştirme konumu tanımlanmaz. Ancak, parametresi `UpdateEnabled` ise güncelleştirme konumu `true` belirtilmelidir. Belirtilen değer, tam URL veya UNC yolu olmalıdır. |
| `Description` | İsteğe `String` bağlı parametre.<br /><br /> Uygulama için isteğe bağlı bir açıklama belirtir. |
| `DisallowUrlActivation` | İsteğe `Boolean` bağlı parametre.<br /><br /> Bir URL aracılığıyla açıldığında uygulamanın otomatik olarak çalıştırıp çalıştırılamayca olmadığını belirtir. Bu parametre `true` ise, uygulama yalnızca Başlat menüsünden **başlatabilirsiniz.** Bu parametrenin varsayılan değeri şu `false` şekildedir: . Bu giriş yalnızca parametre değeri `Install` olduğunda `true` geçerlidir. |
| `EntryPoint` | İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Oluşturulan bildirim derlemesi için giriş noktasını gösterir. Bu giriş, ClickOnce dağıtım bildirimi için uygulama bildirimini ClickOnce belirtir.<br /><br />Görev `EntryPoint` parametresi belirtilmezse etiket `<customHostSpecified>` etiketin alt adı `<entryPoint>` olarak eklenir, örneğin:<br /><br /> `<entryPoint xmlns="urn:schemas-microsoft-com:asm.v2">`<br /><br /> `<co.v1:customHostSpecified />`<br /><br /> `</entryPoint>`<br /><br /> Aşağıdaki adımları kullanarak uygulama bildirimine DLL bağımlılıkları abilirsiniz:<br /><br /> 1. derleme başvurularını çağrısıyla <xref:Microsoft.Build.Tasks.ResolveAssemblyReference> çözümle.<br />2. Önceki görevin çıkışını ve derlemenin kendisini 'ye <xref:Microsoft.Build.Tasks.ResolveManifestFiles> iletir.<br />3. parametresini kullanarak bağımlılıkları `Dependencies` 'a <xref:Microsoft.Build.Tasks.GenerateApplicationManifest> iletir. |
| `ErrorReportUrl` | İsteğe <xref:System.String?displayProperty=fullName> bağlı parametre.<br /><br /> Yüklemeler sırasında iletişim kutularında görüntülenen web sayfasının URL'ClickOnce belirtir. |
| `InputManifest` | İsteğe <xref:Microsoft.Build.Framework.ITaskItem> bağlı parametre.<br /><br /> Bildirim oluşturucu için temel olarak görev yapacak bir giriş XML belgesi gösterir. Bu, özel bildirim tanımları gibi yapılandırılmış verilerin çıkış bildirimine yansıt ednsini sağlar. XML belgesinde kök öğe asmv1 ad alanı içinde bir derleme düğümü olması gerekir. |
| `Install` | İsteğe `Boolean` bağlı parametre.<br /><br /> Uygulamanın yüklü bir uygulama mı yoksa yalnızca çevrimiçi bir uygulama mı olduğunu belirtir. Bu parametre ise, uygulama kullanıcının Başlat menüsüne yüklenir ve Program Ekle veya Kaldır iletişim kutusu `true` **kullanılarak**  kaldırılabilir. Bu parametre `false` ise, uygulama bir web sayfasından çevrimiçi kullanım için tasarlanmıştır. Bu parametrenin varsayılan değeri şu `true` şekildedir: . |
| `MapFileExtensions` | İsteğe `Boolean` bağlı parametre.<br /><br /> .deploy dosya adı *uzantısı eşlemenin* kullan olup olmadığını belirtir. Bu parametre `true` ise, her program dosyası bir *.deploy* dosya adı uzantısıyla yayımlanır. Bu seçenek, web sunucusu güvenliği için, uygulama dağıtımını etkinleştirmek için engelini kaldırması gereken dosya adı ClickOnce yararlıdır. Bu parametrenin varsayılan değeri şu `false` şekildedir: . |
| `MaxTargetPath` | İsteğe `String` bağlı parametre.<br /><br /> Uygulama dağıtımında bir dosya yolunun izin verilen en ClickOnce belirtir. Bu parametre belirtilirse, uygulamanın her dosya yolunun uzunluğu bu sınıra göre denetlenir. Sınırı aşan öğeler derleme uyarısına neden olur. Bu giriş belirtilmezse veya sıfır ise hiçbir denetim gerçekleştirilmez. |
| `MinimumRequiredVersion` | İsteğe `String` bağlı parametre.<br /><br /> Kullanıcının güncelleştirmeyi atlayıp atlayayıp atlayayayıp atlaya olmadığını belirtir. Kullanıcının gereken en düşük sürümden daha düşük bir sürümü varsa güncelleştirmeyi atlama seçeneği yoktur. Bu giriş yalnızca parametresinin değeri `Install` olduğunda `true` geçerlidir. |
| `OutputManifest` | İsteğe <xref:Microsoft.Build.Framework.ITaskItem> bağlı parametre.<br /><br /> Oluşturulan çıkış bildirimi dosyasının adını belirtir. Bu parametre belirtilmezse, çıktı dosyasının adı oluşturulan bildirimin kimliğinden çıkar. |
| `Platform` | İsteğe `String` bağlı parametre.<br /><br /> Uygulamanın hedef platformunu belirtir. Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> `AnyCPU` varsayılan değerdir. |
| `Product` | İsteğe `String` bağlı parametre.<br /><br /> Uygulamanın adını belirtir. Bu parametre belirtilmezse, oluşturulan bildirimin kimliğinden ad çıkar. Bu ad Başlat menüsündeki kısayol adı **için** kullanılır ve Program Ekle veya Kaldır iletişim kutusunda **görünen adın** bir parçasıdır. |
| `Publisher` | İsteğe `String` bağlı parametre.<br /><br /> Uygulamanın yayımcısı belirtir. Bu parametre belirtilmezse, ad kayıtlı kullanıcıdan veya oluşturulan bildirimin kimliğinden çıkar. Bu ad Başlat menüsündeki klasör adı **için kullanılır** ve Program Ekle veya Kaldır iletişim kutusunda **görünen adın** bir parçasıdır. |
| `SuiteNamel` | İsteğe `String` bağlı parametre.<br /><br /> Uygulamanın dağıtımdan sonra bulunduğu **Başlat** menüsündeki klasörün adını ClickOnce belirtir. |
| `SupportUrl` | İsteğe `String` bağlı parametre.<br /><br /> Uygulamanın Program Ekle veya Kaldır **iletişim kutusunda** görünen bağlantıyı belirtir. Belirtilen değer, tam URL veya UNC yolu olmalıdır. |
| `TargetCulture` | İsteğe `String` bağlı parametre.<br /><br /> Uygulamanın kültürünü tanımlar ve oluşturulan `Language` bildirim için derleme kimliğinin alanını belirtir. Bu parametre belirtilmezse, uygulamanın kültür sabit olduğu varsayılır. |
| `TrustUrlParameters` | İsteğe `Boolean` bağlı parametre.<br /><br /> URL sorgu dizesi parametrelerinin uygulama için kullanılabilir olup olmadığını belirtir. Bu parametrenin varsayılan değeri, `false` parametrelerin uygulama tarafından kullanılabilir olmadığını gösteren değeridir. |
| `UpdateEnabled` | İsteğe `Boolean` bağlı parametre.<br /><br /> Uygulamanın güncelleştirmeler için etkin olup olmadığını gösterir. Bu parametrenin varsayılan değeri şu `false` şekildedir: . Bu parametre yalnızca parametresinin değeri `Install` olduğunda `true` geçerlidir. |
| `UpdateInterval` | İsteğe `Int32` bağlı parametre.<br /><br /> Uygulamanın güncelleştirme aralığını belirtir. Bu parametrenin varsayılan değeri sıfırdır. Bu parametre yalnızca ve parametrelerinin değerleri `Install` her ikisi de olduğunda `UpdateEnabled` `true` geçerlidir. |
| `UpdateMode` | İsteğe `String` bağlı parametre.<br /><br /> Uygulama başlamadan önce güncelleştirmelerin ön planda mı yoksa uygulama çalışırken arka planda mı denetlenir? Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `Foreground`<br />-   `Background`<br /><br /> Bu parametrenin varsayılan değeri: `Background` . Bu parametre yalnızca ve parametrelerinin değerleri `Install` her ikisi de olduğunda `UpdateEnabled` `true` geçerlidir. |
| `UpdateUnit` | İsteğe `String` bağlı parametre.<br /><br /> Parametresinin birimlerini `UpdateInterval` belirtir. Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `Hours`<br />-   `Days`<br />-   `Weeks`<br /><br /> Bu parametre yalnızca ve parametrelerinin değerleri `Install` her ikisi de olduğunda `UpdateEnabled` `true` geçerlidir. |

## <a name="remarks"></a>Açıklamalar

Bu görev, yukarıda listelenen parametrelere ek olarak, sınıfından devralınan parametreleri de <xref:Microsoft.Build.Tasks.GenerateManifestBase> sınıfından <xref:Microsoft.Build.Utilities.Task> devralınır. Görev sınıfının parametrelerinin listesi için bkz. [Görev temel sınıfı.](../msbuild/task-base-class.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [GenerateApplicationManifest görevi](../msbuild/generateapplicationmanifest-task.md)
- [SignFile görevi](../msbuild/signfile-task.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
