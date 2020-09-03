---
title: 'IDebugTypeFieldBuilder2:: CreateArrayOfType | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder2::CreateArrayOfType
- CreateArrayOfType
ms.assetid: 85166ac9-0bff-49a0-b2fd-ca7f7a8eae4b
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b02b7c6ef29e1b6c00b5d5a0b7fbfa93c03f132b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152886"
---
# <a name="idebugtypefieldbuilder2createarrayoftype"></a>IDebugTypeFieldBuilder2::CreateArrayOfType
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Belirtilen türde ve boyutta bir dizi oluşturur.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT CreateArrayOfType (  
   IDebugField*  pTypeField,  
   DWORD         rank,  
   IDebugField** pArrayOfTypeField  
);  
```  
  
```csharp  
int CreateArrayOfType (  
   IDebugField     pTypeField,  
   uint            rank,  
   out IDebugField pArrayOfTypeField  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pTypeField`  
 'ndaki Dizinin tutacağız öğelerin türü.  
  
 `rank`  
 'ndaki Dizideki öğe sayısı.  
  
 `pArrayOfTypeField`  
 dışı Yeni diziyi temsil eden [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) nesnelerini döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)
