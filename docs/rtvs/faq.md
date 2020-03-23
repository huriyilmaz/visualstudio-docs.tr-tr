---
title: Visual Studio SSS için R Araçları
description: Visual Studio'da R hakkında sık sorulan sorular.
ms.date: 12/04/2017
ms.topic: reference
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 4eef8e79023bdd3bde03fec33c16a1c8f6d90446
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "72306266"
---
# <a name="frequently-asked-questions"></a>Sık sorulan sorular

## <a name="visual-studio-support"></a>Visual Studio desteği

**S. RTVS OS X veya Linux üzerinde çalışıyor mu?**

A. RTVS şu anda yalnızca Windows'a özel bir uygulama olan Visual Studio'nun üzerine inşa edilmiştir. Microsoft, Visual Studio Code ve Visual Studio for Mac'teki desteği araştırıyor. [RTVS sorunu #1295](https://github.com/Microsoft/RTVS/issues/1295)bakın.

**S. RTVS Visual Studio Express sürümleri ile çalışır mı?**

A. Hayır.

**S. RTVS ile Visual Studio uzantıları nı kullanabilir miyim?**

A. Kesinlikle. Aslında, burada R ile çalışan insanlar için popüler birkaçı vardır.

- [Vim anahtar bağlamaları için VsVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)
- [GitHub](https://marketplace.visualstudio.com/items?itemName=GitHub.GitHubExtensionforVisualStudio)
- [Canlı önizleme ile Markdown editörü](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.MarkdownEditor)

Daha fazla bilgi edinmek için [Visual Studio Marketplace'e](https://marketplace.visualstudio.com/) bakın.

**S. RTVS Visual Studio'da olduğundan, R'nin C#, C++ ve diğer Microsoft dilleriyle kolayca kullanılabildiği anlamına mı geliyor?**

A. Hayır. RTVS, R kodunu geliştirmek için bir araçtır ve standart yerel R yorumlayıcılarını kullanır. R ve diğer diller arasındaki interop şu anda desteklenmez.

**S. RTVS İngilizce olmayan bir yerel ile çalışır mı?**

A. RTVS'nin 1.0 sürümü yalnızca İngilizcedir. 1.1 sürümü Visual Studio kendisi ile aynı dil kümesi ne yerelleştirilmiş olacaktır. Bu arada Visual [Studio 2015 veya Visual Studio 2017 için İngilizce dil paketini](https://www.microsoft.com/download/details.aspx?id=48157)kullanın, yükleyiciyi çalıştırın ve **Dil Paketleri** sekmesinde İngilizce'yi seçin.

![Visual Studio 2017 için uluslararası ayarlar](media/FAQ-international-settings.png)

**S. Gerçekten benim mevcut Visual Studio ayarları gibi, ama yeni Veri Bilimi ayarlarını denemek istiyorum. Ne yapmalıyım?**

A. **Araçlar** > **Alma ve Dışa Aktarma Ayarlarını**kullanarak geçerli Visual Studio ayarlarınızı kaydedin ve ardından Veri Bilimi ayarlarına geçin. Kaydedilen ayarları geri yüklemek için **Ayarlar İçe Ve Dışa Aktar** komutunu yeniden kullanın.

**S. Visual Studio projemi bir ağ paylaşımında saklayabilir miyim?**

A. Hayır, Visual Studio bir ağ paylaşımından proje yüklemeyi desteklemez.

## <a name="r-interpretersintegration"></a>R tercümanları/entegrasyonu

**S. R yorumlayıcıları neyle çalışır?**

A. [CRAN R](https://cran.r-project.org/), [Microsoft R Client ve Microsoft Machine Learning Server](/machine-learning-server/)

**S. Bu tercümanları nereden indirebilirim?**

A. [Bkz. Kurulum](installing-r-tools-for-visual-studio.md).

S **Microsoft R Server nedir?**

A. R [Server, Microsoft Machine Learning Server'ın](/machine-learning-server/what-is-machine-learning-server)eski adıdır.

**S. RTVS R 32-bit sürümleri ile çalışır mı?**

A. Hayır, RTVS yalnızca Windows'un 64 bit sürümlerinde çalışan 64 bit R sürümlerini destekler.

**S. RTVS kaynak kontrol sistemiile çalışıyor mu?**

A. Evet, Visual Studio entegre herhangi bir kaynak kontrol sistemi kullanabilirsiniz.

**S. Bir RTVS projesi için önerilen *.gitignore* ayarları nelerdir?**

A. GitHub önerilen *.gitignore* dosyalarının ana deposunu korur. Burada görebilirsiniz: [R .gitignore](https://github.com/github/gitignore/blob/master/R.gitignore)

## <a name="remote-services"></a>Uzak hizmetler

S. **Visual Studio'da Uzaktan Hizmetler Nedir?**

A. Visual Studio için Uzak R Hizmetleri, Windows veya Linux makinesini kurmanızı ve rtvs'den bağlanmanızı sağlar. Bkz. [Uzak çalışma alanlarını ayarlama.](setting-up-remote-r-workspaces.md)

S. **RTVS Microsoft Machine Learning Server'a bağlanabilir mi?**

A. Hayır, Çünkü Microsoft ML Server farklı bir teknolojidir ve RTVS tarafından gerekli aynı bağlantı mekanizması sağlamaz.

S. **RTVS, Azure'daki Data Science VM görüntüsünü kullanarak oluşturulan bir VM'ye bağlanabilir mi?**

A. Evet; [Data Science VM - Windows 2016](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/) görüntüsü Visual Studio için Remote R Services ile önceden yüklenmiş olarak gelir.

S, **RTVS R yüklü uzak bir makineye bağlanabilir mi?**

Uzak bir makinede R kodunu yürütmek için istekleri dinleyen, kod alan ve sonuçları istemci makinesine geri gönderen bazı hizmetler olmalıdır. Visual Studio için Uzaktan R Hizmetleri bunu yapar. Bkz. [Uzak çalışma alanlarını ayarlama.](setting-up-remote-r-workspaces.md)

S. **Uzaktan Oturum Nedir?**

A. Machine Learning Server belgelerindeki [uzak sunucuda yürütüncü](/machine-learning-server/r/how-to-execute-code-remotely) makaleye bakın.

## <a name="rtvs-development-and-features"></a>RTVS geliştirme ve özellikleri

**S. Özellik X eksik, ama RStudio var!**

A. RStudio yıllardır geliştirme aşamasında olan R için fantastik ve olgun Bir IDE olduğunu. RTVS, başarılı olmak için ihtiyacınız olan tüm kritik özelliklere sahip olmayı amaçlamaktadır. [GitHub'da](https://github.com/Microsoft/RTVS/issues/)sorunları dosyalayarak gelecekteki çalışmaları önceliklendirmeye yardımcı olun.

**S. RTVS'ye katkıda bulunabilir miyim?**

A. Kesinlikle! Kaynak kodu [Github'da](https://github.com/microsoft/RTVS)yaşıyor. Hata göndermek ve zaten dosyalanmış olanlar hakkında yorum yapmak için sorun izleyicisini kullanın.

Ayrıca bu belgelere&mdash;katkıda bulunabilirsiniz sadece herhangi bir sayfanın sağ üst sağ daki **Edit** komutunu seçin. Dokümanlar hakkındaki yorumlar da, herhangi bir sayfanın altına ekleyebileceğiniz hoş karşılanır.
