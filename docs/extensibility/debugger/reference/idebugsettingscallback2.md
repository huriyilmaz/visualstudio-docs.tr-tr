---
description: Hata ayıklama altyapısının ölçüm ayarlarını uzaktan okumasını sağlar.
title: IDebugSettingsCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2 interface
ms.assetid: 7e525d0b-7d7a-4d1c-8b78-e1398fa922f2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 32cab53c2d6a0d97ae5131994f0c63dab9d32f68ac16df9eac08cc5d1c39661e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121402239"
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
