---
title: 'Idebugdocumenttextevents:: onDestroy | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextEvents.onDestroy
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentTextEvents::onDestroy
ms.assetid: 1b7eb341-6bad-403f-9821-19112f8732f3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fd8162a33e61af0aab23d7414a2283ec60480960
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572928"
---
# <a name="idebugdocumenttexteventsondestroy"></a>IDebugDocumentTextEvents::onDestroy
Temel alınan belgenin yok edildiğini ve artık geçerli olmadığını gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT onDestroy();  
```  
  
#### <a name="parameters"></a>Parametreler  
 Bu yöntem hiçbir parametre alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, temeldeki belgenin yok edildiğini ve artık geçerli olmadığını gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugDocumentTextEvents Arabirimi](../../winscript/reference/idebugdocumenttextevents-interface.md)