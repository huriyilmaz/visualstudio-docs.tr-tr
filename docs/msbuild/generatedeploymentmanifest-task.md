---
title: GenerateDeploymentManifest görevi | Microsoft Docs
description: ClickOnce dağıtım bildirimi oluşturmak için MSBuild GenerateDeploymentManifest görevini kullanmayı öğrenin.
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
ms.workload:
- multiple
ms.openlocfilehash: 436aeb1b318aaa98d8a8cc9d8dac6baf4dd3c6c3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914764"
---
# <a name="generatedeploymentmanifest-task"></a>GenerateDeploymentManifest görevi

ClickOnce dağıtım bildirimi oluşturur. ClickOnce dağıtım bildirimi, dağıtım için benzersiz bir kimlik tanımlayarak, uygulama güncelleştirme ayarlarını ve güncelleştirme konumlarını belirterek ve karşılık gelen ClickOnce uygulama bildirimini göstererek, dağıtım için benzersiz bir kimlik tanımlayarak uygulamanın dağıtımını açıklar.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda, görevi için parametreler açıklanmaktadır `GenerateDeploymentManifest` .

| Parametre | Açıklama |
|--------------------------| - |
| `AssemblyName` | İsteğe bağlı `String` parametre.<br /><br /> `Name`Oluşturulan bildirim için derleme kimliği alanını belirtir. Bu parametre belirtilmemişse, ad `EntryPoint` veya `InputManifest` parametrelerinden algılanır. Ad çıkarsanamıyor, görev bir hata oluşturur. |
| `AssemblyVersion` | İsteğe bağlı `String` parametre.<br /><br /> `Version`Oluşturulan bildirim için derleme kimliği alanını belirtir. Bu parametre belirtilmezse, görev "1.0.0.0" değerini kullanır. |
| `CreateDesktopShortcut` | İsteğe bağlı `Boolean` parametre.<br /><br /> Doğru ise, ClickOnce uygulaması yüklemesi sırasında masaüstünde bir simge oluşturulur. |
| `DeploymentUrl` | İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın güncelleştirme konumunu belirtir. Bu parametre belirtilmemişse, uygulama için hiçbir güncelleştirme konumu tanımlanmamıştır. Ancak, `UpdateEnabled` parametresi ise `true` , güncelleştirme konumunun belirtilmesi gerekir. Belirtilen değer, tam olarak nitelenmiş bir URL veya UNC yolu olmalıdır. |
| `Description` | İsteğe bağlı `String` parametre.<br /><br /> Uygulama için isteğe bağlı bir açıklama belirtir. |
| `DisallowUrlActivation` | İsteğe bağlı `Boolean` parametre.<br /><br /> Uygulamanın bir URL aracılığıyla açıldığında otomatik olarak çalıştırılması gerekip gerekmediğini belirtir. Bu parametre ise `true` , uygulama yalnızca **Başlangıç** menüsünden başlatılabilir. Bu parametrenin varsayılan değeri `false` . Bu giriş yalnızca `Install` parametre değeri olduğunda geçerlidir `true` . |
| `EntryPoint` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Oluşturulan bildirim derlemesi için giriş noktasını gösterir. ClickOnce dağıtım bildirimi için, bu giriş ClickOnce uygulama bildirimini belirtir.<br /><br />`EntryPoint`Görev parametresi belirtilmemişse, `<customHostSpecified>` etiketi etiketin alt öğesi olarak eklenir `<entryPoint>` , örneğin:<br /><br /> `<entryPoint xmlns="urn:schemas-microsoft-com:asm.v2">`<br /><br /> `<co.v1:customHostSpecified />`<br /><br /> `</entryPoint>`<br /><br /> Aşağıdaki adımları kullanarak, uygulama bildirimine DLL bağımlılıkları ekleyebilirsiniz:<br /><br /> 1. bir çağrısıyla derleme başvurularını çözümleyin <xref:Microsoft.Build.Tasks.ResolveAssemblyReference> .<br />2. önceki görevin çıkışını ve derlemenin kendisini öğesine geçirin <xref:Microsoft.Build.Tasks.ResolveManifestFiles> .<br />3. parametresini kullanarak bağımlılıkları geçirin `Dependencies` <xref:Microsoft.Build.Tasks.GenerateApplicationManifest> . |
| `ErrorReportUrl` | İsteğe bağlı <xref:System.String?displayProperty=fullName> parametre.<br /><br /> ClickOnce yüklemeleri sırasında iletişim kutularında görüntülenen Web sayfasının URL 'sini belirtir. |
| `InputManifest` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Bildirim Oluşturucu için temel olarak hizmet veren bir giriş XML belgesi gösterir. Bu, özel bildirim tanımları gibi yapılandırılmış verilerin çıktı bildiriminde yansıtılmasına olanak sağlar. XML belgesindeki kök öğesi asmv1 ad alanında bir derleme düğümü olmalıdır. |
| `Install` | İsteğe bağlı `Boolean` parametre.<br /><br /> Uygulamanın yüklü bir uygulama mı yoksa yalnızca çevrimiçi bir uygulama mı olduğunu belirtir. Bu parametre ise `true` , uygulama kullanıcının **Başlat** menüsüne yüklenir ve **Program Ekle veya Kaldır** iletişim kutusu kullanılarak kaldırılabilir. Bu parametre ise `false` , uygulama bir Web sayfasından çevrimiçi olarak kullanılmak üzere tasarlanmıştır. Bu parametrenin varsayılan değeri `true` . |
| `MapFileExtensions` | İsteğe bağlı `Boolean` parametre.<br /><br /> *. Deploy* dosya adı uzantısı eşlemesinin kullanılıp kullanılmayacağını belirtir. Bu parametre ise `true` , her program dosyası bir *. deploy* dosya adı uzantısıyla yayımlanır. Bu seçenek, Web sunucusu güvenliğinin, ClickOnce uygulama dağıtımını etkinleştirmek için engellenmemiş olması gereken dosya adı uzantılarının sayısını sınırlayabilmesini sağlar. Bu parametrenin varsayılan değeri `false` . |
| `MaxTargetPath` | İsteğe bağlı `String` parametre.<br /><br /> ClickOnce uygulama dağıtımında bir dosya yolunun izin verilen maksimum uzunluğunu belirtir. Bu parametre belirtilmişse, uygulamadaki her dosya yolunun uzunluğu bu sınıra karşı denetlenir. Sınırı aşan tüm öğeler, derleme uyarısına neden olur. Bu giriş belirtilmemişse veya sıfırsa, hiçbir denetim yapılmaz. |
| `MinimumRequiredVersion` | İsteğe bağlı `String` parametre.<br /><br /> Kullanıcının güncelleştirmeyi atlayıp atlayamayacağını belirtir. Kullanıcının gerekenden daha düşük bir sürümü varsa, güncelleştirmeyi atlama seçeneği yoktur. Bu giriş yalnızca parametresinin değeri olduğunda geçerlidir `Install` `true` . |
| `OutputManifest` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Oluşturulan çıkış bildirimi dosyasının adını belirtir. Bu parametre belirtilmemişse, çıkış dosyasının adı oluşturulan bildirimin kimliğinden algılanır. |
| `Platform` | İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın hedef platformunu belirtir. Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> `AnyCPU` varsayılan değerdir. |
| `Product` | İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın adını belirtir. Bu parametre belirtilmemişse, ad oluşturulan bildirimin kimliğinden algılanır. Bu ad, **Başlangıç** menüsündeki kısayol adı için kullanılır ve **Program Ekle veya Kaldır** iletişim kutusunda görünen adın bir parçasıdır. |
| `Publisher` | İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın yayımcısını belirtir. Bu parametre belirtilmemişse, ad kayıtlı kullanıcıdan veya oluşturulan bildirimin kimliğiyle algılanır. Bu ad, **Başlangıç** menüsündeki klasör adı için kullanılır ve **Program Ekle veya Kaldır** iletişim kutusunda görünen adın bir parçasıdır. |
| `SuiteNamel` | İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın ClickOnce dağıtımından sonra bulunduğu **Başlangıç** menüsünde klasörün adını belirtir. |
| `SupportUrl` | İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın **Program Ekle veya Kaldır** iletişim kutusunda görünen bağlantıyı belirtir. Belirtilen değer, tam olarak nitelenmiş bir URL veya UNC yolu olmalıdır. |
| `TargetCulture` | İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın kültürünü tanımlar ve `Language` oluşturulan bildirim için derleme kimliği alanını belirtir. Bu parametre belirtilmezse, uygulamanın kültür sabiti olduğu varsayılır. |
| `TrustUrlParameters` | İsteğe bağlı `Boolean` parametre.<br /><br /> URL sorgusu dize parametrelerinin uygulama için kullanılabilir hale yapılıp yapılmayacağını belirtir. Bu parametrenin varsayılan değeri, `false` parametrelerin uygulama için kullanılamayacağını belirten. |
| `UpdateEnabled` | İsteğe bağlı `Boolean` parametre.<br /><br /> Uygulamanın güncelleştirmeler için etkinleştirilip etkinleştirilmeyeceğini belirtir. Bu parametrenin varsayılan değeri `false` . Bu parametre yalnızca parametresinin değeri olduğunda geçerlidir `Install` `true` . |
| `UpdateInterval` | İsteğe bağlı `Int32` parametre.<br /><br /> Uygulamanın güncelleştirme aralığını belirtir. Bu parametrenin varsayılan değeri sıfırdır. Bu parametre yalnızca `Install` ve parametrelerinin değerlerinin her ikisi de olduğunda geçerlidir `UpdateEnabled` `true` . |
| `UpdateMode` | İsteğe bağlı `String` parametre.<br /><br /> Güncelleştirmelerin uygulama başlatılmadan önce ön planda mı yoksa uygulama çalışırken arka planda mı denetlenmesi gerektiğini belirtir. Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `Foreground`<br />-   `Background`<br /><br /> Bu parametrenin varsayılan değeri `Background` . Bu parametre yalnızca `Install` ve parametrelerinin değerlerinin her ikisi de olduğunda geçerlidir `UpdateEnabled` `true` . |
| `UpdateUnit` | İsteğe bağlı `String` parametre.<br /><br /> Parametre için birimleri belirtir `UpdateInterval` . Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `Hours`<br />-   `Days`<br />-   `Weeks`<br /><br /> Bu parametre yalnızca `Install` ve parametrelerinin değerlerinin her ikisi de olduğunda geçerlidir `UpdateEnabled` `true` . |

## <a name="remarks"></a>Açıklamalar

Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.GenerateManifestBase> <xref:Microsoft.Build.Utilities.Task> . Görev sınıfının parametrelerinin listesi için bkz. [görev temel sınıfı](../msbuild/task-base-class.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [GenerateApplicationManifest görevi](../msbuild/generateapplicationmanifest-task.md)
- [SignFile görevi](../msbuild/signfile-task.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
