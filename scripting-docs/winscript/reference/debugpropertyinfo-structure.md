---
title: Debugpropertyınfo yapısı | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DebugPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- DebugPropertyInfo structure
ms.assetid: 3246efbc-c212-4024-8f07-6414c2f85e75
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 793c83b467460f0744abffe3f161f7510f56257a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575064"
---
# <a name="debugpropertyinfo-structure"></a>DebugPropertyInfo Yapısı
Ad, tür ve değer içeren hiyerarşik bir yapıdaki nesneyi tanımlar. Yerel değişkenlerin hata ayıklama özelliklerini, parametreleri, izleme değişkenlerini ve ifadeleri ve kayıtları anlatmak için kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
typedef struct DebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   BSTR  bstrName;  
   BSTR  bstrType;  
   BSTR  bstrValue;  
   BSTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
};  
```  
  
## <a name="members"></a>Üyeler  
 dwValidFields  
 Hangi alanların başlatıldığını belirtmek için kullanılan bir numaralandırılmış veri türü.  
  
 bstrName  
 Bağlam içindeki Özellik adı.  
  
 bstrType  
 Biçimli dize olarak özellik türü.  
  
 bstrValue  
 Biçimli dize olarak özellik değeri.  
  
 bstrFullName  
 Özelliğin tam adı.  
  
 dwAttrib  
 Hata ayıklama özelliği özniteliklerinin bayraklarını belirten bir sabit listesi.  
  
 pDebugProp  
 Bu `DebugPropertyInfo` yapısındaki bilgiler tarafından açıklanan `IDebugProperty`.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Idebugproperty arabirimi](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)