---
title: 'Icriptentry:: GetSignature | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetSignature
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetSignature
ms.assetid: 8cbf37ac-b14c-4e15-a613-06f34857da9b
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e7b07ac64ce7e427a793f0af0db9a7905441d39b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575414"
---
# <a name="iscriptentrygetsignature"></a>IScriptEntry::GetSignature
@No__t_0 Function nesnesinin tür bilgilerini döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetSignature(  
   ITypeInfo          **ppti  
   ULONG              *piMethod  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppti`  
 dışı Bu `IScriptEntry` Function nesnesiyle ilişkili bilgileri yazın.  
  
 `piMethod`  
 dışı @No__t_0 nesnesindeki Yöntem dizini.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 [Icriptentry:: SetSignature](../../winscript/reference/iscriptentry-setsignature.md) veya [ıcriptnode:: CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)kullanarak tür bilgilerini ayarlarsınız. Tür bilgileri, iç işlev gösterimine göre giriş tarafından da oluşturulabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IScriptEntry Arabirimi](../../winscript/reference/iscriptentry-interface.md)