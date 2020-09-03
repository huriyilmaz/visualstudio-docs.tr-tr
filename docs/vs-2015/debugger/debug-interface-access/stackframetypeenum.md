---
title: StackFrameTypeEnum | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 655911bac1efbafe1838e24e2056282f9036479b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179195"
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Yığın çerçeve türünü belirtir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum StackFrameTypeEnum {  
   FrameTypeFPO,  
   FrameTypeTrap,  
   FrameTypeTSS,  
   FrameTypeStandard,  
   FrameTypeFrameData,  
   FrameTypeUnknown = -1  
};  
```  
  
## <a name="elements"></a>Öğeler  
 `FrameTypeFPO`  
 Çerçeve işaretçisi atlandı; Mi bilgileri kullanılabilir.  
  
 `FrameTypeTrap`  
 Çekirdek Tuzak Çerçevesi.  
  
 `FrameTypeTSS`  
 Çekirdek Tuzak Çerçevesi.  
  
 `FrameTypeStandard`  
 Standart EBP yığın çerçevesi.  
  
 `FrameTypeFrameData`  
 Çerçeve işaretçisi atlandı; Çerçeve veri bilgileri kullanılabilir.  
  
 `FrameTypeUnknown`  
 Herhangi bir hata ayıklama bilgisi olmayan çerçeve.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu Numaralandırmadaki değerler, [IDiaStackFrame:: get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md) metoduna yapılan bir çağrı tarafından döndürülür.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: cvconst. h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Numaralandırmalar ve yapılar](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)
