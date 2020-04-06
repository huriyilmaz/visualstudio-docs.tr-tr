---
title: IDebugExpressionEvaluator | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator
helpviewer_keywords:
- IDebugExpressionEvaluator interface
ms.assetid: 0636d8c3-625a-49fa-94b6-516f22b7e1bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e8dd910e4edc110abb40dde14b4cb85ff54a70a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729380"
---
# <a name="idebugexpressionevaluator"></a>IDebugExpressionEvaluator
> [!IMPORTANT]
> Visual Studio 2015'te ifade değerlendiricilerinin bu şekilde uygulanması amortismana uymaktadır. CLR ifade değerlendiricilerinin uygulanması hakkında bilgi için lütfen [CLR İfade Değerlendiriciler](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [Yönetilen İfade Değerlendirici Örneği'ne](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)bakın.

Bu arabirim ifade değerlendiricisi temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IDebugExpressionEvaluator : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
İfade değerlendiricisi bu arabirimi uygulamalıdır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
Bu arabirimi elde etmek için, değerlendiricinin `CoCreateInstance` sınıf kimliğini (CLSID) kullanarak ifade değerlendiricisini yöntem le anında değerlendirin. Örnek'e bakın.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
Aşağıdaki tabloda `IDebugExpressionEvaluator`.

|Yöntem|Açıklama|
|------------|-----------------|
|[Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)|İfade dizesini ayrışmış bir ifadeye dönüştürür.|
|[GetMethodProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)|Bir yöntemin yerel değişkenlerini, bağımsız değişkenlerini ve diğer özelliklerini alır.|
|[GetMethodLocationProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodlocationproperty.md)|Yöntem konumunu ve ofset'i bellek adresine dönüştürür.|
|[Setlocale](../../../extensibility/debugger/reference/idebugexpressionevaluator-setlocale.md)|Yazdırılabilir sonuçlar oluşturmak için hangi dili kullanacağımı belirler.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugexpressionevaluator-setregistryroot.md)|Kayıt defteri kökünü ayarlar. Yan yana hata ayıklama için kullanılır.|

## <a name="remarks"></a>Açıklamalar
Tipik bir durumda, hata ayıklama motoru (DE) [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)bir çağrı sonucunda ifade değerlendirici (EE) anında . DE kullanmak istediği EE'nin dilini ve satıcısını bildiği için, DE EE'nin CLSID'sini kayıt defterinden alır [(Hata Ayıklama işlevi için SDK Yardımcıları,](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `GetEEMetric`bu alma yla yardımcı olur).

EE anında alındıktan sonra, DE [parse'yi](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) ifadeyi ayrıştırmak ve bir [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) nesnesinde depolamak için çağırır. Daha sonra, [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) için bir çağrı ifadeyi değerlendirir.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: ee.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Örnek
Bu örnek, kaynak kodunda bir sembol sağlayıcısı ve bir adres verilen ifade değerlendiricinin anlık olarak nasıl ani olacağını gösterir. Bu örnek, [Debugging](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) kitaplığı için SDK Yardımcıları, `GetEEMetric`dbgmetric.lib bir işlev kullanır.

```cpp
IDebugExpressionEvaluator GetExpressionEvaluator(IDebugSymbolProvider pSymbolProvider,
                                                 IDebugAddress *pSourceAddress)
{
    // This is typically defined globally but is specified here just
    // for this example.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";

    IDebugExpressionEvaluator *pEE = NULL;
    if (pSymbolProvider != NULL && pSourceAddress != NULL) {
        HRESULT hr         = S_OK;
        GUID  languageGuid = { 0 };
        GUID  vendorGuid   = { 0 };

        hr = pSymbolProvider->GetLanguage(pSourceAddress,
                                          &languageGuid,
                                          &vendorGuid);
        if (SUCCEEDED(hr)) {
            CLSID clsidEE = { 0 };
            CComPtr<IDebugExpressionEvaluator> spExpressionEvaluator;
            // Get the expression evaluator's CLSID from the registry.
            ::GetEEMetric(languageGuid,
                          vendorGuid,
                          metricCLSID,
                          &clsidEE,
                          strRegistrationRoot);
            if (!IsEqualGUID(clsidEE,GUID_NULL)) {
                // Instantiate the expression evaluator.
                spExpressionEvaluator.CoCreateInstance(clsidEE);
            }
            if (spExpressionEvaluator != NULL) {
                pEE = spExpressionEvaluator.Detach();
            }
        }
    }
    return pEE;
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [İfade Değerlendirme Arabirimleri](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [Hata Ayıklama için SDK Yardımcıları](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
