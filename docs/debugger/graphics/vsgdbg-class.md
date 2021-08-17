---
description: Grafik tanılamanın uygulama içinde bileşeninin programlı denetimi için bir arabirimi temsil eder.
title: VsgDbg Sınıf | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c663fda50dd6abb97dc5eb9f617e2a7ad46fc72ad5eaf59617483f03908f8858
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121419122"
---
# <a name="vsgdbg-class"></a>VsgDbg Sınıfı
Grafik tanılamanın uygulama içinde bileşeninin programlı denetimi için bir arabirimi temsil eder.

## <a name="syntax"></a>Syntax

```C++
class VsgDbg;
```

## <a name="members"></a>Üyeler
 sınıfı `VsgDbg` aşağıdaki üyeleri destekler.

### <a name="public-constructors"></a>Ortak Oluşturucular

|Ad|Açıklama|
|----------|-----------------|
|[VsgDbg::VsgDbg (Oluşturucu)](vsgdbg-vsgdbg-constructor.md)|sınıfının bir örneğini oluşturun ve isteğe bağlı olarak grafik bilgilerini etkin bir şekilde yakalamak ve kaydetmek için grafik tanılamanın `VsgDbg` uygulama içinde bileşenini hazırlar.|
|[VsgDbg::~VsgDbg (Yok Edici)](vsgdbg-tilde-vsgdbg-destructor.md)|Sınıfının bir örneğini yok `VsgDbg` eder.|

### <a name="public-methods"></a>Ortak Yöntemler

|Ad|Açıklama|
|----------|-----------------|
|[AddMessage](addmessage.md)|Grafik tanılama HUD'si (Baş Yukarı Görüntü) için özel bir ileti ekler.|
|[BeginCapture](begincapture.md)|ile sona erecek bir yakalama aralığı `EndCapture` başlar.|
|[CaptureCurrentFrame](capturecurrentframe.md)|Geçerli çerçevenin geri kalanını grafik günlük dosyasına yakalar.|
|[Kopyalama (Programlı Yakalama)](copy-programmatic-capture.md)|Etkin grafik günlüğü (.vsglog) dosyasının içeriğini yeni bir dosyaya kopyalar.|
|[EndCapture](endcapture.md)|ile başlayan yakalama aralığını sona `BeginCapture` erer.|
|[ınit](init.md)|Grafik bilgilerini etkin bir şekilde yakalamak ve kaydetmek için grafik tanılamanın uygulama içinde bileşenini hazırlar.|
|[ToggleHUD](togglehud.md)|Grafik tanılama HUD katmanlarını açıp kapatarak geçişler.|
|[UnInit](uninit.md)|Grafik günlüğü dosyasını son olarak hazırlar, kapatır ve uygulama grafik bilgilerini etkin bir şekilde kaydederken kullanılan kaynakları serbest bıraktırır.|

## <a name="remarks"></a>Açıklamalar
 sınıfı, `VsgDbg` grafik tanılama özelliklerini program aracılığıyla kontrol etmek için kullanabileceğiniz bir arabirimi temsil eder. Grafik bilgilerini etkin bir şekilde yakalamama ve kaydetmeden bile bazı özellikleri kullanabilirsiniz; Buna üye `AddMessage` işlevi ve üye işlevi `ToggleHUD` dahildir. Diğer üye işlevleri, grafik bilgilerini etkin bir şekilde yakalamayı başlatmak veya durdurmak için grafik tanılamalarının uygulama içinde bileşenini hazırlar veya uygulama grafik bilgilerini etkin bir şekilde yakalayıp grafik günlük dosyasına kaydederken çağrılmaları gerekir.
