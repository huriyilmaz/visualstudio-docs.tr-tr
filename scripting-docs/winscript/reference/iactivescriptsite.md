---
title: IActiveScriptSite | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSite interface
ms.assetid: 4d604a11-5365-46cf-ab71-39b3dbbe9f22
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 56b2a749eb3553044bda5816639498a0682e37e0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570094"
---
# <a name="iactivescriptsite"></a>IActiveScriptSite
Windows komut dosyası altyapısı için bir site oluşturmak üzere ana bilgisayar tarafından uygulanır. Genellikle, bu site, komut dosyasında görünür olan tüm nesnelerin kapsayıcısıyla ilişkilendirilir (örneğin, ActiveX denetimleri). Genellikle, bu kapsayıcı görüntülenen belge veya sayfaya karşılık gelir. Örneğin, Microsoft Internet Explorer, görüntülenmekte olan her HTML sayfası için böyle bir kapsayıcı oluşturur. Sayfadaki her ActiveX denetimi (veya diğer Otomasyon nesnesi) ve betik altyapısının kendisi bu kapsayıcı içinde Numaralandırılabilir.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
  
|||  
|-|-|  
|Yöntem|Açıklama|  
|[IActiveScriptSite::GetLCID](../../winscript/reference/iactivescriptsite-getlcid.md)|Konağın Kullanıcı arabirimi öğelerini görüntülemek için kullandığı yerel ayar tanımlayıcısını alır.|  
|[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)|[IActiveScript:: Addnamedidıtem](../../winscript/reference/iactivescript-addnameditem.md) yöntemine yapılan bir çağrı yoluyla altyapıya eklenen bir öğe hakkında bilgi edinir.|  
|[IActiveScriptSite::GetDocVersionString](../../winscript/reference/iactivescriptsite-getdocversionstring.md)|Geçerli belge sürümünü konağın görünüm noktasından benzersiz bir şekilde tanımlayan, ana bilgisayar tanımlı bir dize alır.|  
|[IActiveScriptSite::OnScriptTerminate](../../winscript/reference/iactivescriptsite-onscriptterminate.md)|Betik yürütmeyi tamamladığında çağırılır.|  
|[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)|Ana bilgisayara, komut dosyası altyapısının durum değiştirmediğini bildirir.|  
|[IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)|Altyapı betiği çalıştırırken bir yürütme hatası oluştuğunu konağa bildirir.|  
|[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)|Komut dosyası altyapısının betik kodunu yürütmeye başladığını ana bilgisayara bildirir.|  
|[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)|Betik altyapısının yürütülen komut dosyası kodundan döndürdüğü konağa bildirir.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Etkin Betik Arabirimleri](../../winscript/reference/active-script-interfaces.md)