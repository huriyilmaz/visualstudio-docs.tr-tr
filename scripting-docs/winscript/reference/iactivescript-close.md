---
title: 'IActiveScript:: Close | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.Close
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_Close
ms.assetid: cc7dd63b-1d7e-410a-857b-09ea3aade275
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f858de42ef2948d218aac6c3194cc6af544da5e9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575789"
---
# <a name="iactivescriptclose"></a>IActiveScript::Close
Komut dosyası altyapısının Şu anda yüklü olan herhangi bir betiği iptal etmesine, durumunu kaybetmesine ve diğer nesnelere sahip olduğu tüm arabirim işaretçilerini, bu nedenle kapalı bir durum girerek serbest bırakılmasına neden olur. Olay havuzları, hemen yürütülen betik metni ve zaten sürmekte olan makro çağırmaları durum değiştirilmeden önce tamamlanır (çalışan bir betik iş parçacığını iptal etmek için [IActiveScript:: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) kullanın). Döngüsel başvuru sorunlarını engellemek için arabirim yayınlanmadan önce bu yöntem, oluşturma ana bilgisayarı tarafından çağrılmalıdır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT Close(void);  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|Değer|Açıklama|  
|-----------|-------------|  
|`S_OK`|Başarılı.|  
|`E_UNEXPECTED`|Çağrı beklenmiyordu (örneğin, komut dosyası altyapısı zaten kapalı durumda).|  
|`OLESCRIPT_S_PENDING`|Yöntem başarıyla sıraya alındı, ancak durum henüz değiştirilmedi. Durum değiştiğinde, site [IActiveScriptSite:: OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) yönteminde geri çağırılır.|  
|`S_FALSE`|Yöntem başarılı oldu, ancak betik zaten kapatılmış.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScript](../../winscript/reference/iactivescript.md)