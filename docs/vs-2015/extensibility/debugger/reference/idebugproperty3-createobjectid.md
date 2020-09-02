---
title: 'IDebugProperty3:: CreateObjectID | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0035faad9078acd70886d597f039c0d8de5ee12f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64788317"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diğer tüm özellikler arasında benzersiz olduğundan emin olmak için bu özellik için benzersiz bir KIMLIK oluşturur.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT CreateObjectID(  
   void  
);  
```  
  
```csharp  
int CreateObjectID();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, oturum hata ayıklama Yöneticisi, bu özelliğin diğer tüm özellikler arasında benzersiz şekilde tanımlanmasını sağlamak istediğinde çağrılır. Hata ayıklama altyapısı (DE), ile ilgilenen özellikler zaten benzersiz olarak tanımlanmamışsa, bu yöntemi destekler. DE bu yöntemi desteklemiyorsa, döndürür `E_NOTIMPL` .  
  
 `CreateObjectID` [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) yöntemi çağrıldığında ile oluşturulan HERHANGI bir benzersiz kimlik yok edilir; bu da bu özelliği benzersiz bir şekilde tanımlamak için gerekin sonuna işaret eder.  
  
> [!NOTE]
> Bu benzersiz KIMLIĞI almak için herhangi bir yöntem yoktur; bu nedenle, yöntemi çağrıldığında DE benzersiz kimlikler için istediği her şeyi yapabilir `CreateObjectID` .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)
