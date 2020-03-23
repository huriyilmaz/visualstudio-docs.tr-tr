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
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 7210a2834dda749cfe1d89b9093cd627b7c0ae1b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114364"
---
# <a name="use-command-line-parameters-to-install-visual-studio"></a>Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme

Visual Studio'yu komut isteminden yüklediğinizde, yüklemeyi denetlemek veya özelleştirmek için çeşitli komut satırı parametrelerini kullanabilirsiniz. Komut satırından aşağıdaki eylemleri gerçekleştirebilirsiniz:

- Önceden seçili belirli seçenekleri ile yüklemebaşlatın.
- Yükleme işlemini otomatikleştirin.
- Daha sonra kullanmak üzere yükleme dosyalarının önbelleği (düzeni) oluşturun.

Komut satırı seçenekleri, indirme işlemini başlatan küçük (1 MB) dosya olan kurulum bootstrapper ile birlikte kullanılır. Bootstrapper Visual Studio sitesinden indirdiğinizde başlatılan ilk çalıştırılabilir.

::: moniker range="vs-2017"

Visual Studio 2017 için bir bootstrapper almak için, nasıl yapılacağını hakkında ayrıntılı bilgi için [**Visual Studio önceki sürümleri**](https://visualstudio.microsoft.com/vs/older-downloads/) indirme sayfasına bakın.

::: moniker-end

::: moniker range="vs-2019"

Yüklediğiniz ürün sürümü için en son sürüm bootstrapper doğrudan bağlantı almak için aşağıdaki bağlantıları kullanın:

- [Visual Studio 2019 Kurumsal](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)
- [Visual Studio 2019 Profesyonel](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)
- [Visual Studio 2019 Topluluğu](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)

::: moniker-end


Bootstrapper dosyanız aşağıdaki dosya adlarından biriyle eşleşmeli veya benzer olmalıdır:

* vs_enterprise.exe
* vs_professional.exe
* vs_community.exe

>[!TIP]
>Daha önce bir bootstrapper dosyası indirdiyseniz ve sürümünü doğrulamak istiyorsanız, şu şekilde. Windows'da Dosya Gezgini'ni açın, bootstrapper dosyasına sağ tıklayın, **Özellikler'i**seçin, **Ayrıntılar** sekmesini seçin ve ardından **Ürün sürüm** numarasını görüntüleyin. Bu sayıyı Visual Studio'nun bir sürümüyle eşleştirmek için [Visual Studio'nun sayı ve çıkış tarihleri](visual-studio-build-numbers-and-release-dates.md) sayfasına bakın.

## <a name="command-line-parameters"></a>Komut satırı parametreleri

 Visual Studio komut satırı parametreleri büyük/küçük harf duyarsızdır.

> Sözdizimi:`vs_enterprise.exe [command] <options>...`

Yüklediğiniz ürün sürümüne uygun şekilde değiştirin. `vs_enterprise.exe` (Alternatif olarak, kullanabilirsiniz.) `vs_installer.exe`

>[!TIP]
> Visual Studio'yu yüklemek için komut satırının nasıl kullanılacağına daha fazla örnek için [Komut satırı parametresi örnekleri](command-line-parameter-examples.md) sayfasına bakın.

::: moniker range="vs-2017"

| **Komut** | **Açıklama** |
| ----------------------- | --------------- |
| (boş) | Ürünü yükler. |
| `modify` | Yüklü bir ürünü değiştirir. |
| `update` | Yüklü bir ürünü güncelleştirir. |
| `repair` | Yüklü bir ürünü onarır. |
| `uninstall` | Yüklü bir ürünü kaldır. |
| `export` | **Sürüm 15.9'da yeni**: Yükleme seçimini yükleme yapılandırma dosyasına dışa aktarın. **Not**: Sadece vs_installer.exe ile kullanılabilir. |

::: moniker-end

::: moniker range="vs-2019"

| **Komut** | **Açıklama** |
| ----------------------- | --------------- |
| (boş) | Ürünü yükler. |
| `modify` | Yüklü bir ürünü değiştirir. |
| `update` | Yüklü bir ürünü güncelleştirir. |
| `repair` | Yüklü bir ürünü onarır. |
| `uninstall` | Yüklü bir ürünü kaldır. |
| `export` | Yükleme seçimini yükleme yapılandırma dosyasına dışa aktarın. **Not**: Sadece vs_installer.exe ile kullanılabilir. |

::: moniker-end

## <a name="install-options"></a>Yükleme seçenekleri

::: moniker range="vs-2017"

| **Yükleme seçeneği** | **Açıklama** |
| ----------------------- | --------------- |
| `--installPath <dir>` | Harekete geçicisi için yükleme dizini. Install komutu için bu **Isteğe bağlıdır** ve örneğin yükleneceği yerdir. Diğer komutlar için bu **gereklidir** ve daha önce yüklenmiş örneğin yüklendiği yerdir. |
| `--addProductLang <language-locale>` | **İsteğe Bağlı**: Yükleme veya değiştirme işlemi sırasında, bu ürüne yüklenen UI dil paketlerini belirler. Birden çok dil paketi eklemek için komut satırında birden çok kez görünebilir. Yoksa, yükleme makine yerelliğini kullanır. Daha fazla bilgi için bu sayfadaki [dil yerelleri listesi](#list-of-language-locales) bölümüne bakın.|
| `--removeProductLang <language-locale>` | **İsteğe Bağlı**: Yükleme veya değiştirme işlemi sırasında, bu üründen kaldırılacak olan UI dil paketlerini belirler. Birden çok dil paketi eklemek için komut satırında birden çok kez görünebilir. Daha fazla bilgi için bu sayfadaki [dil yerelleri listesi](#list-of-language-locales) bölümüne bakın.|
| `--add <one or more workload or component IDs>` | **İsteğe Bağlı**: Eklenecek bir veya daha fazla iş yükü veya bileşen ibaresi. Yapının gerekli bileşenleri yüklenir, ancak önerilen veya isteğe bağlı bileşenler yüklenmez. Ek bileşenleri genel olarak `--includeRecommended` ve/veya `--includeOptional`. Birden çok iş yükü veya `--add` bileşen eklemek için `--add Workload1 --add Workload2`komutu yineleyin (örneğin, ). Daha ince taneli denetim için, `;includeRecommended` kimlik `;includeOptional` ekleyebilirsiniz veya `--add Workload1;includeRecommended` (örneğin, `--add Workload2;includeRecommended;includeOptional`veya). Daha fazla bilgi için [İş Yükü ve bileşen iT'ler](workload-and-component-ids.md) sayfasına bakın. Bu seçeneği gerektiğinde yineleyebilirsiniz.|
| `--remove <one or more workload or component IDs>` | **İsteğe Bağlı**: Kaldırılacak bir veya daha fazla iş yükü veya bileşen ibaresi. Daha fazla bilgi için [İş Yükü ve bileşen t.c.](workload-and-component-ids.md) sayfamıza bakın. Bu seçeneği gerektiğinde yineleyebilirsiniz.|
| `--in <path>` | **İsteğe Bağlı**: URI veya yanıt dosyasına giden yol.  |
| `--all` | **İsteğe Bağlı**: Bir ürün için tüm iş yüklerinin ve bileşenlerinin yüklenip yüklenmeyeceği. |
| `--allWorkloads` | **İsteğe Bağlı**: Önerilen veya isteğe bağlı bileşenler olmayan tüm iş yüklerini ve bileşenleri yükler. |
| `--includeRecommended` | **İsteğe Bağlı**: Yüklenen iş yükleri için önerilen bileşenleri içerir, ancak isteğe bağlı bileşenleri içermez. İş yükleri ya `--allWorkloads` da `--add`. ile belirtilir |
| `--includeOptional` | **İsteğe Bağlı**: Yüklenen, ancak önerilen bileşenleri değil, yüklenen tüm iş yükleri için isteğe bağlı bileşenleri içerir. İş yükleri ya `--allWorkloads` da `--add`. ile belirtilir  |
| `--quiet, -q` | **İsteğe Bağlı**: Yüklemeyi gerçekleştirirken herhangi bir kullanıcı arabirimi görüntülemeyin. |
| `--passive, -p` | **İsteğe Bağlı**: Kullanıcı arabirimini görüntüleyin, ancak kullanıcıdan herhangi bir etkileşim talep etmeyin. |
| `--norestart` | **İsteğe Bağlı**: Varsa, makineyi `--passive` otomatik olarak yeniden başlatAn komutlar `--quiet` (gerekirse).  Ne belirtilmişse `--quiet` ne de `--passive` belirtilmişse bu yoksayılır.  |
| `--nickname <name>` | **İsteğe Bağlı**: Yüklü bir ürüne atamak için takma adı tanımlar. Takma ad 10 karakterden uzun olamaz.  |
| `--productKey` | **İsteğe Bağlı**: Bu, yüklü bir ürün için kullanılacak ürün anahtarını tanımlar. Biçimde `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` veya `xxxxxxxxxxxxxxxxxxxxxxxxx`25 alfanümerik karakterden oluşur. |
| `--help, --?, -h, -?` | Bu sayfanın çevrimdışı sürümünü görüntüleyin. |
| `--config <path>` | **İsteğe Bağlı** ve **Yeni 15.9**: Yükleme veya değiştirme işlemi sırasında, bu, daha önce kaydedilmiş bir yükleme yapılandırma dosyasına göre eklenecek iş yüklerini ve bileşenleri belirler. Bu işlem katkı maddesidir ve dosyada yoksa iş yükünü veya bileşeni kaldırmaz. Ayrıca, ürün için geçerli olmayan öğeler eklenmez. Bir dışa aktarma işlemi sırasında, bu yükleme yapılandırma dosyasını kaydetmek için konum belirler. |

::: moniker-end

::: moniker range="vs-2019"

| **Yükleme seçeneği** | **Açıklama** |
| ----------------------- | --------------- |
| `--installPath <dir>` | Harekete geçicisi için yükleme dizini. Install komutu için bu **Isteğe bağlıdır** ve örneğin yükleneceği yerdir. Diğer komutlar için bu **gereklidir** ve daha önce yüklenmiş örneğin yüklendiği yerdir. |
| `--addProductLang <language-locale>` | **İsteğe Bağlı**: Yükleme veya değiştirme işlemi sırasında, bu ürüne yüklenen UI dil paketlerini belirler. Birden çok dil paketi eklemek için komut satırında birden çok kez görünebilir. Yoksa, yükleme makine yerelliğini kullanır. Daha fazla bilgi için bu sayfadaki [dil yerelleri listesi](#list-of-language-locales) bölümüne bakın.|
| `--removeProductLang <language-locale>` | **İsteğe Bağlı**: Yükleme veya değiştirme işlemi sırasında, bu üründen kaldırılacak olan UI dil paketlerini belirler. Birden çok dil paketi eklemek için komut satırında birden çok kez görünebilir. Daha fazla bilgi için bu sayfadaki [dil yerelleri listesi](#list-of-language-locales) bölümüne bakın.|
| `--add <one or more workload or component IDs>` | **İsteğe Bağlı**: Eklenecek bir veya daha fazla iş yükü veya bileşen ibaresi. Yapının gerekli bileşenleri yüklenir, ancak önerilen veya isteğe bağlı bileşenler yüklenmez. Ek bileşenleri genel olarak `--includeRecommended` ve/veya `--includeOptional`. Birden çok iş yükü veya `--add` bileşen eklemek için `--add Workload1 --add Workload2`komutu yineleyin (örneğin, ). Daha ince taneli denetim için, `;includeRecommended` kimlik `;includeOptional` ekleyebilirsiniz veya `--add Workload1;includeRecommended` (örneğin, `--add Workload2;includeRecommended;includeOptional`veya). Daha fazla bilgi için [İş Yükü ve bileşen iT'ler](workload-and-component-ids.md) sayfasına bakın. Bu seçeneği gerektiğinde yineleyebilirsiniz.|
| `--remove <one or more workload or component IDs>` | **İsteğe Bağlı**: Kaldırılacak bir veya daha fazla iş yükü veya bileşen ibaresi. Daha fazla bilgi için [İş Yükü ve bileşen t.c.](workload-and-component-ids.md) sayfamıza bakın. Bu seçeneği gerektiğinde yineleyebilirsiniz.|
| `--in <path>` | **İsteğe Bağlı**: URI veya yanıt dosyasına giden yol.  |
| `--all` | **İsteğe Bağlı**: Bir ürün için tüm iş yüklerinin ve bileşenlerinin yüklenip yüklenmeyeceği. |
| `--allWorkloads` | **İsteğe Bağlı**: Önerilen veya isteğe bağlı bileşenler olmayan tüm iş yüklerini ve bileşenleri yükler. |
| `--includeRecommended` | **İsteğe Bağlı**: Yüklenen iş yükleri için önerilen bileşenleri içerir, ancak isteğe bağlı bileşenleri içermez. İş yükleri ya `--allWorkloads` da `--add`. ile belirtilir |
| `--includeOptional` | **İsteğe Bağlı**: Yüklenen, ancak önerilen bileşenleri değil, yüklenen tüm iş yükleri için isteğe bağlı bileşenleri içerir. İş yükleri ya `--allWorkloads` da `--add`. ile belirtilir  |
| `--quiet, -q` | **İsteğe Bağlı**: Yüklemeyi gerçekleştirirken herhangi bir kullanıcı arabirimi görüntülemeyin. |
| `--passive, -p` | **İsteğe Bağlı**: Kullanıcı arabirimini görüntüleyin, ancak kullanıcıdan herhangi bir etkileşim talep etmeyin. |
| `--norestart` | **İsteğe Bağlı**: Varsa, makineyi `--passive` otomatik olarak yeniden başlatAn komutlar `--quiet` (gerekirse).  Ne belirtilmişse `--quiet` ne de `--passive` belirtilmişse bu yoksayılır.  |
| `--nickname <name>` | **İsteğe Bağlı**: Yüklü bir ürüne atamak için takma adı tanımlar. Takma ad 10 karakterden uzun olamaz.  |
| `--productKey` | **İsteğe Bağlı**: Bu, yüklü bir ürün için kullanılacak ürün anahtarını tanımlar. Biçimde `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` veya `xxxxxxxxxxxxxxxxxxxxxxxxx`25 alfanümerik karakterden oluşur. |
| `--help, --?, -h, -?` | Bu sayfanın çevrimdışı sürümünü görüntüleyin. |
| `--config <path>` | **İsteğe Bağlı**: Yükleme veya değiştirme işlemi sırasında, bu, daha önce kaydedilmiş bir yükleme yapılandırma dosyasına göre eklenecek iş yüklerini ve bileşenleri belirler. Bu işlem katkı maddesidir ve dosyada yoksa iş yükünü veya bileşeni kaldırmaz. Ayrıca, ürün için geçerli olmayan öğeler eklenmez. Bir dışa aktarma işlemi sırasında, bu yükleme yapılandırma dosyasını kaydetmek için konum belirler. |

::: moniker-end

> [!IMPORTANT]
> Birden çok iş yükü ve bileşen belirtirken, her öğe için veya `--add` `--remove` komut satırı anahtarını yinelemeniz gerekir.

## <a name="layout-options"></a>Düzen seçenekleri

::: moniker range="vs-2017"

| **Düzen seçenekleri** | **Açıklama** |
| ----------------------- | --------------- |
| `--layout <dir>` | Çevrimdışı yükleme önbelleği oluşturmak için bir dizin belirtir. Daha fazla bilgi için [bkz.](create-a-network-installation-of-visual-studio.md)|
| `--lang <one or more language-locales>` | **İsteğe**Bağlı `--layout` : Belirtilen dil(ler) ile kaynak paketleri ile çevrimdışı yükleme önbelleği hazırlamak için kullanılır. Daha fazla bilgi için bu sayfadaki [dil yerelleri listesi](#list-of-language-locales) bölümüne bakın.|
| `--add <one or more workload or component IDs>` | **İsteğe Bağlı**: Eklenecek bir veya daha fazla iş yükü veya bileşen ibaresi. Yapının gerekli bileşenleri yüklenir, ancak önerilen veya isteğe bağlı bileşenler yüklenmez. Ek bileşenleri genel olarak `--includeRecommended` ve/veya `--includeOptional`. Daha ince taneli denetim için, `;includeRecommended` kimlik `;includeOptional` ekleyebilirsiniz veya `--add Workload1;includeRecommended` (örneğin, `--add Workload2;includeOptional`veya). Daha fazla bilgi için [İş Yükü ve bileşen iT'ler](workload-and-component-ids.md) sayfasına bakın. <br/>**Not**: `--add` Kullanılırsa, yalnızca belirtilen iş yükleri ve bileşenleri ve bunların bağımlılıkları indirilir. `--add` Belirtilmemişse, tüm iş yükleri ve bileşenler düzene karşı indirilir.|
| `--includeRecommended` | **İsteğe Bağlı**: Yüklenen iş yükleri için önerilen bileşenleri içerir, ancak isteğe bağlı bileşenleri içermez. İş yükleri ya `--allWorkloads` da `--add`. ile belirtilir |
| `--includeOptional` | **İsteğe Bağlı**: Düzene dahil edilen iş yükleri için önerilen *ve* isteğe bağlı bileşenleri içerir. İş yükleri `--add`' ile belirtilir.  |
| `--keepLayoutVersion` | **15.3'te yeni, isteğe bağlı**: Düzenin sürümünü güncelleştirmeden düzene değişiklik uygulayın. |
| `--verify` | **Yeni 15.3, isteğe bağlı**: Bir düzenin içeriğini doğrulayın. Bozuk veya eksik dosyalar listelenir. |
| `--fix` | **Yeni 15.3, isteğe bağlı**: Bir düzenin içeriğini doğrulayın. Herhangi bir dosya bozuk veya eksikse, yeniden indirilir. Düzeni düzeltmek için Internet erişimi gereklidir. |
| `--clean <one or more paths to catalogs>` | **15.3'te yeni, isteğe bağlı**: Bileşenlerin eski sürümlerini daha yeni bir sürüme güncelleştirilen bir düzenden kaldırır. |

| **Gelişmiş yükleme seçenekleri** | **Açıklama** |
| ----------------------- | --------------- |
| `--channelId <id>` | **İsteğe Bağlı**: Kurulacak örneğin kanal kimliği. Bu yükleme komutu için gereklidir ve belirtilirse diğer komutlar `--installPath` için yoksayılır. |
| `--channelUri <uri>` | **İsteğe bağlı**: Kanal manifestosunun URI'si. Güncelleştirmeler isyan değilse, `--channelUri` var olmayan bir dosyayı (örneğin, channelUri C:\doesntExist.chman) işaret edebilir. Bu yükleme komutu için kullanılabilir; diğer komutlar için yoksayılır. |
| `--installChannelUri <uri>` | **İsteğe Bağlı**: Yükleme için kullanılacak kanal manifestosunun URI'si. Güncelleştirmeleri algılamak için uri `--channelUri` `--installChannelUri` tarafından (belirtildiği nde belirtilmesi gereken) belirtilir. Bu yükleme komutu için kullanılabilir; diğer komutlar için yoksayılır. |
| `--installCatalogUri <uri>` | **İsteğe Bağlı**: Yükleme için kullanılacak katalog manifestosunun URI'si. Belirtildiği takdirde, kanal yöneticisi yükleme kanalı bildiriminde URI'yi kullanmadan önce bu URI'den katalog bildirimini indirmeye çalışır. Bu parametre, zaten indirilen ürün kataloğuyla düzen önbelleğinin oluşturulacağı çevrimdışı yüklemeyi desteklemek için kullanılır. Bu yükleme komutu için kullanılabilir; diğer komutlar için yoksayılır. |
| `--productId <id>` | **İsteğe bağlı** Yüklenecek örnek için ürünün kimliği. Bu, normal yükleme koşullarında önceden doldurulur. |
| `--wait` | **İsteğe Bağlı**: İşlem, bir çıkış kodu döndürmeden önce yükleme tamamlanana kadar bekler. Bu, yüklemenin tamamlanmasını beklemeniz gereken yüklemeleri otomatikleştirirken kullanışlıdır. |
| `--locale <language-locale>` | **İsteğe Bağlı**: Yükleyicinin kendisi için kullanıcı arabiriminin ekran dilini değiştirin. Ayar devam edecek. Daha fazla bilgi için bu sayfadaki [dil yerelleri listesi](#list-of-language-locales) bölümüne bakın.|
| `--cache` | **Yeni 15.2, isteğe bağlı**: Varsa, sonraki onarımlar için yüklendikten sonra paketleri tutulacaktır. Bu, sonraki yüklemeler, onarımlar veya değişiklikler için kullanılacak genel ilke ayarını geçersiz kılar. Varsayılan ilke paketleri önbelleğe almaktır. Bu kaldır komutu için yoksayılır. Daha fazla bilgi için [paket önbelleğini nasıl devre dışı dışı kakacağını veya taşıyacağını zedeyi](disable-or-move-the-package-cache.md) okuyun. |
| `--nocache` | **Yeni 15.2, isteğe bağlı**: Varsa, paketler yüklendikten veya onarıldıktan sonra silinir. Yalnızca gerektiğinde yeniden indirilir ler ve kullanımdan sonra tekrar silinirler. Bu, sonraki yüklemeler, onarımlar veya değişiklikler için kullanılacak genel ilke ayarını geçersiz kılar. Varsayılan ilke paketleri önbelleğe almaktır. Bu kaldır komutu için yoksayılır. Daha fazla bilgi için [paket önbelleğini nasıl devre dışı dışı kakacağını veya taşıyacağını zedeyi](disable-or-move-the-package-cache.md) okuyun. |
| `--noUpdateInstaller` | **15.2'de yeni, isteğe bağlı**: Varsa, sessiz belirtildiğinde yükleyicinin kendisini güncellemesini engeller. Yükleyici komutu başarısız olur ve bir yükleyici güncelleştirmesi gerektiğinde noUpdateInstaller sessiz belirtilirse sıfır olmayan bir çıkış kodu döndürün. |
| `--noWeb` | **Yeni 15.3, isteğe bağlı**: Varsa, Visual Studio kurulum Visual Studio yüklemek için düzen dizininizdeki dosyaları kullanır. Bir kullanıcı düzende olmayan bileşenleri yüklemeye çalışırsa, kurulum başarısız olur.  Daha fazla bilgi için [ağ yüklemesinden dağıtma'ya](create-a-network-installation-of-visual-studio.md)bakın. <br/><br/> **Önemli**: Bu anahtar Visual Studio kurulumunun güncelleştirmeleri denetlemesi engel değildir. Daha fazla bilgi [için, ağ tabanlı Visual Studio dağıtımlarında Denetim güncelleştirmelerine](controlling-updates-to-visual-studio-deployments.md)bakın. |
| `--path <name>=<path>` | **Yeni 15.7, isteğe bağlı**: Yükleme için özel yükleme yollarını belirtmek için kullanılır. Desteklenen yol adları paylaşılır, önbelleğe alınır ve yüklenir. |
| `--path cache=<path>` | **Yeni 15.7, isteğe bağlı**: Yükleme dosyalarını indirmek için belirttiğiniz konumu kullanır. Bu konum yalnızca Visual Studio'nun ilk yüklenmesiyle ayarlanabilir. Örnek: `--path cache="C:\VS\cache"` |
| `--path shared=<path>` | **Yeni 15.7, isteğe bağlı**: Yan yana Visual Studio yüklemeleri için paylaşılan dosyaları içerir. Bazı araçlar ve SDK'lar bu sürücüdeki bir konuma yüklenirken, bazıları bu ayarı geçersiz kılabilir ve başka bir sürücüye yüklenebilir. Örnek: `--path shared="C:\VS\shared"` <br><br>Önemli: Bu yalnızca bir kez ve Visual Studio yüklü ilk kez ayarlanabilir. |
| `--path install=<path>` | **Yeni 15.7, isteğe** `–-installPath`bağlı : Eşdeğer . Özellikle, `--installPath "C:\VS"` `--path install="C:\VS"` ve eşdeğerdir. Bu komutlardan yalnızca biri aynı anda kullanılabilir. |

::: moniker-end

::: moniker range="vs-2019"

| **Düzen seçenekleri** | **Açıklama** |
| ----------------------- | --------------- |
| `--layout <dir>` | Çevrimdışı yükleme önbelleği oluşturmak için bir dizin belirtir. Daha fazla bilgi için [bkz.](create-a-network-installation-of-visual-studio.md)|
| `--lang <one or more language-locales>` | **İsteğe**Bağlı `--layout` : Belirtilen dil(ler) ile kaynak paketleri ile çevrimdışı yükleme önbelleği hazırlamak için kullanılır. Daha fazla bilgi için bu sayfadaki [dil yerelleri listesi](#list-of-language-locales) bölümüne bakın.|
| `--add <one or more workload or component IDs>` | **İsteğe Bağlı**: Eklenecek bir veya daha fazla iş yükü veya bileşen ibaresi. Yapının gerekli bileşenleri yüklenir, ancak önerilen veya isteğe bağlı bileşenler yüklenmez. Ek bileşenleri genel olarak `--includeRecommended` ve/veya `--includeOptional`. Daha ince taneli denetim için, `;includeRecommended` kimlik `;includeOptional` ekleyebilirsiniz veya `--add Workload1;includeRecommended` (örneğin, `--add Workload2;includeOptional`veya). Daha fazla bilgi için [İş Yükü ve bileşen iT'ler](workload-and-component-ids.md) sayfasına bakın. <br/>**Not**: `--add` Kullanılırsa, yalnızca belirtilen iş yükleri ve bileşenleri ve bunların bağımlılıkları indirilir. `--add` Belirtilmemişse, tüm iş yükleri ve bileşenler düzene karşı indirilir.|
| `--includeRecommended` | **İsteğe Bağlı**: Yüklenen iş yükleri için önerilen bileşenleri içerir, ancak isteğe bağlı bileşenleri içermez. İş yükleri ya `--allWorkloads` da `--add`. ile belirtilir |
| `--includeOptional` | **İsteğe Bağlı**: Düzene dahil edilen iş yükleri için önerilen *ve* isteğe bağlı bileşenleri içerir. İş yükleri `--add`' ile belirtilir.  |
| `--keepLayoutVersion` | **İsteğe Bağlı**: Düzenin sürümünü güncelleştirmeden düzene değişiklik uygulayın. |
| `--verify` | **İsteğe Bağlı**: Bir düzenin içeriğini doğrulayın. Bozuk veya eksik dosyalar listelenir. |
| `--fix` | **İsteğe Bağlı**: Bir düzenin içeriğini doğrulayın.  Herhangi bir dosya bozuk veya eksikse, yeniden indirilir. Düzeni düzeltmek için Internet erişimi gereklidir. |
| `--clean <one or more paths to catalogs>` | **İsteğe Bağlı**: Bileşenlerin eski sürümlerini daha yeni bir sürüme güncelleştirilen bir düzenden kaldırır. |

| **Gelişmiş yükleme seçenekleri** | **Açıklama** |
| ----------------------- | --------------- |
| `--channelId <id>` | **İsteğe Bağlı**: Kurulacak örneğin kanal kimliği. Bu yükleme komutu için gereklidir ve belirtilirse diğer komutlar `--installPath` için yoksayılır. |
| `--channelUri <uri>` | **İsteğe bağlı**: Kanal manifestosunun URI'si. Güncelleştirmeler isyan değilse, `--channelUri` var olmayan bir dosyayı (örneğin, channelUri C:\doesntExist.chman) işaret edebilir. Bu yükleme komutu için kullanılabilir; diğer komutlar için yoksayılır. |
| `--installChannelUri <uri>` | **İsteğe Bağlı**: Yükleme için kullanılacak kanal manifestosunun URI'si. Güncelleştirmeleri algılamak için uri `--channelUri` `--installChannelUri` tarafından (belirtildiği nde belirtilmesi gereken) belirtilir. Bu yükleme komutu için kullanılabilir; diğer komutlar için yoksayılır. |
| `--installCatalogUri <uri>` | **İsteğe Bağlı**: Yükleme için kullanılacak katalog manifestosunun URI'si. Belirtildiği takdirde, kanal yöneticisi yükleme kanalı bildiriminde URI'yi kullanmadan önce bu URI'den katalog bildirimini indirmeye çalışır. Bu parametre, zaten indirilen ürün kataloğuyla düzen önbelleğinin oluşturulacağı çevrimdışı yüklemeyi desteklemek için kullanılır. Bu yükleme komutu için kullanılabilir; diğer komutlar için yoksayılır. |
| `--productId <id>` | **İsteğe bağlı** Yüklenecek örnek için ürünün kimliği. Bu, normal yükleme koşullarında önceden doldurulur. |
| `--wait` | **İsteğe Bağlı**: İşlem, bir çıkış kodu döndürmeden önce yükleme tamamlanana kadar bekler. Bu, yüklemenin tamamlanmasını beklemeniz gereken yüklemeleri otomatikleştirirken kullanışlıdır. |
| `--locale <language-locale>` | **İsteğe Bağlı**: Yükleyicinin kendisi için kullanıcı arabiriminin ekran dilini değiştirin. Ayar devam edecek. Daha fazla bilgi için bu sayfadaki [dil yerelleri listesi](#list-of-language-locales) bölümüne bakın.|
| `--cache` | **İsteğe Bağlı**: Varsa, sonraki onarımlar için yüklendikten sonra paketler saklanır. Bu, sonraki yüklemeler, onarımlar veya değişiklikler için kullanılacak genel ilke ayarını geçersiz kılar. Varsayılan ilke paketleri önbelleğe almaktır. Bu kaldır komutu için yoksayılır. Daha fazla bilgi için [paket önbelleğini nasıl devre dışı dışı kakacağını veya taşıyacağını zedeyi](disable-or-move-the-package-cache.md) okuyun. |
| `--nocache` | **İsteğe Bağlı**: Varsa, paketler yüklendikten veya onarıldıktan sonra silinir. Yalnızca gerektiğinde yeniden indirilir ler ve kullanımdan sonra tekrar silinirler. Bu, sonraki yüklemeler, onarımlar veya değişiklikler için kullanılacak genel ilke ayarını geçersiz kılar. Varsayılan ilke paketleri önbelleğe almaktır. Bu kaldır komutu için yoksayılır. Daha fazla bilgi için [paket önbelleğini nasıl devre dışı dışı kakacağını veya taşıyacağını zedeyi](disable-or-move-the-package-cache.md) okuyun. |
| `--noUpdateInstaller` | **İsteğe Bağlı**: Varsa, sessiz belirtildiğinde yükleyicinin kendisini güncelleştirmesini engeller. Yükleyici komutu başarısız olur ve bir yükleyici güncelleştirmesi gerektiğinde noUpdateInstaller sessiz belirtilirse sıfır olmayan bir çıkış kodu döndürün. |
| `--noWeb` | **İsteğe Bağlı**: Varsa, Visual Studio kurulumu Visual Studio'yu yüklemek için düzen dizinizdeki dosyaları kullanır. Bir kullanıcı düzende olmayan bileşenleri yüklemeye çalışırsa, kurulum başarısız olur.  Daha fazla bilgi için [ağ yüklemesinden dağıtma'ya](create-a-network-installation-of-visual-studio.md)bakın. <br/><br/> **Önemli**: Bu anahtar Visual Studio kurulumunun güncelleştirmeleri denetlemesi engel değildir. Daha fazla bilgi [için, ağ tabanlı Visual Studio dağıtımlarında Denetim güncelleştirmelerine](controlling-updates-to-visual-studio-deployments.md)bakın. **16.3.5'te yeni**: Bu anahtar, çevrimdışı yüklemeler ve güncelleştirmelerle hataları önler ve performansı artırır.|
| `--path <name>=<path>` | **İsteğe Bağlı**: Yükleme için özel yükleme yollarını belirtmek için kullanılır. Desteklenen yol adları paylaşılır, önbelleğe alınır ve yüklenir. |
| `--path cache=<path>` | **İsteğe Bağlı**: Yükleme dosyalarını indirmek için belirttiğiniz konumu kullanır. Bu konum yalnızca Visual Studio'nun ilk yüklenmesiyle ayarlanabilir. Örnek: `--path cache="C:\VS\cache"` |
| `--path shared=<path>` | **İsteğe Bağlı**: Yan yana Visual Studio yüklemeleri için paylaşılan dosyaları içerir. Bazı araçlar ve SDK'lar bu sürücüdeki bir konuma yüklenirken, bazıları bu ayarı geçersiz kılabilir ve başka bir sürücüye yüklenebilir. Örnek: `--path shared="C:\VS\shared"` <br><br>Önemli: Bu yalnızca bir kez ve Visual Studio yüklü ilk kez ayarlanabilir. |
| `--path install=<path>` | **İsteğe**Bağlı `–-installPath`: Eşdeğer . Özellikle, `--installPath "C:\VS"` `--path install="C:\VS"` ve eşdeğerdir. Bu komutlardan yalnızca biri aynı anda kullanılabilir. |

::: moniker-end

## <a name="list-of-workload-ids-and-component-ids"></a>İş yükü t'leri ve bileşen ilikleri listesi

Visual Studio ürününe göre sıralanmış iş yükü ve bileşen işleri listesi için [Visual Studio işyükü ve bileşen işleri sayfasına](workload-and-component-ids.md) bakın.

## <a name="list-of-language-locales"></a>Dil yerelleri listesi

| **Dil-yerel** | **Dil** |
| ----------------------- | --------------- |
| Cs-cz | Çekçe |
| De-de | Almanca |
| En-us | Türkçe |
| Es-es | İspanyolca |
| Fr-fr | Fransızca |
| It-it | İtalyanca |
| Ja-jp | Japonca |
| Ko-kr | Korece |
| Pl-pl | Lehçe |
| Pt-br | Portekizce - Brezilya |
| Ru-ru | Rusça |
| Tr-tr | Türkçe |
| Zh-cn | Çince - Basitleştirilmiş |
| Zh-tw | Çince - Geleneksel |

## <a name="error-codes"></a>Hata kodları

İşlemin sonucuna bağlı olarak, `%ERRORLEVEL%` ortam değişkeni aşağıdaki değerlerden birine ayarlanır:

[!INCLUDE[install-error-codes-md](includes/install-error-codes-md.md)]

Her işlem, diziniçinde `%TEMP%` yüklemenin ilerlemesini gösteren birkaç günlük dosyası oluşturur. Klasörü tarihe göre sıralayın ve `dd_bootstrapper`sırasıyla `dd_client` `dd_setup` bootstrapper, yükleyici uygulaması ve kurulum motoru yla başlayan dosyaları arayın.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio kurulumu için komut satırı parametre örnekleri](command-line-parameter-examples.md)
- [Visual Studio'nun çevrimdışı yüklemesini oluşturma](create-an-offline-installation-of-visual-studio.md)
- [Yanıt dosyası ile Visual Studio yüklemesini otomatikleştirme](automated-installation-with-response-file.md)
- [Visual Studio iş yükü ve bileşen kimlikleri](workload-and-component-ids.md)
