---
title: 'IDebugProgramNodeAttach2:: OnAttach | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 845ec66215c5d999aaf3b5c9658bc0fb8e7295a7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148540"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

İlişkili programa ekler veya Attach işlemini [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) yöntemine erteler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT OnAttach(  
   [in] REFGUID guidProgramId  
);  
```  
  
```csharp  
int OnAttach(  
   ref Guid guidProgramId  
};  
```  
  
#### <a name="parameters"></a>Parametreler  
 `guidProgramId`  
 [in] `GUID` ilişkili programa atamak için.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` . `S_FALSE` [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) yönteminin çağrılmaması gerekiyorsa döndürür. Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, [Attach yöntemi çağrılmadan önce iliştirme işlemi](../../../extensibility/debugger/reference/idebugengine2-attach.md) sırasında çağrılır. `OnAttach`Yöntemi, Attach işlemini kendisi gerçekleştirebilir (Bu durumda, bu yöntem ' i döndürür `S_FALSE` ) veya iliştirme işlemini yönteme erteleyin `IDebugEngine2::Attach` ( `OnAttach` Yöntem döndürür `S_OK` ). Her iki olayda da `OnAttach` yöntemi, `GUID` hata ayıklanan programın belirtilen ' a göre ayarlayabilir `GUID` .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [İliştir](../../../extensibility/debugger/reference/idebugengine2-attach.md)
