---
title: IActiveScriptParse32 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c39c14aa-beb7-4eca-8b8c-2181da1c2e3e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 568feacfe75de22a330c892a44fa4f4f6fd0e3b8
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835322"
---
# <a name="iactivescriptparse32"></a>IActiveScriptParse32
Windows komut dosyası altyapısı, ham metin kodu betikkoduna betikte eklenmesine izin veriyorsa veya çalışma zamanında ifade metninin değerlendirilmesini sağlar, `IActiveScriptParse32` arabirimi uygular. VBScript gibi bağımsız yazma ortamına sahip olmayan yorumlanan betik dilleri için bu, betik `IPersist*` oluşturma altyapısına betik kodu almak ve çeşitli nesne olaylarına betik parçaları eklemek için alternatif bir mekanizma (dışında) sağlar.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
  
|Yöntem|Description|  
|------------|-----------------|  
|[IActiveScriptParse32::AddScriptlet](../../winscript/reference/iactivescriptparse32-addscriptlet.md)|Betiğe bir kod oluşturma yöntemi kodu ekler.|  
|[IActiveScriptParse32::InitNew](../../winscript/reference/iactivescriptparse32-initnew.md)|Komut dosyası altyapısını başlatır.|  
|[IActiveScriptParse32::ParseScriptText](../../winscript/reference/iactivescriptparse32-parsescripttext.md)|Verilen kod kod oluşturma yöntemi ayrıştırır, ad alanına bildirim ekliyor ve kodu uygun şekilde değerlendiriyor.|