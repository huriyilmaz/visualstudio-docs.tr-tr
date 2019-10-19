---
title: 'Idebugdocumenttextauthor:: ReplaceText | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextAuthor.ReplaceText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentTextAuthor::ReplaceText
ms.assetid: f89304e6-5be0-45a5-947d-2c59c3c0a05e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: beca5d0ce19a38346ef9b03e39169769c90ea008
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572040"
---
# <a name="idebugdocumenttextauthorreplacetext"></a>IDebugDocumentTextAuthor::ReplaceText
Belgedeki metni değiştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT ReplaceText(  
   ULONG    cCharacterPosition,  
   ULONG    cNumToReplace,  
   OLECHAR  pcharText[]  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cCharacterPosition`  
 'ndaki Değiştirilecek karakter aralığının başlangıç konumu.  
  
 `cNumToReplace`  
 'ndaki Değiştirilecek karakter sayısı.  
  
 `pcharText[]`  
 'ndaki Eski karakterlerin yerini alacak yeni karakterleri içeren bir arabellek.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem belgedeki metni değiştirir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugDocumentTextAuthor Arabirimi](../../winscript/reference/idebugdocumenttextauthor-interface.md)