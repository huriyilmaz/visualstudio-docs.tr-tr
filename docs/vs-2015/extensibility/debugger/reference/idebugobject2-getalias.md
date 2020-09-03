---
title: 'IDebugObject2:: GetAlias | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject2::GetAlias
helpviewer_keywords:
- IDebugObject2::GetAlias method
ms.assetid: aa6824d5-c932-42ba-8713-950e7d1fb42f
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b05d416da41265f6727df843b1b686fcfe5107f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194606"
---
# <a name="idebugobject2getalias"></a>IDebugObject2::GetAlias
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Varsa, bu nesneyle ilişkili diğer adı alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetAlias(  
   IDebugAlias** ppAlias  
);  
```  
  
```csharp  
int GetAlias(  
   out IDebugAlias ppAlias  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppAlias`  
 dışı Bu nesne için diğer adı temsil eden bir [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) nesnesi döndürür; Aksi takdirde, null bir değer döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir nesne için bir diğer ad [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) yöntemi çağrısıyla oluşturulur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
