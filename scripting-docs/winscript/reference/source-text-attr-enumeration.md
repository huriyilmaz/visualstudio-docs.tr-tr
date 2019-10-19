---
title: SOURCE_TEXT_ATTR numaralandırması | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SOURCE_TEXT_ATTR constants
ms.assetid: 459384b0-1463-4841-a2b3-a993207163bf
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1dd0bbf08b6ddfdcfbffa494fdda9842004839b0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572995"
---
# <a name="source_text_attr-enumeration"></a>SOURCE_TEXT_ATTR Numaralandırması
Kaynak metnin tek bir karakterinin özniteliklerini açıklar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
enum enum_SOURCE_TEXT_ATTR{    SOURCETEXT_ATTR_KEYWORD    = 0x0001,    SOURCETEXT_ATTR_COMMENT    = 0x0002,    SOURCETEXT_ATTR_NONSOURCE    = 0x0004,    SOURCETEXT_ATTR_OPERATOR   = 0x0008,    SOURCETEXT_ATTR_NUMBER    = 0x0010,    SOURCETEXT_ATTR_STRING    = 0x0020,    SOURCETEXT_ATTR_FUNCTION_START  = 0x0040};  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Değer|Açıklama|  
|------------|-----------|-----------------|  
|SOURCETEXT_ATTR_KEYWORD|0x0001|Karakter bir dil anahtar sözcüğünün parçasıdır, örneğin, VBScript anahtar sözcüğü `While`.|  
|SOURCETEXT_ATTR_COMMENT|0x0002|Karakter bir açıklama bloğunun parçasıdır.|  
|SOURCETEXT_ATTR_NONSOURCE|0x0004|Karakter, derlenmiş dil kaynak metninin bir parçası değil. Örneğin, bir betik bloğunu çevreleyen HTML.|  
|SOURCETEXT_ATTR_OPERATOR|0x0008|Karakter bir dil işlecinin parçasıdır. Örneğin: aritmetik işleç **+** .|  
|SOURCETEXT_ATTR_NUMBER|0x0010|Karakter, dilin sayısal sabitinin bir parçasıdır.  Örneğin, 3,14159 sabiti.|  
|SOURCETEXT_ATTR_STRING|0x0020|Karakter bir dil dizesi sabitinin parçasıdır. Örneğin, "Merhaba Dünya" dizesi.|  
|SOURCETEXT_ATTR_FUNCTION_START|0x0040|Karakter, bir işlev bloğunun başlangıcını belirtir|  
  
## <a name="remarks"></a>Açıklamalar  
 Genellikle, `IDebugDocumentHost::GetScriptTextAttributes`, `IActiveScriptDebug::GetScriptletTextAttributes` ve `IActiveScriptDebug::GetScriptTextAttributes` yöntemleri, şu durumlar dışında her karakter için bir metin özniteliği döndürür:  
  
- GETATTRTYPE_DEPSCAN bayrağı ayarlanır; Bu durumda yöntemin SOURCETEXT_ATTR_IDENTIFIER ve SOURCETEXT_ATTR_MEMBERLOOKUP bayraklarını döndürebileceği,  
  
- GETATTRFLAG_THIS bayrağı ayarlanır; Bu durumda yöntemin SOURCETEXT_ATTR_THIS bayrağını döndürebileceği,  
  
- GETATTRFLAG_HUMANTEXT bayrağı ayarlanır, bu durumda yöntemin SOURCETEXT_ATTR_HUMANTEXT bayrağını döndürebileceği durumdur.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Etkin Betik Hata Ayıklayıcı Sabitleri, Sabit Listeleri ve Yapıları](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)