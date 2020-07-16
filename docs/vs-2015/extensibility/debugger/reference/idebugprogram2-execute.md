---
title: 'IDebugProgram2:: Execute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 676a3a7d184c1f34cafcfc2b2a4dd7a1c3f81a95
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86387336"
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu programı durdurulmuş bir durumdan çalıştırmaya devam eder. Önceki yürütme durumu (bir adım gibi) temizlenir ve program yeniden yürütülmeye başlar.  
  
> [!NOTE]
> Bu yöntem kullanım dışıdır. Bunun yerine [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md) metodunu kullanın.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Execute(  
   void  
);  
```  
  
```csharp  
int Execute();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanıcı başka bir programın iş parçacığında durdurulmuş bir durumdan yürütmeyi başlattığında, bu yöntem bu programda çağırılır. Bu yöntem, Kullanıcı IDE 'deki **hata ayıklama** menüsünden **Başlat** komutunu seçtiğinde de çağrılır. Bu yöntemin uygulanması, programdaki geçerli iş parçacığında [sürdürülür](../../../extensibility/debugger/reference/idebugthread2-resume.md) yöntemini çağırmak kadar basit olabilir.  
  
> [!WARNING]
> Bu çağrıyı gerçekleştirirken [olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) için bir durdurma olayı veya anında (zaman uyumlu) olay göndermeyin; Aksi takdirde hata ayıklayıcı yanıt vermeyi durdurabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Sürdür](../../../extensibility/debugger/reference/idebugthread2-resume.md)
