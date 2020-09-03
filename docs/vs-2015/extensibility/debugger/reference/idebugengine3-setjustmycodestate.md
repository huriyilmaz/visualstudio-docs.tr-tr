---
title: 'IDebugEngine3:: Setadatmycodestate | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ebaf697bfdfff435c12eee1002ff93f4eba7ed65
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195856"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu yöntem, hata ayıklama altyapısına, Adatmycode durum bilgilerini söyler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SetJustMyCodeState(  
   BOOL           fUpdate,  
   DWORD          dwModules,  
   JMC_CODE_SPEC* rgJMCSpec  
);  
```  
  
```csharp  
int SetJustMyCodeState(  
   int             fUpdate,   
   uint            dwModules,   
   JMC_CODE_SPEC[] rgJMCSpec  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `fUpdate`  
 'ndaki `TRUE`Geçerli bilgileri güncelleştirmek için sıfır olmayan () ( `FALSE` daha önce ayarlanmış herhangi bir şey yok sayılıyor).  
  
 `dwModules`  
 'ndaki İçindeki bilgi yapılarının sayısı `rgJMCSpec.`  
  
 `rgJMCSpec`  
 'ndaki Kullanılacak [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) yapıları dizisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Adammycode, bu sistem kodu için kaynak kodu kullanılabilir olsa bile, yalnızca bir kullanıcıya ait kodu ve sistem kodu gibi tüm ara kodları yok saymanın hata ayıklaması kavramıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)   
 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)
