---
title: 'Iactivescriptprofilercallback:: Initialize | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.Initialize
apilocation:
- scrobj.dll
ms.assetid: a257111e-a50b-4962-9dd6-c893d40f6985
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bbbd61d6b3c10dcfffe2df215cc5a60d685dd803
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576450"
---
# <a name="iactivescriptprofilercallbackinitialize"></a>IActiveScriptProfilerCallback::Initialize
Bir betik altyapısında profil oluşturma her başlatıldığında profil oluşturucu nesnesini başlatmak için çağırılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT Initialize(  
    [in] DWORD dwContext);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwContext`  
 'ndaki [Iactivescriptprofilercontrol:: Startprofil oluşturma](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)öğesine geçirilen 4 baytlık bir değer.  
  
## <a name="return-value"></a>Dönüş Değeri  
 HRESULT döndürür. Olası değerler aşağıdaki gibidir:  
  
|Dönüş Değeri|Açıklama|  
|------------------|-------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yöntem profil oluşturucu nesnesini başlatamıyor, komut dosyası altyapısını bilgilendirmek için HRESULT hatası döndürmelidir. Bu durumda, komut dosyası altyapısı doğrudan [ıactivescriptprofilercallback:: kapatılmasını](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)çağırmalıdır, bu parametre içinde HRESULT ' i geçirerek, sonra profil oluşturucu nesnesini serbest bırakmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScriptProfilerCallback Arabirimi](../../winscript/reference/iactivescriptprofilercallback-interface.md)