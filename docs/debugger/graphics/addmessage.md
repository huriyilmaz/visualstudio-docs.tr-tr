---
title: AddMessage | Microsoft Docs
description: Grafik tanılama Head-Up görüntüsüne (HUD) özel bir ileti eklemek için VsgDbg sınıfının AddMessage yöntemini kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1046b7d8a71efb7d628302041a83fb9d20138a29
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232862"
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