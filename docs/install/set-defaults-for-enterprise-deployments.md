---
title: Kurumsal dağıtımlar için Varsayılanları Ayarla
description: Visual Studio kurumsal dağıtımlarına yönelik etki alanı ilkeleri ve diğer yapılandırma işlemleri hakkında bilgi edinin.
ms.date: 11/23/2021
ms.topic: conceptual
f1_keywords:
- gpo
- policy
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9B7B4608-7A3F-4FF4-BDCE-42D9F7CE6DBA
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 79a0e8fd07d9d30b15832c2b95accbb8ab479f62
ms.sourcegitcommit: 2281b4f1f8737f263c0d7e55e00b5ec81517327d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2021
ms.locfileid: "133108867"
---
# <a name="set-defaults-for-enterprise-deployments-of-visual-studio"></a>Visual Studio kuruluş dağıtımları için varsayılanları ayarlama

Visual Studio dağıtım ve güncelleştirme davranışını etkileyen kayıt defteri ilkeleri ayarlayabilirsiniz. Bu ilkeler, istemci makinesinde geneldir ve şunları etkiler:

- Diğer sürümler veya örneklerle paylaşılan bazı paketlerin yüklendiği yer.
- Paketlerin önbelleğe alınıp alınmayacağı.
- Yönetici güncelleştirmelerinin etkinleştirilmesi ve bunların nasıl uygulanması gerektiği.
- Hangi güncelleştirme kanalları kullanılabilir ve istemciye nasıl sunuldukları.
- Bildirimlerin görünme veya görünme şekli.

Bu ilkeleri, istemci makinesindeki [komut satırı seçeneklerini](use-command-line-parameters-to-install-visual-studio.md) kullanarak, kayıt defteri değerlerini doğrudan istemci makinesinde ayarlayarak ya da bir kuruluş genelinde Grup İlkesi kullanarak dağıtarak ayarlayabilirsiniz.

## <a name="registry-keys"></a>Kayıt defteri anahtarları

Kurumsal Varsayılanları, grup ilkesi veya doğrudan kayıt defterindeki denetimini etkinleştirecek şekilde ayarlayabileceğiniz çeşitli konumlar vardır. Visual Studio, herhangi bir kurumsal ilkenin ayarlanmış olup olmadığını görmek için sırayla görünür; bir ilke değeri aşağıdaki sırada bulunduğunda, kalan anahtarlar yoksayılır.

1. `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup`
2. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`
3. `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\VisualStudio\Setup` (64 bit işletim sistemlerinde)

Bazı kayıt defteri değerleri, henüz ayarlanmamışsa ilk kez otomatik olarak ayarlanır. Bu uygulama, sonraki yüklemelerinin aynı değerleri kullanmasını sağlar. Bu değerler ikinci kayıt defteri anahtarında depolanır `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup` .

Aşağıdaki kayıt defteri değerlerini ayarlayabilirsiniz:

## <a name="controlling-installation-and-download-behavior"></a>Yükleme ve indirme davranışını denetleme
bu bölümdeki kayıt defteri ayarları, Visual Studio ürününün istemci makineye nasıl ve nerede indirileceğini denetler.

| **Ad**                         | **Tür**                    | **Varsayılan**                                         | **Açıklama**       |
|----------------------------------|-----------------------------|-----------------------------------------------------|----------------------------|
| `CachePath`                      | `REG_SZ` veya `REG_EXPAND_SZ` | ProgramData<br>\Microsoft<br>\VisualStudio<br>\ Paketler       | Paket bildirimlerinin ve isteğe bağlı olarak yüklerinin depolandığı dizin. Daha fazla bilgi için bkz. [paket önbelleğini devre dışı bırakma veya taşıma](disable-or-move-the-package-cache.md) sayfası.   |
| `KeepDownloadedPayloads`         | `REG_DWORD`                 | 1                                                   | Yüklendiklerinde bile paket yüklerini saklayın. Değeri dilediğiniz zaman değiştirebilirsiniz. İlkeyi devre dışı bırakmak, tamir ettiğiniz veya değiştirdiğiniz örnek için önbelleğe alınmış tüm paket yüklerini kaldırır. Daha fazla bilgi için bkz. [paket önbelleğini devre dışı bırakma veya taşıma](disable-or-move-the-package-cache.md) sayfası.   |
| `SharedInstallationPath`         | `REG_SZ` veya `REG_EXPAND_SZ` | % ProgramFiles (x86)%<br>\ Microsoft Visual Studio<br>\ Paylaşılan  | bazı paketlerin Visual Studio örneklerinin sürümleri arasında paylaştığı dizin. Değeri dilediğiniz zaman değiştirebilirsiniz, ancak gelecekteki yüklemeleri etkiler. Eski konuma yüklenmiş olan tüm ürünler taşınmamalıdır veya düzgün çalışmayabilir.      |
| `BackgroundDownloadDisabled`     | `REG_DWORD`                 | 0                                                   | kurulumun tüm yüklü Visual Studio ürünleri için güncelleştirmeleri otomatik olarak indirmasını engelleyin. Değeri dilediğiniz zaman değiştirebilirsiniz.    |

> [!IMPORTANT]
> `CachePath`Herhangi bir yüklemeden sonra kayıt defteri ilkesini değiştirirseniz, mevcut paket önbelleğini yeni konuma taşımanız ve `SYSTEM` `Administrators` **tam denetime** sahip olmak ve `Everyone` **okuma** erişimi olması için güvenli olduğundan emin olmanız gerekir.
> Mevcut önbelleğin taşınamaması veya güvenliğinin sağlanması gelecekteki yüklemelerde sorunlara neden olabilir.


## <a name="controlling-administrator-updates"></a>Yönetici güncelleştirmelerini denetleme
::: moniker range="vs-2017"

Bu bölümdeki kayıt defteri ayarları, yönetici güncelleştirmelerinin istemci makineye nasıl uygulandığını denetler.

| **Ad**                         | **Tür**                    | **Varsayılan**                                         | **Açıklama**           |
|----------------------------------|-----------------------------|-----------------------------------------------------|---------------------------|
| `AdministratorUpdatesEnabled`    | `REG_DWORD`                 | 0                                                   | İstemci bilgisayara yönetici güncelleştirmelerinin uygulanmasını sağlar. Bu değer eksikse veya 0 olarak ayarlandıysa, yönetici güncelleştirmeleri engellenir. Bu değer, yönetim kullanımı içindir. Daha fazla bilgi için bkz. [yönetici güncelleştirmelerini etkinleştirme](enabling-administrator-updates.md). |
| `AdministratorUpdatesOptOut`     | `REG_DWORD`                 | 0                                                   | Kullanıcının Visual Studio için yönetici güncelleştirmelerini almak istediğini belirtir. kayıt defteri değerinin yokluğu veya 0 kümesi değeri, Visual Studio kullanıcının Visual Studio için yönetici güncelleştirmelerini almak istediği anlamına gelir. Bu geliştirici kullanıcısına yöneliktir (istemci makinesinde yönetici izinleri varsa). Daha fazla bilgi için bkz. [yönetici güncelleştirmelerini uygulama](../install/applying-administrator-updates.md#understanding-configuration-options). |
| `UpdateConfigurationFile`        | `REG_SZ` veya `REG_EXPAND_SZ` | ProgramData<br>\Microsoft<br>\VisualStudio<br>\updates.config | Yönetim güncelleştirmelerini yapılandırmak için dosya yolu. Daha fazla bilgi için bkz. [yönetici güncelleştirmesi yapılandırma yöntemleri](../install/applying-administrator-updates.md#methods-for-configuring-an-administrator-update).   |    

::: moniker-end

::: moniker range="vs-2019"

Bu bölümdeki kayıt defteri ayarları, yönetici güncelleştirmelerinin istemci makineye nasıl uygulandığını denetler.

| **Ad**                         | **Tür**                    | **Varsayılan**                                         | **Açıklama**           |
|----------------------------------|-----------------------------|-----------------------------------------------------|---------------------------|
| `AdministratorUpdatesEnabled`    | `REG_DWORD`                 | 0                                                   | İstemci bilgisayara yönetici güncelleştirmelerinin uygulanmasını sağlar. Bu değer eksikse veya 0 olarak ayarlandıysa, yönetici güncelleştirmeleri engellenir. Bu değer, yönetim kullanımı içindir. Daha fazla bilgi için bkz. [yönetici güncelleştirmelerini etkinleştirme](enabling-administrator-updates.md). |
| `AdministratorUpdatesOptOut`     | `REG_DWORD`                 | 0                                                   | Kullanıcının Visual Studio için yönetici güncelleştirmelerini almak istediğini belirtir. kayıt defteri değerinin yokluğu veya 0 kümesi değeri, Visual Studio kullanıcının Visual Studio için yönetici güncelleştirmelerini almak istediği anlamına gelir. Bu geliştirici kullanıcısına yöneliktir (istemci makinesinde yönetici izinleri varsa). Daha fazla bilgi için bkz. [yönetici güncelleştirmelerini uygulama](../install/applying-administrator-updates.md#understanding-configuration-options). |
| `UpdateConfigurationFile`        | `REG_SZ` veya `REG_EXPAND_SZ` | ProgramData<br>\Microsoft<br>\VisualStudio<br>\updates.config | Yönetim güncelleştirmelerini yapılandırmak için dosya yolu. Daha fazla bilgi için bkz. [yönetici güncelleştirmesi yapılandırma yöntemleri](../install/applying-administrator-updates.md#methods-for-configuring-an-administrator-update).   |                        
| `BaselineStickinessVersions2019` | `REG_SZ` veya `REG_EXPAND_SZ` | `16.7.0`                                            | İstemcinin üzerinde kalması gereken bakım temeli ikincil sürümü. Daha fazla bilgi için bkz. [yönetici güncelleştirmelerini uygulama](../install/applying-administrator-updates.md#understanding-configuration-options) sayfası. |

::: moniker-end

::: moniker range=">=vs-2022"

Bu bölümdeki kayıt defteri ayarları, yönetici güncelleştirmelerinin istemci makineye nasıl uygulandığını denetler.

| **Ad**                         | **Tür**                    | **Varsayılan**                                         | **Açıklama**           |
|----------------------------------|-----------------------------|-----------------------------------------------------|---------------------------|
| `AdministratorUpdatesEnabled`    | `REG_DWORD`                 | 0                                                   | Yönetici güncelleştirmelerinin istemci bilgisayara uygulanmasına izin verir. Bu değer eksikse veya 0 olarak ayarlanırsa yönetici güncelleştirmeleri engellenir. Bu değer yönetimsel kullanım içindir. Daha fazla bilgi için [bkz. Yönetici Güncelleştirmelerini Etkinleştirme.](enabling-administrator-updates.md) |
| `AdministratorUpdatesOptOut`     | `REG_DWORD`                 | 0                                                   | Kullanıcının kullanıcıya yönetici güncelleştirmeleri almak Visual Studio. Kayıt defteri değerinin olmaması veya 0 değerinin ayarlanmış olmaması, Visual Studio kullanıcıya yönetici güncelleştirmeleri almak istediği Visual Studio. Bu, geliştirici kullanıcıya (istemci makinede yönetici izinlerine sahipse) için. Daha fazla bilgi için [bkz. Yönetici güncelleştirmelerini uygulama.](../install/applying-administrator-updates.md#understanding-configuration-options) |
| `UpdateConfigurationFile`        | `REG_SZ` veya `REG_EXPAND_SZ` | %ProgramData%<br>\Microsoft<br>\VisualStudio<br>\updates.config | Yönetim Güncelleştirmelerini yapılandırmak için dosya yolu. Daha fazla bilgi için [bkz. Yönetici güncelleştirmesini yapılandırma yöntemleri.](../install/applying-administrator-updates.md#methods-for-configuring-an-administrator-update)   |    

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="configuring-source-location-for-updates"></a>Güncelleştirmeler için kaynak konumu yapılandırma 

Bu bölümdeki ayarlar, bir yöneticinin hangi güncelleştirme kanallarının kullanılabilir olduğunu ve kurumsal bir kuruluşta istemcilere nasıl görüneceklerini özelleştirmesine ve denetlemesine olanak sağlar. Güncelleştirme ayarlarının ne olduğu ve nasıl olduğu hakkında bilgi için güncelleştirmelerin [kaynak konumunu yapılandırma belgelerine](update-visual-studio.md#configure-source-location-of-updates-1) bakın. 
Bu işlevsellik, istemcinin Visual Studio 2022 Yükleyicisi'nin ve düzenin 10 Kasım 2021'de veya sonrasında gönderilen 2019 önyükleyici sürümünü kullanmalarını gerektirir. Bunu etkinleştirme kılavuzu, Visual Studio 2019 düzen belgeleri aracılığıyla istemci makinelerinize [Visual Studio 2022](create-a-network-installation-of-visual-studio.md#configure-the-layout-to-always-use-the-latest-installer) yükleyicisini nasıl edinebilirsiniz?

Bu bölümdeki anahtarlar yalnızca kayıt defteri Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup\ geçerlidir

| **Ad**                         | **Tür**                    | **Açıklama**                                                |
|----------------------------------|-----------------------------|-----------------------------------------------------|
| `Channels` | `Key` |  Özel düzen kanalı bilgilerini depolamak için önemli yol. Bu anahtarın değeri Kanal adını göz önünde bulundurarak Kanalı güncelleştir açılan [listesinde yer alan değerdir.](/visualstudio/install/update-visual-studio?#configure-source-location-of-updates-1) |
| `DisabledChannels` | `Key` | Kanalların gizlenme ve kanalların Güncelleştirme Kanalı iletişim kutusunda güncelleştirmesi engellenebilir. Kanal burada tanımlanmışsa iletişim kutusunun dışında filtrelenmiş olur. |
| `ChannelURI` | `REG_SZ` |  Hive'a ekleyerek güncelleştirme kanalı değerleri listesine ekleme veya kayıt defteri kovanını ekleyerek güncelleştirme kanalları listesinden gizleme `Channels` kanalURI'si. `DisabledChannels` Microsoft tarafından barındırılan kanallar için channelURI " https://aka.ms/vs/16/release/channel " veya " " https://aka.ms/vs/16/pre/channel şeklindedir.  Düzenler için bu değerin düzenin ChannelManifest.json'larına işaret ediyor olması gerekir. Aşağıdaki örneklere bakın. |
| `Description` | `REG_SZ` |  Kanalın iki satırlık özel açıklaması. Zaten bir düzenden yüklemişsinizdir, güncelleştirme kullanıcı arabirimi varsayılan Ayarlar "Özel Kanal" olarak değişir ve bunu bu Açıklamayı kullanarak değiştirebilirsiniz. |

Aşağıdaki örnek kayıt defteri dosyası, [Update Ayarlar kullanıcı](/visualstudio/install/update-visual-studio?#configure-source-location-of-updates-1)arabiriminde özel güncelleştirme kanalları için birkaç düzen girdisi eklemenin yanı sıra Önizleme kanalının nasıl gösterildiğini göstermektedir.

```example registry file
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup\Channels]

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup\Channels\More meaningful name of my existing layout]
"channelUri"="\\\\vslayoutserver3\\vs\\2019_Enterprise\\ChannelManifest.json"
"Description"="Dev Tools based on VS 2019 16.9.Spring.2020 servicing baseline"

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup\Channels\Spring 2021 dev toolset]
"channelUri"="\\\\new2019layoutserver\\share\\new2019layout\\ChannelManifest.json"
"Description"="Dev Tools based on VS 2019 16.11.Spring.2021 servicing baseline"

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup\Channels\Next gen dev tools using VS 2022 toolset]
"channelUri"="\\\\vs2022Layoutserver\\share\\2022Enterprise\\ChannelManifest.json"
"Description"="Developer Tools based on the VS 2022 17.0.Winter.2021 LSTC servicing baseline"

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup\DisabledChannels\Preview]
"channelUri"="https://aka.ms/vs/16/pre/channel"
```

::: moniker-end

## <a name="controlling-notifications-in-the-visual-studio-ide"></a>Visual Studio IDE'de bildirimleri denetleme

::: moniker range="vs-2017"

Daha önce açıklandığı Visual Studio, güncelleştirme olup olmadığını görmek için ağ paylaşımı veya İnternet gibi yüklü olduğu konumu denetler. Bir güncelleştirme kullanılabilir olduğunda Visual Studio sağ üst köşesindeki bildirim bayrağını kullanıcıya iletir.

   ![Güncelleştirmeler için bildirim bayrağı](media/notification-flag.png)

::: moniker-end

::: moniker range=">=vs-2019"

Daha önce açıklandığı Visual Studio, güncelleştirme olup olmadığını görmek için ağ paylaşımı veya İnternet gibi yüklü olduğu konumu denetler. Bir güncelleştirme kullanılabilir olduğunda Visual Studio sağ alt köşesindeki bildirim simgesiyle kullanıcıya bunu bildirebilirsiniz.

   ![Visual Studio IDE'de bildirim simgesi](media/vs-2019/notification-bar.png "Visual Studio IDE'de bildirim simgesi")

::: moniker-end

Son kullanıcılara güncelleştirmeler hakkında bildirim verilmesini istemiyorsanız bildirimleri devre dışı abilirsiniz. (Örneğin, güncelleştirmeleri merkezi bir yazılım dağıtım mekanizması aracılığıyla teslim ediyorsanız bildirimleri devre dışı bırakmak istiyor olabilirsiniz.)

::: moniker range="vs-2017"

2017 Visual Studio kayıt [](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance)defteri girdilerini özel bir kayıt defterinde depolayalı olduğundan, kayıt defterini tipik bir şekilde doğrudan düzenleyemezsiniz. Ancak, Visual Studio ayarları `vsregedit.exe` değiştirmek için kullanabileceğiniz bir yardımcı Visual Studio içerir. Aşağıdaki komutla bildirimleri kapatabilirsiniz:

```shell
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

Aşağıdaki komutla bildirimleri yeniden açabilirsiniz:

```shell
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 1
```

Varsayılan davranışa geri dönmek için aşağıdaki komutla değeri de silebilirsiniz:

```shell
vsregedit.exe remove "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override
```

Ayarları değiştirmek için komutunu çalıştırarak Visual Studio başlatmayı Visual Studio. Zaten çalışan tüm Visual Studio örnekleri, Visual Studio ve yeniden başlatana kadar davranışı değiştirmez. Başka bir seçenek olarak, ayarın etkin olduğundan emin olmak için bilgisayarı yeniden başlatabilirsiniz.

Aşağıdaki komutla ayarı onaylayın:

```shell
vsregedit.exe read "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword
```

Değer yoksa (varsayılan olarak bu koşuldur), önceki komut değeri okumanın başarısız olduğunu belirtecek. Değeri ayarlarsanız, önceki komut Visual Studio yapılandırmasında değeri yansıtacak (0 veya 1 ya da olarak ayarlanmış herhangi bir değeri gösterir; yalnızca 0 veya 1 beklenir).

::: moniker-end

::: moniker range="vs-2019"

2019 Visual Studio kayıt [](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance)defteri girdilerini özel bir kayıt defterinde depolayalı olduğundan, kayıt defterini tipik bir şekilde doğrudan düzenleyemezsiniz. Ancak, Visual Studio ayarları `vsregedit.exe` değiştirmek için kullanabileceğiniz bir yardımcı Visual Studio içerir. Aşağıdaki komutla bildirimleri kapatabilirsiniz:

```shell
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

Aşağıdaki komutla bildirimleri yeniden açabilirsiniz:

```shell
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 1
```

Varsayılan davranışa geri dönmek için aşağıdaki komutla değeri de silebilirsiniz:

```shell
vsregedit.exe remove "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override
```

Ayarları değiştirmek için komutunu çalıştırarak Visual Studio başlatmayı Visual Studio. Zaten çalışan tüm Visual Studio örnekleri, Visual Studio ve yeniden başlatana kadar davranışı değiştirmez. Başka bir seçenek olarak, ayarın etkin olduğundan emin olmak için bilgisayarı yeniden başlatabilirsiniz.

Aşağıdaki komutla ayarı onaylayın:

```shell
vsregedit.exe read "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword
```

Değer yoksa (varsayılan olarak bu koşuldur), önceki komut değeri okumanın başarısız olduğunu belirtecek. Değeri ayarlarsanız, önceki komut Visual Studio yapılandırmasında değeri yansıtacak (0 veya 1 ya da olarak ayarlanmış herhangi bir değeri gösterir; yalnızca 0 veya 1 beklenir).

::: moniker-end

::: moniker range=">=vs-2022"

2022 Visual Studio kayıt defteri girdilerini özel bir kayıt defterinde depolayalı [olduğundan,](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance)kayıt defterini tipik bir şekilde doğrudan düzenleyemezsiniz. Ancak, Visual Studio ayarları `vsregedit.exe` değiştirmek için kullanabileceğiniz bir yardımcı Visual Studio içerir. Aşağıdaki komutla bildirimleri kapatabilirsiniz:

```shell
vsregedit.exe set "C:\Program Files\Microsoft Visual Studio\2022\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

Aşağıdaki komutla bildirimleri yeniden açabilirsiniz:

```shell
vsregedit.exe set "C:\Program Files\Microsoft Visual Studio\2022\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 1
```

Varsayılan davranışa geri dönmek için aşağıdaki komutla değeri de silebilirsiniz:

```shell
vsregedit.exe remove "c:\Program Files\Microsoft Visual Studio\2022\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override
```

Ayarları değiştirmek için komutunu çalıştırarak Visual Studio başlatmayı Visual Studio. Zaten çalışan tüm Visual Studio örnekleri, Visual Studio ve yeniden başlatana kadar davranışı değiştirmez. Başka bir seçenek olarak, ayarın etkin olduğundan emin olmak için bilgisayarı yeniden başlatabilirsiniz.

Aşağıdaki komutla ayarı onaylayın:

```shell
vsregedit.exe read "c:\Program Files\Microsoft Visual Studio\2022\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword
```

Değer yoksa (varsayılan olarak bu koşuldur), önceki komut değeri okumanın başarısız olduğunu belirtecek. Değeri ayarlarsanız, önceki komut Visual Studio yapılandırmasında değeri yansıtacak (0 veya 1 ya da olarak ayarlanmış herhangi bir değeri gösterir; yalnızca 0 veya 1 beklenir).

::: moniker-end

(Dizini düzenlemek istediğiniz yüklü örnekle eş olacak şekilde değiştir emin olun.)

> [!TIP]
> İstemci [vswhere.exe](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances) iş istasyonunda belirli bir Visual Studio örneğini bulmak için Visual Studio kullanın.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'yu yükleme](install-visual-studio.md)
- [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
- [Yönetici güncelleştirmelerini uygulama](applying-administrator-updates.md)
- [Paket önbelleğini devre dışı bırakma veya taşıma](disable-or-move-the-package-cache.md)
- [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
