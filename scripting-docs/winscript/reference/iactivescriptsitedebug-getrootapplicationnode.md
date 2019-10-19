---
title: 'Iactivescriptsitedebug:: GetRootApplicationNode | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.GetRootApplicationNode
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::GetRootApplicationNode
ms.assetid: 2393f566-6b97-47c0-8041-4dd7e3b1d3a3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b19ed10178d03be0b96393ad08f1eab88ce40329
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570065"
---
# <a name="iactivescriptsitedebuggetrootapplicationnode"></a>IActiveScriptSiteDebug::GetRootApplicationNode
Betik belgelerinin eklenmesi gereken uygulama düğümünü alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetRootApplicationNode(  
   IDebugApplicationNode**  ppdanRoot  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppdanRoot`  
 dışı Betik belgelerini tutan hata ayıklama uygulama düğümü. @No__t_0 olabilir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, komut dosyası belgelerinin eklenmesi gereken uygulama düğümünü döndürür. Betik belgelerinin en üst düzey olması gerekiyorsa, yöntemi `ppdanRoot` için `NULL` döndürebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScriptSiteDebug Arabirimi](../../winscript/reference/iactivescriptsitedebug-interface.md)