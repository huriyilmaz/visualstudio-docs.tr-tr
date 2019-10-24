---
title: Visual Studio birlikte çalışma derlemelerini kullanma | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d0db6e0e0d5014f09a84316143af40f410bc1b10
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722108"
---
# <a name="using-visual-studio-interop-assemblies"></a>Visual Studio Birlikte Çalışma Bütünleştirilmiş Kodlarını Kullanma
Visual Studio birlikte çalışma derlemeleri, yönetilen uygulamaların Visual Studio genişletilebilirlik sağlayan COM arabirimlerine erişmesine izin verir. Basit COM arabirimleri ve birlikte çalışma sürümleri arasında bazı farklılıklar vardır. Örneğin, HRESULTs genellikle int değerleri olarak temsil edilir ve özel durumlarla aynı şekilde işlenmelidir ve parametreler (özellikle de çıkış parametreleri) farklı şekilde değerlendirilir.

## <a name="handling-hresults-returned-to-managed-code-from-com"></a>COM 'dan yönetilen koda döndürülen HRESULTs işleme
 Yönetilen koddan bir COM arabirimini çağırdığınızda, HRESULT değerini inceleyin ve gerekirse bir özel durum oluşturun. @No__t_0 sınıfı, kendisine geçirilen HRESULT değerine bağlı olarak bir COM özel durumu oluşturan <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> yöntemini içerir.

 Varsayılan olarak, <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> sıfırdan küçük bir değere sahip bir HRESULT geçirildiğinde bir özel durum oluşturur. Bu tür Hsonuçların kabul edilebilir değerler olduğu ve hiçbir özel durum oluşturulması gereken durumlarda, değerler test edildikten sonra ek HRESULTS değerlerinin <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> geçirilmesi gerekir. Test edilmekte olan HRESULT, açıkça <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> 'e geçirilmiş herhangi bir HRESULT değeri ile eşleşiyorsa, hiçbir özel durum oluşturulmaz.

> [!NOTE]
> @No__t_0 sınıfı, ortak HRESULTS için sabitler içerir, örneğin, <xref:Microsoft.VisualStudio.VSConstants.S_OK> ve <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> ve [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] HRESULTS (örneğin, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> ve <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>). <xref:Microsoft.VisualStudio.VSConstants> Ayrıca, COM 'daki başarılı ve başarısız makrolara karşılık gelen <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> ve <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> yöntemleri de sağlar.

 Örneğin, <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> kabul edilebilir bir dönüş değeri olduğu, ancak sıfırdan küçük diğer HRESULT bir hatayı temsil eden aşağıdaki işlev çağrısını göz önünde bulundurun.

 [!code-vb[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_1.vb)]
 [!code-csharp[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_1.cs)]

 Birden fazla kabul edilebilir dönüş değeri varsa, ek HRESULT değerleri yalnızca <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> çağrısında listeye eklenebilir.

 [!code-vb[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_2.vb)]
 [!code-csharp[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_2.cs)]

## <a name="returning-hresults-to-com-from-managed-code"></a>Yönetilen koddan COM 'a HRESULTS döndürme
 Özel durum oluşursa, yönetilen kod onu çağıran COM işlevine <xref:Microsoft.VisualStudio.VSConstants.S_OK> döndürür. COM birlikte çalışması, yönetilen kodda kesin olarak belirlenmiş ortak özel durumları destekler. Örneğin, kabul edilemez bir `null` bağımsız değişkenini alan bir yöntem, bir <xref:System.ArgumentNullException> oluşturur.

 Hangi özel durumun throw dışında, ancak COM 'a geri dönmek istediğinizi bildiğiniz takdirde, uygun bir özel durum oluşturmak için <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> yöntemini kullanabilirsiniz. Bu, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> standart olmayan bir hata ile birlikte çalışarak, örneğin,. <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>, kendisine geçirilen HRESULT 'yi kesin türü belirtilmiş bir özel duruma eşleme girişiminde bulunur. Değilse, bunun yerine genel bir COM özel durumu oluşturur. Nihai sonuç, yönetilen koddan <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> için geçirdiğiniz HRESULT, çağıran COM işlevine döndürülür.

> [!NOTE]
> Özel durumların performansı tehlikeye alınır ve anormal program koşullarını göstermek için tasarlanmıştır. Genellikle oluşan koşulların, oluşturulan özel durum yerine satır içi olarak işlenmesi gerekir.

## <a name="iunknown-parameters-passed-as-type-void"></a>IUnknown parametreleri void * * türü olarak geçildi
 COM arabiriminde `void **` türü olarak tanımlanan, ancak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] birlikte çalışma derleme yöntemi prototipinde `[``iid_is``]` olarak tanımlanan [out] parametreleri arayın.

 Bazen bir COM arabirimi `IUnknown` nesnesi oluşturur ve COM arabirimi bunu `void **` tür olarak geçirir. Bu arabirimler özellikle önemlidir çünkü değişken IDL içinde [out] olarak tanımlandığından, `IUnknown` nesnesi `AddRef` yöntemiyle başvuruya göre sayılır. Nesne doğru işlenmediğinde bir bellek sızıntısı oluşur.

> [!NOTE]
> COM arabirimi tarafından oluşturulan ve bir [out] değişkeninde döndürülen bir `IUnknown` nesnesi, açıkça yayınlanmadıysa bellek sızıntısına neden olur.

 Bu tür nesneleri işleyen yönetilen yöntemler, <xref:System.IntPtr> bir `IUnknown` nesnenin işaretçisi olarak ele alınmalıdır ve nesneyi almak için <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> yöntemini çağırır. Çağıran, dönüş değerini uygun türe göre saçmalıdır. Nesne artık gerekli olmadığında, serbest bırakmak için <xref:System.Runtime.InteropServices.Marshal.Release%2A> çağırın.

 Aşağıda <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> yöntemi çağırma ve `IUnknown` nesnesini doğru işleme örneği verilmiştir:

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
> Aşağıdaki yöntemlerin `IUnknown` nesne işaretçilerini <xref:System.IntPtr> tür olarak geçirmesi bilinmektedir. Bu bölümde açıklandığı gibi işleyin.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>

## <a name="optional-out-parameters"></a>İsteğe bağlı [out] Parametreler
 COM arabiriminde [out] veri türü (`int`, `object` vb.) olarak tanımlanan, ancak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] birlikte çalışma derleme yöntemi prototipinin aynı veri türünde diziler olarak tanımlanan parametreleri arayın.

 @No__t_0 gibi bazı COM arabirimleri, [out] parametrelerini isteğe bağlı olarak değerlendirir. Bir nesne gerekmiyorsa, bu COM arabirimleri, [out] nesnesini oluşturmak yerine bu parametrenin değeri olarak `null` bir işaretçi döndürür. Bu tasarım gereğidir. Bu arabirimler için `null` işaretçileri, VSPackage 'ın doğru davranışının bir parçası olarak kabul edilir ve hiçbir hata döndürülmez.

 CLR bir [out] parametresinin değerine `null` izin vermediğinden, bu arabirimlerin tasarlanan davranışının bir kısmı yönetilen kod içinde doğrudan kullanılamaz. Etkilenen arabirimlerin [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] birlikte çalışma derleme yöntemleri, CLR `null` dizilerinin geçirilmesine izin verdiğinden ilgili parametreleri diziler olarak tanımlayarak soruna geçici olarak çalışır.

 Bu yöntemlerin yönetilen uygulamaları döndürülecek bir şey olmadığında parametreye bir `null` dizisi koymalıdır. Aksi takdirde, doğru türde tek öğeli bir dizi oluşturun ve dönüş değerini diziye koyun.

 İsteğe bağlı [out] parametrelerine sahip arabirimlerden bilgi alan yönetilen yöntemler, parametreyi bir dizi olarak alır. Yalnızca dizinin ilk öğesinin değerini inceleyin. @No__t_0 değilse, ilk öğeyi özgün parametre gibi değerlendirin.

## <a name="passing-constants-in-pointer-parameters"></a>Işaretçi parametrelerinde sabitleri geçirme
 COM arabiriminde [in] işaretçileri olarak tanımlanan, ancak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] birlikte çalışma derleme yöntemi prototipinin <xref:System.IntPtr> türü olarak tanımlanan parametreleri arayın.

 Bir COM arabirimi bir nesne işaretçisi yerine 0,-1 veya-2 gibi özel bir değer geçirdiğinde benzer bir sorun oluşur. @No__t_0 aksine CLR, sabitlerin nesne olarak yayınlaneklenmesine izin vermez. Bunun yerine, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] birlikte çalışma derlemesi, parametreyi bir <xref:System.IntPtr> türü olarak tanımlar.

 Bu yöntemlerin yönetilen uygulamaları, <xref:System.IntPtr> sınıfında, bir nesneden veya bir tamsayı sabitinden bir <xref:System.IntPtr> oluşturmak için hem `int` hem de `void *` oluşturucuları vardır.

 Bu türün <xref:System.IntPtr> parametrelerini alan yönetilen yöntemler, sonuçları işlemek için <xref:System.IntPtr> türü dönüştürme işleçlerini kullanmalıdır. @No__t_0 önce `int` ' e dönüştürün ve ilgili tamsayı sabitlerine karşı test edin. Hiçbir değer eşleşmezse, gerekli türdeki bir nesneye dönüştürün ve devam edin.

 Bunun örnekleri için bkz. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>.

## <a name="ole-return-values-passed-as-out-parameters"></a>OLE dönüş değerleri [out] parametresi olarak geçirildi
 COM arabiriminde `retval` dönüş değeri olan, ancak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] birlikte çalışabilirlik derleme yöntemi prototipinin `int` bir dönüş değerine ve ek [out] dizi parametresine sahip olan yöntemleri arayın. @No__t_0 birlikte çalışma derleme yöntemi prototiptürleri COM arabirimi yöntemlerinden daha fazla parametre içerdiğinden, bu yöntemlerin özel bir işleme gerektirmesinin açık olması gerekir.

 OLE etkinliğiyle ilgilenen birçok COM arabirimi, arabirimin `retval` dönüş değerinde depolanan çağıran programa OLE durumu hakkında bilgi gönderir. Bir dönüş değeri kullanmak yerine, karşılık gelen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] birlikte çalışma derleme yöntemleri, bilgileri bir [out] dizi parametresinde depolanan çağıran programa geri gönderir.

 Bu yöntemlerin yönetilen uygulamaları, [out] parametresiyle aynı türde tek öğeli bir dizi oluşturmalı ve bu parametreyi parametreye koymalıdır. Dizi öğesinin değeri uygun COM `retval` aynı olmalıdır.

 Bu türün arabirimlerini çağıran yönetilen yöntemler, ilk öğeyi [out] dizisinin dışına çekmelidir. Bu öğe, karşılık gelen COM arabiriminden bir `retval` dönüş değeri gibi kabul edilebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Yönetilmeyen Kod ile Birlikte Çalışma](/dotnet/framework/interop/index)