---
title: IDebugEngine2::D estroyProgram | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine2::DestroyProgram
helpviewer_keywords:
- IDebugEngine2::DestroyProgram
ms.assetid: 0c9e2698-c70f-4770-a7bb-39650e9c3a1f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9faacd80b036282a088b006a15eb9500e8606c5e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196023"
---
# <a name="idebugengine2destroyprogram"></a>IDebugEngine2::DestroyProgram
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Belirtilen programın genellikle sonlandırıldığı ve aynı programın tüm başvurularını temizlemesi ve program yok etme olayı göndermesini gerektiren bir hata ayıklama altyapısına (DE) bildirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT DestroyProgram(   
   IDebugProgram2* pProgram  
);  
```  
  
```cpp#  
int DestroyProgram(   
   IDebugProgram2 pProgram  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pProgram`  
 'ndaki Atipik olarak sonlandırılan programı temsil eden bir [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) nesnesi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem çağrıldıktan sonra, daha sonra oturum hata ayıklama Yöneticisi 'ne (SDM) geri bir [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) olayı gönderir.  
  
 Bu yöntem, `E_NOTIMPL` hata ayıklamakta olan programla aynı işlemde çalışıyorsa, uygulanmaz (döndürür). Bu yöntem yalnızca, SDM ile aynı işlemde çalıştırılıyorsa uygulanır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
