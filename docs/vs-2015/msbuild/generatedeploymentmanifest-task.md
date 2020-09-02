---
title: GenerateDeploymentManifest görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
ms.assetid: 0734ebda-734d-49c4-9642-8d9d919d45fd
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6f0c13e5ea8778ca91c30383287aaad6e965bb65
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149613"
---
# <a name="generatedeploymentmanifest-task"></a>GenerateDeploymentManifest Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Dağıtım bildirimi oluşturur. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Dağıtım bildirimi, dağıtım için benzersiz bir kimlik tanımlayarak, uygulama güncelleştirme ayarlarını ve güncelleştirme konumlarını belirterek ve ilgili uygulama bildirimini göstererek, dağıtım için benzersiz bir kimlik tanımlayarak uygulamanın dağıtımını açıklar [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] .  
  
## <a name="parameters"></a>Parametreler  
 Aşağıdaki tabloda, görevi için parametreler açıklanmaktadır `GenerateDeploymentManifest` .  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`AssemblyName`|İsteğe bağlı `String` parametre.<br /><br /> `Name`Oluşturulan bildirim için derleme kimliği alanını belirtir. Bu parametre belirtilmemişse, ad `EntryPoint` veya `InputManifest` parametrelerinden algılanır. Ad çıkarsanamıyor, görev bir hata oluşturur.|  
|`AssemblyVersion`|İsteğe bağlı `String` parametre.<br /><br /> `Version`Oluşturulan bildirim için derleme kimliği alanını belirtir. Bu parametre belirtilmezse, görev "1.0.0.0" değerini kullanır.|  
|`CreateDesktopShortcut`|İsteğe bağlı `Boolean` parametre.<br /><br /> Doğru ise, ClickOnce uygulaması yüklemesi sırasında masaüstünde bir simge oluşturulur.|  
|`DeploymentUrl`|İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın güncelleştirme konumunu belirtir. Bu parametre belirtilmemişse, uygulama için hiçbir güncelleştirme konumu tanımlanmamıştır. Ancak, `UpdateEnabled` parametresi ise `true` , güncelleştirme konumunun belirtilmesi gerekir. Belirtilen değer, tam olarak nitelenmiş bir URL veya UNC yolu olmalıdır.|  
|`Description`|İsteğe bağlı `String` parametre.<br /><br /> Uygulama için isteğe bağlı bir açıklama belirtir.|  
|`DisallowUrlActivation`|İsteğe bağlı `Boolean` parametre.<br /><br /> Uygulamanın bir URL aracılığıyla açıldığında otomatik olarak çalıştırılması gerekip gerekmediğini belirtir. Bu parametre ise `true` , uygulama yalnızca başlangıç menüsünden başlatılabilir. Bu parametrenin varsayılan değeri `false` . Bu giriş yalnızca `Install` parametre değeri olduğunda geçerlidir `true` .|  
|`EntryPoint`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Oluşturulan bildirim derlemesi için giriş noktasını gösterir. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Dağıtım bildirimi için, bu giriş [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama bildirimini belirtir.<br /><br /> [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)]' De, [GenerateApplicationManifest görevi](../msbuild/generateapplicationmanifest-task.md) bir `EntryPoint` uygulama bildirimi oluşturmak için bir gerektirir. (Bütünleştirilmiş kod veya yerel bildirimler bir gerektirmez `EntryPoint` .) Bu gereksinim derleme hatasıyla zorlandı: "MSB3185: EntryPoint için EntryPoint belirtilmemiş".<br /><br /> [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]`EntryPoint`görev parametresi belirtilmediğinde bu hatayı vermez. Bunun yerine, \<customHostSpecified> etiketi etiketinin bir alt öğesi olarak eklenir \<entryPoint> , örneğin:<br /><br /> `<entryPoint xmlns="urn:schemas-`<br /><br /> `microsoft-com:asm.v2">`<br /><br /> `<co.v1:customHostSpecified />`<br /><br /> `</entryPoint>`<br /><br /> Aşağıdaki adımları kullanarak, uygulama bildirimine DLL bağımlılıkları ekleyebilirsiniz:<br /><br /> 1. bir çağrısıyla derleme başvurularını çözümleyin <xref:Microsoft.Build.Tasks.ResolveAssemblyReference> .<br />2. önceki görevin çıkışını ve derlemenin kendisini öğesine geçirin <xref:Microsoft.Build.Tasks.ResolveManifestFiles> .<br />3. parametresini kullanarak bağımlılıkları geçirin `Dependencies` <xref:Microsoft.Build.Tasks.GenerateApplicationManifest> .|  
|`ErrorReportUrl`|İsteğe bağlı [dize] (<!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  -->parametresinin.<br /><br /> ClickOnce yüklemeleri sırasında iletişim kutularında görüntülenen Web sayfasının URL 'sini belirtir.|  
|`InputManifest`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Bildirim Oluşturucu için temel olarak hizmet veren bir giriş XML belgesi gösterir. Bu, özel bildirim tanımları gibi yapılandırılmış verilerin çıktı bildiriminde yansıtılmasına olanak sağlar. XML belgesindeki kök öğesi asmv1 ad alanında bir derleme düğümü olmalıdır.|  
|`Install`|İsteğe bağlı `Boolean` parametre.<br /><br /> Uygulamanın yüklü bir uygulama mı yoksa yalnızca çevrimiçi bir uygulama mı olduğunu belirtir. Bu parametre ise `true` , uygulama kullanıcının Başlat menüsüne yüklenir ve Program Ekle veya Kaldır iletişim kutusu kullanılarak kaldırılabilir. Bu parametre ise `false` , uygulama bir Web sayfasından çevrimiçi olarak kullanılmak üzere tasarlanmıştır. Bu parametrenin varsayılan değeri `true` .|  
|`MapFileExtensions`|İsteğe bağlı `Boolean` parametre.<br /><br /> . Deploy dosya adı uzantısı eşlemesinin kullanılıp kullanılmayacağını belirtir. Bu parametre ise `true` , her program dosyası bir. deploy dosya adı uzantısıyla yayımlanır. Bu seçenek, Web sunucusu güvenliğinin, uygulama dağıtımını etkinleştirmek için engellenmemiş olması gereken dosya adı uzantılarının sayısını sınırlayabilmesini sağlar [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Bu parametrenin varsayılan değeri `false` .|  
|`MaxTargetPath`|İsteğe bağlı `String` parametre.<br /><br /> Bir uygulama dağıtımında bir dosya yolunun izin verilen maksimum uzunluğunu belirtir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Bu parametre belirtilmişse, uygulamadaki her dosya yolunun uzunluğu bu sınıra karşı denetlenir. Sınırı aşan tüm öğeler, derleme uyarısına neden olur. Bu giriş belirtilmemişse veya sıfırsa, hiçbir denetim yapılmaz.|  
|`MinimumRequiredVersion`|İsteğe bağlı `String` parametre.<br /><br /> Kullanıcının güncelleştirmeyi atlayıp atlayamayacağını belirtir. Kullanıcının gerekenden daha düşük bir sürümü varsa, güncelleştirmeyi atlama seçeneği yoktur. Bu giriş yalnızca parametresinin değeri olduğunda geçerlidir `Install` `true` .|  
|`OutputManifest`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Oluşturulan çıkış bildirimi dosyasının adını belirtir. Bu parametre belirtilmemişse, çıkış dosyasının adı oluşturulan bildirimin kimliğinden algılanır.|  
|`Platform`|İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın hedef platformunu belirtir. Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> Varsayılan değer: `AnyCPU`.|  
|`Product`|İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın adını belirtir. Bu parametre belirtilmemişse, ad oluşturulan bildirimin kimliğinden algılanır. Bu ad, başlangıç menüsündeki kısayol adı için kullanılır ve Program Ekle veya Kaldır iletişim kutusunda görünen adın bir parçasıdır.|  
|`Publisher`|İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın yayımcısını belirtir. Bu parametre belirtilmemişse, ad kayıtlı kullanıcıdan veya oluşturulan bildirimin kimliğiyle algılanır. Bu ad, başlangıç menüsündeki klasör adı için kullanılır ve Program Ekle veya Kaldır iletişim kutusunda görünen adın bir parçasıdır.|  
|`SuiteNamel`|İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın ClickOnce dağıtımından sonra bulunduğu başlangıç menüsünde klasörün adını belirtir.|  
|`SupportUrl`|İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın program Ekle veya Kaldır iletişim kutusunda görünen bağlantıyı belirtir. Belirtilen değer, tam olarak nitelenmiş bir URL veya UNC yolu olmalıdır.|  
|`TargetCulture`|İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın kültürünü tanımlar ve `Language` oluşturulan bildirim için derleme kimliği alanını belirtir. Bu parametre belirtilmezse, uygulamanın kültür sabiti olduğu varsayılır.|  
|`TrustUrlParameters`|İsteğe bağlı `Boolean` parametre.<br /><br /> URL sorgusu dize parametrelerinin uygulama için kullanılabilir hale yapılıp yapılmayacağını belirtir. Bu parametrenin varsayılan değeri, `false` parametrelerin uygulama için kullanılamayacağını belirten.|  
|`UpdateEnabled`|İsteğe bağlı `Boolean` parametre.<br /><br /> Uygulamanın güncelleştirmeler için etkinleştirilip etkinleştirilmeyeceğini belirtir. Bu parametrenin varsayılan değeri `false` . Bu parametre yalnızca parametresinin değeri olduğunda geçerlidir `Install` `true` .|  
|`UpdateInterval`|İsteğe bağlı `Int32` parametre.<br /><br /> Uygulamanın güncelleştirme aralığını belirtir. Bu parametrenin varsayılan değeri sıfırdır. Bu parametre yalnızca `Install` ve parametrelerinin değerlerinin her ikisi de olduğunda geçerlidir `UpdateEnabled` `true` .|  
|`UpdateMode`|İsteğe bağlı `String` parametre.<br /><br /> Güncelleştirmelerin uygulama başlatılmadan önce ön planda mı yoksa uygulama çalışırken arka planda mı denetlenmesi gerektiğini belirtir. Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `Foreground`<br />-   `Background`<br /><br /> Bu parametrenin varsayılan değeri `Background` . Bu parametre yalnızca `Install` ve parametrelerinin değerlerinin her ikisi de olduğunda geçerlidir `UpdateEnabled` `true` .|  
|`UpdateUnit`|İsteğe bağlı `String` parametre.<br /><br /> Parametre için birimleri belirtir `UpdateInterval` . Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `Hours`<br />-   `Days`<br />-   `Weeks`<br /><br /> Bu parametre yalnızca `Install` ve parametrelerinin değerlerinin her ikisi de olduğunda geçerlidir `UpdateEnabled` `true` .|  
  
## <a name="remarks"></a>Açıklamalar  
 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.GenerateManifestBase> <xref:Microsoft.Build.Utilities.Task> . Görev sınıfının parametrelerinin listesi için bkz. [görev temel sınıfı](../msbuild/task-base-class.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görevlerinize](../msbuild/msbuild-tasks.md)   
 [GenerateApplicationManifest görevi](../msbuild/generateapplicationmanifest-task.md)   
 [SignFile görevi](../msbuild/signfile-task.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)
