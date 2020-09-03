---
title: AddMessage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f01d4e80c3740ae27b5df8badbc74989c2da2c60
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156519"
---
# <a name="addmessage"></a>AddMessage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Grafik tanılama *HUD* (baş ekran) için özel bir ileti ekler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
void AddMessage(  
  wchar_t const * szMessage  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `szMessage`  
 HUD 'ye eklenecek ileti.  
  
## <a name="remarks"></a>Açıklamalar  
 Grafik tanılama HUD, grafik tanılama altında çalışan uygulamanın sol üst köşesinde görüntülenir. Uygulama ve grafik bilgileri yakalama hakkında çalışma zamanı bilgilerini ve bu işlev çağırarak eklenen iletileri görüntüler.  
  
 HUD 'ye bir ileti eklemek için grafik bilgilerini etkin bir şekilde yakalamanıza gerek kalmaz; Yani, bir ileti bir sınıf örneği aracılığıyla eklenebilir `VsgDbg` , ancak [Init](../debugger/init.md) üye işlevi ilk çağrılmamalıdır. Mesajlar yalnızca HUD 'de görüntülenir, bunlar grafik günlük dosyasına kaydedilmez.
