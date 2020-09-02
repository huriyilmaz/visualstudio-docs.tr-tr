---
title: IDebugProgramNode2::D etachDebugger_V7 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
ms.assetid: d2d4b78e-a2dd-4217-97a6-ab648fd2ee2f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 25c60bc42895a0527f1638dada5a28a1631314e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64806622"
---
# <a name="idebugprogramnode2detachdebugger_v7"></a>IDebugProgramNode2::DetachDebugger_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Kullanım dışı. KULLANMAYıN.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT DetachDebugger_V7 (   
   void   
);  
```  
  
```csharp  
int DetachDebugger_V7 ();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir uygulama her zaman döndürmelidir `E_NOTIMPL` .  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!WARNING]
> İtibariyle [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] , bu yöntem artık kullanılmamaktadır ve her zaman döndürmelidir `E_NOTIMPL` .  
  
 Bu yöntem, hata ayıklayıcı beklenmedik bir şekilde çıktığında çağrılır. Bu yöntem çağrıldığında, Kullanıcı onu ayırmış olsa da programı sürdürmelidir. Daha fazla hata ayıklama olayı gönderilmemelidir. Program, hata ayıklayıcının başka bir örneğinden iliştirilebileceği bir durumda olmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
