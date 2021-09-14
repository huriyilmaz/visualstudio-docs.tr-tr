---
description: Bir iş parçacığının özelliklerini açıklar.
title: THREADPROPERTIES | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 42b5811169a7138cda0d292793bb1ccbaca7316c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634745"
---
# <a name="threadproperties"></a>THREADPROPERTIES
Bir iş parçacığının özelliklerini açıklar.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagTHREADPROPERTIES { 
   THREADPROPERTY_FIELDS dwFields;
   DWORD                 dwThreadId;
   DWORD                 dwSuspendCount;
   DWORD                 dwThreadState;
   BSTR                  bstrPriority;
   BSTR                  bstrName;
   BSTR                  bstrLocation;
} THREADPROPERTIES;
```

```csharp
public struct THREADPROPERTIES { 
   public uint   dwFields;
   public uint   dwThreadId;
   public uint   dwSuspendCount;
   public uint   dwThreadState;
   public string bstrPriority;
   public string bstrName;
   public string bstrLocation;
};
```

## <a name="members"></a>Üyeler
 `dwFields`\
 Bu yapıda hangi [alanların geçerli olduğunu](../../../extensibility/debugger/reference/threadproperty-fields.md) açıklayan THREADPROPERTY_FIELDS bayrağının bir birleşimi.

 `dwThreadId`\
 İş parçacığı kimliği.

 `dwSuspendCount`\
 İş parçacığı askıya alma sayısı.

 `dwThreadState`\
 [İş parçacığının durumunu](../../../extensibility/debugger/reference/threadstate.md) gösteren THREADSTATE numaralama değerinden bir değer.

 `bstrPriority`\
 İş parçacığı önceliğini belirten bir dize; örneğin, "NormalIn Üzerinde", "Normal" veya "Kritik Zaman".

 `bstName`\
 İş parçacığı adı.

 `bstrLocation`\
 İş parçacığı konumu (genellikle en üstteki yığın çerçevesi), genellikle yürütmenin durdurulduğu yöntemin adı olarak ifade edildi.

## <a name="remarks"></a>Açıklamalar
 Bu yapı, [GetThreadProperties yöntemine yapılan bir çağrıyla](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) doldurulur. Döndürülen bilgiler genellikle İş Parçacıkları penceresini doldurmak **için** kullanılır.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
- [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)
- [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)
