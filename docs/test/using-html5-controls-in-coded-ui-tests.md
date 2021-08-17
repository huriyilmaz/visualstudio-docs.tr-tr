---
title: Kodlanmış UI Testlerinde HTML5 Denetimleri Kullanma
description: Internet Explorer 9 ve daha fazla koda dahil edilen HTML5 denetimleri için kodlanmış UI testleri Internet Explorer 10.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: dbe1588789dbf7f8384a658a600864ae6cbb8c10b59fd0c93d8b07225e000d80
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121395016"
---
# <a name="using-html5-controls-in-coded-ui-tests"></a>Kodlanmış UI testlerinde HTML5 denetimlerini kullanma

Kodlanmış UI testleri, Internet Explorer 9 ve daha yeni bir Internet Explorer 10.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Gereksinimler**

- Visual Studio Enterprise

> [!WARNING]
> Önceki sürümlerde Internet Explorer 10, kodlanmış UI testlerini, önceki işlemle karşılaştırıldığında daha yüksek bir ayrıcalık düzeyinde Internet Explorer mümkündu. Kodlanmış UI testlerini Internet Explorer 10, hem kodlanmış UI testi Internet Explorer işlem aynı ayrıcalık düzeyinde olması gerekir. Bunun nedeni, Internet Explorer 10'daki daha güvenli AppContainer özellikleridir.

> [!WARNING]
> Internet Explorer 10'da kodlanmış ui testi Internet Explorer 9 veya Internet Explorer 8 kullanılarak çalıştırılamayabilirsiniz. Bunun nedeni, Internet Explorer 10, Video, ProgressBar ve Kaydırıcı gibi HTML5 denetimlerinin de dahil olduğu bir durum. Bu HTML5 denetimleri, Internet Explorer 9 veya Internet Explorer 8 tarafından tanınmaz. Benzer şekilde, Internet Explorer 9 kullanarak kodlanmış UI testleri, Internet Explorer 8 tarafından tanınmayacak bazı HTML5 denetimleri de içerebilir.

## <a name="audio-control"></a>Ses Denetimi

**Ses denetimi:** HTML5 Ses denetimine yapılan eylemler doğru şekilde kaydedilir ve tekrar çalınmış olur.

![HTML5 Ses denetimi](../test/media/codedui_html5_audio.png)

|Eylem|Kayıt|Oluşturulan Kod|
|-|---------------|-|
|**Ses çalma**<br /><br /> Doğrudan denetimden veya denetimin sağ tıklama menüsünden.|\<name>00:00:00'dan Ses Çalma|HtmlAudio.Play(TimeSpan)|
|**Seste belirli bir zaman arama**|Seek \<name> Audio to 00:01:48|HtmlAudio.Seek(TimeSpan)|
|**Sesi duraklatma**<br /><br /> Doğrudan denetimden veya denetimin sağ tıklama menüsünden.|\<name>00:01:53'te Sesi Duraklatma|HtmlAudio.Pause(TimeSpan)|
|**Sesi kapatma**<br /><br /> Doğrudan denetimden veya denetimin sağ tıklama menüsünden.|Sessiz \<name> Ses|HtmlAudio.Sessiz()|
|**Sesi aç**<br /><br /> Doğrudan denetimden veya denetimin sağ tıklama menüsünden.|Ses seslerini \<name> aç|HtmlAudio.Unmute()|
|**Ses hacmini değiştirme**|Ses hacmini \<name> %79 olarak ayarlayın|HtmlAudio.SetVolume(float)|

Onay ekliyebilirsiniz özellikler listesi için bkz. [HTMLAudioElement.](https://developer.mozilla.org/docs/Web/API/HTMLAudioElement)

**Arama özellikleri:** için arama özellikleri `HtmlAudio` `Id` , ve `Name` 'tir. `Title`

**Filtre özellikleri:** için filtre özellikleri `HtmlAudio` `Src` , ve `Class` `ControlDefinition` 'tir. `TagInstance`

> [!NOTE]
> Seek ve Pause için süre önemli olabilir. Kayıttan yürütme sırasında, kodlanmış UI testi sesi duraklatmadan önce `(TimeSpan)` belirtilen süreye kadar bekler. Özel bir durumla, Belirtilen süre Duraklat komutuna isabetmeden önce geçti ise, bir özel durum oluşturur.

## <a name="video-control"></a>Video Denetimi
**Video denetimi:** HTML5 Video denetimine yapılan eylemler doğru şekilde kaydedilir ve tekrar oynattır.

![HTML5 Video denetimi](../test/media/codedui_html5_video.png)

|Eylem|Kayıt|Oluşturulan Kod|
|-|---------------|-|
|**Video oynatma**<br /><br /> Doğrudan denetimden veya denetimin sağ tıklama menüsünden.|Video \<name> Oynatma: 00:00:00|HtmlVideo.Play(TimeSpan)|
|**Videoda belirli bir zaman arama**|Videoyu \<name> Ara: 00:01:48|HtmlVideo.Seek(TimeSpan)|
|**Videoyu duraklatma**<br /><br /> Doğrudan denetimden veya denetimin sağ tıklama menüsünden.|Videoyu \<name> 00:01:53'te Duraklatma|HtmlVideo.Pause(TimeSpan)|
|**Videoyu sessize alma**<br /><br /> Doğrudan denetimden veya denetimin sağ tıklama menüsünden.|Sessiz \<name> Video|HtmlVideo.Dilsiz()|
|**Videonun seslerini aç**<br /><br /> Doğrudan denetimden veya denetimin sağ tıklama menüsünden.|Videonun Seslerini \<name> Aç|HtmlVideo.Unmute()|
|**Video hacmini değiştirme**|Video hacmini \<name> %79 olarak ayarlayın||

Onay ekliyebilirsiniz özellikler listesi için bkz. [HTMLVideoElement.](https://developer.mozilla.org/docs/Web/HTML/Element/video)

**Arama özellikleri:** için arama özellikleri `HtmlVideo` `Id` , ve `Name` 'tir. `Title`

**Filtre özellikleri:** için filtre özellikleri `HtmlVideo` `Src` , , ve `Poster` `Class` `ControlDefinition` 'tir. `TagInstance`

> [!NOTE]
> Videoyu -30 veya +30s etiketlerini kullanarak geri sarmalar veya ileri sarmalarsanız, uygun zamanı aramak için bu toplanır.

## <a name="progressbar"></a>ProgressBar
**ProgressBar denetimi:** ProgressBar, etkileşim kuramaz bir denetimdir. Bu denetimin ve `Value` özelliklerine `Max` onaylar abilirsiniz. Daha fazla bilgi için bkz. [HTMLProgressElement](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/progress).

![HTML5 ProgressBar denetimi](../test/media/codedui_html5_progressbar.png)

## <a name="see-also"></a>Ayrıca bkz.

- [HTML öğeleri](https://developer.mozilla.org/docs/Web/HTML/Element)
- [Kodunuzu test etmek için UI otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri ve eylem kayıtları için desteklenen yapılandırmalar ve platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
