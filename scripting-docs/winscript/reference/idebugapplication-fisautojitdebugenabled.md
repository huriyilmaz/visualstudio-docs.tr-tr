---
title: 'IDebugApplication:: Fıejıınfo Genabled | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.FIsAutoJitDebugEnabled
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::FIsAutoJitDebugEnabled
ms.assetid: 0551dd3b-e6eb-442a-8201-418f96fe62df
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9bf97a4d3985dd3dd32e582c689fde0ecd6f52e1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574984"
---
# <a name="idebugapplicationfisautojitdebugenabled"></a>IDebugApplication::FIsAutoJitDebugEnabled
Bir tam zamanında (JıT) hata ayıklayıcının, Dumb konaklarının otomatik olarak hata ayıklaması için kaydedilip kaydedilmeyeceğini belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
BOOL FIsAutoJitDebugEnabled();  
```  
  
#### <a name="parameters"></a>Parametreler  
 Bu yöntem hiçbir parametre alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa ve bir JıT hata ayıklayıcısı, Dumb konaklarının otomatik olarak ayıklanmasına kayıtlıysa, yöntem `TRUE` döndürür. Aksi takdirde, `FALSE` döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, Dumb konaklarının otomatik olarak hata ayıklaması için bir JıT hata ayıklayıcının kaydedilip kaydedilmeyeceğini belirler.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugApplication Arabirimi](../../winscript/reference/idebugapplication-interface.md)