---
title: Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme
titleSuffix: ''
description: Komut satırı parametrelerini kullanarak yüklemenizi denetlemeyi veya özelleştirmeyi Visual Studio öğrenin.
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
ms.openlocfilehash: 73783c0aae038b1c3ebeb3daef0b619ccf37834b
ms.sourcegitcommit: d38d1b083322019663fec7d1d85a4cda456aadca
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2021
ms.locfileid: "135534288"
---
# <a name="use-command-line-parameters-to-install-visual-studio"></a>Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme

Program aracılığıyla Visual Studio komut isteminden yükleme işlemi gerçekleştirdiğinde, çeşitli komut satırı parametrelerini kullanarak aşağıdaki eylemleri gerçekleştirecek şekilde yüklemeyi kontrol edin veya özelleştirin:

- Belirli seçenekler ve davranışlar önceden seçilmiş şekilde istemcide yüklemeyi başlatın.
- Yükleme işlemini otomatikleştirin.
- İstemci makinelerini yüklemek veya güncelleştirmek için ürün dosyalarının ağ düzenini oluşturun veya sürdürün.

Çoğu komut satırı seçeneği, indirme işlemini başlatan küçük (yaklaşık 1 MB) dosya (örneğin, vs_enterprise.exe) olan kurulum önyükleyicisi ile kullanılır.  Aşağıda listelenen tüm komutlar ve parametreler önyükleyicilerle çalışacak şekilde tasarlanmıştır. 

Ağ düzeninizi programlı olarak güncelleştirmek için, Microsoft Update [Kataloğu'nda](https://catalog.update.microsoft.com)indirilen yönetici güncelleştirme paketini de kullanabilirsiniz. Bunu yapma hakkında daha fazla bilgi, Düzen belgelerinizi [güncelleştirme veya değiştirme belgelerinde](create-a-network-installation-of-visual-studio.md#update-the-layout-to-a-specific-version-of-the-product) bulunabilir.  

::: moniker range="vs-2017"

Visual Studio 2017 sürüm 15.9 için önyükleyiciyi almak için aşağıdaki önyükleyici dosyalarından birini indirin:

| **Sürüm**                                  | **Önyükleyici**       |
|----------------------------------------------|---------------------|
| Visual Studio Enterprise 2017 sürüm 15.9   | [vs_enterprise.exe](https://aka.ms/vs/15/release/vs_enterprise.exe)  |
| Visual Studio Professional 2017 sürüm 15.9 | [vs_professional.exe](https://aka.ms/vs/15/release/vs_professional.exe)  |
| Visual Studio Derleme Araçları 2017 sürüm 15.9  | [vs_buildtools.exe](https://aka.ms/vs/15/release/vs_buildtools.exe)   |

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 2019 önyükleyicilerini aşağıdaki tablodan edinebilirsiniz. Alternatif olarak, Visual Studio 2019'un belirli bir sürümünü almak için, seçtiğiniz sürüm ve sürüm için sabit sürüm önyükleyicilerine bağlantılar içeren Visual Studio [2019](/visualstudio/releases/2019/history#installing-an-earlier-release) Sürümleri sayfasına Visual Studio.

| **Sürüm**                     | **Önyükleyici**                                                             |
|---------------------------------|------------------------------------------------------------------------------|
| Visual Studio 2019 Enterprise sürüm 16.11   | [vs_enterprise.exe](https://aka.ms/vs/16/release/vs_enterprise.exe)     |
| Visual Studio 2019 Professional sürüm 16.11| [vs_professional.exe](https://aka.ms/vs/16/release/vs_professional.exe) |
| Visual Studio 2019 Derleme Araçları sürüm 16.11 | [vs_buildtools.exe](https://aka.ms/vs/16/release/vs_buildtools.exe)     |

::: moniker-end

::: moniker range=">=vs-2022"

Her zaman Geçerli kanalın en son sürümünü yükecek Visual Studio 2022 için en son önyükleyicileri almak için aşağıdaki dosyalardan birini indirin. Alternatif olarak, belirli bir sürümü veya Visual Studio 2022'nin belirli bir kanalını yüklemek için, her bakım sürümü için sabit sürüm önyükleyicilerine bağlantılar içeren [Visual Studio 2022](/visualstudio/releases/2022/release-history#release-dates-and-build-numbers) Yayın Geçmişi sayfasına gidin. 

| **Sürüm**                      | **Önyükleyici**                                                                                   |
|----------------------------|-------------------------------------------------------------------------------------------|
| Visual Studio 2022 Enterprise   | [vs_enterprise.exe](https://aka.ms/vs/17/release/vs_enterprise.exe)     |
| Visual Studio 2022 Professional | [vs_professional.exe](https://aka.ms/vs/17/release/vs_professional.exe) |
| Visual Studio 2022 Community    | [vs_community.exe](https://aka.ms/vs/17/release/vs_community.exe)       |
| Visual Studio 2022 Derleme Araçları   | [vs_buildtools.exe](https://aka.ms/vs/17/release/vs_buildtools.exe)         |

::: moniker-end

::: moniker range="vs-2017"

>[!TIP]
>Daha önce bir önyükleyici dosyası indirdiy ve hangi sürümün olduğunu doğrulamak için aşağıdaki gibi bir dosya yükleyebilirsiniz. Bu Windows' Dosya Gezgini açın, önyükleyici dosyasına sağ tıklayın, Özellikler'i **seçin,** **Ayrıntılar sekmesini seçin** ve ardından Ürün sürüm **numarasını** görüntüleyin. Bu slanın bir yayın sürümüyle Visual Studio için Visual Studio [numaraları ve yayın tarihleri sayfasına](visual-studio-build-numbers-and-release-dates.md) bakın.

::: moniker-end

::: moniker range="vs-2019"

>[!TIP]
>Daha önce bir önyükleyici dosyası indirdiy ve sürümünü doğrulamak için aşağıdaki şekilde devam edin. Bu Windows' Dosya Gezgini açın, önyükleyici dosyasına sağ tıklayın, Özellikler'i **seçin,** **Ayrıntılar sekmesini seçin** ve ardından Ürün sürüm **numarasını** görüntüleyin. Bu sayıyla bir Visual Studio eşleşmesi için Visual Studio [2019 Sürümler sayfasının Visual Studio bakın.](/visualstudio/releases/2019/history)

::: moniker-end

::: moniker range=">=vs-2022"

>[!TIP]
>Daha önce bir önyükleyici dosyası indirdiy ve hangi sürümün yüklen kuracaklarını doğrulamak için aşağıdaki şekilde devam edin. Bu Windows' Dosya Gezgini açın, önyükleyici dosyasına sağ tıklayın, Özellikler'i **seçin** ve ardından Ayrıntılar **sekmesini** seçin. Ürün **sürümü** alanı, [önyükleyicinin](/visualstudio/releases/2022/vs2022-release-rhythm) yükleyecek kanalı ve sürümü açıklar. Sürüm numarası her zaman "belirtilenin en son bakım sürümü" olarak okunması ve kanal açıkça belirtilmemişse Geçerli olması gerekir. Bu nedenle, LTSC 17.0 Ürün sürümüne sahip bir önyükleyici, 17.0 LTSC kanalında kullanılabilen en son 17.0.x bakım sürümünü yükleyecek. Yalnızca Visual Studio 2022 sürümünün Geçerli kanala Visual Studio 2022'nin en son sürümünü yükley olduğunu söyleyen bir Ürün sürümüne sahip bir önyükleyici.

::: moniker-end

## <a name="bootstrapper-commands-and-command-line-parameters"></a>Önyükleyici komutları ve komut satırı parametreleri

Ürünü yüklemek Visual Studio düzeni korumak için Visual Studio önyükleyicisini program aracılığıyla sorgularken, ilk parametre gerçekleştirecek işlemi açıklayan komut (fiil) parametresidir. Hepsi iki tire (--) ön ekine sahip sonraki isteğe bağlı komut satırı parametreleri, bu işlemi nasıl olacağını daha ayrıntılı olarak tanımlar. Tüm Visual Studio komut satırı parametreleri büyük/büyük/büyük harfe duyarlı değildir ve ek örnekler Komut satırı parametre [örnekleri sayfasında](command-line-parameter-examples.md) bulunabilir.

Söz dizimi örneği: `vs_enterprise.exe [command] <optional parameters>...`

| **Komut** | **Açıklama**                                                                                                         |
|-------------|-------------------------------------------------------------------------------------------------------------------------|
| (boş)     | Varsayılan komutun her ikisi de ürünü yüklüdür ve tüm düzen bakım işlemleri için kullanılır.                    |
| `modify`    | Yüklü bir ürünü değiştiren.                                                                                          |
| `update`    | Yüklü bir ürünü güncelleştirme.                                                                                           |
| `repair`    | Yüklü bir ürünü onarıyor.                                                                                           |
| `uninstall` | Yüklü bir ürünü kaldırır.                                                                                        |
| `export`    | Yükleme seçimini bir yükleme yapılandırma dosyasına dışarı aktarır. **Not:** Yalnızca vs_installer.exe. |

> [!IMPORTANT]
> Birden çok ayrı iş yükü, bileşen veya dil belirtirken, her öğe için `--add` veya komut satırı anahtarını `--remove` tekrarlamalısiniz.

| **Parametreler**                                     | **Açıklama**                                                            |
|----------------------------------------------------|----------------------------------------------------------------------|
| `--installPath <dir>`                              | Varsayılan yükleme komutu için bu parametre İsteğe **bağlıdır** ve örneğin istemci makinesine nereye yük olacağını açıklar. Güncelleştirme veya değiştirme gibi diğer komutlar için bu parametre **Gerekli'dir** ve örneğin üzerinde hareket etmek için yükleme dizinini belirtir.                                                   |
| `--add <one or more workload or component IDs>`    | **İsteğe** bağlı: Bir yükleme veya değiştirme komutu sırasında, bu yinelenebilir parametre eklenecek bir veya daha fazla iş yükünü veya bileşen kimliklerini belirtir. Yapıt için gerekli bileşenler yüklenir, ancak önerilen veya isteğe bağlı bileşenler yüklenmez. ve/veya parametreleri kullanarak ek bileşenleri `--includeRecommended` genel olarak `--includeOptional` kontrol edin. Birden çok iş yükü veya bileşen eklemek için komutunu `--add` tekrarlayın (örneğin, `--add Workload1 --add Workload2` ). Daha ince bir denetim için, kimliği (örneğin, veya ) ekli veya `;includeRecommended` buna `;includeOptional` `--add Workload1;includeRecommended` eklemeler yapmak için. `--add Workload2;includeRecommended;includeOptional` Daha fazla bilgi için İş yükü [ve bileşen kimlikleri sayfasına](workload-and-component-ids.md) bakın. |
| `--remove <one or more workload or component IDs>` | **İsteğe** bağlı: Bir değiştirme komutu sırasında, bu yinelenebilir parametre kaldırılabilir bir veya daha fazla iş yükünü veya bileşen kimliklerini belirtir. Parametresine benzer şekilde tamamlar ve `--add` davranır.   |
| `--addProductLang <language-locale>`               | **İsteğe** bağlı: Bir yükleme veya değiştirme komutu sırasında, bu yinelenebilir parametre ürünle birlikte yüklenmeleri gereken kullanıcı arabirimi dil paketlerini belirtir. Yoksa, yükleme makine yerel diline karşılık gelen dil paketini kullanır. Daha fazla bilgi için bu [sayfanın Dil yerel dillerinin](#list-of-language-locales) listesi bölümüne bakın.  |
| `--removeProductLang <language-locale>`            | **İsteğe** bağlı: Bir yükleme veya değiştirme komutu sırasında, bu yinelenebilir parametre üründen kaldırılması gereken kullanıcı arabirimi dil paketlerini belirler.  Parametresine benzer şekilde tamamlar ve `--addProductLang` davranır. |
| `--in <path>`                                      | **İsteğe** bağlı: Yapılandırma ayarlarını içere [bir yanıt dosyasının](automated-installation-with-response-file.md)URI'sini veya yolunu içerir.  |
| `--all`                                            | **İsteğe** bağlı: Bir yükleme veya değiştirme komutu sırasında bu parametre ürünün tüm iş yüklerinin ve bileşenlerinin yüklü olmasına neden olur.  |
| `--allWorkloads`                                   | **İsteğe** bağlı: Yükleme veya değiştirme komutu sırasında, bu parametre tüm iş yüklerini ve bileşenleri yüklemektedir, ancak önerilen veya isteğe bağlı bileşenler yoktur.  |
| `--includeRecommended`                             | **İsteğe** bağlı: Bir yükleme veya değiştirme komutu sırasında, bu parametre yüklü olan tüm iş yükleri için önerilen bileşenleri içerir, ancak isteğe bağlı bileşenleri içerir. İş yükleri veya ile `--allWorkloads` `--add` belirtilir.  |
| `--includeOptional`                                | **İsteğe** bağlı: Bir yükleme veya değiştirme komutu sırasında, bu parametre yüklü olan tüm iş yükleri için isteğe bağlı bileşenleri içerir, ancak önerilen bileşenleri içerir. İş yükleri veya ile `--allWorkloads` `--add` belirtilir. |
| `--quiet, -q`                                      | **İsteğe** bağlı: Herhangi bir komutla kullanıldığında, bu parametre komut yürütülürken tüm kullanıcı arabirimlerinin görüntülenebilir.    |
| `--passive, -p`                                    | **İsteğe** bağlı: Bu parametre, kullanıcı arabiriminin etkileşimli olmayan bir şekilde görüntülenebilir. Bu parametre, parametresinden karşılıklı olarak dışlar (ve aslında geçersiz `--quiet` kılar).   |
| `--norestart`                                      | **İsteğe** bağlı: Bu parametrenin veya `--passive` parametreleriyle `--quiet` eşleştirilmiş olması gerekir.  Yükleme, güncelleştirme veya değiştirme komutu sırasında, parametresinin `--norestart` ekli olması tüm gerekli yeniden başlatmaları geciktirecek.    |
| `--force`                                          | **İsteğe** bağlı: Bu parametre Visual Studio işlem kullansa bile Visual Studio kapanmaya zorunlu tutulacak.   |
| `--installWhileDownloading`                        | **İsteğe** bağlı: Yükleme, güncelleştirme veya değiştirme komutu sırasında bu parametre, Visual Studio indirip paralel olarak yüklemenizi sağlar. Bu varsayılan deneyimdir.   |
| `--downloadThenInstall`                            | **İsteğe** bağlı: Yükleme, güncelleştirme veya değiştirme komutu sırasında, bu parametre Visual Studio yüklemeden önce tüm dosyaları indirmeye zorunlu kullanır. Bu, parametresinden birbirini `--installWhileDownloading` dışlar.   |
| `--channelURI`                                     | **İsteğe** bağlı: Güncelleştirme komutu sırasında, güncelleştirme ayarları konumunu değiştirmek için yeni bir channelURI'yi geçebilirsiniz.  Yapılandırmanıza hangi örneğinin çok açık olduğunu açıkça ifade etmek için --installPath parametresiyle Visual Studio önerilir. |
| `--nickname <name>`                                | **İsteğe** bağlı: Yükleme komutu sırasında, bu parametre yüklü bir ürüne atanma takma adını tanımlar. Takma ad 10 karakterden uzun olamaz. |
| `--productKey`                                     | **İsteğe** bağlı: Yükleme komutu sırasında, bu parametre yüklü bir ürün için kullanmak üzere ürün anahtarını tanımlar. biçiminde 25 alfasayısal karakterden `xxxxxxxxxxxxxxxxxxxxxxxxx` oluşur.  |
| `--help, --?, -h, -?`                              | Bu sayfanın çevrimdışı bir sürümünü görüntüler.     |
| `--config <path>`                                  | **İsteğe** bağlı: Yükleme veya değiştirme işlemi sırasında bu, daha önce kaydedilmiş bir yükleme yapılandırma dosyasını temel alarak eklenecek iş yüklerini ve bileşenleri belirler. Bu işlem eklenebilirdir ve dosyada mevcut olmayan iş yükünü veya bileşeni kaldırmaz. Ayrıca ürün için geçerli olan öğeler eklenmez. Bir dışarı aktarma işlemi sırasında, bu yükleme yapılandırma dosyasını kaydedecek konumu belirler.                                                                                                                                                                                                                                                                                                                                                  |

## <a name="layout-command-and-command-line-parameters"></a>Düzen komutu ve komut satırı parametreleri

Tüm düzen yönetimi işlemleri, bir düzen oluşturuyor veya güncelleştiriyorsanız, komutun varsayılan Yükle (boş) olduğunu varsayer. Bu nedenle tüm düzen yönetimi işlemlerinin ilk gerekli parametreyle başlaması `--layout` gerekir. Aşağıdaki tabloda, komut satırı kullanarak düzen oluşturmak veya güncelleştirmek [için kullanabileceğiniz diğer](create-a-network-installation-of-visual-studio.md) parametreler açıklanmıştır. 

| **Düzen parametreleri**                           | **Açıklama**                                        |
|-------------------------------------------------|----------------------------------------------------------------------|
| `--layout <dir>`                                | Çevrimdışı yükleme önbelleği oluşturmak veya güncelleştirmek için bir dizin belirtir. Daha fazla bilgi için, [bkz. Create a network-based installation of Visual Studio.](create-a-network-installation-of-visual-studio.md)                       |
| `--lang <one or more language-locales>`         | **İsteğe** bağlı: `--layout` Belirtilen dillere sahip kaynak paketleriyle çevrimdışı yükleme önbelleği hazırlamak için ile kullanılır. Daha fazla bilgi için bu [sayfanın Dil yerel dillerinin](#list-of-language-locales) listesi bölümüne bakın.       |
| `--add <one or more workload or component IDs>` | **İsteğe** bağlı: Eklemek için bir veya daha fazla iş yükü veya bileşen kimlikleri. Yapıt için gerekli bileşenler yüklenir, ancak önerilen veya isteğe bağlı bileşenler yüklenmez. ve/veya kullanarak ek bileşenleri küresel `--includeRecommended` olarak kontrol `--includeOptional` edin. Daha ince bir denetim için, kimliği (örneğin, veya ) ekli veya `;includeRecommended` buna `;includeOptional` `--add Workload1;includeRecommended` eklemeler yapmak için. `--add Workload2;includeOptional` Daha fazla bilgi için İş yükü [ve bileşen kimlikleri sayfasına](workload-and-component-ids.md) bakın. <br/>**Not:** `--add` Kullanılırsa, yalnızca belirtilen iş yükleri ve bileşenler ve bağımlılıkları indirilir. `--add`Belirtilmezse, tüm iş yükleri ve bileşenler düzene indirilir. |
| `--includeRecommended`                          | **İsteğe** bağlı: Yüklü olan tüm iş yükleri için önerilen bileşenleri içerir, ancak isteğe bağlı bileşenleri dahil değildir. İş yükleri veya ile `--allWorkloads` `--add` belirtilir.         |
| `--includeOptional`                             | **İsteğe** bağlı: Düzende *yer alan* tüm iş yükleri için önerilen ve isteğe bağlı bileşenleri içerir. İş yükleri ile `--add` belirtilir.                        |
| `--keepLayoutVersion`                           | **İsteğe** bağlı: Düzende yer alan ürün sürümünü güncelleştirmeden düzende yapılan değişiklikleri uygulama.   |
| `--useLatestInstaller`         | **İsteğe** bağlı: Varsa, Visual Studio Yükleyicisi yeni bir sürüme ait olsa bile, en son sürümü düzeninize dahil edilir. En son yükleyicide bulunan yeni özelliklerden veya hata düzeltmelerinden yararlanmak için bu yararlı olabilir. Daha fazla bilgi için Düzeni her [zaman en son yükleyiciyi kullanmak üzere yapılandırma belgelerine](create-a-network-installation-of-visual-studio.md#configure-the-layout-to-always-include-and-provide-the-latest-installer) bakın. |
| `--verify`                                      | **İsteğe** bağlı: Bir düzenin içeriğini doğrulayın. Bozuk veya eksik dosyalar listelenir.            |
| `--fix`                                         | **İsteğe** bağlı: Bir düzenin içeriğini doğrulayın.  Bozuk veya eksik olan dosyalar yeniden yüklenir. Bir düzeni düzeltmek için İnternet erişimi gereklidir.           |
| `--clean <one or more paths to catalogs>`       | **İsteğe** bağlı: Bileşenlerin eski sürümlerini, daha yeni bir sürüme güncelleştirilmiş bir düzenden kaldırır.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |

| **Gelişmiş düzen parametreleri** | **Açıklama**                                  |
|--------------------------------|--------------------------------------------------|
| `--channelId <id>`             | **İsteğe** bağlı: Yüklanacak örneğin kanalının kimliği. Bu, yükleme komutu için gereklidir ve belirtilirse diğer komutlar için `--installPath` yoksayılır.        |
| `--channelUri <uri>`           | **İsteğe** bağlı: Kanal bildiriminin URI'si. Bu değer [güncelleştirmelerin kaynak konumunu yönetir](update-visual-studio.md#configure-source-location-of-updates-1) ve ilk değer [düzenin response.json](create-a-network-installation-of-visual-studio.md#configure-initial-client-installation-defaults-for-this-layout)dosyasında yapılandırılır.  Güncelleştirmeler gerektirilmemişse, mevcut olmayan bir dosyaya işaret ediyor `--channelUri` olabilir (örneğin, --channelUri C:\doesntExist.chman). Bu, yükleme komutu için kullanılabilir; diğer komutlar için yoksayılır.  |
| `--installChannelUri <uri>`    | **İsteğe** bağlı: Yükleme için kullanmak üzere kanal bildiriminin URI'si. Tarafından belirtilen URI `--channelUri` (belirtilen zaman `--installChannelUri` belirtilmelidir) güncelleştirmeleri algılamak için kullanılır. Bu, yükleme komutu için kullanılabilir; diğer komutlar için yoksayılır.  |
| `--installCatalogUri <uri>`    | **İsteğe** bağlı: Yükleme için kullanmak üzere katalog bildiriminin URI'si. Belirtilirse, kanal yöneticisi yükleme kanalı bildiriminde URI'yi kullanmadan önce katalog bildirimini bu URI'den indirmeye çalışır. Bu parametre, düzen önbelleğinin önceden indirilmiş ürün kataloğuyla oluşturulacak olduğu çevrimdışı yüklemeyi desteklemek için kullanılır. Bu, yükleme komutu için kullanılabilir; diğer komutlar için yoksayılır.    |
| `--productId <id>`             | **İsteğe** bağlı: Yüklenecek örnek için ürünün kimliği. Bu, normal yükleme koşullarında önceden doldurulur. , `productID` "Microsoft.VisualStudio.Product.Enterprise" gibi bir ifadedir. |
| `--wait`                       | **İsteğe** bağlı: İşlem, çıkış kodu döndürmeden önce yükleme tamamlanana kadar bekler. Bu, yüklemeden gelen dönüş kodunu işlemek için yüklemenin bitimini beklemesi gereken yüklemeleri otomatik olarak hazırlarken yararlıdır.      |
| `--locale <language-locale>`   | **İsteğe** bağlı: Yükleyicinin kendisi için kullanıcı arabiriminin görüntüleme dilini değiştirme. Ayar kalıcı olur. Daha fazla bilgi için bu [sayfanın Dil yerel dillerinin](#list-of-language-locales) listesi bölümüne bakın.     |
| `--cache`                      | **İsteğe** bağlı: Varsa, paketler sonraki onarımlar için yüklendikten sonra tutulur. Bu, sonraki yüklemeler, onarımlar veya değişiklikler için kullanılacak genel ilke ayarını geçersiz kılar. Varsayılan ilke paketleri önbelleğe etmektir. Bu, kaldırma komutu için yoksayılır. Daha fazla bilgi [için paket önbelleğini devre dışı bırakma veya taşıma](disable-or-move-the-package-cache.md) makalesini okuyun.   |
| `--nocache`                    | **İsteğe** bağlı: Varsa, paketler yüklendikten veya onarıldıktan sonra silinir. Bunlar yalnızca gerekirse yeniden indirilir ve kullanımdan sonra yeniden silinir. Bu, sonraki yüklemeler, onarımlar veya değişiklikler için kullanılacak genel ilke ayarını geçersiz kılar. Varsayılan ilke paketleri önbelleğe etmektir. Bu, kaldırma komutu için yoksayılır. Daha fazla bilgi [için paket önbelleğini devre dışı bırakma veya taşıma](disable-or-move-the-package-cache.md) makalesini okuyun.    |
| `--noUpdateInstaller`          | **İsteğe** bağlı: Varsa, yükleyicinin sessiz belirtilirken kendisini güncelleştirmesini önler. Bir yükleyici güncelleştirmesi gerektiğinde noUpdateInstaller sessiz belirtilirse yükleyici komutu başarısız olur ve sıfır olmayan bir çıkış kodu geri döner.   |
| `--noWeb`                      | **İsteğe** bağlı: Varsa, Visual Studio kurulum düzen dizininize dosyaları kullanarak Visual Studio. Kullanıcı düzende olmayan bileşenleri yüklemeye çalışırsa kurulum başarısız olur.  Daha fazla bilgi için, [bkz. Deploying from a network installation](create-a-network-installation-of-visual-studio.md). <br/><br/> **Önemli:** Bu anahtar, kurulumun Visual Studio denetlemeyi durdurmaz. Daha fazla bilgi için [bkz. Ağ tabanlı dağıtımlarda Visual Studio denetleme.](controlling-updates-to-visual-studio-deployments.md) |
| `--path <name>=<path>`         | **İsteğe** bağlı: Yükleme için özel yükleme yolları belirtmek üzere kullanılır. Desteklenen yol adları paylaşılır, önbelleğe alınarak yüklenir.    |
| `--path cache=<path>`          | **İsteğe** bağlı: Yükleme dosyalarını indirmek için belirttiğiniz konumu kullanır. Bu konum, yalnızca ilk kez Visual Studio zaman ayarlanır. Örnek: `--path cache="C:\VS\cache"`   |
| `--path shared=<path>`         | **İsteğe** bağlı: Yan yana yüklemeler için paylaşılan Visual Studio içerir. Bazı araçlar ve SDK'ler bu sürücüde bir konuma yüklenirken bazıları bu ayarı geçersiz karak başka bir sürücüye yükleyebilir. Örnek: `--path shared="C:\VS\shared"` <br/><br/>**Önemli:** Bu yalnızca bir kez ve bu yükleme Visual Studio zaman ayarlanır.     |
| `--path install=<path>`        | **İsteğe** bağlı: ile `–-installPath` eşdeğerdir. Özellikle ve `--installPath "C:\VS"` `--path install="C:\VS"` eşdeğerdir. Bu komutlardan yalnızca biri aynı anda kullanılabilir.     |

## <a name="administrator-update-command-and-command-line-parameters"></a>Yönetici güncelleştirme komutu ve komut satırı parametreleri

[Microsoft Update Kataloğu'Microsoft Update](https://catalog.update.microsoft.com) istemci makinenizin yükleme dizinine yönetici güncelleştirmesi indirirseniz, güncelleştirmeyi uygulamak için dosyaya çift tıklarsınız. Varsayılan davranışı değiştirmek için bir komut penceresi açıp aşağıdaki parametrelerin bazılarını da geçebilirsiniz. 

Yönetici güncelleştirmesini Microsoft Endpoint Manager (SCCM) aracılığıyla dağıtıyorsanız, aşağıdaki parametreleri kullanarak paketi davranışını ayarlamak için değiştirebilirsiniz. Parametreleri istemci makinede bir yapılandırma dosyası aracılığıyla da kontrol etmek için kullanılabilirsiniz. Daha fazla bilgi için [bkz. Yönetici güncelleştirmesi yapılandırma yöntemleri](../install/applying-administrator-updates.md#methods-for-configuring-an-administrator-update)

Tüm yönetici güncelleştirme parametrelerinin "güncelleştirme" bağlamında çalıştır olduğunu unutmayın.

| **Yönetici güncelleştirme parametreleri**           | **Açıklama**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|-----------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `--installerUpdateArgs [optional parameters]` | Bu parametre, yönetici güncelleştirme senaryolarıyla ilgili belirli parametrelerin "geçiş dizisi" olarak işlev gösterir. Bu amaçla etkinleştirilmiş isteğe bağlı parametreler: <br/><br/> `--quiet`: Bu, yönetici güncelleştirmeleri için varsayılan deneyimdir ve tamlık için burada listelenir. <br/> `--passive`: Bu parametre, parametresini geçersiz `--quiet` kılar.  Kullanıcı arabiriminin etkileşimli olmayan bir şekilde görünmesine neden olur. <br/>`--norestart`: Bu parametre veya ile birlikte kullanılmalıdır ve gerekli `--quiet` `--passive` tüm yeniden başlatmaların gecikmeye neden olur. <br/>`--noWeb`: Bu parametre, Visual Studio güncelleştirmeleri için İnternet'i denetlemesini önler. <br/>`--force`: Bu parametre Visual Studio olsa bile Visual Studio kapanmaya devam etmek zorunda. İş kaybına neden olabilir ve bu parametreyi dikkatli kullanın. Bu parametre kullanıcı bağlamında kullanılmalıdır. <br/>`--installWhileDownloading`: Bu parametre, Visual Studio paralel olarak indirme ve yükleme izin verir. Yönetici güncelleştirmeleri için varsayılan deneyimdir ve tamlık için burada listelenmiştir. <br/>`--downloadThenInstall`: Bu parametre, Visual Studio yüklemeden önce tüm dosyaları indirmeye hazırlar. Bu, parametresinden birbirini `--installWhileDownloading` dışlar. |
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

- [Yükleme için komut satırı Visual Studio örnekleri](command-line-parameter-examples.md)
- [Visual Studio’nun çevrimdışı yüklemesini oluşturma](create-an-offline-installation-of-visual-studio.md)
- [Yanıt dosyası ile Visual Studio yüklemesini otomatikleştirme](automated-installation-with-response-file.md)
- [Visual Studio iş yükü ve bileşen kimlikleri](workload-and-component-ids.md)
