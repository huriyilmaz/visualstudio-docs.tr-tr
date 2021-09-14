---
title: Ağ tabanlı bir yüklemeyi güncelleştirme
description: --layout komutunu kullanarak ağ tabanlı Visual Studio güncelleştirmeyi öğrenin
ms.date: 05/26/2021
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 1AF69C0E-0AC9-451B-845D-AE4EDBCEA65C
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: d831210d2943a4247f43818eca637ab5b0b5635b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625820"
---
# <a name="update-a-network-based-installation-of-visual-studio"></a>Visual Studio’nun ağ tabanlı yüklemesini güncelleştirme

Visual Studio'nin ağ yükleme düzenini en son ürün güncelleştirmeleriyle güncelleştirebilirsiniz; böylece hem Visual Studio'nin en son güncelleştirmesi için bir yükleme noktası olarak hem de istemci iş istasyonlarına dağıtılmış olan yüklemeleri korumak için kullanılabilir.

## <a name="how-to-update-a-network-layout"></a>Ağ düzenini güncelleştirme

> [!IMPORTANT]
> Bu yönergelerde, daha önce bir ağ yükleme düzeni oluşturduğunuz ve istemcinin güncelleştirmeleri nasıl aldıracakları hakkında bazı kararlar alasınız. Bunun nasıl olduğu hakkında daha fazla bilgi için, Visual Studio ağ yüklemesi oluşturma ve [Dağıtımlara](create-a-network-installation-of-visual-studio.md) [güncelleştirmeleri Visual Studio sayfasına](../install/controlling-updates-to-visual-studio-deployments.md) bakın.

Ağ yükleme paylaşımınızı en son güncelleştirmeleri içeren şekilde yenilemek için, güncelleştirilmiş paketleri indirmek için parametresini `--layout` kullanarak önyükleyiciyi çalıştırın.

Ağ düzenini ilk oluşturulduğunda kısmi [bir düzen seçtiysanız,](create-a-network-installation-of-visual-studio.md)bu ayarlar kaydedilir. Gelecekteki düzen komutları, önceki seçeneklerin yanı sıra belirttiğiniz yeni seçenekleri kullanır.

Bir dosya paylaşımında bir düzen barındırırsanız, düzenin özel bir kopyasını güncelleştirmeniz (örneğin, c:\VSLayout) ve ardından, tüm güncelleştirilmiş içerik indirildikten sonra dosya paylaşımınıza kopyalayın \\ (örneğin, sunucu\ürünler\VS). Bunu yapmasanız, düzeni güncelleştirirken Kurulumu çalıştıran kullanıcıların henüz tamamen güncelleştirilmediklerinden tüm içeriği düzenden alama ihtimali daha yüksek olur.

Şimdi düzeni oluşturma ve güncelleştirmeye birkaç örnek verilmiştir:

* İlk olarak, yalnızca İngilizce için tek bir iş yüküne sahip bir düzen oluşturma örneği:

  ```shell
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
  ```

* Aynı düzeni daha yeni bir sürüme nasıl güncelleştirebilirsiniz? Ek komut satırı parametresi belirtmenize gerek yok. Önceki ayarlar kaydedilmiştir ve bu düzen klasöründeki sonraki düzen komutları tarafından kullanılacaktır.

  ```shell
  vs_enterprise.exe --layout c:\VSLayout
  ```

* Burada, düzeninizi katılımsız bir şekilde daha yeni bir sürüme nasıl güncelleştirebilirsiniz? Düzen işlemi, kurulum işlemini yeni bir konsol penceresinde çalıştırır. Kullanıcılar son sonucu ve oluşan hataların özetini görene kadar pencere açık bıraktır. Bir düzen işlemini katılımsız bir şekilde gerçekleştirıyorsanız (örneğin, düzeninizi en son sürüme güncelleştirmek için düzenli olarak çalıştıran bir betiğiniz varsa) parametresini kullanın; böylece işlem pencereyi otomatik `--passive` olarak kapatır.

  ```shell
  vs_enterprise.exe --layout c:\VSLayout --passive
  ```

* Ek bir iş yükü ve yerelleştirilmiş dil eklemenin nasıl olduğunu burada açık şekilde açıklarız.  (Bu komut *Azure* geliştirme iş yükünü ekler.)  Artık hem Yönetilen Masaüstü hem de Azure bu düzende yer almaktadır.  İngilizce ve Almanca dil kaynakları da tüm bu iş yüklerine dahil edilir.  Ayrıca düzen, kullanılabilir en son sürüme güncelleştirilir.

  ```shell
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
  ```

    > [!IMPORTANT]
    > Güncelleştirme işlemi, düzen veya istemciye ek isteğe bağlı bileşenleri indirmez veya yüklemez. İsteğe bağlı bileşenleri eklemeniz veya değiştirmenizi gerekirse, önce yanıt dosyasından eski isteğe bağlı bileşenleri kaldırın ve "ekle" bölümüne ihtiyacınız `Layout.JSON` [](automated-installation-with-response-file.md) olan yeni bileşenleri `Layout.JSON` ekleyin. Ardından, düzende update komutunu çalıştırarak yeni eklenen bileşenleri düzene indirir. 
    >
    > Bu yeni bileşenleri istemci makinesine yüklemek için bu üç adımı tamamlayanın. İlk olarak, düzenin yukarıda açıklandığı gibi yeni bileşenleri içerdiğini doğrulayın. Ardından, istemcinizi düzende en son bitlere güncelleştirin.  Son olarak, istemcide yeniden, istemci makinesine yeni bileşenleri (düzene eklenmiş olan) yükecek bir değiştirme işlemi çalıştırın.

* Son olarak, sürümü güncelleştirmeden ek bir iş yükü ve yerelleştirilmiş dil eklemenin nasıl olduğunu burada açıklarız. (Bu komut, ASP.NET *ve web geliştirme iş yükünü* ekler.)  Artık Yönetilen Masaüstü, Azure ve ASP.NET & Web Geliştirme iş yükleri bu düzende yer almaktadır. Bu iş yüklerinin tamamında İngilizce, Almanca ve Fransızca dil kaynakları da mevcuttur.  Ancak, bu komut çalıştırılana kadar düzen kullanılabilir en son sürüme güncelleştirilmedi. Mevcut sürümde kalır.

  ```shell
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.NetWeb --lang fr-FR --keepLayoutVersion
  ```

## <a name="deploy-an-update-to-client-machines"></a>İstemci makinelere güncelleştirme dağıtma

Ağ ortamının nasıl yapılandırıldığına bağlı olarak, güncelleştirme bir kuruluş yöneticisi tarafından dağıtılabilir veya bir istemci makineden başlatılabilir.

* Kullanıcılar, çevrimdışı Visual Studio bir yükleme klasöründen yüklenmiş bir örnek örneğini güncelleştirebilirsiniz:
  * Aşağıdaki Visual Studio Yükleyicisi.
  * Ardından **Güncelleştir'e tıklayın.**

::: moniker range="vs-2017"

* Yöneticiler iki ayrı komutla kullanıcı etkileşimi Visual Studio istemci dağıtımlarını güncelleştirebilirsiniz:
  * İlk olarak, Visual Studio güncelleştirin: <br>```vs_enterprise.exe --quiet --update```
  * Ardından, uygulamanın Visual Studio güncelleştirin: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" --quiet --wait --norestart```

::: moniker-end

::: moniker range="vs-2019"

* Yöneticiler iki ayrı komutla kullanıcı etkileşimi Visual Studio istemci dağıtımlarını güncelleştirebilirsiniz:
  * İlk olarak, Visual Studio güncelleştirin: <br>```vs_enterprise.exe --quiet --update```
  * Ardından, uygulamanın Visual Studio güncelleştirin: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" --quiet --wait --norestart```

::: moniker-end

::: moniker range=">=vs-2022"

* Yöneticiler iki ayrı komutla kullanıcı etkileşimi Visual Studio istemci dağıtımlarını güncelleştirebilirsiniz:
  * İlk olarak, Visual Studio güncelleştirin: <br>```vs_enterprise.exe --quiet --update```
  * Ardından, uygulamanın Visual Studio güncelleştirin: <br>```vs_enterprise.exe update --installPath "C:\Program Files\Microsoft Visual Studio\2022\Enterprise" --quiet --wait --norestart```

::: moniker-end

> [!NOTE]
> bir [vswhere.exe makinede](tools-for-managing-visual-studio-instances.md) var olan bir sanal makine örneğinin yükleme Visual Studio için Visual Studio komutunu kullanın.
>
> [!TIP]
> Güncelleştirme bildirimlerinin kullanıcılara ne zaman sun alınarak kontrol edilecekleri hakkında ayrıntılı bilgi için bkz. Ağ tabanlı [güncelleştirmeler ve dağıtımlar Visual Studio denetleme.](controlling-updates-to-visual-studio-deployments.md)

## <a name="verify-a-layout"></a>Düzeni doğrulama

Sağlanan `--verify` çevrimdışı önbellekte doğrulama gerçekleştirmek için kullanın. Paket dosyalarının eksik mi yoksa geçersiz mi olduğunu denetler. Doğrulamanın sonunda eksik dosyaların ve geçersiz dosyaların listesini yazdırır.

```shell
vs_enterprise.exe --layout <layoutDir> --verify
```

vs_enterprise.exe layoutDir içinde çağrılabilir.

> [!NOTE]
> seçeneği tarafından gereken bazı önemli meta veri `--verify` dosyaları, düzen çevrimdışı önbelleğinde yer almalı. Bu meta veri dosyaları eksikse "--verify" çalıştıramaz ve Kurulum size bir hata verir. Bu hatayla karşılaştıysanız, farklı bir klasöre (veya aynı çevrimdışı önbellek klasörüne) yeni bir çevrimdışı düzen yeniden oluşturun. Bunu yapmak için, ilk çevrimdışı düzeni oluşturmak için kullanılan düzen komutunu çalıştırın. Örneğin, `vs_enterprise.exe --layout <layoutDir>`.

Microsoft düzenli aralıklarla Visual Studio güncelleştirmeler ile birlikte gönderilir, bu nedenle, yeni oluştur o düzen ilk düzenle aynı sürümde olmayacaktır.

> [!NOTE]
> Doğrulama yalnızca belirli bir ikincil sürümün en son sürümü için Visual Studio. Yeni bir sürüm yayımlanmasıyla doğrulama, aynı ikincil sürümün önceki düzeltme eki düzeyi sürümleri için çalışmaz.

## <a name="fix-a-layout"></a>Düzeni düzeltme

ile `--fix` aynı doğrulamayı gerçekleştirmek ve `--verify` ayrıca tanımlanan sorunları düzeltmeyi denemek için kullanın. İşlem için bir İnternet bağlantısı olması gerekir, bu nedenle çağırmadan `--fix` önce makinenizin İnternet'e bağlı olduğundan emin `--fix` olun.

```shell
vs_enterprise.exe --layout <layoutDir> --fix
```

vs_enterprise.exe layoutDir içinde çağrılabilir.

## <a name="remove-older-versions-from-a-layout"></a>Düzenden eski sürümleri kaldırma

Çevrimdışı bir önbellekte düzen güncelleştirmeleri gerçekleştirdikten sonra, düzen önbelleği klasöründe artık en son önbellek yüklemesi için gerekmeyecek bazı eski Visual Studio olabilir. Eski paketleri çevrimdışı `--clean` önbellek klasöründen kaldırmak için seçeneğini kullanabilirsiniz.

Bunu yapmak için, bu eski paketleri içeren katalog bildirimlerini içeren dosya yollara ihtiyacınız vardır. Katalog bildirimlerini çevrimdışı düzen önbelleğinde bir "Arşiv" klasöründe bulabilirsiniz. Bir düzeni güncelleştirinca bu sayfalara kaydedilir. "Arşiv" klasöründe, her biri eski bir katalog bildirimi içeren bir veya daha fazla "GUID" adlı klasör vardır. "GUID" klasörlerinin sayısı, çevrimdışı önbelleğinize yapılan güncelleştirmelerin sayısıyla aynı olması gerekir.

Her "GUID" klasörüne birkaç dosya kaydedilir. En çok ilgini alan iki dosya bir "catalog.json" dosyası ve bir "version.txt" dosyasıdır. "catalog.json" dosyası, seçeneğine geçmemiz gereken eski katalog `--clean` bildirimidir. Diğer version.txt dosyası bu eski katalog bildiriminin sürümünü içerir. Sürüm numarasına bağlı olarak, bu katalog bildiriminden eski paketleri kaldırmak isteyip istemeyebilirsiniz. Aynı şekilde diğer "GUID" klasörlerini de geçebilirsiniz. Temizlemek istediğiniz kataloglarla ilgili karar verdikten sonra, bu kataloglara dosya yollarını `--clean` serek komutunu çalıştırın.

--clean seçeneğinin nasıl kullanıla ilgili birkaç örnek aşağıda verilmiştir:

```shell
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> <file-path-of-catalog2> …
```

```shell
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> --clean <file-path-of-catalog2> …
```

LayoutDir içinde vs_enterprise.exe da &lt; &gt; çağırabilirsiniz. Aşağıda bir örnek verilmiştir:

```shell
c:\VSLayout\vs_enterprise.exe --layout c:\VSLayout --clean c:\VSLayout\Archive\1cd70189-fc55-4583-8ad8-a2711e928325\Catalog.json --clean c:\VS2017Layout\Archive\d420889f-6aad-4ba4-99e4-ed7833795a10\Catalog.json
```

Bu komutu yürütürken, Kurulum, kaldıracak dosyaların listesini bulmak için çevrimdışı önbellek klasörlerinizi analiz eder. Ardından, silinecek dosyaları gözden geçirme ve silme işlemlerini onaylama fırsatınız olur.

## <a name="get-support-for-your-offline-installer"></a>Çevrimdışı yükleyiciniz için destek alın

Çevrimdışı yükleme işlemiyle ilgili bir sorun yaşamanız gerekir. Bize söylemenin en iyi yolu Sorun Bildir [aracını kullanmaktır.](../ide/how-to-report-a-problem-with-visual-studio.md) Bu aracı kullanarak sorunu tanılamamıza ve düzeltmeye yardımcı olmak için ihtiyacımız olan telemetri ve günlükleri bize gönderebilirsiniz.

Yüklemeyle ilgili sorunlar [**için canlı**](https://visualstudio.microsoft.com/vs/support/#talktous) sohbet (yalnızca İngilizce) destek seçeneği de sunuyoruz.

Başka destek seçenekleri de mevcuttur. Liste için Geri Bildirim [sayfamıza](../ide/feedback-options.md) bakın.

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yu yükleme](install-visual-studio.md)
* [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
* [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio örneklerini algılamaya ve yönetmeye yönelik araçlar](tools-for-managing-visual-studio-instances.md)
* [Ağ tabanlı dağıtımlarda güncelleştirmeleri Visual Studio denetleme](controlling-updates-to-visual-studio-deployments.md)
* [Visual Studio yaşam döngüsü ve bakım](/visualstudio/releases/2019/servicing/)
