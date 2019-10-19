---
title: 'Idebugdocumenttextevents:: onUpdateTextAttributes | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextEvents.onUpdateTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentTextEvents::onUpdateTextAttributes
ms.assetid: 24a6d409-3137-4a7a-ac24-0955c109902f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 044eec93516bc4e16044c4bf982b48d91269ebaa
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575992"
---
# <a name="idebugdocumenttexteventsonupdatetextattributes"></a>IDebugDocumentTextEvents::onUpdateTextAttributes
Temel alınan karakter konumu aralığı ile ilişkili metin özniteliklerinin değiştiğini gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT onUpdateTextAttributes(  
   ULONG  cCharacterPosition,  
   ULONG  cNumToUpdate  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cCharacterPosition`  
 'ndaki Özniteliklerin değiştiği ilk karakterin karakter konumu.  
  
 `cNumToUpdate`  
 'ndaki Aralıktaki karakterlerin sayısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, temeldeki karakter konum aralığı ile ilişkili metin özniteliklerinin değiştiğini gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugDocumentTextEvents Arabirimi](../../winscript/reference/idebugdocumenttextevents-interface.md)