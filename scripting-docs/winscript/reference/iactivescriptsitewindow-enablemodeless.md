---
title: 'Iactivescriptsitewindow:: Enablemodsuz | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteWindow.EnableModeless
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteWindow_EnableModeless
ms.assetid: 83fe4f62-8e97-4f03-bc6f-d90aa888657d
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 756bda6209b6209ff14f6d67fef18faaed0b5618
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574135"
---
# <a name="iactivescriptsitewindowenablemodeless"></a>IActiveScriptSiteWindow::EnableModeless
Konağın ana penceresini etkinleştirmesine ya da devre dışı bırakmasına ve kalıcı olmayan iletişim kutularına neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT EnableModeless(  
    BOOL fEnable  // enable flag  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `fEnable`  
 'ndaki @No__t_0, ana pencereyi ve modsuz iletişimleri etkinleştirmelerini veya `FALSE` varsa bunları devre dışı bırakır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa `S_OK` döndürür veya bir hata oluştuysa `E_FAIL`.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem `IOleInPlaceFrame::EnableModeless` yöntemiyle aynıdır.  
  
 Bu yönteme yapılan çağrılar iç içe olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)