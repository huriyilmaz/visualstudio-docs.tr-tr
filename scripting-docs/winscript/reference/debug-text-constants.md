---
title: DEBUG_TEXT sabitleri | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5dde10c3-7040-46b1-a328-959c6ce5cd9f
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: facbdc1258b3fca72a239d9d5cc41772cf577f13
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577365"
---
# <a name="debug_text-constants"></a>DEBUG_TEXT Sabitleri
[Idebugexpressioncontext::P arseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md)sırasında kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
typedef DWORD DEBUG_TEXT;  
```  
  
## <a name="constants"></a>Sabitler  
  
|Sabit|Değer|Açıklama|  
|--------------|-----------|-----------------|  
|DWORD DEBUG_TEXT_ISEXPRESSION|0x00000001|Metnin bir deyimin aksine bir ifade olduğunu gösterir. Bu bayrak, metnin bazı diller tarafından ayrıştırılma şeklini etkileyebilir.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Bir dönüş değeri varsa, bu, çağıran tarafından kullanılır.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|Yan etkilere izin verme. Bu bayrak ayarlandıysa, ifadenin değerlendirmesi çalışma zamanı durumunu değiştirmez.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Metnin değerlendirmesi sırasında kesme noktalarına izin verin. Bu bayrak ayarlanmamışsa, metnin değerlendirmesi sırasında kesme noktaları yok sayılır.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Metnin değerlendirmesi sırasında hata raporlarına izin verin. Bu bayrak ayarlanmamışsa, değerlendirme sırasında hatalar konağa bildirilmeyecektir.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|İfadenin kendisini çalıştırmak yerine bir kod bağlamı olarak değerlendirilmesi gerektiğini gösterir.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Etkin Betik Hata Ayıklayıcı Sabitleri, Sabit Listeleri ve Yapıları](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)