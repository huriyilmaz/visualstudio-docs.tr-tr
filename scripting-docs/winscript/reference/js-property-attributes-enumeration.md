---
title: JS_PROPERTY_ATTRIBUTES numaralandırması | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JS_PROPERTY_ATTRIBUTES
apilocation:
- jscript9diag.dll
ms.assetid: e83b9b6c-5b21-48d1-92b6-22bed926b18b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 94a72228e1ad6ab49568f3291ad9add7209ef3da
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571739"
---
# <a name="js_property_attributes-enumeration"></a>JS_PROPERTY_ATTRIBUTES Listelemesi
Bir özelliğin özniteliklerini gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
enum JS_PROPERTY_ATTRIBUTES{   JS_PROPERTY_ATTRIBUTE_NONE = 0,   JS_PROPERTY_HAS_CHILDREN = 0x1,   JS_PROPERTY_FAKE = 0x2,   JS_PROPERTY_METHOD = 0x4,   JS_PROPERTY_READONLY = 0x8,   JS_PROPERTY_NATIVE_WINRT_POINTER = 0x10} JS_PROPERTY_ATTRIBUTES;  
```  
  
## <a name="members"></a>Üyeler  
  
|Name|Açıklama|  
|----------|-----------------|  
|`JS_PROPERTY_ATTRIBUTE_NONE`|Özelliğin öznitelikleri yok.|  
|`JS_PROPERTY_HAS_CHILDREN`|Özelliğin alt öğesi vardır.|  
|`JS_PROPERTY_FAKE`|Özelliği, "[Methods]" gibi sahte bir düğümü temsil eder.|  
|`JS_PROPERTY_METHOD`|Özelliği bir yöntemdir.|  
|`JS_PROPERTY_READONLY`|Özellik salt okunurdur.|  
|`JS_PROPERTY_NATIVE_WINRT_POINTER`|Özelliği, yerel bir WinRT nesnesine yönelik bir işaretçidir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Üstbilgi:** jscript9diag. h  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Windows Betik Arabirimleri Başvurusu](../../winscript/reference/windows-script-interfaces-reference.md)