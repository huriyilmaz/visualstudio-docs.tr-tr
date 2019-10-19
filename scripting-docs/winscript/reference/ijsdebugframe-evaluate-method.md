---
title: 'IJsDebugFrame:: değerlendir yöntemi | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.Evaluate
apilocation:
- jscript9diag.dll
ms.assetid: 0ee61340-37b8-4fbb-a028-748b5315e279
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6227b97c1fd5fae32db3e13ef72751726c36b043
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573491"
---
# <a name="ijsdebugframeevaluate-method"></a>IJsDebugFrame::Evaluate Yöntemi
Bu yığın çerçevesinin bağlamında bir ifadeyi değerlendirin.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT Evaluate(  
   LPCOLESTR pExpressionText,  
   IJsDebugProperty **ppDebugProperty,  
   BSTR *pError  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pExpressionText`  
 'ndaki Değerlendirilecek ifade.  
  
 `ppDebugProperty`  
 dışı Özellik tarayıcısını temsil eden nesne.  
  
 `pError`  
 dışı Hata oluşursa, hata iletisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
## <a name="remarks"></a>Açıklamalar  
 Şunu döndürür: S_OK: değerlendirme başarılı, * ppDebugProperty değerlendirme sonucunu içerir. S_FALSE: değerlendirme bir hata oluşturur (veya değerlendirme işlemi desteklenmez), \*pError hata mesajını içerir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üstbilgi:** jscript9diag. h  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IJsDebugFrame Arabirimi](../../winscript/reference/ijsdebugframe-interface.md)