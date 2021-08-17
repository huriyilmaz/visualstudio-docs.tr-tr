---
title: Visual Studio Birlikte Çalışma Derlemelerini | Microsoft Docs
description: Birlikte çalışma Visual Studio yönetilen uygulamaların genişletilebilirlik sağlayan COM arabirimlerine erişmesine nasıl Visual Studio öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 03538a95d430f14118b253bf6b9fa612e374a23c7213666bb3e7c32cbecfb0c8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121375617"
---
# <a name="using-visual-studio-interop-assemblies"></a>Visual Studio Birlikte Çalışma Bütünleştirilmiş Kodlarını Kullanma
Visual Studio birlikte çalışma derlemeleri, yönetilen uygulamaların daha fazla genişletilebilirlik sağlayan COM arabirimlerine Visual Studio sağlar. Düz COM arabirimleri ile bunların birlikte çalışma sürümleri arasında bazı farklar vardır. Örneğin, HRESULT'ler genellikle int değerleri olarak temsil edilir ve özel durumlar ile aynı şekilde ele alınarak parametrelerin (özellikle de dışı parametreler) farklı şekilde ele alınarak ele alınları gerekir.

## <a name="handling-hresults-returned-to-managed-code-from-com"></a>COM'dan Yönetilen Koda Döndürülen HRESULT'ları İşleme
 Yönetilen koddan COM arabirimini çağırarak HRESULT değerini inceler ve gerekirse bir özel durum oluşturur. <xref:Microsoft.VisualStudio.ErrorHandler>sınıfı, geçirilen HRESULT değerine bağlı olarak bir COM özel durumu oluşturur <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> yöntemini içerir.

 Varsayılan olarak, <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> sıfırdan küçük bir değere sahip bir HRESULT geçiriken bir özel durum oluşturur. Bu tür HRESULT'ların kabul edilebilir değerler olduğu ve özel durumların atılamaz olduğu durumlarda, değerler test edildikten sonra ek HRESULTS <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> değerlerine geçirilebilir. Test edilen HRESULT açıkça geçirilen tüm HRESULT değerleriyle eş <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> olursa, özel durum olmaz.

> [!NOTE]
> sınıfı, ve gibi yaygın HRESULTS sabitlerini ve <xref:Microsoft.VisualStudio.VSConstants> <xref:Microsoft.VisualStudio.VSConstants.S_OK> örneğin ve <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] HRESULTS'i <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT> içerir. <xref:Microsoft.VisualStudio.VSConstants> ayrıca <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> COM'daki BAŞARILI ve BAŞARILI makrolara karşılık gelen ve yöntemlerini sağlar.

 Örneğin, kabul edilebilir bir dönüş değeri olan ancak sıfırdan küçük diğer tüm HRESULT'ların bir hatayı temsil ettiği <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> aşağıdaki işlev çağrısını göz önünde bulundurarak.

 :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb" id="Snippet1":::
 :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs" id="Snippet1":::

 Birden fazla kabul edilebilir dönüş değeri varsa, çağrısında listesine ek HRESULT değerleri <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> ekleyebilirsiniz.

 :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb" id="Snippet2":::
 :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs" id="Snippet2":::

## <a name="returning-hresults-to-com-from-managed-code"></a>Yönetilen Koddan COM'a HRESULTS Döndüren
 Özel durum oluşmazsa, yönetilen kod <xref:Microsoft.VisualStudio.VSConstants.S_OK> onu çağıran COM işlevine geri döner. COM birlikte çalışma, yönetilen kodda kesin olarak yazabilen yaygın özel durumları destekler. Örneğin, kabul edilemez bir bağımsız değişken alan `null` bir yöntem bir <xref:System.ArgumentNullException> atar.

 Hangi özel durumun atacakları kesin değil ancak COM'a geri dönmek istediğiniz HRESULT'un ne olduğunu biliyorsanız, uygun bir özel durum için <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> yöntemini kullanabilirsiniz. Bu, standart olmayan bir hatayla bile çalışır, örneğin <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> , . <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> , geçirilen HRESULT'un türü kesin olarak kesin olan bir özel durumla eşlemeye çalışır. Yoksa, bunun yerine genel bir COM özel durumu oluşturur. Nihai sonuç, yönetilen koddan geçiş yapılan HRESULT'un onu <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> çağıran COM işlevine döndürüleceğidir.

> [!NOTE]
> Özel durumlar performansı tehlikeye atar ve anormal program koşullarını göstermek için tasarlanmıştır. Genellikle oluşan koşullar, oluşan bir özel durum yerine satır içinde iş gerekir.

## <a name="iunknown-parameters-passed-as-type-void"></a>Type void olarak geçirilen IUnknown parametreleri**
 COM arabiriminde tür olarak tanımlanan ancak birlikte çalışma derleme yöntemi prototipi içinde olarak tanımlanan [out] `void **` `[``iid_is``]` parametrelerini [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ara.

 Bazen COM arabirimi bir nesnesi `IUnknown` oluşturur ve COM arabirimi bunu türü olarak iletir. `void **` Bu arabirimler özellikle önemlidir çünkü değişkeni IDL'de [out] olarak tanımlanmışsa, nesne `IUnknown` yöntemiyle başvuru olarak `AddRef` sayılır. Nesne doğru şekilde işlanmazsa bir bellek sızıntısı oluşur.

> [!NOTE]
> COM arabirimi tarafından oluşturulan ve [out] değişkensinde döndürülen bir nesne, açıkça serbest `IUnknown` bırakılamazsa bellek sızıntısına neden olur.

 Bu tür nesneleri işlemek için yönetilen yöntemler bir <xref:System.IntPtr> nesnenin işaretçisi olarak davranmalı ve nesnesini almak için yöntemini `IUnknown` <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> çağırarak. Ardından çağıranın dönüş değerini uygun olan türe attırmaları gerekir. Nesne artık gerekli olmadığı zaman serbest bırakmak <xref:System.Runtime.InteropServices.Marshal.Release%2A> için çağrısında bulundurabilirsiniz.

 Aşağıda yöntemini çağırma ve nesneyi <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> doğru işleme örneği ve ardından ve bir örnek ve ardından ve `IUnknown` vesnesi ve ardından 300000000000000000000000

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
> Aşağıdaki yöntemler, nesne işaretçilerini `IUnknown` türü olarak <xref:System.IntPtr> iletir. Bunları bu bölümde açıklandığı gibi işle.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>

## <a name="optional-out-parameters"></a>İsteğe bağlı [out] Parametreler
 COM arabiriminde [out] veri türü ( , ve gibi) olarak tanımlanan ancak birlikte çalışma derleme yöntemi prototipi içinde aynı veri türüne sahip diziler olarak tanımlanan parametreleri `int` `object` [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ara.

 gibi bazı COM arabirimleri <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> [out] parametrelerini isteğe bağlı olarak işler. Bir nesne gerekli yoksa, bu COM arabirimleri [out] nesnesini oluşturmak yerine bu parametrenin `null` değeri olarak bir işaretçisi geri döner. Bu tasarım gereğidir. Bu arabirimler için işaretçiler VSPackage'ın doğru davranışının bir parçası olarak `null` varsayılır ve hiçbir hata döndürülz.

 CLR bir [out] parametresinin değerinin olmasına izin vermey olduğundan, bu arabirimlerin tasarlanan davranışının bir parçası doğrudan yönetilen kod `null` içinde kullanılamaz. ClR dizilerin geçişe izin verir çünkü etkilenen arabirimler için birlikte çalışma derleme yöntemleri, ilgili parametreleri dizi olarak tanımlayarak sorunu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] `null` geçici olarak işler.

 Bu yöntemlerin yönetilen uygulamaları, döndürülecek bir şey söz konusu olduğunda `null` parametresine bir dizi koymalı. Aksi takdirde, doğru türde bir tek öğeli dizi oluşturun ve diziye dönüş değerini yazın.

 İsteğe bağlı [out] parametrelerine sahip arabirimlerden bilgi alan yönetilen yöntemler, parametreyi dizi olarak alır. Dizinin ilk öğesinin değerini incelemelisiniz. değilse, `null` ilk öğeyi özgün parametre gibi işle.

## <a name="passing-constants-in-pointer-parameters"></a>İşaretçi Parametrelerinde Sabitleri Geçirme
 COM arabiriminde [in] işaretçileri olarak tanımlanan ancak birlikte çalışma derleme yöntemi prototipinin bir türü <xref:System.IntPtr> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] olarak tanımlanan parametreleri ara.

 Com arabirimi nesne işaretçisi yerine 0, -1 veya -2 gibi özel bir değer geçtiğinde de benzer bir sorun oluşur. 'den [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] farklı olarak, CLR sabitlerin nesne olarak at olmasına izin vermez. Bunun yerine, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] birlikte çalışma derlemesi parametreyi bir tür olarak <xref:System.IntPtr> tanımlar.

 Bu yöntemlerin yönetilen uygulamaları, sınıfın bir nesnesinden veya tamsayı sabiti oluşturmak için uygun şekilde hem hem de oluşturuculara sahip olması <xref:System.IntPtr> `int` `void *` <xref:System.IntPtr> avantajından yararlanmalıdır.

 Bu tür parametreleri alan <xref:System.IntPtr> yönetilen yöntemler, sonuçları işlemek için <xref:System.IntPtr> tür dönüştürme işleçlerini kullan olmalıdır. İlk olarak değerini <xref:System.IntPtr> değerine `int` dönüştürecek ve ilgili tamsayı sabitlerine karşı test eder. Hiçbir değer eşleşmezse, bunu gerekli türe sahip bir nesneye dönüştür ve devam.

 Bunun örnekleri için bkz. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> .

## <a name="ole-return-values-passed-as-out-parameters"></a>OLE Dönüş Değerleri [out] Parametreleri Olarak Geçirildi
 COM arabiriminde dönüş değeri olan ancak birlikte çalışma derleme yöntemi prototipi içinde bir dönüş değeri ve ek [out] dizi parametresine sahip `retval` `int` yöntemleri [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ara. Birlikte çalışma derleme yöntemi prototipleri COM arabirim yöntemlerinden bir tane daha fazla parametreye sahip olduğundan, bu yöntemlerin özel işleme [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gerektirmesi net olmalıdır.

 OLE etkinliğiyle ilgili birçok COM arabirimi, OLE durumu hakkında bilgileri arabirimin dönüş değerinde depolanan `retval` çağırma programına geri gönderir. Dönüş değeri kullanmak yerine, karşılık gelen birlikte çalışma derleme yöntemleri bilgileri [out] dizi parametresinde depolanan [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] çağırma programına geri gönderir.

 Bu yöntemlerin yönetilen uygulamaları [out] parametresiyle aynı türde tek öğeli bir dizi oluşturmalı ve bunu parametresine koymalı. Dizi öğesinin değeri, uygun COM ile aynı olması `retval` gerekir.

 Bu tür arabirimleri çağıran yönetilen yöntemlerin ilk öğeyi [out] diziden çekmesi gerekir. Bu öğe, karşılık gelen COM arabiriminden `retval` bir dönüş değeri gibi kabul edilebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Yönetilmeyen Kod ile Birlikte Çalışma](/dotnet/framework/interop/index)
