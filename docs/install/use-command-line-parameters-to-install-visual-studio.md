---
title: Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme
titleSuffix: ''
description: Komut satırı parametreleri denetlemek veya Visual Studio yüklemenizi özelleştirmek için kullanmayı öğrenin.
ms.date: 10/11/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 0043cabf5a134d5891b66f5dbd2ae77360d206fb
ms.sourcegitcommit: a5a54b147e772dc39e519da74ec41a0c25d99628
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72289572"
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


Önyükleyici dosyanız, aşağıdakilerden biriyle aynı olmalıdır veya buna benzer olmalıdır:

* vs_enterprise.exe
* vs_professional.exe
* vs_community.exe

>[!TIP]
>Daha önce bir önyükleyici dosyası indirdiyseniz ve sürümünü doğrulamak istiyorsanız, bunun nasıl yapıldığını burada bulabilirsiniz. Windows 'ta dosya Gezgini 'ni açın, önyükleyici dosyasına sağ tıklayın, **Özellikler**' i seçin, **Ayrıntılar** sekmesini seçin ve ardından **ürün sürümü** numarasını görüntüleyin. Bu numarayı bir Visual Studio sürümüyle eşleştirmek için bkz. [Visual Studio derleme numaraları ve sürüm tarihleri](visual-studio-build-numbers-and-release-dates.md) sayfası.

## <a name="command-line-parameters"></a>Komut satırı parametreleri

 Visual Studio komut satırı parametreleri büyük/küçük harfe duyarsızdır.

> Sözdizimi: `vs_enterprise.exe [command] <options>...`

@No__t-0 ' yı yüklemekte olduğunuz ürün sürümüne uygun şekilde değiştirin. (Alternatif olarak, `vs_installer.exe` ' ı kullanabilirsiniz.)

>[!TIP]
> Visual Studio 'Yu yüklemek için komut satırını kullanma hakkında daha fazla örnek için, [komut satırı parametre örnekleri](command-line-parameter-examples.md) sayfasına bakın.

| **Komutu** | **Açıklama** |
| ----------------------- | --------------- |
| (boş) | Ürün yükler. |
| `modify` | Yüklü bir ürün değiştirir. |
| `update` | Yüklü bir ürün güncelleştirir. |
| `repair` | Yüklü bir ürün onarır. |
| `uninstall` | Yüklü bir ürün kaldırır. |
| `export` | **Sürüm 15,9 ' de yeni**: Yükleme seçimini bir yükleme yapılandırma dosyasına aktarır. **Not**: Yalnızca vs_installer. exe ile kullanılabilir. |

## <a name="install-options"></a>Seçenekleri yükler

| **Yükleme seçeneği** | **Açıklama** |
| ----------------------- | --------------- |
| `--installPath <dir>` | Yükleme dizini örneği üzerinde işlem yapmak için. Yükleme komutu için budur **isteğe bağlı** ve örneğin yüklü olduğu. Diğer komutlar için budur **gerekli** ve önceden yüklenmiş örnek yüklendiği. |
| `--addProductLang <language-locale>` | **Isteğe bağlı**: Yükleme veya değiştirme işlemi sırasında, ürüne yüklenmiş Kullanıcı Arabirimi dil paketlerini belirler. Bu, birden çok dil paketlerini eklemek için komut satırında birden çok kez görünebilir. Yoksa, yükleme makine yerel ayarı kullanır. Daha fazla bilgi için [dil yerel ayarlar listesini](#list-of-language-locales) bu sayfadaki bölümü.|
| `--removeProductLang <language-locale>` | **Isteğe bağlı**: Bir Install veya MODIFY Operation sırasında, bu, üründen kaldırılacak olan UI dil paketlerini belirler. Bu, birden çok dil paketlerini eklemek için komut satırında birden çok kez görünebilir. Daha fazla bilgi için [dil yerel ayarlar listesini](#list-of-language-locales) bu sayfadaki bölümü.|
| `--add <one or more workload or component IDs>` | **Isteğe bağlı**: Eklenecek bir veya daha fazla iş yükü veya Bileşen kimliği. Yapıtın gerekli bileşenleri, değil önerilen veya isteğe bağlı bileşenler yüklenir. Genel olarak aracılığıyla ek bileşenler denetleyebilirsiniz `--includeRecommended` ve/veya `--includeOptional`. Birden çok iş yükleri veya bileşenleri eklemek için yineleyin `--add` komutu (örneğin, `--add Workload1 --add Workload2`). Daha ayrıntılı denetim için eklediğiniz `;includeRecommended` veya `;includeOptional` kimliği (örneğin, `--add Workload1;includeRecommended` veya `--add Workload2;includeRecommended;includeOptional`). Daha fazla bilgi için [iş yükü ve Bileşen kimlikleri](workload-and-component-ids.md) sayfası. Bu seçenek gerekli olarak yineleyebilir.|
| `--remove <one or more workload or component IDs>` | **Isteğe bağlı**: Kaldırılacak bir veya daha fazla iş yükü veya Bileşen kimliği. Daha fazla bilgi için müşterilerimize [iş yükü ve Bileşen kimlikleri](workload-and-component-ids.md) sayfası. Bu seçenek gerekli olarak yineleyebilir.|
| `--in <path>` | **Isteğe bağlı**: Bir yanıt dosyasının URI veya yolu.  |
| `--all` | **Isteğe bağlı**: Bir ürün için tüm iş yüklerinin ve bileşenlerin yüklenip yüklenmeyeceğini belirtir. |
| `--allWorkloads` | **Isteğe bağlı**: Tüm iş yüklerini ve bileşenleri, önerilen veya isteğe bağlı bileşen olmadan yüklenir. |
| `--includeRecommended` | **Isteğe bağlı**: , Yüklü olan, ancak isteğe bağlı bileşenleri olmayan tüm iş yükleri için önerilen bileşenleri içerir. Belirtilen iş yükleri ile birlikte `--allWorkloads` veya `--add`. |
| `--includeOptional` | **Isteğe bağlı**: Yüklü olan, ancak önerilen bileşenleri olmayan tüm iş yükleri için isteğe bağlı bileşenleri içerir. Belirtilen iş yükleri ile birlikte `--allWorkloads` veya `--add`.  |
| `--quiet, -q` | **Isteğe bağlı**: Yüklemeyi gerçekleştirirken hiçbir Kullanıcı arabirimini görüntülememe. |
| `--passive, -p` | **Isteğe bağlı**: Kullanıcı arabirimini görüntüleme, ancak kullanıcıdan herhangi bir etkileşim isteme. |
| `--norestart` | **Isteğe bağlı**: Varsa, `--passive` veya `--quiet` olan komutlar makineyi otomatik olarak yeniden başlatmaz (gerekliyse).  Bu ne sayılır `--passive` ya da `--quiet` belirtilir.  |
| `--nickname <name>` | **Isteğe bağlı**: Bu, yüklü bir ürüne atanacak takma adı tanımlar. Takma ad 10 karakterden uzun olamaz.  |
| `--productKey` | **Isteğe bağlı**: Bu, yüklü bir ürün için kullanılacak ürün anahtarını tanımlar. Şunlardan oluşur 25 alfasayısal karakter ya da biçimi `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` veya `xxxxxxxxxxxxxxxxxxxxxxxxx`. |
| `--help, --?, -h, -?` | Bu sayfanın çevrimdışı bir sürümünü görüntüler. |
| `--config <path>` | **15,9 ' de** **Isteğe bağlı** ve yeni: Yükleme veya değiştirme işlemi sırasında, daha önce kaydedilen bir yükleme yapılandırma dosyasına göre eklenecek iş yüklerini ve bileşenleri belirler. . Bu işlem eklenebilir ve bunlar dosyasında mevcut değilse herhangi bir iş yükü veya bileşen kaldırmaz. Ayrıca, ürün için geçerli olmayan öğeler eklenmeyecek. Dışa aktarma işlemi sırasında bu yükleme yapılandırma dosyasını kaydetmek istediğiniz konumu belirler. |

> [!IMPORTANT]
> Birden çok iş yükü ve bileşen belirtirken, her öğe için `--add` veya `--remove` komut satırı anahtarını tekrarlamanız gerekir.

## <a name="layout-options"></a>Düzen seçenekleri

| **Düzen Seçenekleri** | **Açıklama** |
| ----------------------- | --------------- |
| `--layout <dir>` | Yükleme önbelleği çevrimdışı oluşturmak için bir dizini belirtir. Daha fazla bilgi için [Visual Studio'nun ağ tabanlı yüklemesini oluşturma](create-a-network-installation-of-visual-studio.md).|
| `--lang <one or more language-locales>` | **Isteğe bağlı**: Kaynak paketleriyle, belirtilen dile sahip çevrimdışı bir yüklemeyi hazırlamak için `--layout` ile kullanılır. Daha fazla bilgi için [dil yerel ayarlar listesini](#list-of-language-locales) bu sayfadaki bölümü.|
| `--add <one or more workload or component IDs>` | **Isteğe bağlı**: Eklenecek bir veya daha fazla iş yükü veya Bileşen kimliği. Yapıtın gerekli bileşenleri, değil önerilen veya isteğe bağlı bileşenler yüklenir. Genel olarak aracılığıyla ek bileşenler denetleyebilirsiniz `--includeRecommended` ve/veya `--includeOptional`. Daha ayrıntılı denetim için eklediğiniz `;includeRecommended` veya `;includeOptional` kimliği (örneğin, `--add Workload1;includeRecommended` veya `--add Workload2;includeOptional`). Daha fazla bilgi için [iş yükü ve Bileşen kimlikleri](workload-and-component-ids.md) sayfası. <br/>**Not**: @No__t-0 kullanılırsa, yalnızca belirtilen iş yükleri ve bileşenler ve bunların bağımlılıkları indirilir. Varsa `--add` belirtilmezse, tüm iş yüklerinin ve bileşenlerin düzene indirilir.|
| `--includeRecommended` | **Isteğe bağlı**: , Yüklü olan, ancak isteğe bağlı bileşenleri olmayan tüm iş yükleri için önerilen bileşenleri içerir. Belirtilen iş yükleri ile birlikte `--allWorkloads` veya `--add`. |
| `--includeOptional` | **Isteğe bağlı**: Mizanpaja dahil edilen tüm iş yükleri için önerilen *ve* isteğe bağlı bileşenleri içerir. İş yükleri ile belirtilen `--add`.  |
| `--keepLayoutVersion` | **15,3 ' deki yenilikler, isteğe bağlı**: Düzen sürümünü güncelleştirmeden düzene değişiklikleri uygulayın. |
| `--verify` | **15,3 ' deki yenilikler, isteğe bağlı**: Bir düzenin içeriğini doğrulayın. Herhangi bir bozuk veya eksik dosyalar listelenir. |
| `--fix` | **15,3 ' deki yenilikler, isteğe bağlı**: Bir düzenin içeriğini doğrulayın.  Bozuk veya eksik olması için herhangi bir dosya bulunamazsa, bunlar yeniden indirilecek. Bir düzen düzeltmek için Internet erişimi gerekir. |
| `--clean <one or more paths to catalogs>` | **15,3 ' deki yenilikler, isteğe bağlı**: Daha yeni bir sürüme güncelleştirilmiş bir düzenden bileşenlerin eski sürümlerini kaldırır. |

| **Gelişmiş yükleme seçenekleri** | **Açıklama** |
| ----------------------- | --------------- |
| `--channelId <id>` | **Isteğe bağlı**: Yüklenecek örnek için kanal KIMLIĞI. Diğer komutlar için gözardı yükleme komutu için gerekli olana `--installPath` belirtilir. |
| `--channelUri <uri>` | **Isteğe bağlı**: Kanal bildiriminin URI 'SI. Güncelleştirmeler istenmiyorsa, `--channelUri` var olmayan bir dosyaya işaret edebilir (örneğin,--channelUri C:\atanntexist.chman). Bu yükleme komutu için kullanılabilir; diğer komutlar için göz ardı edilir. |
| `--installChannelUri <uri>` | **Isteğe bağlı**: Yükleme için kullanılacak kanal bildiriminin URI 'SI. URI tarafından belirtilen `--channelUri` (olması gereken belirtilen `--installChannelUri` belirtilir) güncelleştirmeleri algılamak için kullanılır. Bu yükleme komutu için kullanılabilir; diğer komutlar için göz ardı edilir. |
| `--installCatalogUri <uri>` | **Isteğe bağlı**: Yükleme için kullanılacak Katalog bildiriminin URI 'SI. Belirtilmişse, kanal Yöneticisi, yükleme kanal bildiriminde URI'yi kullanmadan önce bu URI'den Kataloğu bildirimi indirmeyi dener. Bu parametre, daha önce indirilip ürün kataloğu ile Düzen önbelleği oluşturulacağı çevrimdışı yükleme desteği için kullanılır. Bu yükleme komutu için kullanılabilir; diğer komutlar için göz ardı edilir. |
| `--productId <id>` | **İsteğe bağlı** yüklenecek örneği için ürün kimliği. Bu, normal yükleme koşullarında doldurulur. |
| `--wait` | **Isteğe bağlı**: İşlem, bir çıkış kodu döndürmeden önce Yüklemenin tamamlanmasını bekler. Bir yükleme dönüş kodu, işlemek için tamamlanması için beklemesi gereken yere otomatikleştirerek yüklemelerine istediğinizde yararlıdır. |
| `--locale <language-locale>` | **Isteğe bağlı**: Yükleyicinin kendisi için Kullanıcı arabiriminin görüntüleme dilini değiştirin. Ayarı kalıcıdır. Daha fazla bilgi için [dil yerel ayarlar listesini](#list-of-language-locales) bu sayfadaki bölümü.|
| `--cache` | **15,2 ' deki yenilikler, isteğe bağlı**: Varsa, paketler sonraki onarımlar için yüklendikten sonra tutulur. Bu, sonraki yükler, onarır veya değişiklikler için kullanılacak için genel ilke ayarını geçersiz kılar. Önbellek paketleri olan varsayılan ilkedir. Bu kaldırma komutu için göz ardı edilir. Nasıl olduğunu okuyun için [devre dışı bırakın veya paket önbelleğini taşıma](disable-or-move-the-package-cache.md) daha fazla bilgi için. |
| `--nocache` | **15,2 ' deki yenilikler, isteğe bağlı**: Varsa, paketler yüklendikten veya onarıldıktan sonra silinir. Bunlar, yalnızca gerekli ve yeniden kullanımdan sonra silinmesi yeniden indirilir. Bu, sonraki yükler, onarır veya değişiklikler için kullanılacak için genel ilke ayarını geçersiz kılar. Önbellek paketleri olan varsayılan ilkedir. Bu kaldırma komutu için göz ardı edilir. Nasıl olduğunu okuyun için [devre dışı bırakın veya paket önbelleğini taşıma](disable-or-move-the-package-cache.md) daha fazla bilgi için. |
| `--noUpdateInstaller` | **15,2 ' deki yenilikler, isteğe bağlı**: Varsa, sessiz belirtildiğinde yükleyicinin kendini güncelleştirmesini önler. Yükleyici komutu başarısız ve yükleyici güncelleştirme gerekli olduğunda noUpdateInstaller sessiz ile belirtilmişse sıfır olmayan çıkış kodu döndürür. |
| `--noWeb` | **15,3 ' deki yenilikler, isteğe bağlı**: Varsa, Visual Studio Kurulumu Visual Studio 'Yu yüklemek için Düzen dizininizdeki dosyaları kullanır. Kullanıcı, düzende olmayan bileşenleri yüklemeye çalışırsa, kurulum başarısız olur.  Daha fazla bilgi için [ağ yüklemesinden dağıtma](create-a-network-installation-of-visual-studio.md). <br/><br/> **Önemli**: Bu anahtar, Visual Studio kurulumunun güncelleştirmeleri denetlemesini durdurmaz. Daha fazla bilgi için bkz. [ağ tabanlı Visual Studio dağıtımlarında güncelleştirmeleri denetleme](controlling-updates-to-visual-studio-deployments.md).|
| `--path <name>=<path>` | **15,7 ' deki yenilikler, isteğe bağlı**: Yükleme için özel yükleme yollarını belirtmek için kullanılır. Adları paylaşılan desteklenen bir yolu, önbellek ve yükleyin. |
| `--path cache=<path>` | **15,7 ' deki yenilikler, isteğe bağlı**: Yükleme dosyalarını indirmek için belirttiğiniz konumu kullanır. Bu konum yalnızca Visual Studio'nun yüklü olduğu ilk kez ayarlanabilir. Örnek: `--path cache="C:\VS\cache"` |
| `--path shared=<path>` | **15,7 ' deki yenilikler, isteğe bağlı**: Yan yana Visual Studio yüklemeleri için paylaşılan dosyaları içerir. Bazıları bu ayarı geçersiz ve başka bir sürücüye yükleme sırasında bazı araçları ve SDK'lar bu sürücüdeki bir konuma yükleyin. Örnek: `--path shared="C:\VS\shared"` <br><br>Önemli: Bu, Visual Studio 'nun ilk kez yüklendiği anda yalnızca bir kez ayarlanabilir. |
| `--path install=<path>` | **15,7 ' deki yenilikler, isteğe bağlı**: @No__t-0 ile eşdeğerdir. Özellikle, `--installPath "C:\VS"` ve `--path install="C:\VS"` eşdeğerdir. Aynı anda bunlardan yalnızca biri kullanılabilir. |

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
