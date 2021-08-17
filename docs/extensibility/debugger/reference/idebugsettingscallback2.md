---
description: Hata ayıklama altyapılarının ölçüm ayarlarını uzaktan okumalarını sağlar.
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
ms.openlocfilehash: babc486a4c8d683a3557b602273bc2e165a49420
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122126264"
---
# <a name="idebugsettingscallback2"></a>IDebugSettingsCallback2
Hata ayıklama altyapılarının ölçüm ayarlarını uzaktan okumalarını sağlar.

## <a name="syntax"></a>Syntax

```
IDebugSettingsCallback2D : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
Bu arabirim, oturum hata ayıklama yöneticisinin olay geri çağırma tarafından uygulanır ve hata ayıklama altyapıları tarafından kullanılır. Dbgmetric[d].lib yerine yerel olarak da kullanılabilir.

## <a name="methods"></a>Yöntemler
Aşağıdaki tabloda yöntemlerini `IDebugSettingsCallback2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[EnumEEs](../../../extensibility/debugger/reference/idebugsettingscallback2-enumees.md)|Dil ve satıcı tanımlayıcıları verilen kullanılabilir ifade değerlendiricilerini numaralar.|
|[GetEELocalObject](../../../extensibility/debugger/reference/idebugsettingscallback2-geteelocalobject.md)|Ölçüme göre bir ifade değerlendirici yerel nesnesini alın.|
|[GetEEMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricdword.md)|İfade değerlendiricinin belirtilen ölçümüne karşılık gelen bir değer verir.|
|[GetEEMetricFile](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricfile.md)|Ad veya ölçüm verilen ifade değerlendiricisi ölçüm dosyasını alın.|
|[GetEEMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricguid.md)|Bir ifade değerlendiricisi ölçümü için benzersiz tanımlayıcıyı adına göre verir.|
|[GetEEMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricstring.md)|Bir ifade değerlendirici ölçümlerinin değer dizesini, adına göre alır.|
|[GetMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricdword.md)|Bir ölçümün adını kullanarak değerini verir.|
|[GetMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricguid.md)|Bir ölçümün adına göre benzersiz tanımlayıcısını verir.|
|[GetMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricstring.md)|Adına göre ölçümün değer dizesini alır.|

## <a name="requirements"></a>Gereksinimler
Üst bilgi: Msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Örnek
Aşağıdaki örnek, parametre olarak **IDebugSettingsCallback2 nesnesini** alan bir işlevi gösterir.

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
