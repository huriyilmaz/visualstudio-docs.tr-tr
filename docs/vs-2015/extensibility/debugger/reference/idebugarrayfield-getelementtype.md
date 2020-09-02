---
title: 'Ihata ayıklama Garrayfield:: GetElementType | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetElementType
helpviewer_keywords:
- IDebugArrayField::GetElementType method
ms.assetid: c46bf625-0a48-4cbb-8f1f-286356f2c065
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 00ae24c2449d9bd26895647fc8f7b026291c4288
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68142972"
---
# <a name="idebugarrayfieldgetelementtype"></a>IDebugArrayField::GetElementType
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Dizideki öğe türünü alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT GetElementType(   
   IDebugField** ppType  
);  
```  
  
```csharp  
int GetElementType(  
   out IDebugField ppType  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppType`  
 dışı Öğe türünü açıklayan bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) nesnesi döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 [Ihata ayıklama Garrayfield](../../../extensibility/debugger/reference/idebugarrayfield.md) nesnesi, dizideki tüm öğelerin aynı türde olduğunu varsayar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ihata ayıklama Garrayfield](../../../extensibility/debugger/reference/idebugarrayfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
