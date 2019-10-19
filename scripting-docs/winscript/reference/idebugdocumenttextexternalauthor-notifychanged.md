---
title: 'Idebugdocumenttextexternalauthor:: NotifyChanged | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextExternalAuthor.NotifyChanged
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentTextExternalAuthor::NotifyChanged
ms.assetid: f0de7984-3a15-49e2-bd29-f768f34d2a4d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad02db80bd24a8a5ba96abaa61e85be9d69e553e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575949"
---
# <a name="idebugdocumenttextexternalauthornotifychanged"></a>IDebugDocumentTextExternalAuthor::NotifyChanged
Ana bilgisayara belge kaynağının değiştiğini bildirir.  
  
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
 Bu yöntem, dosya tabanlı bir hata ayıklayıcı belge değiştirildikten sonra bir harici düzenleyici tarafından çağrılır ve bu, belge kaynağının değiştiğini konağa bildirir. Daha sonra ana bilgisayar, belgeyi kaynak dosyasından yeniler.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugDocumentTextExternalAuthor Arabirimi](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)