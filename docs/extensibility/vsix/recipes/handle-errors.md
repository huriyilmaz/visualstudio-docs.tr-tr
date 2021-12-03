---
title: Hata işleme
description: Uzantılarda oluşan hataların ve özel durumların nasıl en iyi şekilde işlenip düzeltilenemleri açıklar
ms.date: 12/01/2021
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: pchapman
ms.prod: visual-studio-windows
ms.technology: vs-ide-sdk
ms.custom: cookbook
ms.openlocfilehash: 25e6701f0b8702b976181020b1e5a3f6544a9ca7
ms.sourcegitcommit: a149b3a034bb555ad217656c0ec8bc1672b1e215
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "133516732"
---
# <a name="error-handling-in-visual-studio-extensions"></a>Uzantılarda Visual Studio işleme

Özel durumlar büyük olasılıkla uzantılar dahil olmak üzere herhangi Visual Studio oluşur. Bunları, kullanıcı deneyimlerini ortaya çıkarken en iyi duruma getirmek için doğru şekilde işleyecez.

Özel durum olmaması gereken bir anomali ise, özel durumun ayrıntılarını düzeltecek şekilde günlüğe almak gerekir. Sorunun önem derecesine bağlı olarak, kullanıcıya bu konuda bilgi vermeni de istiyor olabilir.

## <a name="include-the-symbols"></a>Sembolleri dahil etmek
Özel durum hakkında en doğru bilgilere sahip olduğundan emin olmak için uzantıya .pdb dosyasını dahil edin. Bu varsayılan olarak etkindir, ancak projenizin özelliklerini (F4) göstererek bunu kontrol edin.

:::image type="content" source="../media/include-pdb.png" alt-text="PDB dosyasını VSIX kapsayıcısı içinde dahil edin.":::

VSIX Kapsayıcısı'nın **Hata Ayıklama Sembollerini Dahil Edin özelliğini** True olarak ayarlayın. 

Bu, ihtiyacınız olan bilgileri toplamak için ayarlar. Şimdi bunu yapmak için bazı stratejilere bakalım.

## <a name="automated-telemetry"></a>Otomatik telemetri
Uzantınız aracılığıyla herhangi bir .NET uygulamasında kullanabileceğiniz herhangi bir telemetri mekanizmasını kullanabilirsiniz. Application [Analizler,](/powerapps/maker/canvas-apps/application-insights) [Raygun,](https://raygun.com/)Google [Analytics vb. popüler](https://analytics.google.com/) seçeneklerdir.

Özel durum ayrıntılarını API'lerini kullanarak bu telemetri sistemleri aracılığıyla el ile bildirmeniz gerekir. Bu seçenek, kullanıcı makinelerde oluşan tüm sorunları takip etmek ve sorunları önceden düzeltmek için harika bir yol sağlar.

Bazı kullanıcılar telemetri raporlamayı tercih etmeyebilirsiniz. Bu seçeneği kullanırken gizlilik bildiriminde bundan bahsetmeyi tercih edin.

## <a name="log-to-output-window"></a>Çıkış Penceresi'de oturum açma
Özel durumları işlemek için bloklar kullanırken, kullanıcıya neyin yanlış gittiğini `try/catch` haber vermenin avantajı olabilir. Böylece sorunu kolayca düzeltecek şekilde size bildirebilirler.

En iyi yöntemlerden biri, özel durum ayrıntılarının çıkışını Çıkış Penceresi. Bu şekilde, kullanıcı bir özel durumun meydana geldiğine bakarak size bir hata raporu göndermesi için stacktrace sağlar.

Community Toolkit bunu çok kolaylaştırır. Zaman uyumlu bağlamlarda, herhangi bir üzerinde `Log()` genişletme yöntemini `Exception` kullanın.

```csharp
try
{
    // Do work;
}
catch (Exception ex)
{
    ex.Log();
}
```

Zaman uyumsuz bağlamlar için aynı şey uzantı yöntemi beklenerek `LogAsync()` yapılır.

```csharp
try
{
    // Do work;
}
catch (Exception ex)
{
    await ex.LogAsync();
}
```

## <a name="notify-the-user"></a>Kullanıcıya bildirme
Özel durum kullanıcı için düşük önem derecesine sahipse, bunları kesintiye uğratmak için bir neden yoktur. Bir hatanın olduğunu göstermek için durum çubuğunu kullanmayı göz önünde bulundurabilirsiniz.

Özel durum ciddi bir durumsa ve kullanıcı akışının kesintiye uğramasına neden oluyorsa, kullanıcıya hata hakkında bilgi vermeleri için bir ileti kutusu kullanmayı göz önünde bulundurabilirsiniz. Özel durumu telemetri verileri ve/veya daha önce açıklandığı gibi Çıkış Penceresi günlüğe Çıkış Penceresi emin olun.

Durum çubuğunu ve ileti kutularını kullanma hakkında daha fazla bilgi edinmek için Bildirimler [tarifine bakın.](notifications.md)
