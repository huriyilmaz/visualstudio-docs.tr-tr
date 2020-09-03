---
title: Visual Studio birlikte çalışma derlemelerini kullanma | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5926b2cce217565c889c7ef2eeef877691101ed6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704129"
---
# <a name="using-visual-studio-interop-assemblies"></a>Visual Studio Birlikte Çalışma Bütünleştirilmiş Kodlarını Kullanma
Visual Studio birlikte çalışma derlemeleri, yönetilen uygulamaların Visual Studio genişletilebilirlik sağlayan COM arabirimlerine erişmesine izin verir. Basit COM arabirimleri ve birlikte çalışma sürümleri arasında bazı farklılıklar vardır. Örneğin, HRESULTs genellikle int değerleri olarak temsil edilir ve özel durumlarla aynı şekilde işlenmelidir ve parametreler (özellikle de çıkış parametreleri) farklı şekilde değerlendirilir.

## <a name="handling-hresults-returned-to-managed-code-from-com"></a>COM 'dan yönetilen koda döndürülen HRESULTs işleme
 Yönetilen koddan bir COM arabirimini çağırdığınızda, HRESULT değerini inceleyin ve gerekirse bir özel durum oluşturun. <xref:Microsoft.VisualStudio.ErrorHandler>Sınıfı, <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> kendısıne geçirilen HRESULT değerine bağlı olarak bir com özel durumu oluşturan yöntemini içerir.

 Varsayılan olarak, <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> sıfırdan küçük bir değere sahip BIR HRESULT geçirildiğinde bir özel durum oluşturur. Bu tür Hsonuçların kabul edilebilir değerler olduğu ve hiçbir özel durum oluşturulması gereken durumlarda, <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> değerler test edildikten sonra ek HSONUÇLARıN değerlerinin geçirilmesi gerekir. Test edilmekte olan HRESULT, açıkça geçirilen herhangi bir HRESULT değeri ile eşleşiyorsa <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> , hiçbir özel durum oluşturulmaz.

> [!NOTE]
> Sınıfı, ve gibi <xref:Microsoft.VisualStudio.VSConstants> ortak HRESULTS için sabitler içerir, örneğin, ve <xref:Microsoft.VisualStudio.VSConstants.S_OK> <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT> . <xref:Microsoft.VisualStudio.VSConstants> Ayrıca, <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> com 'daki başarılı ve başarısız makrolara karşılık gelen ve yöntemlerini de sağlar.

 Örneğin, <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> kabul edilebilir bir dönüş değeri olan, ancak sıfırdan küçük DIĞER HRESULT bir hatayı temsil eden aşağıdaki işlev çağrısını göz önünde bulundurun.

 [!code-vb[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_1.vb)]
 [!code-csharp[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_1.cs)]

 Birden fazla kabul edilebilir dönüş değeri varsa, ek HRESULT değerleri yalnızca öğesine yapılan çağrının listesine eklenebilir <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> .

 [!code-vb[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_2.vb)]
 [!code-csharp[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_2.cs)]

## <a name="returning-hresults-to-com-from-managed-code"></a>Yönetilen koddan COM 'a HRESULTS döndürme
 Özel durum oluşursa, yönetilen kod <xref:Microsoft.VisualStudio.VSConstants.S_OK> onu ÇAĞıRAN com işlevine geri döner. COM birlikte çalışması, yönetilen kodda kesin olarak belirlenmiş ortak özel durumları destekler. Örneğin, kabul edilemez bir bağımsız değişken alan bir yöntem `null` bir oluşturur <xref:System.ArgumentNullException> .

 Hangi özel durumun oluşturulması gerektiğini, ancak COM 'a geri dönmek istediğiniz HRESULT 'yi biliyorsanız, <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> uygun bir özel durum oluşturmak için yöntemini kullanabilirsiniz. Bu, standart dışı bir hata ile (örneğin,) birlikte kullanılır <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> . <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> kendisine geçirilen HRESULT 'yi kesin türü belirtilmiş bir özel durumla eşlemeye çalışır. Değilse, bunun yerine genel bir COM özel durumu oluşturur. Nihai sonuç, <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> yönetilen koddan kendisine GEÇIRDIĞINIZ HRESULT, ÇAĞıRAN com işlevine döndürülür.

> [!NOTE]
> Özel durumların performansı tehlikeye alınır ve anormal program koşullarını göstermek için tasarlanmıştır. Genellikle oluşan koşulların, oluşturulan özel durum yerine satır içi olarak işlenmesi gerekir.

## <a name="iunknown-parameters-passed-as-type-void"></a>IUnknown parametreleri void * * türü olarak geçildi
 COM arabiriminde tür olarak tanımlanan `void **` , ancak `[``iid_is``]` [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] birlikte çalışma derleme yöntemi prototipi içinde olarak tanımlanan [out] parametrelerini arayın.

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

## <a name="optional-out-parameters"></a>İsteğe bağlı [out] Parametreler
 COM arabiriminde [out] veri türü (,, vb.) olarak tanımlanan parametreleri arayın `int` `object` , ancak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] birlikte çalışma derleme yöntemi prototipde aynı veri türünde diziler olarak tanımlanır.

 Gibi bazı COM arabirimleri, <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> [out] parametrelerini isteğe bağlı olarak değerlendirir. Bir nesne gerekli değilse, bu COM arabirimleri `null` [out] nesnesini oluşturmak yerine bu parametrenin değeri olarak bir işaretçi döndürür. Bu tasarım gereğidir. Bu arabirimler için `null` işaretçiler, VSPackage 'ın doğru davranışının bir parçası olarak kabul edilir ve hiçbir hata döndürülmez.

 CLR bir [out] parametresinin değerine izin vermediğinden `null` , bu arabirimlerin tasarlanan davranışının bir kısmı yönetilen kod içinde doğrudan kullanılamaz. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Etkilenen arabirimlerin birlikte çalışma derleme yöntemleri, clr 'nin dizi geçişine izin verdiğinden ilgili parametreleri diziler olarak tanımlayarak soruna geçici olarak çalışır `null` .

 Bu yöntemlerin yönetilen uygulamaları döndürülecek bir şey olmadığında `null` parametreye bir dizi koymalıdır. Aksi takdirde, doğru türde tek öğeli bir dizi oluşturun ve dönüş değerini diziye koyun.

 İsteğe bağlı [out] parametrelerine sahip arabirimlerden bilgi alan yönetilen yöntemler, parametreyi bir dizi olarak alır. Yalnızca dizinin ilk öğesinin değerini inceleyin. Değilse `null` , ilk öğeyi özgün parametresi gibi değerlendirin.

## <a name="passing-constants-in-pointer-parameters"></a>Işaretçi parametrelerinde sabitleri geçirme
 COM arabiriminde [in] işaretçileri olarak tanımlanan, ancak <xref:System.IntPtr> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] birlikte çalışma derleme yöntemi prototipte bir tür olarak tanımlanmış parametreleri arayın.

 Bir COM arabirimi bir nesne işaretçisi yerine 0,-1 veya-2 gibi özel bir değer geçirdiğinde benzer bir sorun oluşur. Farklı olarak [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] , clr sabitler nesne olarak atama yapmasına izin vermez. Bunun yerine, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] birlikte çalışma derlemesi parametreyi bir tür olarak tanımlar <xref:System.IntPtr> .

 Bu yöntemlerin yönetilen uygulamaları, bir <xref:System.IntPtr> `int` `void *` <xref:System.IntPtr> nesneden veya bir tamsayı sabitinden (uygun şekilde) oluşturmak için, sınıfın hem hem de oluşturuculara sahip olduğundan emin olmalıdır.

 Bu türün parametrelerini alan yönetilen yöntemler, <xref:System.IntPtr> <xref:System.IntPtr> sonuçları işlemek için tür dönüştürme işleçlerini kullanmalıdır. Önce öğesini <xref:System.IntPtr> öğesine dönüştürüp `int` ilgili tamsayı sabitlerine göre test edin. Hiçbir değer eşleşmezse, gerekli türdeki bir nesneye dönüştürün ve devam edin.

 Bunun örnekleri için bkz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> . ve.

## <a name="ole-return-values-passed-as-out-parameters"></a>OLE dönüş değerleri [out] parametresi olarak geçirildi
 `retval`Com arabiriminde dönüş değeri olan, ancak `int` [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] birlikte çalışabilirlik derleme yöntemi prototipinin bir dönüş değerine ve ek [out] dizi parametresine sahip olan yöntemleri arayın. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Birlikte çalışma bütünleştirilmiş kod yöntemi prototiptürleri com arabirimi yöntemlerinden daha fazla parametre içerdiğinden, bu yöntemlerin özel bir işleme gerektirmesinin açık olması gerekir.

 OLE etkinliğiyle ilgilenen birçok COM arabirimi, OLE durumu hakkında bilgileri arabirimin dönüş değerinde depolanan çağıran programa geri gönderir `retval` . Bir dönüş değeri kullanmak yerine, karşılık gelen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] birlikte çalışma derleme yöntemleri, bilgileri bir [out] dizi parametresinde depolanan çağıran programa geri gönderir.

 Bu yöntemlerin yönetilen uygulamaları, [out] parametresiyle aynı türde tek öğeli bir dizi oluşturmalı ve bu parametreyi parametreye koymalıdır. Dizi öğesinin değeri uygun COM ile aynı olmalıdır `retval` .

 Bu türün arabirimlerini çağıran yönetilen yöntemler, ilk öğeyi [out] dizisinin dışına çekmelidir. Bu öğe `retval` , karşılık gelen com arabiriminden bir dönüş değeri gibi kabul edilebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Yönetilmeyen Kod ile Birlikte Çalışma](/dotnet/framework/interop/index)
