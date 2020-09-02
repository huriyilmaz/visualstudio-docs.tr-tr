---
title: THREADPROPERTIES | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4815a1e42b98fba812e8a3c2a53516bff16081db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204817"
---
# <a name="threadproperties"></a>THREADPROPERTIES
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bir iş parçacığının özelliklerini açıklar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 dwFields  
 Bu yapıdaki hangi alanların geçerli olduğunu açıklayan [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) Numaralandırmadaki bayrakların birleşimi.  
  
 dwThreadId  
 İş parçacığı KIMLIĞI.  
  
 dwSuspendCount  
 İş parçacığı askıya alma sayısı.  
  
 dwThreadState  
 İş parçacığının durumunu gösteren [ThreadState](../../../extensibility/debugger/reference/threadstate.md) sabit listesinden bir değer.  
  
 bstrPriority  
 İş parçacığı önceliğini belirten bir dize; Örneğin, "normalin üzerinde", "normal" veya "zaman kritik".  
  
 bstName  
 İş parçacığı adı.  
  
 bstrLocation  
 Genellikle yürütmenin Şu anda sonlandırıldığı yöntemin adı olarak ifade edilen iş parçacığı konumu (genellikle en üstteki yığın çerçevesi).  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yapı, [Getthreadproperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) yöntemine yapılan bir çağrı ile doldurulur. Döndürülen bilgiler genellikle **Iş parçacıkları** penceresini doldurmak için kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yapılar ve birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)   
 [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)   
 [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)
