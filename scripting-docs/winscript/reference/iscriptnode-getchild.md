---
title: 'Icriptnode:: GetChild | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.GetChild
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetChild
ms.assetid: 8cb3f8b0-958b-40bb-a91a-49a788661861
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 27ddde527be1ea4148e4166581ab2cb1a71d15f7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573562"
---
# <a name="iscriptnodegetchild"></a>IScriptNode::GetChild
Düğümde belirtilen dizinde olan alt öğesini döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetChild(  
   ULONG              isn,  
   IScriptNode        **ppsn  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `isn`  
 'ndaki Üst öğe içindeki alt öğenin dizini.  
  
 `ppsn`  
 dışı Alt örneğin `IScriptNode` arabirimine bir işaretçi alan bir değişkenin adresi.  
  
 Bir Web sayfasını temsil eden `IScriptNode` nesneler için, bu parametre betik bloğu içeren bir nesne döndürür.  
  
 Bir betik bloğunu belirten `IScriptEntry` nesneler için, bu parametre bir işlevi belirten bir nesne döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir işlev nesnesi ve `IScriptScriptlet` nesneleri belirten `IScriptEntry` nesneler için, alt girdi bulunmadığından bu yöntem başarısız olur.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IScriptNode Arabirimi](../../winscript/reference/iscriptnode-interface.md)