---
title: Iactivescriptsitewindow | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteWindow interface
ms.assetid: 96d5c493-2c0b-47e2-848b-4a8dacdcd65c
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ee680a3d00c6736549b03ce8fee5593a7a8c5af
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575905"
---
# <a name="iactivescriptsitewindow"></a>IActiveScriptSiteWindow
Bu arabirim, [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) ile aynı nesne üzerinde bir kullanıcı arabirimini destekleyen konaklar tarafından uygulanır. Sunucular gibi bir kullanıcı arabirimini desteklemeyen konaklar `IActiveScriptSiteWindow` arabirimini uygulamaz. Betik altyapısı, `IActiveScriptSite` `QueryInterface` çağırarak bu arabirime erişir.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IActiveScriptSiteWindow::GetWindow](../../winscript/reference/iactivescriptsitewindow-getwindow.md)|Komut dosyası altyapısının görüntülemesi gereken bir açılır pencerenin sahibi görevi gören pencere tanıtıcısını alır.|  
|[IActiveScriptSiteWindow::EnableModeless](../../winscript/reference/iactivescriptsitewindow-enablemodeless.md)|Konağın ana penceresini etkinleştirmesine ya da devre dışı bırakmasına ve kalıcı olmayan iletişim kutularına neden olur.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Etkin Betik Arabirimleri](../../winscript/reference/active-script-interfaces.md)