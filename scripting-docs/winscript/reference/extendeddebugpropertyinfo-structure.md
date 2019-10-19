---
title: Extendeddebugpropertyınfo yapısı | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ExtendedDebugPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- ExtendedDebugPropertyInfo structure
ms.assetid: f2cf6477-454b-4d13-95da-ae4c90daa175
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 09f3c5a219fca9ec9b881e2ae8363aae4d48e03f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575830"
---
# <a name="extendeddebugpropertyinfo-structure"></a>ExtendedDebugPropertyInfo Yapısı
Genişletilmiş özelliği niteleyen `DebugPropertyInfo` yapısını ek üyelerle genişletir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
typedef struct ExtendedDebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   LPOLESTR  bstrName;  
   LPOLESTR  bstrType;  
   LPOLESTR  bstrValue;  
   LPOLESTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
   DWORD  nDISPID;  
   DWORD  nType;  
   VARIANT  varValue;  
   ILockBytes*  plbValue;  
   IDebugExtendedProperty*  pDebugExtProp;  
};  
```  
  
## <a name="members"></a>Üyeler  
 `dwValidFields`  
 Hangi alanların başlatıldığını belirtmek için kullanılan bir numaralandırılmış veri türü.  
  
 `bstrName`  
 Bağlam içindeki Özellik adı.  
  
 `bstrType`  
 Özellik türü, biçimli dize olarak.  
  
 `bstrValue`  
 Biçimli bir dize olarak özellik değeri.  
  
 `bstrFullName`  
 Özelliğin tam adı.  
  
 `dwAttrib`  
 Hata ayıklama özelliği özniteliklerinin bayraklarını belirten bir sabit listesi.  
  
 `pDebugProp`  
 Bu `ExtendedDebugPropertyInfo` karşılık gelen nesne `IDebugProperty`.  
  
 `nDISPID`  
 Dağıtım kimliği.  
  
 `nType`  
 Genişletilmiş özellik türü.  
  
 `varValue`  
 DEĞIŞKENLE uyum için genişletilmiş özellik değeri.  
  
 `plbValue`  
 Özellik değerinin gerçek veri baytları.  
  
 `pDebugExtProp`  
 Bu `ExtendedDebugPropertyInfo` karşılık gelen nesne `IDebugExtendedProperty`.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Debugpropertyınfo yapısı](../../winscript/reference/debugpropertyinfo-structure.md)    
 [Idebugproperty arabirimi](../../winscript/reference/idebugproperty-interface.md)    
 [Idebugextendedproperty arabirimi](../../winscript/reference/idebugextendedproperty-interface.md)    
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)    
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)