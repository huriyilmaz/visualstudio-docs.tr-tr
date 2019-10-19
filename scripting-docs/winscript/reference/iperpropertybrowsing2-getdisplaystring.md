---
title: 'IPerPropertyBrowsing2:: GetDisplayString | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.GetDisplayString
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::GetDisplayString
ms.assetid: 8f75c6a9-86a9-4e2d-8cb4-74e7b1c0a524
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bc702ad15d1aba04bf991c04b585728afde4fb41
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571456"
---
# <a name="iperpropertybrowsing2getdisplaystring"></a>IPerPropertyBrowsing2::GetDisplayString
Doğal olarak görüntülenebilen türleri göstermek için bir dize alır döndürülen metin, özelliği açıklayan bir addır ve çağıranın Kullanıcı arabiriminde görüntülenebilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetDisplayString(  
   DISPID  dispid,  
   BSTR*  pBstr  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dispid`  
 'ndaki Görünen adı istenen özelliğin dağıtım tanıtıcısı.  
  
 `pBstr`  
 dışı @No__t_1 tarafından tanımlanan özelliğin görünen adını içeren `BSTR` işaretçisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Geçerli bir `HRESULT` döndürür, genellikle `S_OK`.  
  
## <a name="remarks"></a>Açıklamalar  
 Döndürülen dize, özelliğin geçerli bir değeri değil. Yalnızca özelliğin bir dize görüntülerdir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IPerPropertyBrowsing2 Arabirimi 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)