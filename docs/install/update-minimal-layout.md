---
title: En düşük düzeyde çevrimdışı düzen kullanarak Visual Studio'yu güncelleştirme
description: Minimum çevrimdışı düzen Visual Studio güncelleştirme hakkında bilgi alın.
ms.date: 05/18/2021
ms.topic: how-to
ms.assetid: ''
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: ceb9094d303bc1cd1409338d4d7987248e6c2d1e
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129967892"
---
# <a name="update-visual-studio-using-a-minimal-offline-layout"></a>En düşük düzeyde çevrimdışı düzen kullanarak Visual Studio'yu güncelleştirme

İnternet'e bağlı olan bilgisayarlar için minimum düzen oluşturmak, çevrimdışı örneklerinizi güncelleştirmenin en kolay ve en Visual Studio yöntemdir.

En düşük düzen aracı, takımınıza özel olarak uyarlanmış bir düzen üretir. Enterprise yöneticileri bu aracı kullanarak 2017 ve 2019'Visual Studio sürümleri için güncelleştirme düzenleri oluşturabilir. Tam bir Visual Studio aksine, minimum düzen yalnızca güncelleştirilmiş paketleri içerir, bu nedenle oluşturma ve dağıtma her zaman daha küçük ve daha hızlıdır. Yalnızca istenen dilleri, iş yüklerini ve bileşenleri belirterek güncelleştirme düzeninin boyutunu daha da küçültebilirsiniz.

## <a name="how-to-generate-a-minimal-layout"></a>Minimum düzen oluşturma

> [!IMPORTANT]
> Bu yönergelerde, daha önce düzen oluşturduğunuz ve bunları kullandığı varsayılanlar vardır. Bunun nasıl olduğu hakkında daha fazla bilgi için Ağ [tabanlı yüklemesini güncelleştirme Visual Studio](update-a-network-installation-of-visual-studio.md) bakın.
>
> Uygulama yaşam döngüsünü daha iyi Visual Studio için Ürün Yaşam [Döngüsü Visual Studio Bakım sayfasına](/visualstudio/releases/2019/servicing) bakın.
>

Bu araç, Visual Studio 2017 (15.9) ve sonrası için güncelleştirme düzenleri oluşturur. Düzen, örneklerde güncelleştirme yapmak için ağ/çevrimdışı Visual Studio dağıtılabilir. Normal [düzen oluşturma sırasında,](update-a-network-installation-of-visual-studio.md)bu sürüm için tüm paketler indirilir. Örneklerde onarım, kaldırma ve diğer standart işlemler için normal düzen Visual Studio gerekir. En düşük düzen yalnızca güncelleştirilmiş paketleri indirdiği için çevrimdışı makinelere daha küçük ve daha kolay kopyalayabilirsiniz.

### <a name="installing-the-minimal-layout-tool"></a>En düşük düzen aracını yükleme

 1. İlk olarak, burada bulunan en düşük düzen aracını [indirin.](https://aka.ms/vs/installer/minimallayout) İstendiğinde **Kaydet'i ve** ardından Çalıştır'ı seçin.

     ![En az düzen aracını kaydetme](media/save-minimal-layout.png)

 2. Ardından, Evet'e tıklayarak Kullanıcı Hesabı Denetimi istemini kabul **et.**

     ![Kullanıcı hesabı denetimi kabul etme](media/accept-user-account-control.png)

 3. En düşük düzen aracı sürümüne `C:\Program Files (x86)\Microsoft Visual Studio\MinimalLayout` yüklenir.

### <a name="how-to-use-the-minimal-layout-tool"></a>En düşük düzen aracını kullanma

`MinimalLayout.exe` düzeni oluşturmak için aşağıdaki komutları ve seçenekleri kullanır. Aracı çalıştırmak için en az bir komut gerekir. Aracı şu şekilde çalıştırabilirsiniz:

```MinimalLayout.exe [command] <options>...```

#### <a name="commands"></a>Komutlar

* **Önizleme:** Kaç paketin indireceklerini ve bu düzeni oluşturmak için kullanılan toplam alanı önizlemek için bu komutu kullanın.
* **Oluştur:** Bu komutu kullanarak güncelleştirme için en düşük düzeni Visual Studio.
* **Yeniden oluştur:** Mevcut en düşük düzen yanıt dosyasını kullanarak bir düzeni yeniden oluşturma için bu komutu kullanın. Her minimal düzen, `MinimalLayout.json` özgün en az düzen giriş parametrelerini içeren bir yanıt dosyası üretir. En düşük düzeni **yeniden oluşturma için** Yeniden Oluştur komutunu ve yanıt dosyasını `MinimalLayout.json` kullanabilirsiniz. Bu, önceki en az düzenin yanıt dosyasına göre yeni bir Visual Studio güncelleştirmesi için en düşük düzen oluşturmak istediğinizde kullanışlıdır.

   Bu komut için, `MinimalLayout.json` önceden oluşturulmuş bir düzenden bir dosya yolu gereklidir.

   ```shell
   MinimalLayout.exe regenerate --filePath C:\MinimalLayout\MinimalLayout.json
   ```

* **Doğrulama:** Düzen klasörünün bozuk olup olmadığını belirlemek için bu komutu kullanın.
* **Düzeltme:** Düzen klasöründeki eksik paketleri değiştirmek de dahil olmak üzere bozuk bir düzen klasörünü düzeltmek için bu komutu kullanın.

#### <a name="options"></a>Seçenekler

::: moniker range=">=vs-2019"

| Seçenekler                                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                 | Gerekli/İsteğe Bağlı               | Örnek                                                                                                                                                          |
|-----------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| --targetLocation &lt; dir&gt;                        | En düşük çevrimdışı düzenin oluşturularak bir dizin belirtir.                                                                                                                                                                                                                                                                                                                                                                          | Gerekli                        | --targetLocation c:\VSLayout\                                                                                                                                    |
| --baseVersion &lt; sürümü&gt;                       | Bu sürümden başlayarak en düşük çevrimdışı düzen oluşturulacak.                                                                                                                                                                                                                                                                                                                                                                    | Gerekli                        | --baseVersion 16.4.0                                                                                                                                             |
| --targetVersion &lt; sürümü&gt;                     | Bu sürüme kadar ve bu sürüm dahil olmak üzere en düşük çevrimdışı düzen oluşturulur.                                                                                                                                                                                                                                                                                                                                                              | Gerekli                        | --targetVersion 16.4.4                                                                                                                                           |
| --languages                                         | En düşük çevrimdışı düzende yer alan dilleri belirtir. Boşluklarla ayırarak birden çok değer belirtilebilir.                                                                                                                                                                                                                                                                                                                    | Gerekli                        | --languages en-US fr-FR                                                                                                                                          |
| --productIds &lt; bir veya daha fazla ürün kimlikleri&gt;        | Minimum çevrimdışı düzenin oluşturulacak ürün veya ürün kimlikleri virgülle ayrılmıştır. <br> <ul><li>Microsoft.VisualStudio.Product. Enterprise</li><li>Microsoft.VisualStudio.Product. Professional</li><li>Microsoft.VisualStudio.Product.BuildTools</li><li>Microsoft.VisualStudio.Product.TestAgent</li><li>Microsoft.VisualStudio.Product.TestController</li><li>Microsoft.VisualStudio.Product.TeamExplorer</li></ul> | Gerekli                        | --productIds Microsoft.VisualStudio.Product. Enterprise.Microsoft.VisualStudio.Product. Professional                                                               |
| --filePath                                          | Önceden oluşturulmuş bir düzenden MinimalLayout.json dosyasının dosya yolu. Bu seçenek yalnızca Yeniden Oluştur komutuyla kullanılır.                                                                                                                                                                                                                                                                                                          | Yeniden Oluştur komutu için gereklidir | --filePath C:\VSLayout\minimalLayout.json <br><br> **Yeniden Oluştur komutunun yalnızca --filePath'i bir seçenek olarak kabul gördüğünü unutmayın.**                                      |
| --bir &lt; veya daha fazla iş yükü veya bileşen kimlikleri ekleyin&gt; | Eklenecek bir veya daha fazla iş yükünü veya bileşen kimliklerini belirtir. --includeRecommended ve/veya kullanılarak genel olarak ek bileşenler eklenebilir <br> –-includeOptional. Boşlukla ayırarak birden çok iş yükü veya bileşen kimlikleri belirtilebilir.                                                                                                                                                                                                   | İsteğe Bağlı                        | --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb Bileşeni. GitHub. VisualStudio                                        |
| --includeRecommended                                | Yüklü olan tüm iş yükleri için önerilen bileşenleri içerir, ancak isteğe bağlı bileşenleri dahil değildir.                                                                                                                                                                                                                                                                                                                                  | İsteğe Bağlı                        | Belirli bir iş yükü için: <br> --microsoft.VisualStudio.workload ekleyin. ManagedDesktop;includeRecommended <br><br> Tüm iş yüklerini uygulamak için: --includeRecommended |
| --includeOptional                                   | Önerilen bileşenler de dahil olmak üzere yüklü tüm iş yükleri için isteğe bağlı bileşenleri içerir.                                                                                                                                                                                                                                                                                                                                | İsteğe Bağlı                        | Belirli bir iş yükü için: <br>--microsoft.VisualStudio.workload ekleyin. ManagedDesktop;includeOptional <br><br> Tüm iş yüklerini uygulamak için: --includeOptional         |

::: moniker-end

::: moniker range="vs-2017"

| Seçenekler                                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                 | Gerekli/İsteğe Bağlı               | Örnek                                                                                                                                                          |
|-----------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| --targetLocation &lt; dir&gt;                        | En az bir çevrimdışı düzen oluşturulacağı dizini belirtir.                                                                                                                                                                                                                                                                                                                                                                          | Gerekli                        | --targetLocation c:\VSLayout\                                                                                                                                    |
| --baseVersion &lt; sürümü&gt;                       | Bu sürümle başlayarak en az çevrimdışı düzen oluşturulacaktır.                                                                                                                                                                                                                                                                                                                                                                    | Gerekli                        | --baseVersion 'sının 15.0.0                                                                                                                                             |
| --targetVersion &lt; sürümü&gt;                     | En az çevrimdışı düzen, bu sürüm dahil olmak üzere en çok ve dahil oluşturulacak.                                                                                                                                                                                                                                                                                                                                                              | Gerekli                        | --targetVersion 15.9.31                                                                                                                                          |
| --Diller                                         | En az çevrimdışı düzene dahil edilecek dilleri belirtir. Boşluklarla ayırarak birden çok değer belirtilebilir.                                                                                                                                                                                                                                                                                                                    | Gerekli                        | --Diller en-US fr-FR                                                                                                                                          |
| -- &lt; bir veya daha fazla ürün kimliği Ile ProductIDs&gt;        | En az çevrimdışı düzenin oluşturulacağı, virgülle ayırarak oluşturulan ürünlerin KIMLIĞI (öğeleri). <br> <ul><li>Microsoft. VisualStudio. Product. Enterprise</li><li>Microsoft. VisualStudio. Product. Professional</li><li>Microsoft. VisualStudio. Product. BuildTools</li><li>Microsoft. VisualStudio. Product. TestAgent</li><li>Microsoft. VisualStudio. Product. TestController</li><li>Microsoft. VisualStudio. Product. TeamExplorer</li></ul> | Gerekli                        | --ProductIDs Microsoft. VisualStudio. Product. Enterprise, Microsoft. VisualStudio. Product. Professional                                                               |
| --filePath                                          | Zaten oluşturulmuş bir düzenden en az Allayout. json dosyasının dosya yolu. Bu seçenek yalnızca yeniden oluştur komutuyla kullanılır.                                                                                                                                                                                                                                                                                                          | Yeniden oluştur komutu için gerekli | --filePath C:\vslayout\minimallayout,JSON <br><br> **Yeniden oluştur komutunun yalnızca bir seçenek olarak--filePath aldığını unutmayın.**                                      |
| -- &lt; bir veya daha fazla iş yükü veya Bileşen kimliği ekleyin&gt; | Eklenecek bir veya daha fazla iş yükünü veya bileşen kimliğini belirtir. Ek bileşenler,--ıncludereyorumded ve/veya kullanılarak genel olarak eklenebilir <br> –-includeOptional. Birden çok iş yükü veya Bileşen kimliği, boşlukla ayrılmış olarak belirtilebilir.                                                                                                                                                                                                   | İsteğe Bağlı                        | --Microsoft. VisualStudio. Workload. ManagedDesktop Microsoft. VisualStudio. Workload. NetWeb bileşenini ekleyin. GitHub. VisualStudio                                        |
| --ıncludereyorumded                                | , Yüklü olan, ancak isteğe bağlı bileşenleri olmayan tüm iş yükleri için önerilen bileşenleri içerir.                                                                                                                                                                                                                                                                                                                                  | İsteğe Bağlı                        | Belirli bir iş yükü için: <br> --Microsoft. VisualStudio. Workload ekleyin. ManagedDesktop; ıncludereyorum <br><br> Tüm iş yüklerine uygulamak için:--ıncludereyorumded |
| --IncludeOptional                                   | , Önerilen bileşenler dahil olmak üzere yüklü olan tüm iş yükleri için isteğe bağlı bileşenleri içerir.                                                                                                                                                                                                                                                                                                                                | İsteğe Bağlı                        | Belirli bir iş yükü için: <br>--Microsoft. VisualStudio. Workload ekleyin. ManagedDesktop; IncludeOptional <br><br> Tüm iş yüklerine uygulamak için:--includeOptional         |

::: moniker-end

### <a name="generating-a-minimal-layout"></a>En az düzen oluşturma

> [!IMPORTANT]
> Bu yönergelerde, daha önce bir ağ yükleme düzeni oluşturmuş olduğunuz varsayılır. bunun nasıl yapılacağı hakkında daha fazla bilgi için [Visual Studio ağ yüklemesi oluşturma](create-a-network-installation-of-visual-studio.md) sayfasına bakın.

Belirtilen sürüm aralığınızı oluşturmak için **Oluştur** komutunu kullanarak en az bir düzen oluşturun. Ayrıca ProductID, Languages ve gereken belirli iş yüklerini bilmeniz gerekir. bu en az düzen, temel sürümden hedef sürüm dahil olmak üzere tüm Visual Studio örneklerini güncelleyecek.

Düzeni oluşturmadan önce, indirmenin toplam boyutunu ve **Önizleme** komutu kullanılarak dahil edilen paket sayısını bulabilirsiniz. Bu komut, **Oluştur** komutuyla aynı seçenekleri alır ve Ayrıntılar konsola yazılır.

En az bir düzeni önizleme, oluşturma ve yeniden oluşturma hakkında birkaç örnek adım adım inceleyelim:

::: moniker range=">=vs-2019"

* ilk olarak, 16.4.0 sürümleri için bir düzenin yalnızca ingilizce için nasıl önizlemesinin Visual Studio Enterprise bir örneği aşağıda verilmiştir.

  ```shell
  MinimalLayout.exe preview --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --languages en-US
  ```

* Aynı düzeni bir iş yüküyle nasıl oluşturabileceğiniz aşağıda açıklanmaktadır.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US
  ```

* İşte, var olan bir yanıt dosyasını kullanarak en az bir çevrimdışı düzeni yeniden üretme.

  ```shell
  MinimalLayout.exe regenerate -filepath c:\VSLayout\MinimalLayout.json
  ```

**Generate** komutunu kullanan birkaç örnek aşağıda verilmiştir:

* Ek bir iş yükü ekleme ve yalnızca önerilen paketleri ekleme.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Professional --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb;includeRecommended --languages en-US
  ```

* Birden çok ürünü destekleyen, en az bir çevrimdışı düzen de oluşturabilirsiniz.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise,Microsoft.VisualStudio.Product.Professional --baseVersion 16.4.0 --targetVersion 16.4.4 --languages en-US
  ```

* Son olarak, en az düzeninizde birden çok dili nasıl dahil edeceğiniz aşağıda bulabilirsiniz.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US fr-FR
  ```

::: moniker-end

::: moniker range="vs-2017"

* ilk olarak, 'sının 15.0.0 sürümleri için bir düzenin yalnızca ingilizce için nasıl önizlemesinin Visual Studio Enterprise bir örneği aşağıda verilmiştir.

  ```shell
  MinimalLayout.exe preview --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --languages en-US
  ```

* Aynı düzeni bir iş yüküyle nasıl oluşturabileceğiniz aşağıda açıklanmaktadır.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US
  ```

* İşte, var olan bir yanıt dosyasını kullanarak en az bir çevrimdışı düzeni yeniden üretme.

  ```shell
  MinimalLayout.exe regenerate -filepath c:\VSLayout\MinimalLayout.json
  ```

**Generate** komutunu kullanan birkaç örnek aşağıda verilmiştir:

* Ek bir iş yükü ekleme ve yalnızca önerilen paketleri ekleme.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Professional --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb;includeRecommended --languages en-US
  ```

* Birden çok ürünü destekleyen, en az bir çevrimdışı düzen de oluşturabilirsiniz.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise,Microsoft.VisualStudio.Product.Professional --baseVersion 15.0.0 --targetVersion 15.9.31 --languages en-US
  ```

* Son olarak, en az düzeninizde birden çok dili nasıl dahil edeceğiniz aşağıda bulabilirsiniz.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US fr-FR
  ```

::: moniker-end

### <a name="how-to-maintain-a-minimal-layout"></a>En az bir düzen koruma

Oluşturulduktan sonra en az düzeninizi sürdürmek için **doğrulama** ve **çözme** komutlarını kullanın. **Verify** komutu, en az düzende bozuk veya eksik paketler olup olmadığını belirler. **Verify** komutunu çalıştırdıktan sonra herhangi bir sorunla karşılaşırsanız, eksik veya bozuk paketleri düzeltmek için **Düzelt** komutunu kullanın.

* Bir düzenin bozuk veya eksik paketlere sahip olup olmadığını doğrulamak için şu adımları uygulayın:

  ```shell
  MinimalLayout.exe Verify --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --languages en-US
  ```

* Bu düzenin nasıl düzeltileceğini aşağıda görebilirsiniz:

  ```shell
  MinimalLayout.exe fix --targetLocation C:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeRecommended --languages en-US
  ```

>[!NOTE]
> bu düzen Visual Studio yüklemesini onarmak için kullanılamaz. mevcut bir Visual Studio örneğini onarmak için bkz. [repair Visual Studio](repair-visual-studio.md).
>

### <a name="how-to-use-a-minimal-offline-layout-to-update-an-existing-installation-of-visual-studio"></a>Var olan bir Visual Studio yüklemesini güncelleştirmek için en az bir çevrimdışı düzen kullanma

En az bir düzen oluşturduktan sonra, en küçük düzen klasörünün tamamını bir istemci makinesine kopyalayabilirsiniz. Bilgisayarın özgün konumunda en düşük düzen klasörüne erişimi yoksa bu gereklidir.

Klasöre gidin ve önyükleyici uygulama adını tespit edin. Önyükleyici uygulamasının adı, en az düzen oluşturulurken belirtilen ProductID değerine bağlıdır. Ortak örnekler için aşağıdaki tabloya bakın.

| ProductID değeri                             | Uygulama adı    |
|---------------------------------------------|---------------------|
| Microsoft. VisualStudio. Product. Enterprise   | vs_enterprise.exe   |
| Microsoft. VisualStudio. Product. Professional | vs_professional.exe |
| Microsoft. VisualStudio. Product. BuildTools   | vs_buildtools.exe   |

Güncelleştirme, iki adımda Visual Studio örnek için uygulanır. Başlangıç olarak Visual Studio Yükleyicisi güncelleştirin ve sonra da Visual Studio.

::: moniker range="vs-2017"

1. **Güncelleştirme Visual Studio Yükleyicisi**

    Gerekirse doğru önyükleyici uygulama `vs_enterprise.exe`  adıyla değiştirin ve aşağıdaki komutu çalıştırın.

    ```shell
    vs_enterprise.exe --quiet --update --offline C:\VSLayout\vs_installer.opc
    ```

2. **Visual Studio güncelleştirme**

    Bu Visual Studio güncelleştirmek için, güncelleştirmek istediğiniz Visual Studio örneğinin installPath'ini belirtmeniz gerekir. Birden çok örnek Visual Studio, her birinin ayrı olarak güncelleştirilmiş olması gerekir. Minimum düzende olmayan `–noWeb` bileşenlerin yüklemesini önlemek için güncelleştirme komutuyla seçeneğini belirtmenizi kesinlikle öneririz. Bu, çalışmadan Visual Studio durumda bırakmasını sağlar.

    InstallPath komut satırı parametresini uygun şekilde değiştirarak aşağıdaki komutu çalıştırın. Doğru önyükleyici uygulama adını da kullanmaya emin olun.

    ```shell
    vs_enterprise.exe update --noWeb --quiet --installpath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise"
    ```

::: moniker-end

::: moniker range="vs-2019"

1. **Güncelleştirme Visual Studio Yükleyicisi**

    Gerekirse doğru önyükleyici uygulama `vs_enterprise.exe`  adıyla değiştirin ve aşağıdaki komutu çalıştırın.

    ```shell
    vs_enterprise.exe --quiet --update --offline C:\VSLayout\vs_installer.opc
    ```

2. **Visual Studio güncelleştirme**

    Bu Visual Studio güncelleştirmek için, güncelleştirmek istediğiniz Visual Studio örneğinin installPath'ini belirtmeniz gerekir. Birden çok örnek Visual Studio, her birinin ayrı olarak güncelleştirilmiş olması gerekir. Minimum düzende olmayan `–noWeb` bileşenlerin yüklemesini önlemek için güncelleştirme komutuyla seçeneğini belirtmenizi kesinlikle öneririz. Bu, çalışmadan Visual Studio durumda bırakmasını sağlar.

    InstallPath komut satırı parametresini uygun şekilde değiştirarak aşağıdaki komutu çalıştırın. Doğru önyükleyici uygulama adını da kullanmaya emin olun.

    ```shell
    vs_enterprise.exe update --noWeb --quiet --installpath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise"
    ```

::: moniker-end

::: moniker range=">=vs-2022"

1. **Güncelleştirme Visual Studio Yükleyicisi**

    Gerekirse doğru önyükleyici uygulama `vs_enterprise.exe`  adıyla değiştirin ve aşağıdaki komutu çalıştırın.

    ```shell
    vs_enterprise.exe --quiet --update --offline C:\VSLayout\vs_installer.opc
    ```

2. **Visual Studio güncelleştirme**

    Bu Visual Studio güncelleştirmek için, güncelleştirmek istediğiniz Visual Studio örneğinin installPath'ini belirtmeniz gerekir. Birden çok örnek Visual Studio, her birinin ayrı olarak güncelleştirilmiş olması gerekir. Minimum düzende olmayan `–noWeb` bileşenlerin yüklemesini önlemek için güncelleştirme komutuyla seçeneğini belirtmenizi kesinlikle öneririz. Bu, çalışmadan Visual Studio durumda bırakmasını sağlar.

    InstallPath komut satırı parametresini uygun şekilde değiştirarak aşağıdaki komutu çalıştırın. Doğru önyükleyici uygulama adını da kullanmaya emin olun.

    ```shell
    vs_enterprise.exe update --noWeb --quiet --installpath "C:\Program Files\Microsoft Visual Studio\2022\Enterprise"
    ```

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yu yükleme](install-visual-studio.md)
* [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
* [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio örneklerini algılamaya ve yönetmeye yönelik araçlar](tools-for-managing-visual-studio-instances.md)
* [Yanıt dosyasında ayarları tanımlama](automated-installation-with-response-file.md)
* [Ağ tabanlı dağıtımlarda güncelleştirmeleri Visual Studio denetleme](controlling-updates-to-visual-studio-deployments.md)
* [Visual Studio yaşam döngüsü ve bakım](/visualstudio/releases/2019/servicing/)
