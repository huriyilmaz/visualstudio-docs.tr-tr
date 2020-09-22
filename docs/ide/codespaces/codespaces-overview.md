---
title: GitHub Codespaces 'a genel bakış (Önizleme)
description: Visual Studio ile GitHub Codespaces hakkında daha fazla bilgi edinin ve geliştirme ortamınızı buluta genişletmenize nasıl yardımcı olabileceğini öğrenin.
ms.topic: overview
ms.date: 09/04/2020
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: vs-2019
ms.openlocfilehash: a0991fa1760e2ea4592ec861f9d2d29a5763eaea
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90862191"
---
# <a name="what-is-github-codespaces-preview"></a>GitHub Codespaces nedir? (Önizleme)

Codespaces 'a hoş geldiniz! Burada size sevindik.

GitHub Codespaces, tüm etkinlikler için bulut destekli bir geliştirme ortamı, uzun süreli bir proje veya çekme isteğini gözden geçirme gibi kısa süreli bir görev sağlar. Visual Studio 2019 Preview içinden bir codespace ile çalışabilirsiniz ([sınırlı genel beta için kaydolabilirsiniz](https://github.com/features/codespaces/signup)).

Ayrıca, GitHub Codespaces, &mdash; genellikle üretim iş yükleri için bir geliştirme ortamına ayrılmış yinelenebilirlik ve güvenilirlik gibi DevOps 'ın avantajlarından çoğunu getirir &mdash; . Ayrıca, istediğiniz ve kullandığınız araçların, işlemlerin ve yapılandırmaların de aynı olduğundan, GitHub Code alanlarını kişiselleştirebilirsiniz.

Bu belge, temel kavramları açıklayacak ve Codespaces özelliklerinin tanıtılmasına neden olacak. Başlamak istiyorsanız, [Visual Studio 'yu bir codespace Ile kullanma](use-visual-studio-with-codespaces.md)' yı inceleyin.

> [!IMPORTANT]
> GitHub Codespaces 'ı kullanmak için sınırlı [genel beta](https://github.com/features/codespaces/signup) için kaydolmanız gerekir. Beta döneminde GitHub, Codespaces kullanılabilirliği hakkında garanti vermez. Beta 'a katılma hakkında daha fazla bilgi için bkz. [Codespaces hakkında](https://docs.github.com/github/developing-online-with-codespaces/about-codespaces#joining-the-beta).

## <a name="concepts-and-features"></a>Kavramlar ve özellikler

GitHub Codespaces özellikleri, birkaç temel kavramın üzerine kurulmuştur. Bu bölümde bu kavramlar ele alınmaktadır ve özelliklerin kısa bir turu verilmiştir.

### <a name="remote-development"></a>Uzaktan geliştirme

Günümüzde birçok geliştirici, belirli geliştirme ve çalışma zamanı yığınları ile yapılandırılan uzak kurulumlarda veya VM 'lerde kod denemeye çalışır. Bu, çok zor, çok kesintiye neden olduğu ve bazı durumlarda bu geliştirme ortamlarını yerel olarak ayarlamak imkansız olduğundan, bu şekilde yapılır. Ayrıca bireyler, yeni teknolojileri veya yeni çerçeveleri, günlük işleri için ihtiyaç duydukları makineleri "kullanıma alma" olmaksızın denemek ister.

Uzak ortamları ve uzaktan özellikli araçları kullanarak geliştiricilere güçlendirirken, genellikle makine yönetiminin ek yükü vardır. Ortam yapılandırması genellikle ekleme ve bağlam geçişini karmaşıklaştırır. GitHub Codespaces, birçok ortamın aynı anda var olmasına olanak tanıyarak hızlı ekleme ve bağlam değiştirme engelleri ortadan kaldırır. 

GitHub Codespaces, kurulum üzerinden üretkenliğinizi odaklamenize imkan tanıyan yönetilen çözümler sağlar. GitHub Codespaces, Uzaktan geliştirme için kavramsal ve teknik olarak Visual Studio 2019 ' i genişletir. 

### <a name="about-codespaces"></a>Codespaces hakkında

Bir codespace, GitHub Codespaces 'ın "arka uç" yarısıdır. Yazılım geliştirmeyle ilişkili tüm işlem, derleme, hata ayıklama, geri yükleme vb. olur. Bir kod alanı oluşturmak, bir görevi tamamlaması, bir PR 'yi gözden geçirmeniz veya yeni bir proje başlatmak için ihtiyaç duyduğunuz her şeyi hazırlar. Codespaces çalışma zamanı, derleyici, hata ayıklayıcı, düzenleyici, özel dotfile yapılandırmalarının ve bir proje üzerinde çalışmak için gereken kaynak kodunu yapılandırır.

Bulutta barındırılan kod alanları aşağıdaki avantajları sağlar:

- Bunlar oluşturmak ve atılabilir hızlıdır. İhtiyacınız olan kadar (hesap sınırlarına kadar) oluşturun ve işiniz bittiğinde onları atın.
- Bunlar yönetilirler ve bu, genel bakımın sizin için azaltılıyoruz.
- Tahmin edilebilir fiyatlandırmaları vardır ve yalnızca kullandığınız kadar ödeyin. Ve, ard arda maliyetleri ortadan kaldırmak için yerleşik bir oto askıya alma.
- İşlem kaynaklarını kaydeder. Geliştirme iş yükünüzü buluta taşıdığınızda, bu, kişisel makinenizde sınırlı kaynakları serbest bırakır.

## <a name="custom-configuration"></a>Özel yapılandırma

GitHub Codespaces, çok çeşitli proje veya görevleri kapsayacak şekilde oluşturulmuştur. Ortak varsayılanlar sağlayan akıllı yapılandırma özellikleriyle başlayabilir veya [özel yapılandırmayla](customize-codespaces.md)bir codespace üzerinde ince ayar yapabilirsiniz.

Esnek yapılandırma, geliştiricilerin yerel bir makineye uygulanması zor olan benzersiz yapılandırma ve gereksinimlere sahip projelere hızlı bir şekilde erişmesini sağlar. Ayrıca, tekrarlanabilir codespaces "makinmda çalışma" sorunlarını ortadan kaldırır.

## <a name="personal-configuration"></a>Kişisel yapılandırma

Kişisel tercihlerini koruyan, bulutta barındırılan bir kod alanı hakkında tanıdık ve doğal bir şekilde geliştirme yapmak için kritik olduğunu biliyoruz. GitHub Codespaces, bir codespace yapılandırması üzerinde kişiselleştirilmiş özelleştirmeler için Katmanlar. Düzenleyicilerin ve terminallerin kişisel tercihleri ve yapılandırması GitHub Codespaces tarafından desteklenir.

[Özel bir özel dotfiles](https://docs.github.com/github/developing-online-with-codespaces/personalizing-codespaces-for-your-account) koleksiyonuyla (örneğin,, vb.) bir codespace oluşturulabilir `.bashrc` `.gitconfig` ve GitHub codespaces, oluşturduğunuz her codespace, projeye özgü ortam yeteneklerine bakılmaksızın istediğiniz şekilde, sizin istediğiniz şekilde, bu sayede git kimliğinizi, temaları ve ayarlarınızı otomatik olarak eşitler.

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio 'Yu bir codespace ile kullanma](use-visual-studio-with-codespaces.md)
* [Codespace 'i özelleştirme](customize-codespaces.md)
* [Desteklenen Visual Studio özellikleri](supported-features-codespaces.md)
