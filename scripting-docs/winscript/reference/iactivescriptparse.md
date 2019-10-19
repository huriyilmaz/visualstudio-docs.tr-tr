---
title: IActiveScriptParse | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptParse interface
ms.assetid: 8c967d70-f582-4f64-9e79-49f40c4dcb7c
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 81f64352c15dce233058d49b70e35da7e2238688
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561645"
---
# <a name="iactivescriptparse"></a>IActiveScriptParse
Windows komut dosyası altyapısı betiğe ham metin kodu betiküne izin veriyorsa veya çalışma zamanında ifade metninin değerlendirilmesini sağlar, `IActiveScriptParse` arabirimini uygular. VBScript gibi bağımsız yazma ortamına sahip olmayan yorumlanan betik dilleri için bu, betik oluşturma altyapısına betik kodu almak ve çeşitli nesne olaylarına betik parçaları eklemek için alternatif bir mekanizma (`IPersist*` dışında) sağlar .  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IActiveScriptParse::InitNew](../../winscript/reference/iactivescriptparse-initnew.md)|Komut dosyası altyapısını başlatır.|  
|[IActiveScriptParse::AddScriptlet](../../winscript/reference/iactivescriptparse-addscriptlet.md)|Betiğe bir kod oluşturma yöntemi kodu ekler.|  
|[IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)|Verilen kod kod oluşturma yöntemi ayrıştırır, ad alanına bildirim ekliyor ve kodu uygun şekilde değerlendiriyor.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Etkin Betik Arabirimleri](../../winscript/reference/active-script-interfaces.md)