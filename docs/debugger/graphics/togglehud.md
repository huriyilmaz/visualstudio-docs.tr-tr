---
title: ToggleHUD | Microsoft Docs
description: Uygulama çalıştığında grafik tanılama baş ekran (HUD) görüntülenip görüntülenmeyeceğini değiştirmek için VsgDbg öğesinin ToggleHUD () yöntemini kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 15c232c89bf7f0a502bd98127498bc8047d01fda
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122044034"
---
# <a name="togglehud"></a>ToggleHUD
Grafik tanılama *HUD* (baş ekran görüntüsü) kaplamayı açık veya kapalı olarak değiştirir.

## <a name="syntax"></a>Syntax

```C++
void ToggleHUD();
```

## <a name="remarks"></a>Açıklamalar
 Grafik tanılama HUD, grafik tanılama altında çalışan uygulamanın sol üst köşesinde görüntülenir. Uygulama ve grafik bilgileri yakalama hakkında çalışma zamanı bilgilerini ve [AddMessage](addmessage.md) üye işlevi çağırarak eklenen iletileri görüntüler.

 HUD 'yi değiştirmek için grafik bilgilerini etkin bir şekilde yakalamanıza gerek kalmaz; Yani, sınıfın bir örneği aracılığıyla değiştirilebilir `VsgDbg` , ancak [Init](init.md) üye işlevinin ilk çağrılması gerekmez.