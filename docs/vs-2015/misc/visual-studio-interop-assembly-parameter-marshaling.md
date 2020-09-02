---
title: Visual Studio birlikte çalışma derleme parametresi sıralaması | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- troubleshooting Visual Studio SDK interop assemblies
- interop assemblies, parameter marshaling
- interop assemblies, troubleshooting
ms.assetid: 89123eae-0fef-46d5-bd36-3d2a166b14e3
caps.latest.revision: 24
manager: jillfra
ms.openlocfilehash: ac95c40b356c542da323a3ea3744827087f2d840
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686920"
---
# <a name="visual-studio-interop-assembly-parameter-marshaling"></a>Visual Studio birlikte çalışma derleme parametresi sıralaması
Yönetilen kodda yazılan VSPackages 'in yönetilmeyen COM kodu çağrısı veya çağrılması gerekebilir. Genellikle, yöntem bağımsız değişkenleri birlikte çalışma sıralayıcısı tarafından otomatik olarak dönüştürülür veya sıralanır. Ancak bazen bağımsız değişkenler kolay bir şekilde dönüştürülemez. Bu durumlarda birlikte çalışma derleme yöntemi prototip parametreleri, COM işlev parametrelerini mümkün olduğunca yakından eşleştirmek için kullanılır. Daha fazla bilgi için bkz. [birlikte çalışma hazırlama](https://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a).  
  
## <a name="general-suggestions"></a>Genel öneriler  
  
##### <a name="read-the-reference-documentation"></a>Başvuru belgelerini okuyun  
 Birlikte çalışabilirlik sorunlarını algılamaya yönelik etkili bir yol, her yöntemin başvuru belgelerini okumalıdır.  
  
 Her yöntemin başvuru belgeleri üç ilgili bölüm içerir:  
  
- [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]Com işlevi prototipi.  
  
- Birlikte çalışma bütünleştirilmiş kod yöntemi prototipi.  
  
- COM parametrelerinin bir listesi ve her biri için kısa bir açıklama.  
  
##### <a name="look-for-differences-between-the-two-prototypes"></a>İki prototiptür arasındaki farkları arayın  
 Birçok birlikte çalışabilirlik sorunu, bir COM arabirimindeki belirli bir türün tanımı ile [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] birlikte çalışma derlemelerindeki aynı türün tanımı arasındaki uyuşmazlıkları türeten türetilir. Örneğin, `null` bir [out] parametresinde değer geçme yeteneğinin farkını göz önünde bulundurun. İki prototiptür arasındaki farkları aramanız ve geçirilmekte olan veriler için kollarını göz önünde bulundurmanız gerekir.  
  
##### <a name="read-the-parameter-definitions"></a>Parametre tanımlarını oku  
 Parametre tanımlarını okuyun. COM, farklı veri türlerini tek bir parametrede karıştırma hakkında ortak dil çalışma zamanından (CLR) daha az katı. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Com arabirimleri bu esnekliğin tam avantajlarından yararlanır. Standart olmayan bir değer veya bir işaretçi parametresindeki sabit değer gibi bir veri türü geçirebilen veya gerektirebilecek herhangi bir parametre, belgelerde olduğu gibi açıklanmalıdır.  
  
### <a name="iunknown-objects-passed-as-type-void"></a>Tür void * * olarak geçirilen IUnknown nesneleri  
 COM arabiriminde tür olarak tanımlanan `void **` , ancak `[``iid_is``]` [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] birlikte çalışma derleme yöntemi prototipi içinde olarak tanımlanan [out] parametrelerini arayın.  
  
 Bazen bir COM arabirimi bir nesne oluşturur `IUnknown` ve com arabirimi bunu tür olarak geçirir `void **` . Bu arabirimler özellikle önemlidir çünkü değişken IDL içinde [out] olarak tanımlanmışsa, `IUnknown` nesne, yöntemiyle başvuruya göre sayılır `AddRef` . Nesne doğru işlenmediğinde bir bellek sızıntısı oluşur.  
  
> [!NOTE]
> `IUnknown`Com arabirimi tarafından oluşturulan ve bir [out] değişkeninde döndürülen bir nesne, açıkça yayınlanmadıysa bellek sızıntısına neden olur.  
  
 Bu tür nesneleri işleyen yönetilen yöntemler <xref:System.IntPtr> bir nesnenin işaretçisi olarak değerlendirilir `IUnknown` ve <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> nesneyi elde etmek için yöntemini çağırır. Çağıran, dönüş değerini uygun türe göre saçmalıdır. Nesne artık gerekli olmadığında, <xref:System.Runtime.InteropServices.Marshal.Release%2A> serbest bırakmak için çağırın.  
  
 Aşağıda <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> yöntemi çağırma ve nesneyi doğru işleme örneği verilmiştir `IUnknown` :  
  
```  
MyClass myclass;  
Object object;  
IntPtr pObj;  
Guid iid = Typeof(MyClass).Guid;  
int hr = windowFrame.QueryViewInterface(ref iid, out pObj);     
if (NativeMethods.Succeeded(hr))   
{  
    try   
    {  
        object = Marshal.GetObjectForIUnknown(pObj);  
        myclass = object;  
    }  
    finally   
    {  
        Marshal.Release(pObj);  
    }  
}  
else   
{  
    // error calling QueryViewInterface  
}  
```  
  
> [!NOTE]
> Aşağıdaki yöntemlerin `IUnknown` nesne işaretçilerini tür olarak geçirmesi bilinmektedir <xref:System.IntPtr> . Bu bölümde açıklandığı gibi işleyin.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>  
  
### <a name="optional-out-parameters"></a>İsteğe bağlı [out] Parametreler  
 COM arabiriminde [out] veri türü (,, vb.) olarak tanımlanan parametreleri arayın `int` `object` , ancak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] birlikte çalışma derleme yöntemi prototipde aynı veri türünde diziler olarak tanımlanır.  
  
 Gibi bazı COM arabirimleri, <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> [out] parametrelerini isteğe bağlı olarak değerlendirir. Bir nesne gerekli değilse, bu COM arabirimleri `null` [out] nesnesini oluşturmak yerine bu parametrenin değeri olarak bir işaretçi döndürür. Bu tasarım gereğidir. Bu arabirimler için `null` işaretçiler, VSPackage 'ın doğru davranışının bir parçası olarak kabul edilir ve hiçbir hata döndürülmez.  
  
 CLR bir [out] parametresinin değerine izin vermediğinden `null` , bu arabirimlerin tasarlanan davranışının bir kısmı yönetilen kod içinde doğrudan kullanılamaz. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Etkilenen arabirimlerin birlikte çalışma derleme yöntemleri, clr 'nin dizi geçişine izin verdiğinden ilgili parametreleri diziler olarak tanımlayarak soruna geçici olarak çalışır `null` .  
  
 Bu yöntemlerin yönetilen uygulamaları döndürülecek bir şey olmadığında `null` parametreye bir dizi koymalıdır. Aksi takdirde, doğru türde tek öğeli bir dizi oluşturun ve dönüş değerini diziye koyun.  
  
 İsteğe bağlı [out] parametrelerine sahip arabirimlerden bilgi alan yönetilen yöntemler, parametreyi bir dizi olarak alır. Yalnızca dizinin ilk öğesinin değerini inceleyin. Değilse `null` , ilk öğeyi özgün parametresi gibi değerlendirin.  
  
### <a name="passing-constants-in-pointer-parameters"></a>Işaretçi parametrelerinde sabitleri geçirme  
 COM arabiriminde [in] işaretçileri olarak tanımlanan, ancak <xref:System.IntPtr> [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] birlikte çalışma derleme yöntemi prototipte bir tür olarak tanımlanmış parametreleri arayın.  
  
 Bir COM arabirimi bir nesne işaretçisi yerine 0,-1 veya – 2 gibi özel bir değer geçirdiğinde benzer bir sorun oluşur. Farklı olarak [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] , clr sabitler nesne olarak atama yapmasına izin vermez. Bunun yerine, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] birlikte çalışma derlemesi parametreyi bir tür olarak tanımlar <xref:System.IntPtr> .  
  
 Bu yöntemlerin yönetilen uygulamaları, bir <xref:System.IntPtr> `int` `void *` <xref:System.IntPtr> nesneden veya bir tamsayı sabitinden (uygun şekilde) oluşturmak için, sınıfın hem hem de oluşturuculara sahip olduğundan emin olmalıdır.  
  
 Bu türün parametrelerini alan yönetilen yöntemler, <xref:System.IntPtr> <xref:System.IntPtr> sonuçları işlemek için tür dönüştürme işleçlerini kullanmalıdır. Önce öğesini <xref:System.IntPtr> öğesine dönüştürüp `int` ilgili tamsayı sabitlerine göre test edin. Hiçbir değer eşleşmezse, gerekli türdeki bir nesneye dönüştürün ve devam edin.  
  
 Bunun örnekleri için bkz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> . ve.  
  
### <a name="ole-return-values-passed-as-out-parameters"></a>OLE dönüş değerleri [out] parametresi olarak geçirildi  
 `retval`Com arabiriminde dönüş değeri olan, ancak `int` [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] birlikte çalışabilirlik derleme yöntemi prototipinin bir dönüş değerine ve ek [out] dizi parametresine sahip olan yöntemleri arayın. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Birlikte çalışma bütünleştirilmiş kod yöntemi prototiptürleri com arabirimi yöntemlerinden daha fazla parametre içerdiğinden, bu yöntemlerin özel bir işleme gerektirmesinin açık olması gerekir.  
  
 OLE etkinliğiyle ilgilenen birçok COM arabirimi, OLE durumu hakkında bilgileri arabirimin dönüş değerinde depolanan çağıran programa geri gönderir `retval` . Bir dönüş değeri kullanmak yerine, karşılık gelen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] birlikte çalışma derleme yöntemleri, bilgileri bir [out] dizi parametresinde depolanan çağıran programa geri gönderir.  
  
 Bu yöntemlerin yönetilen uygulamaları, [out] parametresiyle aynı türde tek öğeli bir dizi oluşturmalı ve bu parametreyi parametreye koymalıdır. Dizi öğesinin değeri uygun COM ile aynı olmalıdır `retval` .  
  
 Bu türün arabirimlerini çağıran yönetilen yöntemler, ilk öğeyi [out] dizisinin dışına çekmelidir. Bu öğe `retval` , karşılık gelen com arabiriminden bir dönüş değeri gibi kabul edilebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Birlikte çalışabilirlik sıralaması](https://msdn.microsoft.com/a95fdb76-7c0d-409e-a77e-0349b1ea1490)   
 [Birlikte çalışabilirlik sıralaması](https://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a)   
 [Birlikte çalışabilirlik sorunlarını giderme](https://msdn.microsoft.com/library/b324cc1e-b03c-4f39-aea6-6a6d5bfd0e37)   
 [Yönetilen VSPackages](../misc/managed-vspackages.md)