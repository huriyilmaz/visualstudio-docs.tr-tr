---
title: Dağıtımlara yönelik güncelleştirmeleri denetleme
description: bir ağdan yüklerken Visual Studio güncelleştirmenin nerede göründüğünü değiştirmeyi öğrenin.
ms.date: 11/23/2021
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 620c848ee7d52ab802f8b05135f26bdade122a64
ms.sourcegitcommit: 2281b4f1f8737f263c0d7e55e00b5ec81517327d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2021
ms.locfileid: "133108841"
---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>ağ tabanlı Visual Studio dağıtımlarında güncelleştirmeleri denetleme
> [!WARNING]
> BU IÇERIĞIN BAŞKA SAYFALARLA BIRLEŞTIRILDIĞI IÇIN KULLANıM DıŞı OLMASı AMAÇLANMıŞTıR. Bu sayfa TOC 'den kaldırılmıştır.

Enterprise yöneticiler genellikle son kullanıcılara dağıtmak üzere bir düzen oluşturup bir ağ dosya paylaşımında barındırır. Bu sayfada, ağ düzeni seçeneklerinizi doğru şekilde yapılandırma açıklanmaktadır.

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Visual Studio güncelleştirmelerin nerede göründüğünü denetleme

**Senaryo 1: Istemci bir düzenden başlangıçta yüklendi, ancak ağ düzeni konumundan veya Web 'den güncelleştirmeleri alacak şekilde yapılandırıldı**

varsayılan olarak, yükleme ilk olarak bir ağ paylaşımından dağıtılsa bile Visual Studio güncelleştirmeler için çevrimiçi görünmeye devam eder. Web üzerinde bir güncelleştirme varsa, Kullanıcı bunu yükleyebilir. ağ düzeni önbelleği, güncelleştirilmiş herhangi bir ürün bitleri için ilk olarak incelense de, orada bulunamadıklarında Visual Studio, web 'den güncelleştirilmiş ürün bitlerini arayacaktır ve indirirler.

**Senaryo 2: Istemci başlangıçta yüklendi ve yalnızca ağ düzeninden güncelleştirmeleri almalıdır**

Visual Studio istemcisinin güncelleştirmeleri nerede kurduğunu denetlemek istiyorsanız, örneğin, istemci makineniz ınternet erişimine sahip değilse ve yalnızca ve her zaman düzenden yüklenmesini sağlamak istiyorsanız, istemci yükleyicisinin güncelleştirilmiş ürün bitlerini aradığı konumu yapılandırabilirsiniz. Bu ayarın, istemci düzenden ilk yüklemeyi yapmadan önce doğru şekilde yapılandırıldığından emin olmak en iyisidir.

1. Çevrimdışı düzen oluşturma:

   ```shell
   vs_enterprise.exe --layout C:\vsoffline --lang en-US
   ```

2. Onu barındırmak istediğiniz dosya paylaşımında kopyalayın:

   ```shell
   xcopy /e C:\vsoffline \\server\share\VS
   ```

3. `response.json`Düzendeki dosyayı değiştirin ve `channelUri` değeri, yönetici denetimlerinin channelmanifest. json dosyasının bir kopyasına işaret etmek üzere değiştirin.

   Aşağıdaki örnekte olduğu gibi, değerde ters eğik çizgileri attığınızdan emin olun:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   Artık son kullanıcılar, Visual Studio yüklemek için bu paylaşımdan kurulum 'u çalıştırabilir.

   ```shell
   \\server\share\VS\vs_enterprise.exe
   ```

bir kurumsal yönetici, kullanıcılarının Visual Studio daha yeni bir sürümüne güncelleştirilmesi için zaman olduğunu belirlediğinde, aşağıdaki gibi, güncelleştirilmiş dosyaları içerecek şekilde [düzen konumunu güncelleştirebilirler](update-a-network-installation-of-visual-studio.md) .

1. Aşağıdaki komuta benzer bir komut kullanın:

   ```shell
   vs_enterprise.exe --layout \\server\share\VS --lang en-US
   ```

2. `response.json`Güncelleştirilmiş düzendeki dosyanın özelleştirmelerinizi, özellikle de channelUri değişikliğini şu şekilde içerdiğinden emin olun:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

bu düzenden mevcut Visual Studio yüklemeleri, ' de güncelleştirmeleri arar `\\server\share\VS\ChannelManifest.json` . channelmanifest. json, kullanıcının yükledikinden daha yeniyse Visual Studio, kullanıcıya bir güncelleştirmenin kullanılabildiğini bildirir.

istemciden başlatılan tüm yükleme güncelleştirmeleri otomatik olarak Visual Studio güncelleştirilmiş sürümünü doğrudan düzenden yükler.

**Senaryo 3: Istemci, başlangıçta Web 'den yüklendi, ancak şimdi yalnızca bir ağ düzeninden güncelleştirmeler almalıdır**

bazı durumlarda, istemci makinesi web 'den Visual Studio zaten yüklemiş olabilir, ancak artık yönetici, gelecekteki tüm güncelleştirmelerin yönetilen bir düzenden gelmesini istiyor. Bunu yapmanın tek yolu, ürünün istenen sürümüne sahip bir ağ düzeni oluşturmak ve ardından istemci makinesinde, önyükleyici _konumundan_ (ör.), önyükleyiciyi çalıştırmanız için desteklenir `\\server\share\vs_enterprise.exe` . İdeal olarak, özgün istemci yüklemesi, doğru şekilde yapılandırılmış ChannelURI ile ağ düzeninden önyükleyici kullanılarak gerçekleşmiş olur, ancak güncelleştirilmiş önyükleyici ağ düzeni konumundan çalıştırılarak da çalışır. Bu eylemlerden biri, söz konusu düzen konumuyla bir bağlantı olan istemci makinesine katıştırılabilir. Bu senaryonun doğru çalışması için tek desteklenmediği uyarısıyla, düzen dosyasındaki "Channelurı" nin, `response.json` özgün yüklemenin gerçekleştiği sırada istemcinin makinesinde ayarlanmış olan channelurı ile aynı olması gerekir. Büyük olasılıkla bu değer ilk olarak Internet [Release kanalına](https://aka.ms/vs/16/release/channel)ayarlanmıştır.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
* [Yönetici güncelleştirmelerini etkinleştirme](enabling-administrator-updates.md)
* [Yönetici güncelleştirmeleri uygulanıyor](applying-administrator-updates.md)
* [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio örnekleri yönetmek için araçlar](tools-for-managing-visual-studio-instances.md)
* [ürün yaşam döngüsü ve bakım Visual Studio](/visualstudio/releases/2019/servicing/)
