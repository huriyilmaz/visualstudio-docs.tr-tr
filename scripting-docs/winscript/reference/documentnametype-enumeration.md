---
title: DOCUMENTNAMETYPE numaralandırması | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DOCUMENTNAMETYPE
apilocation:
- scrobj.dll
helpviewer_keywords:
- DOCUMENTNAMETYPE enumeration
ms.assetid: d36d550e-efb4-493d-8971-4de267005654
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 401eb759523ed1a33d24c3a298db0b3de2b7d5a7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575869"
---
# <a name="documentnametype-enumeration"></a>DOCUMENTNAMETYPE Listelemesi
Bir belge için hangi türün alınacağını açıklar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
typedef enum tagDOCUMENTNAMETYPE {  
   DOCUMENTNAMETYPE_APPNODE,  
   DOCUMENTNAMETYPE_TITLE,  
   DOCUMENTNAMETYPE_FILE_TAIL,  
   DOCUMENTNAMETYPE_URL,  
DOCUMENTNAMETYPE_UNIQUE_TITLE,} DOCUMENTNAMETYPE;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|DOCUMENTNAMETYPE_APPNODE|Adı uygulama ağacında göründüğü şekilde alır.|  
|DOCUMENTNAMETYPE_TITLE|Görüntüleyici başlık çubuğunda görünen adı alır.|  
|DOCUMENTNAMETYPE_FILE_TAIL|Dosya adını yol olmadan alır.|  
|DOCUMENTNAMETYPE_URL|Belgenin URL 'sini alır.|  
|DOCUMENTNAMETYPE_UNIQUE_TITLE|Tanımlama için sabit listesi eklenmiş başlığı alır.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Etkin Betik Hata Ayıklayıcı Sabitleri, Sabit Listeleri ve Yapıları](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)