---
title: 'Icriptentry:: SetSignature | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetSignature
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetSignature
ms.assetid: 8513587d-9df2-4621-afe7-56eacbb5e688
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e381e642462fe56e661de9da0d8974dc7bf18b18
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575347"
---
# <a name="iscriptentrysetsignature"></a>IScriptEntry::SetSignature
@No__t_0 Function nesnesinin tür bilgilerini ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT SetSignature(  
   ITypeInfo          *pti  
   ULONG              iMethod  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pti`  
 'ndaki Tür bilgileri.  
  
 `iMethod`  
 'ndaki @No__t_0 nesnesindeki Yöntem dizini.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t_0 veya [ıcriptnode:: CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)kullanarak tür bilgilerini ayarlarsınız. Tür bilgileri, iç işlev gösterimine göre giriş tarafından da oluşturulabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IScriptEntry Arabirimi](../../winscript/reference/iscriptentry-interface.md)