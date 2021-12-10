---
title: Kurumsal dağıtımlar için Varsayılanları Ayarla
description: Visual Studio kurumsal dağıtımlarına yönelik etki alanı ilkeleri ve diğer yapılandırma işlemleri hakkında bilgi edinin.
ms.date: 12/7/2021
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
ms.openlocfilehash: 69546bac8ae47916a49b7d5bb6ae6076a0f2b5a0
ms.sourcegitcommit: 99e0146dfe742f6d1955b9415a89c3d1b8afe4e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2021
ms.locfileid: "134553875"
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
| `AdministratorUpdatesEnabled`    | `REG_DWORD`                 | 0                                                   | İstemci bilgisayara yönetici güncelleştirmelerinin uygulanmasını sağlar. Bu değer eksikse veya 0 olarak ayarlandıysa, yönetici güncelleştirmeleri engellenir. Bu değer, yönetim kullanımı içindir. Daha fazla bilgi için bkz. [yönetici güncelleştirmelerini etkinleştirme](enabling-administrator-updates.md). |
| `AdministratorUpdatesOptOut`     | `REG_DWORD`                 | 0                                                   | Kullanıcının Visual Studio için yönetici güncelleştirmelerini almak istediğini belirtir. kayıt defteri değerinin yokluğu veya 0 kümesi değeri, Visual Studio kullanıcının Visual Studio için yönetici güncelleştirmelerini almak istediği anlamına gelir. Bu geliştirici kullanıcısına yöneliktir (istemci makinesinde yönetici izinleri varsa). Daha fazla bilgi için bkz. [yönetici güncelleştirmelerini uygulama](../install/applying-administrator-updates.md#understanding-configuration-options). |
| `UpdateConfigurationFile`        | `REG_SZ` veya `REG_EXPAND_SZ` | ProgramData<br>\Microsoft<br>\VisualStudio<br>\updates.config | Yönetim güncelleştirmelerini yapılandırmak için dosya yolu. Daha fazla bilgi için bkz. [yönetici güncelleştirmesi yapılandırma yöntemleri](../install/applying-administrator-updates.md#methods-for-configuring-an-administrator-update).   |    

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="configuring-source-location-for-updates"></a>Güncelleştirmeler için kaynak konumu yapılandırma 

Bu bölümdeki ayarlar, bir yöneticinin hangi güncelleştirme kanallarının kullanılabilir olduğunu ve kurumsal bir kuruluştaki istemcilere nasıl göründüğünü denetlemesine olanak tanır. Güncelleştirme ayarlarının ne olduğu ve nasıl çalıştıkları hakkında daha fazla bilgi için [güncelleştirmelerin kaynak konumunu yapılandırma](update-visual-studio.md#configure-source-location-of-updates-1) belgelerine bakın. 
bu işlevsellik, istemcinin Visual Studio 2022 yükleyicisini kullanmasını ve 10 kasım 2021 tarihinde veya sonrasında gönderilen 2019 önyükleyici sürümünü kullanmasını gerektirir. bu işlemi etkinleştirme kılavuzu, [istemci makinelerinizdeki Visual Studio 2022 yükleyicisini Visual Studio 2019 düzen belgeleri aracılığıyla nasıl edinebilirim?](create-a-network-installation-of-visual-studio.md#configure-the-layout-to-always-include-and-provide-the-latest-installer)

Bu bölümdeki anahtarlar yalnızca Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup\registry yolu için geçerlidir

| **Ad**                         | **Tür**                    | **Açıklama**                                                |
|----------------------------------|-----------------------------|-----------------------------------------------------|
| `Channels` | `Key` |  Özel düzen kanalı bilgilerini depolamak için alt anahtar yolu. Bu anahtarın adı kanal adı olarak değerlendirilir ve [güncelleştirme kanalı açılır](/visualstudio/install/update-visual-studio?#configure-source-location-of-updates-1)listesinde gösterilir. `ChannelURI`Değer, alt anahtar altında bulunması gerekir `Channels` . |
| `DisabledChannels` | `Key` | Kanal gizleme iletişim kutusunda kanalların görüntülenmesini önlemek için alt anahtar yolu. Kanal burada tanımlanmışsa (değeri ile birlikte `ChannelURI` ), iletişim kutusunda filtre uygulanır. |
| `ChannelURI` | `REG_SZ` |  Hive 'e ekleyerek kanal değerlerinin güncelleştirilmesi `Channels` veya `DisabledChannels` kayıt defteri kovanına ekleyerek güncelleştirme kanalları listesinden gizlemek Için channeluri. Microsoft tarafından barındırılan kanallar için, channelURI " https://aka.ms/vs/16/release/channel " veya " https://aka.ms/vs/16/pre/channel " olur.  Düzenler için, bu değerin düzenin ChannelManifest. json ' a işaret olması gerekir. Aşağıdaki örneklere bakın. |
| `Description` | `REG_SZ` |  Kanalın iki satırlık özel açıklaması. bir düzenden zaten yüklediyseniz, güncelleştirme Ayarlar kullanıcı arabirimi varsayılan olarak "özel kanal" olarak değişir ve bu açıklamayı kullanarak değiştirebilirsiniz. |


aşağıda, bir bt yöneticisinin [güncelleştirme Ayarlar kullanıcı arabirimini](/visualstudio/install/update-visual-studio?#configure-source-location-of-updates-1)nasıl özelleştirmek istediğini gösteren iki örnek kayıt defteri dosyası verilmiştir. 

İlk kayıt defteri örneği, istemcisinin daha önce konumunda bulunan bir ağ düzeninden yüklendiği bir durumda kullanılabilir `\\vslayoutserver3\vs\2019_Enterprise` . daha önce belirtildiği gibi, bu düzenin kanal adını varsayılan olarak "özel kanal" olarak Visual Studio. Bu düzen için kanal adını ve açıklamasını nasıl özelleştireceğiniz aşağıda verilmiştir.

```example registry file
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup\Channels]

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup\Channels\More meaningful name of my existing layout]
"channelUri"="\\\\vslayoutserver3\\vs\\2019_Enterprise\\ChannelManifest.json"
"Description"="Dev Tools based on VS 2019 16.9.Spring.2020 servicing baseline"
```


Güncelleştirmeler için kaynak olarak kullanılabilir olan diğer özel güncelleştirme kanalları için daha fazla düzen girişi ekleme ve ayrıca önizleme kanalının görüntülenmesini engelleme.

```example registry file
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup\Channels]

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

## <a name="controlling-notifications-in-the-visual-studio-ide"></a>Visual Studio ıde 'de bildirimleri denetleme

::: moniker range="vs-2017"

daha önce açıklandığı gibi, herhangi bir güncelleştirmenin kullanılabilir olup olmadığını görmek için, bir ağ veya internet gibi yüklendiği konumu kontrol Visual Studio. bir güncelleştirme kullanılabilir olduğunda, kullanıcıya pencerenin sağ üst köşesinde bir bildirim bayrağı bildiren Visual Studio.

   ![Güncelleştirmeler için bildirim bayrağı](media/notification-flag.png)

::: moniker-end

::: moniker range=">=vs-2019"

daha önce açıklandığı gibi, herhangi bir güncelleştirmenin kullanılabilir olup olmadığını görmek için, bir ağ veya internet gibi yüklendiği konumu kontrol Visual Studio. bir güncelleştirme kullanılabilir olduğunda Visual Studio, kullanıcıya pencerenin sağ alt köşesinde bir bildirim simgesiyle bildirir.

   ![Visual Studio ıde 'deki bildirim simgesi](media/vs-2019/notification-bar.png "Visual Studio ıde 'deki bildirim simgesi")

::: moniker-end

Son kullanıcılara güncelleştirmelerin bildirilmesini istemiyorsanız bildirimleri devre dışı bırakabilirsiniz. (Örneğin, güncelleştirmeleri merkezi bir yazılım dağıtım mekanizması üzerinden sunmanız durumunda bildirimleri devre dışı bırakmak isteyebilirsiniz.)

::: moniker range="vs-2017"

Visual Studio 2017, [kayıt defteri girişlerini özel bir kayıt defterine depoladığından](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), kayıt defterini normal şekilde doğrudan düzenleyemezsiniz. ancak Visual Studio, `vsregedit.exe` Visual Studio ayarları değiştirmek için kullanabileceğiniz bir yardımcı program içerir. Aşağıdaki komutla bildirimleri devre dışı bırakabilirsiniz:

```shell
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

Aşağıdaki komutla bildirimleri yeniden açabilirsiniz:

```shell
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 1
```

Varsayılan davranışa geri dönmek için değeri aşağıdaki komutla de silebilirsiniz:

```shell
vsregedit.exe remove "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override
```

Visual Studio ayarlarını değiştirmek için komutunu çalıştırdıktan sonra, Visual Studio başlatın. zaten çalışan Visual Studio örnekleri, Visual Studio kapatılıp yeniden başlatılana kadar davranış değiştirmez. Başka bir seçenek olarak, ayarın geçerli olduğundan emin olmak için bilgisayarı yeniden başlatabilirsiniz.

Aşağıdaki komutla ayarı doğrulayabilirsiniz:

```shell
vsregedit.exe read "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword
```

Değer yoksa (varsayılan olarak bu durumdur), önceki komut değeri okuyamayacağı anlamına gelir. değeri ayarlarsanız, önceki komut Visual Studio yapılandırmasındaki değeri yansıtır (0 veya 1 veya olarak ayarlanan herhangi bir değer – yalnızca 0 ya da 1 beklenir).

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 2019, [kayıt defteri girişlerini özel bir kayıt defterine depoladığından](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), kayıt defterini normal şekilde doğrudan düzenleyemezsiniz. ancak Visual Studio, `vsregedit.exe` Visual Studio ayarları değiştirmek için kullanabileceğiniz bir yardımcı program içerir. Aşağıdaki komutla bildirimleri devre dışı bırakabilirsiniz:

```shell
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

Aşağıdaki komutla bildirimleri yeniden açabilirsiniz:

```shell
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 1
```

Varsayılan davranışa geri dönmek için değeri aşağıdaki komutla de silebilirsiniz:

```shell
vsregedit.exe remove "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override
```

Visual Studio ayarlarını değiştirmek için komutunu çalıştırdıktan sonra, Visual Studio başlatın. zaten çalışan Visual Studio örnekleri, Visual Studio kapatılıp yeniden başlatılana kadar davranış değiştirmez. Başka bir seçenek olarak, ayarın geçerli olduğundan emin olmak için bilgisayarı yeniden başlatabilirsiniz.

Aşağıdaki komutla ayarı doğrulayabilirsiniz:

```shell
vsregedit.exe read "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword
```

Değer yoksa (varsayılan olarak bu durumdur), önceki komut değeri okuyamayacağı anlamına gelir. değeri ayarlarsanız, önceki komut Visual Studio yapılandırmasındaki değeri yansıtır (0 veya 1 veya olarak ayarlanan herhangi bir değer – yalnızca 0 ya da 1 beklenir).

::: moniker-end

::: moniker range=">=vs-2022"

Visual Studio 2022, [kayıt defteri girişlerini özel bir kayıt defterine depoladığından](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), kayıt defterini normal şekilde doğrudan düzenleyemezsiniz. ancak Visual Studio, `vsregedit.exe` Visual Studio ayarları değiştirmek için kullanabileceğiniz bir yardımcı program içerir. Aşağıdaki komutla bildirimleri devre dışı bırakabilirsiniz:

```shell
vsregedit.exe set "C:\Program Files\Microsoft Visual Studio\2022\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

Aşağıdaki komutla bildirimleri yeniden açabilirsiniz:

```shell
vsregedit.exe set "C:\Program Files\Microsoft Visual Studio\2022\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 1
```

Varsayılan davranışa geri dönmek için değeri aşağıdaki komutla de silebilirsiniz:

```shell
vsregedit.exe remove "c:\Program Files\Microsoft Visual Studio\2022\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override
```

Visual Studio ayarlarını değiştirmek için komutunu çalıştırdıktan sonra, Visual Studio başlatın. zaten çalışan Visual Studio örnekleri, Visual Studio kapatılıp yeniden başlatılana kadar davranış değiştirmez. Başka bir seçenek olarak, ayarın geçerli olduğundan emin olmak için bilgisayarı yeniden başlatabilirsiniz.

Aşağıdaki komutla ayarı doğrulayabilirsiniz:

```shell
vsregedit.exe read "c:\Program Files\Microsoft Visual Studio\2022\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword
```

Değer yoksa (varsayılan olarak bu durumdur), önceki komut değeri okuyamayacağı anlamına gelir. değeri ayarlarsanız, önceki komut Visual Studio yapılandırmasındaki değeri yansıtır (0 veya 1 veya olarak ayarlanan herhangi bir değer – yalnızca 0 ya da 1 beklenir).

::: moniker-end

(Dizini, düzenlemek istediğiniz yüklü örnekle eşleşecek şekilde değiştirdiğinizden emin olun.)

> [!TIP]
> istemci iş istasyonunda belirli bir Visual Studio örneğini bulmak için [vswhere.exe](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances) kullanın.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'yu yükleme](install-visual-studio.md)
- [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
- [Yönetici güncelleştirmeleri uygulanıyor](applying-administrator-updates.md)
- [Paket önbelleğini devre dışı bırakma veya taşıma](disable-or-move-the-package-cache.md)
- [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
