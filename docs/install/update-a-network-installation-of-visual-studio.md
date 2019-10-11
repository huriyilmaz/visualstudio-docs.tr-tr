---
title: Ağ tabanlı yüklemeyi güncelleştirme
description: Kullanarak ağ tabanlı bir Visual Studio yüklemesini güncelleştirme öğrenin Düzen komutu
ms.date: 10/07/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 1AF69C0E-0AC9-451B-845D-AE4EDBCEA65C
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 2157a6142f95b6ffe34503a8ee80419fcb9ca506
ms.sourcegitcommit: 535ef05b1e553f0fc66082cd2e0998817eb2a56a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72018818"
---
# <a name="update-a-network-based-installation-of-visual-studio"></a>Visual Studio’nun ağ tabanlı yüklemesini güncelleştirme

Bunu mümkün olması için bir ağ yükleme düzeni, Visual Studio'nun en son ürün güncelleştirmelerini ile güncelleştirmek için bir yükleme noktası olarak hem de en son güncelleştirmesi Visual Studio ve ayrıca istemciye zaten dağıtılmış olan yüklemeleri korumak için kullandı İş istasyonu.

## <a name="how-to-update-a-network-layout"></a>Bir ağ düzeni güncelleştirme

Ağ yükleme paylaşımınızı en son güncelleştirmeleri içerecek şekilde yenilemek için, güncelleştirilmiş paketleri artımlı olarak indirmek üzere `--layout` komutunu çalıştırın.

::: moniker range="vs-2017"

**15,3 sürümündeki yenilikler**: İlk ağ düzeni oluşturduğunuz sırada kısmi bir düzen seçtiyseniz, bu ayarlar kaydedilir. Gelecekteki Düzen komutları, önceki seçeneklerinin yanı sıra, belirttiğiniz yeni seçenekleri kullanın. Ancak önceki bir sürümün bir yerleşimini kullanıyorsanız, içeriğini güncelleştirmek için ağ yüklemesi yerleşimini (diğer bir deyişle, aynı iş yüklerini ve dilleri) ilk oluşturduğunuzda kullandığınız komut satırı parametrelerinin aynısını kullanmanız gerekir.

::: moniker-end

::: moniker range="vs-2019"

İlk ağ düzeni oluşturduğunuz sırada kısmi bir düzen seçtiyseniz, bu ayarlar kaydedilir. Gelecekteki Düzen komutları, önceki seçeneklerinin yanı sıra, belirttiğiniz yeni seçenekleri kullanın.

::: moniker-end

Bir dosya paylaşımında bir düzen barındırdıysanız, düzenin özel bir kopyasını (örneğin, c:\VSLayout) güncelleştirmeniz gerekir ve ardından tüm güncelleştirilmiş içerik indirildikten sonra dosyayı dosya paylaşımınıza kopyalayın (örneğin, \\Server \ Products \ VS). Bunu yapmazsanız, Düzen güncelleştirildiği sırada Kurulum'u tüm kullanıcılar, henüz tamamen güncelleştirilmez tüm içeriğin elde düzenden mümkün olmayabilir, büyük bir olasılık yoktur.

Bir düzeni oluşturma ve güncelleştirme hakkında birkaç örnek adım adım inceleyelim:

* İlk olarak, yalnızca İngilizce için bir düzen ile bir iş yükü oluşturmak nasıl bir örnek aşağıdadır:

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
  ```

* Bu aynı düzen yeni bir sürüme güncelleştirmek açıklanmıştır. Herhangi bir ek komut satırı parametrelerini belirtmeniz gerekmez. Önceki ayarları kaydedildi ve bu düzen klasördeki herhangi bir sonraki Düzen komut tarafından kullanılacak.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout
  ```

* Düzeninizi katılımsız bir şekilde yeni bir sürüme güncelleştirmek açıklanmıştır. Düzen işlemi yeni bir konsol penceresi Kurulum işlemi çalıştırır. Kullanıcılar, nihai sonucu ve ortaya çıkan hataları özetini görebilmeniz için penceresi açık kalır. Katılımsız bir şekilde bir düzen işlemi gerçekleştiriyorsanız varsa (örneğin, en son sürüme düzeninizi güncelleştirmek için düzenli olarak çalışan bir betik varsa), ardından `--passive` parametresi ve işlem otomatik olarak kapatılır penceresi.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --passive
  ```

* Bir ek iş yükü ve yerelleştirilmiş dilini nasıl ekleneceğini aşağıda verilmiştir.  (Bu komut *Azure geliştirme* iş yükünü ekler.)  Artık hem yönetilen Masaüstü hem de Azure Bu düzende dahil edilir.  İngilizce ve Almanca dil kaynakları için bu iş yükleri de dahildir.  Ve düzeni, kullanılabilir en son sürüme güncelleştirilir.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
  ```

    > [!IMPORTANT]
    > Bir güncelleştirme işlemi, bir [yanıt dosyasının](automated-installation-with-response-file.md)"Ekle" bölümüne bu bileşenleri dahil etseniz bile yeni eklenen isteğe bağlı bileşenleri yüklemez. Bu durum, bir güncelleştirme sırasında ekleme işlemi kullanılmadığından oluşur.
    >
    > **Geçici çözüm**: Eksik bileşenleri yüklemek için yükseltmeden sonra ayrı bir değiştirme işlemi çalıştırın.

* Son olarak, burada da bir ek iş yükü ve yerelleştirilmiş dil sürümü güncelleştirmeden ekleme. (Bu komut *ASP.net ve Web geliştirme* iş yükünü ekler.)  Artık yönetilen Masaüstü, Azure ve ASP.NET & Web geliştirme iş yükleri bu düzene dahildir. İngilizce, Almanca ve Fransızca Dil kaynakları için bu iş yükleri de dahildir.  Ancak, bu komutu çalıştırdığınızda düzenini kullanılabilir en son sürüme güncelleştirilmedi. Bu, mevcut sürümde kalır.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.NetWeb --lang fr-FR --keepLayoutVersion
  ```

## <a name="how-to-deploy-an-update-to-client-machines"></a>İstemci makineler için bir güncelleştirme dağıtma

Ağ ortamınızı nasıl yapılandırıldığına bağlı olarak, bir güncelleştirme bir kurumsal yönetici tarafından dağıtılan veya bir istemci makinesinden başlattı.

* Kullanıcılar bir çevrimdışı yükleme klasöründen yüklü olduğu bir Visual Studio örneği güncelleştirebilirsiniz:
  * Visual Studio Yükleyicisi'ni çalıştırın.
  * ' A tıklayarak **güncelleştirme**.

::: moniker range="vs-2017"

* Yöneticiler, Visual Studio'nun istemci dağıtımlarını iki ayrı komutlar içeren herhangi bir kullanıcı etkileşimi olmadan güncelleştirebilirsiniz:
  * İlk olarak, Visual Studio Yükleyicisi güncelleştirmesi: <br>```vs_enterprise.exe --quiet --update```
  * Ardından, Visual Studio uygulamasını güncelleştirin: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" --quiet --wait --norestart```

::: moniker-end

::: moniker range="vs-2019"

* Yöneticiler, Visual Studio'nun istemci dağıtımlarını iki ayrı komutlar içeren herhangi bir kullanıcı etkileşimi olmadan güncelleştirebilirsiniz:
  * İlk olarak, Visual Studio Yükleyicisi güncelleştirmesi: <br>```vs_enterprise.exe --quiet --update```
  * Ardından, Visual Studio uygulamasını güncelleştirin: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" --quiet --wait --norestart```

::: moniker-end

> [!NOTE]
> Kullanım [vswhere.exe komut](tools-for-managing-visual-studio-instances.md) istemci makinede mevcut bir Visual Studio örneğini yükleme yolunu tanımlamak için.
>
> [!TIP]
> Güncelleştirme bildirimleri kullanıcılara sunulduğundan zaman denetleme hakkında daha fazla bilgi için bkz: [ağ tabanlı Visual Studio dağıtımlarına yönelik güncelleştirmeleri denetlemek](controlling-updates-to-visual-studio-deployments.md).

## <a name="how-to-verify-a-layout"></a>Bir düzen doğrulama

Kullanım `--verify` sağlanan çevrimdışı önbellekte doğrulama gerçekleştirmek için. Eksik veya geçersiz paketleri dosyaları olup olmadığını denetler. Doğrulama sonunda eksik dosyalar ve geçersiz dosyaların listesini yazdırır.

```cmd
vs_enterprise.exe --layout <layoutDir> --verify
```

İçinde layoutDir vs_enterprise.exe çağrılabilir.

> [!NOTE]
> Tarafından gereken bazı önemli meta veri dosyaları `--verify` seçeneği Düzen çevrimdışı önbellekte olması gerekir. Bu meta veri dosyaları eksikse "--doğrulayın" çalıştırılamıyor ve Kurulum bir hata verir. Bu hata ile karşılaşırsanız, yeni bir çevrimdışı Düzen farklı bir klasöre (veya aynı Çevrimdışı Önbellek klasörü. yeniden oluştur Bu nedenle yapmak için ilk çevrimdışı düzen oluşturmak için kullandığınız aynı düzen komutu çalıştırın. Örneğin: `vs_enterprise.exe --layout <layoutDir>`

Oluşturduğunuz yeni düzene ilk düzeni sürümünün aynı olmayabilir bu nedenle, Microsoft Visual Studio güncelleştirmeleri düzenli olarak gelir.

> [!NOTE]
> Doğrulama yalnızca Visual Studio 'nun belirli bir ikincil sürümünün en son sürümü için geçerlidir. Yeni bir sürüm yayımlandığında, doğrulama işlemi, aynı ikincil sürümün önceki düzeltme eki düzeyi sürümleri için çalışmaz.

## <a name="how-to-fix-a-layout"></a>Bir düzen nasıl

Kullanım `--fix` olarak aynı doğrulamanın `--verify` ve bilinen sorunları düzeltmek de deneyin. @No__t-0 işlemi bir internet bağlantısına ihtiyaç duyuyor, bu nedenle `--fix` ' i çağırmadan önce makinenizin internet 'e bağlı olduğundan emin olun.

```cmd
vs_enterprise.exe --layout <layoutDir> --fix
```

İçinde layoutDir vs_enterprise.exe çağrılabilir.

## <a name="how-to-remove-older-versions-from-a-layout"></a>Bir düzenden eski sürümlerini kaldırma

Çevrimdışı bir önbellek için Düzen güncelleştirmeleri gerçekleştirdikten sonra Düzen önbellek klasörünün en son Visual Studio yüklemesinin artık gerekli olmayan bazı eski paketleri olabilir. Kullanabileceğiniz `--clean` seçeneği bir Çevrimdışı Önbellek klasör'den eski paketleri kaldırın.

Bunu yapmak için bu eski paketleri içeren katalog manifest(s) için dosya yolu gerekir. Çevrimdışı Düzen önbellek "Arşiv" klasöründe Kataloğu bildirimlerini bulabilirsiniz. Bir düzen güncelleştirdiğinizde var. kaydedilir. "Arşiv" klasöründe, "her biri bir eski katalog bildirimi içeren klasörleri adlı bir veya daha fazla GUID" yoktur. "GUID" klasörlerin sayısı çevrimdışı önbelleğinizi yapılan güncelleştirmelerin sayısı ile aynı olması gerekir.

Bazı dosyalar her "GUID" klasöründen kaydedilir. Çoğu ilgilenilen iki dosyalar "catalog.json" dosyası ve bir "version.txt" dosyası olur. "Catalog.json" dosyası için geçmesi gereken eski katalog bildirimidir `--clean` seçeneği. Bu eski katalog bildiriminin sürümü diğer version.txt dosyası içerir. Sürüm sayısına göre eski paketleri bu katalog bildiriminden kaldırmak isteyip istemediğinize karar verebilirsiniz. Diğer "GUID" klasörlerde kullandıkça da aynısını yapabilir. Katalogları üzerinde karar yaptıktan sonra istediğiniz temizlemek çalıştırın `--clean` sağlayarak bu katalog dosyaları yolları tarafından komutu.

İşte birkaç örnek nasıl kullanılacağı hakkında temiz seçeneği:

```cmd
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> <file-path-of-catalog2> …
```

```cmd
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> --clean <file-path-of-catalog2> …
```

İçinde vs_enterprise.exe de çağırabilirsiniz &lt;layoutDir&gt;. Örnek buradadır:

```cmd
c:\VSLayout\vs_enterprise.exe --layout c:\VSLayout --clean c:\VSLayout\Archive\1cd70189-fc55-4583-8ad8-a2711e928325\Catalog.json --clean c:\VS2017Layout\Archive\d420889f-6aad-4ba4-99e4-ed7833795a10\Catalog.json
```

Kurulum, bu komutu yürüttükten sonra onu kaldırır dosyaların listesini bulmak için Çevrimdışı Önbellek klasörü analiz eder. Ardından, silinecek ve silme onayı yükleneceği dosyalarını gözden geçirmek için bir fırsat gerekir.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yu yükleyin](install-visual-studio.md)
* [Visual Studio Yönetici Kılavuzu](visual-studio-administrator-guide.md)
* [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio örneklerini algılamaya ve yönetmeye yönelik araçlar](tools-for-managing-visual-studio-instances.md)
* [Ağ tabanlı Visual Studio dağıtımlarına yönelik güncelleştirmeleri denetleme](controlling-updates-to-visual-studio-deployments.md)
* [Visual Studio ürün yaşam döngüsü ve bakım](/visualstudio/releases/2019/servicing/)
