---
title: 'Iactivescriptsitewindow:: GetWindow | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteWindow.GetWindow
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteWindow_GetWindow
ms.assetid: 6284e38c-9dfb-4d69-903d-f243f78c0331
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d8263db447c7692ec7b0982127d63b4bea588a4b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574351"
---
# <a name="iactivescriptsitewindowgetwindow"></a>IActiveScriptSiteWindow::GetWindow
Komut dosyası altyapısının görüntülemesi gereken bir açılır pencerenin sahibi görevi gören bir pencereye tutamacı alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetWindow(  
    HWND *phwnd  // address of variable for window handle  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `phwnd`  
 dışı Pencere tanıtıcısını alan bir değişkenin adresi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa `S_OK` döndürür veya bir hata oluştuysa `E_FAIL`.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem `IOleWindow::GetWindow` metoduna benzerdir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)