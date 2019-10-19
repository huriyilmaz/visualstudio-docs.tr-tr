---
title: 'Idebugsyncoperation:: InProgressAbort | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugSyncOperation.InProgressAbort
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugSyncOperation::InProgressAbort
ms.assetid: bfd0889c-b627-4843-b1c6-b6b918f42d61
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 40974c738c071e52648297ac90a0ab89d9681435
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576664"
---
# <a name="idebugsyncoperationinprogressabort"></a>IDebugSyncOperation::InProgressAbort
Başka bir iş parçacığında sürmekte olan bir işlemi iptal eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT InProgressAbort();  
```  
  
#### <a name="parameters"></a>Parametreler  
 Bu yöntem hiçbir parametre alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`E_NOTIMPL`|İşlem iptal edilemiyor.|  
|`E_ABORT`|İşlem tamamlanamadı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Işlem hata ayıklama Yöneticisi, başka bir iş parçacığında sürmekte olan bir işlemi iptal etmek için bu yöntemi hata ayıklayıcı iş parçacığı içinden çağırır.  
  
 @No__t_0 yöntemi işlemi tamamlayamadıysanız, mümkün olan en kısa sürede `E_ABORT` döndürür. İşlem iptal edilemezse, bu yöntem `E_NOTIMPL` döndürebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugSyncOperation Arabirimi](../../winscript/reference/idebugsyncoperation-interface.md)