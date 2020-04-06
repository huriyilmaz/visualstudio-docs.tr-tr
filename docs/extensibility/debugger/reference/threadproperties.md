---
title: KONU ÖZELLIKLERI | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bd0ed4e33b1f8e0e905f3c88493c9f513c177fbc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713431"
---
# <a name="threadproperties"></a>THREADPROPERTIES
İş parçacığının özelliklerini açıklar.

## <a name="syntax"></a>Sözdizimi

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
 Bu yapıdaki hangi alanların geçerli olduğunu açıklayan [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) numaralandırmadan gelen bayrakların birleşimi.

 `dwThreadId`\
 İş parçacığı kimliği.

 `dwSuspendCount`\
 İş parçacığı askıya alma sayısı.

 `dwThreadState`\
 [ThreadSTATE](../../../extensibility/debugger/reference/threadstate.md) numaralandırmasından, çalışma iş parçacığının durumunu gösteren bir değer.

 `bstrPriority`\
 İş parçacığı önceliğini belirten bir dize; örneğin, "Normalin Üzerinde", "Normal", "Zaman Kritik".

 `bstName`\
 İş parçacığı adı.

 `bstrLocation`\
 İş parçacığı konumu (genellikle en üstteki yığın çerçevesi), genellikle yürütmenin şu anda durdurulduğu yöntemin adı olarak ifade edilir.

## <a name="remarks"></a>Açıklamalar
 Bu yapı [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) yöntemine yapılan bir çağrı yla doldurulur. Döndürülen bilgiler genellikle **İş Parçacıkları** penceresinde kullanılır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
- [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)
- [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)
