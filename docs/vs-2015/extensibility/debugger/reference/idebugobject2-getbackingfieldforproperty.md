---
title: 'IDebugObject2:: GetBackingFieldForProperty | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5eadbed61638ff1442c4ed7033426e245abf930a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62536392"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu nesne tarafından temsil edilen özelliği yedeklebilecek alanı veya değişkeni (varsa) alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetBackingFieldForProperty(  
   IDebugObject2** ppObject  
);  
```  
  
```csharp  
int GetBackingFieldForProperty(  
   out IDebugObject2 ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppObject`  
 dışı Destek alanını açıklayan bir [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) nesnesi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) nesnesi, bir yönetilen kod sınıfı özelliğini, diğer bir deyişle, Get ve/veya set erişimcisi olan bir yöntemi temsil eder. Bu tür özellikler genellikle özelliği tarafından yönetilen değeri içermesi için bir değişken gerektirir. Bu değişken, yedekleme alanı olarak bilinir. Nesne için bir yedekleme alanı yoksa, bir null değer döndürtığınızdan emin olun: bazı çağıranlar dönüş değerine dikkat ödemeyebilir ancak bunun yerine null değer döndürülüp döndürülmeyeceğini göz atalım `ppObject` .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
