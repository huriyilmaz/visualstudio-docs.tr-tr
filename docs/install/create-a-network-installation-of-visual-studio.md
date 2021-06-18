---
title: Ağ tabanlı yükleme oluşturma
description: Bir kuruluş içinde uygulama dağıtmak için ağ yükleme noktası Visual Studio öğrenin.
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 4CABFD20-962E-482C-8A76-E4012052F701
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 080c4450cfcdca28386811865229af75303beb6a
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307537"
---
# <a name="create-a-network-installation-of-visual-studio"></a>Ağ yüklemesi oluşturma Visual Studio

Bazen kuruluş yöneticisi, istemci iş istasyonlarına dağıtılabilir Visual Studio içeren bir ağ yükleme noktası oluşturmak ister. Bu, istemci makinelerinin sınırlı izinlere veya sınırlı İnternet erişimine sahip olduğu ya da şirket içi ekiplerin geliştirici araç kümesine belirli bir sürümü standart hale getirmeden önce uyumluluk testi yapmak istemesi senaryolarını kolaylaştırmaktır. Bir yöneticinin Visual Studio temel olarak hem  ilk yükleme hem de gelecekteki tüm ürün güncelleştirmeleri için tüm Visual Studio dosyalarını içeren bir iç statik ağ paylaşımında bulunan bir dosya önbelleğini oluşturacak bir ağ düzeni oluşturacak şekilde tasarlayacağız.

 > [!NOTE]
 >  - Kurum içinde birden fazla Visual Studio sürümünüz varsa (örneğin, hem Visual Studio 2019 Professional hem de Visual Studio 2019 Enterprise), her sürüm için ayrı bir ağ yükleme paylaşımı oluşturmanız gerekir.
 >  - İlk istemci yüklemesini öncesinde istemcilerin ürün güncelleştirmelerini nasıl _almalarını istediğinize_ karar vermenizi öneririz.  Bu, yapılandırma seçeneklerinizin doğru şekilde ayar olduğundan emin olunmasınızı kolaylaştırır. Seçenekleriniz, istemcilerin güncelleştirmeleri ağ düzeni konumdan veya İnternet'den aldırmalarını içerir. 
 >  - Özgün Visual Studio yükleme düzeni ve sonraki tüm ürün güncelleştirmelerinin, onarım ve kaldırma işlevlerinin düzgün şekilde çalışması için aynı ağ dizininde yer alıyor olması gerekir.

## <a name="download-the-visual-studio-bootstrapper"></a>Önyükleyiciyi Visual Studio indirme

Istediğiniz uygulamanın sürümü için bir önyükleyici Visual Studio indirin. Kaydet'i ve **ardından Klasör** aç'ı **seçtiğinizden emin olun.**

::: moniker range="vs-2017"

Visual Studio 2017 sürüm 15.9 için en son önyükleyiciyi [](https://visualstudio.microsoft.com/vs/older-downloads/) almak için Visual Studio önceki sürümler sayfasına gidin ve aşağıdaki önyükleyici dosyalarından birini indirin:

| Sürüm                                      | Dosyaadı            |
|----------------------------------------------|---------------------|
| Visual Studio 2017 Enterprise sürüm 15.9   | vs_enterprise.exe   |
| Visual Studio 2017 Professional sürüm 15.9 | vs_professional.exe |
| Visual Studio 2017 Derleme Araçları sürüm 15.9  | vs_buildtools.exe   |

Desteklenen diğer önyükleyiciler vs_feedbackclient.exe, vs_teamexplorer.exe, vs_testagent.exe, vs_testcontroller.exe ve vs_testprofessional.exe.

::: moniker-end

::: moniker range="vs-2019"

başlangıç olarak Visual Studio indirmeleri sayfasından [Visual Studio](https://visualstudio.microsoft.com/downloads) 2019 önyükleyicisi veya seçtiğiniz sürüm ve sürüm için [Visual Studio 2019](/visualstudio/releases/2019/history#installing-an-earlier-release) Sürümler Visual Studio.  Kurulum yürütülebilir dosyanız veya daha belirli olması için, önyükleyici dosyası aşağıdakilerden &mdash; &mdash; biri ile eşler veya benzer olur:

| Sürüm                    | İndir                                                                                                                                                                                                                           |
|----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Visual Studio Enterprise   | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019)     |
| Visual Studio Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
| Visual Studio Derleme Araçları  | [vs_buildtools.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |

Desteklenen diğer önyükleyiciler arasında [vs_teamexplorer.exe, ](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/4026077127d25d33789f3882998266946608d8ada378b6ed7c8fff8c07f3dde2/vs_TeamExplorer.exe) [vs_testagent.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/1383bf8bcda3d0e986a2e42c14114aaea8a7b085d31aa0623c9f70b2bad130e4/vs_TestAgent.exe)ve [vs_testcontroller.exe. ](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/54dcf24b76e7cd9fb8be0ac518a9dfba6daf18fe9b2aa1543411b1cda8820918/vs_TestController.exe)

::: moniker-end

::: moniker range=">=vs-2022"

>![!TIP]
> Visual Studio 2022'nin yayımlanan sürümleri henüz kullanılamıyor, aşağıdaki önyükleyiciler Visual Studio 2022'nin önizleme sürümü için.
Visual Studio indirme sayfasından Visual Studio 2022 [önyükleyicisi'Visual Studio indirin.](https://aka.ms/vs2022preview)

| Sürüm                    | İndir                                                                             |
|----------------------------|--------------------------------------------------------------------------------------|
| Visual Studio Enterprise   | [vs_enterprise.exe](https://aka.ms/vs/17/preview/bootstrapper/vs_enterprise.exe)     |
| Visual Studio Professional | [vs_professional.exe](https://aka.ms/vs/17/preview/bootstrapper/vs_professional.exe) |

::: moniker-end

::: moniker range="vs-2017"

>[!TIP]
>Daha önce bir önyükleyici dosyası indirdiy ve hangi sürümün olduğunu doğrulamak için aşağıdaki gibi bir dosya yükleyebilirsiniz. Windows'da Dosya Gezgini açın, önyükleyici dosyasına sağ tıklayın, Özellikler'i **seçin,** **Ayrıntılar sekmesini seçin** ve ardından Ürün sürüm **numarasını** görüntüleyin. Bu slanı bir yayın sürümüyle Visual Studio için [bkz. Visual Studio numaraları ve yayın tarihleri.](visual-studio-build-numbers-and-release-dates.md)

::: moniker-end

::: moniker range="vs-2019"

>[!TIP]
>Daha önce bir önyükleyici dosyası indirdiy ve hangi sürümün olduğunu doğrulamak için aşağıdaki gibi bir dosya yükleyebilirsiniz. Windows'da Dosya Gezgini açın, önyükleyici dosyasına sağ tıklayın, Özellikler'i **seçin,** **Ayrıntılar sekmesini seçin** ve ardından Ürün sürüm **numarasını** görüntüleyin. Bu s numarayı bir sürümle Visual Studio için [bkz. Visual Studio 2019 Yayınları.](/visualstudio/releases/2019/history)

::: moniker-end

::: moniker range=">=vs-2022"

>[!TIP]
>Daha önce bir önyükleyici dosyası indirdiy ve hangi sürümün olduğunu doğrulamak için aşağıdaki gibi bir dosya yükleyebilirsiniz. Windows'da Dosya Gezgini açın, önyükleyici dosyasına sağ tıklayın, Özellikler'i **seçin,** **Ayrıntılar sekmesini seçin** ve ardından Ürün sürüm **numarasını** görüntüleyin. Bu sayıyla bir Visual Studio eşleşmesi için [bkz. Visual Studio 2022 Yayınları.](/visualstudio/releases/2022/history)

::: moniker-end

## <a name="create-an-offline-installation-folder"></a>Çevrimdışı yükleme klasörü oluşturma

Bu adımı tamamlamak için bir İnternet bağlantınız olması gerekir.

Bir komut istemi açın, önyükleyiciyi indirdiğiniz dizine gidin ve ağ yükleme önbelleğinizi oluşturmak ve korumak için [Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) yüklemek için komut satırı parametrelerini kullanma sayfasında tanımlandığı gibi önyükleyicinin parametrelerini kullanın. İlk düzen oluşturmanın yaygın örnekleri aşağıda ve yüklemesi için [Komut satırı parametre Visual Studio gösterilmiştir.](../install/command-line-parameter-examples.md)  

   > [!IMPORTANT]
   > Tek dil yereli için tam bir başlangıç düzeni için yaklaşık 35 GB disk alanı ve Visual Studio Community için 42 GB Visual Studio Enterprise. Ek [dil yerelleri için](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales) her biri yaklaşık yarım GB gerekir. Daha fazla [bilgi için Ağ düzenini](#customize-the-network-layout) özelleştirme bölümüne bakın. Sonraki düzen güncelleştirmelerinin de aynı ağ konumu içinde depolanmış olması gerektiğini, bu nedenle ağ düzeni konumunun dizin içeriklerinin zaman içinde oldukça genişleyebizleyebilirsiniz.  

- Tüm diller ve tüm özelliklerle Visual Studio Enterprise başlangıç düzeni oluşturmak için şu şekilde çalıştırın:

  ```vs_enterprise.exe --layout c:\VSLayout```

- Tüm diller ve tüm özelliklerle Visual Studio Professional başlangıç düzeni oluşturmak için şu şekilde çalıştırın:

  ```vs_professional.exe --layout c:\VSLayout```

## <a name="modify-the-responsejson-file"></a>Dosya response.jsdeğiştirme

Kurulum çalıştır olduğunda `response.json` kullanılan varsayılan değerleri ayarlamak için dosyasını değiştirebilirsiniz.  Örneğin, dosyayı otomatik olarak `response.json` seçilecek belirli bir iş yükü kümesi seçecek şekilde yapılandırabilirsiniz. ayrıca istemcinin ağ `response.json` düzeni konumdan yalnızca güncelleştirilmiş dosyaları alacak olup olamayacaklarını belirtmek için de yapılandırabilirsiniz. Daha fazla bilgi için [bkz. Yanıt Visual Studio yüklemesini otomatikleştirme.](../install/automated-installation-with-response-file.md) 

Visual Studio önyükleyicisi bir dosyayla eşleştirilirken hata verirken bir sorunla karşılaştınız, daha fazla bilgi için bkz. Visual Studio sayfasını yükleme veya kullanma sırasında ağ ile `response.json` [ilgili](../install/troubleshooting-network-related-errors-in-visual-studio.md#error-failed-to-parse-id-from-parent-process) hataları giderme.

## <a name="copy-the-layout-to-a-network-share"></a>Düzeni bir ağ paylaşımına kopyalama

İstemci makinelerinden çalıştırılamaları için düzeni bir ağ paylaşımında barındırabilirsiniz.

Aşağıdaki örnek [`xcopy`](/windows-server/administration/windows-commands/xcopy/) kullanır. Ayrıca isterseniz [`robocopy`](/windows-server/administration/windows-commands/robocopy/) kullanabilirsiniz.

::: moniker range="vs-2017"

Örnek:

```shell
xcopy /e c:\VSLayout \\server\products\VS2017
```

::: moniker-end

::: moniker range="vs-2019"

```shell
xcopy /e c:\VSLayout \\server\products\VS2019
```

::: moniker-end

::: moniker range=">=vs-2022"

```shell
xcopy /e c:\VSLayout \\server\products\VS2022
```

::: moniker-end

> [!IMPORTANT]
> Bir hatayı önlemek için tam düzen yol 80 karakterden az olduğundan emin olun.

## <a name="customize-the-network-layout"></a>Ağ düzenini özelleştirme

Ağ düzeninizi özelleştirmek için kullanabileceğiniz çeşitli seçenekler vardır. Yalnızca belirli bir dil yerel ayar [kümesi,](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales)iş yükleri, bileşenler ve bunların önerilen veya isteğe bağlı bağımlılıklarını içeren [kısmi bir düzen oluşturabilirsiniz.](workload-and-component-ids.md) İstemci iş istasyonlarına yalnızca bir iş yükü alt kümesi dağıtacaksanız bu yararlı olabilir. Düzeni özelleştirmek için tipik komut satırı parametreleri şunlardır:

* `--add` iş yükü [veya bileşen kimliklerini belirtmek için](workload-and-component-ids.md). <br>`--add`kullanılırsa, yalnızca ile belirtilen iş yükleri ve bileşenler `--add` indirilir.  `--add`Kullanılmazsa, tüm iş yükü ve bileşenler indirilir.
* `--includeRecommended` belirtilen iş yükü kimlikleri için önerilen tüm bileşenleri dahil etmek için
* `--includeOptional` belirtilen iş yükü kimlikleri için önerilen ve isteğe bağlı tüm bileşenleri dahil etmek için.
* `--lang` dil [yerellerini belirtmek için](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales).

Özel kısmi düzen oluşturma hakkında birkaç örnek aşağıda verilmiştir.

* Yalnızca bir dil için tüm iş yüklerini ve bileşenleri indirmek için şu işlemi çalıştırın:

    ```shell
    vs_enterprise.exe --layout C:\VSLayout --lang en-US
    ```

* Birden çok dilin tüm iş yüklerini ve bileşenlerini indirmek için şu işlemi çalıştırın:

    ```shell
    vs_enterprise.exe --layout C:\VSLayout --lang en-US de-DE ja-JP
    ```

* Tüm diller için bir iş yükü indirmek için şu işlemi çalıştırın:

    ```shell
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --includeRecommended
    ```

* İki iş yükünü ve üç dil için isteğe bağlı bir bileşeni indirmek için şu işlemi çalıştırın:

    ```shell
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended --lang en-US de-DE ja-JP
    ```

* İki iş yükünü ve önerilen tüm bileşenlerini indirmek için:

    ```shell
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended
    ```

* İki iş yükünü ve önerilen ve isteğe bağlı bileşenlerinin hepsini indirmek için şu işlemi çalıştırın:

    ```shell
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeOptional
    ```

### <a name="save-your-layout-options"></a>Düzen seçeneklerinizi kaydetme

Bir düzen komutunu çalıştırarak belirttiğiniz seçenekler kaydedilir (iş yükleri ve diller gibi). Sonraki düzen komutları önceki seçeneklerin hepsini içerir.  Yalnızca İngilizce için tek bir iş yüküne sahip bir düzen örneği:

```shell
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
```

Bu düzeni daha yeni bir sürüme güncelleştirmek istediğinizde, ek komut satırı parametresi belirtmenize gerek yok. Önceki ayarlar bu düzen klasöründeki sonraki düzen komutları tarafından kaydedilir ve kullanılır.  Aşağıdaki komut, mevcut kısmi düzeni güncelleştirecek.

```shell
vs_enterprise.exe --layout c:\VSLayout
```

Ek bir iş yükü eklemek istediğiniz zaman, bunun nasıl yapl bir örneği burada ve ardından ve burada açık bir şekilde açık ve açık bir şekilde açık ve açık bir şekilde açık bir şekilde ifade etmek gerekir. Bu durumda, Azure iş yükünü ve yerelleştirilmiş bir dili ekleyiz.  Artık hem Yönetilen Masaüstü hem de Azure bu düzende yer almaktadır.  İngilizce ve Almanca dil kaynakları tüm bu iş yüklerine dahildir. Düzen, kullanılabilir en son sürüme güncelleştirilir.

```shell
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
```

Var olan bir düzeni tam düzende güncelleştirmek için aşağıdaki örnekte gösterildiği gibi --all seçeneğini kullanın.

```shell
vs_enterprise.exe --layout c:\VSLayout --all
```

## <a name="deploy-from-a-network-installation"></a>Ağ yüklemeden dağıtma

Yöneticiler bir yükleme Visual Studio parçası olarak istemci iş istasyonlarına sanal ağ dağıtarak iş istasyonlarına dağıtın. Ya da yönetici haklarına sahip kullanıcılar doğrudan paylaşımdan kurulumu çalıştırarak makinelerine Visual Studio yükleyebilir.

* Kullanıcılar aşağıdaki komutu çalıştırarak yükleyebilir: <br>

    ```shell
    \\server\products\VS\vs_enterprise.exe
    ```

* Yöneticiler aşağıdaki komutu çalıştırarak katılımsız modda yükleyebilir:

    ```shell
    \\server\products\VS\vs_enterprise.exe --quiet --wait --norestart
    ```

> [!IMPORTANT]
> Bir hatayı önlemek için tam düzen yol 80 karakterden az olduğundan emin olun.

> [!TIP]
> Bir toplu iş dosyasının parçası olarak yürütülürken seçeneği, bir çıkış kodu döndürene kadar yükleme tamamlandıktan sonra sürecin `--wait` `vs_enterprise.exe` beklemesini sağlar.
>
> Bu, kuruluş yöneticisinin tamamlanmış bir yüklemede daha fazla eylem gerçekleştirmek (örneğin, başarılı bir yükleme için bir ürün anahtarı [uygulamak)](automatically-apply-product-keys-when-deploying-visual-studio.md)istediği ancak yüklemenin bu yüklemeden dönüş kodunu işlemek için yüklemenin tamamlandıktan sonra bitip beklemesi gereken durumlarda kullanışlıdır.
>
> kullanmazsanız, yükleme tamamlandıktan önce işlem çıkar ve yükleme işleminin durumunu temsil etmeyen yanlış bir `--wait` `vs_enterprise.exe` çıkış kodu döndürür.
>

::: moniker range=">=vs-2019"
> [!IMPORTANT]
> Çevrimdışı yüklemeler için "Aşağıdaki parametrelerle eşleşen bir ürün bulunamadı" hata iletisini alırsanız, 16.3.5 veya sonraki bir sürüme sahip anahtarı kullanırkenn `--noweb` emin olun.
>
::: moniker-end

Bir düzenden yüklemeniz, yüklü olan içerik düzenden edinilen içeriktir. Ancak, düzende olmayan bir bileşeni seçersiniz, bu bileşen internetten elde edersiniz.  Bu ayarın Visual Studio içeriği indirmesini engellemek için seçeneğini `--noWeb` kullanın. `--noWeb`kullanılırsa ve düzende yüklenmek üzere seçilen herhangi bir içerik eksikse kurulum başarısız olur.

> [!TIP]
> İnternet'e bağlı olmayan bir bilgisayara çevrimdışı bir kaynaktan yüklemek istiyorsanız, hem hem de `--noWeb` seçeneklerini `--noUpdateInstaller` belirtin. Önceki, güncelleştirilmiş iş yüklerinin, bileşenlerin ve diğer bileşenlerin indir indirebilirsiniz. İkincisi, yükleyicinin web'den kendi kendine güncelleştirmesini önler.

> [!IMPORTANT]
> seçeneği, `--noWeb` İnternet'e Visual Studio bir bilgisayarda kurulumun güncelleştirmeleri denetlemesi için durdurmaz. Daha fazla bilgi için Ağ [tabanlı dağıtımlarda güncelleştirmeleri denetleme Visual Studio bakın.](controlling-updates-to-visual-studio-deployments.md)

### <a name="error-codes"></a>Hata kodları

parametresini `--wait` kullandıysanız, işlem sonucuna bağlı olarak ortam `%ERRORLEVEL%` değişkeni aşağıdaki değerlerden biri olarak ayarlanır:

[!INCLUDE[install-error-codes-md](includes/install-error-codes-md.md)]

## <a name="update-a-network-install-layout"></a>Ağ yükleme düzenini güncelleştirme

Ürün güncelleştirmeleri kullanılabilir hale geldikça, ağ [yükleme düzenini güncelleştirilmiş paketleri dahil etmek](update-a-network-installation-of-visual-studio.md) için güncelleştirmek istiyor olabilir.

## <a name="how-to-create-a-layout-for-a-previous-visual-studio-release"></a>Önceki bir sürüm için düzen Visual Studio oluşturma

İlk olarak, "latest", "current", "evergreen" ve "tip" sözcükleriyle nitelendirilen ve temelde "sabit sürüm" anlamına gelen iki tür Visual Studio önyükleyicisi olduğunu anlamalısınız. Her iki önyükleyici dosya türü de tam olarak aynı adla aynıdır ve türü ayırt etmek için en iyi yol, nereden bu türe sahip olduğunuz yere dikkat etmektir. [Visual Studio](https://visualstudio.microsoft.com/downloads) indirmeleri sayfasında bulunan Visual Studio önyükleyicileri her zaman yeşil Visual Studio önyükleyici olarak kabul edilir ve önyükleyici çalıştırıldıklarında kanalda mevcut olan en son sürümü her zaman yüklenir (veya güncelleştirmesi). [Visual Studio Visual Studio 2019 Sürümler Visual Studio 2022](/visualstudio/releases/2019/history) [](/visualstudio/releases/2022/history) Sürümler sayfasında bulunan veya Microsoft Update Kataloğu'daki yönetici güncelleştirmesinde eklenmiş olan önyükleyiciler ürünün belirli bir sabit sürümünü yükleyin.

Bu nedenle, bugün hiç yeşil Visual Studio önyükleyici indirip bundan altı ay sonra çalıştırırsanız, önyükleyici çalıştırıldıklarında geçerli olan Visual Studio sürümü yüklenir. Her zaman en son bitleri yüklemek ve güncel tutmak için tasarlanmıştır.

Sabit bağlantı önyükleyicisini indirirseniz veya Microsoft Kataloğu'dan indirdiğiniz bir yönetici güncelleştirmesi çalıştırırsanız, ne zaman çalıştır olursa olsun her zaman ürünün belirli bir sürümünü yüklenir.

Son olarak, bu önyükleyicilerden herhangi birini kullanarak bir ağ düzeni oluşturabilirsiniz ve düzende oluşturulacak sürüm kullandığınız önyükleyiciye bağlıdır, örneğin sabit bir sürüm veya geçerli olur. Daha sonra ağ düzenini daha sonra herhangi bir önyükleyici kullanarak güncelleştirebilirsiniz veya Daha Sonra Katalog'dan yönetici güncelleştirme Microsoft Update kullanabilirsiniz. Düzeni nasıl güncelleştirmiş olursanız olun, sonuçta elde edilen güncelleştirilmiş düzen ürünün belirli bir sürümünü içeren bir paket önbelleği olur ve ardından sabit bir bağlantı önyükleyicisi gibi davranır. Bu nedenle, istemci düzenden her yüklense, istemci düzende mevcut olan belirli Visual Studio sürümünü (daha yeni bir sürüm çevrimiçi olsa bile) yükleyebilir.

### <a name="how-to-get-support-for-your-offline-installer"></a>Çevrimdışı yükleyiciniz için destek nasıl elde edebilirsiniz?

Çevrimdışı yükleme işlemiyle ilgili bir sorun yaşamanız gerekir. Bize söylemenin en iyi yolu Sorun Bildir [aracını kullanmaktır.](../ide/how-to-report-a-problem-with-visual-studio.md) Bu aracı kullanarak sorunu tanılamamıza ve düzeltmeye yardımcı olmak için ihtiyacımız olan telemetri ve günlükleri bize gönderebilirsiniz.

Ayrıca yüklemeyle ilgili [**sorunlar için bir**](https://visualstudio.microsoft.com/vs/support/#talktous) yükleme sohbeti (yalnızca İngilizce) destek seçeneği sunuyoruz.

Başka destek seçenekleri de mevcuttur. Liste için Geri Bildirim [sayfamıza](../ide/feedback-options.md) bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
- [Visual Studio’nun ağ tabanlı yüklemesini güncelleştirme](update-a-network-installation-of-visual-studio.md)
- [Ağ ile ilgili sorunları, Visual Studio'i yükleme veya kullanma sırasında Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md)
- [Ağ tabanlı dağıtımlarda güncelleştirmeleri Visual Studio denetleme](controlling-updates-to-visual-studio-deployments.md)
- [Visual Studio yaşam döngüsü ve bakım](/visualstudio/releases/2019/servicing/)
- [Bakım temeli sırasında Visual Studio’yu güncelleştirme](update-servicing-baseline.md)
- [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
- [Visual Studio iş yükü ve bileşen kimlikleri](workload-and-component-ids.md)
- [Çevrimdışı yükleme için Visual Studio sertifikaları yükleme](install-certificates-for-visual-studio-offline.md)
