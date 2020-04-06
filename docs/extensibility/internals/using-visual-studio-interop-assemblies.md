---
title: Visual Studio Interop Montajları Kullanma | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704129"
---
# <a name="using-visual-studio-interop-assemblies"></a>Visual Studio Birlikte Çalışma Bütünleştirilmiş Kodlarını Kullanma
Visual Studio interop derlemeleri, yönetilen uygulamaların Visual Studio genişletilebilirliğini sağlayan COM arabirimlerine erişmesine olanak tanır. Düz COM arabirimleri ve interop sürümleri arasında bazı farklılıklar vardır. Örneğin, HRESULTs genellikle int değerleri olarak temsil edilir ve özel durumlar olarak aynı şekilde ele alınması gerekir ve parametreler (özellikle dışarı parametreleri) farklı tedavi edilir.

## <a name="handling-hresults-returned-to-managed-code-from-com"></a>COM'dan Yönetilen Koda Dönen HRESULT'ların İşlemi
 Yönetilen koddan COM arabirimi çağırdığınızda, HRESULT değerini inceleyin ve gerekirse bir özel durum atın. Sınıf, <xref:Microsoft.VisualStudio.ErrorHandler> ona <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> geçen HRESULT'In değerine bağlı olarak com özel durumu atan yöntemi içerir.

 Varsayılan olarak, <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> değeri sıfırdan az olan bir HRESULT geçirildiğinde bir özel durum atar. Bu tür HRESULTs kabul edilebilir değerler ve hiçbir istisna atılması gereken durumlarda, <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> ek HRESULTS değerleri değerleri test edildikten sonra geçirilmelidir. Test edilen HRESULT açıkça geçirilen herhangi bir <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>HRESULT değerleriyle eşleşirse, hiçbir istisna atılmaz.

> [!NOTE]
> Sınıf, <xref:Microsoft.VisualStudio.VSConstants> örneğin <xref:Microsoft.VisualStudio.VSConstants.S_OK> <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>ortak HRESULTS ve , [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> ve HRESULTS, örneğin ve <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>. <xref:Microsoft.VisualStudio.VSConstants>ayrıca COM'daki <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> BAŞARILI ve <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> BAŞARILI makrolara karşılık gelen ve yöntemler sağlar.

 Örneğin, kabul edilebilir bir iade <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> değeri olan ancak sıfırdan küçük başka bir HRESULT'in bir hatayı temsil ettiği aşağıdaki işlev çağrısını düşünün.

 [!code-vb[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_1.vb)]
 [!code-csharp[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_1.cs)]

 Birden fazla kabul edilebilir iade değeri varsa, ek HRESULT değerleri sadece çağrıda <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>listeye eklenebilir .

 [!code-vb[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_2.vb)]
 [!code-csharp[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_2.cs)]

## <a name="returning-hresults-to-com-from-managed-code"></a>Yönetilen Koddan HRESULTS'in COM'a döndürülme
 Özel durum oluşmazsa, yönetilen <xref:Microsoft.VisualStudio.VSConstants.S_OK> kod onu çağıran COM işlevine geri döner. COM interop, yönetilen kodda güçlü bir şekilde yazılan genel özel durumları destekler. Örneğin, kabul edilemez `null` bir bağımsız değişken <xref:System.ArgumentNullException>alan bir yöntem .

 Hangi özel durumu atacağınız emin değilseniz, ancak COM'a dönmek istediğiniz HRESULT'ı biliyorsanız, uygun bir özel durum atmak için <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> yöntemi kullanabilirsiniz. Bu, örneğin standart olmayan bir hatayla bile <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>çalışır. <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>güçlü bir şekilde yazılan bir özel durum için geçirilen HRESULT haritasını çıkarma girişimleri. Yapamıyorsa, bunun yerine genel bir COM özel durum atar. Nihai sonuç, yönetilen <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> koddan geçtiğiniz HRESULT'in onu çağıran COM işlevine döndürülmesidir.

> [!NOTE]
> Özel durumlar performansı tehlikeye atmaktadır ve anormal program koşullarını belirtmek için tasarlanmıştır. Sık sık oluşan koşullar, atılan bir özel durum yerine satır içinde işlenmelidir.

## <a name="iunknown-parameters-passed-as-type-void"></a>IBilinmeyen parametreler IType void olarak geçti**
 COM arabiriminde tür `void **` olarak tanımlanan ancak interop montaj yöntemi `[``iid_is``]` prototipinde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tanımlanan [out] parametrelerine bakın.

 Bazen, com arabirimi `IUnknown` bir nesne oluşturur ve COM arabirimi daha sonra türü `void **`olarak geçer. Değişken IDL'de [out] olarak tanımlanırsa, `IUnknown` nesne `AddRef` yöntemle referans sayılır, çünkü bu arabirimler özellikle önemlidir. Nesne doğru şekilde işlenmezse bellek sızıntısı oluşur.

> [!NOTE]
> COM `IUnknown` arabirimi tarafından oluşturulan ve [out] değişkeninde döndürülen bir nesne, açıkça serbest bırakılmadığı takdirde bellek sızıntısına neden olur.

 Bu tür nesneleri işleyen yönetilen <xref:System.IntPtr> yöntemler bir `IUnknown` nesneye işaretçi <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> olarak ele almalı ve nesneyi elde etmek için yöntemi çağırmalıdır. Arayan daha sonra uygun olan türe iade değerini atmalıdır. Nesneye artık gerek kalmadığında, nesneyi serbest bırakmak için arayın. <xref:System.Runtime.InteropServices.Marshal.Release%2A>

 Aşağıdaki <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> yöntem arama ve nesneyi `IUnknown` doğru işleme bir örnektir:

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
> Aşağıdaki yöntemlerin nesne `IUnknown` işaretçileri türü <xref:System.IntPtr>olarak geçtiği bilinmektedir. Bu bölümde açıklandığı gibi bunları ele alın.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>

## <a name="optional-out-parameters"></a>İsteğe bağlı [out] Parametreleri
 COM arabiriminde [çıkış] veri türü`int`(, , `object`vb.) olarak tanımlanan, ancak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interop montaj yöntemi prototipinde aynı veri türündeki diziler olarak tanımlanan parametreleri arayın.

 Bazı COM arabirimleri, <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>örneğin, [dışarı] parametreleri isteğe bağlı olarak ele. Bir nesne gerekli değilse, bu COM `null` arabirimleri [out] nesnesini oluşturmak yerine bu parametrenin değeri olarak bir işaretçi döndürer. Bu tasarım gereğidir. Bu arabirimler `null` için işaretçiler VSPackage'ın doğru davranışının bir parçası olarak kabul edilir ve hiçbir hata döndürülür.

 CLR bir [out] parametresinin değerinin bulunmasına `null`izin vermeyince, bu arabirimlerin tasarlanmış davranışının bir parçası doğrudan yönetilen kod içinde kullanılamaz. ClR [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] `null` dizilerin geçişine izin verdiğinden, etkilenen arabirimler için interop derleme yöntemleri, ilgili parametreleri dizi olarak tanımlayarak sorunu çözer.

 Döndürülecek bir şey olmadığında, `null` bu yöntemlerin yönetilen uygulamaları parametreye bir dizi koymalıdır. Aksi takdirde, doğru türde tek öğeli bir dizi oluşturun ve diziye iade değeri koyun.

 İsteğe bağlı [çıkış] parametreleri olan arabirimlerden bilgi alan yönetilen yöntemler parametreyi bir dizi olarak alır. Dizinin ilk öğesinin değerini incelemen izniniz. `null`Değilse, ilk öğeyi orijinal parametreyonmuş gibi davranın.

## <a name="passing-constants-in-pointer-parameters"></a>İşaretçi Parametrelerinde Sabitleri Geçirme
 COM arabiriminde [in] işaretçileri olarak tanımlanan, ancak <xref:System.IntPtr> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interop derleme yöntemi prototipinde bir tür olarak tanımlanan parametreleri arayın.

 Benzer bir sorun, com arabirimi nesne işaretçisi yerine 0, -1 veya -2 gibi özel bir değerden geçtiğinde oluşur. Bunun [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]aksine, CLR sabitlerin nesne olarak döküme izin vermez. Bunun yerine, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interop derlemesi parametreyi bir <xref:System.IntPtr> tür olarak tanımlar.

 Bu yöntemlerin yönetilen <xref:System.IntPtr> uygulamaları, sınıfın bir nesne den `int` `void *` veya tamsayı sabitinden, uygun şekilde bir <xref:System.IntPtr> nesne veya tamsayı sabiti oluşturmak için hem de oluşturuculara sahip olması gerçeğinden yararlanmalıdır.

 Bu tür <xref:System.IntPtr> parametreleri alan yönetilen <xref:System.IntPtr> yöntemler, sonuçları işlemek için tür dönüştürme işleçlerini kullanmalıdır. Önce <xref:System.IntPtr> dönüştürün `int` ve ilgili tümsekli sabitlere karşı test edin. Hiçbir değer eşleşmiyorsa, gerekli türdeki bir nesneye dönüştürün ve devam edin.

 Bunun örnekleri için <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> bkz. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>

## <a name="ole-return-values-passed-as-out-parameters"></a>OLE İade Değerleri [out] Parametreleri Olarak Geçti
 COM arabiriminde `retval` geri dönüş değeri olan, ancak `int` bir geri dönüş değeri ne var, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ve interop derleme yöntemi prototipinde ek [out] dizi parametresi olan yöntemleri arayın. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Interop montaj yöntemi prototipleri COM arabirim yöntemlerine göre bir parametreye sahip olduğundan, bu yöntemlerin özel işleme gerektirdiği açıktır.

 OLE etkinliğiyle ilgili birçok COM arabirimi, OLE durumu yla ilgili `retval` bilgileri arabirimin geri dönüş değerinde depolanan arama programına geri gönderir. İade değeri kullanmak yerine, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] karşılık gelen interop derleme yöntemleri bilgileri [out] dizi parametresinde depolanan arama programına geri gönderir.

 Bu yöntemlerin yönetilen uygulamaları[out] parametresi ile aynı türde tek bir öğe dizisi oluşturmalı ve parametreye koymalıdır. Dizi öğesinin değeri uygun COM `retval`ile aynı olmalıdır.

 Bu tür arabirimleri çağıran yönetilen yöntemler, [out] dizisinden ilk öğeyi çekmelidir. Bu öğe, ilgili COM arabiriminden bir `retval` geri dönüş değeri gibi davranılabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Yönetilmeyen Kod ile Birlikte Çalışma](/dotnet/framework/interop/index)
