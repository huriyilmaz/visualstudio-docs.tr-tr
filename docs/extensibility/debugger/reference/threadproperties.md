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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 186d9b0cd4f9ee3a822a528ab16788902d9ff1af
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102225272"
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
 Bu yapıdaki hangi alanların geçerli olduğunu açıklayan [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) Numaralandırmadaki bayrakların birleşimi.

 `dwThreadId`\
 İş parçacığı KIMLIĞI.

 `dwSuspendCount`\
 İş parçacığı askıya alma sayısı.

 `dwThreadState`\
 İş parçacığının durumunu gösteren [ThreadState](../../../extensibility/debugger/reference/threadstate.md) sabit listesinden bir değer.

 `bstrPriority`\
 İş parçacığı önceliğini belirten bir dize; Örneğin, "normalin üzerinde", "normal" veya "zaman kritik".

 `bstName`\
 İş parçacığı adı.

 `bstrLocation`\
 Genellikle yürütmenin Şu anda sonlandırıldığı yöntemin adı olarak ifade edilen iş parçacığı konumu (genellikle en üstteki yığın çerçevesi).

## <a name="remarks"></a>Açıklamalar
 Bu yapı, [Getthreadproperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) yöntemine yapılan bir çağrı ile doldurulur. Döndürülen bilgiler genellikle **Iş parçacıkları** penceresini doldurmak için kullanılır.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
- [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)
- [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)
