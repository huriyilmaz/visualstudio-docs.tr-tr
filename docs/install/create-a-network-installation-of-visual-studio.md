---
title: Bir ağ tabanlı yüklemesini oluşturma
description: Visual Studio içinde bir kuruluş dağıtımı için bir ağ yükleme noktasını oluşturmayı öğrenin.
ms.date: 10/29/2019
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
ms.openlocfilehash: bc31b6c5286e5d02d5fd6d4da441a001f190de90
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78410097"
---
# <a name="create-a-network-installation-of-visual-studio"></a>Visual Studio 'nun ağ yüklemesi oluşturma

Genellikle, bir kuruluş Yöneticisi istemci iş istasyonlarına dağıtmak için bir ağ yüklemesi noktası oluşturur. Visual Studio 'Yu, tüm ürün güncelleştirmeleriyle birlikte tek bir klasöre kadar, ilk yükleme için dosyaları önbelleğe alma olanağı sağlayacak şekilde tasarladık. (Bu işleme de _düzen oluşturma_adı verilir.)

Böylece istemci iş istasyonları, aynı ağ konumunu en son hizmet güncelleştirmesi güncelleştirilmemiş olmasanız bile yükleme yönetmek için kullanabilirsiniz biz bunu yaptık.

 > [!NOTE]
 > (Örneğin, Visual Studio Professional ve Visual Studio Enterprise), kuruluşunuzda kullanımda Visual Studio'nun birden çok sürüm varsa, bir her sürümü için ayrı bir ağ yükleme paylaşımı oluşturmanız gerekir.

## <a name="download-the-visual-studio-bootstrapper"></a>Visual Studio önyükleyicisini yükleyin

İstediğiniz Visual Studio sürümü için bir önyükleyici dosyası indirin. **Kaydet**' i seçtiğinizden emin olun ve sonra **klasörü aç**' ı seçin.

::: moniker range="vs-2017"

Visual Studio 2017 için bir önyükleyici almak üzere, bunun nasıl yapılacağı hakkında ayrıntılı bilgi için [Visual Studio önceki sürümler](https://visualstudio.microsoft.com/vs/older-downloads/) indirme sayfasına bakın.

Kurulum çalıştırılabiliriniz&mdash;veya daha belirli bir şekilde,&mdash;önyükleyici dosyası eşleşmelidir veya aşağıdakilerden birine benzer olmalıdır.

| Sürüm | Kısaltın |
|-------------|-----------------------|
|Visual Studio Enterprise | **vs_enterprise. exe** |
|Visual Studio Professional | **vs_professional. exe** |
|Visual Studio Derleme Araçları   | **vs_buildtools. exe** |

Desteklenen diğer bootstrapdenetleyicileri **vs_feedbackclient. exe**, **vs_TeamExplorer. exe**, **vs_testagent. exe**, **vs_testcontroller. exe**ve **vs_testprofessional. exe**' yi içerir.

::: moniker-end

::: moniker range="vs-2019"

Kurulum çalıştırılabilir&mdash;veya daha belirgin bir şekilde,&mdash;bir önyükleyici dosyası eşleşmelidir veya aşağıdakilerden birine benzer olmalıdır.

|Sürüm | İndir|
|-------------|-----------------------|
|Visual Studio Enterprise | [**vs_enterprise. exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
|Visual Studio Professional | [**vs_professional. exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
| Visual Studio Derleme Araçları   | [**vs_buildtools. exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019) |

Desteklenen diğer bootstrapdenetleyicileri [vs_TeamExplorer. exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/4026077127d25d33789f3882998266946608d8ada378b6ed7c8fff8c07f3dde2/vs_TeamExplorer.exe), [vs_testagent. exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/1383bf8bcda3d0e986a2e42c14114aaea8a7b085d31aa0623c9f70b2bad130e4/vs_TestAgent.exe)ve [vs_testcontroller. exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/54dcf24b76e7cd9fb8be0ac518a9dfba6daf18fe9b2aa1543411b1cda8820918/vs_TestController.exe)' yi içerir.

::: moniker-end

>[!TIP]
>Daha önce bir önyükleyici dosyası indirdiyseniz ve sürümünü doğrulamak istiyorsanız, bunun nasıl yapıldığını burada bulabilirsiniz. Windows 'ta dosya Gezgini 'ni açın, önyükleyici dosyasına sağ tıklayın, **Özellikler**' i seçin, **Ayrıntılar** sekmesini seçin ve ardından **ürün sürümü** numarasını görüntüleyin. Bu numarayı bir Visual Studio sürümüyle eşleştirmek için bkz. [Visual Studio derleme numaraları ve sürüm tarihleri](visual-studio-build-numbers-and-release-dates.md) sayfası.

## <a name="create-an-offline-installation-folder"></a>Bir çevrimdışı yükleme klasörü oluşturun

Bu adımı tamamlamak için bir internet bağlantısı olması gerekir. Tüm diller ve tüm özelliklerle çevrimdışı bir yükleme oluşturmak için aşağıdaki örneklerden birine benzer bir komut kullanın.

   > [!IMPORTANT]
   > Tamamen Visual Studio düzeni en az 35 GB disk alanı gerektirir ve indirmek biraz zaman alabilir. Yalnızca yüklemek istediğiniz bileşenleri içeren bir düzen oluşturma hakkında ayrıntılı bilgi için [ağ yerleşimini özelleştirme](#customize-the-network-layout) bölümüne bakın.
   >
   > [!TIP]
   > İndirme dizininize komutu çalıştırdığınızdan emin olun. Genellikle, bu, Windows 10 çalıştıran bir bilgisayarda `C:\Users\<username>\Downloads`.

- Visual Studio Enterprise'ı çalıştırın:

  ```vs_enterprise.exe --layout c:\VSLayout```

- Visual Studio Professional için çalıştırın:

  ```vs_professional.exe --layout c:\VSLayout```

## <a name="modify-the-responsejson-file"></a>Response.json dosyasını değiştirme

Kurulumu çalıştırdığınızda kullanılan varsayılan değerleri ayarlamak için response.json değiştirebilirsiniz.  Örneğin, otomatik olarak seçilen belirli bir iş yükü kümesini seçmek için `response.json` dosyasını yapılandırabilirsiniz. Ayrıntılar için bkz. [Visual Studio yüklemesini bir yanıt dosyasıyla otomatikleştirin](automated-installation-with-response-file.md) .

Ayrıca, Visual Studio önyükleyici ile bir yanıt. JSON dosyasıyla eşleştirmeniz sırasında hata oluşturan bir sorunla karşılaşırsanız, ne yapacaklarına ilişkin daha fazla bilgi için [Visual Studio 'yu yüklediğinizde veya kullanırken ağla ilgili hatalarda sorun giderme](troubleshooting-network-related-errors-in-visual-studio.md#error-failed-to-parse-id-from-parent-process) sayfasında "üst işlemden ID ayrıştırılamadı" bölümüne bakın.

## <a name="copy-the-layout-to-a-network-share"></a>Düzen bir ağ paylaşımına kopyalayın.

Diğer makinelerden çalıştırılabilir için bir ağ paylaşımındaki düzenini barındırın.

Aşağıdaki örnek [xcopy](/windows-server/administration/windows-commands/xcopy/)kullanır. Ayrıca, [Robocopy](/windows-server/administration/windows-commands/robocopy/)de kullanabilirsiniz.  

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
> Bir hatayı engellemek için, tam düzen yolunuz 80 karakterden az olduğundan emin olun.

## <a name="customize-the-network-layout"></a>Ağ yerleşimini özelleştirme

Ağ düzeninize özelleştirmek için kullanabileceğiniz birkaç seçenek vardır. Yalnızca belirli bir [dil yerel](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales)ayarı, [iş yükleri, bileşenler ve önerilen ya da isteğe bağlı bağımlılıklarını](workload-and-component-ids.md)içeren kısmi bir düzen oluşturabilirsiniz. Bu, istemci iş istasyonlarına yalnızca bir iş yükü alt kümesini dağıtacağınızı biliyorsanız yararlı olabilir. Düzeni özelleştirmek için tipik komut satırı parametreleri şunlardır:

* [iş yükünü veya bileşen kimliklerini](workload-and-component-ids.md)belirtmek için `--add`. <br>`--add` kullanılırsa, yalnızca `--add` ile belirtilen iş yükleri ve bileşenler indirilir.  `--add` kullanılmazsa, tüm iş yükü ve bileşenler indirilir.
* Belirtilen iş yükü kimlikleri için önerilen tüm bileşenleri dahil `--includeRecommended`
* Belirtilen iş yükü kimlikleri için tüm önerilen ve isteğe bağlı bileşenleri dahil etmek `--includeOptional`.
* [dil yerel ayarlarını](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales)belirtmek için `--lang`.

Özel bir kısmi düzen oluşturma bazı örnekleri aşağıda verilmiştir.

* Tüm iş yükleri ve bileşenler için yalnızca bir dil yüklemek için çalıştırın:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --lang en-US
    ```

* Tüm iş yüklerinin ve bileşenlerin birden çok dil için karşıdan yüklemek için şunu çalıştırın:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --lang en-US de-DE ja-JP
    ```

* Tüm diller için bir iş yükünü indirmek için şunu çalıştırın:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --includeRecommended
    ```

* İki iş yükü ve üç diller için isteğe bağlı bir bileşen yüklemek için şunu çalıştırın:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended --lang en-US de-DE ja-JP
    ```

* İki iş yükünü ve tüm önerilen bileşenlerini indirmek için:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended
    ```

* İki iş yükü ve tüm önerilen ve isteğe bağlı bileşenleri yüklemek için çalıştırın:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeOptional
    ```

::: moniker range="vs-2017"

### <a name="new-in-version-153"></a>Sürüm 15,3 ' de yeni

::: moniker-end

::: moniker range="vs-2019"

### <a name="save-your-layout-options"></a>Düzen seçeneklerinizi kaydedin

::: moniker-end

Bir düzen komutu çalıştırdığınızda, belirttiğiniz seçenekleri (iş yüklerini ve dilleri gibi) kaydedilir. Sonraki Düzen komutları tüm önceki seçenekleri içerir.  Bir iş yüküyle İngilizce için yalnızca bir düzen örneği aşağıda verilmiştir:

```cmd
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
```

Bu düzeni daha yeni bir sürüme güncelleştirmek istediğiniz zaman herhangi ek komut satırı parametrelerini belirtmeniz gerekmez. Önceki ayarları kaydedilir ve bu düzen klasördeki herhangi bir sonraki Düzen komut tarafından kullanılır.  Aşağıdaki komut, var olan kısmi düzenini güncelleştirir.

```cmd
vs_enterprise.exe --layout c:\VSLayout
```

Bunu yapmak nasıl bir örneği bir ek yükünün, burada eklemek istediğinizde. Bu durumda, Azure iş yükü ve yerelleştirilmiş dili ekleyeceğiz.  Şimdi, hem yönetilen Masaüstü hem de Azure Bu düzende dahil edilir.  Ingilizce ve Almanca için dil kaynakları tüm bu iş yükleri için eklenmiştir. Düzeni, kullanılabilir en son sürüme güncelleştirilir.

```cmd
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
```

Varolan bir düzen bir tam düzeni güncelleştirmek istiyorsanız, kullanın all seçeneği, aşağıdaki örnekte gösterildiği gibi.

```cmd
vs_enterprise.exe --layout c:\VSLayout --all
```

## <a name="deploy-from-a-network-installation"></a>Ağ yüklemesinden dağıtma

Yöneticiler, bir yükleme betiğinin bir parçası istemci iş istasyonlarında Visual Studio dağıtabilirsiniz. Veya yönetici haklarına sahip kullanıcılar, makinede Visual Studio'yu yüklemek için doğrudan paylaşımından Kurulumu çalıştırın.

* Kullanıcılar, aşağıdaki komutu çalıştırarak yükleyebilir: <br>

    ```cmd
    \\server\products\VS\vs_enterprise.exe
    ```

* Yöneticiler, aşağıdaki komutu çalıştırarak katılımsız modda yüklenebilir:

    ```cmd
    \\server\products\VS\vs_enterprise.exe --quiet --wait --norestart
    ```

> [!IMPORTANT]
> Bir hatayı engellemek için, tam düzen yolunuz 80 karakterden az olduğundan emin olun.

> [!TIP]
> Bir toplu iş dosyasının parçası olarak yürütüldüğünde `--wait` seçeneği, `vs_enterprise.exe` işleminin, yükleme tamamlanmadan önce, bir çıkış kodu döndürene kadar bekleyip beklememesini sağlar.
>
> Bu, bir Kurumsal Yönetici tamamlanmış bir yüklemede daha fazla eylem gerçekleştirmek istiyorsa (örneğin, [başarılı bir yüklemeye bir ürün anahtarı uygulamak](automatically-apply-product-keys-when-deploying-visual-studio.md)için), ancak yükleme işleminin bu yüklemeden dönüş kodunu işlemesini beklemesi gereken durumlarda yararlıdır.
>
> `--wait`kullanmıyorsanız, yükleme tamamlanmadan önce `vs_enterprise.exe` işlemi çıkar ve yükleme işleminin durumunu temsil etmeyen yanlış bir çıkış kodu döndürür.
>

::: moniker range="vs-2019"
> [!IMPORTANT]
> Çevrimdışı yüklemeler için, "aşağıdaki parametrelerle eşleşen bir ürün bulunamıyor" adlı bir hata mesajı alırsanız, 16.3.5 veya sonraki bir sürümüyle `--noweb` anahtarını kullandığınızdan emin olun.
>
::: moniker-end

Bir düzenden yükleme sırasında düzeninde yüklü içeriği alınır. Ancak, düzende olmayan bir bileşeni seçerseniz, internet 'ten elde edilir.  Visual Studio kurulumunun düzeninizde eksik olan içeriği indirmasını engellemek istiyorsanız `--noWeb` seçeneğini kullanın. `--noWeb` kullanılıyorsa ve mizanpajda yüklenmek üzere seçilen içerik eksikse, kurulum başarısız olur.

> [!IMPORTANT]
> `--noWeb` seçeneği, Visual Studio kurulumunun güncelleştirmeleri denetlemesini durdurmaz. Daha fazla bilgi için bkz. [ağ tabanlı Visual Studio dağıtımlarının güncelleştirmelerini denetleme](controlling-updates-to-visual-studio-deployments.md) sayfası.

### <a name="error-codes"></a>Hata kodları

`--wait` parametresini kullandıysanız, işlem sonucuna bağlı olarak, `%ERRORLEVEL%` ortam değişkeni aşağıdaki değerlerden birine ayarlanır:

[!INCLUDE[install-error-codes-md](includes/install-error-codes-md.md)]

## <a name="update-a-network-install-layout"></a>Ağ yüklemesi yerleşimini güncelleştirme

Ürün güncelleştirmeleri kullanılabilir hale geldiğinde, güncelleştirilmiş paketleri eklemek için [ağ yüklemesi mizanpajını güncelleştirmek](update-a-network-installation-of-visual-studio.md) isteyebilirsiniz.

## <a name="how-to-create-a-layout-for-a-previous-visual-studio-release"></a>Önceki bir Visual Studio sürümü için düzen oluşturma

::: moniker range="vs-2017"

> [!NOTE]
> [VisualStudio.Microsoft.com](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ' de kullanılabilir olan Visual Studio Bootstrap, her çalıştırıldığında kullanılabilir olan en son Visual Studio sürümünü indirip yükler.
>
> Bu nedenle, bugün bir Visual Studio *önyükleyici* indirir ve şu anda altı ay çalıştırırsanız, önyükleyici çalıştırdığınız zaman geçerli olan Visual Studio sürümünü yükler.
>
> Ancak, bir *Düzen* oluşturup buradan yüklüyorsanız, düzen mizanpajda mevcut olan Visual Studio 'nun belirli sürümünü yükler. Yeni bir sürüme çevrimiçi mevcut olabilecek olsa da, düzeni Visual Studio'nun sürümü alın.

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> [VisualStudio.Microsoft.com](https://visualstudio.microsoft.com/downloads) ' de kullanılabilir olan Visual Studio Bootstrap, her çalıştırıldığında kullanılabilir olan en son Visual Studio sürümünü indirip yükler.
>
> Bu nedenle, bugün bir Visual Studio *önyükleyici* indirir ve şu anda altı ay çalıştırırsanız, önyükleyici çalıştırdığınız zaman geçerli olan Visual Studio sürümünü yükler.
>
> Ancak, bir *Düzen* oluşturup buradan yüklüyorsanız, düzen mizanpajda mevcut olan Visual Studio 'nun belirli sürümünü yükler. Yeni bir sürüme çevrimiçi mevcut olabilecek olsa da, düzeni Visual Studio'nun sürümü alın.

::: moniker-end

Visual Studio 'nun daha eski bir sürümü için bir düzen oluşturmanız gerekiyorsa, Visual Studio bootstrap'ın "düzeltilen" sürümlerini indirmek için [https://my.visualstudio.com](https://my.visualstudio.com) gidin.

### <a name="how-to-get-support-for-your-offline-installer"></a>Çevrimdışı yükleyicinizi için destek alma

Çevrimdışı yüklemenizle ilgili bir sorun yaşarsanız, bunu bilmek istiyoruz. Bize anlatmak için en iyi yol, [sorun bildir](../ide/how-to-report-a-problem-with-visual-studio.md) aracını kullanmaktır. Bu aracı, bize tanılayın ve sorunu çözmeye yardımcı olmak için ihtiyacımız olan günlükleri ve telemetri gönderebilir.

Ayrıca, yüklemeyle ilgili sorunlar için [**canlı sohbet**](https://visualstudio.microsoft.com/vs/support/#talktous) (yalnızca İngilizce) destek seçeneği sunuyoruz.

Diğer destek seçenekleri, çok sahibiz. Bir liste için bkz. [geri bildirim](../ide/feedback-options.md) sayfamız.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Yönetici Kılavuzu](visual-studio-administrator-guide.md)
- [Visual Studio’nun ağ tabanlı yüklemesini güncelleştirme](update-a-network-installation-of-visual-studio.md)
- [Visual Studio 'Yu yüklerken veya kullanırken ağla ilgili hatalarda sorun giderme](troubleshooting-network-related-errors-in-visual-studio.md)
- [Ağ tabanlı Visual Studio dağıtımlarında güncelleştirmeleri denetleme](controlling-updates-to-visual-studio-deployments.md)
- [Visual Studio ürün yaşam döngüsü ve bakım](/visualstudio/releases/2019/servicing/)
- [Bakım temeliyle Visual Studio 'Yu güncelleştirme](update-servicing-baseline.md)
- [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
- [Visual Studio iş yükü ve bileşen kimlikleri](workload-and-component-ids.md)
