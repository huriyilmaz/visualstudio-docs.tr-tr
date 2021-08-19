---
description: Bir iş parçacığı hakkında hangi bilgilerin alın olacağını belirtir.
title: THREADPROPERTY_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c70e331de05b3288e1105832616acb1d3359b049
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122137840"
---
# <a name="threadproperty_fields"></a>THREADPROPERTY_FIELDS
Bir iş parçacığı hakkında hangi bilgilerin alın olacağını belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_THREADPROPERTY_FIELDS { 
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
public enum enum_THREADPROPERTY_FIELDS { 
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
 `dwThreadId` [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) yapısının alanını başlatma/kullanma.

 `TPF_SUSPENDCOUNT`\
 S yapısının `dwSuspendCount` alanını `THREADPROPERTIE` başlatma/kullanma.

 `TPF_STATE`\
 S yapısının `dwThreadState` alanını `THREADPROPERTIE` başlatma/kullanma.

 `TPF_PRIORITY`\
 S yapısının `bstrPriority` alanını `THREADPROPERTIE` başlatma/kullanma.

 `TPF_NAME`\
 S yapısının `bstrName` alanını `THREADPROPERTIE` başlatma/kullanma.

 `TPF_LOCATION`\
 S yapısının `bstrLocation` alanını `THREADPROPERTIE` başlatma/kullanma.

 `TPF_ALLFIELDS`\
 Tüm alanları belirtir.

## <a name="remarks"></a>Açıklamalar
 Bu değerler, [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) yapısının hangi alanlarının başlat olacağını belirtmek için [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) yöntemine bağımsız değişken olarak geçirildi.

 Bu değerler, hangi alanların `dwFields` ve geçerli olduğunu belirtmek için `THREADPROPERTIES` yapının üyesinde de kullanılır.

 Bu bayraklar bit olarak birleştirilmiş `OR` olabilir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
