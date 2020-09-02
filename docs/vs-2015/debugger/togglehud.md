---
title: ToggleHUD | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 87c2571926b92e59ae03e5e988bbf535474dc6d0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144573"
---
# <a name="togglehud"></a>ToggleHUD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Grafik tanılama *HUD* (baş ekran görüntüsü) kaplamayı açık veya kapalı olarak değiştirir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Grafik tanılama HUD, grafik tanılama altında çalışan uygulamanın sol üst köşesinde görüntülenir. Uygulama ve grafik bilgileri yakalama hakkında çalışma zamanı bilgilerini ve [AddMessage](../debugger/addmessage.md) üye işlevi çağırarak eklenen iletileri görüntüler.  
  
 HUD 'yi değiştirmek için grafik bilgilerini etkin bir şekilde yakalamanıza gerek kalmaz; Yani, sınıfın bir örneği aracılığıyla değiştirilebilir `VsgDbg` , ancak [Init](../debugger/init.md) üye işlevinin ilk çağrılması gerekmez.
