---
title: PROCESS_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FIELDS
helpviewer_keywords:
- PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f81709e7146bbdef13daa3564bb784fd9c08d58e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80714008"
---
# <a name="process_info_fields"></a>PROCESS_INFO_FIELDS
Bir işlem için hangi tür bilgilerin alınması belirtildi.

## <a name="syntax"></a>Syntax

```cpp
enum enum_PROCESS_INFO_FIELDS { 
   PIF_FILE_NAME             = 0x00000001,
   PIF_BASE_NAME             = 0x00000002,
   PIF_TITLE                 = 0x00000004,
   PIF_PROCESS_ID            = 0x00000008,
   PIF_SESSION_ID            = 0x00000010,
   PIF_ATTACHED_SESSION_NAME = 0x00000020,
   PIF_CREATION_TIME         = 0x00000040,
   PIF_FLAGS                 = 0x00000080,
   PIF_ALL                   = 0x000000ff
};
typedef DWORD PROCESS_INFO_FIELDS;
```

```csharp
public enum enum_PROCESS_INFO_FIELDS { 
   PIF_FILE_NAME             = 0x00000001,
   PIF_BASE_NAME             = 0x00000002,
   PIF_TITLE                 = 0x00000004,
   PIF_PROCESS_ID            = 0x00000008,
   PIF_SESSION_ID            = 0x00000010,
   PIF_ATTACHED_SESSION_NAME = 0x00000020,
   PIF_CREATION_TIME         = 0x00000040,
   PIF_FLAGS                 = 0x00000080,
   PIF_ALL                   = 0x000000ff
};
```

## <a name="fields"></a>Alanlar
 `PIF_FILE_NAME`\
 `bstrFileName` [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) yapısının alanını başlatın/kullanın.

 `PIF_BASE_NAME`\
 Yapının alanını başlatın/kullanın `bstrBaseName` `PROCESS_INFO` .

 `PIF_TITLE`\
 Yapının alanını başlatın/kullanın `bstrTitle` `PROCESS_INFO` .

 `PIF_PROCESS_ID`\
 Yapının alanını başlatın/kullanın `ProcessId` `PROCESS_INFO` .

 `PIF_SESSION_ID`\
 Yapının alanını başlatın/kullanın `dwSessionId` `PROCESS_INFO` .

 `PIF_ATTACHED_SESSION_NAME`\
 Yapının alanını başlatın/kullanın `bstrAttachedSessionName` `PROCESS_INFO` .

 `PIF_CREATION_TIME`\
 Yapının alanını başlatın/kullanın `CreationTime` `PROCESS_INFO` .

 `PIF_FLAGS`\
 Yapının alanını başlatın/kullanın `Flags` `PROCESS_INFO` .

 `PIF_ALL`\
 Tüm alanları doldurur.

## <a name="remarks"></a>Açıklamalar
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) yapısının hangi alanlarının başlatıldığını göstermek Için [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) yöntemine geçirilir.

 Ayrıca `Fields` , `PROCESS_INFO` hangi alanların kullanıldığını ve geçerli olduğunu göstermek için yapının alanında kullanılır.

 Bu bayraklar bit düzeyinde birleştirilebilir `OR` .

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırmalar](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
