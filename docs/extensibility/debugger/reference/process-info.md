---
title: PROCESS_INFO | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ef73145fb0a2598dc5e4ee98e8652314e0bc1c89
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713879"
---
# <a name="process_info"></a>PROCESS_INFO
Bir işlem hakkında bilgi içerir.

## <a name="syntax"></a>Sözdizimi

```cpp
typedef struct tagPROCESS_INFO { 
   PROCESS_INFO_FIELDS Fields;
   BSTR                bstrFileName;
   BSTR                bstrBaseName;
   BSTR                bstrTitle;
   AD_PROCESS_ID       ProcessId;
   DWORD               dwSessionId;
   BSTR                bstrAttachedSessionName;
   FILETIME            CreationTime;
   PROCESS_INFO_FLAGS  Flags;
} PROCESS_INFO;
```

```csharp
public struct PROCESS_INFO { 
   public uint          Fields;
   public string        bstrFileName;
   public string        bstrBaseName;
   public string        bstrTitle;
   public AD_PROCESS_ID ProcessId;
   public uint          dwSessionId;
   public string        bstrAttachedSessionName;
   public FILETIME      CreationTime;
   public uint          Flags;
};
```

## <a name="members"></a>Üyeler
 `Fields`\
 Hangi alanların doldurulduğuna işaret eden [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) numaralandırmadaki bayrakların birleşimi.

 `bstrFileName`\
 İşlemin tam yol adı. [Parametre](../../../extensibility/debugger/reference/idebugprocess2-getname.md) `GN_FILENAME`ile GetName yöntemini çağırmaya eşdeğerdir.

 `bstrBaseName`\
 Dosya adı ve işlemin uzantısı. Parametre `GN_BASENAME`ile `IDebugProcess2::Getname` yöntemi çağırmaya eşdeğerdir.

 `bstrTitle`\
 Varsa, sürecin başlığı. Parametre `GN_TITLE`ile `IDebugProcess2::Getname` yöntemi çağırmaya eşdeğerdir.

 `ProcessId`\
 İşlemi tanımlayan [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) yapı. [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md) yöntemini aramaya eşdeğerdir.

 `dwSessionId`\
 Bu işlemin yürüttün hata ayıklama oturumunun tanımlayıcısı.

 `bstrAttachedSessionName`\
 Ekteki oturum adı. [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md) yöntemini aramaya eşdeğerdir.

 `CreationTime`\
 İşlemin oluşturulduğu saat.

 `Flags`\
 İşlemin özelliklerini belirten [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) numaralandırmadan gelen bayrakların birleşimi.

## <a name="remarks"></a>Açıklamalar
 Bu yapı doldurulduğu [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) yöntemine aktarılır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)
- [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
- [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)
- [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)
