---
title: Ağ tabanlı yüklemeyi güncelleştirme
description: --düzen komutunu kullanarak ağ tabanlı Visual Studio yüklemesini nasıl güncelleştireceklerini öğrenin
ms.date: 01/08/2020
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 1AF69C0E-0AC9-451B-845D-AE4EDBCEA65C
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 68acfcd4acc06ff2b370f3d77a30bd4ec21eb6d1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114970"
---
# <a name="update-a-network-based-installation-of-visual-studio"></a>Visual Studio’nun ağ tabanlı yüklemesini güncelleştirme

Visual Studio'nun ağ yükleme düzenini en son ürün güncellemeleriyle güncelleştirebilirsiniz, böylece hem Visual Studio'nun en son güncelleştirmesi için bir yükleme noktası olarak kullanılabilir hem de istemciye zaten dağıtılmış olan yüklemeleri korumak için Iş istasyon -ları.

## <a name="how-to-update-a-network-layout"></a>Ağ düzeni nasıl güncellenir?

> [!IMPORTANT]
> Bu yönergeler, daha önce bir ağ yükleme düzeni oluşturduğunuzu varsayar. Nasıl yapılacağınız hakkında daha fazla bilgi için [Visual Studio sayfasının ağ yüklemesi oluştur](create-a-network-installation-of-visual-studio.md) sayfasına bakın.

Ağ yükleme paylaşımınızı en son güncelleştirmeleri içerecek `--layout` şekilde yenilemek için, güncelleştirilmiş paketleri artımlı olarak indirmek için komutu çalıştırın.

::: moniker range="vs-2017"

**15.3'te Yeni**: [Ağ düzenini ilk oluşturduğunuzda](create-a-network-installation-of-visual-studio.md)kısmi bir düzen seçtiyseniz, bu ayarlar kaydedilir. Gelecekteki düzen komutları önceki seçenekleri ve belirttiğiniz yeni seçenekleri kullanır. Ancak, önceki bir sürümün düzenini kullanıyorsanız, içeriğini güncelleştirmek için ağ yükleme düzenini (diğer bir deyişle, aynı iş yükleri ve diller) ilk oluşturduğunuzda kullandığınız komut satırı parametrelerini kullanmanız gerekir.

::: moniker-end

::: moniker range="vs-2019"

[Ağ düzenini ilk oluşturduğunuzda](create-a-network-installation-of-visual-studio.md)kısmi bir düzen seçtiyseniz, bu ayarlar kaydedilir. Gelecekteki düzen komutları önceki seçenekleri ve belirttiğiniz yeni seçenekleri kullanır.

::: moniker-end

Bir dosya paylaşımında bir düzen barındırırsanız, düzenin özel bir kopyasını güncelleştirmeniz gerekir (örneğin, c:\VSLayout) ve ardından güncelleştirilen içeriğin tümü \\indirildikten sonra dosya paylaşımınıza (örneğin, sunucu\products\VS) kopyalamalısınız. Bunu yapmazsanız, düzeni güncelleştirirken Kurulum'u çalıştıran kullanıcıların henüz tam olarak güncelleştirilmediği için içeriğin tamamını düzenden alamayabilir.

Bir düzeni oluşturma ve sonra güncelleme hakkında birkaç örnek üzerinden bakalım:

* İlk olarak, yalnızca İngilizce için tek bir iş yüküiçeren bir düzen oluşturmanın bir örneğini aşağıda verilmiştir:

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
  ```

* Aynı düzeni daha yeni bir sürümle şu şekilde güncelleştirebilirsiniz. Ek komut satırı parametreleri belirtmeniz gerekmez. Önceki ayarlar kaydedildi ve bu düzen klasöründe sonraki düzen komutları tarafından kullanılacaktır.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout
  ```

* Düzeninizi gözetimsiz bir şekilde yeni bir sürüme nasıl güncelleştirebilirsiniz. Düzen işlemi, kurulum işlemini yeni bir konsol penceresinde çalıştırZ. Kullanıcılar nihai sonucu ve oluşmuş olabilecek hataların bir özetini görebilsin diye pencere açık bırakılır. Bir düzen işlemini gözetimsiz bir şekilde gerçekleştiriyorsanız (örneğin, düzeninizi en son sürüme güncelleştirmek için `--passive` düzenli olarak çalıştırılacak bir komut dosyanız varsa), parametreyi kullanın ve işlem pencereyi otomatik olarak kapatır.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --passive
  ```

* Ek bir iş yükü ve yerelleştirilmiş dil şu şekilde ekleyebilirsiniz.  (Bu komut *Azure geliştirme* iş yükünü ekler.)  Artık hem Yönetilen Masaüstü hem de Azure bu düzene dahildir.  Tüm bu iş yükleri için İngilizce ve Almanca dil kaynakları da dahildir.  Ve, düzen en son kullanılabilir sürüme güncelleştirilir.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
  ```

    > [!IMPORTANT]
    > Bir güncelleştirme işlemi, bu bileşenleri [yanıt dosyasının](automated-installation-with-response-file.md)"ekle" bölümüne ekleseniz bile yeni eklenen isteğe bağlı bileşenleri yüklemez. Bu, ekleme işlemi bir güncelleştirme sırasında kullanılmadığından oluşur.
    >
    > **Geçici Çözüm**: Eksik bileşenleri yüklemek için yükseltmeden sonra ayrı bir değişiklik işlemi çalıştırın.

* Ve son olarak, sürümü güncelleştirmeden ek bir iş yükü ve yerelleştirilmiş dil eklemenin nasıl olduğu aşağıda açıklanmıştır. (Bu *komut, ASP.NET ve web geliştirme* iş yükünü ekler.)  Artık Yönetilen Masaüstü, Azure ve ASP.NET & Web Geliştirme iş yükleri bu düzene dahil edilmiştir. Tüm bu iş yükleri için İngilizce, Almanca ve Fransızca dil kaynakları da dahildir.  Ancak, bu komut çalıştırıldığında düzen en son kullanılabilir sürüme güncelleştirilemedi. Varolan sürümde kalır.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.NetWeb --lang fr-FR --keepLayoutVersion
  ```

## <a name="deploy-an-update-to-client-machines"></a>İstemci makinelerine güncelleştirme dağıtma

Ağ ortamınızın nasıl yapılandırıldığına bağlı olarak, güncelleştirme bir kuruluş yöneticisi tarafından dağıtılabilir veya istemci makinesinden başlatılabilir.

* Kullanıcılar çevrimdışı yükleme klasöründen yüklenen bir Visual Studio örneğini güncelleştirebilirsiniz:
  * Visual Studio Yükleyici'yi çalıştırın.
  * Ardından, **Güncelleştir'i**tıklatın.

::: moniker range="vs-2017"

* Yöneticiler, Visual Studio'nun istemci dağıtımlarını iki ayrı komutla herhangi bir kullanıcı etkileşimi olmadan güncelleyebilir:
  * İlk olarak, Visual Studio yükleyicisini güncelleyin: <br>```vs_enterprise.exe --quiet --update```
  * Ardından, Visual Studio uygulamasının kendisini güncelleyin: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" --quiet --wait --norestart```

::: moniker-end

::: moniker range="vs-2019"

* Yöneticiler, Visual Studio'nun istemci dağıtımlarını iki ayrı komutla herhangi bir kullanıcı etkileşimi olmadan güncelleyebilir:
  * İlk olarak, Visual Studio yükleyicisini güncelleyin: <br>```vs_enterprise.exe --quiet --update```
  * Ardından, Visual Studio uygulamasının kendisini güncelleyin: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" --quiet --wait --norestart```

::: moniker-end

> [!NOTE]
> Bir istemci makinesinde Visual Studio'nun varolan bir örneğinin yükleme yolunu tanımlamak için [vswhere.exe komutunu](tools-for-managing-visual-studio-instances.md) kullanın.
>
> [!TIP]
> Güncelleştirme bildirimlerinin kullanıcılara ne zaman sunulduğuna ilişkin ayrıntılar [için, ağ tabanlı Visual Studio dağıtımlarında Denetim güncelleştirmelerine](controlling-updates-to-visual-studio-deployments.md)bakın.

## <a name="verify-a-layout"></a>Düzeni doğrulama

Sağlanan `--verify` çevrimdışı önbellekte doğrulama gerçekleştirmek için kullanın. Paket dosyalarının eksik veya geçersiz olup olmadığını denetler. Doğrulamanın sonunda, eksik dosyaların ve geçersiz dosyaların listesini yazdırır.

```cmd
vs_enterprise.exe --layout <layoutDir> --verify
```

vs_enterprise.exe düzendir içinde çağrılabilir.

> [!NOTE]
> `--verify` Seçenek tarafından gereken bazı önemli meta veri dosyaları, düzen çevrimdışı önbellekte olmalıdır. Bu meta veri dosyaları eksikse, "--verify" çalıştırılamıyor ve Kurulum size bir hata verir. Bu hatayla karşılaşırsanız, farklı bir klasöre (veya aynı çevrimdışı önbellek klasörüne) yeni bir çevrimdışı düzeni yeniden oluşturun. Bunu yapmak için, ilk çevrimdışı düzeni oluşturmak için kullandığınız düzen komutunu çalıştırın. Örneğin, `vs_enterprise.exe --layout <layoutDir>`.

Microsoft güncelleştirmeleri Visual Studio'ya düzenli aralıklarla iletir, bu nedenle oluşturduğunuz yeni düzen ilk düzenle aynı sürüm olmayabilir.

> [!NOTE]
> Doğrulama yalnızca Visual Studio'nun belirli bir küçük sürümünün en son sürümü için çalışır. Yeni bir sürüm yayımlanır yayınlanmaz doğrulama, aynı küçük sürümün önceki yama düzeyi sürümlerinde çalışmaz.

## <a name="fix-a-layout"></a>Düzeni düzeltme

Aynı `--fix` doğrulamayı gerçekleştirmek `--verify` ve tanımlanan sorunları düzeltmeye çalışmak için kullanın. İşlemin `--fix` bir internet bağlantısına ihtiyacı vardır, bu nedenle makinenizin internete bağlı olduğundan emin olun. `--fix`

```cmd
vs_enterprise.exe --layout <layoutDir> --fix
```

vs_enterprise.exe düzendir içinde çağrılabilir.

## <a name="remove-older-versions-from-a-layout"></a>Eski sürümleri düzenden kaldırma

Çevrimdışı önbellekte düzen güncelleştirmeleri gerçekleştirdikten sonra, düzen önbelleği klasöründe artık en son Visual Studio yüklemesi tarafından ihtiyaç duyulmayan bazı eski paketler olabilir. Eski paketleri `--clean` çevrimdışı önbellek klasöründen kaldırmak için seçeneği kullanabilirsiniz.

Bunu yapmak için, bu eski paketleri içeren bildirim(ler) kataloglamak için dosya yolunun(lar) gerekir. Katalog bildirimlerini çevrimdışı düzen önbelleğinde bir "Arşiv" klasöründe bulabilirsiniz. Bir düzeni güncelleştirdiğinizde bunlar orada kaydedilir. "Arşivle" klasöründe, her biri eski bir katalog bildirimi içeren bir veya daha fazla "GUID" adlı klasör vardır. "GUID" klasörlerinin sayısı, çevrimdışı önbelleğinize yapılan güncelleştirme sayısıyla aynı olmalıdır.

Her "GUID" klasörüne birkaç dosya kaydedilir. En çok ilgi çeken iki dosya bir "catalog.json" dosyası ve bir "version.txt" dosyasıdır. "Catalog.json" dosyası, `--clean` seçeneğe geçirmeniz gereken eski katalog bildirimidir. Diğer sürüm.txt dosyası bu eski katalog bildiriminin sürümünü içerir. Sürüm numarasına bağlı olarak, bu katalog bildiriminden eski paketleri kaldırmak isteyip istemediğinizkarar verebilirsiniz. Diğer "GUID" klasörlerinde gezinirken aynı şeyi yapabilirsiniz. Temizlemek istediğiniz katalog(lar) hakkında karar aldıktan sonra, `--clean` bu kataloglara dosya yollarını sağlayarak komutu çalıştırın.

İşte -- temiz seçeneğin nasıl kullanılacağına ilgili birkaç örnek:

```cmd
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> <file-path-of-catalog2> …
```

```cmd
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> --clean <file-path-of-catalog2> …
```

Ayrıca &lt;düzenDir&gt;içinde vs_enterprise.exe çağırabilirsiniz. Bir örneği aşağıda verilmiştir:

```cmd
c:\VSLayout\vs_enterprise.exe --layout c:\VSLayout --clean c:\VSLayout\Archive\1cd70189-fc55-4583-8ad8-a2711e928325\Catalog.json --clean c:\VS2017Layout\Archive\d420889f-6aad-4ba4-99e4-ed7833795a10\Catalog.json
```

Bu komutu çalıştırdığınızda, Setup kaldıracağı dosyaların listesini bulmak için çevrimdışı önbellek klasörünüzü analiz eder. Daha sonra silinecek dosyaları gözden geçirme ve silmeleri onaylama şansınız olacaktır.

## <a name="get-support-for-your-offline-installer"></a>Çevrimdışı yükleyiciniz için destek alın

Çevrimdışı yüklemenizde bir sorun la karşılaşırsanız, bu konuda bir sorun yaşamak isteriz. Bize bildirmenin en iyi yolu [Sorun Bildir](../ide/how-to-report-a-problem-with-visual-studio.md) aracını kullanmaktır. Bu aracı kullandığınızda, sorunu tanılamamıza ve düzeltmemize yardımcı olmak için ihtiyacımız olan telemetri ve günlükleri bize gönderebilirsiniz.

Ayrıca, yüklemeyle ilgili sorunlar için [**canlı sohbet**](https://visualstudio.microsoft.com/vs/support/#talktous) (yalnızca İngilizce) destek seçeneği de sunuyoruz.

Başka destek seçeneklerimiz de mevcuttur. Bir liste için [Geri Bildirim](../ide/feedback-options.md) sayfamıza bakın.

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio yükleme](install-visual-studio.md)
* [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
* [Visual Studio'yı yüklemek için komut satırı parametrelerini kullanma](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio örneklerini algılamaya ve yönetmeye yönelik araçlar](tools-for-managing-visual-studio-instances.md)
* [Ağ tabanlı Visual Studio dağıtımlarında denetim güncelleştirmeleri](controlling-updates-to-visual-studio-deployments.md)
* [Visual Studio ürün yaşam döngüsü ve servis](/visualstudio/releases/2019/servicing/)
