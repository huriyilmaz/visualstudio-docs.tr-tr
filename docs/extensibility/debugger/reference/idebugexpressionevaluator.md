---
description: Bu arabirim ifade değerlendiriciyi temsil eder.
title: IDebugExpressionEvaluator | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 41128445dca38d6d735d3dd4f83b84363bcb4989
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122138685"
---
# <a name="idebugexpressionevaluator"></a>IDebugExpressionEvaluator
> [!IMPORTANT]
> 2015 Visual Studio de ifade değerlendiricilerini uygulamanın bu yolu kullanım dışıdır. CLR ifade değerlendiricilerini uygulama hakkında bilgi için bkz. [CLR İfade Değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [Yönetilen İfade Değerlendirici Örneği.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

Bu arabirim ifade değerlendiriciyi temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugExpressionEvaluator : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
İfade değerlendiricisi bu arabirimi uygulamalı.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
Bu arabirimi elde etmek için, değerlendiricinin sınıf kimliğini (CLSID) kullanarak yöntem aracılığıyla `CoCreateInstance` ifade değerlendiricinin örneğini alın. Bkz. Örnek.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
Aşağıdaki tabloda yöntemlerini `IDebugExpressionEvaluator` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)|Bir ifade dizesini ayrıştırıldı ifadeye dönüştürür.|
|[GetMethodProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)|Bir yöntemin yerel değişkenlerini, bağımsız değişkenlerini ve diğer özelliklerini alır.|
|[GetMethodLocationProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodlocationproperty.md)|Yöntem konumunu ve uzaklığı bir bellek adresine dönüştürür.|
|[SetLocale](../../../extensibility/debugger/reference/idebugexpressionevaluator-setlocale.md)|Yazdırılabilir sonuçlar oluşturmak için hangi dilin kullanılacaklarını belirler.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugexpressionevaluator-setregistryroot.md)|Kayıt defteri kökünü ayarlar. Yan yana hata ayıklama için kullanılır.|

## <a name="remarks"></a>Açıklamalar
Tipik bir durumda, hata ayıklama altyapısı (DE), [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)çağrısının bir sonucu olarak ifade değerlendiricisini (EE) örneğini sağlar. DE, kullanmak istediği EE dilini ve satıcısını bildiği için, DE kayıt defterinden EE'nin CLSID'sini alır (Hata Ayıklama işlevi [için SDK](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) Yardımcıları, bu alma işlemiyle yardımcı `GetEEMetric` olur).

Örnek EE sonra DE, ifadeyi ayrıştırmak ve [bir IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) nesnesinde depolamak için Ayrıştır'ı arar. [](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) Daha sonra [EvaluateSync çağrısı](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) ifadeyi değerlendirir.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: ee.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Örnek
Bu örnek, kaynak kodda bir sembol sağlayıcısı ve bir adres verilen ifade değerlendiricinin nasıl örneklendiricisi olduğunu gösterir. Bu örnekte hata ayıklama kitaplığı için SDK Yardımcıları'nın `GetEEMetric` dbgmetric.lib işlevi lanmıştır. [](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)

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
