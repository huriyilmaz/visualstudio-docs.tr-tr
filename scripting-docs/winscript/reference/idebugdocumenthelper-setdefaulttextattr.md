---
title: 'Idebugbelgethelper:: SetDefaultTextAttr | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.SetDefaultTextAttr
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::SetDefaultTextAttr
ms.assetid: 019a4191-0019-4376-bf70-89b33e7369de
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea63f028497f1eb90803f59423f608d0a42960cf
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574643"
---
# <a name="idebugdocumenthelpersetdefaulttextattr"></a>IDebugDocumentHelper::SetDefaultTextAttr
Komut dosyası bloğunda olmayan metin için kullanılacak varsayılan öznitelikleri ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT SetDefaultTextAttr(  
   SOURCE_TEXT_ATTR  staTextAttr  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `staTextAttr`  
 Varsayılan kaynak metin öznitelikleri.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan öznitelikler bu yöntem tarafından değiştirilmediği takdirde, bir betik bloğu dışındaki metnin varsayılan öznitelikleri SOURCETEXT_ATTR_NONSOURCE ' dir. Kullanıcı arabirimi bu bilgileri betik blokları dışındaki metni salt okunurdur olarak işaretlemek için kullanabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Idebugbelgethelper arabirimini](../../winscript/reference/idebugdocumenthelper-interface.md)    
 [SOURCE_TEXT_ATTR Sabit Listesi](../../winscript/reference/source-text-attr-enumeration.md)