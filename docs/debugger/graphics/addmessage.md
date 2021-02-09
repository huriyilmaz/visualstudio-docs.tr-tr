---
title: AddMessage | Microsoft Docs
description: Grafik tanılama Head-Up görüntüsüne (HUD) özel bir ileti eklemek için VsgDbg sınıfının AddMessage yöntemini kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d9d51e4415d9707b2df4bb0912290d4f5aa7825f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874645"
---
# <a name="addmessage"></a>AddMessage
Grafik tanılama *HUD* (baş ekran) için özel bir ileti ekler.

## <a name="syntax"></a>Sözdizimi

```C++
void AddMessage(
  wchar_t const * szMessage
);
```

#### <a name="parameters"></a>Parametreler
 `szMessage` HUD 'ye eklenecek ileti.

## <a name="remarks"></a>Açıklamalar
 Grafik tanılama HUD, grafik tanılama altında çalışan uygulamanın sol üst köşesinde görüntülenir. Uygulama ve grafik bilgileri yakalama hakkında çalışma zamanı bilgilerini ve bu işlev çağırarak eklenen iletileri görüntüler.

 HUD 'ye bir ileti eklemek için grafik bilgilerini etkin bir şekilde yakalamanıza gerek kalmaz; Yani, bir ileti bir sınıf örneği aracılığıyla eklenebilir `VsgDbg` , ancak [Init](init.md) üye işlevi ilk çağrılmamalıdır. Mesajlar yalnızca HUD 'de görüntülenir, bunlar grafik günlük dosyasına kaydedilmez.