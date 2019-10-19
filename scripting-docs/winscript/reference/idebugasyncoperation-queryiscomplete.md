---
title: 'Ihata ayıklama Gasyncoperation:: Queryıstamam| Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.QueryIsComplete
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::QueryIsComplete
ms.assetid: fcf6e229-4d40-46d9-ab81-d3561bc8e084
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51bbfa6a19a247f378a0408e250651c94219fcb5
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573266"
---
# <a name="idebugasyncoperationqueryiscomplete"></a>IDebugAsyncOperation::QueryIsComplete
Hata ayıklama işleminin tamamlanıp tamamlanmadığını belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT QueryIsComplete();  
```  
  
#### <a name="parameters"></a>Parametreler  
 Bu yöntem hiçbir parametre alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|İşlem tamamlanmıştır.|  
|`S_FALSE`|İşlem tamamlanmadı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, hata ayıklama işleminin tamamlanıp tamamlanmadığını belirler.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugAsyncOperation Arabirimi](../../winscript/reference/idebugasyncoperation-interface.md)