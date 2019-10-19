---
title: 'Ibindeventhandler:: BindHandler | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IBindEventHandler.BindHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IBindEventHandler::BindHandler
ms.assetid: 87909828-2224-4bb1-a6c9-dfe715ac4c9b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 160020832509c9fb2aa95c095148127228a92e17
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572577"
---
# <a name="ibindeventhandlerbindhandler"></a>IBindEventHandler::BindHandler
Bir olayı nesnesine bağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT BindHandler(  
   LPCOLESTR   pstrEvent,  
   IDispatch*  pdisp  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pstrEvent`  
 'ndaki İşlenecek olayı belirtir.  
  
 `pdisp`  
 'ndaki Olayı işleyecek nesneyi belirtir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem bir olayı bir nesnesine bağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IBindEventHandler Arabirimi](../../winscript/reference/ibindeventhandler-interface.md)