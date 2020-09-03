---
title: 'IDebugFunctionObject2:: CreateObject | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::CreateObject
- CreateObject
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b60801f5288e88795ab75145b9c6120d4308d1c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202991"
---
# <a name="idebugfunctionobject2createobject"></a>IDebugFunctionObject2::CreateObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Değerlendirme bayrağı ayarları ve zaman aşımı değeri verilen bir Oluşturucu kullanan bir nesne oluşturur.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT CreateObject (  
   IDebugFunctionObject* pConstructor,  
   DWORD                 dwArgs,  
   IDebugObject*         pArgs[],  
   DWORD                 dwEvalFlags,  
   DWORD                 dwTimeout,  
   IDebugObject**        ppObject  
);  
```  
  
```csharp  
int CreateObject (  
   IDebugFunctionObject pConstructor,  
   uint                 dwArgs,  
   IDebugObject[]       pArgs,  
   uint                 dwEvalFlags,  
   uint                 dwTimeout,  
   out IDebugObject**   ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pConstructor`  
 'ndaki Oluşturulacak nesnenin oluşturucusunu temsil eden bir [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) nesnesi.  
  
 `dwArgs`  
 'ndaki Dizideki parametrelerin sayısı `pArg` . Oluşturucuya geçirilen parametre sayısını temsil eder.  
  
 `pArgs`  
 'ndaki Oluşturucuya geçirilen parametreleri temsil eden bir [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nesneleri dizisi.  
  
 `dwEvalFlags`  
 'ndaki [Evalflags](../../../extensibility/debugger/reference/evalflags.md) numaralandırmasındaki, değerlendirmenin nasıl gerçekleştirileceğini belirten bayrakların birleşimi.  
  
 `dwTimeout`  
 'ndaki Bu yöntemden dönmeden önce beklenecek en uzun süre (milisaniye cinsinden). Sonsuza kadar beklemek için **sonsuz** kullanın.  
  
 `ppObject`  
 dışı Yeni oluşturulan nesneyi temsil eden bir **IDebugObject** döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir sınıf örneğini temsil eden bir nesne veya bir parametre olan bir Oluşturucu gerektiren başka bir karmaşık tür oluşturmak için bu yöntemi çağırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
