---
title: Ağ tabanlı yükleme oluşturma
description: Visual Studio 'Yu bir kuruluş içinde dağıtmak için bir ağ yüklemesi noktası oluşturmayı öğrenin.
ms.date: 08/27/2020
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
ms.openlocfilehash: 0b48f35a9467e1f69a0055ac0859083078f9cf3b
ms.sourcegitcommit: f4d734329c82f2c8005b36af4b2b5516d90e6c63
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88992361"
---
# <a name="create-a-network-installation-of-visual-studio"></a>Visual Studio 'nun ağ yüklemesi oluşturma

Genellikle, bir kuruluş Yöneticisi istemci iş istasyonlarına dağıtmak için bir ağ yüklemesi noktası oluşturur. Visual Studio 'Yu, tüm ürün güncelleştirmeleriyle birlikte tek bir klasöre kadar, ilk yükleme için dosyaları önbelleğe alma olanağı sağlayacak şekilde tasarladık. (Bu işleme de _düzen oluşturma_adı verilir.)

İstemci iş istasyonlarının, henüz en son bakım güncelleştirmesine güncelleştirilmemiş olsalar bile, yüklemelerini yönetmek için aynı ağ konumunu kullanabilmesi için bunu yaptık.

 > [!NOTE]
 > Kuruluşunuzda kullanılan Visual Studio 'nun birden çok sürümü varsa (örneğin, hem Visual Studio Professional hem de Visual Studio Enterprise), her sürüm için ayrı bir ağ yüklemesi oluşturmanız gerekir.

## <a name="download-the-visual-studio-bootstrapper"></a>Visual Studio önyükleyici 'yi indirin

İstediğiniz Visual Studio sürümü için bir önyükleyici dosyası indirin. **Kaydet**' i seçtiğinizden emin olun ve sonra **klasörü aç**' ı seçin.

::: moniker range="vs-2017"

Visual Studio 2017 için bir önyükleyici almak üzere, bunun nasıl yapılacağı hakkında ayrıntılı bilgi için [Visual Studio önceki sürümler](https://visualstudio.microsoft.com/vs/older-downloads/) indirme sayfasına bakın.

Kurulum çalıştırılabiliriniz &mdash; veya daha belirgin olması için, önyükleyici dosyası &mdash; eşleşmelidir veya aşağıdakilerden birine benzer olmalıdır.

| Sürüm | Kısaltın |
|-------------|-----------------------|
|Visual Studio Enterprise | **vs_enterprise.exe** |
|Visual Studio Professional | **vs_professional.exe** |
|Visual Studio Derleme Araçları   | **vs_buildtools.exe** |

Desteklenen diğer bootstrapdenetleyicileri **vs_feedbackclient.exe**, **vs_teamexplorer.exe**, **vs_testagent.exe**, **vs_testcontroller.exe**ve **vs_testprofessional.exe**içerir.

::: moniker-end

::: moniker range="vs-2019"

Kurulum çalıştırılabiliriniz &mdash; veya daha belirgin olması için bir önyükleyici dosyası &mdash; eşleşmelidir veya aşağıdakilerden birine benzer olmalıdır.

|Sürüm | İndir|
|-------------|-----------------------|
|Visual Studio Enterprise | [**vs_enterprise.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
|Visual Studio Professional | [**vs_professional.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
| Visual Studio Derleme Araçları   | [**vs_buildtools.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019) |

Desteklenen diğer bootstrapdenetleyicileri [vs_teamexplorer.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/4026077127d25d33789f3882998266946608d8ada378b6ed7c8fff8c07f3dde2/vs_TeamExplorer.exe), [vs_testagent.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/1383bf8bcda3d0e986a2e42c14114aaea8a7b085d31aa0623c9f70b2bad130e4/vs_TestAgent.exe)ve [vs_testcontroller.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/54dcf24b76e7cd9fb8be0ac518a9dfba6daf18fe9b2aa1543411b1cda8820918/vs_TestController.exe)içerir.

::: moniker-end

>[!TIP]
>Daha önce bir önyükleyici dosyası indirdiyseniz ve sürümünü doğrulamak istiyorsanız, bunun nasıl yapıldığını burada bulabilirsiniz. Windows 'ta dosya Gezgini 'ni açın, önyükleyici dosyasına sağ tıklayın, **Özellikler**' i seçin, **Ayrıntılar** sekmesini seçin ve ardından **ürün sürümü** numarasını görüntüleyin. Bu numarayı bir Visual Studio sürümüyle eşleştirmek için bkz. [Visual Studio derleme numaraları ve sürüm tarihleri](visual-studio-build-numbers-and-release-dates.md) sayfası.

## <a name="create-an-offline-installation-folder"></a>Çevrimdışı yükleme klasörü oluşturma

Bu adımı tamamlayabilmeniz için bir internet bağlantınızın olması gerekir. Tüm diller ve tüm özelliklerle çevrimdışı bir yükleme oluşturmak için aşağıdaki örneklerden birine benzer bir komut kullanın.

   > [!IMPORTANT]
   > Tek bir dil yerel ayarı için kapsamlı bir düzen, Visual Studio Community için 35 GB disk alanı ve Visual Studio Enterprise için 42 GB gerektirir. Ek [dil yerel ayarları](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales) her bırı için GB olmak üzere gereklidir. Daha fazla bilgi için [ağ yerleşimini özelleştirme](#customize-the-network-layout) bölümüne bakın.
   >
   > [!TIP]
   > Indirme dizininizden komutunu çalıştırdığınızdan emin olun. Genellikle, `C:\Users\<username>\Downloads` Windows 10 çalıştıran bir bilgisayarda.

- Visual Studio Enterprise için şunu çalıştırın:

  ```vs_enterprise.exe --layout c:\VSLayout```

- Visual Studio Professional için şunu çalıştırın:

  ```vs_professional.exe --layout c:\VSLayout```

## <a name="modify-the-responsejson-file"></a>Dosyadaki response.jsDeğiştir

Kurulum çalıştırıldığında kullanılan varsayılan değerleri ayarlamak için üzerinde response.jsdeğiştirebilirsiniz.  Örneğin, `response.json` otomatik olarak seçilen belirli bir iş yükü kümesini seçmek için dosyayı yapılandırabilirsiniz. Ayrıntılar için bkz. [Visual Studio yüklemesini bir yanıt dosyasıyla otomatikleştirin](automated-installation-with-response-file.md) .

response.jsAyrıca, Visual Studio önyükleyici ile bir hata oluşturan bir sorunla karşılaşırsanız, ne yapacaklarına ilişkin daha fazla bilgi için [Visual Studio 'yu yüklerken veya kullanırken ağla ilgili hatalarda sorun giderme](troubleshooting-network-related-errors-in-visual-studio.md#error-failed-to-parse-id-from-parent-process) konusunun "üst işlemden kimliği ayrıştırılamadı" bölümüne bakın.

## <a name="copy-the-layout-to-a-network-share"></a>Düzeni bir ağ paylaşımında kopyalama

Diğer makinelerden çalıştırılabilmesi için düzeni bir ağ paylaşımında barındırın.

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

Ağ düzeninizi özelleştirmek için kullanabileceğiniz çeşitli seçenekler vardır. Yalnızca belirli bir [dil yerel](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales)ayarı, [iş yükleri, bileşenler ve önerilen ya da isteğe bağlı bağımlılıklarını](workload-and-component-ids.md)içeren kısmi bir düzen oluşturabilirsiniz. Bu, istemci iş istasyonlarına yalnızca bir iş yükü alt kümesini dağıtacağınızı biliyorsanız yararlı olabilir. Düzeni özelleştirmeye yönelik tipik komut satırı parametreleri şunları içerir:

* `--add`[iş yükünü veya bileşen kimliklerini](workload-and-component-ids.md)belirtmek için. <br>Kullanılıyorsa `--add` , yalnızca ile belirtilen iş yükleri ve bileşenler `--add` indirilir.  `--add`Kullanılmıyorsa, tüm iş yükü ve bileşenler indirilir.
* `--includeRecommended` Belirtilen iş yükü kimlikleri için önerilen tüm bileşenleri dahil etmek için
* `--includeOptional` Belirtilen iş yükü kimliklerinin tüm önerilen ve isteğe bağlı bileşenlerini dahil etmek için.
* `--lang`[dil yerel ayarlarını](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales)belirtmek için.

Özel kısmi düzenin nasıl oluşturulacağı hakkında birkaç örnek aşağıda verilmiştir.

* Tüm iş yüklerini ve bileşenleri yalnızca bir dile indirmek için şunu çalıştırın:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --lang en-US
    ```

* Tüm iş yüklerini ve bileşenleri birden çok dile indirmek için şunu çalıştırın:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --lang en-US de-DE ja-JP
    ```

* Tüm diller için bir iş yükünü indirmek için şunu çalıştırın:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --includeRecommended
    ```

* Üç dil için iki iş yükü ve isteğe bağlı bir bileşen indirmek için şunu çalıştırın:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended --lang en-US de-DE ja-JP
    ```

* İki iş yükünü ve tüm önerilen bileşenlerini indirmek için:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended
    ```

* İki iş yükünü ve tüm önerilen ve isteğe bağlı bileşenlerini indirmek için şunu çalıştırın:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeOptional
    ```

::: moniker range="vs-2017"

### <a name="new-in-version-153"></a>Sürüm 15,3 ' de yeni

::: moniker-end

::: moniker range="vs-2019"

### <a name="save-your-layout-options"></a>Düzen seçeneklerinizi kaydedin

::: moniker-end

Bir düzen komutu çalıştırdığınızda belirttiğiniz seçenekler kaydedilir (iş yükleri ve diller gibi). Sonraki düzen komutları, önceki tüm seçenekleri içerir.  Yalnızca Ingilizce için bir iş yüküne sahip bir düzen örneği aşağıda verilmiştir:

```cmd
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
```

Bu düzeni daha yeni bir sürüme güncellemek istediğinizde, ek komut satırı parametreleri belirtmeniz gerekmez. Önceki ayarlar, bu düzen klasöründeki sonraki düzen komutları tarafından kaydedilir ve kullanılır.  Aşağıdaki komut, mevcut kısmi düzeni güncelleştirecek.

```cmd
vs_enterprise.exe --layout c:\VSLayout
```

Ek bir iş yükü eklemek istediğinizde, bunun nasıl yapılacağını gösteren bir örnek aşağıda verilmiştir. Bu durumda, Azure iş yükünü ve yerelleştirilmiş dili ekleyeceğiz.  Artık, hem yönetilen masaüstü hem de Azure bu düzene dahildir.  Ingilizce ve Almanca için dil kaynakları tüm bu iş yükleri için eklenmiştir. Düzen, kullanılabilir en son sürüme güncelleştirilir.

```cmd
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
```

Varolan bir düzeni tam düzene güncelleştirmek istiyorsanız, aşağıdaki örnekte gösterildiği gibi--ALL seçeneğini kullanın.

```cmd
vs_enterprise.exe --layout c:\VSLayout --all
```

## <a name="deploy-from-a-network-installation"></a>Ağ yüklemesinden dağıtma

Yöneticiler, Visual Studio 'Yu bir yükleme betiğinin parçası olarak istemci iş istasyonlarına dağıtabilir. Ya da, yönetici haklarına sahip kullanıcılar, kendi makinesine doğrudan Visual Studio 'Yu yüklemek için kurulum 'u doğrudan paylaşımdan çalıştırabilir.

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
> Bir toplu iş dosyasının parçası olarak yürütüldüğünde, bu `--wait` seçenek `vs_enterprise.exe` işlemin bir çıkış kodu vermeden önce Yüklemenin tamamlanmasını bekleyip beklememesini sağlar.
>
> Bu, bir Kurumsal Yönetici tamamlanmış bir yüklemede daha fazla eylem gerçekleştirmek istiyorsa (örneğin, [başarılı bir yüklemeye bir ürün anahtarı uygulamak](automatically-apply-product-keys-when-deploying-visual-studio.md)için), ancak yükleme işleminin bu yüklemeden dönüş kodunu işlemesini beklemesi gereken durumlarda yararlıdır.
>
> Kullanmıyorsanız `--wait` , `vs_enterprise.exe` yükleme tamamlanmadan önce işlem çıkar ve yükleme işleminin durumunu temsil etmeyen yanlış bir çıkış kodu döndürür.
>

::: moniker range="vs-2019"
> [!IMPORTANT]
> Çevrimdışı yüklemeler için, "aşağıdaki parametrelerle eşleşen bir ürün bulunamıyor" ifadesini içeren bir hata iletisi alırsanız, `--noweb` anahtarı 16.3.5 veya sonraki bir sürümüyle kullandığınızdan emin olun.
>
::: moniker-end

Bir düzenden yüklerken, yüklenen içerik düzenden alınır. Ancak, düzende olmayan bir bileşeni seçerseniz, internet 'ten elde edilir.  Visual Studio kurulumunun mizanpajında bulunmayan içeriği indirmasını engellemek istiyorsanız `--noWeb` seçeneğini kullanın. `--noWeb`Kullanılıyorsa ve mizanpajda yüklenmek üzere seçilen içerik eksikse, kurulum başarısız olur.

> [!TIP]
> İnternet 'e bağlı olmayan bir bilgisayarda çevrimdışı bir kaynaktan yüklemek istiyorsanız, `--noWeb` ve `--noUpdateInstaller` seçeneklerini belirtin. İlki, güncelleştirilmiş iş yüklerini, bileşenleri, vb. indirmeyi önler. İkincisi, yükleyicinin Web 'den kendi kendine güncelleştirilmesini engeller.

> [!IMPORTANT]
> Bu `--noWeb` seçenek, internet 'e bağlı bir bilgisayardaki güncelleştirmeleri denetlemek Için Visual Studio kurulumunu durdurmaz. Daha fazla bilgi için bkz. [ağ tabanlı Visual Studio dağıtımlarının güncelleştirmelerini denetleme](controlling-updates-to-visual-studio-deployments.md) sayfası.

### <a name="error-codes"></a>Hata kodları

Parametresini kullandıysanız, `--wait` işlem sonucuna bağlı olarak, `%ERRORLEVEL%` ortam değişkeni aşağıdaki değerlerden birine ayarlanır:

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
> Ancak, bir *Düzen* oluşturup buradan yüklüyorsanız, düzen mizanpajda mevcut olan Visual Studio 'nun belirli sürümünü yükler. Çevrimiçi olarak daha yeni bir sürüm mevcut olsa da, düzen içindeki Visual Studio 'nun sürümünü alırsınız.

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> [VisualStudio.Microsoft.com](https://visualstudio.microsoft.com/downloads) ' de kullanılabilir olan Visual Studio Bootstrap, her çalıştırıldığında kullanılabilir olan en son Visual Studio sürümünü indirip yükler.
>
> Bu nedenle, bugün bir Visual Studio *önyükleyici* indirir ve şu anda altı ay çalıştırırsanız, önyükleyici çalıştırdığınız zaman geçerli olan Visual Studio sürümünü yükler.
>
> Ancak, bir *Düzen* oluşturup buradan yüklüyorsanız, düzen mizanpajda mevcut olan Visual Studio 'nun belirli sürümünü yükler. Çevrimiçi olarak daha yeni bir sürüm mevcut olsa da, düzen içindeki Visual Studio 'nun sürümünü alırsınız.

::: moniker-end

Visual Studio 'nun daha eski bir sürümü için bir düzen oluşturmanız gerekiyorsa, [https://my.visualstudio.com](https://my.visualstudio.com) Visual Studio bootstrap'ın "düzeltilen" sürümlerini indirmek için adresine gidin.

### <a name="how-to-get-support-for-your-offline-installer"></a>Çevrimdışı Yükleyicinizle ilgili destek alma

Çevrimdışı yüklemenizde bir sorunla karşılaşırsanız bunun hakkında bilgi sahibi olmak istiyoruz. Bize anlatmak için en iyi yol, [sorun bildir](../ide/how-to-report-a-problem-with-visual-studio.md) aracını kullanmaktır. Bu aracı kullandığınızda sorunu tanılamanıza ve gidermenize yardımcı olması için ihtiyacımız olan telemetri ve günlükleri bize gönderebilirsiniz.

Ayrıca, yükleme ile ilgili sorunlar için bir [**yükleme sohbeti**](https://visualstudio.microsoft.com/vs/support/#talktous) (yalnızca İngilizce) için destek seçeneği sunuyoruz.

Diğer destek seçenekleri de mevcuttur. Bir liste için bkz. [geri bildirim](../ide/feedback-options.md) sayfamız.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
- [Visual Studio’nun ağ tabanlı yüklemesini güncelleştirme](update-a-network-installation-of-visual-studio.md)
- [Visual Studio 'Yu yüklerken veya kullanırken ağla ilgili hatalarda sorun giderme](troubleshooting-network-related-errors-in-visual-studio.md)
- [Ağ tabanlı Visual Studio dağıtımlarında güncelleştirmeleri denetleme](controlling-updates-to-visual-studio-deployments.md)
- [Visual Studio ürün yaşam döngüsü ve bakım](/visualstudio/releases/2019/servicing/)
- [Bakım temeli sırasında Visual Studio’yu güncelleştirme](update-servicing-baseline.md)
- [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
- [Visual Studio iş yükü ve bileşen kimlikleri](workload-and-component-ids.md)
- [Visual Studio çevrimdışı yükleme için gerekli sertifikaları yükleme](install-certificates-for-visual-studio-offline.md)