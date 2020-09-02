---
title: 'IDebugPortNotify2:: RemoveProgramNode | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortNotify2::RemoveProgramNode
helpviewer_keywords:
- IDebugPortNotify2::RemoveProgramNode
ms.assetid: 3668157b-66d2-416e-a359-fc04dcd18a48
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cc4ac539fdf0a5b27f8e9eb94e7644fa44070b3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188410"
---
# <a name="idebugportnotify2removeprogramnode"></a>IDebugPortNotify2::RemoveProgramNode
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Üzerinde çalıştığı bağlantı noktasından hata ayıklaabilecek bir programın kaydını siler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT RemoveProgramNode(   
   IDebugProgramNode2* pProgramNode  
);  
```  
  
```csharp  
int RemoveProgramNode(   
   IDebugProgramNode2 pProgramNode  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pProgramNode`  
 'ndaki Kaydı kaldırılacak programı temsil eden bir [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) Objecy.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) yöntemine yapılan bir çağrıyla eklenen bir program düğümünü kaldırır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
