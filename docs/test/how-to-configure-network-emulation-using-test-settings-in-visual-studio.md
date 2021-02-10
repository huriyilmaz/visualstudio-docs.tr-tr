---
title: Test ayarlarını kullanarak ağ öykünmesini yapılandırma
description: Visual Studio 'daki çeşitli ağ ortamları altında uygulamanızı test etmek için tanılama veri bağdaştırıcısını nasıl yapılandıracağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/03/2016
ms.topic: how-to
helpviewer_keywords:
- test settings, network emulation
ms.assetid: ff275cfb-5df9-4710-9a91-9caabaaad34f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 6126441890f34296fa0d8a9cda20bee32752cd81
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966766"
---
# <a name="how-to-configure-network-emulation-using-test-settings-in-visual-studio"></a>Nasıl yapılır: Visual Studio 'da test ayarlarını kullanarak ağ öykünmesini yapılandırma

Uygulamanızı Visual Studio 'daki çeşitli ağ ortamları altında test etmek için tanılama veri bağdaştırıcısını yapılandırabilirsiniz. Ayrıca, testlerinizi çalıştırdığınızda yapay bir ağ yükünü veya performans sorunlarını test etmek üzere de yapılandırılabilir.

> [!WARNING]
> Testlerinizi, öykünmesi yaptığınız ağdan daha yavaş bir türde olan gerçek bir ağda çalıştırırsanız, test yine daha yavaş ağ hızında çalışmaya devam edecektir. Öykünme yalnızca ağ ortamını yavaşlatabilir, hızlandıramaz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

::: moniker range="vs-2017"
Aşağıdaki yordamda, yapılandırma düzenleyicisinden Ağ öykünmesinin nasıl yapılandırılacağı açıklanmaktadır. Bu adımlar hem Microsoft Test Yöneticisi hem de Visual Studio 'daki yapılandırma Düzenleyicisi için geçerlidir.
::: moniker-end
::: moniker range=">=vs-2019"
Aşağıdaki yordamda, yapılandırma düzenleyicisinden Ağ öykünmesinin nasıl yapılandırılacağı açıklanmaktadır. Bu adımlar, Visual Studio 'daki yapılandırma Düzenleyicisi için geçerlidir.
::: moniker-end

> [!NOTE]
> Ağ öykünmesi tanılama veri bağdaştırıcısı yalnızca Visual Studio test ayarları için geçerlidir. Microsoft Test Yöneticisi (Visual Studio 2017 ' de kullanım dışı) test ayarları için kullanılmaz.

::: moniker range="vs-2017"
Ağ öykünmesi için yönetici ayrıcalıklarına sahip bir hesap kullanılmalıdır. El ile testler çalıştıran yerel bir rol için ağ öykünmesi seçtiyseniz, yönetici ayrıcalıklarını kullanarak Microsoft Test Yöneticisi başlatmanız gerekir. Başka herhangi bir rol için ağ öykünmesi seçtiyseniz, söz konusu rolün makinedeki test aracısının Yöneticiler grubunun üyesi olan bir kullanıcı hesabı kullandığını doğrulamanız gerekir. Test aracınız için hesabı ayarlama hakkında daha fazla bilgi için bkz. [test aracılarını yüklemek ve yapılandırmak](../test/lab-management/install-configure-test-agents.md).
::: moniker-end

> [!NOTE]
> Test Aracısı için varsayılan hesap olan ağ hizmeti hesabı, Yöneticiler grubunun bir üyesi değildir.

**Gerçek ağ öykünmesi**

Visual Studio tüm test türleri için yazılım tabanlı doğru ağ öykünmesi kullanır. Bu yük testlerini içerir. Gerçek ağ öykünmesi, ağ paketlerinin doğrudan işlemesini sağlayarak ağ koşullarına benzetir. Gerçek ağ öykünücüsü, Ethernet gibi güvenilir bir fiziksel bağlantı kullanarak hem kablolu hem de kablosuz ağların davranışını taklit edebilir. Aşağıdaki ağ öznitelikleri, gerçek ağ öykünmesine dahil edilir:

- Ağ üzerinden gidiş dönüş süresi (gecikme)

- Kullanılabilir bant genişliği miktarı

- Sıraya alma davranışı

- Paket kaybı

- Paketlerin yeniden sıralanması

- Hata yayılmaları.

Gerçek ağ öykünmesi, ağ paketlerinin IP adresleri veya TCP, UDP ve ıCMP gibi protokollere göre filtrelenmesi için esneklik de sağlar.

Gerçek ağ öykünmesi, ağ tabanlı geliştiriciler ve test ediciler tarafından istenen bir test ortamına öykünmek, performansı değerlendirmek, değişikliğin etkisini tahmin etmek veya teknoloji iyileştirmesi hakkında kararlar almak için kullanılabilir. Gerçek ağ öykünmesi, donanım test bedine kıyasla, çok daha ucuz ve esnek bir çözümdür.

## <a name="configure-network-emulation-for-your-test-settings"></a>Test ayarlarınız için ağ öykünmesini yapılandırma

Bu yordamdaki adımları gerçekleştirmeden önce, Visual Studio 'dan test ayarlarınızı açmanız ve sonra **veri ve tanılama** sayfasını seçmeniz gerekir.

### <a name="to-configure-network-emulation-for-your-test-settings"></a>Test ayarlarınız için ağ öykünmesini yapılandırmak için

1. Belirli bir ağı benzemek için kullanılacak rolü seçin.

    > [!NOTE]
    > Ağ öykünmesi bağdaştırıcısını yalnızca istemci rolü veya sunucu rolü üzerinde yapılandırmanız gerekir. Bağdaştırıcıyı her iki rolde de kullanmanız gerekmez. Bağdaştırıcı her iki rol arasındaki iletişimi etkileyen ağ gürültüsünü taklit eder; böylece her ikisinde de kullanmanız gerekmez. Gerekli olmadığı durumlar dışında, sunucu rolünde ek yüke engel olmak için ağ öykünmesi bağdaştırıcısı için bir istemci rolü seçmeniz gerekir.

2. **Ağ öykünmesi** ' ni seçin ve ardından **Yapılandır**' ı seçin.

     Ağ öykünmesinin yapılandırılacağı iletişim kutusu görüntülenir.

3. **Kullanılacak ağ profilini seç**' in yanındaki oku seçin ve bir testi çalıştırdığınızda öykünmek istediğiniz ağ türünü seçin (örneğin, **kablo-DSL 768Kps**).

    > [!WARNING]
    > Testlerinizi, öykünmesi yaptığınız ağdan daha yavaş bir türde olan gerçek bir ağda çalıştırırsanız, test yine daha yavaş ağ hızında çalışmaya devam edecektir. Öykünme yalnızca ağ ortamını yavaşlatabilir, hızlandıramaz.

4. Ağ öykünmesi tanılama veri bağdaştırıcısını test ayarlarına dahil etmeniz ve yerel makinenizde kullanmayı düşünüyorsanız, ağ öykünmesi sürücüsünü Makinenizin ağ bağdaştırıcılarından birine bağlamanız gerekir. Ağ öykünmesi sürücüsü, ağ öykünmesi tanılama veri bağdaştırıcısının çalışması için gereklidir. Ağ öykünmesi sürücüsü, bağdaştırıcınıza yüklenmiş ve iki şekilde bağlanır:

    - **Microsoft Visual Studio Test Aracısı ile yüklenen ağ öykünmesi sürücüsü:** Microsoft Visual Studio Test Aracısı hem uzak makinelerde hem de yerel makinenizde kullanılabilir. Bir Visual Studio Test Aracısı yüklediğinizde, yükleme işlemi ağ öykünmesi sürücüsünü ağ kartınıza bağlayan bir yapılandırma adımı içerir. Daha fazla bilgi için bkz. [test aracılarını yükleyip yapılandırma](../test/lab-management/install-configure-test-agents.md).

    - **Ağ öykünmesi sürücüsü Microsoft Visual Studio Test Professional yüklendi:** Ağ öykünmesini ilk kez kullandığınızda, ağ öykünmesi sürücüsünü bir ağ kartına bağlamanız istenir.

    > [!TIP]
    > Ayrıca, aşağıdaki komutu kullanarak Visual Studio test aracısını yüklemeden yerel makinenize komut satırından ağ öykünme sürücüsünü yükleyebilirsiniz: **VSTestConfig NETWORKEMULATION/install**

## <a name="see-also"></a>Ayrıca bkz.

- [Test ayarlarını kullanarak tanılama bilgilerini topla](../test/collect-diagnostic-information-using-test-settings.md)
- [El ile testleri çalıştırma (Azure Test Plans)](/azure/devops/test/run-manual-tests?view=vsts&preserve-view=true)
