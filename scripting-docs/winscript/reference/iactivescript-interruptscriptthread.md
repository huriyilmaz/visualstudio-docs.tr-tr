---
title: 'IActiveScript:: InterruptScriptThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.InterruptScriptThread
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_InterruptScriptThread
ms.assetid: 2304d035-6d39-4811-acd3-8a9640fdbef6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a436f973df05b945c0939f3a593640f567774277
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577260"
---
# <a name="iactivescriptinterruptscriptthread"></a>IActiveScript::InterruptScriptThread
Çalışan bir betik iş parçacığının yürütülmesini keser (olay havuzu, anlık yürütme veya makro çağırma). Bu yöntem, takılmış bir betiği sonlandırmak için kullanılabilir (örneğin, sonsuz bir döngüde). Temel olmayan iş parçacıklarından, nesneleri barındırmak için temel olmayan bir belirtme çizgisine veya [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) yöntemine yol açmadan çağrılabilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT InterruptScriptThread(  
    SCRIPTTHREADID   stidThread,  // identifier of thread  
    const EXCEPINFO *pexcepinfo,  // receives error information  
    DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `stidThread`  
 'ndaki Kesintiye uğratmak için iş parçacığının tanımlayıcısı veya aşağıdaki özel iş parçacığı tanımlayıcı değerlerinden biri:  
  
|Değer|Açıklama|  
|-----------|-------------|  
|SCRIPTTHREADID_ALL|Tüm iş parçacıkları. Kesme, şu anda sürmekte olan tüm betik yöntemlerine uygulanır. Çağıran betiğin bağlantısının kesileceğini istemediği takdirde, sonraki betikleştirilmiş olay, SCRIPTSTATE_DISCONNECTED veya SCRIPTSTATE_INITIALIZED bayrağıyla [IActiveScript:: SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) metodunu çağırarak betik kodunun yeniden çalışmasına neden olur. kurmak.|  
|SCRIPTTHREADID_BASE|Temel iş parçacığı; diğer bir deyişle, komut dosyası altyapısının örneklendiği iş parçacığı.|  
|SCRIPTTHREADID_CURRENT|Yürütülmekte olan iş parçacığı.|  
  
 `pexcepinfo`  
 'ndaki Durdurulan betiğe bildirilmesi gereken hata bilgilerini içeren `EXCEPINFO` yapısının adresi.  
  
 `dwFlags`  
 'ndaki Kesintiyle ilişkili seçenek bayrakları. Şu değerlerden biri olabilir:  
  
|Değer|Açıklama|  
|-----------|-------------|  
|SCRIPTINTERRUPT_DEBUG|Destekleniyorsa, komut dosyası altyapısının hata ayıklayıcıyı geçerli betik yürütme noktasına girin.|  
|SCRIPTINTERRUPT_RAISEEXCEPTION|Komut dosyası altyapısının dili tarafından destekleniyorsa betiğin özel durumu işlemesini sağlar. Aksi takdirde, betik yöntemi iptal edilir ve hata kodu çağırana döndürülür; diğer bir deyişle, olay kaynağı veya makro Invoker.|  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|Dönüş Değeri|Açıklama|  
|------------------|-------------|  
|`S_OK`|Başarılı.|  
|`E_INVALIDARG`|Bağımsız değişken geçersizdi.|  
|`E_POINTER`|Geçersiz bir işaretçi belirtildi.|  
|`E_UNEXPECTED`|Çağrı beklenmiyordu (örneğin, komut dosyası altyapısı henüz yüklenmemiş veya başlatılmamış).|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScript](../../winscript/reference/iactivescript.md)