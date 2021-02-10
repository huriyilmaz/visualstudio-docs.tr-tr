---
title: Ağ tabanlı yüklemeyi güncelleştirme
description: --Layout komutunu kullanarak ağ tabanlı Visual Studio yüklemesini güncelleştirme hakkında bilgi edinin
ms.date: 06/29/2020
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 1AF69C0E-0AC9-451B-845D-AE4EDBCEA65C
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 6829bac79f747d4f9bacfe5e71f57352fcad0970
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99959161"
---
# <a name="update-a-network-based-installation-of-visual-studio"></a>Visual Studio’nun ağ tabanlı yüklemesini güncelleştirme

Visual Studio 'nun bir ağ yükleme düzeninin en son ürün güncelleştirmeleriyle güncelleştirilmesi olasıdır. böylece, Visual Studio 'nun en son güncelleştirmesi için bir yükleme noktası olarak ve ayrıca istemci iş istasyonlarına zaten dağıtılan yüklemelerin bakımını yapabilirsiniz.

## <a name="how-to-update-a-network-layout"></a>Ağ yerleşimini güncelleştirme

> [!IMPORTANT]
> Bu yönergelerde, daha önce bir ağ yükleme düzeni oluşturmuş olduğunuz varsayılır. Bunun nasıl yapılacağı hakkında daha fazla bilgi için [Visual Studio 'nun ağ yüklemesi oluşturma](create-a-network-installation-of-visual-studio.md) sayfasına bakın.

Ağ yükleme paylaşımınızı en son güncelleştirmeleri içerecek şekilde yenilemek için, `--layout` güncelleştirilmiş paketleri artımlı olarak indirmek üzere komutunu çalıştırın.

::: moniker range="vs-2017"

**15,3 ' de yeni**: [ağ düzeni ilk oluşturduğunuzda](create-a-network-installation-of-visual-studio.md)kısmi bir düzen seçtiyseniz, bu ayarlar kaydedilir. Gelecekteki tüm düzen komutları, önceki seçenekleri ve belirttiğiniz tüm yeni seçenekleri kullanır. Ancak önceki bir sürümün bir yerleşimini kullanıyorsanız, içeriğini güncelleştirmek için ağ yüklemesi yerleşimini (diğer bir deyişle, aynı iş yüklerini ve dilleri) ilk oluşturduğunuzda kullandığınız komut satırı parametrelerinin aynısını kullanmanız gerekir.

::: moniker-end

::: moniker range="vs-2019"

[Ağ yerleşimini ilk oluşturduğunuzda](create-a-network-installation-of-visual-studio.md)kısmi bir düzen seçtiyseniz, bu ayarlar kaydedilir. Gelecekteki tüm düzen komutları, önceki seçenekleri ve belirttiğiniz tüm yeni seçenekleri kullanır.

::: moniker-end

Bir dosya paylaşımında bir düzen barındırdıysanız, düzenin özel bir kopyasını (örneğin, c:\VSLayout) güncelleştirmeniz gerekir ve ardından tüm güncelleştirilmiş içerik indirildikten sonra dosyayı dosya paylaşımınıza kopyalayın (örneğin, \\ Server\products\vs). Bunu yapmazsanız, düzeni güncelleştirirken kurulum 'U çalıştıran tüm kullanıcıların, henüz tamamen güncelleştirilmediği için düzenden tüm içeriği elde edememesinde daha büyük bir şansınız vardır.

Bir düzeni oluşturma ve güncelleştirme hakkında birkaç örnek adım adım inceleyelim:

* İlk olarak, yalnızca Ingilizce için bir iş yüküne sahip bir düzen oluşturma örneği aşağıda verilmiştir:

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
  ```

* Aynı düzeni daha yeni bir sürüme güncelleştirme hakkında daha fazla bilgiyi burada bulabilirsiniz. Ek komut satırı parametreleri belirtmeniz gerekmez. Önceki ayarlar kaydedildi ve bu düzen klasöründe sonraki tüm düzen komutları tarafından kullanılacak.

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
    > Bir güncelleştirme işlemi yeni eklenen isteğe bağlı bileşenleri yüklemez. Yeni eklenen isteğe bağlı bileşenlere ihtiyacınız varsa, lütfen yanıt dosyasındaki eski isteğe bağlı bileşenleri kaldırın `Layout.JSON` [](automated-installation-with-response-file.md) ve ' nin "Ekle" bölümünde ihtiyacınız olan bileşenleri ekleyin `Layout.JSON` . 
    >
    > **Geçici çözüm**: eksik bileşenleri yüklemek için bir yükseltmeden sonra ayrı bir değiştirme işlemi çalıştırın.

* Son olarak, sürümü güncelleştirme olmadan ek bir iş yükü ve yerelleştirilmiş dil ekleme hakkında daha fazla bilgiyi burada bulabilirsiniz. (Bu komut *ASP.net ve Web geliştirme* iş yükünü ekler.)  Artık yönetilen Masaüstü, Azure ve ASP.NET & Web geliştirme iş yükleri bu düzene dahildir. Ingilizce, Almanca ve Fransızca için dil kaynakları, tüm bu iş yükleri için de eklenmiştir.  Ancak, bu komut çalıştırıldığında düzen en son kullanılabilir sürüme güncelleştirilmedi. Mevcut sürümde kalır.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.NetWeb --lang fr-FR --keepLayoutVersion
  ```

## <a name="deploy-an-update-to-client-machines"></a>İstemci makinelerine güncelleştirme dağıtma

Ağ ortamınızın nasıl yapılandırıldığına bağlı olarak, bir güncelleştirme bir kurumsal yönetici tarafından dağıtılabilir ya da bir istemci makineden başlatılabilir.

* Kullanıcılar, çevrimdışı yükleme klasöründen yüklenen bir Visual Studio örneğini güncelleştirebilir:
  * Visual Studio Yükleyicisi çalıştırın.
  * Ardından **Güncelleştir**' e tıklayın.

::: moniker range="vs-2017"

* Yöneticiler, Visual Studio 'nun istemci dağıtımlarını iki ayrı komutlarla hiçbir Kullanıcı etkileşimi olmadan güncelleştirebilir:
  * İlk olarak, Visual Studio yükleyicisini güncelleştirin: <br>```vs_enterprise.exe --quiet --update```
  * Ardından, Visual Studio uygulamasını güncelleştirin: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" --quiet --wait --norestart```

::: moniker-end

::: moniker range="vs-2019"

* Yöneticiler, Visual Studio 'nun istemci dağıtımlarını iki ayrı komutlarla hiçbir Kullanıcı etkileşimi olmadan güncelleştirebilir:
  * İlk olarak, Visual Studio yükleyicisini güncelleştirin: <br>```vs_enterprise.exe --quiet --update```
  * Ardından, Visual Studio uygulamasını güncelleştirin: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" --quiet --wait --norestart```

::: moniker-end

> [!NOTE]
> Bir istemci makinesinde var olan bir Visual Studio örneğinin yüklemesinin yolunu tanımlamak için [vswhere.exe komutunu](tools-for-managing-visual-studio-instances.md) kullanın.
>
> [!TIP]
> Güncelleştirme bildirimlerinin kullanıcılara ne zaman sunulduğunu denetleme hakkında daha fazla bilgi için bkz. [ağ tabanlı Visual Studio dağıtımlarında güncelleştirmeleri denetleme](controlling-updates-to-visual-studio-deployments.md).

## <a name="verify-a-layout"></a>Bir düzeni doğrulama

`--verify`Sağlanan çevrimdışı önbellekte doğrulama gerçekleştirmek için kullanın. Paket dosyalarının eksik ya da geçersiz olup olmadığını denetler. Doğrulamanın sonunda, eksik dosyaların ve geçersiz dosyaların listesini yazdırır.

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

Her bir "GUID" klasörünün içine birkaç dosya kaydedilir. En çok ilgilendiğiniz iki dosya bir "catalog.json" dosyası ve "version.txt" dosyasıdır. "catalog.json" dosyası, seçeneğe geçirmeniz gereken eski Katalog bildirimidir `--clean` . Diğer version.txt dosyası, bu kullanımdan kaldırılmış Katalog bildiriminin sürümünü içerir. Sürüm numarasına bağlı olarak, eski paketleri bu katalog bildiriminden kaldırmak isteyip istemediğinize karar verebilirsiniz. Diğer "GUID" klasörlerinde ilerlerinizle aynı şekilde yapabilirsiniz. Temizlemek istediğiniz katalogda karar verdikten sonra, `--clean` Bu kataloglara dosya yollarını sağlayarak komutunu çalıştırın.

--Clean seçeneğinin nasıl kullanılacağına ilişkin birkaç örnek aşağıda verilmiştir:

```cmd
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> <file-path-of-catalog2> …
```

```cmd
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> --clean <file-path-of-catalog2> …
```

Ayrıca, layoutdir içinde vs_enterprise.exe çağırabilirsiniz &lt; &gt; . Aşağıda bir örnek verilmiştir:

```cmd
c:\VSLayout\vs_enterprise.exe --layout c:\VSLayout --clean c:\VSLayout\Archive\1cd70189-fc55-4583-8ad8-a2711e928325\Catalog.json --clean c:\VS2017Layout\Archive\d420889f-6aad-4ba4-99e4-ed7833795a10\Catalog.json
```

Bu komutu çalıştırdığınızda, kurulum, kaldıracağız dosyaların listesini bulmak için çevrimdışı önbellek klasörünüzü analiz eder. Daha sonra silinecek dosyaları gözden geçirebilir ve silme işlemlerini onaylamanız şansınız olur.

## <a name="get-support-for-your-offline-installer"></a>Çevrimdışı yükleyicinizin desteğini alın

Çevrimdışı yüklemenizde bir sorunla karşılaşırsanız bunun hakkında bilgi sahibi olmak istiyoruz. Bize anlatmak için en iyi yol, [sorun bildir](../ide/how-to-report-a-problem-with-visual-studio.md) aracını kullanmaktır. Bu aracı kullandığınızda sorunu tanılamanıza ve gidermenize yardımcı olması için ihtiyacımız olan telemetri ve günlükleri bize gönderebilirsiniz.

Ayrıca, yüklemeyle ilgili sorunlar için [**canlı sohbet**](https://visualstudio.microsoft.com/vs/support/#talktous) (yalnızca İngilizce) destek seçeneği sunuyoruz.

Diğer destek seçenekleri de mevcuttur. Bir liste için bkz. [geri bildirim](../ide/feedback-options.md) sayfamız.

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yu yükleme](install-visual-studio.md)
* [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
* [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio örneklerini algılamaya ve yönetmeye yönelik araçlar](tools-for-managing-visual-studio-instances.md)
* [Ağ tabanlı Visual Studio dağıtımlarında güncelleştirmeleri denetleme](controlling-updates-to-visual-studio-deployments.md)
* [Visual Studio ürün yaşam döngüsü ve bakım](/visualstudio/releases/2019/servicing/)
