---
title: 'Icriptentry:: GetBody | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetBody
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetBody
ms.assetid: 419c8c11-a1f8-4b97-ab00-e8af2b2f9bfc
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aba6019f4729f1b4a31933a4ca93c0eddf6159a2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575483"
---
# <a name="iscriptentrygetbody"></a>IScriptEntry::GetBody
Bir `IScriptEntry` betik bloğunun, işlev bloğunun veya kod oluşturma yöntemi gövdesine karşılık gelen metni döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetBody(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pbstr`  
 dışı Aşağıdakilerden birinin gövdesinde bulunan metin:  
  
- @No__t_0 betik bloğu  
  
- İşlev bloğunda `IScriptEntry` işlevi  
  
- Bir `IScriptEntry` kod oluşturma yöntemi olay işleyicisi  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IScriptEntry Arabirimi](../../winscript/reference/iscriptentry-interface.md)