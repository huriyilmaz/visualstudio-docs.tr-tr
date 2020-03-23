---
title: Test Ayarlarını Kullanarak Ağ Öykünme'yi Yapılandır
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- test settings, network emulation
ms.assetid: ff275cfb-5df9-4710-9a91-9caabaaad34f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 350640a4db6a81d19801aedb03d0d490895f97ef
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589220"
---
# <a name="how-to-configure-network-emulation-using-test-settings-in-visual-studio"></a>Nasıl yapılır: Visual Studio'da test ayarlarını kullanarak ağ öykünme sini yapılandırın

Tanılama veri bağdaştırıcısını, uygulamanızı Visual Studio'dan çeşitli ağ ortamları altında test etmek üzere yapılandırabilirsiniz. Ayrıca, testlerinizi çalıştırdığınızda yapay ağ yükünü veya darboğazını sınamak için yapılandırılabilir.

> [!WARNING]
> Testlerinizi taklit ettiğiniz ağdan daha yavaş bir türde gerçek bir ağda çalıştırıyorsanız, test yine de daha yavaş ağ hızında çalışır. Öykünme yalnızca ağ ortamını yavaşlatabilir, hızlandıramaz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Aşağıdaki yordam, yapılandırma düzenleyicisinden ağ öykünme yapılandırmanasıl açıklanır. Bu adımlar, hem Microsoft Test Yöneticisi'ndeki hem de Visual Studio'daki yapılandırma düzenleyicisi için geçerlidir.

> [!NOTE]
> Ağ öykünme tanılama veri bağdaştırıcısı yalnızca Visual Studio test ayarları için geçerlidir. Microsoft Test Yöneticisi'nde test ayarları için kullanılmaz.

Yönetici ayrıcalıkları olan bir hesap ağ öykünmesi için kullanılmalıdır. El ile testler çalıştıran yerel bir rol için ağ öykünmesi seçtiyseniz, yönetici ayrıcalıklarını kullanarak Microsoft Test Yöneticisi'ni başlatmanız gerekir. Başka bir rol için ağ öykünmesi seçtiyseniz, bu rol için makinedeki test aracısının yöneticiler grubunun bir üyesi olan bir kullanıcı hesabı kullandığını doğrulamanız gerekir. Test aracınız için hesabı nasıl ayarlayacağıhakkında daha fazla bilgi için, [test aracılarını Yükle ve yapılandırma](../test/lab-management/install-configure-test-agents.md)ya da yapılandırma'ya bakın.

> [!NOTE]
> Test aracısının varsayılan hesabı olan Ağ Hizmeti hesabı, yöneticiler grubunun bir üyesi değildir.

**Gerçek Ağ Öykünme**

Visual Studio tüm test türleri için yazılım tabanlı gerçek ağ öykünme kullanır. Bu yük testleri içerir. Gerçek ağ öykünme, ağ paketlerinin doğrudan manipülasyonu yla ağ koşullarını simüle eder. Gerçek ağ emülatörü, Ethernet gibi güvenilir bir fiziksel bağlantı kullanarak hem kablolu hem de kablosuz ağların davranışını taklit edebilir. Aşağıdaki ağ öznitelikleri gerçek ağ öykünme dahil edilmiştir:

- Ağ da gidiş-dönüş süresi (gecikme süresi)

- Kullanılabilir bant genişliği miktarı

- Kuyruk davranışı

- Paket kaybı

- Paketlerin yeniden sıralanması

- Hata yayılmaları.

Gerçek ağ öykünasyonu, IP adreslerine veya TCP, UDP ve ICMP gibi protokollere dayalı ağ paketlerini filtrelemede esneklik de sağlar.

Gerçek ağ öykünmesi, ağ tabanlı geliştiriciler ve sınananlar tarafından istenilen test ortamını taklit etmek, performansı değerlendirmek, değişimin etkisini tahmin etmek veya teknoloji optimizasyonu hakkında kararlar almak için kullanılabilir. Donanım test yatakları ile karşılaştırıldığında, gerçek ağ öykünme çok daha ucuz ve daha esnek bir çözümdür.

## <a name="configure-network-emulation-for-your-test-settings"></a>Test ayarlarınız için ağ öykünme yapılandırma

Bu yordamdaki adımları gerçekleştirmeden önce, Test ayarlarınızı Visual Studio'dan açmanız ve ardından **Veri ve Tanılama** sayfasını seçmeniz gerekir.

### <a name="to-configure-network-emulation-for-your-test-settings"></a>Test ayarlarınız için ağ öykünülmasını yapılandırmak için

1. Belirli bir ağa öykünmek için kullanılacak rolü seçin.

    > [!NOTE]
    > Ağ Öykünme bağdaştırıcısını yalnızca istemci rolüne veya sunucu rolüne göre yapılandırmanız gerekir. Bağdaştırıcıyı her iki rolde de kullanmanız gerekmez. Bağdaştırıcı, her iki rol arasındaki iletişimi etkileyen ağ gürültüsünü taklit eder, böylece her iki rolde de kullanmak zorunda kalmamanız gerekir. Gerekli olmadığı sürece, sunucu rolü üzerinde ek yükü önlemek için Ağ Öykünme bağdaştırıcısı için bir istemci rolü seçmelisiniz.

2. **Ağ Öykünme'yi** seçin ve sonra **Yapılandır'ı**seçin.

     Ağ öykünmesini yapılandırmak için iletişim kutusu görüntülenir.

3. **Kullanmak üzere ağ profilini seç'in**yanındaki oku seçin ve bir test çalıştırdığınızda taklit etmek istediğiniz ağ türünü seçin (örneğin, **Kablo-DSL 768Kps).**

    > [!WARNING]
    > Testlerinizi taklit ettiğiniz ağdan daha yavaş bir türde gerçek bir ağda çalıştırıyorsanız, test yine de daha yavaş ağ hızında çalışır. Öykünme yalnızca ağ ortamını yavaşlatabilir, hızlandıramaz.

4. Ağ öykünme tanılama veri bağdaştırıcısını test ayarlarına eklerseniz ve bunu yerel makinenizde kullanmayı planlıyorsanız, ağ öykünme sürücüsünü de makinenizin ağ bağdaştırıcılarından birine bağlamanız gerekir. Ağ öykünme sürücüsü, ağ öykünme tanıveri bağdaştırıcısının işlevi ne kadar gerekli. Ağ öykünme sürücüsü yüklenir ve bağdaştırıcınıza iki şekilde bağlanır:

    - **Microsoft Visual Studio Test Aracısı ile yüklü ağ öykünme sürücüsü:** Microsoft Visual Studio Test Aracısı hem uzak makinelerde hem de yerel makinenizde kullanılabilir. Visual Studio Test Aracısı yüklediğinizde, yükleme işlemi ağ öykünme sürücüsünü ağ kartınıza bağlayan bir yapılandırma adımı içerir. Daha fazla bilgi için [bkz.](../test/lab-management/install-configure-test-agents.md)

    - **Microsoft Visual Studio Test Professional ile yüklü ağ öykünme sürücüsü:** Ağ öykünme sini'ni ilk kez kullandığınızda, ağ öykünme sürücüsünü bir ağ kartına bağlamanız istenir.

    > [!TIP]
    > Ayrıca aşağıdaki komutu kullanarak Visual Studio test aracısını yüklemeden yerel makinenizdeki komut satırından ağ öykünme sürücüsünü yükleyebilirsiniz: **VSTestConfig NETWORKEMULATION /install**

## <a name="see-also"></a>Ayrıca bkz.

- [Test ayarlarını kullanarak tanılama bilgilerini toplama](../test/collect-diagnostic-information-using-test-settings.md)
- [El ile testler çalıştırın (Azure Test Planları)](/azure/devops/test/run-manual-tests?view=vsts)
