---
description: Bir işlem için ne tür bilgilerin alınamadı.
title: PROCESS_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FIELDS
helpviewer_keywords:
- PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cdcf987151af31e9f8921bfca3f758b20b818e32
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122029183"
---
# <a name="process_info_fields"></a>PROCESS_INFO_FIELDS
Bir işlem için ne tür bilgilerin alınamadı.

## <a name="syntax"></a>Syntax

```cpp
enum enum_PROCESS_INFO_FIELDS { 
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
public enum enum_PROCESS_INFO_FIELDS { 
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
 İlke `bstrFileName` yapısının alanını [PROCESS_INFO.](../../../extensibility/debugger/reference/process-info.md)

 `PIF_BASE_NAME`\
 Yapı alanını `bstrBaseName` `PROCESS_INFO` başlatma/kullanma.

 `PIF_TITLE`\
 Yapı alanını `bstrTitle` `PROCESS_INFO` başlatma/kullanma.

 `PIF_PROCESS_ID`\
 Yapı alanını `ProcessId` `PROCESS_INFO` başlatma/kullanma.

 `PIF_SESSION_ID`\
 Yapı alanını `dwSessionId` `PROCESS_INFO` başlatma/kullanma.

 `PIF_ATTACHED_SESSION_NAME`\
 Yapı alanını `bstrAttachedSessionName` `PROCESS_INFO` başlatma/kullanma.

 `PIF_CREATION_TIME`\
 Yapı alanını `CreationTime` `PROCESS_INFO` başlatma/kullanma.

 `PIF_FLAGS`\
 Yapı alanını `Flags` `PROCESS_INFO` başlatma/kullanma.

 `PIF_ALL`\
 Tüm alanları doldurur.

## <a name="remarks"></a>Açıklamalar
 İlke [yapısının](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) hangi alanlarının başlatılmayacaklarını [belirtmek PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) GetInfo yöntemine geçirildi.

 Ayrıca, `Fields` kullanılan ve geçerli `PROCESS_INFO` olan alanları belirtmek için yapı alanında kullanılır.

 Bu bayraklar bit olarak birleştirilmiş `OR` olabilir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
