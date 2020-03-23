---
title: DeploymentManifest Görev Oluşturma | Microsoft Dokümanlar
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ca55f3eeb9b3119b27e67dcb0255f8386c521af6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634077"
---
# <a name="generatedeploymentmanifest-task"></a>GenerateDeploymentManifest görevi

ClickOnce dağıtım bildirimi oluşturur. ClickOnce dağıtım bildirimi, dağıtım için benzersiz bir kimlik tanımlayarak, yükleme veya çevrimiçi mod gibi dağıtım özelliklerini tanımlayarak, uygulama güncelleştirme ayarlarını ve güncelleştirme konumlarını belirterek bir uygulamanın dağıtımını açıklar ve ilgili ClickOnce uygulama bildirimini gösterir.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda görev parametreleri `GenerateDeploymentManifest` açıklanmaktadır.

| Parametre | Açıklama |
|--------------------------| - |
| `AssemblyName` | İsteğe bağlı `String` parametre.<br /><br /> Oluşturulan bildirim `Name` için derleme kimliğinin alanını belirtir. Bu parametre belirtilmemişse, ad veya `EntryPoint` `InputManifest` parametrelerden çıkarılır. Ad çıkarılamazsa, görev bir hata atar. |
| `AssemblyVersion` | İsteğe bağlı `String` parametre.<br /><br /> Oluşturulan bildirim `Version` için derleme kimliğinin alanını belirtir. Bu parametre belirtilmemişse, görev "1.0.0.0" değerini kullanır. |
| `CreateDesktopShortcut` | İsteğe bağlı `Boolean` parametre.<br /><br /> Doğruysa, ClickOnce uygulama yüklemesi sırasında masaüstünde bir simge oluşturulur. |
| `DeploymentUrl` | İsteğe bağlı `String` parametre.<br /><br /> Uygulamaiçin güncelleştirme konumunu belirtir. Bu parametre belirtilmemişse, uygulama için güncelleştirme konumu tanımlanmaz. Ancak, `UpdateEnabled` parametre ise, `true`güncelleştirme konumu belirtilmelidir. Belirtilen değer tam nitelikli bir URL veya UNC yolu olmalıdır. |
| `Description` | İsteğe bağlı `String` parametre.<br /><br /> Uygulama için isteğe bağlı bir açıklama belirtir. |
| `DisallowUrlActivation` | İsteğe bağlı `Boolean` parametre.<br /><br /> Uygulamanın bir URL üzerinden açıldığında otomatik olarak çalıştırılıp çalıştırılmayacağını belirtir. Bu parametre `true`ise, uygulama yalnızca **Başlat** menüsünden başlatılabilir. Bu parametrenin varsayılan `false`değeri . Bu giriş yalnızca `Install` parametre değeri . `true` |
| `EntryPoint` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Oluşturulan bildirim derlemesinin giriş noktasını gösterir. ClickOnce dağıtım bildirimi için bu giriş, ClickOnce uygulama bildirimini belirtir.<br /><br />`EntryPoint` Görev parametresi belirtilmemişse, `<customHostSpecified>` etiket `<entryPoint>` etiketin alt bölümü olarak eklenir, örneğin:<br /><br /> `<entryPoint xmlns="urn:schemas-microsoft-com:asm.v2">`<br /><br /> `<co.v1:customHostSpecified />`<br /><br /> `</entryPoint>`<br /><br /> Aşağıdaki adımları kullanarak uygulama bildirimine DLL bağımlılıkları ekleyebilirsiniz:<br /><br /> 1. Montaj başvurularını bir <xref:Microsoft.Build.Tasks.ResolveAssemblyReference>çağrı ile çöz.<br />2. Önceki görevin çıktısını ve montajın kendisini <xref:Microsoft.Build.Tasks.ResolveManifestFiles>.<br />3. Parametreyi `Dependencies` kullanarak bağımlılıkları <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>geçirin. |
| `ErrorReportUrl` | İsteğe bağlı <xref:System.String?displayProperty=fullName> parametre.<br /><br /> ClickOnce yüklemeleri sırasında iletişim kutularında görüntülenen web sayfasının URL'sini belirtir. |
| `InputManifest` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Manifest jeneratör için bir temel olarak hizmet vermek için bir giriş XML belge gösterir. Bu, özel bildirim tanımları gibi yapılandırılmış verilerin çıktı bildirimine yansıtılmasını sağlar. XML belgesindeki kök öğe asmv1 ad alanında bir derleme düğümü olmalıdır. |
| `Install` | İsteğe bağlı `Boolean` parametre.<br /><br /> Uygulamanın yüklü bir uygulama mı yoksa yalnızca çevrimiçi bir uygulama mı olduğunu belirtir. Bu parametre `true`ise, uygulama kullanıcının **Başlat** menüsüne yüklenir ve Programlar Ekle **veya Kaldır** iletişim kutusu kullanılarak kaldırılabilir. Bu parametre `false`ise, uygulama bir web sayfasından çevrimiçi kullanım için tasarlanmıştır. Bu parametrenin varsayılan `true`değeri . |
| `MapFileExtensions` | İsteğe bağlı `Boolean` parametre.<br /><br /> *.deploy* dosya adı uzantısı eşleminin kullanılıp kullanılmayacağını belirtir. Bu parametre `true`ise, her program dosyası bir *.deploy* dosya adı uzantısı ile yayımlanır. Bu seçenek, ClickOnce uygulama dağıtımını etkinleştirmek için engelinin kaldırılması gereken dosya adı uzantılarının sayısını sınırlamak için web sunucusu güvenliği için yararlıdır. Bu parametrenin varsayılan `false`değeri . |
| `MaxTargetPath` | İsteğe bağlı `String` parametre.<br /><br /> ClickOnce uygulama dağıtımında dosya yolunun izin verilen maksimum uzunluğunu belirtir. Bu parametre belirtilirse, uygulamadaki her dosya yolunun uzunluğu bu sınıra göre denetlenir. Sınırı aşan tüm öğeler bir yapı uyarısı na neden olur. Bu giriş belirtilmemişse veya sıfır ise, hiçbir denetim yapılmaz. |
| `MinimumRequiredVersion` | İsteğe bağlı `String` parametre.<br /><br /> Kullanıcının güncelleştirmeyi atlayıp atlayamayacağını belirtir. Kullanıcının gereken minimumdan daha az bir sürümü varsa, güncelleştirmeyi atlama seçeneği yoktur. Bu giriş yalnızca `Install` parametrenin değeri . `true` |
| `OutputManifest` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Oluşturulan çıktı bildirimi dosyasının adını belirtir. Bu parametre belirtilmemişse, çıktı dosyasının adı oluşturulan bildirimin kimliğinden çıkarılır. |
| `Platform` | İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın hedef platformını belirtir. Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> Varsayılan değer: `AnyCPU`. |
| `Product` | İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın adını belirtir. Bu parametre belirtilmemişse, ad oluşturulan bildirimin kimliğinden çıkarılır. Bu **ad, Başlat** menüsündeki kısayol adı için kullanılır ve **Programlar Ekle veya Kaldır** iletişim kutusunda görünen adın bir parçasıdır. |
| `Publisher` | İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın yayımcısını belirtir. Bu parametre belirtilmemişse, ad kayıtlı kullanıcıdan veya oluşturulan bildirimin kimliğinden çıkarılır. Bu ad **Başlat** menüsündeki klasör adı için kullanılır ve Programlar Ekle **veya Kaldır** iletişim kutusunda görünen adın bir parçasıdır. |
| `SuiteNamel` | İsteğe bağlı `String` parametre.<br /><br /> ClickOnce dağıtımından sonra uygulamanın bulunduğu **Başlat** menüsündeki klasörün adını belirtir. |
| `SupportUrl` | İsteğe bağlı `String` parametre.<br /><br /> Uygulama için Programlar Ekle veya **Kaldır** iletişim kutusunda görünen bağlantıyı belirtir. Belirtilen değer tam nitelikli bir URL veya UNC yolu olmalıdır. |
| `TargetCulture` | İsteğe bağlı `String` parametre.<br /><br /> Uygulama kültürünü tanımlar ve oluşturulan bildirim `Language` için derleme kimliğinin alanını belirtir. Bu parametre belirtilmemişse, uygulamanın kültür değişmezi olduğu varsayılır. |
| `TrustUrlParameters` | İsteğe bağlı `Boolean` parametre.<br /><br /> URL sorgu dize parametrelerinin uygulamaya sunulup sunulmayacağını belirtir. Bu parametrenin varsayılan `false`değeri, parametrelerin uygulama için kullanılmadığını gösterir. |
| `UpdateEnabled` | İsteğe bağlı `Boolean` parametre.<br /><br /> Uygulamanın güncelleştirmeler için etkin olup olmadığını gösterir. Bu parametrenin varsayılan `false`değeri . Bu parametre yalnızca `Install` parametrenin değeri . `true` |
| `UpdateInterval` | İsteğe bağlı `Int32` parametre.<br /><br /> Uygulama için güncelleştirme aralığını belirtir. Bu parametrenin varsayılan değeri sıfırdır. Bu parametre yalnızca parametrelerin `Install` ve `UpdateEnabled` parametrelerin `true`değerleri her ikisi de olduğunda geçerlidir. |
| `UpdateMode` | İsteğe bağlı `String` parametre.<br /><br /> Uygulama başlamadan önce güncelleştirmelerin ön planda mı yoksa uygulama çalışırken arka planda mı denetlenmeleri gerektiğini belirtir. Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `Foreground`<br />-   `Background`<br /><br /> Bu parametrenin varsayılan `Background`değeri . Bu parametre yalnızca parametrelerin `Install` ve `UpdateEnabled` parametrelerin `true`değerleri her ikisi de olduğunda geçerlidir. |
| `UpdateUnit` | İsteğe bağlı `String` parametre.<br /><br /> `UpdateInterval` Parametre için birimleri belirtir. Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `Hours`<br />-   `Days`<br />-   `Weeks`<br /><br /> Bu parametre yalnızca parametrelerin `Install` ve `UpdateEnabled` parametrelerin `true`değerleri her ikisi de olduğunda geçerlidir. |

## <a name="remarks"></a>Açıklamalar

Yukarıda listelenen parametrelere ek olarak, bu görev, kendisinden sınıftan <xref:Microsoft.Build.Tasks.GenerateManifestBase> <xref:Microsoft.Build.Utilities.Task> devralınan sınıftan parametreleri devralır. Görev sınıfının parametrelerinin listesi için [Görev taban sınıfına](../msbuild/task-base-class.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [GenerateApplicationManifest görevi](../msbuild/generateapplicationmanifest-task.md)
- [SignFile görevi](../msbuild/signfile-task.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
