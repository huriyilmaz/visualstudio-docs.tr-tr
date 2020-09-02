---
title: 'IDebugManagedObject:: GetManagedObject | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugManagedObject::GetManagedObject
helpviewer_keywords:
- IDebugManagedObject::GetManagedObject method
ms.assetid: 6abe1402-6aad-41e6-8ec1-ae12d5945992
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 74390d4c5f27400b0549408b1c36e9e385b3e60b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180611"
---
# <a name="idebugmanagedobjectgetmanagedobject"></a>IDebugManagedObject::GetManagedObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Yönetilen nesneyi temsil eden bir arabirim döndürür.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT GetManagedObject(   
   IUnknown** ppManagedObject  
);  
```  
  
```cpp#  
int GetManagedObject(  
   out object ppManagedObject  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppManagedObject`  
 dışı Yönetilen nesneyi temsil eden bir arabirim döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntemden döndürülen arabirim, yönetilen sınıf tarafından uygulanan herhangi bir arabirim için sorgulanarak yöntemlerinin çağrılmasına izin verir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
