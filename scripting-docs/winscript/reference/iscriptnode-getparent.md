---
title: 'Icriptnode:: GetParent | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.GetParent
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetParent
ms.assetid: 0fb813f6-ab94-46b2-b0cf-ef5d1cd38ae4
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 58ef5f88f4404d57a7edad3590fba1d2614faec6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572562"
---
# <a name="iscriptnodegetparent"></a>IScriptNode::GetParent
Nesnenin üst öğesi olan `IScriptNode` nesnesini döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetParent(  
   IScriptNode       **ppsnParent  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppsnParent`  
 dışı Üst örneğin `IScriptNode` arabirimine bir işaretçi alan bir değişkenin adresi.  
  
 Sınıf `IScriptEntry` veya `IScriptScriptlet` uygularsa, bir `IScriptNode` nesnesi döndürülür.  
  
 Sınıf `IScriptNode` uygularsa (bir Web sayfasını temsil eder), NULL döndürülür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IScriptNode Arabirimi](../../winscript/reference/iscriptnode-interface.md)