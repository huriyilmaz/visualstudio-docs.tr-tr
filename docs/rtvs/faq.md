---
title: Visual Studio için R Araçları SSS
description: Visual Studio 'da R hakkında sık sorulan sorular.
ms.date: 12/04/2017
ms.topic: reference
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 4eef8e79023bdd3bde03fec33c16a1c8f6d90446
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306266"
---
# <a name="frequently-asked-questions"></a>Sık sorulan sorular

## <a name="visual-studio-support"></a>Visual Studio desteği

**SORU. RTVS OS X veya Linux üzerinde çalışıyor mu?**

A. RTVS, Visual Studio 'nun yalnızca Windows 'un bir uygulama olan üzerine kurulmuştur. Microsoft Visual Studio Code ve Mac için Visual Studio desteğini araştırmaktadır. [Rtvs sorun #1295](https://github.com/Microsoft/RTVS/issues/1295)bakın.

**SORU. RTVS Visual Studio Express sürümleriyle çalışır mı?**

A. Hayır.

**SORU. Visual Studio uzantılarını RTVS? ile kullanabilir miyim**

A. Kesinlikle. İşte, R ile çalışan insanlar için popüler olan birkaç özellik aşağıda verilmiştir.

- [VIM anahtar bağlamaları için Vsvım](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)
- [GitHub](https://marketplace.visualstudio.com/items?itemName=GitHub.GitHubExtensionforVisualStudio)
- [Canlı önizleme özellikli markın Düzenleyicisi](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.MarkdownEditor)

Daha fazla bilgi edinmek için [Visual Studio Market](https://marketplace.visualstudio.com/) bakın.

**SORU. Rtvs, Visual Studio 'da olduğu için R 'nin C# C++ ve diğer Microsoft dilleri ile kolayca kullanılabileceği anlamına gelir.**

A. Hayır. RTVS, R kodu geliştirmeye yönelik bir araçtır ve standart yerel R yorumlayıcıları kullanır. R ve diğer diller arasında birlikte çalışma şu anda desteklenmiyor.

**SORU. RTVS, Ingilizce olmayan bir yerel ayarla çalışıyor mu?**

A. RTVS 'nin 1,0 sürümü yalnızca Ingilizce 'dir. 1,1 sürümü, Visual Studio 'nun kendisi tarafından kullanılan aynı dil kümesine yerelleştirilir. Bu sırada, [Visual studio 2015 Için İngilizce dil paketini](https://www.microsoft.com/download/details.aspx?id=48157)kullanın veya visual Studio 2017 ' de, yükleyiciyi çalıştırın ve **dil paketleri** sekmesinde İngilizce ' yi seçin.

![Visual Studio 2017 için uluslararası ayarlar](media/FAQ-international-settings.png)

**SORU. Gerçekten geçerli Visual Studio ayarlarımı beğendiniz, ancak yeni veri bilimi ayarlarını denemek istiyorum. Ne yapmam gerekir?**

A. Geçerli Visual Studio ayarlarınızı **araçlar**@no__t**Içeri aktarma ve dışarı aktarma ayarlarını**kullanarak kaydedin, sonra veri bilimi ayarlarına geçin. Kaydedilen ayarları geri yüklemek için, **Ayarları içeri ve dışarı aktar** komutunu yeniden kullanın.

**SORU. Visual Studio projem bir ağ paylaşımında depolayabilirim miyim?**

A. Hayır, Visual Studio bir ağ paylaşımından proje yüklemeyi desteklemez.

## <a name="r-interpretersintegration"></a>R yorumlayıcıları/tümleştirmesi

**SORU. Hangi R yorumlayıcılarla birlikte çalışır?**

A. [Cran R](https://cran.r-project.org/), [Microsoft R Client ve Microsoft Machine Learning Server](/machine-learning-server/)

**SORU. Bu yorumlayıcıları nereden indirebilirim?**

A. Bkz. [yükleme](installing-r-tools-for-visual-studio.md).

Soru **Microsoft R Server nedir?**

A. R Server [Microsoft Machine Learning Server](/machine-learning-server/what-is-machine-learning-server)eski adıdır.

**SORU. RTVS, R 'nin 32 bitlik sürümleriyle çalışır mı?**

A. Hayır, RTVS yalnızca Windows 'un 64 bit sürümlerinde çalışan R 'nin 64 bitlik sürümlerini destekler.

**SORU. RTVS, kaynak denetimi sistemim ile çalışıyor mu?**

A. Evet, Visual Studio ile tümleştirilmiş herhangi bir kaynak denetimi sistemini kullanabilirsiniz.

**SORU. Bir RTVS projesi için önerilen *. gitignore* ayarları nelerdir?**

A. GitHub, önerilen *. gitignore* dosyalarının ana deposunu tutar. Burada görebilirsiniz: [R. gitignore](https://github.com/github/gitignore/blob/master/R.gitignore)

## <a name="remote-services"></a>Uzak hizmetler

S. **Visual Studio 'da uzak hizmetler nedir?**

A. Visual Studio için uzak R Hizmetleri, Windows veya Linux makinesini ayarlamanıza ve sonra RTVS 'den buna bağlanmanızı sağlar. Bkz. [uzak çalışma alanlarını ayarlama](setting-up-remote-r-workspaces.md).

S. **RTVS Microsoft Machine Learning Server 'ye bağlanabilir mi?**

A. Hayır, Microsoft ML Server farklı bir teknolojidir ve RTVS 'nin gerektirdiği şekilde aynı bağlantı mekanizmasına sahip değildir.

S. **Azure 'da Veri Bilimi VM'si görüntüsü kullanılarak oluşturulan bir sanal makineye RTVS bağlanabilir mi?**

A. Yes [veri bilimi VM'si-Windows 2016](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/) görüntüsü, Visual Studio Için uzak R hizmetleriyle önceden yüklenmiş olarak gelir.

S, **R 'nin yüklü olduğu uzak bir makineye RTVS bağlanabilir mi?**

R kodunu uzak bir makinede yürütmek için, bazı hizmetin istekleri dinlemesi, kodun alınması ve sonuçların istemci makinesine geri gönderilmesi gerekir. Bu, Visual Studio için uzak R Hizmetleri 'nin yaptığı şeydir. Bkz. [uzak çalışma alanlarını ayarlama](setting-up-remote-r-workspaces.md).

S. **Uzak oturum nedir?**

A. Machine Learning Server belgelerinde [uzak sunucuda yürütme](/machine-learning-server/r/how-to-execute-code-remotely) başlıklı makaleye bakın.

## <a name="rtvs-development-and-features"></a>RTVS geliştirme ve özellikleri

**SORU. Özellik X eksik, ancak RStudio şunu içeriyor!**

A. RStudio, birçok yıl boyunca geliştirmede olan R için harika ve yetişkinlere yönelik bir IDE 'dir. RTVS, başarılı olması gereken tüm kritik özelliklere sahip olacak şekilde arar. [GitHub](https://github.com/Microsoft/RTVS/issues/)'daki sorunları dosyalayarak gelecekteki çalışmanın önceliklendirmesine yardımcı olun.

**SORU. RTVS 'e katkıda bulunabilir**

A. Kesinlikle! Kaynak kodu [GitHub](https://github.com/microsoft/RTVS)'da bulunur. Zaten dosyalananlara hata ve açıklama göndermek için sorun izleyicisini kullanın.

Ayrıca, bu belgeye katkıda bulunmak için de hoş geldiniz @ no__t-0Herhangi bir sayfanın sağ üst kısmındaki **Düzenle** komutunu seçmeniz yeterlidir. Belgeler hakkındaki yorumlara Ayrıca, herhangi bir sayfanın en altına ekleyebileceğiniz hoş geldiniz.
