---
title: IActiveScript | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScript interface
ms.assetid: d8acee11-7f0d-4999-b97a-66774af16f71
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7a33db2bcbcb356a508fec2e6bc5449a899a1299
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577243"
---
# <a name="iactivescript"></a>IActiveScript
Komut dosyası altyapısını başlatmak için gereken yöntemleri sağlar. Betik altyapısının `IActiveScript` arabirimini uygulaması gerekir.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)|Konak tarafından sunulan [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) sitesinin betik motoruna bilgilendirir.|  
|[IActiveScript::GetScriptSite](../../winscript/reference/iactivescript-getscriptsite.md)|Windows komut dosyası altyapısı ile ilişkili site nesnesini alır.|  
|[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)|Komut dosyası altyapısını belirtilen duruma koyar.|  
|[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)|Komut dosyası altyapısının geçerli durumunu alır.|  
|[IActiveScript::Close](../../winscript/reference/iactivescript-close.md)|Komut dosyası altyapısının Şu anda yüklü olan herhangi bir betiği iptal etmesine, durumunu kaybetmesine ve diğer nesnelere sahip olduğu tüm arabirim işaretçilerini, bu nedenle kapalı bir durum girerek serbest bırakılmasına neden olur.|  
|[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)|Kök düzeyindeki bir öğenin adını komut dosyası altyapısının ad alanına ekler.|  
|[IActiveScript::AddTypeLib](../../winscript/reference/iactivescript-addtypelib.md)|Betik için ad alanına bir tür kitaplığı ekler.|  
|[IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)|Çalışan betik için `IDispatch` arabirimini alır.|  
|[IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)|Şu anda yürütülmekte olan iş parçacığı için bir komut dosyası motoru tanımlı tanımlayıcı alır.|  
|[IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)|Verilen Microsoft Win32 iş parçacığıyla ilişkili iş parçacığı için bir komut dosyası motoru tanımlı tanımlayıcı alır.|  
|[IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)|Bir betik iş parçacığının geçerli durumunu alır.|  
|[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)|Çalışan bir betik iş parçacığının yürütülmesini keser.|  
|[IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)|Geçerli komut dosyası altyapısını (yani geçerli yürütme durumu) klonlar, geçerli iş parçacığında hiç sitesi olmayan yüklü bir betik altyapısı döndürüyor.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Windows Betik Arabirimleri Başvurusu](../../winscript/reference/windows-script-interfaces-reference.md)