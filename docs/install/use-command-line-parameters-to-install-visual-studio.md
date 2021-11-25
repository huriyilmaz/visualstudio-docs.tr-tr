---
title: Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme
titleSuffix: ''
description: Visual Studio yüklemenizi denetlemek veya özelleştirmek için komut satırı parametrelerini nasıl kullanacağınızı öğrenin.
ms.date: 11/23/2021
ms.topic: conceptual
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 6e98285f50105ab49964bb1cc1b633cc505af7a1
ms.sourcegitcommit: 2281b4f1f8737f263c0d7e55e00b5ec81517327d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2021
ms.locfileid: "133108854"
---
# <a name="use-command-line-parameters-to-install-visual-studio"></a>Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme

program aracılığıyla veya bir komut isteminden Visual Studio yüklediğinizde, aşağıdaki eylemleri gerçekleştirmek üzere yüklemeyi denetlemek veya özelleştirmek için çeşitli komut satırı parametreleri kullanabilirsiniz:

- Yüklemeyi istemci üzerinde belirli seçenekler ve davranışlar önceden seçilmiş olarak başlatın.
- Yükleme işlemini otomatikleştirin.
- İstemci makinelerini yüklemek veya güncelleştirmek için ürün dosyalarının bir ağ yerleşimini oluşturun veya güncelleştirin.

Çoğu komut satırı seçeneği, yükleme işlemini başlatan küçük (~ 1 MB) dosya (örneğin, vs_enterprise.exe) olan kurulum Önyükleyicisi ile birlikte kullanılır.  Aşağıda listelenen tüm komutlar ve parametreler, bootstrapile çalışacak şekilde tasarlanmıştır. 

Ayrıca, ağ düzeninizi program aracılığıyla güncelleştirmek için [Microsoft Update kataloğundan](https://catalog.update.microsoft.com)indirilebilir olan yönetici güncelleştirme paketini kullanmak da mümkündür. Bunun nasıl yapılacağı hakkında daha fazla bilgi için, güncelleştirme bölümünde bulunabilir [veya Düzen belgelerinizde değişiklik](/visualstudio/install/create-a-network-installation-of-visual-studio#update-the-layout-to-a-specific-version-of-the-product) yapabilirsiniz.  

::: moniker range="vs-2017"

önyükleyici Visual Studio 2017 sürüm 15,9 ' ye ulaşmak için aşağıdaki önyükleyici dosyalarından birini indirin:

| **Sürüm**                                  | **Önyükleyici**       |
|----------------------------------------------|---------------------|
| Visual Studio Enterprise 2017 sürüm 15,9   | [vs_enterprise.exe](https://aka.ms/vs/15/release/vs_enterprise.exe)  |
| Visual Studio Professional 2017 sürüm 15,9 | [vs_professional.exe](https://aka.ms/vs/15/release/vs_professional.exe)  |
| Visual Studio Derleme Araçları 2017 sürüm 15,9  | [vs_buildtools.exe](https://aka.ms/vs/15/release/vs_buildtools.exe)   |

::: moniker-end

::: moniker range="vs-2019"

aşağıdaki tablodan Visual Studio 2019 bootstrap' i edinebilirsiniz. alternatif olarak, Visual Studio 2019 ' nin belirli bir sürümünü istiyorsanız, seçtiğiniz Visual Studio sürümü ve sürümü için sabit sürüm bootstrapbağlantılarına yönelik [Visual Studio 2019 yayınlar](/visualstudio/releases/2019/history#installing-an-earlier-release) sayfasına gidebilirsiniz.

| **Sürüm**                     | **Önyükleyici**                                                             |
|---------------------------------|------------------------------------------------------------------------------|
| Visual Studio 2019 Enterprise sürüm 16,11   | [vs_enterprise.exe](https://aka.ms/vs/16/release/vs_enterprise.exe)     |
| Visual Studio 2019 Professional sürüm 16,11| [vs_professional.exe](https://aka.ms/vs/16/release/vs_professional.exe) |
| Visual Studio 2019 derleme araçları sürüm 16,11 | [vs_buildtools.exe](https://aka.ms/vs/16/release/vs_buildtools.exe)     |

::: moniker-end

::: moniker range=">=vs-2022"

geçerli kanalın en son sürümünü her zaman yükleyecek Visual Studio 2022 için en son bootstrap'ı almak için aşağıdaki dosyalardan birini indirin. alternatif olarak, belirli bir sürümü veya Visual Studio 2022 ' nin belirli bir kanalını yüklemek isterseniz, her bir bakım sürümü için sabit sürüm bootstrapbağlantıları olan [Visual Studio 2022 yayın geçmişi](/visualstudio/releases/2022/release-history#release-dates-and-build-numbers) sayfasına gidin. 

| **Sürüm**                      | **Önyükleyici**                                                                                   |
|----------------------------|-------------------------------------------------------------------------------------------|
| Visual Studio 2022 Enterprise   | [vs_enterprise.exe](https://aka.ms/vs/17/release/vs_enterprise.exe)     |
| Visual Studio 2022 Professional | [vs_professional.exe](https://aka.ms/vs/17/release/vs_professional.exe) |
| Visual Studio 2022 Community    | [vs_community.exe](https://aka.ms/vs/17/release/vs_community.exe)       |
| Visual Studio 2022 derleme araçları   | [vs_buildtools.exe](https://aka.ms/vs/17/release/vs_buildtools.exe)         |

::: moniker-end

::: moniker range="vs-2017"

>[!TIP]
>Daha önce bir önyükleyici dosyası indirdiyseniz ve hangi sürümün olduğunu doğrulamak istiyorsanız, bunun nasıl yapıldığını burada bulabilirsiniz. Windows, dosya gezgini 'ni açın, önyükleyici dosyasına sağ tıklayın, **özellikler**' i seçin, **ayrıntılar** sekmesini seçin ve ardından **ürün sürümü** numarasını görüntüleyin. bu sayıyı Visual Studio bir sürümüyle eşleştirmek için, [Visual Studio derleme numaraları ve sürüm tarihleri](visual-studio-build-numbers-and-release-dates.md) sayfasına bakın.

::: moniker-end

::: moniker range="vs-2019"

>[!TIP]
>Daha önce bir önyükleyici dosyası indirdiyseniz ve sürümünü doğrulamak istiyorsanız, bunun nasıl yapıldığını burada bulabilirsiniz. Windows, dosya gezgini 'ni açın, önyükleyici dosyasına sağ tıklayın, **özellikler**' i seçin, **ayrıntılar** sekmesini seçin ve ardından **ürün sürümü** numarasını görüntüleyin. bu numarayı bir Visual Studio sürümüyle eşleştirmek için, [Visual Studio 2019 yayınları](/visualstudio/releases/2019/history) sayfasının altındaki tabloya bakın.

::: moniker-end

::: moniker range=">=vs-2022"

>[!TIP]
>Daha önce bir önyükleyici dosyası indirdiyseniz ve hangi sürümün yükleneceğini doğrulamak istiyorsanız, şöyle olur. Windows, dosya gezgini 'ni açın, önyükleyici dosyasına sağ tıklayın, **özellikler** ' i seçin ve **ayrıntılar** sekmesini seçin. **Ürün sürümü** alanı, önyükleyicinin yükleneceği [kanalı ve sürümü](/visualstudio/releases/2022/vs2022-release-rhythm) anlatmaktadır. Sürüm numarası her zaman "belirtilen sayının en son bakım sürümü" olarak okunmalı ve açıkça belirtilmediği sürece kanal geçerli olur. Bu nedenle, LTSC 17,0 ürün sürümüne sahip bir önyükleyici, 17,0 LTSC kanalında bulunan en son 17.0. x bakım sürümünü yükler. yalnızca Visual Studio 2022 ' i belirten ürün sürümüne sahip bir önyükleyici, geçerli kanala Visual Studio 2022 ' nin en son sürümünü yükler.

::: moniker-end

## <a name="bootstrapper-commands-and-command-line-parameters"></a>Önyükleyici komutları ve komut satırı parametreleri

ürünü yüklemek veya bir düzeni sürdürmek için program aracılığıyla Visual Studio önyükleyici çağrılırken, ilk parametre gerçekleştirilecek işlemi açıklayan komuttur (fiil). İki kısa çizgi (--) önekli sonraki isteğe bağlı komut satırı parametreleri, bu işlemin nasıl gerçekleşmesi gerektiğini daha da tanımlar. tüm Visual Studio komut satırı parametreleri büyük/küçük harfe duyarlıdır ve [komut satırı parametre örnekleri](command-line-parameter-examples.md) sayfasında ek örnekler bulunabilir.

Söz dizimi örneği: `vs_enterprise.exe [command] <optional parameters>...`

| **Komutundaki** | **Açıklama**                                                                                                         |
|-------------|-------------------------------------------------------------------------------------------------------------------------|
| adet     | Varsayılan komutun her ikisi de ürünü yüklerse ve tüm düzen bakım işlemlerinde kullanılır.                    |
| `modify`    | Yüklü bir ürünü değiştirir.                                                                                          |
| `update`    | Yüklü bir ürünü güncelleştirir.                                                                                           |
| `repair`    | Yüklü bir ürünü onarır.                                                                                           |
| `uninstall` | Yüklü bir ürünü kaldırır.                                                                                        |
| `export`    | Yükleme seçimini bir yükleme yapılandırma dosyasına aktarır. **Note**: yalnızca vs_installer.exe ile kullanılabilir. |

> [!IMPORTANT]
> Birden çok farklı iş yükü veya bileşen ya da dil belirtirken, `--add` `--remove` her öğe için veya komut satırı anahtarını tekrarlamanız gerekir.

| **Parametreler**                                     | **Açıklama**                                                            |
|----------------------------------------------------|----------------------------------------------------------------------|
| `--installPath <dir>`                              | Varsayılan install komutu için, bu parametre **Isteğe bağlıdır** ve örneğin istemci makineye nereye yükleneceğini açıklar. Güncelleştirme veya değiştirme gibi diğer komutlar için, bu parametre **gereklidir** ve örneğin üzerinde işlem yapması için yükleme dizinini gösterir.                                                   |
| `--add <one or more workload or component IDs>`    | **Isteğe bağlı**: bir Install veya Modify komutu sırasında, bu yinelenebilir parametre, eklenecek bir veya daha fazla iş yükünü veya bileşen kimliğini belirtir. Yapıtın gerekli bileşenleri yüklendi, ancak önerilen veya isteğe bağlı bileşenler değil. `--includeRecommended`Ve/veya parametrelerini kullanarak ek bileşenleri genel olarak denetleyebilirsiniz `--includeOptional` . Birden çok iş yükünü veya bileşeni eklemek için, `--add` komutunu tekrarlayın (örneğin, `--add Workload1 --add Workload2` ). Daha ayrıntılı denetim için, KIMLIĞE ekleme yapabilir `;includeRecommended` `;includeOptional` (örneğin, `--add Workload1;includeRecommended` veya `--add Workload2;includeRecommended;includeOptional` ). Daha fazla bilgi için bkz. [Iş yükü ve bileşen kimlikleri](workload-and-component-ids.md) sayfası. |
| `--remove <one or more workload or component IDs>` | **Isteğe bağlı**: bir değiştirme komutu sırasında, bu yinelenebilir parametre, kaldırılacak bir veya daha fazla iş yükünü veya bileşen kimliğini belirtir. Parametresi için benzer şekilde tamamlar ve davranır `--add` .   |
| `--addProductLang <language-locale>`               | **Isteğe bağlı**: bir Install veya Modify komutu sırasında, bu yinelenebilir parametre, ürünle birlikte yüklenmesi gereken kullanıcı arabirimi dil paketlerini belirtir. Mevcut değilse, yükleme makine yerel ayarına karşılık gelen dil paketini kullanır. Daha fazla bilgi için bu sayfadaki [dil yerel ayarları listesi](#list-of-language-locales) bölümüne bakın.  |
| `--removeProductLang <language-locale>`            | **Isteğe bağlı**: bir Install veya Modify komutu sırasında, bu yinelenebilir parametre, üründen kaldırılması gereken kullanıcı arabirimi dil paketlerini belirler.  Parametresi için benzer şekilde tamamlar ve davranır `--addProductLang` . |
| `--in <path>`                                      | **Isteğe bağlı**: yapılandırma ayarlarını içerebilen bir [yanıt dosyasının](automated-installation-with-response-file.md)URI 'si veya yolu.  |
| `--all`                                            | **Isteğe bağlı**: bir yükleme veya değiştirme komutu sırasında, bu parametre, ürüne yönelik tüm iş yüklerinin ve bileşenlerin yüklenmesine neden olur.  |
| `--allWorkloads`                                   | **Isteğe bağlı**: bir yükleme veya değiştirme komutu sırasında, bu parametre tüm iş yüklerini ve bileşenleri yükler, ancak önerilen veya isteğe bağlı bileşenler içermez.  |
| `--includeRecommended`                             | **Isteğe bağlı**: bir yükleme veya değiştirme komutu sırasında, bu parametre yüklü olan ancak isteğe bağlı bileşenleri olmayan tüm iş yükleri için önerilen bileşenleri içerir. İş yükleri veya ile belirtilir `--allWorkloads` `--add` .  |
| `--includeOptional`                                | **Isteğe bağlı**: bir yükleme veya değiştirme komutu sırasında, bu parametre, yüklenmiş ancak önerilen bileşenleri değil, yüklü olan tüm iş yükleri için isteğe bağlı bileşenleri içerir. İş yükleri veya ile belirtilir `--allWorkloads` `--add` . |
| `--quiet, -q`                                      | **Isteğe bağlı**: herhangi bir komutla birlikte kullanılırsa, bu parametre, komut yürütülürken herhangi bir kullanıcı arabiriminin görüntülenmesini önler.    |
| `--passive, -p`                                    | **Isteğe bağlı**: Bu parametre, Kullanıcı arabiriminin etkileşimli olmayan bir şekilde görüntülenmesine neden olur. Bu parametre, parametresini (ve aslında geçersiz Kılmalarda) birbirini dışlar `--quiet` .   |
| `--norestart`                                      | **Isteğe bağlı**: Bu parametre `--passive` ya da parametreleriyle eşleştirilmelidir `--quiet` .  Yükleme, güncelleştirme veya değiştirme komutu sırasında parametresini eklemek, `--norestart` gerekli tüm yeniden başlatmayı erteler.    |
| `--force`                                          | **isteğe bağlı**: bu parametre, Visual Studio bir işlem kullanımda olsa bile Visual Studio kapanmaya zorlar.   |
| `--installWhileDownloading`                        | **isteğe bağlı**: bir ınstall, update veya modify komutu sırasında, bu parametre Visual Studio ürünün hem paralel olarak hem de yüklenmesini sağlar. Bu varsayılan deneyimdir.   |
| `--downloadThenInstall`                            | **İsteğe** bağlı: Yükleme, güncelleştirme veya değiştirme komutu sırasında, bu parametre Visual Studio yüklemeden önce tüm dosyaları indirmeye zorunlu kullanır. Bu, parametresinden birbirini `--installWhileDownloading` dışlar.   |
| `--channelURI`                                     | **İsteğe** bağlı: Güncelleştirme komutu sırasında, güncelleştirme ayarları konumunu değiştirmek için yeni bir channelURI'yi geçebilirsiniz.  Yapılandırmak için hangi örneğinin çok açık olduğunu açıkça ifade etmek için --installPath parametresiyle Visual Studio önerilir. |
| `--nickname <name>`                                | **İsteğe** bağlı: Yükleme komutu sırasında, bu parametre yüklü bir ürüne atanma takma adını tanımlar. Takma ad 10 karakterden uzun olamaz. |
| `--productKey`                                     | **İsteğe** bağlı: Yükleme komutu sırasında, bu parametre yüklü bir ürün için kullanmak üzere ürün anahtarını tanımlar. biçiminde 25 alfasayısal karakterden `xxxxxxxxxxxxxxxxxxxxxxxxx` oluşur.  |
| `--help, --?, -h, -?`                              | Bu sayfanın çevrimdışı bir sürümünü görüntüler.     |
| `--config <path>`                                  | **İsteğe** bağlı: Yükleme veya değiştirme işlemi sırasında bu, daha önce kaydedilmiş bir yükleme yapılandırma dosyasını temel alarak eklenecek iş yüklerini ve bileşenleri belirler. Bu işlem eklenebilirdir ve dosyada mevcut olmayan iş yükünü veya bileşeni kaldırmaz. Ayrıca ürün için geçerli olan öğeler eklenmez. Bir dışarı aktarma işlemi sırasında, bu yükleme yapılandırma dosyasını kaydedecek konumu belirler.                                                                                                                                                                                                                                                                                                                                                  |

## <a name="layout-command-and-command-line-parameters"></a>Düzen komutu ve komut satırı parametreleri

Tüm düzen yönetimi işlemleri, bir düzen oluşturuyor veya güncelleştiriyorsanız, komutun varsayılan Yükle (boş) olduğunu varsayer. Bu nedenle tüm düzen yönetimi işlemlerinin ilk gerekli parametreyle başlaması `--layout` gerekir. Aşağıdaki tabloda, komut satırı kullanarak düzen oluşturmak veya güncelleştirmek [için kullanabileceğiniz diğer](/visualstudio/install/create-a-network-installation-of-visual-studio) parametreler açıklanmıştır. 

| **Düzen parametreleri**                           | **Açıklama**                                        |
|-------------------------------------------------|----------------------------------------------------------------------|
| `--layout <dir>`                                | Çevrimdışı yükleme önbelleği oluşturmak veya güncelleştirmek için bir dizin belirtir. Daha fazla bilgi için, [bkz. Create a network-based installation of Visual Studio.](create-a-network-installation-of-visual-studio.md)                       |
| `--lang <one or more language-locales>`         | **İsteğe** bağlı: `--layout` Belirtilen dillere sahip kaynak paketleriyle çevrimdışı yükleme önbelleği hazırlamak için ile kullanılır. Daha fazla bilgi için bu [sayfanın Dil yerel dillerinin](#list-of-language-locales) listesi bölümüne bakın.       |
| `--add <one or more workload or component IDs>` | **İsteğe** bağlı: Eklemek için bir veya daha fazla iş yükü veya bileşen kimlikleri. Yapıt için gerekli bileşenler yüklenir, ancak önerilen veya isteğe bağlı bileşenler yüklenmez. ve/veya kullanarak ek bileşenleri küresel `--includeRecommended` olarak kontrol `--includeOptional` edin. Daha ince bir denetim için, kimliği (örneğin, veya ) ekli veya `;includeRecommended` buna `;includeOptional` `--add Workload1;includeRecommended` eklemeler yapmak için. `--add Workload2;includeOptional` Daha fazla bilgi için İş yükü [ve bileşen kimlikleri sayfasına](workload-and-component-ids.md) bakın. <br/>**Not:** `--add` Kullanılırsa, yalnızca belirtilen iş yükleri ve bileşenler ve bağımlılıkları indirilir. `--add`Belirtilmezse, tüm iş yükleri ve bileşenler düzene indirilir. |
| `--includeRecommended`                          | **İsteğe** bağlı: Yüklü olan tüm iş yükleri için önerilen bileşenleri içerir, ancak isteğe bağlı bileşenleri dahil değildir. İş yükleri veya ile `--allWorkloads` `--add` belirtilir.         |
| `--includeOptional`                             | **İsteğe** bağlı: Düzende *yer alan* tüm iş yükleri için önerilen ve isteğe bağlı bileşenleri içerir. İş yükleri ile `--add` belirtilir.                        |
| `--keepLayoutVersion`                           | **İsteğe** bağlı: Düzende yer alan ürün sürümünü güncelleştirmeden düzende yapılan değişiklikleri uygulama.   |
| `--useLatestInstaller`         | **İsteğe** bağlı: Varsa, Visual Studio Yükleyicisi sürümü daha yeni bir sürüme ait olsa bile düzeninize dahil edilir. En son yükleyicide bulunan yeni özelliklerden veya hata düzeltmelerinden yararlanmak için bu yararlı olabilir. Daha fazla bilgi için Düzeni her [zaman en son yükleyiciyi kullanmak üzere yapılandırma belgelerine](/visualstudio/install/create-a-network-installation-of-visual-studio#configure-the-layout-to-always-use-the-latest-installer) bakın. |
| `--verify`                                      | **İsteğe** bağlı: Bir düzenin içeriğini doğrulayın. Bozuk veya eksik dosyalar listelenir.            |
| `--fix`                                         | **İsteğe** bağlı: Bir düzenin içeriğini doğrulayın.  Bozuk veya eksik olan dosyalar yeniden yüklenir. Bir düzeni düzeltmek için İnternet erişimi gereklidir.           |
| `--clean <one or more paths to catalogs>`       | **İsteğe** bağlı: Bileşenlerin eski sürümlerini, daha yeni bir sürüme güncelleştirilmiş bir düzenden kaldırır.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |

| **Gelişmiş düzen parametreleri** | **Açıklama**                                  |
|--------------------------------|--------------------------------------------------|
| `--channelId <id>`             | **İsteğe** bağlı: Yüklanacak örneğin kanalının kimliği. Bu, yükleme komutu için gereklidir ve belirtilirse diğer komutlar için `--installPath` yoksayılır.        |
| `--channelUri <uri>`           | **İsteğe** bağlı: Kanal bildiriminin URI'si. Bu değer [güncelleştirmelerin kaynak konumunu yönetir](/visualstudio/install/update-visual-studio#configure-source-location-of-updates-1) ve ilk değer [düzenin response.json](/visualstudio/install/create-a-network-installation-of-visual-studio#configure-initial-client-installation-defaults-for-this-layout)dosyasında yapılandırılır.  Güncelleştirmeler gerektirilmemişse, mevcut olmayan bir dosyaya işaret ediyor `--channelUri` olabilir (örneğin, --channelUri C:\doesntExist.chman). Bu, yükleme komutu için kullanılabilir; diğer komutlar için yoksayılır.  |
| `--installChannelUri <uri>`    | **İsteğe** bağlı: Yükleme için kullanmak üzere kanal bildiriminin URI'si. Tarafından belirtilen URI `--channelUri` (belirtilen zaman `--installChannelUri` belirtilmelidir) güncelleştirmeleri algılamak için kullanılır. Bu, yükleme komutu için kullanılabilir; diğer komutlar için yoksayılır.  |
| `--installCatalogUri <uri>`    | **İsteğe** bağlı: Yükleme için kullanmak üzere katalog bildiriminin URI'si. Belirtilirse, kanal yöneticisi yükleme kanalı bildiriminde URI'yi kullanmadan önce katalog bildirimini bu URI'den indirmeye çalışır. Bu parametre, düzen önbelleğinin önceden indirilmiş ürün kataloğuyla oluşturulacak olduğu çevrimdışı yüklemeyi desteklemek için kullanılır. Bu, yükleme komutu için kullanılabilir; diğer komutlar için yoksayılır.    |
| `--productId <id>`             | **İsteğe** bağlı: Yüklenecek örnek için ürünün kimliği. Bu, normal yükleme koşullarında önceden doldurulur. , `productID` "Microsoft.VisualStudio.Product.Enterprise" gibi bir ifadedir. |
| `--wait`                       | **İsteğe** bağlı: İşlem, çıkış kodu döndürmeden önce yükleme tamamlanana kadar bekler. Bu, yüklemeden gelen dönüş kodunu işlemek için yüklemenin bitimini beklemesi gereken yüklemeleri otomatik olarak hazırlarken yararlıdır.      |
| `--locale <language-locale>`   | **İsteğe** bağlı: Yükleyicinin kendisi için kullanıcı arabiriminin görüntüleme dilini değiştirme. Ayar kalıcı olur. Daha fazla bilgi için bu [sayfanın Dil yerel dillerinin](#list-of-language-locales) listesi bölümüne bakın.     |
| `--cache`                      | **İsteğe** bağlı: Varsa, paketler sonraki onarımlar için yüklendikten sonra tutulur. Bu, sonraki yüklemeler, onarımlar veya değişiklikler için kullanılacak genel ilke ayarını geçersiz kılar. Varsayılan ilke paketleri önbelleğe etmektir. Bu, kaldırma komutu için yoksayılır. Daha fazla bilgi [için paket önbelleğini devre dışı bırakma veya taşıma](disable-or-move-the-package-cache.md) makalesini okuyun.   |
| `--nocache`                    | **İsteğe** bağlı: Varsa, paketler yüklendikten veya onarıldıktan sonra silinir. Bunlar yalnızca gerekirse yeniden indirilir ve kullanımdan sonra yeniden silinir. Bu, sonraki yüklemeler, onarımlar veya değişiklikler için kullanılacak genel ilke ayarını geçersiz kılar. Varsayılan ilke paketleri önbelleğe etmektir. Bu, kaldırma komutu için yoksayılır. Daha fazla bilgi [için paket önbelleğini devre dışı bırakma veya taşıma](disable-or-move-the-package-cache.md) makalesini okuyun.    |
| `--noUpdateInstaller`          | **İsteğe** bağlı: Varsa, yükleyicinin sessiz belirtilirken kendisini güncelleştirmesini önler. Bir yükleyici güncelleştirmesi gerektiğinde noUpdateInstaller sessiz belirtilirse yükleyici komutu başarısız olur ve sıfır olmayan bir çıkış kodu geri döner.   |
| `--noWeb`                      | **İsteğe** bağlı: Varsa, Visual Studio düzeni dizininize dosyaları kullanarak yükleme Visual Studio. Kullanıcı düzende olmayan bileşenleri yüklemeye çalışırsa kurulum başarısız olur.  Daha fazla bilgi için, [bkz. Deploying from a network installation](create-a-network-installation-of-visual-studio.md). <br/><br/> **Önemli:** Bu anahtar, kurulumun Visual Studio denetlemeyi durdurmaz. Daha fazla bilgi için [bkz. Ağ tabanlı dağıtımlarda Visual Studio denetleme.](controlling-updates-to-visual-studio-deployments.md) |
| `--path <name>=<path>`         | **İsteğe** bağlı: Yükleme için özel yükleme yolları belirtmek üzere kullanılır. Desteklenen yol adları paylaşılır, önbelleğe alınarak yüklenir.    |
| `--path cache=<path>`          | **İsteğe** bağlı: Yükleme dosyalarını indirmek için belirttiğiniz konumu kullanır. Bu konum, yalnızca ilk kez Visual Studio olarak ayarlanır. Örnek: `--path cache="C:\VS\cache"`   |
| `--path shared=<path>`         | **İsteğe** bağlı: Yan yana yüklemeler için paylaşılan Visual Studio içerir. Bazı araçlar ve SDK'ler bu sürücüde bir konuma yüklenirken bazıları bu ayarı geçersiz karak başka bir sürücüye yükleyebilir. Örnek: `--path shared="C:\VS\shared"` <br/><br/>**Önemli:** Bu ayar yalnızca bir kez ve ilk kez Visual Studio zaman ayarlanır.     |
| `--path install=<path>`        | **İsteğe** bağlı: ile `–-installPath` eşdeğerdir. Özellikle ve `--installPath "C:\VS"` `--path install="C:\VS"` eşdeğerdir. Bu komutlardan yalnızca biri aynı anda kullanılabilir.     |

## <a name="administrator-update-command-and-command-line-parameters"></a>Yönetici güncelleştirme komutu ve komut satırı parametreleri

[Microsoft Update Kataloğu'Microsoft Update](https://catalog.update.microsoft.com) istemci makinenizin yükleme dizinine yönetici güncelleştirmesi indirirseniz, güncelleştirmeyi uygulamak için dosyaya çift tıklarsınız. Varsayılan davranışı değiştirmek için bir komut penceresi açıp aşağıdaki parametrelerin bazılarını da geçebilirsiniz. 

Yönetici güncelleştirmesini Microsoft Endpoint Manager (SCCM) aracılığıyla dağıtıyorsanız, aşağıdaki parametreleri kullanarak paketi davranışını ayarlamak için değiştirebilirsiniz. Parametreleri istemci makinede bir yapılandırma dosyası aracılığıyla da kontrol etmek için kullanılabilirsiniz. Daha fazla bilgi için [bkz. Yönetici güncelleştirmesi yapılandırma yöntemleri](../install/applying-administrator-updates.md#methods-for-configuring-an-administrator-update)

Tüm yönetici güncelleştirme parametrelerinin "güncelleştirme" bağlamında çalıştır olduğunu unutmayın.

| **Yönetici güncelleştirme parametreleri**           | **Açıklama**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|-----------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `--installerUpdateArgs [optional parameters]` | Bu parametre, yönetici güncelleştirme senaryolarıyla ilgili belirli parametrelerin "geçiş dizisi" olarak işlev gösterir. Bu amaçla etkinleştirilmiş isteğe bağlı parametreler: <br/><br/> `--quiet`: Bu, yönetici güncelleştirmeleri için varsayılan deneyimdir ve tamlık için burada listelenir. <br/> `--passive`: Bu parametre, parametresini geçersiz `--quiet` kılar.  Kullanıcı arabiriminin etkileşimli olmayan bir şekilde görünmesine neden olur. <br/>`--norestart`: Bu parametre veya ile birlikte kullanılmalıdır ve gerekli `--quiet` `--passive` tüm yeniden başlatmaların gecikmeye neden olur. <br/>`--noWeb`: Bu parametre, Visual Studio güncelleştirmeleri İnternet'e denetlemesini önler. <br/>`--force`: Bu parametre Visual Studio olsa bile Visual Studio kapanmaya devam etmek zorunda. İş kaybına neden olabilir ve bu parametreyi dikkatli kullanın. Bu parametre kullanıcı bağlamında kullanılmalıdır. <br/>`--installWhileDownloading`: Bu parametre, Visual Studio paralel olarak indirme ve yükleme izinlerini verir. Yönetici güncelleştirmeleri için varsayılan deneyimdir ve tamlık için burada listelenmiştir. <br/>`--downloadThenInstall`: Bu parametre, Visual Studio yüklemeden önce tüm dosyaları indirmeye hazırlar. Bu, parametresinden birbirini `--installWhileDownloading` dışlar. |
| `--checkPendingReboot`                        | Makinede bekleyen bir yeniden başlatma varsa, hangi uygulamanın neden olduğuna bakılmaksızın güncelleştirme durdurulacak. Varsayılan değer bekleyen yeniden başlatmaları denetlemez.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |

Söz dizimi örneği: `visualstudioupdate-16.9.0to16.9.4.exe --installerUpdateArgs=--force,--noWeb --checkPendingReboot`

## <a name="list-of-workload-ids-and-component-ids"></a>İş yükü kimliklerinin ve bileşen kimliklerinin listesi

Ürüne göre sıralanmış iş yükü ve bileşen Visual Studio listesi için Visual Studio iş yükü [ve bileşen kimlikleri sayfasına](workload-and-component-ids.md) bakın.

## <a name="list-of-language-locales"></a>Dil yerellerinin listesi

| **Dil yereli** | **Dil**          |
|---------------------|-----------------------|
| Cs-cz               | Çekçe                 |
| De-de               | Almanca                |
| En-us               | İngilizce               |
| Es-es               | İspanyolca               |
| Fr-fr               | Fransızca                |
| It-it               | İtalyanca               |
| Ja-jp               | Japonca              |
| Ko-kr               | Korece                |
| Pl-pl               | Lehçe                |
| Pt-br               | Portekizce - Brezilya   |
| Ru-ru               | Rusça               |
| Tr-tr               | Türkçe               |
| Zh-cn               | Basitleştirilmiş Çince  |
| Zh-tw               | Geleneksel Çince |

## <a name="error-codes"></a>Hata kodları

İşlem sonucuna bağlı olarak ortam `%ERRORLEVEL%` değişkeni aşağıdaki değerlerden biri olarak ayarlanır:

[!INCLUDE[install-error-codes-md](includes/install-error-codes-md.md)]

Her işlem, dizinde yüklemenin `%TEMP%` ilerlemesini gösteren birkaç günlük dosyası üretir. Klasörü tarihe göre sırala ve sırasıyla önyükleyici, yükleyici uygulaması ve kurulum altyapısı için , ve ile `dd_bootstrapper` `dd_client` başlayan dosyaları `dd_setup` ara.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama yüklemesi için komut Visual Studio örnekleri](command-line-parameter-examples.md)
- [Visual Studio’nun çevrimdışı yüklemesini oluşturma](create-an-offline-installation-of-visual-studio.md)
- [Yanıt dosyası ile Visual Studio yüklemesini otomatikleştirme](automated-installation-with-response-file.md)
- [Visual Studio iş yükü ve bileşen kimlikleri](workload-and-component-ids.md)
