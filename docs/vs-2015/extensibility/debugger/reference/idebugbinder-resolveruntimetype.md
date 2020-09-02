---
title: 'Idebugciltçi:: ResolveRuntimeType | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBinder::ResolveRuntimeType
helpviewer_keywords:
- IDebugBinder::ResolveRuntimeType method
ms.assetid: 6456ab3e-1c03-4f3c-91f9-16797ab7f5e7
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 69b1418c76e01b87bcd6d992a82ce58287e79ceb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192301"
---
# <a name="idebugbinderresolveruntimetype"></a>IDebugBinder::ResolveRuntimeType
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu yöntem, bir nesnenin çalışma zamanı türünü belirler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT ResolveRuntimeType(   
   IDebugObject* pObject,  
   IDebugField** ppResolved  
);  
```  
  
```csharp  
int ResolveRuntimeType(  
   IDebugObject     pObject,   
   out IDebugField  ppResolved  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pObject`  
 'ndaki Çözümlenecek [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) .  
  
 `ppResolved`  
 dışı Nesnenin türünü bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)olarak döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir nesnenin çalışma zamanı türü, derleme zamanında her zaman bilinmez. Örneğin, çok biçimlilik kullanarak, bir bağımsız değişken bir işleve, düğme sınıfı gibi temel sınıfı olarak geçirilebilir. Gerçek bağımsız değişken, bir radyo düğmesi sınıfı gibi türetilmiş bir sınıf olabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Idebugciltçi](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
