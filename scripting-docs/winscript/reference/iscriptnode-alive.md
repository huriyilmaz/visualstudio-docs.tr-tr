---
title: 'Icriptnode:: canlı | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.Alive
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::Alive
ms.assetid: d2755c83-e9b9-4c0a-acb7-25b554fc9fe8
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b7e0216824506ee942b42a42d5c3c4475f63f9e2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573623"
---
# <a name="iscriptnodealive"></a>IScriptNode::Alive
Bir nesnenin hala etkin olup olmadığını gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT Alive();  
```  
  
#### <a name="parameters"></a>Parametreler  
 Yöntem hiçbir parametre alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Betik düğümü hala etkin.|  
  
## <a name="remarks"></a>Açıklamalar  
 Nesne etkin değilse, bileşen nesne modeli (COM) Bu metoda yapılan çağrılar için sıralama proxy 'sinden bir hata döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IScriptNode Arabirimi](../../winscript/reference/iscriptnode-interface.md)