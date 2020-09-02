---
title: IDebugProperty3::D Estroyobjectıd | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty3::DestroyObjectID
helpviewer_keywords:
- IDebugProperty3::DestroyObjectID
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3a610cd5c947d77048e86b31c92298f6cc18607d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193426"
---
# <a name="idebugproperty3destroyobjectid"></a>IDebugProperty3::DestroyObjectID
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu özellik ile ilişkili benzersiz KIMLIĞI yok eder ve çağıranın artık bu özelliği diğer tüm özelliklerden benzersiz bir şekilde belirlemesine işaret eder.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT DestroyObjectID(  
   void  
);  
```  
  
```csharp  
int DestroyObjectID();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Hata ayıklama altyapısının bir özelliğin benzersiz kimliklerini desteklemesi gerekmiyorsa (bunları benzersiz bir şekilde takip ettiğinden), bu yöntem için yalnızca geri dönüş yapılabilir `E_NOTIMPL` .  
  
 Çağıran, bu özelliğin diğer tüm özellikler arasında benzersiz bir şekilde tanımlandığını doğrulamak istediğinde [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) yöntemine yapılan bir çağrıyla benzersiz kimlikler oluşturulur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)
