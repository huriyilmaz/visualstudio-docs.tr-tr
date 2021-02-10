---
title: Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme
titleSuffix: ''
description: Visual Studio yüklemenizi denetlemek veya özelleştirmek için komut satırı parametrelerini nasıl kullanacağınızı öğrenin.
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
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: d5bea30b8a046be55ba49a1cc1dbf12e3093585f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935670"
---
# <a name="use-command-line-parameters-to-install-visual-studio"></a>Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme

Visual Studio 'Yu bir komut isteminden yüklediğinizde, yüklemeyi denetlemek veya özelleştirmek için çeşitli komut satırı parametrelerini kullanabilirsiniz. Komut satırından aşağıdaki eylemleri gerçekleştirebilirsiniz:

- Yüklemeyi seçilen belirli seçeneklerle başlatın.
- Yükleme işlemini otomatikleştirin.
- Daha sonra kullanmak üzere yükleme dosyalarının bir önbelleğini (Düzen) oluşturun.

Komut satırı seçenekleri, yükleme işlemini başlatan küçük (1 MB) dosya olan kurulum Önyükleyicisi ile birlikte kullanılır. Önyükleyici, Visual Studio sitesinden indirdiğinizde başlatılan ilk yürütülebilir dosyadır.

::: moniker range="vs-2017"

Visual Studio 2017 için bir önyükleyici almak üzere, bunun nasıl yapılacağı hakkında ayrıntılı bilgi için [**Visual Studio önceki sürümler**](https://visualstudio.microsoft.com/vs/older-downloads/) indirme sayfasına bakın.

::: moniker-end

::: moniker range="vs-2019"

Yüklemekte olduğunuz ürün sürümü için en son sürüm önyükleyicisinin doğrudan bağlantısını almak için aşağıdaki bağlantıları kullanın:

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

 Visual Studio komut satırı parametreleri büyük/küçük harfe duyarlıdır.

> Sözdizimi `vs_enterprise.exe [command] <options>...`

`vs_enterprise.exe`Yüklemekte olduğunuz ürün sürümüne uygun şekilde değiştirin. (Alternatif olarak, kullanabilirsiniz `vs_installer.exe` .)

>[!TIP]
> Visual Studio 'Yu yüklemek için komut satırını kullanma hakkında daha fazla örnek için, [komut satırı parametre örnekleri](command-line-parameter-examples.md) sayfasına bakın.

::: moniker range="vs-2017"

| **Komut** | **Açıklama** |
| ----------------------- | --------------- |
| adet | Ürünü yüklüyor. |
| `modify` | Yüklü bir ürünü değiştirir. |
| `update` | Yüklü bir ürünü güncelleştirir. |
| `repair` | Yüklü bir ürünü onarır. |
| `uninstall` | Yüklü bir ürünü kaldırır. |
| `export` | **Sürüm 15,9 ' de yeni**: yükleme seçimini bir yükleme yapılandırma dosyasına aktarır. **Note**: yalnızca vs_installer.exe ile kullanılabilir. |

::: moniker-end

::: moniker range="vs-2019"

| **Komut** | **Açıklama** |
| ----------------------- | --------------- |
| adet | Ürünü yüklüyor. |
| `modify` | Yüklü bir ürünü değiştirir. |
| `update` | Yüklü bir ürünü güncelleştirir. |
| `repair` | Yüklü bir ürünü onarır. |
| `uninstall` | Yüklü bir ürünü kaldırır. |
| `export` | Yükleme seçimini bir yükleme yapılandırma dosyasına aktarır. **Note**: yalnızca vs_installer.exe ile kullanılabilir. |

::: moniker-end

## <a name="install-options"></a>Yükleme seçenekleri

::: moniker range="vs-2017"

| **Install seçeneği** | **Açıklama** |
| ----------------------- | --------------- |
| `--installPath <dir>` | Üzerinde işlem yapılacak örnek için yükleme dizini. Yükleme komutu için bu **Isteğe bağlıdır** ve örneğin, örnek yüklenir. Diğer komutlar için bu **gereklidir** ve daha önce yüklenen örneğin yüklendiği yerdir. |
| `--addProductLang <language-locale>` | **Isteğe bağlı**: bir yükleme veya değiştirme işlemi sırasında, ürüne yüklenen Kullanıcı Arabirimi dil paketlerini belirler. Birden çok dil paketi eklemek için komut satırında birden çok kez görünebilir. Mevcut değilse, yükleme makinenin yerel ayarını kullanır. Daha fazla bilgi için bu sayfadaki [dil yerel ayarları listesi](#list-of-language-locales) bölümüne bakın.|
| `--removeProductLang <language-locale>` | **Isteğe bağlı**: bir Install veya MODIFY Operation sırasında, bu, üründen KALDıRıLACAK olan UI dil paketlerini belirler. Birden çok dil paketi eklemek için komut satırında birden çok kez görünebilir. Daha fazla bilgi için bu sayfadaki [dil yerel ayarları listesi](#list-of-language-locales) bölümüne bakın.|
| `--add <one or more workload or component IDs>` | **Isteğe bağlı**: eklenecek bir veya daha fazla iş yükü veya Bileşen kimliği. Yapıtın gerekli bileşenleri yüklendi, ancak önerilen veya isteğe bağlı bileşenler değil. Ve/veya kullanarak ek bileşenleri genel olarak denetleyebilirsiniz `--includeRecommended` `--includeOptional` . Birden çok iş yükünü veya bileşeni eklemek için, `--add` komutunu tekrarlayın (örneğin, `--add Workload1 --add Workload2` ). Daha ayrıntılı denetim için, KIMLIĞE ekleme yapabilir `;includeRecommended` `;includeOptional` (örneğin, `--add Workload1;includeRecommended` veya `--add Workload2;includeRecommended;includeOptional` ). Daha fazla bilgi için bkz. [Iş yükü ve bileşen kimlikleri](workload-and-component-ids.md) sayfası. Bu seçeneği, gereken şekilde yineleyebilirsiniz.|
| `--remove <one or more workload or component IDs>` | **Isteğe bağlı**: kaldırılacak bir veya daha fazla iş yükü veya Bileşen kimliği. Daha fazla bilgi için bkz. [Iş yükünüz ve bileşen kimlikleri](workload-and-component-ids.md) sayfası. Bu seçeneği, gereken şekilde yineleyebilirsiniz.|
| `--in <path>` | **Isteğe bağlı**: bir yanıt dosyasının URI 'si veya yolu.  |
| `--all` | **Isteğe bağlı**: bir ürün için tüm iş yüklerinin ve bileşenlerin yüklenip yüklenmeyeceğini belirtir. |
| `--allWorkloads` | **Isteğe bağlı**: tüm iş yüklerini ve bileşenleri, önerilen veya isteğe bağlı bileşen olmadan yüklenir. |
| `--includeRecommended` | **Isteğe bağlı**: yüklü olan, ancak isteğe bağlı bileşenleri olmayan tüm iş yükleri için önerilen bileşenleri içerir. İş yükleri veya ile belirtilir `--allWorkloads` `--add` . |
| `--includeOptional` | **Isteğe bağlı**: önerilen bileşenleri değil, yüklü olan tüm iş yükleri için isteğe bağlı bileşenleri içerir. İş yükleri veya ile belirtilir `--allWorkloads` `--add` .  |
| `--quiet, -q` | **Isteğe bağlı**: yüklemeyi gerçekleştirirken hiçbir Kullanıcı arabirimini görüntülememe. |
| `--passive, -p` | **Isteğe bağlı**: Kullanıcı arabirimini görüntüleme, ancak kullanıcıdan herhangi bir etkileşim isteme. |
| `--norestart` | **Isteğe bağlı**: varsa, `--passive` veya `--quiet` (gerekliyse) komutları otomatik olarak yeniden başlatmaz.  Hiçbiri veya belirtilmemişse bu yok `--passive` sayılır `--quiet` .  |
| `--nickname <name>` | **Isteğe bağlı**: Bu, yüklü bir ürüne atanacak takma adı tanımlar. Takma ad 10 karakterden uzun olamaz.  |
| `--productKey` | **Isteğe bağlı**: Bu, yüklü bir ürün için kullanılacak ürün anahtarını tanımlar. Bu, ya da biçiminde 25 alfasayısal karakterden oluşur `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` `xxxxxxxxxxxxxxxxxxxxxxxxx` . |
| `--help, --?, -h, -?` | Bu sayfanın çevrimdışı bir sürümünü görüntüleyin. |
| `--config <path>` | **15,9 ' de** **Isteğe bağlı** ve yeni: bir yükleme veya değiştirme işlemi sırasında, daha önce kaydedilen bir yükleme yapılandırma dosyasına göre eklenecek iş yüklerini ve bileşenleri belirler. Bu işlem eklenebilir ve dosyada yoksa herhangi bir iş yükünü veya bileşeni kaldırmaz. Ayrıca, ürüne uygulanmayacak öğeler eklenmez. Dışarı aktarma işlemi sırasında, yükleme yapılandırma dosyasının kaydedileceği konumu belirler. |

::: moniker-end

::: moniker range="vs-2019"

| **Install seçeneği** | **Açıklama** |
| ----------------------- | --------------- |
| `--installPath <dir>` | Üzerinde işlem yapılacak örnek için yükleme dizini. Yükleme komutu için bu **Isteğe bağlıdır** ve örneğin, örnek yüklenir. Diğer komutlar için bu **gereklidir** ve daha önce yüklenen örneğin yüklendiği yerdir. |
| `--addProductLang <language-locale>` | **Isteğe bağlı**: bir yükleme veya değiştirme işlemi sırasında, ürüne yüklenen Kullanıcı Arabirimi dil paketlerini belirler. Birden çok dil paketi eklemek için komut satırında birden çok kez görünebilir. Mevcut değilse, yükleme makinenin yerel ayarını kullanır. Daha fazla bilgi için bu sayfadaki [dil yerel ayarları listesi](#list-of-language-locales) bölümüne bakın.|
| `--removeProductLang <language-locale>` | **Isteğe bağlı**: bir Install veya MODIFY Operation sırasında, bu, üründen KALDıRıLACAK olan UI dil paketlerini belirler. Birden çok dil paketi eklemek için komut satırında birden çok kez görünebilir. Daha fazla bilgi için bu sayfadaki [dil yerel ayarları listesi](#list-of-language-locales) bölümüne bakın.|
| `--add <one or more workload or component IDs>` | **Isteğe bağlı**: eklenecek bir veya daha fazla iş yükü veya Bileşen kimliği. Yapıtın gerekli bileşenleri yüklendi, ancak önerilen veya isteğe bağlı bileşenler değil. Ve/veya kullanarak ek bileşenleri genel olarak denetleyebilirsiniz `--includeRecommended` `--includeOptional` . Birden çok iş yükünü veya bileşeni eklemek için, `--add` komutunu tekrarlayın (örneğin, `--add Workload1 --add Workload2` ). Daha ayrıntılı denetim için, KIMLIĞE ekleme yapabilir `;includeRecommended` `;includeOptional` (örneğin, `--add Workload1;includeRecommended` veya `--add Workload2;includeRecommended;includeOptional` ). Daha fazla bilgi için bkz. [Iş yükü ve bileşen kimlikleri](workload-and-component-ids.md) sayfası. Bu seçeneği, gereken şekilde yineleyebilirsiniz.|
| `--remove <one or more workload or component IDs>` | **Isteğe bağlı**: kaldırılacak bir veya daha fazla iş yükü veya Bileşen kimliği. Daha fazla bilgi için bkz. [Iş yükünüz ve bileşen kimlikleri](workload-and-component-ids.md) sayfası. Bu seçeneği, gereken şekilde yineleyebilirsiniz.|
| `--in <path>` | **Isteğe bağlı**: bir yanıt dosyasının URI 'si veya yolu.  |
| `--all` | **Isteğe bağlı**: bir ürün için tüm iş yüklerinin ve bileşenlerin yüklenip yüklenmeyeceğini belirtir. |
| `--allWorkloads` | **Isteğe bağlı**: tüm iş yüklerini ve bileşenleri, önerilen veya isteğe bağlı bileşen olmadan yüklenir. |
| `--includeRecommended` | **Isteğe bağlı**: yüklü olan, ancak isteğe bağlı bileşenleri olmayan tüm iş yükleri için önerilen bileşenleri içerir. İş yükleri veya ile belirtilir `--allWorkloads` `--add` . |
| `--includeOptional` | **Isteğe bağlı**: önerilen bileşenleri değil, yüklü olan tüm iş yükleri için isteğe bağlı bileşenleri içerir. İş yükleri veya ile belirtilir `--allWorkloads` `--add` .  |
| `--quiet, -q` | **Isteğe bağlı**: yüklemeyi gerçekleştirirken hiçbir Kullanıcı arabirimini görüntülememe. |
| `--passive, -p` | **Isteğe bağlı**: Kullanıcı arabirimini görüntüleme, ancak kullanıcıdan herhangi bir etkileşim isteme. |
| `--norestart` | **Isteğe bağlı**: varsa, `--passive` veya `--quiet` (gerekliyse) komutları otomatik olarak yeniden başlatmaz.  Hiçbiri veya belirtilmemişse bu yok `--passive` sayılır `--quiet` .  |
| `--nickname <name>` | **Isteğe bağlı**: Bu, yüklü bir ürüne atanacak takma adı tanımlar. Takma ad 10 karakterden uzun olamaz.  |
| `--productKey` | **Isteğe bağlı**: Bu, yüklü bir ürün için kullanılacak ürün anahtarını tanımlar. Bu, ya da biçiminde 25 alfasayısal karakterden oluşur `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` `xxxxxxxxxxxxxxxxxxxxxxxxx` . |
| `--help, --?, -h, -?` | Bu sayfanın çevrimdışı bir sürümünü görüntüleyin. |
| `--config <path>` | **Isteğe bağlı**: yükleme veya değiştirme işlemi sırasında, daha önce kaydedilen bir yükleme yapılandırma dosyasına göre eklenecek iş yüklerini ve bileşenleri belirler. Bu işlem eklenebilir ve dosyada yoksa herhangi bir iş yükünü veya bileşeni kaldırmaz. Ayrıca, ürüne uygulanmayacak öğeler eklenmez. Dışarı aktarma işlemi sırasında, yükleme yapılandırma dosyasının kaydedileceği konumu belirler. |

::: moniker-end

> [!IMPORTANT]
> Birden çok iş yükü ve bileşen belirtirken, `--add` `--remove` her öğe için veya komut satırı anahtarını tekrarlamanız gerekir.

## <a name="layout-options"></a>Düzen seçenekleri

::: moniker range="vs-2017"

| **Düzen seçenekleri** | **Açıklama** |
| ----------------------- | --------------- |
| `--layout <dir>` | Çevrimdışı bir yüklemesi önbelleği oluşturmak için bir dizin belirtir. Daha fazla bilgi için bkz. [Visual Studio 'nun ağ tabanlı yüklemesi oluşturma](create-a-network-installation-of-visual-studio.md).|
| `--lang <one or more language-locales>` | **Isteğe bağlı**: `--layout` belirtilen dil (ler) i olan kaynak paketleriyle çevrimdışı bir yüklemesi önbelleği hazırlamak için ile birlikte kullanılır. Daha fazla bilgi için bu sayfadaki [dil yerel ayarları listesi](#list-of-language-locales) bölümüne bakın.|
| `--add <one or more workload or component IDs>` | **Isteğe bağlı**: eklenecek bir veya daha fazla iş yükü veya Bileşen kimliği. Yapıtın gerekli bileşenleri yüklendi, ancak önerilen veya isteğe bağlı bileşenler değil. Ve/veya kullanarak ek bileşenleri genel olarak denetleyebilirsiniz `--includeRecommended` `--includeOptional` . Daha ayrıntılı denetim için, KIMLIĞE ekleme yapabilir `;includeRecommended` `;includeOptional` (örneğin, `--add Workload1;includeRecommended` veya `--add Workload2;includeOptional` ). Daha fazla bilgi için bkz. [Iş yükü ve bileşen kimlikleri](workload-and-component-ids.md) sayfası. <br/>**Note**: `--add` kullanılıyorsa, yalnızca belirtilen iş yükleri ve bileşenler ve bunların bağımlılıkları indirilir. `--add`Belirtilmezse, tüm iş yükleri ve bileşenler düzene indirilir.|
| `--includeRecommended` | **Isteğe bağlı**: yüklü olan, ancak isteğe bağlı bileşenleri olmayan tüm iş yükleri için önerilen bileşenleri içerir. İş yükleri veya ile belirtilir `--allWorkloads` `--add` . |
| `--includeOptional` | **Isteğe bağlı**: mizanpaja dahil edilen tüm iş yükleri için önerilen *ve* isteğe bağlı bileşenleri içerir. İş yükleri ile belirtilir `--add` .  |
| `--keepLayoutVersion` | **15,3 ' deki yenilikler, isteğe bağlı**: düzen sürümünü güncelleştirmeden değişiklikleri düzene uygulayın. |
| `--verify` | **15,3 ' deki yenilikler, isteğe bağlı**: bir düzenin içeriğini doğrulayın. Bozuk veya eksik dosyalar listelenir. |
| `--fix` | **15,3 ' deki yenilikler, isteğe bağlı**: bir düzenin içeriğini doğrulayın. Herhangi bir dosya bozuksa veya eksikse, bunlar yeniden indirilir. Bir düzeni onarmak için Internet erişimi gerekir. |
| `--clean <one or more paths to catalogs>` | **15,3 ' deki yenilikler, isteğe bağlı**: bileşenlerin eski sürümlerini, daha yeni bir sürüme güncelleştirilmiş bir düzenden kaldırır. |

| **Gelişmiş yüklemesi seçenekleri** | **Açıklama** |
| ----------------------- | --------------- |
| `--channelId <id>` | **Isteğe bağlı**: yüklenecek ÖRNEĞIN kanalının kimliği. Bu, install komutu için gereklidir ve belirtilirse diğer komutlar için yok sayılır `--installPath` . |
| `--channelUri <uri>` | **Isteğe bağlı**: Kanal bildiriminin URI 'si. Güncelleştirmeler istenmemişse, `--channelUri` var olmayan bir dosyaya işaret edebilir (örneğin,--channelUri C:\atanntexist.chman). Bu, install komutu için kullanılabilir; diğer komutlar için yok sayılır. |
| `--installChannelUri <uri>` | **Isteğe bağlı**: yükleme için kullanılacak kanal bildiriminin URI 'si. `--channelUri`Güncelleştirmeleri algılamak için (belirtildiğinde belirtilmesi gereken) tarafından BELIRTILEN URI `--installChannelUri` kullanılır. Bu, install komutu için kullanılabilir; diğer komutlar için yok sayılır. |
| `--installCatalogUri <uri>` | **Isteğe bağlı**: yükleme için kullanılacak Katalog bildiriminin URI 'si. Belirtilmişse, kanal yöneticisi, yükleme kanalı bildiriminde URI 'yi kullanmadan önce bu URI 'den Katalog bildirimini indirmeye çalışır. Bu parametre, düzen önbelleğinin zaten indirilmiş olan ürün kataloğu ile oluşturulacağı çevrimdışı yüklemeyi desteklemek için kullanılır. Bu, install komutu için kullanılabilir; diğer komutlar için yok sayılır. |
| `--productId <id>` | **Isteğe bağlı** Yüklenecek örnek için ürünün KIMLIĞI. Bu, normal yükleme koşullarında önceden doldurulur. |
| `--wait` | **Isteğe bağlı**: işlem, bir çıkış kodu döndürmeden önce Yüklemenin tamamlanmasını bekler. Bu, yüklemenin, yükleme işleminin geri dönüş kodunu işlemesini tamamlaması için beklemesi gereken yüklemeleri otomatik hale getirmeye yönelik bir seçenektir. |
| `--locale <language-locale>` | **Isteğe bağlı**: yükleyicinin kendisi için Kullanıcı arabiriminin görüntüleme dilini değiştirin. Ayar kalıcı olacak. Daha fazla bilgi için bu sayfadaki [dil yerel ayarları listesi](#list-of-language-locales) bölümüne bakın.|
| `--cache` | **15,2 ' deki yenilikler, isteğe bağlı**: varsa, paketler sonraki onarımlar için yüklendikten sonra saklanır. Bu, sonraki yüklemeler, onarımlar veya değişiklikler için kullanılacak genel ilke ayarını geçersiz kılar. Varsayılan ilke, paketleri önbelleğe almak için kullanılır. Bu, Kaldır komutu için yok sayılır. Daha fazla bilgi için [paket önbelleğini devre dışı bırakma veya taşıma](disable-or-move-the-package-cache.md) konusunu okuyun. |
| `--nocache` | **15,2 ' deki yenilikler, isteğe bağlı**: varsa, paketler yüklendikten veya onarıldıktan sonra silinir. Yalnızca gerekirse yeniden indirilir ve kullanıldıktan sonra yeniden silinir. Bu, sonraki yüklemeler, onarımlar veya değişiklikler için kullanılacak genel ilke ayarını geçersiz kılar. Varsayılan ilke, paketleri önbelleğe almak için kullanılır. Bu, Kaldır komutu için yok sayılır. Daha fazla bilgi için [paket önbelleğini devre dışı bırakma veya taşıma](disable-or-move-the-package-cache.md) konusunu okuyun. |
| `--noUpdateInstaller` | **15,2 ' deki yenilikler, isteğe bağlı**: varsa, sessiz belirtildiğinde yükleyicinin kendini güncelleştirmesini önler. Yükleyici, bir yükleyici güncelleştirmesi gerektiğinde sessiz bir şekilde belirtilmişse, komut başarısız olur ve sıfır olmayan bir çıkış kodu döndürür. |
| `--noWeb` | **15,3 ' deki yenilikler, isteğe bağlı**: varsa, Visual Studio Kurulumu Visual Studio 'yu yüklemek için Düzen dizininizdeki dosyaları kullanır. Bir Kullanıcı, mizanpajda olmayan bileşenleri yüklemeye çalışırsa, kurulum başarısız olur.  Daha fazla bilgi için bkz. [ağ yüklemesinden dağıtma](create-a-network-installation-of-visual-studio.md). <br/><br/> **Önemli**: Bu anahtar, Visual Studio kurulumunun güncelleştirmeleri denetlemesini durdurmaz. Daha fazla bilgi için bkz. [ağ tabanlı Visual Studio dağıtımlarında güncelleştirmeleri denetleme](controlling-updates-to-visual-studio-deployments.md). |
| `--path <name>=<path>` | **15,7 ' deki yenilikler, isteğe bağlı**: yükleme için özel yükleme yollarını belirtmek için kullanılır. Desteklenen yol adları paylaşılır, önbelleğe alınır ve yüklenir. |
| `--path cache=<path>` | **15,7 ' deki yenilikler, isteğe bağlı**: yükleme dosyalarını indirmek için belirttiğiniz konumu kullanır. Bu konum yalnızca Visual Studio 'Nun ilk kez yüklendiği zaman ayarlanabilir. Örnek: `--path cache="C:\VS\cache"` |
| `--path shared=<path>` | **15,7 ' deki yenilikler, isteğe bağlı**: yan yana Visual Studio yüklemeleri için paylaşılan dosyaları içerir. Bazı araçlar ve SDK 'lar bu sürücüdeki bir konuma yüklenir, bazı diğerleri bu ayarı geçersiz kılabilir ve başka bir sürücüye yükler. Örnek: `--path shared="C:\VS\shared"` <br><br>Önemli: Bu, yalnızca bir kez ve Visual Studio 'nun ilk kez yüklendiği zaman ayarlanabilir. |
| `--path install=<path>` | **15,7 ' deki yenilikler, isteğe bağlı**: ile eşdeğerdir `–-installPath` . Özellikle, `--installPath "C:\VS"` ve `--path install="C:\VS"` eşdeğerdir. Tek seferde bu komutlardan yalnızca biri kullanılabilir. |

::: moniker-end

::: moniker range="vs-2019"

| **Düzen seçenekleri** | **Açıklama** |
| ----------------------- | --------------- |
| `--layout <dir>` | Çevrimdışı bir yüklemesi önbelleği oluşturmak için bir dizin belirtir. Daha fazla bilgi için bkz. [Visual Studio 'nun ağ tabanlı yüklemesi oluşturma](create-a-network-installation-of-visual-studio.md).|
| `--lang <one or more language-locales>` | **Isteğe bağlı**: `--layout` belirtilen dil (ler) i olan kaynak paketleriyle çevrimdışı bir yüklemesi önbelleği hazırlamak için ile birlikte kullanılır. Daha fazla bilgi için bu sayfadaki [dil yerel ayarları listesi](#list-of-language-locales) bölümüne bakın.|
| `--add <one or more workload or component IDs>` | **Isteğe bağlı**: eklenecek bir veya daha fazla iş yükü veya Bileşen kimliği. Yapıtın gerekli bileşenleri yüklendi, ancak önerilen veya isteğe bağlı bileşenler değil. Ve/veya kullanarak ek bileşenleri genel olarak denetleyebilirsiniz `--includeRecommended` `--includeOptional` . Daha ayrıntılı denetim için, KIMLIĞE ekleme yapabilir `;includeRecommended` `;includeOptional` (örneğin, `--add Workload1;includeRecommended` veya `--add Workload2;includeOptional` ). Daha fazla bilgi için bkz. [Iş yükü ve bileşen kimlikleri](workload-and-component-ids.md) sayfası. <br/>**Note**: `--add` kullanılıyorsa, yalnızca belirtilen iş yükleri ve bileşenler ve bunların bağımlılıkları indirilir. `--add`Belirtilmezse, tüm iş yükleri ve bileşenler düzene indirilir.|
| `--includeRecommended` | **Isteğe bağlı**: yüklü olan, ancak isteğe bağlı bileşenleri olmayan tüm iş yükleri için önerilen bileşenleri içerir. İş yükleri veya ile belirtilir `--allWorkloads` `--add` . |
| `--includeOptional` | **Isteğe bağlı**: mizanpaja dahil edilen tüm iş yükleri için önerilen *ve* isteğe bağlı bileşenleri içerir. İş yükleri ile belirtilir `--add` .  |
| `--keepLayoutVersion` | **Isteğe bağlı**: düzen sürümünü güncelleştirmeden mizanpajdaki değişiklikleri uygulayın. |
| `--verify` | **Isteğe bağlı**: bir düzenin içeriğini doğrulayın. Bozuk veya eksik dosyalar listelenir. |
| `--fix` | **Isteğe bağlı**: bir düzenin içeriğini doğrulayın.  Herhangi bir dosya bozuksa veya eksikse, bunlar yeniden indirilir. Bir düzeni onarmak için Internet erişimi gerekir. |
| `--clean <one or more paths to catalogs>` | **Isteğe bağlı**: daha yeni bir sürüme güncelleştirilmiş bir düzenden bileşenlerin eski sürümlerini kaldırır. |

| **Gelişmiş yüklemesi seçenekleri** | **Açıklama** |
| ----------------------- | --------------- |
| `--channelId <id>` | **Isteğe bağlı**: yüklenecek ÖRNEĞIN kanalının kimliği. Bu, install komutu için gereklidir ve belirtilirse diğer komutlar için yok sayılır `--installPath` . |
| `--channelUri <uri>` | **Isteğe bağlı**: Kanal bildiriminin URI 'si. Güncelleştirmeler istenmemişse, `--channelUri` var olmayan bir dosyaya işaret edebilir (örneğin,--channelUri C:\atanntexist.chman). Bu, install komutu için kullanılabilir; diğer komutlar için yok sayılır. |
| `--installChannelUri <uri>` | **Isteğe bağlı**: yükleme için kullanılacak kanal bildiriminin URI 'si. `--channelUri`Güncelleştirmeleri algılamak için (belirtildiğinde belirtilmesi gereken) tarafından BELIRTILEN URI `--installChannelUri` kullanılır. Bu, install komutu için kullanılabilir; diğer komutlar için yok sayılır. |
| `--installCatalogUri <uri>` | **Isteğe bağlı**: yükleme için kullanılacak Katalog bildiriminin URI 'si. Belirtilmişse, kanal yöneticisi, yükleme kanalı bildiriminde URI 'yi kullanmadan önce bu URI 'den Katalog bildirimini indirmeye çalışır. Bu parametre, düzen önbelleğinin zaten indirilmiş olan ürün kataloğu ile oluşturulacağı çevrimdışı yüklemeyi desteklemek için kullanılır. Bu, install komutu için kullanılabilir; diğer komutlar için yok sayılır. |
| `--productId <id>` | **Isteğe bağlı** Yüklenecek örnek için ürünün KIMLIĞI. Bu, normal yükleme koşullarında önceden doldurulur. |
| `--wait` | **Isteğe bağlı**: işlem, bir çıkış kodu döndürmeden önce Yüklemenin tamamlanmasını bekler. Bu, yüklemenin, yükleme işleminin geri dönüş kodunu işlemesini tamamlaması için beklemesi gereken yüklemeleri otomatik hale getirmeye yönelik bir seçenektir. |
| `--locale <language-locale>` | **Isteğe bağlı**: yükleyicinin kendisi için Kullanıcı arabiriminin görüntüleme dilini değiştirin. Ayar kalıcı olacak. Daha fazla bilgi için bu sayfadaki [dil yerel ayarları listesi](#list-of-language-locales) bölümüne bakın.|
| `--cache` | **Isteğe bağlı**: varsa, paketler sonraki onarımlar için yüklendikten sonra saklanır. Bu, sonraki yüklemeler, onarımlar veya değişiklikler için kullanılacak genel ilke ayarını geçersiz kılar. Varsayılan ilke, paketleri önbelleğe almak için kullanılır. Bu, Kaldır komutu için yok sayılır. Daha fazla bilgi için [paket önbelleğini devre dışı bırakma veya taşıma](disable-or-move-the-package-cache.md) konusunu okuyun. |
| `--nocache` | **Isteğe bağlı**: varsa, paketler yüklendikten veya onarıldıktan sonra silinir. Yalnızca gerekirse yeniden indirilir ve kullanıldıktan sonra yeniden silinir. Bu, sonraki yüklemeler, onarımlar veya değişiklikler için kullanılacak genel ilke ayarını geçersiz kılar. Varsayılan ilke, paketleri önbelleğe almak için kullanılır. Bu, Kaldır komutu için yok sayılır. Daha fazla bilgi için [paket önbelleğini devre dışı bırakma veya taşıma](disable-or-move-the-package-cache.md) konusunu okuyun. |
| `--noUpdateInstaller` | **Isteğe bağlı**: varsa, sessiz belirtildiğinde yükleyicinin kendini güncelleştirmesini önler. Yükleyici, bir yükleyici güncelleştirmesi gerektiğinde sessiz bir şekilde belirtilmişse, komut başarısız olur ve sıfır olmayan bir çıkış kodu döndürür. |
| `--noWeb` | **Isteğe bağlı**: varsa, Visual Studio Kurulumu Visual Studio 'yu yüklemek için Düzen dizininizdeki dosyaları kullanır. Bir Kullanıcı, mizanpajda olmayan bileşenleri yüklemeye çalışırsa, kurulum başarısız olur.  Daha fazla bilgi için bkz. [ağ yüklemesinden dağıtma](create-a-network-installation-of-visual-studio.md). <br/><br/> **Önemli**: Bu anahtar, Visual Studio kurulumunun güncelleştirmeleri denetlemesini durdurmaz. Daha fazla bilgi için bkz. [ağ tabanlı Visual Studio dağıtımlarında güncelleştirmeleri denetleme](controlling-updates-to-visual-studio-deployments.md). **16.3.5 ' de yeni**: Bu anahtar hataları engeller ve çevrimdışı yüklemeler ve güncelleştirmeler ile performansı geliştirir.|
| `--path <name>=<path>` | **Isteğe bağlı**: yükleme için özel yükleme yollarını belirtmek için kullanılır. Desteklenen yol adları paylaşılır, önbelleğe alınır ve yüklenir. |
| `--path cache=<path>` | **Isteğe bağlı**: yükleme dosyalarını indirmek için belirttiğiniz konumu kullanır. Bu konum yalnızca Visual Studio 'Nun ilk kez yüklendiği zaman ayarlanabilir. Örnek: `--path cache="C:\VS\cache"` |
| `--path shared=<path>` | **Isteğe bağlı**: yan yana Visual Studio yüklemeleri için paylaşılan dosyaları içerir. Bazı araçlar ve SDK 'lar bu sürücüdeki bir konuma yüklenir, bazı diğerleri bu ayarı geçersiz kılabilir ve başka bir sürücüye yükler. Örnek: `--path shared="C:\VS\shared"` <br><br>Önemli: Bu, yalnızca bir kez ve Visual Studio 'nun ilk kez yüklendiği zaman ayarlanabilir. |
| `--path install=<path>` | **Isteğe bağlı**: ile eşdeğerdir `–-installPath` . Özellikle, `--installPath "C:\VS"` ve `--path install="C:\VS"` eşdeğerdir. Tek seferde bu komutlardan yalnızca biri kullanılabilir. |

::: moniker-end

## <a name="list-of-workload-ids-and-component-ids"></a>İş yükü kimliklerinin ve bileşen kimliklerinin listesi

Visual Studio ürününe göre sıralanan iş yükünün ve bileşen kimliklerinin bir listesi için bkz. [Visual Studio iş yükü ve bileşen kimlikleri](workload-and-component-ids.md) sayfası.

## <a name="list-of-language-locales"></a>Dil yerel ayarları listesi

| **Dil yerel ayarı** | **Dil** |
| ----------------------- | --------------- |
| CS-CZ | Çekçe |
| De-de | Almanca |
| En-US | İngilizce |
| Es-es | İspanyolca |
| Fr-fr | Fransızca |
| BT BT | İtalyanca |
| Ja-JP | Japonca |
| Ko-KR | Korece |
| Pl-pl | Lehçe |
| Pt-br | Portekizce - Brezilya |
| Ru-ru | Rusça |
| Tr-tr | Türkçe |
| Zh-cn | Basitleştirilmiş Çince |
| Zh-TW | Geleneksel Çince |

## <a name="error-codes"></a>Hata kodları

İşlemin sonucuna bağlı olarak, `%ERRORLEVEL%` ortam değişkeni aşağıdaki değerlerden birine ayarlanır:

[!INCLUDE[install-error-codes-md](includes/install-error-codes-md.md)]

Her işlem, `%TEMP%` dizinde yüklemenin ilerlemesini gösteren birkaç günlük dosyası oluşturur. Klasörü tarihe göre sıralayın ve `dd_bootstrapper` `dd_client` `dd_setup` Önyükleyici, yükleyici uygulaması ve kurulum altyapısı için sırasıyla,, ve ile başlayan dosyaları arayın.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio yüklemesi için komut satırı parametresi örnekleri](command-line-parameter-examples.md)
- [Visual Studio’nun çevrimdışı yüklemesini oluşturma](create-an-offline-installation-of-visual-studio.md)
- [Yanıt dosyası ile Visual Studio yüklemesini otomatikleştirme](automated-installation-with-response-file.md)
- [Visual Studio iş yükü ve bileşen kimlikleri](workload-and-component-ids.md)
