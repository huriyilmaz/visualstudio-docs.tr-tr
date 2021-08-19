---
title: Dotfuscator Community’yi yükseltme
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: dotfuscator, dotfuscator Community, dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, koruma, topluluk sürümü, gizleme, .net, ücretsiz, Visual Studio 2019, Visual Studio 2017, Visual Studio, yükseltme, komut satırı
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator Community
- Dotfuscator
- obfuscation
- protection
- Dotfuscator upgrade
- upgrade Dotfuscator
- upgrading Dotfuscator
- register Dotfuscator
- registering Dotfuscator
- Dotfuscator command line
- Dotfuscator Professional
description: Visual Studio eklenen Community dotfuscator 'un ücretsiz kopyasını nasıl yükselteceğinizi öğrenin.
ms.assetid: c7c60904-27f9-4f1f-b79b-ddf65041b810
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.openlocfilehash: ef784a6c0d0816fdbf2ff93c5d4de09c2e4a40a5
ms.sourcegitcommit: f930bc28bdb0ba01d6f7cb48f229afecfa0c90cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2021
ms.locfileid: "122334693"
---
# <a name="upgrade-dotfuscator-community"></a>Dotfuscator Community’yi yükseltme

dotfuscator Community, tüm geliştiriciler için Microsoft Visual Studio kullanan birçok uygulama koruma ve sağlamlaştırma özelliği sunar.
Ancak, Dotfuscator sürümlerini yükseltecek kullanıcılar için daha fazla özellik mevcuttur.

bu kullanıcı kılavuzunda ***PreEmptive Protection-dotfuscator Community* 6** ele alınmaktadır.
yükleme geçmişinize ve Visual Studio sürümüne bağlı olarak, önceki ana sürümü şu anda dotfuscator Community 5 ' i çalıştırıyor olabilirsiniz.
Bu durumda, [kodunuzun en son koruma önlemleri verildiğinden emin olmak önemli][always-improving]olduğundan, ' yi yükseltmeniz gerekir.
Yükseltmeler ücretsiz olarak kullanılabilir.

Bu sayfada şu anda hangi sürümün olduğunu, gerekirse sürüm 6 ' ya yükseltme ve iki sürüm arasında hangi özelliklerin değiştirildiği veya kaldırıldığı açıklanmaktadır.

## <a name="determining-dotfuscators-version"></a>Dotfuscator 'un sürümünü belirleme

Hangi Dotfuscator sürümünün çalıştırdığınızı bilmiyorsanız, aşağıdakilerden birini yaparak sürümü belirleyebilirsiniz:

* Visual Studio **araçlar** menüsüne gidip **PreEmptive Protection-dotfuscator Community**' yı seçerek dotfuscator Community [grafik kullanıcı arabirimini][gui] (guı) başlatın.
  Dotfuscator GUI 'sinden **Yardım** menüsünü açın ve hakkında ekranını göstermek için **hakkında...** seçeneğini belirleyin.
  Bu ekranda Dotfuscator 'un sürümü listelenir.

* Derleme ile tümleşik bir Dotfuscator varsa ( [Xamarin][xamarin] Apps gibi [), yapı][cli] günlüklerinizi aşağıdakine benzer bir satır için de denetleyebilirsiniz:

  ```no-highlight
  Dotfuscator Community Version 5.42.0.9514-e0e25f754
  ```

  Bu metni görmek için, derlemenize ait ayrıntı düzeyini artırmanız gerekebilir.
  Visual Studio için bkz. [ayrıntı Ayarlar][verbosity].

İlk noktadan önceki sürümün ilk tamsayı `.` , Dotfuscator 'un ana sürümünü gösterir.
Bu durumda `5` , en son Dotfuscator 6 özelliklerinden ve koruma güncelleştirmelerinden faydalanabilmeniz için bu sayfada yükseltme adımlarını gerçekleştirmeniz gerekir.

## <a name="upgrade-instructions"></a>Yükseltme yönergeleri

bu bölüm, sürüm 5 ' ten sürüm 6 ' ya kadar dotfuscator Community tipik kullanımlarını yükseltmeye yönelik yönergelerin kümelerini içerir.

### <a name="installing-dotfuscator-6"></a>Dotfuscator 6 yükleniyor

dotfuscator Community, Visual Studio için bir uzantı olarak dağıtılır.
dotfuscator 6 ' yı yüklemeye yönelik yönergeler, sahip olduğunuz Visual Studio sürümüne göre farklılık gösterir:

* **Visual Studio 2019**.
  dotfuscator Community 6, Visual Studio 2019 (sürüm 16.10.0 ve üzeri) sonraki sürümlerinde bulunur.
  [Visual Studio 2019][vs-update] ' i en son sürüme güncelleştirin.
  bu, tüm dotfuscator Community 5 yüklemesini dotfuscator Community 6 ' ya yükseltir.

    * dotfuscator zaten yüklü değilse, önce Visual Studio güncelleştirin ve ardından [yükleme][install]bölümüne bakın.

    * Visual Studio olan sürümlere ek olarak, dotfuscator [indirmeleri][download] sayfasından her zaman en son dotfuscator Community sürümlerini alabilirsiniz.

* **Visual Studio 2017**.
  bu Visual Studio sürümü yalnızca dotfuscator Community 5 ile birlikte gönderilir.
  ancak, [dotfuscator indirmeleri][download] sayfasına giderek ve uygun indirme bağlantısını seçerek dotfuscator Community 6 sürümüne yükleyebilirsiniz.

  indirilen dosyayı çalıştırın `.vsix` ve Visual Studio ' ye dotfuscator Community 6 yüklemek için istemleri izleyin.
  bu, var olan dotfuscator Community 5 yüklemelerini yükseltir.

* **Visual Studio önceki sürümleri.**
  dotfuscator Community 6, bu Visual Studio sürümlerinde desteklenmez.
  Visual Studio daha yeni bir sürümüne yükseltmeniz veya [dotfuscator Community 'den dotfuscator Professional yükseltmeniz][pro]önerilir.

daha önce dotfuscator Community 5 ' i [kaydettiniz][register] , dotfuscator Community 6 ' ı ilk kez çalıştırdığınızda bu kayıt otomatik olarak dönüştürülür.

### <a name="updating-paths-to-the-command-line-interface"></a>Yollar komut satırı arabirimine güncelleştiriliyor

clı güncelleştirme yönergeleri için tam dotfuscator Community kullanıcı kılavuzunun [Community 5 ' ten güncelleştirme][up-com] sayfasına bakın.

### <a name="upgrading-dotfuscator-config-files"></a>Dotfuscator yapılandırma dosyalarını yükseltme

yapılandırma dosyaları yükseltme yönergeleri için, tam dotfuscator Community kullanıcı kılavuzunun [Community 5 ' ten güncelleştirme][up-com-d] bölümüne bakın.

### <a name="updating-xamarin-integration"></a>Xamarin tümleştirmesi güncelleştiriliyor

Xamarin tümleştirme güncelleştirme yönergeleri için, tam dotfuscator Community kullanıcı kılavuzunun [Community 5 ' ten güncelleştirme][up-com-xa] ' ye bakın

### <a name="updating-references-to-attribute-libraries"></a>Öznitelik kitaplıklarına başvuruları güncelleştirme

öznitelik kitaplıkları güncelleştirme yönergelerine başvurular için, tam dotfuscator Community kullanıcı kılavuzunun [Community 5 ' ten güncelleştirme][up-com-li] bölümüne bakın.

## <a name="removed-features"></a>Kaldırılan özellikler

dotfuscator Community 6, dotfuscator Community 5 ' ten önemli değişiklikler sunar.
dotfuscator Community 5 kullanıyorsanız, bu bölümde derleme değişiklikleri gerektirebilecek veya dotfuscator 'un çıkışını etkileyebilecek değişikliklerle nasıl başa çıkılabileceğinizi açıklanmaktadır.
[Changelog][changelog]'da değişikliklerin tam bir listesi bulunur.

## <a name="registering-dotfuscator-community"></a>Dotfuscator Community kaydediliyor

dotfusCommunity cator 'un kayıtlı kullanıcıları, dotfuscator Community otomatik derleme sürecinizde tümleştirmeyi kolaylaştıran [komut satırı desteği][cli]gibi ek özelliklere erişim sağlar. Kayıt Ayrıca, [karıştırılmış yığın izlemelerinin kodunu çözmek][decode-obfuscated]için kullanılan yerleşik bir araca erişim izni verir.

Kayıt hızlı, basit ve ücretsizdir.
dotfuscator Community kaydetmek için, [tam dotfuscator Community kullanıcı kılavuzundaki yönergelere][register-ce]bakın.

## <a name="upgrading-to-dotfuscator-professional"></a>Dotfuscator 'a yükseltme Professional

dotfuscator Community temel bir koruma düzeyi sağladığından, ***PreEmptive protection-dotfuscator Professional*** sürümüne yükseltme, gelişmiş gizleme dönüştürmeleri ve koruma özelliklerine erişmenizi sağlayacaktır. Bu modüller şunlardır:

* *Fikri mülkiyet koruması*
  * Gelişmiş aşırı yükleme endüksiyon™ ve rastgele tanımlayıcı seçimi dahil ek yeniden adlandırma seçenekleri.
  * [Otomatik kod ayrıştırılmış derleme sırasında hedeflenen dönüşümler][control-flow]de dahil olmak üzere kurumsal düzeyde gizleme dönüştürmelerini erişim.
  * [Gizli dizeleri gizleyebilme][string-encryption]özelliği, ayrıştırılmış kodun basit bir aramasını olanaksız hale getirir.
  * [Şekilde belirtmeyecek adlandırmak sahiplik ve dağıtım dizelerini derlemelerinize ekleme][watermarking]özelliği (yazılım sulu işaret), yetkisiz yazılım sızıntılarının kaynağını belirlemenizi sağlar.
  * [Birden çok derlemeyi tek bir halinde birleştirebilme][linking]özelliği, saldırganların kod öğelerinin rollerini belirlemede daha da zor olduğundan, kaygıların ayrılması ortadan kalkar.
  * [Kullanılmayan kodu uygulamanızdan otomatik olarak kaldırabilme][pruning], gönderilen hassas kod miktarını azaltır.
* *Uygulama bütünlüğü koruması*
  * Ek [uygulama savunma davranışları][check-actions].
  * Derlemelere karşı koruma ve hata ayıklama kodu ekleme özelliği `.dll` .
  * Uygulamanın yaşam süresi sonu tarihinden önce bir uyarı dönemi sağlama özelliği.
  * Süre sonu uyarı dönemi sırasında veya son tarihten sonra uygulama kodunu bildirebilme özelliği.

dotfuscator Professional, sektör standardı [.net gizleme][net-obfuscator] ve devam eden destek, bakım ve ürün güncelleştirmeleri gerektiren kurumsal geliştiricilere uygundur.
ayrıca, dotfuscator Professional Visual Studio ile sıkı tümleştirme sağlar ve ticari kullanım için lisanslanır.

dotfuscator Professional gelişmiş uygulama koruma özellikleri hakkında daha fazla bilgi için lütfen [dotfuscator genel bakış][product-about] sayfamızı ziyaret edin ve [dotfuscator Professional öğesini dotfuscator Community ile karşılaştırın][product-compare].

[dotfuscator Professional 'nin tam olarak desteklenen denemeleri, preemptive.com adresinden istekte bulunabilir.][eval]

## <a name="see-also"></a>Ayrıca bkz.

[Dotfuscator Community’yi yükseltme][full]

<!-- Copyright © 2021 PreEmptive Solutions, LLC -->

[control-flow]:  https://www.preemptive.com/products/dotfuscator/features#controlflow
[string-encryption]:  https://www.preemptive.com/products/dotfuscator/features#string
[watermarking]:  https://www.preemptive.com/products/dotfuscator/features#watermarking
[linking]:  https://www.preemptive.com/products/dotfuscator/features#linking
[pruning]:  https://www.preemptive.com/products/dotfuscator/features#pruning

[check-actions]:  https://www.preemptive.com/dotfuscator/pro/userguide/en/protection_checks_overview.html#actions

[net-obfuscator]:  https://www.preemptive.com/products/dotfuscator/overview
[eval]:  https://www.preemptive.com/eval-request

[product-about]:  https://www.preemptive.com/products/dotfuscator/overview
[product-compare]:  https://www.preemptive.com/products/dotfuscator/compare-editions

[cli]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_cli.html
[register-ce]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html#register

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_upgrades.html
[decode-obfuscated]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_decode_stack_trace.html

[dotfuscator Community kullanıcı kılavuzu][home]

[always-improving]:  https://www.preemptive.com/always-improving
[gui]:  https://www.preemptive.com/dotfuscator/ce/docs/help/getting_started_gui.html
[xamarin]:  https://www.preemptive.com/dotfuscator/ce/docs/help/getting_started_xamarin.html
[verbosity]:  ../how-to-view-save-and-configure-build-log-files.md?view=vs-2019&preserve-view=true#to-change-the-amount-of-information-included-in-the-build-log
[vs-update]:  ../../install/update-visual-studio.md?view=vs-2019&preserve-view=true
[install]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_install.html
[download]:  https://www.preemptive.com/products/dotfuscator/downloads
[pro]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_upgrades.html
[register]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_register.html
[up-com]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_upgrade_from_5.html#pctoc-updating-paths-to-the-command-line-interface
[up-com-d]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_upgrade_from_5.html#pctoc-upgrading-dotfuscator-config-files
[up-com-xa]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_upgrade_from_5.html#pctoc-updating-xamarin-integration
[up-com-li]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_upgrade_from_5.html#pctoc-updating-references-to-attribute-libraries
[changelog]:  https://www.preemptive.com/support/dotfuscator-support/dotfuscator-ce-change-log
[home]:  https://www.preemptive.com/dotfuscator/ce/docs/help/index.html