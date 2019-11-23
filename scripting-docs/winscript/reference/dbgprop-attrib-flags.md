---
title: DBGPROP_ATTRIB_FLAGS | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DBGPROP_ATTRIB_FLAGS
apilocation:
- scrobj.dll
f1_keywords:
- DBGPROP_ATTRIB_FLAGS
helpviewer_keywords:
- DBGPROP_ATTRIB_FLAGS
ms.assetid: 90314496-527b-4357-9df8-125a360bf216
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3170e310aa3177e2ca7a1dd81ead02bcc4050114
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572602"
---
# <a name="dbgprop_attrib_flags"></a>DBGPROP_ATTRIB_FLAGS
`IDebugProperty`için çeşitli öznitelikleri açıklar. `DebugPropertyInfo` yapısının üyesi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
enum {  
DBGPROP_ATTRIB_NO_ATTRIB  =0x00000000,  
   DBGPROP_ATTRIB_VALUE_IS_INVALID  =0x00000008,  
   DBGPROP_ATTRIB_VALUE_IS_EXPANDABLE  =0x00000010,  
   DBGPROP_ATTRIB_VALUE_READONLY  =0x00000800,  
   DBGPROP_ATTRIB_ACCESS_PUBLIC  =0x00001000,  
   DBGPROP_ATTRIB_ACCESS_PRIVATE  =0x00002000,  
   DBGPROP_ATTRIB_ACCESS_PROTECTED  =0x00004000,  
   DBGPROP_ATTRIB_ACCESS_FINAL  =0x00008000,  
   DBGPROP_ATTRIB_STORAGE_GLOBAL  =0x00010000,  
   DBGPROP_ATTRIB_STORAGE_STATIC  =0x00020000,  
   DBGPROP_ATTRIB_STORAGE_FIELD  =0x00040000,  
   DBGPROP_ATTRIB_STORAGE_VIRTUAL  =0x00080000,  
   DBGPROP_ATTRIB_TYPE_IS_CONSTANT  =0x00100000,  
   DBGPROP_ATTRIB_TYPE_IS_SYNCHRONIZED  =0x00200000,  
   DBGPROP_ATTRIB_TYPE_IS_VOLATILE  =0x00400000,  
   DBGPROP_ATTRIB_HAS_EXTENDED_ATTRIBS  =0x00800000  
   DBGPROP_ATTRIB_VALUE_IS_RETURN_VALUE  =0x08000000,  
};  
  
```  
  
## <a name="members"></a>Üyeler  
 DBGPROP_ATTRIB_NO_ATTRIB  
 Öznitelik olmadığını gösterir.  
  
 DBGPROP_ATTRIB_VALUE_IS_INVALID  
 `DebugPropertyInfo::bstrValue` değerinin geçerli olmadığını gösterir.  
  
 DBGPROP_ATTRIB_VALUE_IS_EXPANDABLE  
 Başvurunun veya özelliğin alt öğe olduğunu gösterir.  
  
 DBGPROP_ATTRIB_VALUE_READONLY  
 Değerin salt okunurdur olduğunu gösterir.  
  
 DBGPROP_ATTRIB_ACCESS_PUBLIC  
 Ortak erişime sahip bir nesneyi gösterir.  
  
 DBGPROP_ATTRIB_ACCESS_PRIVATE  
 Özel erişimi olan bir nesneyi gösterir.  
  
 DBGPROP_ATTRIB_ACCESS_PROTECTED  
 Korumalı erişimi olan bir nesneyi gösterir.  
  
 DBGPROP_ATTRIB_ACCESS_FINAL  
 Son erişimi olan bir nesneyi gösterir.  
  
 DBGPROP_ATTRIB_STORAGE_GLOBAL  
 Genel depolamayı gösterir.  
  
 DBGPROP_ATTRIB_STORAGE_STATIC  
 Statik depolamayı gösterir.  
  
 DBGPROP_ATTRIB_STORAGE_FIELD  
 Özelliği olan bir nesneyi gösterir.  
  
 DBGPROP_ATTRIB_STORAGE_VIRTUAL  
 Sanal depolamayı gösterir.  
  
 DBGPROP_ATTRIB_TYPE_IS_CONSTANT  
 Nesne türünün sabit olduğunu gösterir.  
  
 DBGPROP_ATTRIB_TYPE_IS_SYNCHRONIZED  
 Bu yuvanın iş parçacığı eşitlenmiş olduğunu gösterir.  
  
 DBGPROP_ATTRIB_TYPE_IS_VOLATILE  
 Bu yuvanın kalıcı depolamaya göre geçici olduğunu gösterir.  
  
 DBGPROP_ATTRIB_HAS_EXTENDED_ATTRIBS  
 Bu yuvanın yukarıda ve bu önceden tanımlanmış bitlerin ötesinde özniteliklerin olduğunu gösterir.  
  
 DBGPROP_ATTRIB_VALUE_IS_RETURN_VALUE  
 Değerin bir işlevden döndürülen değer olduğunu gösterir.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu bayraklar bir nesnenin alt öğelerini filtrelemek için de kullanılır. Değerler bit düzeyinde OR ile birleştirilebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Idebugproperty arabirimi](../../winscript/reference/idebugproperty-interface.md)   
 [DebugPropertyInfo Yapısı](../../winscript/reference/debugpropertyinfo-structure.md)