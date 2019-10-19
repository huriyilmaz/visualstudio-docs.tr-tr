---
title: 'Idebugproperty:: EnumMembers | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.EnumMembers
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::EnumMembers
ms.assetid: 8ce398a5-6452-4804-ae8f-5c54cd11c661
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5f8c5f2cbb107d55e9ffe602cb7d3492701de10c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562428"
---
# <a name="idebugpropertyenummembers"></a>IDebugProperty::EnumMembers
Bir özelliğin üyelerini numaralandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT EnumMembers (  
   DBGPROP_INFO_FLAGSdwFieldSpec,  
   UINTnRadix,  
   REFIIDrefiid,  
   IEnumDebugPropertyInfo**ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwFieldSpec`  
 'ndaki Numaralandırılmış hata ayıklama özelliği yapılarında hangi alanların doldurulacağını belirleyen `DBGPROP_INFO_FLAGS` sabitlerini belirtir.  
  
 `nRadix`  
 'ndaki Herhangi bir sayısal bilgiyi yorumlamak için kullanılan Radix.  
  
 `refiid`  
 'ndaki Bu IID, Numaralandırıcı filtrelemeye yönelik olarak geçirilir. IID, `IDebugPropertyEnumType_All` devraldığı `IDebugPropertyEnumType` arabirimlerinden biridir.  
  
 `ppEnum`  
 dışı Üye özelliklerini numaralandırır `IEnumDebugPropertyInfo` arabirimini döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Geçerli bir `HRESULT` döndürür, genellikle `S_OK`.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Idebugproperty arabirimi](../../winscript/reference/idebugproperty-interface.md)    
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)    
 [IDebugPropertyEnumType_All arabirimi](../../winscript/reference/idebugpropertyenumtype-all-interface.md)    
 [IEnumDebugPropertyInfo Arabirimi](../../winscript/reference/ienumdebugpropertyinfo-interface.md)