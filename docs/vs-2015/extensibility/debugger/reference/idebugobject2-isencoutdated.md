---
title: 'IDebugObject2:: ısencoutte | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject2::IsEncOutdated
helpviewer_keywords:
- IDebugObject2::IsEncOutdated method
ms.assetid: d3a8c02d-895b-478c-9957-d663130f308e
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fa4acd0476a0df75644738840da562db97a34bf6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64796279"
---
# <a name="idebugobject2isencoutdated"></a>IDebugObject2::IsEncOutdated
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu yöntem, bu nesnenin veya üst kapsayıcının düzenleme ve devam etme durumunun güncel olup olmadığını belirler. Özel bir ifade değerlendirici bu yöntemi uygulamaz ve her zaman döndürülür `E_NOTIMPL` .  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT IsEncOutdated(  
   BOOL* pfEncOutdated  
);  
```  
  
```csharp  
int IsEncOutdated(  
   out int pfEncOutdated  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pfEncOutdated`  
 dışı `TRUE`Düzenle ve devam et durumu güncel değilse sıfır (), değilse sıfır () olur `FALSE` .  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
> [!NOTE]
> Özel bir ifade değerlendirici her zaman döndürmelidir `E_NOTIMPL` .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
