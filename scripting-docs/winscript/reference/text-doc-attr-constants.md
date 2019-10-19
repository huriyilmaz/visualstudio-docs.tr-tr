---
title: TEXT_DOC_ATTR sabitleri | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- TEXT_DOC_ATTR
apilocation:
- scrobj.dll
helpviewer_keywords:
- TEXT_DOC_ATTR constants
ms.assetid: fd9c53a4-8f73-4c6a-abe5-6b831ecd5b1e
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3604c06b6cb36cc4ff7ef6c76348b5ece53bed61
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572991"
---
# <a name="text_doc_attr-constants"></a>TEXT_DOC_ATTR Sabitleri
Belgenin özniteliklerini açıklar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
typedef DWORD TEXT_DOC_ATTR;  
```  
  
## <a name="constants"></a>Sabitler  
  
|Sabit|Değer|Açıklama|  
|--------------|-----------|-----------------|  
|TEXT_DOC_ATTR_READONLY|0x00000001|Belge salt okunurdur.|  
|TEXT_DOC_ATTR_TYPE_PRIMARY|0x00000002|Belge, bu belge ağacının birincil dosyasıdır.|  
|TEXT_DOC_ATTR_TYPE_WORKER|0x00000004|Belge bir çalışandır.|  
|TEXT_DOC_ATTR_TYPE_SCRIPT|0x00000008|Belge bir komut dosyasıdır.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Etkin Betik Hata Ayıklayıcı Sabitleri, Sabit Listeleri ve Yapıları](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)