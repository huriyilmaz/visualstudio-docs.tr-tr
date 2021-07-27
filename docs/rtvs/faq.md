---
title: Visual Studio için R Araçları SSS
description: R ile ilgili sık sorulan sorular Visual Studio.
ms.date: 12/04/2017
ms.prod: visual-studio-dev15
ms.topic: reference
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: acfd103e3839115c795de57c8e3359058885b7a6
ms.sourcegitcommit: fdba1b294b94e1f6a8e897810646873422393fff
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2021
ms.locfileid: "114679994"
---
# <a name="frequently-asked-questions"></a>Sık sorulan sorular

## <a name="visual-studio-support"></a>Visual Studio desteği

**S. RTVS OS X veya Linux üzerinde çalışır mı?**

A. RTVS şu anda yalnızca Visual Studio bir uygulama olan Windows üzerine inşa edilmiştir. Microsoft, Visual Studio Code ve Mac için Visual Studio. rtvs [sorununa bakın #1295.](https://github.com/Microsoft/RTVS/issues/1295)

**S. RTVS, Visual Studio Express çalışır mı?**

A. Hayır.

**S. RTVS ile Visual Studio kullanabilir miyim?**

A. Elbette. Aslında R ile çalışan kişiler için popüler olan birkaç şey burada verİler.

- [Vim anahtar bağlamaları için VsVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)
- [GitHub](https://marketplace.visualstudio.com/items?itemName=GitHub.GitHubExtensionforVisualStudio)
- [Canlı önizleme ile Markdown düzenleyicisi](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.MarkdownEditor)

Daha fazla [Visual Studio markete](https://marketplace.visualstudio.com/) bakın.

**S. RTVS bir Visual Studio olduğu için R'nin C#, C++ ve diğer Microsoft dilleriyle kolayca kullanılası anlamına mı geliyor?**

A. Hayır. RTVS, R kodu geliştirmeye yönelik bir araçtır ve standart yerel R yorumlayıcılarını kullanır. R ve diğer diller arasında birlikte çalışma şu anda desteklenmiyor.

**S. RTVS, İngilizce olmayan bir yerel dille çalışır mı?**

A. RTVS'nin 1.0 sürümü yalnızca İngilizcedir. 1.1 sürümü, kendi diliyle aynı dil Visual Studio yerelleştirilmiş olur. Bu arada, [Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=48157)için İngilizce dil paketini kullanın veya Visual Studio 2017'de yükleyiciyi çalıştırın ve Dil Paketleri sekmesinde **İngilizce'yi** seçin.

![Visual Studio 2017 için uluslararası ayarlar](media/FAQ-international-settings.png)

**S. Geçerli uygulama ayarlarımı Visual Studio, ancak yeni Veri Bilimi ayarlarını denemek istiyorum. Ne yapabilirim?**

A. Araçlar İçeri ve Dışarı Visual Studio'ı kullanarak **geçerli** Ayarlar ayarlarınızı  >  **kaydedin** ve veri bilimi ayarlarına geçiş yapın. Kaydedilen ayarları geri yüklemek için İçeri ve Dışarı **Aktarma Ayarlar** kullanın.

**S. Bir ağ paylaşımında Visual Studio projemi depolar musunuz?**

A. Hayır, Visual Studio ağ paylaşımından proje yüklenmesini desteklemez.

## <a name="r-interpretersintegration"></a>R yorumlayıcıları/tümleştirme

**S. RTVS hangi R yorumlayıcıları ile çalışır?**

A. [CRAN R,](https://cran.r-project.org/) [Microsoft R Client ve Microsoft Machine Learning Server](/machine-learning-server/)

**S. Bu yorumlayıcıları nereden indirebilirim?**

A. Bkz. [Yükleme.](installing-r-tools-for-visual-studio.md)

S **Ne Microsoft R Server?**

A. R Server, [Microsoft Machine Learning Server.](/machine-learning-server/what-is-machine-learning-server)

**S. RTVS, R'nin 32 bit sürümleriyle çalışır mı?**

A. Hayır, RTVS yalnızca 64 bit R sürümünün 64 bit sürümlerde çalışan R sürümünü Windows.

**S. RTVS kaynak denetim sistemim ile çalışıyor mu?**

A. Evet, kaynak denetimiyle tümleştirilmiş herhangi bir kaynak denetim sistemini Visual Studio.

**S. RTVS projesi için *önerilen .gitignore* ayarları nedir?**

A. GitHub önerilen *.gitignore dosyalarının deposunu bulundurur.* Burada bunu görebilir: [R .gitignore](https://github.com/github/gitignore/blob/master/R.gitignore)

## <a name="remote-services"></a>Uzak hizmetler

S. **Visual Studio'daki Uzak Hizmetler nedir?**

A. Visual Studio için Uzak R Hizmetleri, Windows veya Linux makinesi ayarlamanıza ve ardından RTVS'den bu makineye bağlanmanıza olanak sağlar. Bkz. [Uzak çalışma alanlarını ayarlama.](setting-up-remote-r-workspaces.md)

S. **RTVS, Microsoft Machine Learning Server?**

A. Hayır, Microsoft ML Server farklı bir teknoloji olduğundan ve RTVS için gereken bağlantı mekanizmasını sağlamaz.

S. **RTVS, Azure'da sanal makine görüntüsü kullanılarak Veri Bilimi VM'si vm'ye bağlanıyor mu?**

A. Evet; Veri Bilimi VM'si [- Windows 2016 görüntüsü, 2016](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/) için Uzak R Hizmetleri'ne önceden Visual Studio.

S, **RTVS R yüklü bir uzak makineye bağlanıyor mu?**

Uzak makinede R kodu yürütmek için istekleri dinleyen, kod alan ve sonuçları istemci makinesine geri gönderen bir hizmet olması gerekir. Uzak R Hizmetleri bu Visual Studio yapar. Bkz. [Uzak çalışma alanlarını ayarlama.](setting-up-remote-r-workspaces.md)

S. **Uzak Oturum nedir?**

A. Machine Learning Server [belgelerinde Uzak sunucuda](/machine-learning-server/r/how-to-execute-code-remotely) yürütme makalesine bakın.

## <a name="rtvs-development-and-features"></a>RTVS geliştirme ve özellikleri

**S. X özelliği eksik, ancak RStudio'da var!**

A. RStudio, uzun yıllardır geliştirme aşamasında olan R için harika ve olgun bir IDE'dir. RTVS, başarılı olmak için ihtiyacınız olan tüm kritik özelliklere sahip olmak için arama yapmaktır. sorunlarını dosyalama ile gelecekteki çalışma önceliklerini belirlemeye [yardımcı GitHub.](https://github.com/Microsoft/RTVS/issues/)

**S. RTVS'ye katkıda olabilir miyim?**

A. Kesinlikle! Kaynak kodu [Github'da yer alar.](https://github.com/microsoft/RTVS) Hataları göndermek ve önceden dosyalandırmış olanlar hakkında yorum yapmak için sorun izleyicisini kullanın.

Ayrıca bu belgelere katkıda bulunmak için herhangi bir sayfanın sağ üst köşesindeki Düzenle &mdash; komutunu seçmeniz de gerekir.  Herhangi bir sayfanın en altına ek olarak belgelere yönelik yorumlar da abilirsiniz.
