---
title: 'IDebugProgram3:: ExecuteOnThread | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cfc64f8ae928b4bb0057a16b8a74c6ddbff588c0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148628"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Hata ayıklayıcı programını yürütür. İş parçacığı, Kullanıcı tarafından program yürütürken hangi iş parçacığının görüntülemekte olduğunu hata ayıklayıcı bilgilerini vermek üzere döndürülür.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT ExecuteOnThread(  
   [in] IDebugThread2* pThread)  
```  
  
```csharp  
int ExecuteOnThread(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pThread`  
 'ndaki Bir [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) nesnesi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Hata ayıklayıcının çalışmayı durdurduktan sonra sürdürüleceği üç farklı yol vardır:  
  
- Yürüt: önceki adımları Iptal edin ve sonraki kesme noktasına kadar çalıştırın.  
  
- Adım: herhangi bir eski adımı Iptal edin ve yeni adım tamamlanana kadar çalıştırın.  
  
- Devam: tekrar çalıştırın ve eski bir adımı etkin bırakın.  
  
  Öğesine geçirilen iş parçacığı, `ExecuteOnThread` hangi adımın iptal edildiğini saptarken yararlı olur. İş parçacığını bilinmediğinizde yürütme çalıştırıldığında tüm adımlar iptal edilir. İş parçacığı hakkında bilgi sahibi olarak yalnızca etkin iş parçacığında adımı iptal etmeniz gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yürütme](../../../extensibility/debugger/reference/idebugprogram2-execute.md)   
 [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)
