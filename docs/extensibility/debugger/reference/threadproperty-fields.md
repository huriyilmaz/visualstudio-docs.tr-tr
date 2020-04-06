---
title: THREADPROPERTY_FIELDS | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b31c43187d1136f7a194c42749c430de6cd064a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713405"
---
# <a name="threadproperty_fields"></a>THREADPROPERTY_FIELDS
Bir iş parçacığı hakkında hangi bilgilerin alınıp alıneceğini belirtir.

## <a name="syntax"></a>Sözdizimi

```cpp
enum enum_THREADPROPERTY_FIELDS { 
   TPF_ID           = 0x0001,
   TPF_SUSPENDCOUNT = 0x0002,
   TPF_STATE        = 0x0004,
   TPF_PRIORITY     = 0x0008,
   TPF_NAME         = 0x0010,
   TPF_LOCATION     = 0x0020,
   TPF_ALLFIELDS    = 0xffffffff
};
typedef DWORD THREADPROPERTY_FIELDS;
```

```csharp
public enum enum_THREADPROPERTY_FIELDS { 
   TPF_ID           = 0x0001,
   TPF_SUSPENDCOUNT = 0x0002,
   TPF_STATE        = 0x0004,
   TPF_PRIORITY     = 0x0008,
   TPF_NAME         = 0x0010,
   TPF_LOCATION     = 0x0020,
   TPF_ALLFIELDS    = 0xffffffff
};
```

## <a name="fields"></a>Alanlar
 `TPF_ID`\
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) yapısının `dwThreadId` alanını başlatma/kullanma.

 `TPF_SUSPENDCOUNT`\
 `THREADPROPERTIE`S yapısının `dwSuspendCount` alanını başlatma/kullanma.

 `TPF_STATE`\
 `THREADPROPERTIE`S yapısının `dwThreadState` alanını başlatma/kullanma.

 `TPF_PRIORITY`\
 `THREADPROPERTIE`S yapısının `bstrPriority` alanını başlatma/kullanma.

 `TPF_NAME`\
 `THREADPROPERTIE`S yapısının `bstrName` alanını başlatma/kullanma.

 `TPF_LOCATION`\
 `THREADPROPERTIE`S yapısının `bstrLocation` alanını başlatma/kullanma.

 `TPF_ALLFIELDS`\
 Tüm alanları belirtir.

## <a name="remarks"></a>Açıklamalar
 Bu değerler, [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) yapısının hangi alanlarının başharfe başlatılanolacağını belirtmek için [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) yöntemine bir bağımsız değişken olarak geçirilir.

 Bu değerler, yapının `dwFields` `THREADPROPERTIES` üyesi nde hangi alanların kullanıldığını ve geçerli olduğunu belirtmek için de kullanılır.

 Bu bayraklar biraz ile `OR`birleştirilebilir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
