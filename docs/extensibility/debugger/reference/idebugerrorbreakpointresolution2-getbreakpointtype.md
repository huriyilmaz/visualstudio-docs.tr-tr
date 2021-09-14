---
description: Kesme noktası türünü alır.
title: 'IDebugErrorBreakpointResolution2:: GetBreakpointType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorBreakpointResolution2::GetBreakpointType
helpviewer_keywords:
- IDebugErrorBreakpointResolution2::GetBreakpointType
ms.assetid: 0bdb1152-4752-4464-ae7c-6d666dc293b7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 44991f03a59e53fcdcee9d7fd163ac13635e51d5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634910"
---
# <a name="idebugerrorbreakpointresolution2getbreakpointtype"></a>IDebugErrorBreakpointResolution2::GetBreakpointType
Kesme noktası türünü alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetBreakpointType(
    BP_TYPE* pBPType
);
```

```csharp
int GetBreakpointType(
    out enum_BP_TYPE pBPType
);
```

## <a name="parameters"></a>Parametreler
`pBPType`\
dışı [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) numaralandırmasından kesme noktası türünü açıklayan bir değer döndürür.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
Bu yöntem, bağlanamayacak başarısız olan kesme noktasının türünü döndürür ve bu nedenle hata kesme noktası olayı gerektirir.

## <a name="example"></a>Örnek
Aşağıdaki örnek, `CDebugErrorBreakpointResolution` [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md) arabirimini kullanıma sunan basit bir nesne için bu yöntemin nasıl uygulanacağını gösterir.

```
HRESULT CDebugErrorBreakpointResolution::GetBreakpointType(BP_TYPE* pBPType)
{
    HRESULT hr;

    if (pBPType)
    {
        // Set default BP_TYPE.
        *pBPType = BPT_NONE;

        // Check if the BPERESI_BPRESLOCATION flag is set in BPERESI_FIELDS.
        if (IsFlagSet(m_bpErrorResolutionInfo.dwFields, BPERESI_BPRESLOCATION))
        {
            // Set the new BP_TYPE.
            *pBPType = m_bpErrorResolutionInfo.bpResLocation.bpType;
            hr = S_OK;
        }
        else
        {
            hr = E_FAIL;
        }
    }
    else
    {
        hr = E_INVALIDARG;
    }

    return hr;
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
