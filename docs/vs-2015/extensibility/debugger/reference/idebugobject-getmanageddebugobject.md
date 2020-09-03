---
title: 'IDebugObject:: GetManagedDebugObject | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject::GetManagedDebugObject
helpviewer_keywords:
- IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4f2917135f5e25648cf08cd9030e3fdf31aedb52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162468"
---
# <a name="idebugobjectgetmanageddebugobject"></a>IDebugObject::GetManagedDebugObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Hata ayıklama altyapısının adres alanında yönetilen nesnenin bir kopyasını oluşturur.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT GetManagedDebugObject(   
   IDebugManagedObject** ppObject  
);  
```  
  
```csharp  
int GetManagedDebugObject(  
   out IDebugManagedObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppObject`  
 dışı Yeni oluşturulan yönetilen nesneyi temsil eden bir [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) nesnesi döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür. Bu [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) bir yönetilen değer sınıfı örneğini temsil etmediği E_FAIL döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nesnesi, örnek gibi bir yönetilen değer sınıfı örneğini temsil etmelidir `System.Decimal` . Yerel bir kopyaya sahip olarak, [değerlendir](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) çağırma yükü ortadan kalkar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
