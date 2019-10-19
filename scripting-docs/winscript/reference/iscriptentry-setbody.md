---
title: 'Icriptentry:: SetBody | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetBody
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetBody
ms.assetid: 719062e4-98e4-4a7b-946d-6e5dbbcc5225
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1af865c8366481204ee413377a083b09d8c97383
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575375"
---
# <a name="iscriptentrysetbody"></a>IScriptEntry::SetBody
@No__t_0 betik bloğunun gövdesinde bulunan metni veya bir `IScriptScriptlet` kod oluşturma yöntemi belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT SetBody(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `psz`  
 'ndaki Bir `IScriptEntry` betik bloğunda, `psz` komut dosyası etiketlerinin içine alınmış metindir.  
  
 @No__t_0 işlev bloğu için, `psz` işlev gövdesidir.  
  
 @No__t_0 nesnesi (`IScriptEntry` türeten türetilmiş) için, `psz`, kod oluşturma yöntemi 'in betik metintir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Icriptentry arabirimi](../../winscript/reference/iscriptentry-interface.md)    
 [IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)