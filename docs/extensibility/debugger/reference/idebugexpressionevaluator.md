---
description: Bu arabirim, ifade değerlendiricisi temsil eder.
title: Idebugexpressiondeğerlendirici | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator
helpviewer_keywords:
- IDebugExpressionEvaluator interface
ms.assetid: 0636d8c3-625a-49fa-94b6-516f22b7e1bc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dd14e85d279bd724dcfdf2cd9b71028ac5a4fd87
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092078"
---
# <a name="idebugexpressionevaluator"></a>IDebugExpressionEvaluator
> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için lütfen bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Bu arabirim, ifade değerlendiricisi temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugExpressionEvaluator : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
İfade değerlendirici bu arabirimi uygulamalıdır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
Bu arabirimi edinmek için, `CoCreateInstance` değerlendirici 'in sınıf kimliğini (CLSID) kullanarak yöntemi aracılığıyla ifade değerlendirici örneğini oluşturun. Örneğe bakın.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugExpressionEvaluator` .

|Yöntem|Açıklama|
|------------|-----------------|
|[Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)|Bir ifade dizesini ayrıştırılmış ifadeye dönüştürür.|
|[GetMethodProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)|Bir yöntemin yerel değişkenlerini, bağımsız değişkenlerini ve diğer özelliklerini alır.|
|[GetMethodLocationProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodlocationproperty.md)|Bir yöntem konumunu ve sapmayı bir bellek adresine dönüştürür.|
|[SetLocale](../../../extensibility/debugger/reference/idebugexpressionevaluator-setlocale.md)|Yazdırılabilir sonuçlar oluşturmak için hangi dilin kullanılacağını belirler.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugexpressionevaluator-setregistryroot.md)|Kayıt defteri kökünü ayarlar. Yan yana hata ayıklama için kullanılır.|

## <a name="remarks"></a>Açıklamalar
Tipik bir durumda, hata ayıklama altyapısı (DE), bir [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)çağrısının sonucu olarak ifade DEĞERLENDIRICI (ee) oluşturur. Ayrıca, kullanmak istediği EE 'ın dilini ve satıcısını bildiği için, kayıt defterinden EE 'ın CLSID değerini alır ( [hata ayıklama işlevi Için SDK yardımcıları](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) , `GetEEMetric` Bu almaya yardımcı olur).

EE örneği oluşturulduktan sonra, ifadeyi ayrıştırmak ve bir [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) nesnesinde saklamak Için [ayrıştırılacak](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) de çağrılır. Daha sonra, bir [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) çağrısı ifadeyi değerlendirir.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: ee. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Örnek
Bu örnek, bir sembol sağlayıcısı ve kaynak kodundaki bir adres için verilen ifade değerlendiricisi örneğini oluşturmayı gösterir. Bu örnek, `GetEEMetric` hata ayıklama kitaplığı, dbgmetric. lib [Için SDK yardımcılarından](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) bir işlevi kullanır.

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
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [Hata Ayıklama için SDK Yardımcıları](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
