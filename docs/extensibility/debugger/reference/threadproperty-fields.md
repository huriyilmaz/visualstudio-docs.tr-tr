---
description: Bir iş parçacığıyla ilgili hangi bilgilerin alınacağını belirtir.
title: THREADPROPERTY_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 698c803304cf5efd3375b6d49e4dedbc4622f4c1
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221840"
---
# <a name="threadproperty_fields"></a>THREADPROPERTY_FIELDS
Bir iş parçacığıyla ilgili hangi bilgilerin alınacağını belirtir.

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
 `dwThreadId` [Threadproperties](../../../extensibility/debugger/reference/threadproperties.md) yapısının alanını başlatın/kullanın.

 `TPF_SUSPENDCOUNT`\
 `dwSuspendCount`S yapısının alanını başlatın/kullanın `THREADPROPERTIE` .

 `TPF_STATE`\
 `dwThreadState`S yapısının alanını başlatın/kullanın `THREADPROPERTIE` .

 `TPF_PRIORITY`\
 `bstrPriority`S yapısının alanını başlatın/kullanın `THREADPROPERTIE` .

 `TPF_NAME`\
 `bstrName`S yapısının alanını başlatın/kullanın `THREADPROPERTIE` .

 `TPF_LOCATION`\
 `bstrLocation`S yapısının alanını başlatın/kullanın `THREADPROPERTIE` .

 `TPF_ALLFIELDS`\
 Tüm alanları belirtir.

## <a name="remarks"></a>Açıklamalar
 Bu değerler, [threadproperties](../../../extensibility/debugger/reference/threadproperties.md) yapısının hangi alanlarının başlatıldığını göstermek Için [getthreadproperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) yöntemine bir bağımsız değişken olarak geçirilir.

 Bu değerler `dwFields` , `THREADPROPERTIES` hangi alanların kullanıldığını ve geçerli olduğunu göstermek için yapının üyesinde de kullanılır.

 Bu bayraklar bit düzeyinde birleştirilebilir `OR` .

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
