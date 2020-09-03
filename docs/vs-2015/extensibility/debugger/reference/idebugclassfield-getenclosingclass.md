---
title: 'IDebugClassField:: GetEnclosingClass | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 896d3ecd5202bf85e6b9e86af31796c662a6eef1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190998"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu sınıfı kapsayan sınıfı alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT GetEnclosingClass(   
   IDebugClassField** ppClassField  
);  
```  
  
```csharp  
int GetEnclosingClass(  
   out IDebugClassField ppClassField  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppClassField`  
 dışı Kapsayan sınıfı temsil eden bir [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) nesnesi döndürür. Kapsayan sınıf yoksa null değeri döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) nesnesi tarafından temsil edilen sınıf iç içe bir sınıf ise, `ppClassField` parametre `IDebugClassField` kapsayan sınıfı temsil eden bir nesne döndürür. Örneğin, bu sınıf tanımı verildiğinde:  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 `GetEnclosingClass` `IDebugClassField` Sınıfını temsil eden nesne üzerinde yöntemi çağırmak, `NestedClass` `IDebugClassField` sınıfını temsil eden bir nesne döndürür `RootClass` .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
