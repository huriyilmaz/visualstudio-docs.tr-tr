---
title: 'IEnumDebugThreads2:: Next | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2::Next
helpviewer_keywords:
- IEnumDebugThreads2::Next
ms.assetid: bcffd954-3c67-4867-96f3-041ddb3e34d4
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8553ae1c75bd8b5716182485f0b0dc8d77da14f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147727"
---
# <a name="ienumdebugthreads2next"></a>IEnumDebugThreads2::Next
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Numaralandırmadaki öğelerin bir sonraki kümesini döndürür.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT Next(  
   ULONG           celt,  
   IDebugThread2** rgelt,  
   ULONG*          pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint            celt,  
   IDebugThread2[] rgelt,  
   ref uint        pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `celt`  
 'ndaki Alınacak öğe sayısı. Ayrıca, dizinin en büyük boyutunu belirtir `rgelt` .  
  
 `rgelt`  
 [in, out] Doldurulacak [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) öğelerinin dizisi.  
  
 `pceltFetched`  
 dışı İçinde gerçekten döndürülen öğelerin sayısını döndürür `rgelt` .  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` . `S_FALSE`İstenen sayıda öğeden daha az döndürülüp döndürülmeyeceğini döndürür; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
