---
description: Bir işlem hakkında bilgi içerir.
title: PROCESS_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e2fc29833c8d3f6b64e5bbc683ad6f5fc82231ef
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726968"
---
# <a name="process_info"></a>PROCESS_INFO
Bir işlem hakkında bilgi içerir.

## <a name="syntax"></a>Syntax

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
 Hangi alanların doldurulması [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) bir bayrak birleşimi.

 `bstrFileName`\
 Sürecin tam yol adı. parametresiyle [GetName yöntemini](../../../extensibility/debugger/reference/idebugprocess2-getname.md) çağırmaya `GN_FILENAME` eşdeğerdir.

 `bstrBaseName`\
 Sürecin dosya adı ve uzantısı. parametresiyle yöntemini `IDebugProcess2::Getname` çağırmaya `GN_BASENAME` eşdeğerdir.

 `bstrTitle`\
 Varsa, sürecin başlığı. parametresiyle yöntemini `IDebugProcess2::Getname` çağırmaya `GN_TITLE` eşdeğerdir.

 `ProcessId`\
 İşlem [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) tanımlayan bir yapıdır. [GetPhysicalProcessId yöntemini çağırmaya](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md) eşdeğerdir.

 `dwSessionId`\
 Bu işlemde çalışan hata ayıklama oturumunun tanımlayıcısı.

 `bstrAttachedSessionName`\
 Eklenen oturum adı. [GetAttachedSessionName yöntemini çağırmaya eşdeğerdir.](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)

 `CreationTime`\
 sürecin oluşturulma zamanı.

 `Flags`\
 İşlem özelliklerini belirten [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) bir bayrak birleşimi.

## <a name="remarks"></a>Açıklamalar
 Bu yapı, [doldurulan GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) yöntemine geçirildi.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)
- [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
- [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)
- [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)
