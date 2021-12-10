---
title: Ağ tabanlı yükleme oluşturma
description: Bir kuruluş içinde uygulama dağıtmak için ağ yükleme noktası Visual Studio öğrenin.
ms.date: 12/7/2021
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 4CABFD20-962E-482C-8A76-E4012052F701
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 493d39ce7da5009681d33f8d00315d21f22d78e0
ms.sourcegitcommit: 99e0146dfe742f6d1955b9415a89c3d1b8afe4e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2021
ms.locfileid: "134553862"
---
# <a name="create-maintain-and-deploy-a-network-installation-of-visual-studio"></a>Ağ yüklemesi oluşturma, bakımını ve dağıtma Visual Studio

Bazen kuruluş yöneticisi, istemci iş istasyonlarına dağıtılabilir Visual Studio içeren bir ağ yükleme noktası oluşturmak ister. Bu, istemci makinelerinin sınırlı izinlere veya sınırlı İnternet erişimine sahip olduğu ya da bir kuruluşun geliştirici araç kümesine yönelik belirli bir sürümü standart hale getirttir istediği senaryoları kolaylaştırmaktır. Bir yöneticinin Visual Studio bir ağ paylaşımında  depolanmış bir ağ düzeni (dosya önbelleği) oluşturması ve korumasını sağlamak için bu verileri tasarladık. Ağ düzeni, hem ilk yükleme Visual Studio sonraki ürün güncelleştirmeleri için gereken tüm uygulama dosyalarını içerir.

Bu web sayfasında çok fazla bilgi vardır ve aşağıdaki bölümlerde gruplanmıştır:
- [**Başlamadan önce:**](#before-you-get-started)plan yapmayı planlayınca göz önünde bulundurulması gereken ipuçlarını ve diğer önemli konuları vurgular.
- [**Doğru önyükleyiciyi alın:**](#download-the-visual-studio-bootstrapper-to-create-the-network-layout)kullanabileceğiniz çeşitli önyükleyicileri nerede bulup ayırt etmek için rehberlik.
- [**Ağ düzenini oluşturma:**](#create-the-network-layout)Doğru ürün içeriği, kanal ayarları ve yükleyicinin sürümüyle düzenin nasıl oluşturularak bir ağ paylaşımına nasıl kopyalanacakları açıklanacak. 
- [**Ağ düzenini güncelleştirin,**](#update-or-modify-your-layout)değiştirin ve bakımını yapın: düzeninizin en iyi şekilde korunmasına ilişkin bilgiler; düzenin ürün sürümünü, ürün içeriğini, kanal ayarlarını, yükleyici sürümünü ve klasör boyutunu güncelleştirme. 
- [**Düzeni istemci makinelere yükleme:**](#install-visual-studio-onto-a-client-machine-from-a-network-installation)Varsayılan olarak hangi iş yüklerinin ve bileşenlerin yükll olduğu ve istemcinin güncelleştirmeleri nerede araması gerektiği gibi istemci varsayılan ayarlarının nasıl yapılandırıldığından emin olun. Ayrıca, istemci makinelere _ilk Visual Studio_ yüklemesini de içerir. Başlangıçta bir _düzenden yüklenmiş_ istemci makinelerini güncelleştirmeyle ilgili rehberlik ve bilgiler, ayrı bir güncelleştirmenin ağ tabanlı yüklemesi [Visual Studio](/visualstudio/install/update-a-network-installation-of-visual-studio) ele alındı.
- [**Yardım ve Destek:**](#get-support-for-your-network-layout)Yardım istemek için nereye

## <a name="before-you-get-started"></a>Başlamadan önce
Başlamadan önce plan yapmak ve farkında olmak için birkaç önemli şey vardır.  
::: moniker range="vs-2017"

- **Klasör Yönetimi:** Kurum içinde birden fazla Visual Studio sürümünüz varsa (örneğin, Visual Studio 2017 Professional ve Visual Studio 2017 Enterprise), her sürüm için ayrı bir ağ yükleme noktası oluşturmanız gerekir. Ayrıca, istemcinin Visual Studio ve kaldırma işlevlerinin düzgün şekilde çalışması için özgün uygulama yükleme düzeni ve sonraki tüm ürün güncelleştirmelerinin aynı ağ dizininde yer alıyor olması gerekir. Son olarak, bazı kuruluşlar 80 karakterlik sınırlamaya çözüm olarak [](/windows/win32/fileio/symbolic-links) sembolik bağlantıları başarıyla kullansa da düzen yolu 80 karakterden az olmalıdır. 
- **Güncelleştirmeleri Planlama:** İlk istemci yüklemesini öncesinde istemci makinelerinizin ürün güncelleştirmelerini _nasıl alalı_ olduğuna karar ver. Bu, istemcinizin güncelleştirme konumu yapılandırmasının doğru şekilde ayar olduğundan emin olmak için gereklidir. Seçenekleriniz, istemcilerin güncelleştirmeleri ağ düzeni konumdan veya Microsoft tarafından barındırılan internetteki sunuculardan aldırmalarını içerir. İstemci düzenden yüklendikten sonra, istemcinin güncelleştirme konumu yapılandırması kilitlenir ve değiştirilemez. 

::: moniker-end

::: moniker range="vs-2019"

- **Klasör Yönetimi:** Kurum içinde birden fazla Visual Studio sürümünüz varsa (örneğin, Visual Studio 2019 Professional ve Visual Studio 2019 Enterprise), her sürüm için ayrı bir ağ yükleme noktası oluşturmanız gerekir. Ayrıca, bazı kuruluşlar 80 karakterlik sınırlamaya çözüm olarak [](/windows/win32/fileio/symbolic-links) sembolik bağlantıları başarıyla kullansa da, düzen yolu 80 karakterden az olmalıdır. 
- **Güncelleştirmeleri Planlama:** İlk istemci yüklemesini yapmadan önce istemci makinelerinizin ürün güncelleştirmelerini _nasıl alalı_ olduğuna karar ver. Bu, istemcinizin güncelleştirme konumu yapılandırmasının doğru şekilde ayar olduğundan emin olmak için gereklidir. Seçenekleriniz, istemcilerin güncelleştirmeleri ağ düzeni konumdan veya Microsoft tarafından barındırılan internetteki sunuculardan aldırmalarını içerir. 

 > [!IMPORTANT]
 > Yalnızca Visual Studio 2019 işlevselliğini kullanırken düzen yönetimiyle ilgili aşağıdaki sınırlama vardır: İstemci düzenden yüklendikten sonra istemcinin güncelleştirme konumu kilitlenir ve değiştirilemez. Bu durum, istemcilerinizin onarım ve kaldırma işlevlerini korurken düzeninden güncelleştirmeleri almalarını amaçladıysanız, sonraki  tüm ürün güncelleştirmelerini istemcilerinin yükıldığı özgün düzen klasörüne koymanız gerektiğini ifade eder. Başka bir deyişle, temel Visual Studio 2019 özelliği, bir  istemcinin bir düzen konumdan özgün yükleme yapma yeteneğini desteklemez ve ardından bu istemcinin farklı bir düzen konumdan ürün güncelleştirmesi almalarını sağlar. 
 > 
 > Ürün güncelleştirme konumunun sabit olduğu ve ürün güncelleştirmelerinin özgün yükleme düzeniyle aynı  düzen klasöründe olması gereken bu sınırlama, 2022'de Visual Studio. 2022 Visual Studio de güncelleştirmeler için istemcinin kaynak konumunu eaily olarak değiştirebilirsiniz. Visual Studio 2019 düzenlerinizi yönetmek ve ürünün 2019 sürümündeki sınırlamayı ortadan kaldırmak için Visual Studio ürün ailesinin tüm _modern_ sürümlerini yöneten en son (Visual Studio 2022) yükleyicisini dahil etmek ve kullanmak mümkün hale geldi. Aşağıdaki Düzeni her [zaman içerecek şekilde yapılandırma ve en son yükleyiciyi sağlama bölümünde](#configure-the-layout-to-always-include-and-provide-the-latest-installer) bunun nasıl etkinleştirildikleri açıklanmıştır.
 
::: moniker-end

::: moniker range="vs-2022"

- **Klasör Yönetimi:** Kurum içinde birden fazla Visual Studio sürümünüz varsa (örneğin, Visual Studio 2022 Professional ve Visual Studio 2022 Enterprise), her sürüm için ayrı bir ağ yükleme noktası oluşturmanız gerekir. Ayrıca, bazı kuruluşlar 80 karakterlik sınırlamaya çözüm olarak [](/windows/win32/fileio/symbolic-links) sembolik bağlantıları başarıyla kullansa da, düzen yolu 80 karakterden az olmalıdır.
- **Güncelleştirmeleri Planlama:** İlk istemci yüklemesini yapmadan önce istemci makinelerinizin ürün güncelleştirmelerini nasıl _alası_ gerektiğine karar vermenizi öneririz. Bu, istemcinizin güncelleştirme konumu yapılandırmasının doğru şekilde başlatılmasını sağlamaktır. Seçenekleriniz, istemcilerin güncelleştirmeleri ağ düzeni konumdan veya Microsoft tarafından barındırılan internetteki sunuculardan aldırmalarını içerir. Neyse ki, ilk yükleme gerçekleştikten sonra güncelleştirmeler için istemci _kaynak konumunu_ yapılandırmak da mümkündür. 

::: moniker-end

## <a name="download-the-visual-studio-bootstrapper-to-create-the-network-layout"></a>Ağ Visual Studio oluşturmak için önyükleyiciyi indirin

Visual Studio sürümünün önyükleyiciyi indirin ve düzenin kaynak konumu olarak hizmet vermek istediğiniz dizine kopyalayın. Önyükleyici, diğer düzen işlemlerini oluşturmak, güncelleştirmek ve gerçekleştirmek için kullanabileceğiniz yürütülebilir dosyadır.

::: moniker range="vs-2017"

Aşağıda listelenen önyükleyiciler, ne zaman çalıştırsanız çalıştırın Visual Studio 2017'nin en son güvenli sürümünü her zaman yükleyebilir:

| Sürüm                                      | Önyükleyici            |
|----------------------------------------------|---------------------|
| Visual Studio 2017 Enterprise sürüm 15.9   | [vs_enterprise.exe](https://aka.ms/vs/15/release/vs_enterprise.exe) |
| Visual Studio 2017 Professional sürüm 15.9 | [vs_professional.exe](https://aka.ms/vs/15/release/vs_professional.exe) |
| Visual Studio 2017 Derleme Araçları sürüm 15.9  | [vs_buildtools.exe](https://aka.ms/vs/15/release/vs_buildtools.exe)   |

Desteklenen diğer önyükleyiciler vs_feedbackclient.exe, vs_teamexplorer.exe, vs_testagent.exe, vs_testcontroller.exe ve vs_testprofessional.exe.

::: moniker-end

::: moniker range="vs-2019"

Aşağıda listelenen önyükleyiciler, ne zaman çalıştırsanız çalıştırın Visual Studio 2019'un en son güvenli sürümünü her zaman yükleyebilir. Alternatif olarak, bir düzeni belirli bir Visual Studio 2019 sürümüne oluşturmak veya güncelleştirmek için, her bakım sürümü için sabit sürüm önyükleyicilerinin bağlantılarını içeren [Visual Studio 2019](/visualstudio/releases/2019/history#installing-an-earlier-release) Sürümler sayfasına gidin ve istediğiniz sürümü indirin. Bunu, düzenin kaynak konumu olarak hizmet vermek istediğiniz dizine kopyalayın.

| Sürüm                    | Önyükleyici                                                                                                                                                                                                                           |
|----------------------------|---------------------------------------------------------------------------|
| Visual Studio 2019 Enterprise sürüm 16.11   | [vs_enterprise.exe](https://aka.ms/vs/16/release/vs_enterprise.exe) |
| Visual Studio 2019 Professional sürüm 16.11 | [vs_professional.exe](https://aka.ms/vs/16/release/vs_professional.exe) |
| Visual Studio 2019 Derleme Araçları sürüm 16.11 | [vs_buildtools.exe](https://aka.ms/vs/16/release/vs_buildtools.exe) |

Desteklenen diğer önyükleyiciler arasında [vs_teamexplorer.exe](https://aka.ms/vs/16/release/vs_TeamExplorer.exe), [vs_testagent.exe](https://aka.ms/vs/16/release/vs_TestAgent.exe)ve [vs_testcontroller.exe. ](https://aka.ms/vs/16/release/vs_TestController.exe)

::: moniker-end

::: moniker range=">=vs-2022"

Aşağıda listelenen önyükleyiciler, ne zaman çalıştırsanız çalıştırın Visual Studio 2022'nin en son güvenli sürümünü her zaman Geçerli kanala yükleyebilir. Alternatif olarak, bir düzeni belirli bir sürüme veya belirli bir Visual Studio 2022 kanalına oluşturmak veya güncelleştirmek için, her kanalda her bir bakım sürümü için evergreen ve sabit sürüm önyükleyicilerinin bağlantılarını içeren [Visual Studio 2022](/visualstudio/releases/2022/release-history#release-dates-and-build-numbers) Yayın Geçmişi sayfasına gidin ve istediğiniz sürümü indirin. Bunu, düzenin kaynak konumu olarak hizmet vermek istediğiniz dizine kopyalayın. 

| Sürüm                    | Önyükleyici                                                        |
|----------------------------|----------------------------------------------------------------------|
| Visual Studio Enterprise   | [vs_enterprise.exe](https://aka.ms/vs/17/release/vs_enterprise.exe)     |
| Visual Studio Professional | [vs_professional.exe](https://aka.ms/vs/17/release/vs_professional.exe) |
| Visual Studio 2022 Derleme Araçları   | [vs_buildtools.exe](https://aka.ms/vs/17/release/vs_buildtools.exe)         |

::: moniker-end

::: moniker range="vs-2017"

>[!TIP]
>Daha önce bir önyükleyici dosyası indirdiy ve hangi sürümün olduğunu doğrulamak için aşağıdaki gibi bir dosya yükleyebilirsiniz. Bu Windows' Dosya Gezgini açın, önyükleyici dosyasına sağ tıklayın, Özellikler'i **seçin,** **Ayrıntılar sekmesini** seçin ve ardından Ürün sürüm **numarasını** görüntüleyin. Bu slası bir sürümle Visual Studio için [bkz. Visual Studio numaraları ve yayın tarihleri.](visual-studio-build-numbers-and-release-dates.md)

::: moniker-end

::: moniker range="vs-2019"

>[!TIP]
>Daha önce bir önyükleyici dosyası indirdiy ve hangi sürümün olduğunu doğrulamak için aşağıdaki gibi bir dosya yükleyebilirsiniz. Bu Windows' Dosya Gezgini açın, önyükleyici dosyasına sağ tıklayın, Özellikler'i **seçin,** **Ayrıntılar sekmesini** seçin ve ardından Ürün sürüm **numarasını** görüntüleyin. Bu sayıyla bir Visual Studio eşleşmesi için Visual Studio [2019 Sürümler](/visualstudio/releases/2019/history) sayfasının en altındaki tabloya bakın.

::: moniker-end

::: moniker range=">=vs-2022"

>[!TIP]
>Daha önce bir önyükleyici dosyası indirdiy ve hangi sürümün yüklen kuracaklarını doğrulamak için aşağıdaki şekilde devam edin. Bu Windows, Dosya Gezgini dosyasını açın, önyükleyici dosyasına sağ  tıklayın, Özellikler'i seçin ve ardından Ayrıntılar **sekmesini** seçin. Ürün **sürümü** alanı, [önyükleyicinin](/visualstudio/releases/2022/vs2022-release-rhythm) yükleyecek kanalı ve sürümü açıklar. Sürüm numarası her zaman "belirtilenin en son bakım sürümü" olarak okunması ve kanalın açıkça belirtilmemişse Geçerli olduğu varsayılır. Bu nedenle, LTSC 17.0 Ürün sürümüne sahip bir önyükleyici, 17.0 LTSC kanalında kullanılabilen en son 17.0.x bakım sürümünü yükleyecek. Yalnızca Visual Studio 2022 sürümünün Geçerli kanala Visual Studio 2022'nin en son bakım sürümünü yükley olduğunu söyleyen bir Ürün sürümüne sahip bir önyükleyici.

::: moniker-end

## <a name="create-the-network-layout"></a>Ağ düzenini oluşturma

Bu adımı tamamlamak için bir İnternet bağlantınız olması gerekir.

Yönetici ayrıcalıklarıyla bir komut istemi açın, önyükleyiciyi indirdiğiniz dizine gidin ve ağ düzeninizi oluşturmak ve korumak için [Visual Studio](use-command-line-parameters-to-install-visual-studio.md) sayfasını yüklemek için komut satırı parametrelerini kullanma sayfasında tanımlandığı gibi önyükleyicinin parametrelerini kullanın. İlk düzen oluşturmanın yaygın örnekleri aşağıda ve yükleme sayfasındaki komut satırı [parametre Visual Studio gösterilmiştir.](command-line-parameter-examples.md)  

Tek dil yereli için tam bir başlangıç düzeni için yaklaşık 35 GB disk alanı ve Visual Studio Community için 45 GB Visual Studio Enterprise. Ek [dil yerelleri için](/visualstudio/install/use-command-line-parameters-to-install-visual-studio#list-of-language-locales) her biri yaklaşık yarım GB gerekir. 
 
Önerilen yaklaşım, ağ sunucusundaki düzen dizininde Visual Studio Enterprise tüm dillerle ve tüm iş yükleriyle bir başlangıç düzeni oluşturmaktır. Böylece, istemcileriniz ürün tekliflerinin tamamına erişecek. Ağ düzeninin tam Visual Studio oluşturmak için, ağ düzenini barındırmayı planlayan makineden aşağıdakini çalıştırın:

  ```vs_enterprise.exe --layout c:\VSLayout```
  
::: moniker range=">=vs-2022"

### <a name="ensure-your-layout-has-the-correct-channel"></a>Düzeninizin doğru kanala sahip olduğundan emin olun
Ağ düzeninin doğru kanalı temel alarak olduğundan [](/visualstudio/releases/2022/vs2022-release-rhythm)emin olmak önemlidir. Bu, [](/visualstudio/install/applying-administrator-updates)yöneticinin güncelleştirme ölçütlerinden biri olduğundan kuruluş genelinde dağıtıldıysa, hangi istemci örneklerinin güncelleştirileceği belirlemek için kullanın. Örneğin, düzeniniz VisualStudio.17.Release.LTSC.17.0 kanalını temel alacak şekilde yapılandırılmışsa ve istemcileriniz Microsoft tarafından barındırılan sunuculardan güncelleştirme alacak şekilde yapılandırılmışsa, 17.0 LTSC kanalında kullanılabilir hale gelen tüm güvenlik güncelleştirmeleri bu düzenden yüklenmiş veya güncelleştirilmiş istemciler tarafından kullanılabilir. 

Yukarıda listelenen önyükleyiciler Geçerli kanalı temel almaktadır. LTSC kanallarından birini temel alan bir düzen oluşturmak [için, Visual Studio 2022](/visualstudio/releases/2022/release-history#release-dates-and-build-numbers) Yayın Geçmişi sayfasından doğru kanalın önyükleyicisini edinmeniz, bunu düzen klasörünüze kopyalamanız ve bunu kullanarak düzeni oluşturmanız veya güncelleştirmeniz gerekir. 

::: moniker-end

### <a name="configure-the-contents-of-a-network-layout"></a>Ağ düzeninin içeriğini yapılandırma

Ağ düzeninizin içeriğini özelleştirmek için kullanabileceğiniz çeşitli seçenekler vardır. Yalnızca belirli bir dil yerel ayar [kümesi,](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales)iş yükleri, bileşenler ve bunların önerilen veya isteğe bağlı bağımlılıklarını içeren [kısmi bir düzen oluşturabilirsiniz.](workload-and-component-ids.md) İstemci iş istasyonlarına yalnızca bir iş yükü alt kümesi dağıtacaksanız bu yararlı olabilir. Düzeni özelleştirmek için tipik komut satırı parametreleri şunlardır:

* `--add` iş yükü [veya bileşen kimliklerini belirtmek için](workload-and-component-ids.md). <br>`--add`kullanılırsa, yalnızca ile belirtilen iş yükleri ve bileşenler `--add` indirilir.  `--add`Kullanılmazsa, tüm iş yükü ve bileşenler indirilir.
* `--includeRecommended` belirtilen iş yükü kimlikleri için önerilen tüm bileşenleri dahil etmek için.
* `--includeOptional` belirtilen iş yükü kimlikleri için isteğe bağlı tüm bileşenleri dahil etmek için.
* `--lang` dil [yerellerini belirtmek için](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales).

Burada özel kısmi düzen oluşturmayla ilgili birkaç örnek verilmiştir.

* Yalnızca bir dil için tüm iş yükleriyle ve bileşenlerle bir düzen oluşturmak için şunları çalıştırın:

    ```shell
    vs_enterprise.exe --layout C:\VSLayout --lang en-US
    ```

* Birden çok dil için tüm iş yükleriyle ve bileşenlerle bir düzen oluşturmak için şu sayfayı çalıştırın:

    ```shell
    vs_enterprise.exe --layout C:\VSLayout --lang en-US de-DE ja-JP
    ```

* Tek bir iş yüküne ve bu iş yükü için önerilen tüm bileşenlere sahip bir düzen oluşturmak için, tüm diller için şu çalıştırın:

    ```shell
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --includeRecommended
    ```

* İki iş yüküne ve üç dil için bir isteğe bağlı bileşene sahip bir düzen oluşturmak için aşağıdakini çalıştırın:

    ```shell
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Component.Git --lang en-US de-DE ja-JP
    ```

* İki iş yüküne ve bunların önerilen ve isteğe bağlı bileşenlerine sahip bir düzen oluşturmak için şunları çalıştırın:

    ```shell
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --includeOptional
    ```
    
::: moniker range=">=vs-2019"

### <a name="ensure-your-layout-is-using-the-latest-installer"></a>Düzeninizin en son yükleyiciyi kullanmaya devam olduğundan emin olmak

Her zaman düzeninize en son Visual Studio ve istemcilerinize dağıtmanızı öneririz. Böylece, ürünün sonraki sürümlerinde kullanılabilir hale gelen yeni özelliklere ve işlevlere erişebilirsiniz. Örneğin, Visual Studio 2022 Yükleyicisini Visual Studio 2019 düzenlerinize dağıtırsanız, Visual Studio 2019 istemcileriniz bu düzeni temel alarak güncelleştirmeler için kaynak konumunu değiştirebilir. Bu işlevin yararlı olduğu senaryo, bir düzenden yüklemek ancak güncelleştirmelerin başka bir düzenden geliyor olmasıdır. En son yükleyiciyi kullanarak kapatma _da dahil_ olmak üzere daha fazla ayrıntı aşağıda [açıklanmıştır](#configure-the-layout-to-always-include-and-provide-the-latest-installer)

 > [!IMPORTANT]
 > Bu en son yükleyiciyi kullanma özelliği yalnızca Visual Studio 2022'nin ilk kez gönderildikten sonra Visual Studio 2019 önyükleyicileri tarafından kullanılabilir. Bu nedenle vs_enterprise.exe örnekteki örnek, 10 Kasım  2021'den sonra gönderilen bir sürüme sahip olması gerekir. 

* Kullanılabilir en son ve en büyük yükleyiciyi kullanan ürünün tamamının düzenini oluşturmak için şu sayfayı çalıştırın:
    ```shell
    vs_enterprise.exe --layout C:\VSLayout --useLatestInstaller
    ```

::: moniker-end

### <a name="copy-the-layout-to-a-network-share"></a>Düzeni bir ağ paylaşımına kopyalama

İstemci makinelerinden çalıştırılana kadar düzeni bir ağ paylaşımında barındırmanız gerekir. Düzeni yerel bir makinede oluşturduysanız, bir ağ konuma kopyalamanız gerekir. Aşağıdaki örnek [`xcopy`](/windows-server/administration/windows-commands/xcopy/) kullanır. Ayrıca isterseniz [`robocopy`](/windows-server/administration/windows-commands/robocopy/) kullanabilirsiniz. Örnek:

```shell
xcopy /e c:\VSLayout \\server\share\layoutdirectory
```

> [!IMPORTANT]
> Bir hatayı önlemek için ağ paylaşımında tam düzen yol 80 karakterden az olduğundan emin olun. Ya da bazı kuruluşlar 80 [karakterlik sınırlamaya](/windows/win32/fileio/symbolic-links) çözüm olarak sembolik bağlantıları başarıyla kullanmıştır.

## <a name="update-or-modify-your-layout"></a>Düzeninizi güncelleştirme veya değiştirme 
Visual Studio'nin ağ düzenini en son ürün güncelleştirmeleriyle güncelleştirebilirsiniz. Böylece istemci iş istasyonlarının hem yükleme noktası olarak hem de güncelleştirme kaynağı olarak en son sürümünü al Visual Studio. Özellikle istemcilerinizin düzenden güncelleştirmeleri almalarını sağlamak için düzeninizi düzenli aralıklarla güncelleştirmek en iyi uygulamadır. Bu bölümde en yaygın veya kullanışlı düzen bakım işlemleri açıkmektedir.

Bir dosya paylaşımında düzen barındırırsanız, düzenin özel bir kopyasını güncelleştirmek (örneğin, c:\VSLayout) ve ardından, tüm güncelleştirilmiş içerik indirildikten sonra bunu dosya paylaşımınıza kopyalayın (örneğin, \\ \server\products\VS). Bunu yapmasanız, düzeni güncelleştirirken Kurulum'u çalıştıran tüm kullanıcıların henüz tamamen güncelleştirilmediklerinden düzenden içerikte eşleşmezlik elde etme şansı daha fazladır.

### <a name="update-the-layout-to-the-most-current-version-of-the-product"></a>Düzeni ürünün en güncel sürümüne güncelleştirin
Microsoft, işlev veya güvenlik sorunlarını düzeltmek için sıklıkla ürünün güncelleştirilmiş sürümlerini yayımlar. Yeni istemci yüklemelerinin her zaman en son sürümü aldıracak şekilde, düzeninizi ürünün en son sürümüyle güncelleştirmenizi öneririz. ayrıca istemcileriniz düzenden güncelleştirme alacak şekilde yapılandırıldıklarından düzeninizi güncel tutmak da çok önemlidir. 

İlk düzeni oluşturma sırasında, düzenin yapılandırma dosyasına hangi iş yüklerinin ve dillerin dahil olduğu gibi belirtilen seçenekler kaydedilir. Daha sonra bu düzeni ürünün daha yeni bir sürümüne güncelleştirmek istediğinizde, ilk düzen oluşturma sırasında kullanılan seçenekleri yeniden belirtmenize gerek yoktur. Düzen güncelleştirme komutları, kaydedilen düzen ayarlarını otomatik olarak kullanır. 

Yukarıdaki tabloda yer alan [evergreen](#download-the-visual-studio-bootstrapper-to-create-the-network-layout)önyükleyicilerden birini kullanarak bu kısmi düzeni zaten oluşturduğunuz düşünün.

```shell
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
```

Bu düzeni Microsoft tarafından sunulan ve Microsoft sunucularında barındırılan ürünün en son sürümüne güncelleştirmek kolaydır. Yalnızca aynı yeşil önyükleyiciyi kullanmalı ve en son paketleri düzeninize `--layout` indirmek için komutunu yeniden çalıştırmanız gerekir.

```shell
vs_enterprise.exe --layout c:\VSLayout
```

Ayrıca, düzeninizi katılımsız bir şekilde daha yeni bir sürüme güncelleştirebilirsiniz. Düzen işlemi, kurulum işlemini yeni bir konsol penceresinde çalıştırır. Kullanıcıların son sonucu ve oluşan hataların özetini görene kadar pencere açık bıraktır. Bir düzen işlemini katılımsız bir şekilde gerçekleştirıyorsanız (örneğin, düzeninizi en son sürüme güncelleştirmek için düzenli olarak çalıştıran bir betiğiniz varsa) parametresini kullanın; böylece işlem pencereyi otomatik `--passive` olarak kapatır.

```shell
vs_enterprise.exe --layout c:\VSLayout --passive
```

### <a name="update-the-layout-to-a-specific-version-of-the-product"></a>Düzeni ürünün belirli bir sürümüne güncelleştirme
Bazen düzeninizi ürünün belirli bir _sürümüne güncelleştirmek istiyor olabilirsiniz._  Örneğin, düzeninizin, kuruluşu standart hale getirerek bakım temel çizgisinin en son güvenli sürümüyle eşleşmesini sağlamak istiyor olabilirsiniz. Bu işlemi şöyle yapabilirsiniz:

::: moniker range="vs-2019"

[Visual Studio 2019](/visualstudio/releases/2019/history#installing-an-earlier-release) Sürümler sayfasına gidip belirli bir sabit sürüm önyükleyicisini indirebilir, düzeninize kopyalayıp düzeni önyükleyicide belirtilen tam sürüme güncelleştirmek için kullanabilirsiniz. Yukarıdaki söz dizimini tam olarak aynı şekilde kullanabilirsiniz.

::: moniker-end

::: moniker range="vs-2022"

[Visual Studio 2022](/visualstudio/releases/2022/release-history#release-dates-and-build-numbers) Yayın Geçmişi sayfasına gidip belirli bir sabit sürüm önyükleyicisini indirebilir, düzeninize kopyalayıp düzeni önyükleyicide belirtilen tam sürüme güncelleştirmek için kullanabilirsiniz. Yukarıdaki söz dizimini tam olarak aynı şekilde kullanabilirsiniz.

::: moniker-end

Düzeninizi belirli **[bir sürüme](applying-administrator-updates.md)** güncelleştirmek için yönetici güncelleştirmesini kullanabilirsiniz. Yönetici **Güncelleştirmesini almak** için Microsoft Update [Kataloğu'Microsoft Update](https://catalog.update.microsoft.com)gidin, düzeninizi güncelleştirmek istediğiniz güncelleştirmeyi arayın.  Uygulamayı _update.exe_ barındıran bilgisayara indirin, bu bilgisayarda bir komut istemi açın ve aşağıdaki gibi bir komut çalıştırın:

```shell
visualstudioupdate-17.0.0to17.0.1.exe layout --layoutPath c:\VSLayout
```
Yönetici güncelleştirmelerinin özgün düzen yüklemesi başlatmayacaklarını unutmayın; yalnızca mevcut bir düzeni veya istemci örneğini güncelleştirecek. 

::: moniker range=">=vs-2022"

### <a name="modify-the-channel-of-the-network-layout"></a>Ağ düzeninin kanalını değiştirme

Bazen, kanallar destekten dışarı geçişte olduğundan, ağ düzeninin desteklenen bir kanalı temel almaya devam ettiğine emin olun, böylece istemcileriniz güvenlik güncelleştirmeleri bildirimlerini almaya devam eder. Düzeniniz VisualStudio.17.Release.LTSC.17.0 kanalını temel aldıktan sonra 17.0 LTSC kanalı destekten çıktıktan sonra bu kanalda daha fazla güvenlik güncelleştirmesi yayınlamayacak ve düzeniniz ve istemcileriniz güvensiz hale gelecektir.

Düzenin temel alınan kanalı değiştirmek için, [Visual Studio 2022](/visualstudio/releases/2022/release-history#release-dates-and-build-numbers) Yayın Geçmişi sayfasından istediğiniz kanalın önyükleyicisini alın, düzen klasörünüze kopyalayın ve normal bir güncelleştirme gerçekleştirin. Bundan sonra istemcileriniz de güvenli kalabilecekleri bir güncelleştirme hakkında uygun şekilde bilgi almak zorunda kalır.

::: moniker-end

### <a name="modify-the-contents-of-the-layout"></a>Düzenin içeriğini değiştirme

Bu düzeni değiştirmek ve ek iş yükleri ya da bileşenler ya da diller eklemek veya kaldırmak mümkündür. Aşağıdaki örnekte, yukarıda oluşturduğum düzene Azure iş yükünü ve yerelleştirilmiş bir dili ekleyebilirsiniz. Değişikliği tamamladikten sonra hem Yönetilen Masaüstü hem de Azure iş yükleri ile İngilizce ve Almanca kaynaklar bu düzende yer alır. Ayrıca düzen, kullanılabilir en son sürüme güncelleştirilir.

```shell
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
```

Mevcut bir kısmi düzeni tam düzen olacak şekilde değiştirmek için, aşağıdaki örnekte gösterildiği gibi --all seçeneğini kullanın.

```shell
vs_enterprise.exe --layout c:\VSLayout --all
```

Sürümü güncelleştirmeden ek bir iş yükü ve yerelleştirilmiş dil _ekleme hakkında_ bilgi için buraya bakın. (Bu komut, ASP.NET web geliştirme iş yükünü ekler.) Artık Yönetilen Masaüstü, Azure ve ASP.NET & Web Geliştirme iş yükleri bu düzende yer almaktadır. Bu iş yüklerinin tamamında İngilizce, Almanca ve Fransızca dil kaynakları da mevcuttur. Ancak, bu komut çalıştır çalıştır olduğunda düzen kullanılabilir en son sürüme güncelleştirilmez. Mevcut sürümde kalır.

```shell
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.NetWeb --lang fr-FR --keepLayoutVersion
```

 > [!IMPORTANT]
 > Güncelleştirme işlemi, düzen veya istemciye ek isteğe bağlı bileşenleri indirmez veya yüklemez. İsteğe bağlı bileşenleri eklemeniz veya değiştirmenizi gerekirse, önce yapılandırma dosyasından eski isteğe bağlı bileşenleri kaldırın ve ihtiyacınız olan yeni bileşenleri `layout.json` dosyasının "ekle" bölümüne `layout.json` ekleyin. Ardından, düzeni güncelleştirmek `--layout` için komutunu çalıştırarak yeni eklenen bileşenleri düzene indirir.
 >
 > Bu yeni bileşenleri istemci makinesine yüklemek için bu üç adımı tamamlayanın. İlk olarak, düzenin yukarıda açıklandığı gibi yeni bileşenleri içerdiğini doğrulayın. Ardından, istemcinizi düzende en son bitlere güncelleştirin. Son olarak, istemcide yeniden, istemci makinesine yeni bileşenleri (düzene eklenmiş olan) yükecek bir değiştirme işlemi çalıştırın.

::: moniker range=">=vs-2019"

### <a name="configure-the-layout-to-always-include-and-provide-the-latest-installer"></a>Düzeni her zaman dahil etmek ve en son yükleyiciyi sağlamak için yapılandırma

Yükleyici daha yeni bir _sürümün_ parçası olarak kabul edilirse bile, düzeninizi her zaman dahil etmek ve istemcilerinize en son yükleyiciyi sağlamak üzere Visual Studio. Bu nedenle, istemciniz bu düzenden güncelleştirmeler sağladığında, bu düzen tarafından dahil edilen ve sağlanan en son yükleyiciyi edinecek. Bunun avantajı, istemcinize en son yükleyicinin yüklenmesinden sonra istemci yüklemelerinin yükleyiciye eklemeye devam eden hata düzeltmelerinden ve yeni işlevlerden yararlanabilecek olmasıdır. 

::: moniker-end

::: moniker range="vs-2019"

>[!TIP]
>İstemcinizin Visual Studio [2019](/visualstudio/install/update-visual-studio#configure-source-location-of-updates)yüklemesinde güncelleştirmelerin bulunduğu konumu değiştirmek için istemci  makinenize en son Visual Studio 2022 yükleyicisini alasınız. Bunu yapmanın bir yolu, Visual Studio 2022 yükleyicisini aşağıda açıklanan parametreleri kullanarak Visual Studio 2019 düzenlerinize dahil etmektir. En son yükleyiciyi kullanma özelliği yalnızca Visual Studio 2022 ilk kez gönderildikten sonra Visual Studio 2019 önyükleyicileri tarafından kullanılabilir. Bu nedenle, aşağıdaki örnekteki vs_enterprise.exe 10 Kasım 2021 ' _den sonra_ gelen bir sürüm olmalıdır. 

::: moniker-end

::: moniker range=">=vs-2019"

Düzeninizi, en son yükleyiciyi dahil etmek ve sağlamak üzere etkinleştirmenin iki yolu vardır:
- `--useLatestInstaller`Düzeni oluştururken veya güncelleştirirken, yükleyiciyi önyükleyici olarak geçirebilirsiniz. Bu, düzenin kök dizininde bulunan Layout. json dosyasında bir ayarın ayarlanmasına neden olur. Bu, düzeni güncelleştirme ve en son ve en büyük yükleyiciyi kullanacak şekilde yapılandırma hakkında bir örnektir.  
   ```shell
   vs_enterprise.exe --layout C:\VSLayout --useLatestInstaller
   ```

- Bu ayarı eklemek için Layout. json dosyasını doğrudan düzenleyebilirsiniz.

   ```Example layout.json contents
   {
     "installChannelUri": ".\\ChannelManifest.json",
     "channelUri": "\\\\server\\share\\layoutdirectory\\ChannelManifest.json",
     "installCatalogUri": ".\\Catalog.json",
     "channelId": "VisualStudio.16.Release",
     "productId": "Microsoft.VisualStudio.Product.Enterprise",
   
     "useLatestInstaller": true
     
   }
   ```

Layout. json dosyasında bu ayarı program aracılığıyla kaldırmanın bir yolu yoktur. bu nedenle, mizanpajınızı Microsoft 'un kullanılabilir olduğu en son yükleyiciyi kullanmayı _durdurmasını_ istiyorsanız (büyük olasılıkla en son yükleyiciden daha eski olan), düzen. json dosyasını düzenlemeniz ve ayarı kaldırmanız yeterlidir `"UseLatestInstaller": true` . 

Bu `"UseLatestInstaller": true` ayarı, düzenin Response. json dosyasında de bulabilirsiniz, ancak burada yok sayılır. [Yanıt. JSON dosyası, istemci bir düzenden yüklediğinde veya bir düzeninden güncelleştirme yaparken  varsayılan yapılandırma seçeneklerini ayarlamak için kullanılır](/visualstudio/install/automated-installation-with-response-file). Bu `"useLatestInstaller": true` ayar, _Düzen_ içeriğinin en son yükleyiciyi içerdiğinden emin olmak için kullanılır, böylece istemci makineleri düzenden en son yükleyiciyi elde edebilir.   

::: moniker-end

### <a name="verify-a-layout"></a>Bir düzeni doğrulama

`--verify`Paket dosyalarının eksik veya geçersiz olup olmadığını denetleyen ağ düzeninde doğrulama gerçekleştirmek için kullanın. Doğrulamanın sonunda, eksik ve geçersiz dosyaların listesini yazdırır.

Doğrulama yalnızca belirli bir Visual Studio alt sürümünün en son sürümü için geçerlidir. Yeni bir sürüm yayımlandığında, doğrulama önceki sürümleri içeren düzenlerle çalışmaz.

```shell
vs_enterprise.exe --layout <layoutDir> --verify
```

> [!NOTE]
> Seçeneğinin gerektirdiği bazı önemli meta veri dosyaları `--verify` Düzen klasöründe olmalıdır. Bu meta veri dosyaları eksikse, "--Verify" çalıştırılamaz ve kurulum size bir hata verir. Bu hatayla karşılaşırsanız, düzeni yeniden güncelleştirmeyi deneyin veya farklı bir klasörde yeni bir ağ düzeni yeniden oluşturun.

Microsoft 'un güncelleştirmeleri düzenli aralıklarla Visual Studio aldığını unutmayın. bu nedenle, [sabit bağlantı bootstrap'ı](#download-the-visual-studio-bootstrapper-to create-the-network-layout)kullanmadığınız sürece daha yeni bir düzen ilk düzen ile aynı sürümü içermeyebilir.

### <a name="fix-a-layout"></a>Düzeni çözme

İle `--fix` aynı doğrulamayı gerçekleştirmek `--verify` ve ayrıca belirtilen sorunları gidermeyi denemek için kullanın. `--fix`İşlemin bir internet bağlantısı olması gerekir, bu nedenle, çağırabilmeniz için makinenizin internet 'e bağlı olduğundan emin olun `--fix` .

```shell
vs_enterprise.exe --layout <layoutDir> --fix
```

### <a name="remove-older-versions-from-a-layout"></a>Eski sürümleri düzenden kaldırma

bir ağ önbelleğinde düzen güncelleştirmeleri gerçekleştirdikten sonra, düzen klasöründe en son Visual Studio yüklemesinde artık gerekli olmayan bazı eski paketler bulunabilir. `--clean`Kullanılmayan paketleri ağ düzeni klasöründen kaldırmak için seçeneğini kullanabilirsiniz.

Bunu yapmak için, bu eski paketleri içeren katalog bildirimlerinin dosya yolları gerekir. Katalog bildirimlerini, ağ düzeni önbelleğindeki bir "Arşiv" klasöründe bulabilirsiniz. Bir düzeni güncelleştirdiğinizde bunlar buraya kaydedilir. "Arşiv" klasöründe, her biri eski bir katalog bildirimi içeren bir veya daha fazla "GUID" adlı klasör vardır. "GUID" klasörlerinin sayısı, düzenlerinizde yapılan güncelleştirme sayısıyla aynı olmalıdır.

Her bir "GUID" klasörünün içine birkaç dosya kaydedilir. En çok ilgilendiğiniz iki dosya bir "Catalog. JSON" dosyası ve bir "version.txt" dosyasıdır. "Catalog. JSON" dosyası, seçeneğe geçirmeniz gereken eski Katalog bildirimidir `--clean` . Diğer version.txt dosyası, bu kullanımdan kaldırılmış Katalog bildiriminin sürümünü içerir. Sürüm numarasına bağlı olarak, eski paketleri bu katalog bildiriminden kaldırmak isteyip istemediğinize karar verebilirsiniz. Diğer "GUID" klasörlerinde ilerlerinizle aynı şekilde yapabilirsiniz. Temizlemek istediğiniz katalogda karar verdikten sonra, `--clean` Bu kataloglara dosya yollarını sağlayarak komutunu çalıştırın.

--Clean seçeneğinin nasıl kullanılacağına ilişkin bir örnek aşağıda verilmiştir:

```shell
c:\VSLayout\vs_enterprise.exe --layout c:\VSLayout --clean c:\VSLayout\Archive\1cd70189-fc55-4583-8ad8-a2711e928325\Catalog.json --clean c:\VSLayout\Archive\d420889f-6aad-4ba4-99e4-ed7833795a10\Catalog.json
```

Bu komutu çalıştırdığınızda, kurulum, kaldıramayacak dosyaların listesini bulmak için ağ düzeni klasörünüzü analiz eder. Daha sonra silinecek dosyaları gözden geçirebilir ve silme işlemlerini onaylamanız şansınız olur.

## <a name="install-visual-studio-onto-a-client-machine-from-a-network-installation"></a>bir ağ yüklemesinden istemci makinesine Visual Studio yükleme

yöneticiler, yükleme komut dosyasının bir parçası olarak istemci iş istasyonlarına Visual Studio dağıtabilir. ya da yönetici haklarına sahip kullanıcılar, makinesine Visual Studio yüklemek için doğrudan paylaşımdan kurulum çalıştırabilir.

* Kullanıcılar aşağıdaki komutu çalıştırarak ürünü bir ağ düzeninden el ile yükleyebilir:

    ```shell
    \\server\products\VS\vs_enterprise.exe
    ```

* Yöneticiler, aşağıdaki komutu çalıştırarak katılımsız modda yüklenebilir:

    ```shell
    \\server\products\VS\vs_enterprise.exe --quiet --wait --norestart
    ```

> [!NOTE] 
> Sabırlı olun. `--wait`Hem yükleyicinin hem de ürünün tamamlaması için olduğunuzdan emin olun. bir istemciyi bir düzenden yüklerken veya güncelleştirirken, yükleyici her zaman yükleme veya güncelleştirme için ilk şeydir ve Visual Studio ürünün kendisi yüklenir veya güncelleştirilir. Bu işlemlerin **her Ikisinin de** başarılı bir güncelleştirme olarak değerlendirilmesi için tamamlaması gerekir.   
>
> Katılımsız otomatik toplu iş dosyasının bir parçası olarak yükleme veya güncelleştirme yürütürken, `--wait` `vs_enterprise.exe` bir çıkış kodu döndürülünceye kadar işlemin yükleme tamamlanana kadar bekleyip emin olmak için bu seçenek yararlı olur. Bu, bir Kurumsal Yönetici, [başarılı bir yüklemeye bir ürün anahtarı uygulama](automatically-apply-product-keys-when-deploying-visual-studio.md)gibi tamamlanan bir yüklemede daha fazla eylem gerçekleştirmek isterse yararlı olur. --Wait seçeneğinin kullanılması, sonraki işlemlerin erken dönmesini önler. Kullanmıyorsanız `--wait` , `vs_enterprise.exe` yüklemenin her iki bölümü de tamamlanmadan önce işlem çıkabilir ve bu nedenle yükleme işleminin durumunu temsil etmeyen yanlış bir çıkış kodu döndürür.

### <a name="install-on-a-client-that-doesnt-have-internet-access"></a>İnternet erişimi olmayan bir istemciye yüklemesi

Bir düzenden yüklerken, yüklenen içerik varsayılan olarak düzenden alınır. ancak, mizanpajda olmayan bir bileşeni seçerseniz ve [istemci güncelleştirmeler için Microsoft tarafından barındırılan sunuculara bakmak üzere yapılandırılmışsa](/visualstudio/install/automated-installation-with-response-file), yükleyici Visual Studio paketlerini internetten edinmeye çalışacaktır. Visual Studio kurulum 'un, düzeninizde bulunmayan web 'den içerik yüklemeye çalışmasını engellemek istiyorsanız, `--noWeb` seçeneğini kullanın. `--noWeb`Kullanılıyorsa ve mizanpajda yüklenmek üzere seçilen içerik eksikse, kurulum başarısız olur.

> [!IMPORTANT]
> bu `--noWeb` seçenek, istemci, güncelleştirmeler için Microsoft tarafından barındırılan sunuculara bakmak üzere yapılandırılmışsa, internet 'e bağlı bir istemci makinesindeki Visual Studio yükleyiciyi güncelleştirmeleri _denetlemesinin_ durdurmaz. Bunun yerine, `--noWeb` yalnızca istemcinin ürün paketlerini indirmelerini önler. daha fazla bilgi için, [bir ağ düzeninden yüklenmiş Visual Studio istemcisini güncelleştirme](/visualstudio/install/update-a-network-installation-of-visual-studio) sayfasına bakın.

::: moniker range=">=vs-2019"

"Aşağıdaki parametrelerle eşleşen bir ürünün bulunamadığını" belirten bir hata iletisi alırsanız, anahtarı kullandığınızdan emin olun `--noweb` .

::: moniker-end

### <a name="configure-initial-client-installation-defaults-for-this-layout"></a>Bu düzen için ilk istemci Yükleme varsayılanlarını Yapılandır

Ürün istemci makinesine başlangıçta yüklendiğinde kullanılan varsayılan değerleri ayarlamak için Düzen klasöründeki bazı dosyaları değiştirebilirsiniz. Ortak yapılandırma seçenekleri şunlardır:
- İlk yüklemesi sırasında **Varsayılan olarak hangi iş yüklerini, bileşenleri veya dilleri seçeceğini yapılandırabilme** . 
- **İstemcinin güncelleştirmelerin nereden alacağını** belirtme özelliği.  Seçenekler, yönetici denetimli ağ düzeni konumundan veya Internet 'teki Microsoft tarafından barındırılan sunuculardan (varsayılan olarak) bulunur.

düzen için varsayılan istemci ayarlarını özelleştirme ve yapılandırma hakkında daha fazla bilgi için bkz. [bir yanıt dosyasıyla Visual Studio yüklemeyi otomatikleştirme](automated-installation-with-response-file.md).  

### <a name="configure-enterprise-deployment-behavior"></a>Kurumsal Dağıtım davranışını yapılandırma

::: moniker range=">=vs-2019"

Ayrıca, gibi diğer kurumsal dağıtım davranışlarını da denetleyebilirsiniz. 

- Yönetici güncelleştirmelerinin etkinleştirilmesi ve bunların nasıl uygulanması gerektiği 
- hangi güncelleştirme kanalları kullanılabilir ve ağ düzenlerinin güncelleştirme Ayarlar iletişim kutusunda istemci makinelerde görünme şekli.
- Paylaşılan paketlerin yüklendiği yer.
- Paketlerin önbelleğe alınıp alınmayacağı.
- Bildirimlerin görünme veya görünme şekli

ek ayrıntılar için [Visual Studio kurumsal dağıtımlarına yönelik varsayılanları ayarlama](set-defaults-for-enterprise-deployments.md) bölümüne bakın.

::: moniker-end

::: moniker range="vs-2017"

Paylaşılan paketlerin yüklendiği gibi diğer kurumsal dağıtım davranışlarını da denetleyebilirsiniz. ek ayrıntılar için [Visual Studio kurumsal dağıtımlarına yönelik varsayılanları ayarlama](set-defaults-for-enterprise-deployments.md) bölümüne bakın.

::: moniker-end

### <a name="error-codes"></a>Hata kodları

Parametresini kullandıysanız, `--wait` işlem sonucuna bağlı olarak, `%ERRORLEVEL%` ortam değişkeni aşağıdaki değerlerden birine ayarlanır:

[!INCLUDE[install-error-codes-md](includes/install-error-codes-md.md)]

### <a name="get-support-for-your-network-layout"></a>Ağ düzeniniz için destek alın

Ağ düzeninizle ilgili bir sorunla karşılaşırsanız, bunun hakkında bilgi sahibi olmak istiyoruz. bize söylemek için en iyi yol, hem Visual Studio Yükleyicisi hem de Visual Studio ıde 'de görüntülenen [sorun bildir](/visualstudio/ide/how-to-report-a-problem-with-visual-studio) aracını kullanmaktır. bt yöneticisiyseniz ve yüklü Visual Studio yoksa, [**buraya buraya, yönetici geri bildirimi**](https://aka.ms/vs/admin/guide)gönderebilirsiniz. Bu aracı kullandığınızda, bu sorunu tanılamanıza ve gidermenize yardımcı olabilecek [vs Collect aracından](https://aka.ms/vscollect) günlükleri gönderebiliyorsanız çok yararlı olacaktır.

Ayrıca, yükleme ile ilgili sorunlar için bir [**yükleme sohbeti**](https://visualstudio.microsoft.com/vs/support/#talktous) (yalnızca İngilizce) için destek seçeneği sunuyoruz.

Diğer destek seçenekleri de mevcuttur. [Visual Studio geliştirici Community](https://developercommunity.visualstudio.com/home)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
- [Visual Studio’nun ağ tabanlı yüklemesini güncelleştirme](update-a-network-installation-of-visual-studio.md)
- [Visual Studio yüklerken veya kullanırken ağla ilgili hatalarda sorun giderme](troubleshooting-network-related-errors-in-visual-studio.md)
- [ağ tabanlı Visual Studio dağıtımlarında güncelleştirmeleri denetleme](controlling-updates-to-visual-studio-deployments.md)
- [ürün yaşam döngüsü ve bakım Visual Studio](/visualstudio/releases/2019/servicing/)
- [Bakım temeli sırasında Visual Studio’yu güncelleştirme](update-servicing-baseline.md)
- [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
- [Visual Studio iş yükü ve bileşen kimlikleri](workload-and-component-ids.md)
- [Visual Studio çevrimdışı yükleme için gerekli sertifikaları yükleme](install-certificates-for-visual-studio-offline.md)
