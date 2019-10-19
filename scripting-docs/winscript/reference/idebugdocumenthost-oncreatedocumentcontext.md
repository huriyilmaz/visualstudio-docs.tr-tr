---
title: 'Idebugbelgethost:: OnCreateDocumentContext | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.OnCreateDocumentContext
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::OnCreateDocumentContext
ms.assetid: 080c8604-cfd7-484e-a337-15040870e683
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3fdfa64f66288cba47dec7c498db15238e55f954
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569115"
---
# <a name="idebugdocumenthostoncreatedocumentcontext"></a>IDebugDocumentHost::OnCreateDocumentContext
Ana bilgisayara yeni bir belge bağlamının oluşturulduğunu bildirir ve konağın isteğe bağlı olarak yeni bağlam için bilinmeyen bir denetim döndürmesini sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT OnCreateDocumentContext(  
   IUnknown**  ppunkOuter  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppunkOuter`  
 dışı Yeni bağlamı denetleyen nesne.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`E_NOTIMPL`|Konak bir denetim nesnesi sağlamıyor.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, ana bilgisayarın yardımcı tarafından sunulan belge bağlamlarına yeni işlevsellik eklemesine olanak tanır. Bu yöntem, **E_NOTIMPL** veya null bir dış nesne döndürebilir, bu durumda çağıranın bağlamı oluşturmasından sorumludur.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugDocumentHost Arabirimi](../../winscript/reference/idebugdocumenthost-interface.md)