---
title: FRAMEINFO | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO
helpviewer_keywords:
- FRAMEINFO structure
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c40361a9739bf468de2038df4325fa1ac98337c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736787"
---
# <a name="frameinfo"></a>FRAMEINFO
Yığın çerçeveyi açıklar.

## <a name="syntax"></a>Sözdizimi

```cpp
typedef struct tagFRAMEINFO {
    FRAMEINFO_FLAGS    m_dwValidFields;
    BSTR               m_bstrFuncName;
    BSTR               m_bstrReturnType;
    BSTR               m_bstrArgs;
    BSTR               m_bstrLanguage;
    BSTR               m_bstrModule;
    UINT64             m_addrMin;
    UINT64             m_addrMax;
    IDebugStackFrame2* m_pFrame;
    IDebugModule2*     m_pModule;
    BOOL               m_fHasDebugInfo;
    BOOL               m_fStaleCode;
    BOOL               m_fAnnotatedFrame;
} FRAMEINFO;
```

```csharp
public struct FRAMEINFO {
    public uint              m_dwValidFields;
    public string            m_bstrFuncName;
    public string            m_bstrReturnType;
    public string            m_bstrArgs;
    public string            m_bstrLanguage;
    public string            m_bstrModule;
    public ulong             m_addrMin;
    public ulong             m_addrMax;
    public IDebugStackFrame2 m_pFrame;
    public IDebugModule2     m_pModule;
    public int               m_fHasDebugInfo;
    public int               m_fStaleCode;
    public int               m_fAnnotatedFrame;
} FRAMEINFO;
```

## <a name="members"></a>Üyeler
`m_dwValidFields`\
Hangi alanların [doldurulduğuna](../../../extensibility/debugger/reference/frameinfo-flags.md) FRAMEINFO_FLAGS numaralandırmadan gelen bayrakların birleşimi.

`m_bstrFuncName`\
Yığın çerçevesiile ilişkili işlev adı.

`m_bstrReturnType`\
Yığın çerçevesiile ilişkili iade türü.

`m_bstrArgs`\
Yığın çerçevesi ile ilişkili işlevin bağımsız değişkenleri.

`m_bstrLanguage`\
İşlevin uygulandığı dil.

`m_bstrModule`\
Yığın çerçevesiile ilişkili modül adı.

`m_addrMin`\
Minimum fiziksel yığın adresi.

`m_addrMAX`\
Maksimum fiziksel yığın adresi.

`m_pFrame`\
Bu yığın çerçevesini temsil eden [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) nesnesi.

`m_pModule`\
Bu yığın çerçevesini içeren modülü temsil eden [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) nesnesi.

`m_fHasDebugInfo`\
Verilen çerçevede`TRUE`hata ayıklama bilgisi varsa sıfır olmayan ( )

`m_fStaleCode`\
Yığın çerçevesi`TRUE`artık geçerli olmayan kodla ilişkiliyse sıfır dışı ( )

`m_fAnnotatedFrame`\
Yığın çerçevesi`TRUE`oturum hata ayıklama yöneticisi (SDM) tarafından açıklamalı ise sıfır olmayan ( )

## <a name="remarks"></a>Açıklamalar
Bu yapı doldurulmak üzere [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) yöntemine geçirilir. Bu yapı, Sırayla, [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) yöntemine bir çağrı döndürülür [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) arabiriminde bulunan bir listede yer almaktadır.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
