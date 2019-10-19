---
title: 'Iscriptscriptlet:: Setsubıtemname | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptScriptlet.SetSubItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptScriptlet::SetSubItemName
ms.assetid: 619f222f-b4c3-4c7b-9d19-e4e7037343a6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab4f7afec9302126ccbfcbe7f2abafc74cbf17d6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571853"
---
# <a name="iscriptscriptletsetsubitemname"></a>IScriptScriptlet::SetSubItemName
Bir kod oluşturma yöntemi nesnesinin nesne konağının tam adı içindeki son tanımlayıcıyı ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT SetSubItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `psz`  
 Konağın tam kod oluşturma yöntemi adında birden fazla düzey varsa, `psz` ikinci düzeydeki tanımlayıcının arabellek adresidir.  
  
 Konağın tam kod oluşturma yöntemi adı bir düzey içeriyorsa, `psz` ilk düzeydeki tanımlayıcının arabellek adresidir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IScriptScriptlet Arabirimi](../../winscript/reference/iscriptscriptlet-interface.md)