---
title: Ağ tabanlı bir yüklemeyi güncelleştirme
description: --layout komutunu kullanarak ağ tabanlı bir Visual Studio güncelleştirmeyi öğrenin
ms.date: 05/26/2021
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 1AF69C0E-0AC9-451B-845D-AE4EDBCEA65C
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 74464aa76c24a798d33fa7639cdd0b6a07489bf7
ms.sourcegitcommit: 62e39ea1bf0ed939376c4375fc180ff7c4c760fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2021
ms.locfileid: "110660227"
---
# <a name="update-a-network-based-installation-of-visual-studio"></a>Visual Studio’nun ağ tabanlı yüklemesini güncelleştirme

Visual Studio'ın ağ yükleme düzenini en son ürün güncelleştirmeleriyle güncelleştirebilirsiniz; böylece hem Visual Studio'nin en son güncelleştirmesi için bir yükleme noktası olarak hem de istemci iş istasyonlarına dağıtılmış olan yüklemelerin bakımını yapmak için kullanılabilir.

## <a name="how-to-update-a-network-layout"></a>Ağ düzenini güncelleştirme

> [!IMPORTANT]
> Bu yönergelerde, daha önce bir ağ yükleme düzeni oluşturduğunuz ve istemcinin güncelleştirmeleri nasıl aldıracakları konusunda bazı kararlar alasınız. Bunun nasıl olduğu hakkında daha fazla bilgi için, Visual Studio ağ yüklemesi oluşturma ve [Dağıtımlarda](create-a-network-installation-of-visual-studio.md) [güncelleştirmeleri Visual Studio sayfasına](../install/controlling-updates-to-visual-studio-deployments.md) bakın.

Ağ yükleme paylaşımınızı en son güncelleştirmeleri içeren şekilde yenilemek için, güncelleştirilmiş paketleri indirmek için parametresini `--layout` kullanarak önyükleyiciyi çalıştırın.

Ağ düzenini ilk oluşturulduğunda kısmi [bir düzen seçtiysanız,](create-a-network-installation-of-visual-studio.md)bu ayarlar kaydedilir. Gelecekteki düzen komutları, önceki seçeneklerin yanı sıra belirttiğiniz yeni seçenekleri kullanır.

Bir dosya paylaşımında düzen barındırırsanız, düzenin özel bir kopyasını güncelleştirmeniz (örneğin, c:\VSLayout) ve ardından, tüm güncelleştirilmiş içerik indirildikten sonra bunu dosya paylaşımınıza \\ (örneğin, sunucu\ürünler\VS) kopyalamanız gerekir. Bunu yapmasanız, düzeni güncelleştirirken Kurulumu çalıştıran kullanıcıların henüz tamamen güncelleştirilmediklerinden tüm içeriği düzenden alama ihtimali daha yüksek olur.

Şimdi düzeni oluşturma ve güncelleştirmeye birkaç örnek verilmiştir:

* İlk olarak, yalnızca İngilizce için tek bir iş yüküne sahip bir düzen oluşturma örneği:

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
  ```

* Aynı düzeni daha yeni bir sürüme nasıl güncelleştirebilirsiniz? Ek komut satırı parametresi belirtmenize gerek yok. Önceki ayarlar kaydedilmiştir ve bu düzen klasöründeki sonraki düzen komutları tarafından kullanılacaktır.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout
  ```

* Bu şekilde, düzeninizi daha yeni bir sürüme katılımsız bir şekilde güncelleştirebilirsiniz. Düzen işlemi, kurulum işlemini yeni bir konsol penceresinde çalıştırır. Bu pencere açık kalır, böylece kullanıcılar nihai sonucu ve oluşmuş olabilecek hataların özetini görebilirler. Bir düzen işlemini katılımsız bir şekilde gerçekleştiriyorsanız (örneğin, düzeninizi en son sürüme güncelleştirmek için düzenli olarak çalıştırılan bir betiğe sahipseniz), ardından `--passive` parametresini kullanın ve işlem pencereyi otomatik olarak kapatır.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --passive
  ```

* Ek bir iş yükü ve yerelleştirilmiş dil ekleme hakkında daha fazla bilgiyi burada bulabilirsiniz.  (Bu komut *Azure geliştirme* iş yükünü ekler.)  Artık hem yönetilen masaüstü hem de Azure bu düzene dahildir.  Ingilizce ve Almanca için dil kaynakları, tüm bu iş yükleri için de eklenmiştir.  Düzen, kullanılabilir en son sürüme güncelleştirilir.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
  ```

    > [!IMPORTANT]
    > Bir güncelleştirme işlemi, düzen veya istemciye ek isteğe bağlı bileşenler indirmez veya yüklemez. İsteğe bağlı bileşenler eklemeniz veya değiştirmeniz gerekiyorsa, önce yanıt dosyasındaki eski isteğe bağlı bileşenleri kaldırın `Layout.JSON` [](automated-installation-with-response-file.md) ve "Ekle" bölümünde ihtiyacınız olan yeni bileşenleri ekleyin `Layout.JSON` . Sonra, düzen üzerinde Güncelleştir komutunu çalıştırdığınızda bu, yeni eklenen bileşenleri düzene indirir. 
    >
    > Bu yeni bileşenlerin istemci makinesine yüklenmesini sağlamak için bu üç adımı yaptığınızdan emin olun. İlk olarak, yukarıda açıklandığı gibi düzenin yeni bileşenleri içerdiğini doğrulayın. Sonra, istemcinizi mizanpajda en son bitleri güncelleştirin.  Son olarak, istemci üzerinde, yeni bileşenleri (düzene eklenen) istemci makinesine yükleyecek bir değiştirme işlemi çalıştırın.

* Son olarak, sürümü güncelleştirme olmadan ek bir iş yükü ve yerelleştirilmiş dil ekleme hakkında daha fazla bilgiyi burada bulabilirsiniz. (Bu komut *ASP.net ve Web geliştirme* iş yükünü ekler.)  Artık yönetilen Masaüstü, Azure ve ASP.NET & Web geliştirme iş yükleri bu düzene dahildir. Bu iş yüklerinin tamamında İngilizce, Almanca ve Fransızca dil kaynakları da mevcuttur.  Ancak, bu komut çalıştırılana kadar düzen kullanılabilir en son sürüme güncelleştirilmedi. Mevcut sürümde kalır.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.NetWeb --lang fr-FR --keepLayoutVersion
  ```

## <a name="deploy-an-update-to-client-machines"></a>İstemci makinelere güncelleştirme dağıtma

Ağ ortamının nasıl yapılandırıldığına bağlı olarak, bir güncelleştirme bir kuruluş yöneticisi tarafından dağıtılabilir veya bir istemci makineden başlatılabilir.

* Kullanıcılar, çevrimdışı Visual Studio bir yükleme klasöründen yüklenmiş bir uygulama örneğini güncelleştirebilirsiniz:
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

> [!NOTE]
> İstemci [vswhere.exe var](tools-for-managing-visual-studio-instances.md) olan bir istemci örneğinin yükleme yolunu belirlemek için Visual Studio komutunu kullanın.
>
> [!TIP]
> Güncelleştirme bildirimlerinin kullanıcılara ne zaman sun alınarak kontrol edilecekleri hakkında ayrıntılı bilgi için bkz. Ağ tabanlı [güncelleştirmeler ve dağıtımlar için Visual Studio denetleme.](controlling-updates-to-visual-studio-deployments.md)

## <a name="verify-a-layout"></a>Düzeni doğrulama

Sağlanan `--verify` çevrimdışı önbellekte doğrulama gerçekleştirmek için kullanın. Paket dosyalarının eksik mi yoksa geçersiz mi olduğunu denetler. Doğrulamanın sonunda eksik dosyaların ve geçersiz dosyaların listesini yazdırır.

```cmd
vs_enterprise.exe --layout <layoutDir> --verify
```

vs_enterprise.exe layoutDir içinde çağrılabilir.

> [!NOTE]
> Seçeneğinin gerektirdiği bazı önemli meta veri dosyaları, `--verify` Düzen çevrimdışı önbelleğinde olmalıdır. Bu meta veri dosyaları eksikse, "--Verify" çalıştırılamaz ve kurulum size bir hata verir. Bu hatayla karşılaşırsanız, farklı bir klasöre (veya aynı çevrimdışı önbellek klasörüne) yeni bir çevrimdışı düzen yeniden oluşturun. Bunu yapmak için, ilk çevrimdışı düzeni oluşturmak için kullandığınız Düzen komutunu çalıştırın. Örneğin, `vs_enterprise.exe --layout <layoutDir>`.

Microsoft güncelleştirmeleri Visual Studio 'ya düzenli aralıklarla sevk eder, bu nedenle oluşturduğunuz yeni düzen başlangıç düzeniyle aynı sürümde olmayabilir.

> [!NOTE]
> Doğrulama yalnızca Visual Studio 'nun belirli bir ikincil sürümünün en son sürümü için geçerlidir. Yeni bir sürüm yayımlandığında, doğrulama işlemi, aynı ikincil sürümün önceki düzeltme eki düzeyi sürümleri için çalışmaz.

## <a name="fix-a-layout"></a>Düzeni çözme

İle `--fix` aynı doğrulamayı gerçekleştirmek `--verify` ve ayrıca belirtilen sorunları gidermeyi denemek için kullanın. `--fix`İşlemin bir internet bağlantısı olması gerekir, bu nedenle, çağırabilmeniz için makinenizin internet 'e bağlı olduğundan emin olun `--fix` .

```cmd
vs_enterprise.exe --layout <layoutDir> --fix
```

vs_enterprise.exe layoutDir içinde çağrılabilir.

## <a name="remove-older-versions-from-a-layout"></a>Eski sürümleri düzenden kaldırma

Çevrimdışı bir önbellekte düzen güncelleştirmeleri gerçekleştirdikten sonra, düzen önbellek klasöründe en son Visual Studio yüklemesinde artık gerekli olmayan bazı eski paketler bulunabilir. `--clean`Kullanılmayan paketleri çevrimdışı bir önbellek klasöründen kaldırmak için seçeneğini kullanabilirsiniz.

Bunu yapmak için, bu eski paketleri içeren katalog bildirimlerinin dosya yolları gerekir. Katalog bildirimlerini çevrimdışı düzen önbelleğindeki bir "Arşiv" klasöründe bulabilirsiniz. Bir düzeni güncelleştirdiğinizde bunlar buraya kaydedilir. "Arşiv" klasöründe, her biri eski bir katalog bildirimi içeren bir veya daha fazla "GUID" adlı klasör vardır. "GUID" klasörlerinin sayısı, çevrimdışı önbelleğiniz için yapılan güncelleştirme sayısıyla aynı olmalıdır.

Her "GUID" klasörüne birkaç dosya kaydedilir. En çok ilgini alan iki dosya bir "catalog.js" dosyası ve bir "version.txt" dosyasıdır. "catalog.js" dosyası, seçeneğine geçmemiz gereken eski katalog `--clean` bildirimidir. Diğer version.txt dosyası bu eski katalog bildiriminin sürümünü içerir. Sürüm numarasına bağlı olarak, bu katalog bildiriminden eski paketleri kaldırmak isteyip istemeyebilirsiniz. Aynı şekilde diğer "GUID" klasörlerini de atabilirsiniz. Temizlemek istediğiniz kataloglarla ilgili karar verdikten sonra, bu kataloglara dosya yollarını `--clean` serek komutunu çalıştırın.

--clean seçeneğinin nasıl kullanıla ilgili birkaç örnek aşağıda verilmiştir:

```cmd
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> <file-path-of-catalog2> …
```

```cmd
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> --clean <file-path-of-catalog2> …
```

LayoutDir içinde vs_enterprise.exe da &lt; &gt; çağırabilirsiniz. Aşağıda bir örnek verilmiştir:

```cmd
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
