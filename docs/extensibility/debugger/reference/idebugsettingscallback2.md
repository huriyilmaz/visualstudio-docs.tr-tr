---
title: IDebugSettingsCallback2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2 interface
ms.assetid: 7e525d0b-7d7a-4d1c-8b78-e1398fa922f2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2c85b54f92970dca5d712b827019300f850b03cc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719945"
---
# <a name="idebugsettingscallback2"></a>IDebugSettingsCallback2
Hata ayıklama motorlarının metrik ayarları uzaktan okumasını sağlar.

## <a name="syntax"></a>Sözdizimi

```
IDebugSettingsCallback2D : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
Bu arabirim, oturum hata ayıklama yöneticisinin olay geri çağırması tarafından uygulanır ve hata ayıklama motorları tarafından tüketilir. Ayrıca Dbgmetric[d].lib yerine yerel olarak kullanılabilir.

## <a name="methods"></a>Yöntemler
Aşağıdaki tabloda `IDebugSettingsCallback2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[EnumEEs](../../../extensibility/debugger/reference/idebugsettingscallback2-enumees.md)|Dil ve satıcı tanımlayıcıları verilen kullanılabilir ifade değerlendiricilerini oyalar.|
|[GetEELocalObject](../../../extensibility/debugger/reference/idebugsettingscallback2-geteelocalobject.md)|Metrik verilen bir ifade değerlendirici yerel nesne alır.|
|[GetEEMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricdword.md)|İfade değerlendiricinin belirtilen metnine karşılık gelen bir değer alır.|
|[GetEEMetricFile](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricfile.md)|Ad veya metrik verilen ifade değerlendirici metrik dosyasını alır.|
|[GetEEMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricguid.md)|Adı verilen bir ifade değerlendirici ölçümü için benzersiz tanımlayıcıyı alır.|
|[GetEEMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricstring.md)|Adından gelen bir ifade değerlendirici ölçümünün değer dizesini alır.|
|[GetMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricdword.md)|Adı verilen bir metnin değerini alır.|
|[GetMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricguid.md)|Adı verilen bir metnin benzersiz tanımlayıcısını alır.|
|[GetMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricstring.md)|Adı verilen ölçümün değer dizesini alır.|

## <a name="requirements"></a>Gereksinimler
Üstbilgi: Msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Örnek
Aşağıdaki örnekte, parametre olarak **iDebugSettingsCallback2** nesnesini alan bir işlev gösterilmektedir.

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
