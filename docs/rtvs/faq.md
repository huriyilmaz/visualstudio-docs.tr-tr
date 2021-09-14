---
title: Visual Studio için R Araçları SSS
description: Visual Studio 'de R hakkında sık sorulan sorular.
ms.date: 12/04/2017
ms.prod: visual-studio-dev15
ms.topic: reference
author: kraigb
ms.author: kraigb
manager: jmartens
ms.technology: vs-rtvs
ms.workload:
- data-science
ms.openlocfilehash: 9d49c6b8d52fd047a109f2f470c97adafb457810
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628263"
---
# <a name="frequently-asked-questions"></a>Sık sorulan sorular

## <a name="visual-studio-support"></a>Visual Studio desteği

**Ç. RTVS OS X veya Linux üzerinde çalışıyor mu?**

A. rtvs, şu anda Visual Studio en üstünde oluşturulmuştur, bu da yalnızca Windows bir uygulama. Microsoft Visual Studio Code ve Mac için Visual Studio desteğini araştırmaktadır. [Rtvs sorun #1295](https://github.com/Microsoft/RTVS/issues/1295)bakın.

**Ç. rtvs Visual Studio Express sürümleriyle çalışır mi?**

A. Hayır.

**Ç. rtvs ile Visual Studio uzantıları kullanabilir miyim?**

A. Elbette. İşte, R ile çalışan insanlar için popüler olan birkaç özellik aşağıda verilmiştir.

- [VIM anahtar bağlamaları için Vsvım](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)
- [GitHub](https://marketplace.visualstudio.com/items?itemName=GitHub.GitHubExtensionforVisualStudio)
- [Canlı önizleme özellikli markın Düzenleyicisi](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.MarkdownEditor)

daha fazla bilgi edinmek için [Visual Studio marketi](https://marketplace.visualstudio.com/) 'ne bakın.

**Ç. rtvs Visual Studio olduğundan, R 'nin C#, C++ ve diğer Microsoft dilleriyle kolayca kullanılabileceği anlamına gelir.**

A. Hayır. RTVS, R kodu geliştirmeye yönelik bir araçtır ve standart yerel R yorumlayıcıları kullanır. R ve diğer diller arasında birlikte çalışma şu anda desteklenmiyor.

**Ç. RTVS, Ingilizce olmayan bir yerel ayarla çalışır mı?**

A. RTVS 'nin 1,0 sürümü yalnızca Ingilizce 'dir. 1,1 sürümü Visual Studio kendisi olan aynı dil kümesine yerelleştirilir. bu sırada, [Visual Studio 2015 için ingilizce dil paketini](https://www.microsoft.com/download/details.aspx?id=48157)kullanın veya Visual Studio 2017 ' de, yükleyiciyi çalıştırın ve **dil paketleri** sekmesinde ingilizce ' yi seçin.

![Visual Studio 2017 için uluslararası ayarlar](media/FAQ-international-settings.png)

**Ç. gerçekten geçerli Visual Studio ayarlarımı beğendiniz, ancak yeni veri bilimi ayarlarını denemek istiyorum. Ne yapmam gerekir?**

A. **araç**  >  **içeri ve dışarı aktarma Ayarlar** araçları kullanarak geçerli Visual Studio ayarlarınızı kaydedin, sonra veri bilimi ayarlarına geçin. kaydedilen ayarları geri yüklemek için **içeri aktar ve dışarı aktar Ayarlar** komutunu yeniden kullanın.

**Ç. Visual Studio projem bir ağ paylaşımında depolayabilirim miyim?**

A. hayır, Visual Studio bir ağ paylaşımından proje yüklemeyi desteklemez.

## <a name="r-interpretersintegration"></a>R yorumlayıcıları/tümleştirmesi

**Ç. Hangi R yorumlayıcılarla birlikte çalışır?**

A. [cran R](https://cran.r-project.org/), [Microsoft R Client ve Microsoft Machine Learning Server](/machine-learning-server/)

**Ç. Bu yorumlayıcıları nereden indirebilirim?**

A. Bkz. [yükleme](installing-r-tools-for-visual-studio.md).

Soru **Microsoft R Server nedir?**

A. R Server [Microsoft Machine Learning Server](/machine-learning-server/what-is-machine-learning-server)eski adıdır.

**Ç. RTVS, R 'nin 32 bitlik sürümleriyle çalışır mi?**

A. Hayır, RTVS yalnızca Windows 64 bit sürümlerinde çalışan R 'nin 64 bitlik sürümlerini destekler.

**Ç. RTVS, kaynak denetimi sistemimde çalışıyor mu?**

A. Evet, Visual Studio ile tümleştirilmiş herhangi bir kaynak denetimi sistemini kullanabilirsiniz.

**Ç. Bir RTVS projesi için önerilen *. gitignore* ayarları nelerdir?**

A. GitHub, önerilen *. gitignore* dosyaları deposunu saklar. Burada görebilirsiniz: [R. gitignore](https://github.com/github/gitignore/blob/master/R.gitignore)

## <a name="remote-services"></a>Uzak hizmetler

S. **Visual Studio uzak hizmetler nedir?**

A. Visual Studio için uzak R hizmetleri, Windows veya Linux makinesi ayarlamanıza ve sonra rtvs 'den buna bağlanmanızı sağlar. Bkz. [uzak çalışma alanlarını ayarlama](setting-up-remote-r-workspaces.md).

S. **RTVS Microsoft Machine Learning Server 'ye bağlanabilir mi?**

A. hayır, Microsoft ML Server farklı bir teknolojidir ve rtvs 'nin gerektirdiği şekilde aynı bağlantı mekanizmasına sahip değildir.

S. **Azure 'da Veri Bilimi VM'si görüntüsü kullanılarak oluşturulan bir sanal makineye RTVS bağlanabilir mi?**

A. Yes [Veri Bilimi VM'si-Windows 2016](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/) görüntüsü Visual Studio için uzak R hizmetleriyle önceden yüklenmiş olarak gelir.

S, **R 'nin yüklü olduğu uzak bir makineye RTVS bağlanabilir mi?**

R kodunu uzak bir makinede yürütmek için, bazı hizmetin istekleri dinlemesi, kodun alınması ve sonuçların istemci makinesine geri gönderilmesi gerekir. Bu, Visual Studio için uzak R hizmetlerinden hangileridir. Bkz. [uzak çalışma alanlarını ayarlama](setting-up-remote-r-workspaces.md).

S. **Uzak oturum nedir?**

A. Machine Learning Server belgelerinde [uzak sunucuda yürütme](/machine-learning-server/r/how-to-execute-code-remotely) başlıklı makaleye bakın.

## <a name="rtvs-development-and-features"></a>RTVS geliştirme ve özellikleri

**Q. feature X eksik, ancak RStudio şunu içeriyor!**

A. RStudio, birçok yıl boyunca geliştirmede olan R için harika ve yetişkinlere yönelik bir IDE 'dir. RTVS, başarılı olması gereken tüm kritik özelliklere sahip olacak şekilde arar. [GitHub](https://github.com/Microsoft/RTVS/issues/)sorunları girerek gelecekteki çalışmanın önceliklerini belirlemeye yardımcı olun.

**Ç. RTVS 'ye katkıda bulunabilir miyim?**

A. Kesinlikle! Kaynak kodu [GitHub](https://github.com/microsoft/RTVS)üzerinde bulunur. Zaten dosyalananlara hata ve açıklama göndermek için sorun izleyicisini kullanın.

Ayrıca, bu belgeye katkıda bulunmak için &mdash; herhangi bir sayfanın sağ üst kısmındaki **Düzenle** komutunu seçmeniz yeterlidir. Belgeler hakkındaki yorumlara Ayrıca, herhangi bir sayfanın en altına ekleyebileceğiniz hoş geldiniz.
