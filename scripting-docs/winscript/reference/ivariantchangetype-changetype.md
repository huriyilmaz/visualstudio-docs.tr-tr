---
title: 'Ivariantchangetype:: ChangeType | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IVariantChangeType.ChangeType
apilocation:
- scrobj.dll
helpviewer_keywords:
- IVariantChangeType::ChangeType
ms.assetid: 52374764-c42e-49af-a219-ee00c535a118
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 406d5d8486b3016f0105b7bd8bf231db0e1e9613
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571775"
---
# <a name="ivariantchangetypechangetype"></a>IVariantChangeType::ChangeType
Bir değişken değeri alır ve belirtilen türe sahip yeni bir değişken oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT ChangeType(  
   VARIANT*  pvarDst,  
   VARIANT*  pvarSrc,  
   LCID  lcid,  
   VARTYPE  vtNew  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pvarDst`  
 [in, out] @No__t_0 tarafından temsil edilen değeri içeren, ancak `vtNew` tarafından belirtilen türde bir değişken.  
  
 `pvarSrc`  
 'ndaki Yeni bir türe değiştirilecek bir Varyant değeri.  
  
 `lcid`  
 'ndaki Bağımsız değişkenler dizeden veya dizeden dönüştürülürken kullanılacak yerel ayar bağlamı.  
  
 `vtNew`  
 'ndaki Yapılacak `pvarDst` türünü belirtir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t_0 ve `pvarSrc` bağımsız değişkenleri eşit olabilir, bu durumda orijinal değerin üzerine yazılır. Bu yöntem, `VariantClear` işlevine `pvarDst` geçirir ve sonuç olarak `pvarDst` geçerli bir değere başlatılmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IVariantChangeType Arabirimi](../../winscript/reference/ivariantchangetype-interface.md)