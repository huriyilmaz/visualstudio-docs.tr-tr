---
title: ToggleHUD | Microsoft Docs
description: Uygulama çalıştırıldıken grafik tanılama baş yukarı görüntüleme (HUD) görüntülendiğinden geçiş yapmak için VsgDbg'nin ToggleHUD() yöntemini kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 809b33fe3339da56507d09fcf15ec51481b751e0
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232498"
---
# <a name="togglehud"></a>ToggleHUD
Grafik tanılama *HUD'leri* (Baş Yukarı Görüntü) katmanlarını açıp kapatarak geçişler.

## <a name="syntax"></a>Syntax

```C++
void ToggleHUD();
```

## <a name="remarks"></a>Açıklamalar
 Grafik tanılama HUD'i, grafik tanılama altında çalışan uygulamanın sol üst köşesinde görüntülenir. Uygulama ve grafik bilgileri yakalama hakkında çalışma zamanı bilgilerini ve [AddMessage](addmessage.md) üye işlevi çağrılarak eklenen iletileri görüntüler.

 HUD'yi iki durumlu yapmak için grafik bilgilerini etkin bir şekilde yakalamaya gerek yok; diğer bir ifade, sınıfın bir örneği aracılığıyla geçişli olabilir `VsgDbg` ancak [önce Init](init.md) üye işlevinin çağrılmak zorunda değildir.