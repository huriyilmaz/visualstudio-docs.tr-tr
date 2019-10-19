---
title: 'Idebugbelgethost:: NotifyChanged | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.NotifyChanged
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::NotifyChanged
ms.assetid: 33a4a54f-3bcb-4422-b3c0-bdbf46590f34
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a4fc0c744887eb3592c4d94c520f33da86812bfc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569178"
---
# <a name="idebugdocumenthostnotifychanged"></a>IDebugDocumentHost::NotifyChanged
Ana bilgisayara belgenin kaynak dosyasının kaydedildiğini ve içeriğinin yenilenmesi gerektiğini bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT NotifyChanged();  
```  
  
#### <a name="parameters"></a>Parametreler  
 Bu yöntem hiçbir parametre alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, ana bilgisayara belgenin kaynak dosyasının kaydedildiğini ve içeriğinin yenilenmesi gerektiğini bildirir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugDocumentHost Arabirimi](../../winscript/reference/idebugdocumenthost-interface.md)