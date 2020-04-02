---
title: Ağ tabanlı yükleme oluşturma
description: Visual Studio'yı kuruluş içinde dağıtmak için ağ yükleme noktası oluşturmayı öğrenin.
ms.date: 03/27/2020
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 4CABFD20-962E-482C-8A76-E4012052F701
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: ea7efd82aa25844e8eb33745aa53d44be1ed14f6
ms.sourcegitcommit: 054815dc9821c3ea219ae6f31ebd9cd2dc8f6af5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80544070"
---
# <a name="create-a-network-installation-of-visual-studio"></a>Visual Studio'nun ağ yüklemesini oluşturma

Genellikle, bir kurumsal yönetici istemci iş istasyonlarına dağıtmak için bir ağ yükleme noktası oluşturur. Visual Studio'yu, tüm ürün güncelleştirmeleriyle birlikte ilk yükleme için dosyaları tek bir klasöre önbelleğe almanızı sağlayacak şekilde tasarladık. (Bu işlem, bir _düzen oluşturma_olarak da adlandırılır.)

Bunu, istemci iş istasyonlarının yüklemelerini yönetmek için en son servis güncelleştirmesine henüz güncelleştirilmeseler bile aynı ağ konumunu kullanabilmeleri için yaptık.

 > [!NOTE]
 > İşletmenizde kullanılan Visual Studio'nun birden fazla sürümü varsa (örneğin, hem Visual Studio Professional hem de Visual Studio Enterprise), her sürüm için ayrı bir ağ yükleme paylaşımı oluşturmanız gerekir.

## <a name="download-the-visual-studio-bootstrapper"></a>Karşıdan yükleme Visual Studio bootstrapper

İstediğinbir bootstrapper dosyasını indirmek istediğiniz Visual Studio sürümü için. **Kaydet'i**ve ardından **Klasörü Aç'ı**seçtiğinizden emin olun.

::: moniker range="vs-2017"

Visual Studio 2017 için bir bootstrapper almak için, nasıl yapılacağını hakkında ayrıntılı bilgi için [Visual Studio önceki sürümleri](https://visualstudio.microsoft.com/vs/older-downloads/) indirme sayfasına bakın.

Kurulumunuzun&mdash;yürütülebilir veya daha spesifik olması&mdash;için, bootstrapper dosyası aşağıdakilerden biriyle eşleşmeli veya benzer olmalıdır.

| Sürüm | Dosyaadı |
|-------------|-----------------------|
|Visual Studio Enterprise | **vs_enterprise.exe** |
|Visual Studio Professional | **vs_professional.exe** |
|Visual Studio Derleme Araçları   | **vs_buildtools.exe** |

Diğer desteklenen bootstrappers **vs_feedbackclient.exe**dahil , **vs_teamexplorer.exe**, **vs_testagent.exe**, **vs_testcontroller.exe**, ve **vs_testprofessional.exe**.

::: moniker-end

::: moniker range="vs-2019"

Kurulumunuzun&mdash;yürütülebilir veya daha spesifik olması&mdash;için, bir bootstrapper dosyası aşağıdakilerden biriyle eşleşmeli veya benzer olmalıdır.

|Sürüm | İndirme|
|-------------|-----------------------|
|Visual Studio Enterprise | [**vs_enterprise.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
|Visual Studio Professional | [**vs_professional.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
| Visual Studio Derleme Araçları   | [**vs_buildtools.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019) |

Diğer desteklenen bootstrappers [vs_teamexplorer.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/4026077127d25d33789f3882998266946608d8ada378b6ed7c8fff8c07f3dde2/vs_TeamExplorer.exe), [vs_testagent.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/1383bf8bcda3d0e986a2e42c14114aaea8a7b085d31aa0623c9f70b2bad130e4/vs_TestAgent.exe), ve [vs_testcontroller.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/54dcf24b76e7cd9fb8be0ac518a9dfba6daf18fe9b2aa1543411b1cda8820918/vs_TestController.exe)içerir.

::: moniker-end

>[!TIP]
>Daha önce bir bootstrapper dosyası indirdiyseniz ve sürümünü doğrulamak istiyorsanız, şu şekilde. Windows'da Dosya Gezgini'ni açın, bootstrapper dosyasına sağ tıklayın, **Özellikler'i**seçin, **Ayrıntılar** sekmesini seçin ve ardından **Ürün sürüm** numarasını görüntüleyin. Bu sayıyı Visual Studio'nun bir sürümüyle eşleştirmek için [Visual Studio'nun sayı ve çıkış tarihleri](visual-studio-build-numbers-and-release-dates.md) sayfasına bakın.

## <a name="create-an-offline-installation-folder"></a>Çevrimdışı yükleme klasörü oluşturma

Bu adımı tamamlamak için bir internet bağlantınız olmalıdır. Tüm dillerve tüm özellikleri içeren çevrimdışı yükleme oluşturmak için, aşağıdaki örneklerden birine benzer bir komut kullanın.

   > [!IMPORTANT]
   > Tam bir Visual Studio düzeni en az 35 GB disk alanı gerektirir ve karşıdan yüklemesi biraz zaman alabilir. Yalnızca yüklemek istediğiniz bileşenlerle bir düzen oluşturma hakkında ayrıntılar için [ağ düzenini özelleştir](#customize-the-network-layout) bölümüne bakın.
   >
   > [!TIP]
   > İndir dizinindeki komutu çalıştırdığınızdan emin olun. Genellikle, Windows 10 çalıştıran bir bilgisayarda. `C:\Users\<username>\Downloads`

- Visual Studio Enterprise için çalıştırın:

  ```vs_enterprise.exe --layout c:\VSLayout```

- Visual Studio Professional için çalıştırın:

  ```vs_professional.exe --layout c:\VSLayout```

## <a name="modify-the-responsejson-file"></a>yanıt.json dosyasını değiştirme

Kurulum çalıştırıldığında kullanılan varsayılan değerleri ayarlamak için yanıt.json'u değiştirebilirsiniz.  Örneğin, dosyayı `response.json` otomatik olarak seçilen belirli bir iş yükü kümesini seçmek üzere yapılandırabilirsiniz. Ayrıntılar için [bir yanıt dosyasıyla Visual Studio yüklemeyi otomatikleştir'e](automated-installation-with-response-file.md) bakın.

Ayrıca, Visual Studio bootstrapper'ın bir yanıt.json dosyasıyla eşleştirdiğinizde hata yapmasıyla ilgili bir sorunla karşılaşıyorsanız, Visual Studio sayfasını yüklediğinizde veya visual studio sayfasını [kullandığınızda Sorun Giderme ağıyla ilgili hataların](troubleshooting-network-related-errors-in-visual-studio.md#error-failed-to-parse-id-from-parent-process) "Ana işlemden kimliği ayrıştırmak için başarısız oldu" bölümüne bakın.

## <a name="copy-the-layout-to-a-network-share"></a>Düzeni ağ paylaşımına kopyalama

Düzeni, diğer makinelerden çalıştırılabilmek için bir ağ paylaşımında barındırın.

Aşağıdaki örnekte [xcopy](/windows-server/administration/windows-commands/xcopy/)kullanır. İsterseniz [robocopy](/windows-server/administration/windows-commands/robocopy/)de kullanabilirsiniz.  

::: moniker range="vs-2017"

Örnek:

```cmd
xcopy /e c:\VSLayout \\server\products\VS2017
```

::: moniker-end

::: moniker range="vs-2019"

```cmd
xcopy /e c:\VSLayout \\server\products\VS2019
```

::: moniker-end

> [!IMPORTANT]
> Bir hatayı önlemek için, tam düzen yolunun 80 karakterden az olduğundan emin olun.

## <a name="customize-the-network-layout"></a>Ağ düzenini özelleştirme

Ağ düzeninizi özelleştirmek için kullanabileceğiniz birkaç seçenek vardır. Yalnızca belirli bir [dil yerel ayarlar](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales)kümesi, iş [yükleri, bileşenler ve bunların önerilen veya isteğe bağlı bağımlılıklarını](workload-and-component-ids.md)içeren kısmi bir düzen oluşturabilirsiniz. Bu, istemci iş istasyonlarına yalnızca iş yüklerinin bir alt kümesini dağıtacağını biliyorsanız yararlı olabilir. Düzeni özelleştirmek için tipik komut satırı parametreleri şunlardır:

* `--add`iş [yükü veya bileşen itislerini](workload-and-component-ids.md)belirtmek için. <br>`--add` Kullanılırsa, yalnızca bu iş yükleri ve bileşenler karşıdan `--add` yüklenir.  `--add` Kullanılmazsa, tüm iş yükü ve bileşenler karşıdan yüklenir.
* `--includeRecommended`belirtilen iş yükü disleri için önerilen tüm bileşenleri içerecek şekilde
* `--includeOptional`belirtilen iş yükü titremleri için önerilen ve isteğe bağlı tüm bileşenleri dahil etmek.
* `--lang`dil [yerellerini](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales)belirtmek için.

Burada, özel bir kısmi düzen oluşturmanın birkaç örneği verilmiştir.

* Tüm iş yüklerini ve bileşenlerini yalnızca bir dil için indirmek için çalıştırın:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --lang en-US
    ```

* Birden çok dil için tüm iş yüklerini ve bileşenleri indirmek için çalıştırın:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --lang en-US de-DE ja-JP
    ```

* Tüm diller için bir iş yükü indirmek için çalıştırın:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --includeRecommended
    ```

* Üç dil için iki iş yükü ve bir isteğe bağlı bileşen indirmek için çalıştırın:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended --lang en-US de-DE ja-JP
    ```

* İki iş yükünü ve önerilen tüm bileşenlerini indirmek için:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended
    ```

* İki iş yükünü ve önerilen ve isteğe bağlı tüm bileşenlerini indirmek için çalıştırın:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeOptional
    ```

::: moniker range="vs-2017"

### <a name="new-in-version-153"></a>Sürüm 15.3'te yeni

::: moniker-end

::: moniker range="vs-2019"

### <a name="save-your-layout-options"></a>Düzen seçeneklerinizi kaydetme

::: moniker-end

Bir düzen komutu çalıştırdığınızda, belirttiğiniz seçenekler kaydedilir (iş yükleri ve diller gibi). Sonraki düzen komutları önceki tüm seçenekleri içerir.  Aşağıda, yalnızca İngilizce için tek bir iş yüküne sahip bir düzen örneği verilmiştir:

```cmd
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
```

Bu düzeni daha yeni bir sürüme güncelleştirmek istediğinizde, ek komut satırı parametreleri belirtmeniz gerekmez. Önceki ayarlar kaydedilir ve bu düzen klasöründeki sonraki düzen komutları tarafından kullanılır.  Aşağıdaki komut varolan kısmi düzeni güncelleştirecektir.

```cmd
vs_enterprise.exe --layout c:\VSLayout
```

Ek bir iş yükü eklemek istediğinizde, bunu nasıl yapacağınız hakkında bir örnek aşağıda verilmiştir. Bu durumda, Azure iş yükünü ve yerelleştirilmiş bir dil ekleriz.  Artık hem Yönetilen Masaüstü hem de Azure bu düzene dahildir.  Tüm bu iş yükleri için İngilizce ve Almanca dil kaynakları dahildir. Düzen, kullanılabilir en son sürüme güncelleştirilir.

```cmd
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
```

Varolan bir düzeni tam düzene güncelleştirmek istiyorsanız, aşağıdaki örnekte gösterildiği gibi tüm seçeneğini kullanın.

```cmd
vs_enterprise.exe --layout c:\VSLayout --all
```

## <a name="deploy-from-a-network-installation"></a>Ağ yüklemesinden dağıtma

Yöneticiler, yükleme komut dosyasının bir parçası olarak Visual Studio'yu istemci iş istasyonlarına dağıtabilir. Veya yönetici haklarına sahip kullanıcılar, Visual Studio'yu makinelerine yüklemek için kurulumu doğrudan paylaşımdan çalıştırabilir.

* Kullanıcılar aşağıdaki komutu çalıştırarak yükleyebilirsiniz: <br>

    ```cmd
    \\server\products\VS\vs_enterprise.exe
    ```

* Yöneticiler aşağıdaki komutu çalıştırarak katılımsız bir modda yükleyebilir:

    ```cmd
    \\server\products\VS\vs_enterprise.exe --quiet --wait --norestart
    ```

> [!IMPORTANT]
> Bir hatayı önlemek için, tam düzen yolunun 80 karakterden az olduğundan emin olun.

> [!TIP]
> Toplu iş dosyasının bir parçası `--wait` olarak yürütüldüğünde, seçenek, bir çıkış kodu döndürmeden önce `vs_enterprise.exe` işlemin yükleme tamamlanana kadar beklemesini sağlar.
>
> Bu, bir kuruluş yöneticisi tamamlanmış bir yükleme üzerinde daha fazla eylem gerçekleştirmek istiyorsa (örneğin, [başarılı bir yüklemeye ürün anahtarı uygulamak](automatically-apply-product-keys-when-deploying-visual-studio.md)için) ancak yüklemenin bu yüklemeden gelen iade kodunu işlemek için tamamlanmasını beklemesi gerekir.
>
> `--wait`Kullanmazsanız, `vs_enterprise.exe` yükleme tamamlanmadan önce işlem çıkar ve yükleme işleminin durumunu temsil etmeyen yanlış bir çıkış kodu verir.
>

::: moniker range="vs-2019"
> [!IMPORTANT]
> Çevrimdışı yüklemeler için, "Aşağıdaki parametrelerle eşleşen bir ürün bulunamıyor" yazan bir hata iletisi `--noweb` alırsanız, anahtarı sürüm 16.3.5 veya sonraki sürümlerle kullandığınızdan emin olun.
>
::: moniker-end

Bir düzenden yüklediğinizde, yüklenen içerik düzenden elde edilir. Ancak, düzende olmayan bir bileşen seçerseniz, bu bileşen internetten edinici olur.  Visual Studio kurulumunun düzeninizde eksik olan içeriği indirmesini engellemek istiyorsanız, `--noWeb` seçeneği kullanın. `--noWeb` Kullanılıyorsa ve düzen de yüklenecek şekilde seçilen herhangi bir içerik eksikse, kurulum başarısız olur.

> [!TIP]
> Internet'e bağlı olmayan bir bilgisayara çevrimdışı bir kaynaktan yüklemek `--noWeb` `--noUpdateInstaller` istiyorsanız, hem seçenekleri hem de seçenekleri belirtin. Eski güncelleştirilmiş iş yükleri, bileşenleri ve benzeri indirme engeller. İkincisi, yükleyicinin web'den kendi kendini güncellemesini engeller.

> [!IMPORTANT]
> Bu `--noWeb` seçenek, Internet'e bağlı bir bilgisayardaki Visual Studio kurulumunun güncelleştirmeleri denetlemesini engellemez. Daha fazla bilgi için [ağ tabanlı Visual Studio dağıtımları](controlling-updates-to-visual-studio-deployments.md) sayfasında denetim güncelleştirmelerine bakın.

### <a name="error-codes"></a>Hata kodları

Parametreyi `--wait` kullandıysanız, işlemin sonucuna bağlı olarak `%ERRORLEVEL%` ortam değişkeni aşağıdaki değerlerden birine ayarlanır:

[!INCLUDE[install-error-codes-md](includes/install-error-codes-md.md)]

## <a name="update-a-network-install-layout"></a>Ağ yükleme düzenini güncelleştirme

Ürün güncelleştirmeleri kullanılabilir hale geldikçe, güncelleştirilmiş paketleri dahil etmek için [ağ yükleme düzenini güncelleştirmek](update-a-network-installation-of-visual-studio.md) isteyebilirsiniz.

## <a name="how-to-create-a-layout-for-a-previous-visual-studio-release"></a>Önceki Visual Studio sürümü için düzen oluşturma

::: moniker range="vs-2017"

> [!NOTE]
> [visualstudio.microsoft.com'da](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) bulunan Visual Studio bootstrappers, çalıştırıldıklarında kullanılabilen en son Visual Studio yayınını indirip yükler.
>
> Yani, bugün bir Visual Studio *bootstrapper* indirmek ve bundan altı ay sonra çalıştırmak, bootstrapper çalıştırmak anda geçerli Olan Visual Studio sürümü yükler.
>
> Ancak, bir *düzen* oluşturur ve ondan yüklerseniz, düzen, Visual Studio'nun düzende bulunan belirli sürümünü yükler. Çevrimiçi olarak daha yeni bir sürüm olsa da, Visual Studio'nun düzendeki sürümünü alırsınız.

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> [visualstudio.microsoft.com'da](https://visualstudio.microsoft.com/downloads) bulunan Visual Studio bootstrappers, çalıştırıldıklarında kullanılabilen en son Visual Studio yayınını indirip yükler.
>
> Yani, bugün bir Visual Studio *bootstrapper* indirmek ve bundan altı ay sonra çalıştırmak, bootstrapper çalıştırmak anda geçerli Olan Visual Studio sürümü yükler.
>
> Ancak, bir *düzen* oluşturur ve ondan yüklerseniz, düzen, Visual Studio'nun düzende bulunan belirli sürümünü yükler. Çevrimiçi olarak daha yeni bir sürüm olsa da, Visual Studio'nun düzendeki sürümünü alırsınız.

::: moniker-end

Visual Studio'nun eski bir sürümü için bir düzen [https://my.visualstudio.com](https://my.visualstudio.com) oluşturmanız gerekiyorsa, Visual Studio bootstrappers'ın "sabit" sürümlerini indirmeye gidin.

### <a name="how-to-get-support-for-your-offline-installer"></a>Çevrimdışı yükleyiciniz için destek alma

Çevrimdışı yüklemenizde bir sorun la karşılaşırsanız, bu konuda bir sorun yaşamak isteriz. Bize bildirmenin en iyi yolu [Sorun Bildir](../ide/how-to-report-a-problem-with-visual-studio.md) aracını kullanmaktır. Bu aracı kullandığınızda, sorunu tanılamamıza ve düzeltmemize yardımcı olmak için ihtiyacımız olan telemetri ve günlükleri bize gönderebilirsiniz.

Ayrıca, yüklemeyle ilgili sorunlar için [**yükleme sohbeti**](https://visualstudio.microsoft.com/vs/support/#talktous) (yalnızca İngilizce) destek seçeneği de sunuyoruz.

Başka destek seçeneklerimiz de mevcuttur. Bir liste için [Geri Bildirim](../ide/feedback-options.md) sayfamıza bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
- [Visual Studio’nun ağ tabanlı yüklemesini güncelleştirme](update-a-network-installation-of-visual-studio.md)
- [Visual Studio'yu yüklediğinizde veya kullandığınızda ağla ilgili hataları giderme](troubleshooting-network-related-errors-in-visual-studio.md)
- [Ağ tabanlı Visual Studio dağıtımlarında denetim güncelleştirmeleri](controlling-updates-to-visual-studio-deployments.md)
- [Visual Studio ürün yaşam döngüsü ve servis](/visualstudio/releases/2019/servicing/)
- [Bakım temeli sırasında Visual Studio’yu güncelleştirme](update-servicing-baseline.md)
- [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
- [Visual Studio iş yükü ve bileşen kimlikleri](workload-and-component-ids.md)
- [Visual Studio çevrimdışı yüklemesi için gerekli sertifikaları yükleme](/install-certificates-for-visual-studio-offline.md)