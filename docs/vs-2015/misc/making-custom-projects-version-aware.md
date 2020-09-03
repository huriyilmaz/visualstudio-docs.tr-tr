---
title: Özel proje sürümü ile uyumlu hale getirme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 5233d3ff-6e89-4401-b449-51b4686becca
caps.latest.revision: 33
manager: jillfra
ms.openlocfilehash: 0b29728cffc962b5d09a5adc45f8cac2093b020a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825679"
---
# <a name="making-custom-projects-version-aware"></a>Özel proje sürümü duyarlı hale getirme
Özel Proje sisteminizde, bu türdeki projelerin Visual Studio 'nun birden çok sürümüne yüklenmesine izin verebilirsiniz. Ayrıca, bu türdeki projelerin Visual Studio 'nun önceki bir sürümünde yüklenmesini engelleyebilirsiniz. Projenin onarım, dönüştürme veya kullanımdan kaldırma gerektirmesi durumunda kendisini daha sonraki bir sürüme tanıtmak için de etkinleştirebilirsiniz.  
  
## <a name="allowing-projects-to-load-in-multiple-versions"></a>Projelerin birden çok sürüme yüklenmesine izin verme  
 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]Birden çok sürümde çalışmak için, SP1 veya sonraki sürümlerde oluşturulan çoğu projeyi değiştirebilirsiniz.  
  
 Proje yüklenmeden önce, Visual Studio <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly%2A> projenin yükseltilip yükseltimeyeceğini belirlemede yöntemini çağırır. Proje yükseltilediyse, `UpgradeProject_CheckOnly` yöntemi daha sonra <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> projeye yükseltme yöntemine bir çağrı çağrısının oluşmasına neden olan bir bayrak ayarlar. Uyumsuz projeler yükseltilemediğinden, `UpgradeProject_CheckOnly` önceki bölümde açıklandığı gibi öncelikle proje uyumluluğunu kontrol etmelidir.  
  
 Proje sisteminin yazarı olarak, bir `UpgradeProject_CheckOnly` `IVsProjectUpgradeViaFactory4` yükseltme denetimi ile proje sisteminizin kullanıcılarını sağlamak için (arabiriminden) uygulamasını uygulayın. Kullanıcılar bir projeyi açtıklarında, bir projenin yüklenmeden önce onarılması gerekip gerekmediğini öğrenmek için bu yöntem çağrılır. Olası yükseltme gereksinimleri içinde numaralandırılır `VSPUVF_REPAIRFLAGS` ve aşağıdaki olasılıkları içerir:  
  
1. `SPUVF_PROJECT_NOREPAIR`: Onarım gerektirmez.  
  
2. `VSPUVF_PROJECT_SAFEREPAIR`: Projenin önceki sürümleriyle karşılaşacağınız sorunlar olmadan, projeyi önceki bir sürümle uyumlu hale getirir.  
  
3. `VSPUVF_PROJECT_UNSAFEREPAIR`: Projeyi geriye dönük olarak uyumlu hale getirir, ancak ürünün önceki sürümleriyle karşılaşabilecek sorunlar hakkında bazı risklerle karşılaşırsınız. Örneğin, proje farklı SDK sürümlerine bağımlıyadıysanız uyumlu olmayacaktır.  
  
4. `VSPUVF_PROJECT_ONEWAYUPGRADE`: Projeyi önceki bir sürümle uyumsuz hale getirir.  
  
5. `VSPUVF_PROJECT_INCOMPATIBLE`: Geçerli sürümün bu projeyi desteklemediğini belirtir.  
  
6. `VSPUVF_PROJECT_DEPRECATED`: Bu projenin artık desteklenmediğini belirtir.  
  
> [!NOTE]
> Karışıklığı önlemek için, bunları ayarladığınızda yükseltme bayraklarını birleştirmeyin. Örneğin, gibi belirsiz bir yükseltme durumu oluşturmayın `VSPUVF_PROJECT_SAFEREPAIR | VSPUVF_PROJECT_DEPRECATED` .  
  
 Proje türleri, işlevini `UpgradeProjectFlavor_CheckOnly` `IVsProjectFlavorUpgradeViaFactory2` arabiriminden uygulayabilir. Bu işlevin çalışmasını sağlamak için, `IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly` daha önce bahsedilen uygulamanın bu uygulamayı çağırması gerekir. Bu çağrı Visual Basic veya C# temel proje sisteminde zaten uygulanmış. Bu işlevin etkisi, proje türlerini, temel proje sisteminin ne olduğuna ek olarak projenin Yükseltme gereksinimlerini de belirlemesine olanak sağlar. Uyumluluk iletişim kutusunda iki gereksinimin en önemlisi gösterilmektedir.  
  
 Visual Studio bir yükseltme denetimi gerçekleştirdiğinde, Visual Studio 'nun önceki sürümlerinde olduğu gibi NULL değer yerine bir günlükçü sağlar. Günlükçü, proje sistemleri ve türleri, Eski projelerinizi doğru bir şekilde yüklemek için gereken değişikliklerin yapısını anlamanıza yardımcı olabilecek ek bilgiler sağlar. İletişim kutularını kullanmak yerine daha fazla bilgi sağlamak için günlükçü 'yi kullanmanızı öneririz. Daha fazla bilgi için bu konunun ilerleyen kısımlarında bulunan [yükseltme günlükçüsü](../misc/making-custom-projects-version-aware.md#BKMK_UpgradeLogger) bölümüne bakın.  
  
 Yönetilen uygulamalar için, proje yükseltme arabirimleri Microsoft.VisualStudio.Shell.Interop.11.0.dll birlikte çalışma derlemesinde kullanılabilir.  
  
 `UpgradeProject`Yöntemi, yaptığı değişikliklerin projenin Visual Studio 'nun önceki bir sürümünde yüklenmesini önleyemeyeceğini belirleyebilir. Öyleyse, yöntemi projeyi uyumsuz olarak işaretler. Projenin uyumsuz olarak nasıl işaretlendiğini anlamak için, bu konunun önceki kısımlarında [bir projeyi uyumsuz olarak işaretleme](../misc/making-custom-projects-version-aware.md#BKMK_Incompat) bölümüne bakın. Bu iletişim kutusu görüntülendikten sonra, `IVsAppCompat.BreakAssetCompatibility` `IVsAppCompat.AskForUserConsentToBreakAssetCompat` iletişim kutusunun iki kez görünmesi gerektiğinden yöntemi çağırmak yerine, projeyi, yöntemi çağırmak yerine doğrudan çağırarak projeyi uyumsuz olarak işaretlemenizi öneririz.  
  
 Uyumluluk Kullanıcı deneyimini özetlemeye yardımcı olacak bir örnek aşağıda verilmiştir. Bir proje daha önceki bir sürümde oluşturulduysa ve geçerli sürüm bir yükseltmenin gerekli olduğunu belirlerse, Visual Studio kullanıcıdan değişiklikleri yapmak için izin vermesini istemek üzere bir iletişim kutusu görüntüler. Kullanıcı kabul ederse proje değiştirilir ve sonra yüklenir. Çözüm daha sonra kapatılırsa ve önceki sürümde yeniden açıldığında, tek yönlü yükseltilen proje uyumsuz olur ve yüklenmez. Projenin yalnızca bir onarım yapması gerekseydi (yükseltme yerine), onarılan proje her iki sürümde de açık olur.  
  
## <a name="marking-a-project-as-incompatible"></a><a name="BKMK_Incompat"></a> Projeyi uyumsuz olarak işaretleme  
 Projeyi, Visual Studio 'nun önceki sürümleriyle uyumsuz olarak işaretleyebilirsiniz.  Örneğin, .NET Framework 4,5 özelliği kullanan bir proje oluşturduğunuzu varsayalım. Bu proje içinde derlenmediği [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] için, bu sürümün yüklemeyi denemeden kaçınmak için, uyumsuz olarak işaretleyebilirsiniz.  
  
 Uyumsuz özelliği ekleyen bileşen, projenin uyumsuz olarak işaretlenmesinden sorumludur. Bileşenin, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> ilgilendiğiniz projeleri temsil eden arabirime erişimi olmalıdır.  
  
#### <a name="to-mark-a-project-as-incompatible"></a>Projeyi uyumsuz olarak işaretlemek için  
  
1. Bileşeninde, `IVsAppCompat` genel hizmet SVsSolution bir arabirim alın.  
  
     Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>.  
  
2. Bileşeninde, çağırın `IVsAppCompat.AskForUserConsentToBreakAssetCompat` ve bunu `IVsHierarchy` ilgilendiğiniz projeleri temsil eden arabirimlerin bir dizisini geçirin.  
  
     Bu yöntem aşağıdaki imzaya sahiptir:  
  
    ```  
    HRESULT AskForUserConsentToBreakAssetCompat([in] SAFEARRAY(IVsHierarchy*) sarrProjectHierarchies)  
  
    ```  
  
     Bu kodu uygularsanız, bir proje uyumluluğu iletişim kutusu görüntülenir. İletişim kutusu kullanıcıdan belirtilen tüm projeleri uyumsuz olarak işaretlemesini ister. Kullanıcı kabul ederse `AskForUserConsentToBreakAssetCompat` `S_OK` ; Aksi takdirde, `AskForUserConsentToBreakAssetCompat` döndürür `OLE_E_PROMPTSAVECANCELLED` .  
  
    > [!WARNING]
    > En yaygın senaryolarda, `IVsHierarchy` dizi yalnızca bir öğe içerir.  
  
3. `AskForUserConsentToBreakAssetCompat`Dönerse `S_OK` , bileşen bu uyumluluğu kesen değişiklikleri yapar veya kabul eder.  
  
4. Bileşeninizdeki, `IVsAppCompat.BreakAssetCompatibility` uyumsuz olarak işaretlemek istediğiniz her proje için yöntemini çağırın. Bileşen, `lpszMinimumVersion` Visual Studio 'nun kayıt defterindeki geçerli sürüm dizesini aramak yerine, parametrenin değerini belirli bir en düşük sürüme ayarlayabilir. Bu yaklaşım, bu durumda, kayıt defterindeki kayıt defterine göre yanlışlıkla daha yüksek bir değer ayarlanmasını sağlayan Bileşen riskini en aza indirir. Bu daha yüksek değer ayarlandıysa, Visual Studio projeyi açamadı.  
  
     Bu yöntem aşağıdaki imzaya sahiptir:  
  
    ```  
    HRESULT BreakAssetCompatibility([in] IVsHierarchy * pProjHier), [in] LPCOLESTR lpszMinimumVersion);  
  
    ```  
  
     Bileşen `lpszMinimumVersion` null olarak ayarlanırsa, `BreakAssetCompatibility` yöntemi `IVsAppCompat.GetCurrentDesignTimeCompatVersion` Visual Studio 'nun geçerli sürümünü temsil eden bir dize almak için yöntemini çağırır.  
  
     Bu yöntem aşağıdaki imzaya sahiptir:  
  
    ```  
    HRESULT GetCurrentDesignTimeCompatVersion([out] BSTR * pbstrCurrentDesignTimeCompatVersion)  
    ```  
  
     Breakkassetcompatibility yöntemi daha sonra, `IVsHierarchy.SetProperty` kök `VSHPROPID_MinimumDesignTimeCompatVersion` özelliğini önceki adımda elde ettiğiniz sürüm dizesinin değerine ayarlamak için yöntemini çağırır.  
  
     Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>.  
  
> [!IMPORTANT]
> `VSHPROPID_MinimumDesignTimeCompatVersion`Projeyi uyumlu veya uyumsuz olarak işaretlemek için özelliğini uygulamanız gerekir. Örneğin, proje sistemi bir MSBuild proje dosyası kullanıyorsa, proje dosyasına `<MinimumVisualStudioVersion>` karşılık gelen özellik değerine eşit bir değere sahip bir yapı özelliği ekleyin `VSHPROPID_MinimumDesignTimeCompatVersion` .  
  
## <a name="detecting-whether-a-project-is-incompatible"></a>Projenin uyumsuz olup olmadığını algılama  
 Visual Studio 'nun geçerli sürümü ile uyumlu olmayan bir proje, yüklemeden korunmalıdır. Ayrıca, uyumsuz bir proje yükseltilemez veya onarılamıyor. Bu nedenle, bir proje uyumluluk için iki kez denetlenmelidir: Birincisi, yükseltme veya onarım için kabul edildiğinde ve ikincisi yüklenmeden önce.  
  
 Proje uyumsuzluğunun algılanmasını etkinleştirmek için <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly%2A> ve yöntemlerini uygulamanız gerekir <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> . Bir proje uyumsuz ise, `UpgradeProject_CheckOnly` başarı kodunu döndürmelidir `VS_S_INCOMPATIBLEPROJECT` ve `CreateProject` hata kodunu döndürmelidir `VS_E_INCOMPATIBLEPROJECT` . Flavored projeleri için yerine uygulamanız gerekir `IVsProjectFlavorUpgradeViaFactory2.UpgradeProjectFlavor_CheckOnly` `IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly` .  
  
 Bir Web, Office (VSTO), Silverlight veya üzerine inşa edilmiş diğer proje türleri varsa, proje sistemi flavored olarak adlandırılır. Zaten `IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly` uygulanmış olan proje sistemlerini önceden uygulayan ve flatabilen daha eski proje sistemleri `IVsProjectFlavorUpgradeViaFactory.UpgradeProjectFlavor_CheckOnly` desteklenmeye devam eder. Eski sürümü `IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly` aşağıdaki uygulama imzasına sahiptir:  
  
```  
IVsProjectUpgradeViaFactory::UpgradeProject_CheckOnly(  
  
/* [in] */ BSTR bstrFileName,  
/* [in] */ IVsUpgradeLogger *pLogger,  
/* [out] */ BOOL *pUpgradeRequired,  
/* [out] */ GUID *pguidNewProjectFactory,  
/* [out] */ VSPUVF_FLAGS *pUpgradeProjectCapabilityFlags  
)  
```  
  
 Bu yöntem `pUpgradeRequired` true olarak ayarlanır ve döndürürse `S_OK` , sonuç "Upgrade" olarak değerlendirilir ve yöntemi `VSPUVF_PROJECT_ONEWAYUPGRADE` Bu konunun ilerleyen kısımlarında açıklanan değere bir yükseltme bayrağı ayarladı. Aşağıdaki dönüş değerleri, bu eski yöntem kullanılarak desteklenir ancak yalnızca `pUpgradeRequired` true olarak ayarlanır:  
  
1. `VS_S_PROJECT_SAFEREPAIRREQUIRED`. Bu dönüş değeri `pUpgradeRequired` `VSPUVF_PROJECT_SAFEREPAIR` , bu konunun ilerleyen kısımlarında açıklanan değeri değerine eşdeğer olarak çevirir.  
  
2. `VS_S_PROJECT_UNSAFEREPAIRREQUIRED`. Bu dönüş değeri `pUpgradeRequired` `VSPUVF_PROJECT_UNSAFEREPAIR` , bu konunun ilerleyen kısımlarında açıklanan değeri değerine eşdeğer olarak çevirir  
  
3. `VS_S_PROJECT_ONEWAYUPGRADEREQUIRED`. Bu dönüş değeri `pUpgradeRequired` `VSPUVF_PROJECT_ONEWAYUPGRADE` , bu konunun ilerleyen kısımlarında açıklanan değeri değerine eşdeğer olarak çevirir.  
  
   Ve ' deki yeni uygulamalar, `IVsProjectUpgradeViaFactory4` `IVsProjectFlavorUpgradeViaFactory2` geçiş türünü daha kesin şekilde belirtmeyi sağlar.  
  
> [!NOTE]
> Uyumluluk denetiminin sonucunu yöntemine göre önbelleğe alarak, `UpgradeProject_CheckOnly` sonraki çağrısı tarafından da kullanılabilir `CreateProject` .  
  
 Örneğin, `UpgradeProject_CheckOnly` `CreateProject` [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1 proje sistemi ile birlikte yazılan ve yöntemleri bir proje dosyasını inceler ve `<MinimumVisualStudioVersion>` Build özelliğinin "11,0" olduğunu fark ederseniz, sp1 içeren Visual Studio 2010 projeyi yüklemez. Buna ek olarak, **Çözüm Gezgini** projenin "uyumsuz" olduğunu gösterir ve bu uygulamayı yüklemez.  
  
## <a name="the-upgrade-logger"></a><a name="BKMK_UpgradeLogger"></a> Yükseltme günlükçüsü  
 ' A çağrı `IVsProjectUpgradeViaFactory::UpgradeProject` `IVsUpgradeLogger` , proje sistemleri ve türleri, sorun giderme için ayrıntılı yükseltme izlemesi sağlamak üzere kullanması gereken bir günlükçü içerir. Bir uyarı veya hata günlüğe kaydedildiğinde, Visual Studio yükseltme raporunu gösterir.  
  
 Yükseltme günlükçüsü ' ne yazdığınızda aşağıdaki yönergeleri göz önünde bulundurun:  
  
- Visual Studio, tüm projeler yükseltmeyi tamamladıktan sonra Flush çağırır. Bunu Proje sisteminizde çağırmayın.  
  
- LogMessage işlevi şu hata düzeylerine sahiptir:  
  
  - 0, izlemek istediğiniz herhangi bir bilgi içindir.  

  - 1 bir uyarı içindir.  

  - 2 bir hata için  

  - 3, rapor biçimlendiricisi içindir. Projeniz yükseltildiğinde, "dönüştürülmüş" sözcüğünü bir kez günlüğe kaydedin ve sözcüğü yerelleştirmeyin.  
  
- Bir proje herhangi bir onarım veya yükseltme gerektirmiyorsa, Visual Studio günlük dosyasını yalnızca proje sisteminde bir uyarı veya UpgradeProject_CheckOnly ya da UpgradeProjectFlavor_CheckOnly yöntemleri sırasında bir hata günlüğe kaydedilmiş olması durumunda oluşturacaktır.
