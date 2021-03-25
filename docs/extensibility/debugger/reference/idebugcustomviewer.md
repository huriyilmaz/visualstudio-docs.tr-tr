---
description: Bu arabirim, bir ifade değerlendiricisi (EE) bir özelliğin değerini herhangi bir biçimde görüntülemesini sağlar.
title: IDebugCustomViewer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer
helpviewer_keywords:
- IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3c44706549d7d638a8fbf3686de57780ffa6bf4e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077557"
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
Bu arabirim, bir ifade değerlendiricisi (EE) bir özelliğin değerini herhangi bir biçimde görüntülemesini sağlar.

## <a name="syntax"></a>Syntax

```
IDebugCustomViewer : IUknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
Bir EE, bir özelliğin değerini özel bir biçimde göstermek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
COM işlevine yapılan bir çağrı `CoCreateInstance` Bu arabirimi başlatır. `CLSID`Geçilen öğesine, `CoCreateInstance` kayıt defterinden alınır. [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) çağrısı, kayıt defterindeki konumunu alır. Ayrıntılar ve örnek için bkz. açıklamalar.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
Bu arabirim aşağıdaki yöntemi uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|Verilen bir değeri göstermek için gereken her şey olur.|

## <a name="remarks"></a>Açıklamalar
Bu arabirim, bir özelliğin değeri normal yollarla (örneğin, bir veri tablosu veya başka bir karmaşık özellik türü) görüntülenemediğinde kullanılır. `IDebugCustomViewer`Arayüzden bağımsız olarak belirli bir türdeki verileri görüntülemek için bir dış program olan, arabirim tarafından temsil edilen özel bir görüntüleyici, bir tür görselleştiricisinden farklıdır. EE, bu EE 'a özgü özel bir Görüntüleyici uygular. Kullanıcı hangi tür Görselleştirici kullanacağınızı seçer, bir tür görselleştiricisi veya özel bir Görüntüleyici olur. Bu işlemle ilgili ayrıntılar için bkz. [verileri görselleştirme ve görüntüleme](../../../extensibility/debugger/visualizing-and-viewing-data.md) .

Özel bir görüntüleyici, EE ile aynı şekilde kaydedilir ve bu nedenle dil GUID 'SI ve satıcı GUID 'SI gerektirir. Tam ölçüm (veya kayıt defteri giriş adı) yalnızca EE için bilinir. Bu ölçüm [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) yapısında döndürülür, bu da [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)çağrısıyla döndürülür. Ölçümde depolanan değer, `CLSID` com `CoCreateInstance` işlevinin işlevine geçirilir (örneğe bakın).

[Hata ayıklama işlevi Için SDK yardımcıları](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) , `SetEEMetric` özel bir görüntüleyiciyi kaydetmek için kullanılabilir. `Debugging SDK Helpers`Özel görüntüleyiciye ihtiyacı olan belirli kayıt defteri anahtarlarının "Expression değerlendiricileri" kayıt defteri bölümüne bakın. Özel görüntüleyicisinin yalnızca bir metrik (EE 'ın uygulayıcısı tarafından tanımlanır), bir ifade değerlendiricisi ise önceden tanımlanmış birkaç ölçüm gerektirdiğini unutmayın.

Normal olarak, bir özel Görüntüleyici verilerin salt okunurdur görünümünü sağlar, çünkü [DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) 'A sağlanan [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) arabirimi özelliğin değerini dize olarak değiştirme yöntemi değildir. Rastgele veri bloklarının değiştirilmesini desteklemek için, EE arabirimini uygulayan aynı nesne üzerinde özel bir arabirim uygular `IDebugProperty3` . Bu özel arabirim daha sonra rastgele bir veri bloğunu değiştirmek için gereken yöntemleri sağlar.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Örnek
Bu örnek, bu özellikte özel görüntüleyicilerin varsa, özelliğin ilk özel görüntüleyicisinin nasıl alınacağını gösterir.

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
