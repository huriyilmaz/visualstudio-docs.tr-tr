---
description: Hata ayıklama altyapısının ölçüm ayarlarını uzaktan okumasını sağlar.
title: IDebugSettingsCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2 interface
ms.assetid: 7e525d0b-7d7a-4d1c-8b78-e1398fa922f2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7053c45ba86f4bea54befc3bde67d831cc9c822e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168666"
---
# <a name="idebugsettingscallback2"></a>IDebugSettingsCallback2
Hata ayıklama altyapısının ölçüm ayarlarını uzaktan okumasını sağlar.

## <a name="syntax"></a>Syntax

```
IDebugSettingsCallback2D : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
Bu arabirim, oturum hata ayıklama yöneticisinin olay geri çağırması tarafından uygulanır ve hata ayıklama motorları tarafından kullanılır. Ayrıca, dbgmetric [d]. lib yerine yerel olarak da kullanılabilir.

## <a name="methods"></a>Yöntemler
Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugSettingsCallback2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[EnumEEs](../../../extensibility/debugger/reference/idebugsettingscallback2-enumees.md)|Dil ve satıcı tanımlayıcıları verilen kullanılabilir ifade değerlendiricileri numaralandırır.|
|[GetEELocalObject](../../../extensibility/debugger/reference/idebugsettingscallback2-geteelocalobject.md)|Ölçüm verilen bir ifade değerlendirici yerel nesnesi alır.|
|[GetEEMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricdword.md)|İfade değerlendiricisi 'nin belirtilen ölçüsüne karşılık gelen bir değer alır.|
|[GetEEMetricFile](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricfile.md)|Ad veya ölçüm verilen ifade değerlendirici ölçüm dosyasını alır.|
|[GetEEMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricguid.md)|Bir ifade değerlendirici ölçüsünün adına verilen benzersiz tanımlayıcıyı alır.|
|[GetEEMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricstring.md)|Adı verilen bir ifade değerlendirici ölçüsünün değer dizesini alır.|
|[GetMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricdword.md)|Bir ölçümün adını verilen değerini alır.|
|[GetMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricguid.md)|Bir ölçümün adı verilen benzersiz tanımlayıcısını alır.|
|[GetMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricstring.md)|Ölçüsünün adı verilen değer dizesini alır.|

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Örnek
Aşağıdaki örnek, bir **IDebugSettingsCallback2** nesnesini parametre olarak alan bir işlevi gösterir.

```cpp
HRESULT GetDebugSettingsCallback (IDebugSettingsCallback2 **ppCallback)
{
    HRESULT hRes = E_FAIL;

    if ( ppCallback )
    {
        if ( EVAL(m_pdec) )
            hRes = m_pdec->QueryInterface(IID_IDebugSettingsCallback2, (void **)ppCallback);
        else
            hRes = E_FAIL;
    }
    else
        hRes = E_INVALIDARG;

    return ( hRes );
}
```
