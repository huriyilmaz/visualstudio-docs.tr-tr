---
title: ToggleHUD | Microsoft Docs
description: Uygulama çalıştığında grafik tanılama baş ekran (HUD) görüntülenip görüntülenmeyeceğini değiştirmek için VsgDbg öğesinin ToggleHUD () yöntemini kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 60bee5a89be0fc1503595a36cfc48a692711d40a
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996077"
---
# <a name="togglehud"></a>ToggleHUD
Grafik tanılama *HUD* (baş ekran görüntüsü) kaplamayı açık veya kapalı olarak değiştirir.

## <a name="syntax"></a>Sözdizimi

```C++
void ToggleHUD();
```

## <a name="remarks"></a>Açıklamalar
 Grafik tanılama HUD, grafik tanılama altında çalışan uygulamanın sol üst köşesinde görüntülenir. Uygulama ve grafik bilgileri yakalama hakkında çalışma zamanı bilgilerini ve [AddMessage](addmessage.md) üye işlevi çağırarak eklenen iletileri görüntüler.

 HUD 'yi değiştirmek için grafik bilgilerini etkin bir şekilde yakalamanıza gerek kalmaz; Yani, sınıfın bir örneği aracılığıyla değiştirilebilir `VsgDbg` , ancak [Init](init.md) üye işlevinin ilk çağrılması gerekmez.