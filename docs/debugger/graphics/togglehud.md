---
title: ToggleHUD | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb05bb6a424b5639e0ee98e96c80315c51081ace
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62848464"
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