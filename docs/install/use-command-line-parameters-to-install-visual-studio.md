---
title: Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme
titleSuffix: ''
description: Komut satırı parametreleri denetlemek veya Visual Studio yüklemenizi özelleştirmek için kullanmayı öğrenin.
ms.date: 10/22/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 7210a2834dda749cfe1d89b9093cd627b7c0ae1b
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114364"
---
# <a name="use-command-line-parameters-to-install-visual-studio"></a>Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme

Visual Studio 'Yu bir komut isteminden yüklediğinizde, yüklemeyi denetlemek veya özelleştirmek için çeşitli komut satırı parametrelerini kullanabilirsiniz. Komut satırından aşağıdaki eylemleri gerçekleştirebilirsiniz:

- Yükleme önceden belirli seçenekleri ile başlayın.
- Yükleme işlemini otomatik hale getirin.
- Daha sonra kullanmak için yükleme dosyalarından oluşan bir önbellek (Düzen) oluşturun.

Komut satırı seçenekleri, yükleme işlemini başlatan küçük (1 MB) dosya olan kurulum Önyükleyicisi ile birlikte kullanılır. Önyükleyici Visual Studio sitesinden indirdiğinizde başlatıldığında ilk yürütülebilir ' dir.

::: moniker range="vs-2017"

Visual Studio 2017 için bir önyükleyici almak üzere, bunun nasıl yapılacağı hakkında ayrıntılı bilgi için [**Visual Studio önceki sürümler**](https://visualstudio.microsoft.com/vs/older-downloads/) indirme sayfasına bakın.

::: moniker-end

::: moniker range="vs-2019"

Doğrudan bir bağlantı için en son sürüm önyükleyici için yüklemekte olduğunuz ürün sürümünü almak için aşağıdaki bağlantıları kullanın:

- [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)
- [Visual Studio 2019 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)
- [Visual Studio 2019 Community](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)

::: moniker-end


Önyükleyici dosyanızın eşleşmesi veya aşağıdaki dosya adlarından birine benzer olması gerekir:

* vs_enterprise.exe
* vs_professional.exe
* vs_community.exe

>[!TIP]
>Daha önce bir önyükleyici dosyası indirdiyseniz ve sürümünü doğrulamak istiyorsanız, bunun nasıl yapıldığını burada bulabilirsiniz. Windows 'ta dosya Gezgini 'ni açın, önyükleyici dosyasına sağ tıklayın, **Özellikler**' i seçin, **Ayrıntılar** sekmesini seçin ve ardından **ürün sürümü** numarasını görüntüleyin. Bu numarayı bir Visual Studio sürümüyle eşleştirmek için bkz. [Visual Studio derleme numaraları ve sürüm tarihleri](visual-studio-build-numbers-and-release-dates.md) sayfası.

## <a name="command-line-parameters"></a>Komut satırı parametreleri

 Visual Studio komut satırı parametreleri büyük/küçük harfe duyarsızdır.

> Sözdizimi: `vs_enterprise.exe [command] <options>...`

`vs_enterprise.exe`, yüklemekte olduğunuz ürün sürümüne uygun şekilde değiştirin. (Alternatif olarak, `vs_installer.exe`de kullanabilirsiniz.)

>[!TIP]
> Visual Studio 'Yu yüklemek için komut satırını kullanma hakkında daha fazla örnek için, [komut satırı parametre örnekleri](command-line-parameter-examples.md) sayfasına bakın.

::: moniker range="vs-2017"

| **Komutu** | **Açıklama** |
| ----------------------- | --------------- |
| (boş) | Ürün yükler. |
| `modify` | Yüklü bir ürün değiştirir. |
| `update` | Yüklü bir ürün güncelleştirir. |
| `repair` | Yüklü bir ürün onarır. |
| `uninstall` | Yüklü bir ürün kaldırır. |
| `export` | **Sürüm 15,9 ' de yeni**: yükleme seçimini bir yükleme yapılandırma dosyasına aktarır. **Note**: yalnızca vs_installer. exe ile kullanılabilir. |

::: moniker-end

::: moniker range="vs-2019"

| **Komutu** | **Açıklama** |
| ----------------------- | --------------- |
| (boş) | Ürün yükler. |
| `modify` | Yüklü bir ürün değiştirir. |
| `update` | Yüklü bir ürün güncelleştirir. |
| `repair` | Yüklü bir ürün onarır. |
| `uninstall` | Yüklü bir ürün kaldırır. |
| `export` | Yükleme seçimini bir yükleme yapılandırma dosyasına aktarır. **Note**: yalnızca vs_installer. exe ile kullanılabilir. |

::: moniker-end

## <a name="install-options"></a>Seçenekleri yükler

::: moniker range="vs-2017"

| **Yükleme seçeneği** | **Açıklama** |
| ----------------------- | --------------- |
| `--installPath <dir>` | Yükleme dizini örneği üzerinde işlem yapmak için. Yükleme komutu için budur **isteğe bağlı** ve örneğin yüklü olduğu. Diğer komutlar için budur **gerekli** ve önceden yüklenmiş örnek yüklendiği. |
| `--addProductLang <language-locale>` | **İsteğe bağlı**: bir yükleme sırasında veya değiştirme işlemi, bu ürünü yüklü UI dil paketlerini belirler. Bu, birden çok dil paketlerini eklemek için komut satırında birden çok kez görünebilir. Yoksa, yükleme makine yerel ayarı kullanır. Daha fazla bilgi için [dil yerel ayarlar listesini](#list-of-language-locales) bu sayfadaki bölümü.|
| `--removeProductLang <language-locale>` | **İsteğe bağlı**: bir yükleme sırasında veya değiştirme işlemi, bu ürün kaldırılacak kullanıcı Arabirimi dil paketlerini belirler. Bu, birden çok dil paketlerini eklemek için komut satırında birden çok kez görünebilir. Daha fazla bilgi için [dil yerel ayarlar listesini](#list-of-language-locales) bu sayfadaki bölümü.|
| `--add <one or more workload or component IDs>` | **İsteğe bağlı**: bir veya daha fazla iş yükü veya Bileşen kimlikleri eklemek için. Yapıtın gerekli bileşenleri, değil önerilen veya isteğe bağlı bileşenler yüklenir. Genel olarak aracılığıyla ek bileşenler denetleyebilirsiniz `--includeRecommended` ve/veya `--includeOptional`. Birden çok iş yükleri veya bileşenleri eklemek için yineleyin `--add` komutu (örneğin, `--add Workload1 --add Workload2`). Daha ayrıntılı denetim için eklediğiniz `;includeRecommended` veya `;includeOptional` kimliği (örneğin, `--add Workload1;includeRecommended` veya `--add Workload2;includeRecommended;includeOptional`). Daha fazla bilgi için [iş yükü ve Bileşen kimlikleri](workload-and-component-ids.md) sayfası. Bu seçenek gerekli olarak yineleyebilir.|
| `--remove <one or more workload or component IDs>` | **İsteğe bağlı**: bir veya daha fazla iş yükü veya Bileşen kimlikleri kaldırmak için. Daha fazla bilgi için müşterilerimize [iş yükü ve Bileşen kimlikleri](workload-and-component-ids.md) sayfası. Bu seçenek gerekli olarak yineleyebilir.|
| `--in <path>` | **İsteğe bağlı**: URI veya bir yanıt dosyasının yolu.  |
| `--all` | **İsteğe bağlı**: tüm iş yüklerinin ve bileşenlerin bir ürünün yükleneceğini. |
| `--allWorkloads` | **İsteğe bağlı**: tüm iş yüklerinin ve bileşenlerin, hiçbir önerilen veya isteğe bağlı bileşenleri yükler. |
| `--includeRecommended` | **İsteğe bağlı**: yüklü olan tüm iş yükleri için önerilen bileşenleri, ancak isteğe bağlı bileşenler içerir. Belirtilen iş yükleri ile birlikte `--allWorkloads` veya `--add`. |
| `--includeOptional` | **İsteğe bağlı**: isteğe bağlı bileşenler yüklü olan tüm iş yükleri için ancak önerilen bileşenleri içerir. Belirtilen iş yükleri ile birlikte `--allWorkloads` veya `--add`.  |
| `--quiet, -q` | **Isteğe bağlı**: yüklemeyi gerçekleştirirken hiçbir Kullanıcı arabirimini görüntülememe. |
| `--passive, -p` | **Isteğe bağlı**: Kullanıcı arabirimini görüntüleme, ancak kullanıcıdan herhangi bir etkileşim isteme. |
| `--norestart` | **Isteğe bağlı**: varsa, `--passive` veya `--quiet` olan komutlar makineyi otomatik olarak yeniden başlatmaz (gerekliyse).  Bu ne sayılır `--passive` ya da `--quiet` belirtilir.  |
| `--nickname <name>` | **İsteğe bağlı**: Bu takma ad atamak için yüklü bir ürün için tanımlar. Takma ad 10 karakterden uzun olamaz.  |
| `--productKey` | **İsteğe bağlı**: Bu ürün anahtarı yüklü bir ürün için tanımlar. Bu, `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` ya da `xxxxxxxxxxxxxxxxxxxxxxxxx`biçimde 25 alfasayısal karakterden oluşur. |
| `--help, --?, -h, -?` | Bu sayfanın çevrimdışı bir sürümünü görüntüler. |
| `--config <path>` | **İsteğe bağlı** ve **15.9 yeni**: bir yükleme sırasında veya değiştirme işlemi, bu iş yükleri belirler ve bileşenleri eklemek için temel bir önceden kaydedilmiş yükleme yapılandırma dosyası. Bu işlem eklenebilir ve dosyada yoksa herhangi bir iş yükünü veya bileşeni kaldırmaz. Ayrıca, ürüne uygulanmayacak öğeler eklenmez. Dışa aktarma işlemi sırasında bu yükleme yapılandırma dosyasını kaydetmek istediğiniz konumu belirler. |

::: moniker-end

::: moniker range="vs-2019"

| **Yükleme seçeneği** | **Açıklama** |
| ----------------------- | --------------- |
| `--installPath <dir>` | Yükleme dizini örneği üzerinde işlem yapmak için. Yükleme komutu için budur **isteğe bağlı** ve örneğin yüklü olduğu. Diğer komutlar için budur **gerekli** ve önceden yüklenmiş örnek yüklendiği. |
| `--addProductLang <language-locale>` | **İsteğe bağlı**: bir yükleme sırasında veya değiştirme işlemi, bu ürünü yüklü UI dil paketlerini belirler. Bu, birden çok dil paketlerini eklemek için komut satırında birden çok kez görünebilir. Yoksa, yükleme makine yerel ayarı kullanır. Daha fazla bilgi için [dil yerel ayarlar listesini](#list-of-language-locales) bu sayfadaki bölümü.|
| `--removeProductLang <language-locale>` | **İsteğe bağlı**: bir yükleme sırasında veya değiştirme işlemi, bu ürün kaldırılacak kullanıcı Arabirimi dil paketlerini belirler. Bu, birden çok dil paketlerini eklemek için komut satırında birden çok kez görünebilir. Daha fazla bilgi için [dil yerel ayarlar listesini](#list-of-language-locales) bu sayfadaki bölümü.|
| `--add <one or more workload or component IDs>` | **İsteğe bağlı**: bir veya daha fazla iş yükü veya Bileşen kimlikleri eklemek için. Yapıtın gerekli bileşenleri, değil önerilen veya isteğe bağlı bileşenler yüklenir. Genel olarak aracılığıyla ek bileşenler denetleyebilirsiniz `--includeRecommended` ve/veya `--includeOptional`. Birden çok iş yükleri veya bileşenleri eklemek için yineleyin `--add` komutu (örneğin, `--add Workload1 --add Workload2`). Daha ayrıntılı denetim için eklediğiniz `;includeRecommended` veya `;includeOptional` kimliği (örneğin, `--add Workload1;includeRecommended` veya `--add Workload2;includeRecommended;includeOptional`). Daha fazla bilgi için [iş yükü ve Bileşen kimlikleri](workload-and-component-ids.md) sayfası. Bu seçenek gerekli olarak yineleyebilir.|
| `--remove <one or more workload or component IDs>` | **İsteğe bağlı**: bir veya daha fazla iş yükü veya Bileşen kimlikleri kaldırmak için. Daha fazla bilgi için müşterilerimize [iş yükü ve Bileşen kimlikleri](workload-and-component-ids.md) sayfası. Bu seçenek gerekli olarak yineleyebilir.|
| `--in <path>` | **İsteğe bağlı**: URI veya bir yanıt dosyasının yolu.  |
| `--all` | **İsteğe bağlı**: tüm iş yüklerinin ve bileşenlerin bir ürünün yükleneceğini. |
| `--allWorkloads` | **İsteğe bağlı**: tüm iş yüklerinin ve bileşenlerin, hiçbir önerilen veya isteğe bağlı bileşenleri yükler. |
| `--includeRecommended` | **İsteğe bağlı**: yüklü olan tüm iş yükleri için önerilen bileşenleri, ancak isteğe bağlı bileşenler içerir. Belirtilen iş yükleri ile birlikte `--allWorkloads` veya `--add`. |
| `--includeOptional` | **İsteğe bağlı**: isteğe bağlı bileşenler yüklü olan tüm iş yükleri için ancak önerilen bileşenleri içerir. Belirtilen iş yükleri ile birlikte `--allWorkloads` veya `--add`.  |
| `--quiet, -q` | **Isteğe bağlı**: yüklemeyi gerçekleştirirken hiçbir Kullanıcı arabirimini görüntülememe. |
| `--passive, -p` | **Isteğe bağlı**: Kullanıcı arabirimini görüntüleme, ancak kullanıcıdan herhangi bir etkileşim isteme. |
| `--norestart` | **Isteğe bağlı**: varsa, `--passive` veya `--quiet` olan komutlar makineyi otomatik olarak yeniden başlatmaz (gerekliyse).  Bu ne sayılır `--passive` ya da `--quiet` belirtilir.  |
| `--nickname <name>` | **İsteğe bağlı**: Bu takma ad atamak için yüklü bir ürün için tanımlar. Takma ad 10 karakterden uzun olamaz.  |
| `--productKey` | **İsteğe bağlı**: Bu ürün anahtarı yüklü bir ürün için tanımlar. Bu, `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` ya da `xxxxxxxxxxxxxxxxxxxxxxxxx`biçimde 25 alfasayısal karakterden oluşur. |
| `--help, --?, -h, -?` | Bu sayfanın çevrimdışı bir sürümünü görüntüler. |
| `--config <path>` | **Isteğe bağlı**: yükleme veya değiştirme işlemi sırasında, daha önce kaydedilen bir yükleme yapılandırma dosyasına göre eklenecek iş yüklerini ve bileşenleri belirler. Bu işlem eklenebilir ve dosyada yoksa herhangi bir iş yükünü veya bileşeni kaldırmaz. Ayrıca, ürüne uygulanmayacak öğeler eklenmez. Dışa aktarma işlemi sırasında bu yükleme yapılandırma dosyasını kaydetmek istediğiniz konumu belirler. |

::: moniker-end

> [!IMPORTANT]
> Birden çok iş yükü ve bileşen belirtirken, her öğe için `--add` veya `--remove` komut satırı anahtarını tekrarlamanız gerekir.

## <a name="layout-options"></a>Düzen seçenekleri

::: moniker range="vs-2017"

| **Düzen Seçenekleri** | **Açıklama** |
| ----------------------- | --------------- |
| `--layout <dir>` | Yükleme önbelleği çevrimdışı oluşturmak için bir dizini belirtir. Daha fazla bilgi için [Visual Studio'nun ağ tabanlı yüklemesini oluşturma](create-a-network-installation-of-visual-studio.md).|
| `--lang <one or more language-locales>` | **İsteğe bağlı**: ile kullanılan `--layout` hazırlamak için çevrimdışı önbellek ile yükleme kaynak paketleri ile belirtilen diller. Daha fazla bilgi için [dil yerel ayarlar listesini](#list-of-language-locales) bu sayfadaki bölümü.|
| `--add <one or more workload or component IDs>` | **İsteğe bağlı**: bir veya daha fazla iş yükü veya Bileşen kimlikleri eklemek için. Yapıtın gerekli bileşenleri, değil önerilen veya isteğe bağlı bileşenler yüklenir. Genel olarak aracılığıyla ek bileşenler denetleyebilirsiniz `--includeRecommended` ve/veya `--includeOptional`. Daha ayrıntılı denetim için eklediğiniz `;includeRecommended` veya `;includeOptional` kimliği (örneğin, `--add Workload1;includeRecommended` veya `--add Workload2;includeOptional`). Daha fazla bilgi için [iş yükü ve Bileşen kimlikleri](workload-and-component-ids.md) sayfası. <br/>**Not**: varsa `--add` olan kullanıldığında, yalnızca belirtilen iş yükleri ve bileşenleri ve bunların bağımlılıklarını karşıdan yüklenir. `--add` belirtilmemişse, tüm iş yükleri ve bileşenler düzene indirilir.|
| `--includeRecommended` | **İsteğe bağlı**: yüklü olan tüm iş yükleri için önerilen bileşenleri, ancak isteğe bağlı bileşenler içerir. Belirtilen iş yükleri ile birlikte `--allWorkloads` veya `--add`. |
| `--includeOptional` | **İsteğe bağlı**: önerilen içerir *ve* düzende tüm iş yükleri için isteğe bağlı bileşenler. İş yükleri ile belirtilen `--add`.  |
| `--keepLayoutVersion` | **15.3, isteğe bağlı olarak yeni**: Düzen sürümüne güncelleştirmeden düzene değişiklikleri uygulayın. |
| `--verify` | **15.3, isteğe bağlı olarak yeni**: bir düzen içeriğini doğrulayın. Herhangi bir bozuk veya eksik dosyalar listelenir. |
| `--fix` | **15.3, isteğe bağlı olarak yeni**: bir düzen içeriğini doğrulayın. Herhangi bir dosya bozuksa veya eksikse, bunlar yeniden indirilir. Bir düzen düzeltmek için Internet erişimi gerekir. |
| `--clean <one or more paths to catalogs>` | **15.3, isteğe bağlı olarak yeni**: yeni bir sürüme güncelleştiren bir düzenden eski sürümlerini bileşenleri kaldırır. |

| **Gelişmiş yükleme seçenekleri** | **Açıklama** |
| ----------------------- | --------------- |
| `--channelId <id>` | **İsteğe bağlı**: kanal örneği için yüklenecek kimliği. Bu, install komutu için gereklidir ve `--installPath` belirtilmişse diğer komutlar için yok sayılır. |
| `--channelUri <uri>` | **İsteğe bağlı**: kanal bildirimi, URI. Güncelleştirmeler istenmemişse, `--channelUri` var olmayan bir dosyaya işaret edebilir (örneğin,--channelUri C:\atanntexist.chman). Bu, install komutu için kullanılabilir; diğer komutlar için yok sayılır. |
| `--installChannelUri <uri>` | **İsteğe bağlı**: kanal bildiriminin yüklenmesi için kullanılacak URI. URI tarafından belirtilen `--channelUri` (olması gereken belirtilen `--installChannelUri` belirtilir) güncelleştirmeleri algılamak için kullanılır. Bu, install komutu için kullanılabilir; diğer komutlar için yok sayılır. |
| `--installCatalogUri <uri>` | **İsteğe bağlı**: Katalog bildiriminin yüklenmesi için kullanılacak URI. Belirtilmişse, kanal Yöneticisi, yükleme kanal bildiriminde URI'yi kullanmadan önce bu URI'den Kataloğu bildirimi indirmeyi dener. Bu parametre, daha önce indirilip ürün kataloğu ile Düzen önbelleği oluşturulacağı çevrimdışı yükleme desteği için kullanılır. Bu, install komutu için kullanılabilir; diğer komutlar için yok sayılır. |
| `--productId <id>` | **İsteğe bağlı** yüklenecek örneği için ürün kimliği. Bu, normal yükleme koşullarında önceden doldurulur. |
| `--wait` | **İsteğe bağlı**: İşlem çıkış kodu döndürmeden önce yükleme tamamlanana kadar bekler. Bir yükleme dönüş kodu, işlemek için tamamlanması için beklemesi gereken yere otomatikleştirerek yüklemelerine istediğinizde yararlıdır. |
| `--locale <language-locale>` | **İsteğe bağlı**: yükleyici için kullanıcı arabirimi görüntüleme dilini değiştirin. Ayarı kalıcıdır. Daha fazla bilgi için [dil yerel ayarlar listesini](#list-of-language-locales) bu sayfadaki bölümü.|
| `--cache` | **15.2, isteğe bağlı olarak yeni**: varsa, paketler için sonraki onarım yüklendikten sonra tutulacak. Bu, sonraki yükler, onarır veya değişiklikler için kullanılacak için genel ilke ayarını geçersiz kılar. Önbellek paketleri olan varsayılan ilkedir. Bu kaldırma komutu için göz ardı edilir. Nasıl olduğunu okuyun için [devre dışı bırakın veya paket önbelleğini taşıma](disable-or-move-the-package-cache.md) daha fazla bilgi için. |
| `--nocache` | **15.2, isteğe bağlı olarak yeni**: varsa, paketler kaldıktan sonra ya da onarılması işlemlerinin hangisinin yapılacağını silinecek. Yalnızca gerekirse yeniden indirilir ve kullanıldıktan sonra yeniden silinir. Bu, sonraki yükler, onarır veya değişiklikler için kullanılacak için genel ilke ayarını geçersiz kılar. Önbellek paketleri olan varsayılan ilkedir. Bu kaldırma komutu için göz ardı edilir. Nasıl olduğunu okuyun için [devre dışı bırakın veya paket önbelleğini taşıma](disable-or-move-the-package-cache.md) daha fazla bilgi için. |
| `--noUpdateInstaller` | **15.2, isteğe bağlı olarak yeni**: varsa, sessiz belirtildiğinde kendini güncelleştirmesini yükleyici engeller. Yükleyici komutu başarısız ve yükleyici güncelleştirme gerekli olduğunda noUpdateInstaller sessiz ile belirtilmişse sıfır olmayan çıkış kodu döndürür. |
| `--noWeb` | **15,3 ' deki yenilikler, isteğe bağlı**: varsa, Visual Studio Kurulumu Visual Studio 'yu yüklemek için Düzen dizininizdeki dosyaları kullanır. Bir Kullanıcı, mizanpajda olmayan bileşenleri yüklemeye çalışırsa, kurulum başarısız olur.  Daha fazla bilgi için [ağ yüklemesinden dağıtma](create-a-network-installation-of-visual-studio.md). <br/><br/> **Önemli**: Bu anahtar, Visual Studio kurulumunun güncelleştirmeleri denetlemesini durdurmaz. Daha fazla bilgi için bkz. [ağ tabanlı Visual Studio dağıtımlarında güncelleştirmeleri denetleme](controlling-updates-to-visual-studio-deployments.md). |
| `--path <name>=<path>` | **15.7, isteğe bağlı olarak yeni**: yükleme için özel yükleme yollarını belirtmek için kullanılır. Adları paylaşılan desteklenen bir yolu, önbellek ve yükleyin. |
| `--path cache=<path>` | **15.7, isteğe bağlı olarak yeni**: belirttiğiniz yükleme dosyalarının indirileceği konumu kullanır. Bu konum yalnızca Visual Studio'nun yüklü olduğu ilk kez ayarlanabilir. Örnek: `--path cache="C:\VS\cache"` |
| `--path shared=<path>` | **15.7, isteğe bağlı olarak yeni**: yan yana Visual Studio yüklemeleri için paylaşılan dosyaları içerir. Bazıları bu ayarı geçersiz ve başka bir sürücüye yükleme sırasında bazı araçları ve SDK'lar bu sürücüdeki bir konuma yükleyin. Örnek: `--path shared="C:\VS\shared"` <br><br>Önemli: Bu yalnızca bir kez ve Visual Studio'nun yüklü olduğu ilk kez ayarlanabilir. |
| `--path install=<path>` | **15.7, isteğe bağlı olarak yeni**: eşdeğer `–-installPath`. Özellikle, `--installPath "C:\VS"` ve `--path install="C:\VS"` eşdeğerdir. Tek seferde bu komutlardan yalnızca biri kullanılabilir. |

::: moniker-end

::: moniker range="vs-2019"

| **Düzen Seçenekleri** | **Açıklama** |
| ----------------------- | --------------- |
| `--layout <dir>` | Yükleme önbelleği çevrimdışı oluşturmak için bir dizini belirtir. Daha fazla bilgi için [Visual Studio'nun ağ tabanlı yüklemesini oluşturma](create-a-network-installation-of-visual-studio.md).|
| `--lang <one or more language-locales>` | **İsteğe bağlı**: ile kullanılan `--layout` hazırlamak için çevrimdışı önbellek ile yükleme kaynak paketleri ile belirtilen diller. Daha fazla bilgi için [dil yerel ayarlar listesini](#list-of-language-locales) bu sayfadaki bölümü.|
| `--add <one or more workload or component IDs>` | **İsteğe bağlı**: bir veya daha fazla iş yükü veya Bileşen kimlikleri eklemek için. Yapıtın gerekli bileşenleri, değil önerilen veya isteğe bağlı bileşenler yüklenir. Genel olarak aracılığıyla ek bileşenler denetleyebilirsiniz `--includeRecommended` ve/veya `--includeOptional`. Daha ayrıntılı denetim için eklediğiniz `;includeRecommended` veya `;includeOptional` kimliği (örneğin, `--add Workload1;includeRecommended` veya `--add Workload2;includeOptional`). Daha fazla bilgi için [iş yükü ve Bileşen kimlikleri](workload-and-component-ids.md) sayfası. <br/>**Not**: varsa `--add` olan kullanıldığında, yalnızca belirtilen iş yükleri ve bileşenleri ve bunların bağımlılıklarını karşıdan yüklenir. `--add` belirtilmemişse, tüm iş yükleri ve bileşenler düzene indirilir.|
| `--includeRecommended` | **İsteğe bağlı**: yüklü olan tüm iş yükleri için önerilen bileşenleri, ancak isteğe bağlı bileşenler içerir. Belirtilen iş yükleri ile birlikte `--allWorkloads` veya `--add`. |
| `--includeOptional` | **İsteğe bağlı**: önerilen içerir *ve* düzende tüm iş yükleri için isteğe bağlı bileşenler. İş yükleri ile belirtilen `--add`.  |
| `--keepLayoutVersion` | **Isteğe bağlı**: düzen sürümünü güncelleştirmeden mizanpajdaki değişiklikleri uygulayın. |
| `--verify` | **Isteğe bağlı**: bir düzenin içeriğini doğrulayın. Herhangi bir bozuk veya eksik dosyalar listelenir. |
| `--fix` | **Isteğe bağlı**: bir düzenin içeriğini doğrulayın.  Herhangi bir dosya bozuksa veya eksikse, bunlar yeniden indirilir. Bir düzen düzeltmek için Internet erişimi gerekir. |
| `--clean <one or more paths to catalogs>` | **Isteğe bağlı**: daha yeni bir sürüme güncelleştirilmiş bir düzenden bileşenlerin eski sürümlerini kaldırır. |

| **Gelişmiş yükleme seçenekleri** | **Açıklama** |
| ----------------------- | --------------- |
| `--channelId <id>` | **İsteğe bağlı**: kanal örneği için yüklenecek kimliği. Bu, install komutu için gereklidir ve `--installPath` belirtilmişse diğer komutlar için yok sayılır. |
| `--channelUri <uri>` | **İsteğe bağlı**: kanal bildirimi, URI. Güncelleştirmeler istenmemişse, `--channelUri` var olmayan bir dosyaya işaret edebilir (örneğin,--channelUri C:\atanntexist.chman). Bu, install komutu için kullanılabilir; diğer komutlar için yok sayılır. |
| `--installChannelUri <uri>` | **İsteğe bağlı**: kanal bildiriminin yüklenmesi için kullanılacak URI. URI tarafından belirtilen `--channelUri` (olması gereken belirtilen `--installChannelUri` belirtilir) güncelleştirmeleri algılamak için kullanılır. Bu, install komutu için kullanılabilir; diğer komutlar için yok sayılır. |
| `--installCatalogUri <uri>` | **İsteğe bağlı**: Katalog bildiriminin yüklenmesi için kullanılacak URI. Belirtilmişse, kanal Yöneticisi, yükleme kanal bildiriminde URI'yi kullanmadan önce bu URI'den Kataloğu bildirimi indirmeyi dener. Bu parametre, daha önce indirilip ürün kataloğu ile Düzen önbelleği oluşturulacağı çevrimdışı yükleme desteği için kullanılır. Bu, install komutu için kullanılabilir; diğer komutlar için yok sayılır. |
| `--productId <id>` | **İsteğe bağlı** yüklenecek örneği için ürün kimliği. Bu, normal yükleme koşullarında önceden doldurulur. |
| `--wait` | **İsteğe bağlı**: İşlem çıkış kodu döndürmeden önce yükleme tamamlanana kadar bekler. Bir yükleme dönüş kodu, işlemek için tamamlanması için beklemesi gereken yere otomatikleştirerek yüklemelerine istediğinizde yararlıdır. |
| `--locale <language-locale>` | **İsteğe bağlı**: yükleyici için kullanıcı arabirimi görüntüleme dilini değiştirin. Ayarı kalıcıdır. Daha fazla bilgi için [dil yerel ayarlar listesini](#list-of-language-locales) bu sayfadaki bölümü.|
| `--cache` | **Isteğe bağlı**: varsa, paketler sonraki onarımlar için yüklendikten sonra saklanır. Bu, sonraki yükler, onarır veya değişiklikler için kullanılacak için genel ilke ayarını geçersiz kılar. Önbellek paketleri olan varsayılan ilkedir. Bu kaldırma komutu için göz ardı edilir. Nasıl olduğunu okuyun için [devre dışı bırakın veya paket önbelleğini taşıma](disable-or-move-the-package-cache.md) daha fazla bilgi için. |
| `--nocache` | **Isteğe bağlı**: varsa, paketler yüklendikten veya onarıldıktan sonra silinir. Yalnızca gerekirse yeniden indirilir ve kullanıldıktan sonra yeniden silinir. Bu, sonraki yükler, onarır veya değişiklikler için kullanılacak için genel ilke ayarını geçersiz kılar. Önbellek paketleri olan varsayılan ilkedir. Bu kaldırma komutu için göz ardı edilir. Nasıl olduğunu okuyun için [devre dışı bırakın veya paket önbelleğini taşıma](disable-or-move-the-package-cache.md) daha fazla bilgi için. |
| `--noUpdateInstaller` | **Isteğe bağlı**: varsa, sessiz belirtildiğinde yükleyicinin kendini güncelleştirmesini önler. Yükleyici komutu başarısız ve yükleyici güncelleştirme gerekli olduğunda noUpdateInstaller sessiz ile belirtilmişse sıfır olmayan çıkış kodu döndürür. |
| `--noWeb` | **Isteğe bağlı**: varsa, Visual Studio Kurulumu Visual Studio 'yu yüklemek için Düzen dizininizdeki dosyaları kullanır. Bir Kullanıcı, mizanpajda olmayan bileşenleri yüklemeye çalışırsa, kurulum başarısız olur.  Daha fazla bilgi için [ağ yüklemesinden dağıtma](create-a-network-installation-of-visual-studio.md). <br/><br/> **Önemli**: Bu anahtar, Visual Studio kurulumunun güncelleştirmeleri denetlemesini durdurmaz. Daha fazla bilgi için bkz. [ağ tabanlı Visual Studio dağıtımlarında güncelleştirmeleri denetleme](controlling-updates-to-visual-studio-deployments.md). **16.3.5 ' de yeni**: Bu anahtar hataları engeller ve çevrimdışı yüklemeler ve güncelleştirmeler ile performansı geliştirir.|
| `--path <name>=<path>` | **Isteğe bağlı**: yükleme için özel yükleme yollarını belirtmek için kullanılır. Adları paylaşılan desteklenen bir yolu, önbellek ve yükleyin. |
| `--path cache=<path>` | **Isteğe bağlı**: yükleme dosyalarını indirmek için belirttiğiniz konumu kullanır. Bu konum yalnızca Visual Studio'nun yüklü olduğu ilk kez ayarlanabilir. Örnek: `--path cache="C:\VS\cache"` |
| `--path shared=<path>` | **Isteğe bağlı**: yan yana Visual Studio yüklemeleri için paylaşılan dosyaları içerir. Bazıları bu ayarı geçersiz ve başka bir sürücüye yükleme sırasında bazı araçları ve SDK'lar bu sürücüdeki bir konuma yükleyin. Örnek: `--path shared="C:\VS\shared"` <br><br>Önemli: Bu yalnızca bir kez ve Visual Studio'nun yüklü olduğu ilk kez ayarlanabilir. |
| `--path install=<path>` | **Isteğe bağlı**: `–-installPath`eşdeğerdir. Özellikle, `--installPath "C:\VS"` ve `--path install="C:\VS"` eşdeğerdir. Tek seferde bu komutlardan yalnızca biri kullanılabilir. |

::: moniker-end

## <a name="list-of-workload-ids-and-component-ids"></a>İş yükü kimlikleri ve bileşen listesi

Visual Studio ürününe göre sıralanan iş yükünün ve bileşen kimliklerinin bir listesi için bkz. [Visual Studio iş yükü ve bileşen kimlikleri](workload-and-component-ids.md) sayfası.

## <a name="list-of-language-locales"></a>Dil yerel ayarlar listesi

| **Dil yerel ayar** | **Dil** |
| ----------------------- | --------------- |
| Cs-cz | Çekçe |
| De-de | Almanca |
| En-us | İngilizce |
| ES-es | İspanyolca |
| FR-fr | Fransızca |
| İt-IT | İtalyanca |
| Ja-jp | Japonca |
| Ko-kr | Korece |
| PL-pl | Lehçe |
| PT-br | Portekizce - Brezilya |
| RU-ru | Rusça |
| Tr-tr | Türkçe |
| Zh-cn | Çince - Basitleştirilmiş |
| Zh-tw | Çince - Geleneksel |

## <a name="error-codes"></a>Hata kodları

İşlemin sonucu bağlı olarak `%ERRORLEVEL%` ortam değişkeni aşağıdaki değerlerden birine ayarlanır:

[!INCLUDE[install-error-codes-md](includes/install-error-codes-md.md)]

Her işlemin birkaç günlük dosyalarında oluşturur `%TEMP%` yüklemenin ilerleme durumunu belirten bir dizin. Klasör tarihe göre sıralayın ve ile başlayan dosyaları arayın `dd_bootstrapper`, `dd_client`, ve `dd_setup` önyükleyici için yükleyici uygulama ve Kurulum altyapısı, sırasıyla.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio yüklemesi için komut satırı parametresi örnekleri](command-line-parameter-examples.md)
- [Visual Studio’nun çevrimdışı yüklemesini oluşturma](create-an-offline-installation-of-visual-studio.md)
- [Yanıt dosyası ile Visual Studio yüklemesini otomatikleştirme](automated-installation-with-response-file.md)
- [Visual Studio iş yükü ve bileşen kimlikleri](workload-and-component-ids.md)
