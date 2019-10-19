---
title: 'Idebugdocumenttextevents:: Onupdatebelgetattributes | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextEvents.onUpdateDocumentAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentTextEvents::onUpdateDocumentAttributes
ms.assetid: 48fa909c-14c2-4ca4-af86-a5809c72dd39
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c256d2cc6d826a72eb369cda0ad1e5f108e909bc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576041"
---
# <a name="idebugdocumenttexteventsonupdatedocumentattributes"></a>IDebugDocumentTextEvents::onUpdateDocumentAttributes
Belge özniteliklerinin değiştiğini gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT onUpdateDocumentAttributes(  
   TEXT_DOC_ATTR  textdocattr  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `textdocattr`  
 'ndaki Yeni belge öznitelikleri.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, belge özniteliklerinin değiştiğini gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Idebugdocumenttextevents arabirimi](../../winscript/reference/idebugdocumenttextevents-interface.md)    
 [TEXT_DOC_ATTR Sabitleri](../../winscript/reference/text-doc-attr-constants.md)