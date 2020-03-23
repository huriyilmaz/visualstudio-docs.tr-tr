---
title: Kodlanmış UI Testlerinde HTML5 Denetimleri Kullanma
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 13f5da784a43df5146a66ca868bb6add9a702906
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585593"
---
# <a name="using-html5-controls-in-coded-ui-tests"></a>Kodlu UI testlerinde HTML5 denetimlerini kullanma

Kodlanmış UI testleri, Internet Explorer 9 ve Internet Explorer 10'da bulunan HTML5 denetimlerinden bazılarının desteğini içerir.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Gereksinimler**

- Visual Studio Enterprise

> [!WARNING]
> Internet Explorer 10'dan önceki sürümlerde, kodlanmış UI testlerini Internet Explorer işlemine kıyasla daha yüksek bir ayrıcalık düzeyinde çalıştırmak mümkündü. Internet Explorer 10'da kodlanmış UI testlerini çalıştırırken, hem kodlanmış UI testi hem de Internet Explorer işlemi aynı ayrıcalık düzeyinde olmalıdır. Bunun nedeni, Internet Explorer 10'daki daha güvenli AppContainer özellikleridir.

> [!WARNING]
> Internet Explorer 10'da kodlanmış bir UI testi oluşturursanız, Internet Explorer 9 veya Internet Explorer 8 kullanarak çalışmayabilir. Bunun nedeni, Internet Explorer 10'un Ses, Video, ProgressBar ve Kaydırıcı gibi HTML5 denetimlerini içermesidir. Bu HTML5 denetimleri, Internet Explorer 9 veya Internet Explorer 8 tarafından tanınmaz. Benzer şekilde, Internet Explorer 9 kullanarak kodlanmış UI testleri, Internet Explorer 8 tarafından tanınmayacak bazı HTML5 denetimleri de içerebilir.

## <a name="audio-control"></a>Ses Kontrolü

**Ses kontrolü:** HTML5 Ses denetimindeki eylemler doğru bir şekilde kaydedilir ve oynatılır.

![HTML5 Ses kontrolü](../test/media/codedui_html5_audio.png)

|Eylem|Kayıt|Oluşturulan Kod|
|-|---------------|-|
|**Ses çalma**<br /><br /> Doğrudan denetimden veya denetimin sağ tıklama menüsünden.|00:00:00 dan Ses> çal \<|HtmlAudio.Play(Zaman Aralığı)|
|**Seste belirli bir zamanı arama**|00:01:48 için Ses> isim ara \<|HtmlAudio.Seek(Zaman Aralığı)|
|**Sesi duraklatma**<br /><br /> Doğrudan denetimden veya denetimin sağ tıklama menüsünden.|Duraklatma \<adı> Ses 00:01:53|HtmlAudio.Pause(Zaman Aralığı)|
|**Sesi sessize al**<br /><br /> Doğrudan denetimden veya denetimin sağ tıklama menüsünden.|\<Sesi> sessiz adı|HtmlAudio.Sessiz()|
|**Sesi sessize al**<br /><br /> Doğrudan denetimden veya denetimin sağ tıklama menüsünden.|Ses> \<unmute adı|HtmlAudio.Unmute()|
|**Ses düzeyini değiştirme**|\<Ses> ses adını %79'a ayarlama|HtmlAudio.SetVolume(float)|

Bir iddia ekleyebileceğiniz özelliklerin listesi için [HTMLAudioElement'e](https://developer.mozilla.org/docs/Web/API/HTMLAudioElement) bakın.

**Arama özellikleri:** Arama `HtmlAudio` özellikleri , `Id` `Name` ve `Title`.

**Filtre özellikleri:** Için filtre `HtmlAudio` özellikleri `Src` `Class`, `ControlDefinition` `TagInstance`, ve .

> [!NOTE]
> Arama ve Duraklatma için süre önemli olabilir. Oynatma sırasında, kodlanmış UI testi sesi `(TimeSpan)` duraklatmadan önce belirtilen süreye kadar bekler. Bazı özel durumlara göre, Duraklat komutuna çarpmadan önce belirtilen süre geçmişse, bir özel durum atılır.

## <a name="video-control"></a>Video Kontrolü
**Video kontrolü:** HTML5 Video denetimindeki eylemler doğru bir şekilde kaydedilir ve oynatılır.

![HTML5 Video kontrolü](../test/media/codedui_html5_video.png)

|Eylem|Kayıt|Oluşturulan Kod|
|-|---------------|-|
|**Videoyu oynat**<br /><br /> Doğrudan denetimden veya denetimin sağ tıklama menüsünden.|00:00:00 dan video> oynatma \<|HtmlVideo.Play(Zaman Aralığı)|
|**Videoda belirli bir zaman alanın**|00:01:48 için> Video adı ara \<|HtmlVideo.Seek(Zaman Aralığı)|
|**Videoyu duraklatma**<br /><br /> Doğrudan denetimden veya denetimin sağ tıklama menüsünden.|Duraklatma \<adı> Video at 00:01:53|HtmlVideo.Pause(Zaman Aralığı)|
|**Videoyu sessize al**<br /><br /> Doğrudan denetimden veya denetimin sağ tıklama menüsünden.|Adı \<> Video'da sessize al|HtmlVideo.Sessiz()|
|**Sessiz video**<br /><br /> Doğrudan denetimden veya denetimin sağ tıklama menüsünden.|\<Adı> Video|HtmlVideo.Unmute()|
|**Videonun ses düzeyini değiştirme**|Video> \<ad hacmini %79'a ayarlayın||

Bir iddia ekleyebileceğiniz özelliklerin listesi için [HTMLVideoElement'e](https://developer.mozilla.org/docs/Web/HTML/Element/video) bakın.

**Arama özellikleri:** Arama `HtmlVideo` özellikleri , `Id` `Name` ve `Title`.

**Filtre özellikleri:** Filtre özellikleri `HtmlVideo` `Src`, `Poster`, `Class` `ControlDefinition` , `TagInstance`ve .

> [!NOTE]
> -30'lu veya +30'lu etiketleri kullanarak videoyu geri sarar veya ileri sararsanız, bu işlem uygun zamanı aramak için toplanır.

## <a name="progressbar"></a>ProgressBar
**ProgressBar denetimi:** ProgressBar etkileşime giremeyen bir denetimdir. Bu denetimin `Value` özellikleri ve `Max` özellikleri hakkında iddialar ekleyebilirsiniz. Daha fazla bilgi için [HTMLProgressElement'e](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/progress)bakın.

![HTML5 ProgressBar denetimi](../test/media/codedui_html5_progressbar.png)

## <a name="see-also"></a>Ayrıca bkz.

- [HTML öğeleri](https://developer.mozilla.org/docs/Web/HTML/Element)
- [Kodunuzu test etmek için UI otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri ve eylem kayıtları için desteklenen yapılandırmalar ve platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
