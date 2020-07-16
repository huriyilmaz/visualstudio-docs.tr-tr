---
title: 'IDebugProcess3:: Execute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess3::Execute
helpviewer_keywords:
- IDebugProcess3::Execute
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f9b70deabd4cb7996d76373c6216057678c0bd3
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86386179"
---
# <a name="idebugprocess3execute"></a>IDebugProcess3::Execute
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu işlemi durdurulmuş bir durumdan çalıştırmaya devam eder. Önceki yürütme durumu (bir adım gibi) temizlenir ve işlem yeniden yürütülmeye başlar.  
  
> [!NOTE]
> Bu yöntem, [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)yerine kullanılmalıdır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT Execute(  
   IDebugThread2* pThread  
);  
```  
  
```csharp  
int Execute(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pThread`  
 'ndaki Yürütülecek iş parçacığını temsil eden bir [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) nesnesi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanıcı başka bir işlemin iş parçacığında durdurulmuş bir durumdan yürütülmeye başladığında, bu yöntem bu işlem üzerinde çağrılır. Bu yöntem, Kullanıcı IDE 'deki **hata ayıklama** menüsünden **Başlat** komutunu seçtiğinde de çağrılır. Bu yöntemin uygulanması, işlemdeki geçerli iş parçacığında [sürdürülmesi](../../../extensibility/debugger/reference/idebugthread2-resume.md) yöntemini çağırmak kadar basit olabilir.  
  
> [!WARNING]
> Bu çağrıyı gerçekleştirirken [olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) için bir durdurma olayı veya anında (zaman uyumlu) olay göndermeyin; Aksi takdirde hata ayıklayıcı yanıt vermeyi durdurabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Bilmeniz](../../../extensibility/debugger/reference/idebugthread2-resume.md)   
 [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
