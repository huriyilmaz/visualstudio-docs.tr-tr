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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75585593"
---
# <a name="using-html5-controls-in-coded-ui-tests"></a>Kodlanmış UI testlerinde HTML5 denetimleri kullanma

Kodlanmış UI testleri, Internet Explorer 9 ve Internet Explorer 10 ' da bulunan HTML5 denetimlerinin bazılarına yönelik destek içerir.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Requirements**

- Visual Studio Enterprise

> [!WARNING]
> Internet Explorer 10 ' dan önceki sürümlerde, kodlanmış UI testlerini Internet Explorer süreciyle karşılaştırıldığında daha yüksek bir ayrıcalık düzeyinde çalıştırmak mümkün oldu. Internet Explorer 10 ' da kodlanmış UI testleri çalıştırılırken, hem kodlanmış UI testi hem de Internet Explorer işlemi aynı ayrıcalık düzeyinde olmalıdır. Bunun nedeni, Internet Explorer 10 ' da daha güvenli AppContainer özellikleri.

> [!WARNING]
> Internet Explorer 10 ' da kodlanmış UI testi oluşturursanız, Internet Explorer 9 veya Internet Explorer 8 kullanılarak çalışmayabilir. Bunun nedeni, Internet Explorer 10 ' un ses, video, ProgressBar ve kaydırıcı gibi HTML5 denetimlerini içermektir. Bu HTML5 denetimleri, Internet Explorer 9 veya Internet Explorer 8 tarafından tanınmaz. Benzer şekilde, Internet Explorer 9 kullanarak kodlanmış UI testleri, Internet Explorer 8 tarafından tanınmayacak bazı HTML5 denetimleri de içerebilir.

## <a name="audio-control"></a>Ses denetimi

**Ses denetimi:** HTML5 ses denetimindeki eylemler doğru şekilde kaydedilir ve kayıttan yürütülür.

![HTML5 ses denetimi](../test/media/codedui_html5_audio.png)

|Eylem|Kayıt|Oluşturulan kod|
|-|---------------|-|
|**Ses çal**<br /><br /> Doğrudan denetimden veya denetimin sağ tıklama menüsünden.|00:00:00 'den Ses > \<adı oynat|Htmdefdio. Play (TimeSpan)|
|**Ses içinde belirli bir zamana arama**|\<> Ses ara 00:01:48|Htmdefdio. Seek (TimeSpan)|
|**Sesi Duraklat**<br /><br /> Doğrudan denetimden veya denetimin sağ tıklama menüsünden.|\<adı > sesi 00:01:53 adresinden Duraklat|Htmdefdio. Pause (TimeSpan)|
|**Sesi sustur**<br /><br /> Doğrudan denetimden veya denetimin sağ tıklama menüsünden.|Sessiz \<adı > Ses|Htmdefdio. Mute ()|
|**Sesi aç**<br /><br /> Doğrudan denetimden veya denetimin sağ tıklama menüsünden.|\<adı > sesi aç|Htmdefdio. aç ()|
|**Ses düzeyini Değiştir**|Ses \<adı > sesini %79 olarak ayarla|Htmdefdio. SetVolume (float)|

Onaylama ekleyebileceğiniz özelliklerin listesi için bkz. [Htmdefdioelement](https://developer.mozilla.org/docs/Web/API/HTMLAudioElement) .

**Arama özellikleri:** `HtmlAudio` için arama özellikleri `Id`, `Name` ve `Title`.

**Filtre özellikleri:** `HtmlAudio` için filtre özellikleri `Src`, `Class`, `ControlDefinition` ve `TagInstance`.

> [!NOTE]
> Arama ve duraklatma için zaman miktarı önemli olabilir. Kayıttan yürütme sırasında, kodlanmış UI testi sesi duraklatmadan önce `(TimeSpan)` belirtilen zamana kadar bekler. Bazı özel durumlar tarafından, belirtilen süre duraklatma komutuna vurmadan önce geçmişse, bir özel durum oluşturulur.

## <a name="video-control"></a>Video denetimi
**Video denetimi:** HTML5 video denetimindeki eylemler doğru şekilde kaydedilir ve kayıttan yürütülür.

![HTML5 video denetimi](../test/media/codedui_html5_video.png)

|Eylem|Kayıt|Oluşturulan kod|
|-|---------------|-|
|**Videoyu oynat**<br /><br /> Doğrudan denetimden veya denetimin sağ tıklama menüsünden.|00:00:00 'den video > \<adı oynat|HtmlVideo. Play (TimeSpan)|
|**Videoda belirli bir zamana arama**|\<adı ara > video 00:01:48|HtmlVideo. Seek (TimeSpan)|
|**Videoyu Duraklat**<br /><br /> Doğrudan denetimden veya denetimin sağ tıklama menüsünden.|00:01:53 adresinden \<adı > video Duraklat|HtmlVideo. Pause (TimeSpan)|
|**Videoyu sustur**<br /><br /> Doğrudan denetimden veya denetimin sağ tıklama menüsünden.|\<adı > video sesini kapat|HtmlVideo. Mute ()|
|**Videoyu aç**<br /><br /> Doğrudan denetimden veya denetimin sağ tıklama menüsünden.|\<adı > videoyu aç|HtmlVideo. aç ()|
|**Video hacmini değiştirme**|Video > \<adı birimini %79 olarak ayarlayın||

Onaylama ekleyebileceğiniz özelliklerin listesi için bkz. [Htmlvideoelement](https://developer.mozilla.org/docs/Web/HTML/Element/video) .

**Arama özellikleri:** `HtmlVideo` için arama özellikleri `Id`, `Name` ve `Title`.

**Filtre özellikleri:** `HtmlVideo` için filtre özellikleri `Src`, `Poster`, `Class`, `ControlDefinition` ve `TagInstance`.

> [!NOTE]
> -30s veya + 30s etiketlerini kullanarak videoyu geri sarın veya ileri sardıysanız, bu, uygun zamana göre arama yapmak için toplanır.

## <a name="progressbar"></a>ProgressBar
**ProgressBar denetimi:** ProgressBar, ınteractable olmayan bir denetimdir. Bu denetimin `Value` ve `Max` özelliklerine onaylama ekleyebilirsiniz. Daha fazla bilgi için bkz. [HTMLProgressElement](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/progress).

![HTML5 ProgressBar denetimi](../test/media/codedui_html5_progressbar.png)

## <a name="see-also"></a>Ayrıca bkz.

- [HTML öğeleri](https://developer.mozilla.org/docs/Web/HTML/Element)
- [UI otomasyonunu kullanarak kodunuzu test etme](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri ve eylem kayıtları için desteklenen yapılandırmalar ve platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
