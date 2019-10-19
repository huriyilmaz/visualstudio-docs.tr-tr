---
title: 'Iapplicationdebugger:: QueryAlive | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.QueryAlive
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::QueryAlive
ms.assetid: 41181ebb-a3bf-4e41-82af-d6c7348dc706
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 867d00a4ef42aa8759496540edc1937fc6f2a0a6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577821"
---
# <a name="iapplicationdebuggerqueryalive"></a>IApplicationDebugger::QueryAlive
Hata ayıklayıcının yanıt verdiğini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT QueryAlive();  
```  
  
#### <a name="parameters"></a>Parametreler  
 Bu yöntem hiçbir parametre alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, hata ayıklayıcının yanıt verdiğini gösterir. Bu yöntemin uygulamaları her zaman `S_OK` döndürmelidir.  
  
 Hata ayıklayıcı işlemi beklenmedik şekilde sonlandırılırsa, COM Bu metoda yapılan çağrılar için sıralama proxy 'sinden bir hata döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IApplicationDebugger Arabirimi](../../winscript/reference/iapplicationdebugger-interface.md)