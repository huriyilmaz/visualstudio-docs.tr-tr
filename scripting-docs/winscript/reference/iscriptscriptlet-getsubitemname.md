---
title: 'Iscriptscriptlet:: Getsubıtemname | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptScriptlet.GetSubItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptScriptlet::GetSubItemName
ms.assetid: 9ad963fc-9ce8-4b77-92c1-fb90d6307801
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b36f6dd98534b8122a6814f1fd154eca7882251a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571922"
---
# <a name="iscriptscriptletgetsubitemname"></a>IScriptScriptlet::GetSubItemName
Bir kod oluşturma yöntemi nesnesinin nesne konağının tam adı içindeki son tanımlayıcıyı döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetSubItemName(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pbstr`  
 dışı Konağın tam kod oluşturma yöntemi adında birden fazla düzey varsa `pbstr`, tanımlayıcının arabellek adresini ikinci düzeyde döndürür.  
  
 Konağın tam kod oluşturma yöntemi adının bir düzeyi varsa `pbstr`, ilk düzeydeki tanımlayıcının arabellek adresini döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IScriptScriptlet Arabirimi](../../winscript/reference/iscriptscriptlet-interface.md)