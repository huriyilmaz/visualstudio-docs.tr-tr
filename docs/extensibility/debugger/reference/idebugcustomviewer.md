---
title: IDebugCustomViewer | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer
helpviewer_keywords:
- IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c44d2289180ece35725b9258e9d20abeb3a4cac3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732424"
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
Bu arabirim, bir ifade değerlendiricisinin (EE) bir özelliğin değerini ne biçim gerekirse görüntülemesini sağlar.

## <a name="syntax"></a>Sözdizimi

```
IDebugCustomViewer : IUknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
EE, bir özelliğin değerini özel bir biçimde görüntülemek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
COM `CoCreateInstance` işlevine yapılan bir çağrı bu arabirimi anında yönlendirir. `CLSID` Geçirilen kayıt `CoCreateInstance` defterinden elde edilir. [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) için bir çağrı kayıt defterinde yer alır. Ayrıntılar ve Örnek için Açıklamalar'a bakın.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
Bu arabirim aşağıdaki yöntemi uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|Belirli bir değeri görüntülemek için ne gerekiyorsa yapar.|

## <a name="remarks"></a>Açıklamalar
Bu arabirim, bir özelliğin değeri normal yollarla görüntülenemediğinde (örneğin, bir veri tablosu veya başka bir karmaşık özellik türüyle) kullanılır. `IDebugCustomViewer` Arayüz tarafından temsil edildiği üzere özel bir görüntüleyici, EE'den bağımsız olarak belirli bir türdeki verileri görüntülemek için harici bir program olan tür görselleştiricisinden farklıdır. EE, bu EE'ye özgü özel bir görüntüleyici uygular. Kullanıcı, tür görselleştiricisi veya özel görüntüleyici olmak üzere hangi tür de görselleştirici kullanılacağını seçer. Bu işlemle ilgili ayrıntılar için [Verileri Görselleştirme ve Görüntüleme'ye](../../../extensibility/debugger/visualizing-and-viewing-data.md) bakın.

Özel bir görüntüleyici, EE ile aynı şekilde kaydedilir ve bu nedenle bir dil GUID ve satıcı GUID gerektirir. Tam metrik (veya kayıt defteri giriş adı) yalnızca EE tarafından bilinir. Bu metrik, [getCustomViewerList'e](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)yapılan bir çağrıyla döndürülen [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) yapısında döndürülür. Metrikte depolanan değer, `CLSID` COM `CoCreateInstance` işlevine geçirilen değerdir (Örnek'e bakın).

Hata Ayıklama işlevi [için SDK Yardımcıları,](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetEEMetric`özel bir görüntüleyici kaydetmek için kullanılabilir. Özel bir görüntüleyenin ihtiyaç duyduğu `Debugging SDK Helpers` belirli kayıt defteri anahtarları için "İfade Değerlendiriciler" kayıt defteri bölümüne bakın. Özel bir görüntüleyicinin yalnızca bir metriğe (EE'nin uygulayıcısı tarafından tanımlanan) ihtiyaç duyduğuna, ifade değerlendiricinin ise önceden tanımlanmış birkaç ölçüm gerektirdiğini unutmayın.

Normalde, [DisplayValue'a](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) sağlanan [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) arabirimi dize dışında özelliğin değerini değiştirmek için hiçbir yöntem olmadığından, özel bir görüntüleyici verilerin salt okunur görünümünü sağlar. Değişen rasgele veri bloklarını desteklemek için, EE `IDebugProperty3` arabirimi uygulayan nesne üzerinde özel bir arabirim uygular. Bu özel arabirim daha sonra rasgele bir veri bloğunu değiştirmek için gereken yöntemleri sağlar.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Örnek
Bu örnek, bu özelliğin özel görüntüleyicisi varsa, ilk özel görüntüleyenin bir özellikten nasıl alınabildiğini gösterir.

```cpp
IDebugCustomViewer *GetFirstCustomViewer(IDebugProperty2 *pProperty)
{
    // This string is typically defined globally.  For this example, it
    // is defined here.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";
    IDebugCustomViewer *pViewer = NULL;
    if (pProperty != NULL) {
        CComQIPtr<IDebugProperty3> pProperty3(pProperty);
        if (pProperty3 != NULL) {
            HRESULT hr;
            ULONG viewerCount = 0;
            hr = pProperty3->GetCustomViewerCount(&viewerCount);
            if (viewerCount > 0) {
                ULONG viewersFetched = 0;
                DEBUG_CUSTOM_VIEWER viewerInfo = { 0 };
                hr = pProperty3->GetCustomViewerList(0,
                                                     1,
                                                     &viewerInfo,
                                                     &viewersFetched);
                if (viewersFetched == 1) {
                    CLSID clsidViewer = { 0 };
                    CComPtr<IDebugCustomViewer> spCustomViewer;
                    // Get the viewer's CLSID from the registry.
                    ::GetEEMetric(viewerInfo.guidLang,
                                  viewerInfo.guidVendor,
                                  viewerInfo.bstrMetric,
                                  &clsidViewer,
                                  strRegistrationRoot);
                    if (!IsEqualGUID(clsidViewer,GUID_NULL)) {
                        // Instantiate the custom viewer.
                        spCustomViewer.CoCreateInstance(clsidViewer);
                        if (spCustomViewer != NULL) {
                            pViewer = spCustomViewer.Detach();
                        }
                    }
                }
            }
        }
    }
    return(pViewer);
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [Hata Ayıklama için SDK Yardımcıları](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
