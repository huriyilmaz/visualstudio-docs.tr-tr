---
title: 'IDebugApplication:: StartDebugSession | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.StartDebugSession
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::StartDebugSession
ms.assetid: 737f8424-bbcf-473f-9cf1-6601b9aa250d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a7fd27ec86485d39ee9f13997c1a2db7175afcde
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570989"
---
# <a name="idebugapplicationstartdebugsession"></a>IDebugApplication::StartDebugSession
Varsayılan hata ayıklayıcı tümleşik geliştirme ortamı 'nı (IDE) başlatır ve henüz ekli değilse bu uygulamaya bir hata ayıklama oturumu ekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT StartDebugSession();  
```  
  
#### <a name="parameters"></a>Parametreler  
 Bu yöntem hiçbir parametre alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, tam zamanında hata ayıklamayı uygulamak için kullanılır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugApplication Arabirimi](../../winscript/reference/idebugapplication-interface.md)