---
title: 'IDebugProgram2:: Step | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dd9d314865eb2051b67d7c127a6c5cc2395b1863
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86387232"
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bir adım gerçekleştirir.  
  
> [!NOTE]
> Bu yöntem kullanım dışıdır. Bunun yerine [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md) metodunu kullanın.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT Step(   
   IDebugThread2*  pThread,  
   STEPKIND        sk,  
   STEPUNIT        step  
);  
```  
  
```csharp  
int Step(   
   IDebugThread2  pThread,  
   enum_STEPKIND  sk,  
   enum_STEPUNIT  step  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pThread`  
 'ndaki Bulanan iş parçacığını temsil eden bir [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) nesnesi.  
  
 `sk`  
 'ndaki Adım türünü belirten [stepkind](../../../extensibility/debugger/reference/stepkind.md) numaralandırmasındaki bir değer.  
  
 `step`  
 'ndaki Adım birimini belirten [stepunit](../../../extensibility/debugger/reference/stepunit.md) numaralandırmasındaki bir değer (örneğin, ifadeye veya yönergeye göre).  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 İş parçacıkları arasında herhangi bir iş parçacığı eşitlemesi veya iletişim varsa, belirli bir iş parçacığı adımlarken programdaki diğer iş parçacıklarının çalışması gerekir.  
  
> [!WARNING]
> Bu çağrıyı gerçekleştirirken [olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) için bir durdurma olayı veya anında (zaman uyumlu) olay göndermeyin; Aksi takdirde hata ayıklayıcı yanıt vermeyi durdurabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
