---
title: Ağ tabanlı yükleme oluşturma
description: Visual Studio 'Yu bir kuruluş içinde dağıtmak için bir ağ yüklemesi noktası oluşturmayı öğrenin.
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
ms.openlocfilehash: 6a93a8a41e4d2c4c91a55cfe91459f7a501b8efc
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107296995"
---
# <a name="create-a-network-installation-of-visual-studio"></a>Visual Studio 'nun ağ yüklemesi oluşturma

Bazen bir Kurumsal Yönetici, istemci iş istasyonlarına dağıtılabilecek Visual Studio dosyalarını içeren bir ağ yüklemesi noktası oluşturmak istemektedir. Bu, istemci makinelerin internet 'e sınırlı izinleri olabileceği ya da iç ekipler Geliştirici araç takımının belirli bir sürümünde standartmadan önce uyumluluk testi yapmak istediği senaryolara yardımcı olur. Visual Studio 'Yu, yöneticinin hem ilk yükleme hem de gelecekteki tüm ürün güncelleştirmeleri için tüm Visual Studio dosyalarını içeren dahili bir statik ağ paylaşımında bulunan bir dosya önbelleği oluşturan bir _ağ düzeni oluşturabilmesi_ için tasarlıyoruz.

 > [!NOTE]
 >  - Kuruluşunuzda birden çok Visual Studio sürümü (örneğin, hem Visual Studio 2019 Professional hem de Visual Studio 2019 Enterprise) varsa, her sürüm için ayrı bir ağ yüklemesi oluşturmanız gerekir.
 >  - İlk istemci yüklemesi _yapmadan önce_ istemcilerin ürün güncelleştirmelerini nasıl alacağını tercih etmenizi öneririz.  Bu, yapılandırma seçeneklerinizin doğru şekilde ayarlandığından emin olmanızı kolaylaştırır. Seçenekleriniz, istemcilerin ağ düzeni konumundan veya internet 'ten güncelleştirme almasını içerir. 
 >  - Onarma ve kaldırma işlevlerinin düzgün çalıştığından emin olmak için özgün Visual Studio yükleme düzeni ve sonraki tüm ürün güncelleştirmelerinin aynı ağ dizininde bulunması gerekir. 

## <a name="download-the-visual-studio-bootstrapper"></a>Visual Studio önyükleyici 'yi indirin

İstediğiniz Visual Studio sürümü için bir önyükleyici dosyası indirin. **Kaydet**' i seçtiğinizden emin olun ve sonra **klasörü aç**' ı seçin.

::: moniker range="vs-2017"

Visual Studio 2017 sürüm 15,9 için en son önyükleyici almak üzere [Visual Studio önceki sürümler](https://visualstudio.microsoft.com/vs/older-downloads/) sayfasına gidin ve aşağıdaki önyükleyici dosyalarından birini indirin:

| Sürüm | Kısaltın |
|-------------|-----------------------|
|Visual Studio 2017 Enterprise sürüm 15,9 | vs_enterprise.exe |
|Visual Studio 2017 Professional sürüm 15,9 | vs_professional.exe |
|Visual Studio 2017 derleme araçları sürüm 15,9  | vs_buildtools.exe |

Desteklenen diğer bootstrapdenetleyicileri vs_feedbackclient.exe, vs_teamexplorer.exe, vs_testagent.exe, vs_testcontroller.exe ve vs_testprofessional.exe içerir.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 2019 önyükleyici 'yi Visual Studio [İndirmeleri sayfasından](https://visualstudio.microsoft.com/downloads) veya Visual Studio 'nun seçili sürümü için visual Studio [2019 yayınlar](https://docs.microsoft.com/visualstudio/releases/2019/history#installing-an-earlier-release) sayfasından indirerek başlayın.  Kurulum çalıştırılabiliriniz &mdash; veya daha belirgin olması için bir önyükleyici dosyası &mdash; eşleşecektir veya aşağıdakilerden birine benzer olacaktır:

|Sürüm | İndir|
|-------------|-----------------------|
|Visual Studio Enterprise | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
|Visual Studio Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
| Visual Studio Derleme Araçları   | [vs_buildtools.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019) |

Desteklenen diğer bootstrapdenetleyicileri [vs_teamexplorer.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/4026077127d25d33789f3882998266946608d8ada378b6ed7c8fff8c07f3dde2/vs_TeamExplorer.exe), [vs_testagent.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/1383bf8bcda3d0e986a2e42c14114aaea8a7b085d31aa0623c9f70b2bad130e4/vs_TestAgent.exe)ve [vs_testcontroller.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/54dcf24b76e7cd9fb8be0ac518a9dfba6daf18fe9b2aa1543411b1cda8820918/vs_TestController.exe)içerir.

::: moniker-end

::: moniker range="vs-2017"

>[!TIP]
>Daha önce bir önyükleyici dosyası indirdiyseniz ve hangi sürümün olduğunu doğrulamak istiyorsanız, bunun nasıl yapıldığını burada bulabilirsiniz. Windows 'ta dosya Gezgini 'ni açın, önyükleyici dosyasına sağ tıklayın, **Özellikler**' i seçin, **Ayrıntılar** sekmesini seçin ve ardından **ürün sürümü** numarasını görüntüleyin. Bu numarayı bir Visual Studio sürümüyle eşleştirmek için bkz. [Visual Studio derleme numaraları ve sürüm tarihleri](visual-studio-build-numbers-and-release-dates.md).

::: moniker-end

::: moniker range="vs-2019"

>[!TIP]
>Daha önce bir önyükleyici dosyası indirdiyseniz ve hangi sürümün olduğunu doğrulamak istiyorsanız, bunun nasıl yapıldığını burada bulabilirsiniz. Windows 'ta dosya Gezgini 'ni açın, önyükleyici dosyasına sağ tıklayın, **Özellikler**' i seçin, **Ayrıntılar** sekmesini seçin ve ardından **ürün sürümü** numarasını görüntüleyin. Bu numarayı bir Visual Studio sürümüyle eşleştirmek için bkz. [Visual studio 2019 yayımları](https://docs.microsoft.com/visualstudio/releases/2019/history).

::: moniker-end

## <a name="create-an-offline-installation-folder"></a>Çevrimdışı yükleme klasörü oluşturma

Bu adımı tamamlayabilmeniz için bir internet bağlantınızın olması gerekir. 

Bir komut istemi açın, önyükleyiciyi indirdiğiniz dizine gidin ve ağ yükleme önbelleğinizi oluşturup sürdürmek üzere [Visual Studio 'yu yüklemek için komut satırı parametrelerini kullanma](../install/use-command-line-parameters-to-install-visual-studio.md) sayfasında tanımlandığı şekilde önyükleyici parametrelerini kullanın. İlk düzen oluşturma örnekleri aşağıda gösterilmektedir ve [Visual Studio yüklemesi Için komut satırı parametre örnekleri](../install/command-line-parameter-examples.md)aşağıda verilmiştir.  

   > [!IMPORTANT]
   > Tek bir dil yerel ayarı için tüm ilk düzen, Visual Studio Community için 35 GB disk alanı ve Visual Studio Enterprise için 42 GB gerektirir. Ek [dil yerel ayarları](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales) her bırı için GB olmak üzere gereklidir. Daha fazla bilgi için [ağ yerleşimini özelleştirme](#customize-the-network-layout) bölümüne bakın. Sonraki düzen güncelleştirmelerinin aynı ağ konumunda de depolanması gerekir. bu nedenle, ağ düzeni konumunun Dizin içeriğinin zaman içinde çok büyük bir zaman almasını beklediğinden emin olun.  
   
- Tüm diller ve tüm özelliklerle Visual Studio Enterprise ilk düzeni oluşturmak için şunu çalıştırın:

  ```vs_enterprise.exe --layout c:\VSLayout```

- Tüm diller ve tüm özelliklerle Visual Studio Professional ilk düzeni oluşturmak için şunu çalıştırın:

  ```vs_professional.exe --layout c:\VSLayout```

## <a name="modify-the-responsejson-file"></a>Dosyadaki response.jsDeğiştir

`response.json`Dosyayı, kurulum çalıştırıldığında kullanılan varsayılan değerleri ayarlamak için değiştirebilirsiniz.  Örneğin, `response.json` otomatik olarak seçilmesi gereken belirli bir iş yükü kümesini seçmek için dosyayı yapılandırabilirsiniz. Ayrıca, `response.json` istemcinin yalnızca ağ düzeni konumundan güncelleştirilmiş dosyaları alıp almamanız gerektiğini belirtmek için yapılandırabilirsiniz. Daha fazla bilgi için bkz. [Visual Studio yüklemesini bir yanıt dosyasıyla otomatikleştirme](../install/automated-installation-with-response-file.md). 

Visual Studio önyükleyici ile bir dosyayla eşleştirmeniz sırasında hata oluşturan bir sorunla karşılaşırsanız `response.json` , daha fazla bilgi için bkz. [Visual Studio 'yu yüklerken veya kullanırken ağla Ilgili hatalarda sorun giderme](../install/troubleshooting-network-related-errors-in-visual-studio.md#error-failed-to-parse-id-from-parent-process) sayfası.

## <a name="copy-the-layout-to-a-network-share"></a>Düzeni bir ağ paylaşımında kopyalama

İstemci makinelerden çalıştırılabilmesi için düzeni bir ağ paylaşımında barındırın.

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

### <a name="save-your-layout-options"></a>Düzen seçeneklerinizi kaydedin

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

İlk olarak, "en son", "geçerli", "tek yeşil" ve "Tıp" sözcüklerinin ayırt edilebilir iki tür Visual Studio bootstrapolduğunu ve temelde "sabit sürüm" anlamına gelen bir tane olduğunu anlamanız gerekir. Önyükleyici dosyalarının her iki türü de tam olarak aynı ada sahiptir ve türü ayırt etmenin en iyi yolu, aldığınız yere dikkat çekici bir ödemelidir. Visual Studio [İndirmeleri sayfasında](https://visualstudio.microsoft.com/downloads) bulunan Visual Studio bootstrapdenetleyicileri, her zaman yeşil Visual Studio bootstrapolarak kabul edilir ve önyükleyici çalıştırıldığında her zaman kanalda bulunan en son sürümü yükler (veya güncelleştirir). Visual Studio [2019 yayımları](https://docs.microsoft.com/visualstudio/releases/2019/history) sayfasında bulunan veya Microsoft Update kataloğunda yönetici güncelleştirmesinin içine katıştırılmış olan Visual Studio Bootstrap, ürünün belirli bir sabit sürümünü yüklememektedir. 

Bu nedenle, şu anda bir tek yeşil Visual Studio önyükleyici indirir ve bugün altı ay sonra çalıştırırsanız, önyükleyici çalıştırıldığı sırada geçerli olan Visual Studio sürümünü yükler. Her zaman en son bitleri yüklemek ve güncel tutmak için tasarlanmıştır.

Sabit bağlantı önyükleyiciyi indirdiyseniz veya Microsoft Kataloğundan indirdiğiniz bir yönetici güncelleştirmesi çalıştırırsanız, ne zaman çalıştırıldıklarından bağımsız olarak ürünün belirli bir sürümünü yükler.

Son olarak, bu Bootstrap'in herhangi birini kullanarak bir ağ düzeni oluşturabilirsiniz ve düzende oluşturulacak olan sürüm, kullandığınız önplanda, örneğin, sabit bir sürüm veya geçerli olacaktır. Daha sonra, herhangi bir ön önyükleyici kullanarak ağ yerleşimini güncelleştirebilir veya Microsoft Update kataloğundan yönetici güncelleştirme paketini de kullanabilirsiniz. Düzeni nasıl güncelleştirtiğinize bakılmaksızın, sonuçta elde edilen güncelleştirilmiş düzen ürünün belirli bir sürümünü içeren bir paket önbelleği olur ve daha sonra sabit bir bağlantı önyükleyici gibi davranır. Bu nedenle, istemci düzenden her yüklendiğinde, istemci, düzende bulunan Visual Studio 'nun belirli sürümünü yükler (daha yeni bir sürüm çevrimiçi olmasına rağmen). 

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
