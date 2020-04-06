---
title: PROCESS_INFO_FIELDS | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714008"
---
# <a name="process_info_fields"></a>PROCESS_INFO_FIELDS
İşlem için ne tür bilgilerin alınıp alınabilmek için belirtilir.

## <a name="syntax"></a>Sözdizimi

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
 `bstrFileName` [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) yapının alanını başlatma/kullanma.

 `PIF_BASE_NAME`\
 `PROCESS_INFO` Yapının `bstrBaseName` alanını başlatma/kullanma.

 `PIF_TITLE`\
 `PROCESS_INFO` Yapının `bstrTitle` alanını başlatma/kullanma.

 `PIF_PROCESS_ID`\
 `PROCESS_INFO` Yapının `ProcessId` alanını başlatma/kullanma.

 `PIF_SESSION_ID`\
 `PROCESS_INFO` Yapının `dwSessionId` alanını başlatma/kullanma.

 `PIF_ATTACHED_SESSION_NAME`\
 `PROCESS_INFO` Yapının `bstrAttachedSessionName` alanını başlatma/kullanma.

 `PIF_CREATION_TIME`\
 `PROCESS_INFO` Yapının `CreationTime` alanını başlatma/kullanma.

 `PIF_FLAGS`\
 `PROCESS_INFO` Yapının `Flags` alanını başlatma/kullanma.

 `PIF_ALL`\
 Tüm alanları doldurur.

## <a name="remarks"></a>Açıklamalar
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) yapısının hangi alanlarının başharfe atılolacağını belirtmek için [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) yöntemine geçirildi.

 Ayrıca `PROCESS_INFO` hangi `Fields` alanların kullanıldığını ve geçerli olduğunu belirtmek için yapı alanında da kullanılır.

 Bu bayraklar biraz ile `OR`birleştirilebilir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
