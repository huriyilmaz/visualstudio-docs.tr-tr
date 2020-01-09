---
title: GenerateDeploymentManifest görevi | Microsoft Docs
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
ms.openlocfilehash: fc953298241ec7c48bbf5ea87c902aa28b349ce0
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588310"
---
# <a name="generatedeploymentmanifest-task"></a>GenerateDeploymentManifest görevi

Bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtım bildirimi oluşturur. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtım bildirimi, dağıtım için benzersiz bir kimlik tanımlayarak, uygulama güncelleştirme ayarlarını ve güncelleştirme konumlarını belirten ve karşılık gelen [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama bildirimini belirten dağıtım niteliklerini tanımlayarak uygulamanın dağıtımını açıklar.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda `GenerateDeploymentManifest` görevinin parametreleri açıklanmaktadır.

| Parametre | Açıklama |
|--------------------------| - |
| `AssemblyName` | İsteğe bağlı `String` parametresi.<br /><br /> Oluşturulan bildirim için derleme kimliğinin `Name` alanını belirtir. Bu parametre belirtilmemişse, ad `EntryPoint` veya `InputManifest` parametrelerinden algılanır. Ad çıkarsanamıyor, görev bir hata oluşturur. |
| `AssemblyVersion` | İsteğe bağlı `String` parametresi.<br /><br /> Oluşturulan bildirim için derleme kimliğinin `Version` alanını belirtir. Bu parametre belirtilmezse, görev "1.0.0.0" değerini kullanır. |
| `CreateDesktopShortcut` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Doğru ise, ClickOnce uygulaması yüklemesi sırasında masaüstünde bir simge oluşturulur. |
| `DeploymentUrl` | İsteğe bağlı `String` parametresi.<br /><br /> Uygulamanın güncelleştirme konumunu belirtir. Bu parametre belirtilmemişse, uygulama için hiçbir güncelleştirme konumu tanımlanmamıştır. Ancak, `UpdateEnabled` parametresi `true`, güncelleştirme konumunun belirtilmesi gerekir. Belirtilen değer, tam olarak nitelenmiş bir URL veya UNC yolu olmalıdır. |
| `Description` | İsteğe bağlı `String` parametresi.<br /><br /> Uygulama için isteğe bağlı bir açıklama belirtir. |
| `DisallowUrlActivation` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Uygulamanın bir URL aracılığıyla açıldığında otomatik olarak çalıştırılması gerekip gerekmediğini belirtir. Bu parametre `true`, uygulama yalnızca **Başlangıç** menüsünden başlatılabilir. Bu parametrenin varsayılan değeri `false`. Bu giriş yalnızca `Install` parametre değeri `true`geçerlidir. |
| `EntryPoint` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Oluşturulan bildirim derlemesi için giriş noktasını gösterir. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtım bildirimi için, bu giriş [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama bildirimini belirtir.<br /><br />`EntryPoint` görev parametresi belirtilmemişse, `<customHostSpecified>` etiketi `<entryPoint>` etiketinin bir alt öğesi olarak eklenir, örneğin:<br /><br /> `<entryPoint xmlns="urn:schemas-microsoft-com:asm.v2">`<br /><br /> `<co.v1:customHostSpecified />`<br /><br /> `</entryPoint>`<br /><br /> Aşağıdaki adımları kullanarak, uygulama bildirimine DLL bağımlılıkları ekleyebilirsiniz:<br /><br /> 1. derleme başvurularını <xref:Microsoft.Build.Tasks.ResolveAssemblyReference>çağrısıyla çözümleyin.<br />2. önceki görevin çıkışını ve derlemenin kendisini <xref:Microsoft.Build.Tasks.ResolveManifestFiles>geçirin.<br />3. <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>için `Dependencies` parametresini kullanarak bağımlılıkları geçirin. |
| `ErrorReportUrl` | İsteğe bağlı <xref:System.String?displayProperty=fullName> parametresi.<br /><br /> ClickOnce yüklemeleri sırasında iletişim kutularında görüntülenen Web sayfasının URL 'sini belirtir. |
| `InputManifest` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametresi.<br /><br /> Bildirim Oluşturucu için temel olarak hizmet veren bir giriş XML belgesi gösterir. Bu, özel bildirim tanımları gibi yapılandırılmış verilerin çıktı bildiriminde yansıtılmasına olanak sağlar. XML belgesindeki kök öğesi asmv1 ad alanında bir derleme düğümü olmalıdır. |
| `Install` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Uygulamanın yüklü bir uygulama mı yoksa yalnızca çevrimiçi bir uygulama mı olduğunu belirtir. Bu parametre `true`, uygulama kullanıcının **Başlat** menüsüne yüklenir ve **Program Ekle veya Kaldır** iletişim kutusu kullanılarak kaldırılabilir. Bu parametre `false`, uygulama bir Web sayfasından çevrimiçi kullanım için tasarlanmıştır. Bu parametrenin varsayılan değeri `true`. |
| `MapFileExtensions` | İsteğe bağlı `Boolean` parametresi.<br /><br /> *. Deploy* dosya adı uzantısı eşlemesinin kullanılıp kullanılmayacağını belirtir. Bu parametre `true`ise, her program dosyası bir *. deploy* dosya adı uzantısıyla yayımlanır. Bu seçenek, Web sunucusu güvenliğinin, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama dağıtımını etkinleştirmek için engellenmemiş olması gereken dosya adı uzantılarının sayısını sınırlayabilmesini sağlamak için yararlıdır. Bu parametrenin varsayılan değeri `false`. |
| `MaxTargetPath` | İsteğe bağlı `String` parametresi.<br /><br /> [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama dağıtımında bir dosya yolunun izin verilen maksimum uzunluğunu belirtir. Bu parametre belirtilmişse, uygulamadaki her dosya yolunun uzunluğu bu sınıra karşı denetlenir. Sınırı aşan tüm öğeler, derleme uyarısına neden olur. Bu giriş belirtilmemişse veya sıfırsa, hiçbir denetim yapılmaz. |
| `MinimumRequiredVersion` | İsteğe bağlı `String` parametresi.<br /><br /> Kullanıcının güncelleştirmeyi atlayıp atlayamayacağını belirtir. Kullanıcının gerekenden daha düşük bir sürümü varsa, güncelleştirmeyi atlama seçeneği yoktur. Bu giriş yalnızca `Install` parametresinin değeri `true`olduğunda geçerlidir. |
| `OutputManifest` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametresi.<br /><br /> Oluşturulan çıkış bildirimi dosyasının adını belirtir. Bu parametre belirtilmemişse, çıkış dosyasının adı oluşturulan bildirimin kimliğinden algılanır. |
| `Platform` | İsteğe bağlı `String` parametresi.<br /><br /> Uygulamanın hedef platformunu belirtir. Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> Varsayılan değer `AnyCPU` şeklindedir. |
| `Product` | İsteğe bağlı `String` parametresi.<br /><br /> Uygulamanın adını belirtir. Bu parametre belirtilmemişse, ad oluşturulan bildirimin kimliğinden algılanır. Bu ad, **Başlangıç** menüsündeki kısayol adı için kullanılır ve **Program Ekle veya Kaldır** iletişim kutusunda görünen adın bir parçasıdır. |
| `Publisher` | İsteğe bağlı `String` parametresi.<br /><br /> Uygulamanın yayımcısını belirtir. Bu parametre belirtilmemişse, ad kayıtlı kullanıcıdan veya oluşturulan bildirimin kimliğiyle algılanır. Bu ad, **Başlangıç** menüsündeki klasör adı için kullanılır ve **Program Ekle veya Kaldır** iletişim kutusunda görünen adın bir parçasıdır. |
| `SuiteNamel` | İsteğe bağlı `String` parametresi.<br /><br /> Uygulamanın ClickOnce dağıtımından sonra bulunduğu **Başlangıç** menüsünde klasörün adını belirtir. |
| `SupportUrl` | İsteğe bağlı `String` parametresi.<br /><br /> Uygulamanın **Program Ekle veya Kaldır** iletişim kutusunda görünen bağlantıyı belirtir. Belirtilen değer, tam olarak nitelenmiş bir URL veya UNC yolu olmalıdır. |
| `TargetCulture` | İsteğe bağlı `String` parametresi.<br /><br /> Uygulamanın kültürünü tanımlar ve oluşturulan bildirim için derleme kimliğinin `Language` alanını belirtir. Bu parametre belirtilmezse, uygulamanın kültür sabiti olduğu varsayılır. |
| `TrustUrlParameters` | İsteğe bağlı `Boolean` parametresi.<br /><br /> URL sorgusu dize parametrelerinin uygulama için kullanılabilir hale yapılıp yapılmayacağını belirtir. Bu parametrenin varsayılan değeri `false`ve parametrelerin uygulama tarafından kullanılamayacağını gösterir. |
| `UpdateEnabled` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Uygulamanın güncelleştirmeler için etkinleştirilip etkinleştirilmeyeceğini belirtir. Bu parametrenin varsayılan değeri `false`. Bu parametre yalnızca `Install` parametresinin değeri `true`olduğunda geçerlidir. |
| `UpdateInterval` | İsteğe bağlı `Int32` parametresi.<br /><br /> Uygulamanın güncelleştirme aralığını belirtir. Bu parametrenin varsayılan değeri sıfırdır. Bu parametre yalnızca `Install` ve `UpdateEnabled` parametrelerinin değerleri `true`olduğunda geçerlidir. |
| `UpdateMode` | İsteğe bağlı `String` parametresi.<br /><br /> Güncelleştirmelerin uygulama başlatılmadan önce ön planda mı yoksa uygulama çalışırken arka planda mı denetlenmesi gerektiğini belirtir. Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `Foreground`<br />-   `Background`<br /><br /> Bu parametrenin varsayılan değeri `Background`. Bu parametre yalnızca `Install` ve `UpdateEnabled` parametrelerinin değerleri `true`olduğunda geçerlidir. |
| `UpdateUnit` | İsteğe bağlı `String` parametresi.<br /><br /> `UpdateInterval` parametresine yönelik birimleri belirtir. Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `Hours`<br />-   `Days`<br />-   `Weeks`<br /><br /> Bu parametre yalnızca `Install` ve `UpdateEnabled` parametrelerinin değerleri `true`olduğunda geçerlidir. |

## <a name="remarks"></a>Açıklamalar

Yukarıda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.Task> sınıfından devralan <xref:Microsoft.Build.Tasks.GenerateManifestBase> sınıfından parametreleri devralır. Görev sınıfının parametrelerinin listesi için bkz. [görev temel sınıfı](../msbuild/task-base-class.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [GenerateApplicationManifest görevi](../msbuild/generateapplicationmanifest-task.md)
- [SignFile görevi](../msbuild/signfile-task.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
