---
title: En düşük düzeyde çevrimdışı düzen kullanarak Visual Studio'yu güncelleştirme
description: en düşük düzeyde çevrimdışı düzen kullanarak Visual Studio güncelleştirme hakkında bilgi edinin.
ms.date: 05/18/2021
ms.custom: seodec18
ms.topic: how-to
ms.assetid: ''
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 0cc014754a57eb719212341cab62a2912487bd53
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628455"
---
# <a name="update-visual-studio-using-a-minimal-offline-layout"></a>En düşük düzeyde çevrimdışı düzen kullanarak Visual Studio'yu güncelleştirme

internet 'e bağlı olmayan bilgisayarlar için, en az bir düzen oluşturmak, çevrimdışı Visual Studio örneklerinizi güncelleştirmenin en kolay ve en hızlı yoludur.

En küçük düzen Aracı, takımınızın ihtiyaçlarına özel olarak uyarlanmış bir düzen oluşturur. Enterprise yöneticiler bu aracı, Visual Studio 2017 ve 2019 için çoğu sürüm için güncelleştirme düzeni oluşturmak üzere kullanabilir. tam Visual Studio düzeninin aksine, en az bir düzen yalnızca güncelleştirilmiş paketleri içerir, bu nedenle oluşturmak ve dağıtmak için her zaman daha küçük ve daha hızlıdır. Yalnızca istediğiniz dilleri, iş yüklerini ve bileşenleri belirterek güncelleştirme düzeninin boyutunu daha da en aza indirgeyin.

## <a name="how-to-generate-a-minimal-layout"></a>En az bir düzen oluşturma

> [!IMPORTANT]
> Bu yönergelerde, düzenleri daha önce oluşturduğunuz ve kullandığınız varsayılır. bunun nasıl yapılacağı hakkında daha fazla bilgi için [Visual Studio ağ tabanlı yüklemesini güncelleştirme](update-a-network-installation-of-visual-studio.md) sayfasına bakın.
>
> Visual Studio yaşam döngüsünü daha iyi anlamak için bkz. [Visual Studio ürün yaşam döngüsü ve bakım](/visualstudio/releases/2019/servicing) sayfası.
>

bu araç Visual Studio 2017 (15,9) ve sonraki sürümler için güncelleştirme düzenleri oluşturur. düzen, Visual Studio örnekleri güncelleştirmek için ağ/çevrimdışı makinelere dağıtılabilir. [Normal düzen oluşturma](update-a-network-installation-of-visual-studio.md)sırasında, söz konusu sürümün tüm paketleri indirilir. Visual Studio örneklerine yönelik onarım, kaldırma ve diğer standart işlemler için Normal düzen oluşturma gereklidir. En küçük düzen yalnızca güncelleştirilmiş paketleri indirir, bu nedenle çevrimdışı makinelere kopyalamak daha küçüktür ve daha kolay olur.

### <a name="installing-the-minimal-layout-tool"></a>En az düzen aracını yükleme

 1. İlk olarak, [burada](https://aka.ms/vs/installer/minimallayout)bulunan en az düzen aracını indirin. İstendiğinde **Kaydet** ' i seçtiğinizden emin olun ve **Çalıştır**' ı seçin.

     ![En az düzen aracını Kaydet](media/save-minimal-layout.png)

 2. Ardından, **Evet**' i tıklatarak Kullanıcı hesabı denetim istemi 'ni kabul edin.

     ![Kullanıcı hesabı denetimini kabul et](media/accept-user-account-control.png)

 3. En küçük düzen Aracı ' e yüklenir `C:\Program Files (x86)\Microsoft Visual Studio\MinimalLayout` .

### <a name="how-to-use-the-minimal-layout-tool"></a>En az düzen aracını kullanma

`MinimalLayout.exe` düzeni oluşturmak için aşağıdaki komutları ve seçenekleri kullanır. Aracı çalıştırmak için en az bir komut gereklidir. Aracı nasıl çalıştıracağınızı aşağıda bulabilirsiniz:

```MinimalLayout.exe [command] <options>...```

#### <a name="commands"></a>Komutlar

* **Önizleme**: kaç paketin indirileceği ve bu düzeni oluşturmak için kullanılan toplam alanın önizlemesi için bu komutu kullanın.
* **Oluştur**: güncelleştirme Visual Studio için en az düzeni oluşturmak için bu komutu kullanın.
* Yeniden **Oluştur**: var olan en az düzen yanıt dosyasını kullanarak bir düzeni yeniden oluşturmak için bu komutu kullanın. En az Düzen `MinimalLayout.json` , özgün en az düzen giriş parametrelerini içeren bir yanıt dosyası üretir. En az düzeni yeniden oluşturmak için yeniden **Oluştur** komutunu ve bir `MinimalLayout.json` yanıt dosyasını kullanabilirsiniz. bu, önceki minimum düzenin yanıt dosyasına göre yeni bir Visual Studio güncelleştirmesi için en az bir düzen oluşturmak istiyorsanız yararlıdır.

   Bu komut için, `MinimalLayout.json` önceden oluşturulmuş bir düzenden bir dosya yolu gereklidir.

   ```shell
   MinimalLayout.exe regenerate --filePath C:\MinimalLayout\MinimalLayout.json
   ```

* **Doğrula**: düzen klasörünün bozuk olup olmadığını anlamak için bu komutu kullanın.
* **Çözüm**: eksik olan paketleri düzen klasöründen değiştirme dahil bozuk bir düzen klasörünü onarmak için bu komutu kullanın.

#### <a name="options"></a>Seçenekler

::: moniker range=">=vs-2019"

| Seçenekler                                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                 | Gerekli/İsteğe Bağlı               | Örnek                                                                                                                                                          |
|-----------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| --targetLocation &lt; dir&gt;                        | En az bir çevrimdışı düzen oluşturulacağı dizini belirtir.                                                                                                                                                                                                                                                                                                                                                                          | Gerekli                        | --targetLocation c:\VSLayout\                                                                                                                                    |
| --baseVersion &lt; sürümü&gt;                       | Bu sürümle başlayarak en az çevrimdışı düzen oluşturulacaktır.                                                                                                                                                                                                                                                                                                                                                                    | Gerekli                        | --baseVersion 16.4.0                                                                                                                                             |
| --targetVersion &lt; sürümü&gt;                     | En az çevrimdışı düzen, bu sürüm dahil olmak üzere en çok ve dahil oluşturulacak.                                                                                                                                                                                                                                                                                                                                                              | Gerekli                        | --targetVersion 16.4.4                                                                                                                                           |
| --Diller                                         | En az çevrimdışı düzene dahil edilecek dilleri belirtir. Boşluklarla ayırarak birden çok değer belirtilebilir.                                                                                                                                                                                                                                                                                                                    | Gerekli                        | --Diller en-US fr-FR                                                                                                                                          |
| -- &lt; bir veya daha fazla ürün kimliği Ile ProductIDs&gt;        | En az çevrimdışı düzenin oluşturulacağı, virgülle ayırarak oluşturulan ürünlerin KIMLIĞI (öğeleri). <br> <ul><li>Microsoft. VisualStudio. Product. Enterprise</li><li>Microsoft. VisualStudio. Product. Professional</li><li>Microsoft. VisualStudio. Product. BuildTools</li><li>Microsoft. VisualStudio. Product. TestAgent</li><li>Microsoft. VisualStudio. Product. TestController</li><li>Microsoft. VisualStudio. Product. TeamExplorer</li></ul> | Gerekli                        | --ProductIDs Microsoft. VisualStudio. Product. Enterprise, Microsoft. VisualStudio. Product. Professional                                                               |
| --filePath                                          | Zaten oluşturulmuş bir düzenden en az Allayout. json dosyasının dosya yolu. Bu seçenek yalnızca yeniden oluştur komutuyla kullanılır.                                                                                                                                                                                                                                                                                                          | Yeniden oluştur komutu için gerekli | --filePath C:\vslayout\minimallayout,JSON <br><br> **Yeniden oluştur komutunun yalnızca bir seçenek olarak--filePath aldığını unutmayın.**                                      |
| -- &lt; bir veya daha fazla iş yükü veya Bileşen kimliği ekleyin&gt; | Eklenecek bir veya daha fazla iş yükünü veya bileşen kimliğini belirtir. Ek bileşenler,--ıncludereyorumded ve/veya kullanılarak genel olarak eklenebilir <br> –-includeOptional. Birden çok iş yükü veya Bileşen kimliği, boşlukla ayrılmış olarak belirtilebilir.                                                                                                                                                                                                   | İsteğe Bağlı                        | --Microsoft. VisualStudio. Workload. ManagedDesktop Microsoft. VisualStudio. Workload. NetWeb bileşenini ekleyin. GitHub. VisualStudio                                        |
| --ıncludereyorumded                                | , Yüklü olan, ancak isteğe bağlı bileşenleri olmayan tüm iş yükleri için önerilen bileşenleri içerir.                                                                                                                                                                                                                                                                                                                                  | İsteğe Bağlı                        | Belirli bir iş yükü için: <br> --Microsoft. VisualStudio. Workload ekleyin. ManagedDesktop; ıncludereyorum <br><br> Tüm iş yüklerine uygulamak için:--ıncludereyorumded |
| --IncludeOptional                                   | , Önerilen bileşenler dahil olmak üzere yüklü olan tüm iş yükleri için isteğe bağlı bileşenleri içerir.                                                                                                                                                                                                                                                                                                                                | İsteğe Bağlı                        | Belirli bir iş yükü için: <br>--Microsoft. VisualStudio. Workload ekleyin. ManagedDesktop; IncludeOptional <br><br> Tüm iş yüklerine uygulamak için:--includeOptional         |

::: moniker-end

::: moniker range="vs-2017"

| Seçenekler                                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                 | Gerekli/İsteğe Bağlı               | Örnek                                                                                                                                                          |
|-----------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| --targetLocation &lt; dir&gt;                        | En düşük çevrimdışı düzenin oluşturularak bir dizin belirtir.                                                                                                                                                                                                                                                                                                                                                                          | Gerekli                        | --targetLocation c:\VSLayout\                                                                                                                                    |
| --baseVersion &lt; sürümü&gt;                       | Bu sürümden başlayarak en düşük çevrimdışı düzen oluşturulacak.                                                                                                                                                                                                                                                                                                                                                                    | Gerekli                        | --baseVersion 15.0.0                                                                                                                                             |
| --targetVersion &lt; sürümü&gt;                     | Bu sürüme kadar ve bu sürüm dahil olmak üzere en düşük çevrimdışı düzen oluşturulur.                                                                                                                                                                                                                                                                                                                                                              | Gerekli                        | --targetVersion 15.9.31                                                                                                                                          |
| --languages                                         | En düşük çevrimdışı düzende yer alan dilleri belirtir. Boşluklarla ayırarak birden çok değer belirtilebilir.                                                                                                                                                                                                                                                                                                                    | Gerekli                        | --languages en-US fr-FR                                                                                                                                          |
| --productIds &lt; bir veya daha fazla ürün kimlikleri&gt;        | Minimum çevrimdışı düzenin oluşturulacak ürün veya ürün kimlikleri virgülle ayrılmıştır. <br> <ul><li>Microsoft.VisualStudio.Product. Enterprise</li><li>Microsoft.VisualStudio.Product. Professional</li><li>Microsoft.VisualStudio.Product.BuildTools</li><li>Microsoft.VisualStudio.Product.TestAgent</li><li>Microsoft.VisualStudio.Product.TestController</li><li>Microsoft.VisualStudio.Product.TeamExplorer</li></ul> | Gerekli                        | --productIds Microsoft.VisualStudio.Product. Enterprise.Microsoft.VisualStudio.Product. Professional                                                               |
| --filePath                                          | Önceden oluşturulmuş bir düzenden MinimalLayout.json dosyasının dosya yolu. Bu seçenek yalnızca Yeniden Oluştur komutuyla kullanılır.                                                                                                                                                                                                                                                                                                          | Yeniden Oluştur komutu için gereklidir | --filePath C:\VSLayout\minimalLayout.json <br><br> **Yeniden Oluştur komutunun yalnızca --filePath'i bir seçenek olarak kabul gördüğünü unutmayın.**                                      |
| --bir &lt; veya daha fazla iş yükü veya bileşen kimlikleri ekleyin&gt; | Eklenecek bir veya daha fazla iş yükünü veya bileşen kimliklerini belirtir. --includeRecommended ve/veya kullanılarak genel olarak ek bileşenler eklenebilir <br> –-includeOptional. Boşlukla ayırarak birden çok iş yükü veya bileşen kimlikleri belirtilebilir.                                                                                                                                                                                                   | İsteğe Bağlı                        | --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb Bileşeni. GitHub. VisualStudio                                        |
| --includeRecommended                                | Yüklü olan tüm iş yükleri için önerilen bileşenleri içerir, ancak isteğe bağlı bileşenleri dahil değildir.                                                                                                                                                                                                                                                                                                                                  | İsteğe Bağlı                        | Belirli bir iş yükü için: <br> --add Microsoft.VisualStudio.Workload. ManagedDesktop;includeRecommended <br><br> Tüm iş yüklerini uygulamak için: --includeRecommended |
| --includeOptional                                   | Önerilen bileşenler de dahil olmak üzere yüklü tüm iş yükleri için isteğe bağlı bileşenleri içerir.                                                                                                                                                                                                                                                                                                                                | İsteğe Bağlı                        | Belirli bir iş yükü için: <br>--add Microsoft.VisualStudio.Workload. ManagedDesktop;includeOptional <br><br> Tüm iş yüklerini uygulamak için: --includeOptional         |

::: moniker-end

### <a name="generating-a-minimal-layout"></a>Minimum düzen oluşturma

> [!IMPORTANT]
> Bu yönergelerde, daha önce bir ağ yükleme düzeni oluşturduğunuz varsayılanlar vardır. Bunun nasıl olduğu hakkında daha fazla bilgi için Ağ [yüklemesi oluşturma Visual Studio](create-a-network-installation-of-visual-studio.md) bakın.

Belirtilen sürüm aralığınız için **oluştur komutunu** kullanarak minimal bir düzen oluşturun. Ayrıca productId, languages ve gerekli olan belirli iş yüklerini de biliyor oluruz. Bu en düşük düzen, Visual Studio ve hedef sürüm dahil olmak üzere temel sürümden tüm örnek örneklerini güncelleştirecek.

Düzeni oluşturmadan önce, önizleme komutunu kullanarak indirmenin toplam boyutunu ve paket sayısını **bulabilirsiniz.** Bu komut, oluşturma **komutuyla** aynı seçenekleri alır ve ayrıntılar konsola yazılır.

Şimdi minimum düzende önizleme, oluşturma ve yeniden oluşturma ile ilgili birkaç örnek üzerinde durelim:

::: moniker range=">=vs-2019"

* İlk olarak, yalnızca İngilizce için 16.4.0 Visual Studio Enterprise 16.4.4 sürümleri için bir düzenin önizlemesini nasıl görüntüleyebilirsiniz?

  ```shell
  MinimalLayout.exe preview --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --languages en-US
  ```

* Aynı düzeni tek bir iş yüküyle nasıl oluşturabilirsiniz?

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US
  ```

* Ayrıca var olan bir yanıt dosyasını kullanarak en düşük düzeyde çevrimdışı düzeni yeniden oluşturma.

  ```shell
  MinimalLayout.exe regenerate -filepath c:\VSLayout\MinimalLayout.json
  ```

generate komutunu kullanan birkaç **örnek daha:**

* Ek iş yükü ekleme ve yalnızca önerilen paketleri dahil etmek için aşağıdakiler kullanılabilir.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Professional --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb;includeRecommended --languages en-US
  ```

* Ayrıca, birden çok ürünü destekleyen en düşük düzeyde çevrimdışı düzen de oluşturabilirsiniz.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise,Microsoft.VisualStudio.Product.Professional --baseVersion 16.4.0 --targetVersion 16.4.4 --languages en-US
  ```

* Son olarak, en düşük düzeninize birden çok dili nasıl dahil etmek istediğinize de bakabilirsiniz.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US fr-FR
  ```

::: moniker-end

::: moniker range="vs-2017"

* İlk olarak, yalnızca İngilizce için 15.0.0 Visual Studio Enterprise 15.9.31 sürümleri için bir düzenin önizlemesini nasıl görüntüleyebilirsiniz?

  ```shell
  MinimalLayout.exe preview --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --languages en-US
  ```

* Aynı düzeni tek bir iş yüküyle nasıl oluşturabilirsiniz?

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US
  ```

* Ayrıca var olan bir yanıt dosyasını kullanarak en düşük düzeyde çevrimdışı düzeni yeniden oluşturma.

  ```shell
  MinimalLayout.exe regenerate -filepath c:\VSLayout\MinimalLayout.json
  ```

generate komutunu kullanan birkaç **örnek daha:**

* Ek iş yükü ekleme ve yalnızca önerilen paketleri dahil etmek için aşağıdakiler kullanılabilir.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Professional --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb;includeRecommended --languages en-US
  ```

* Ayrıca, birden çok ürünü destekleyen en düşük düzeyde çevrimdışı düzen de oluşturabilirsiniz.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise,Microsoft.VisualStudio.Product.Professional --baseVersion 15.0.0 --targetVersion 15.9.31 --languages en-US
  ```

* Son olarak, en düşük düzeninize birden çok dili nasıl dahil etmek istediğinize de bakabilirsiniz.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US fr-FR
  ```

::: moniker-end

### <a name="how-to-maintain-a-minimal-layout"></a>En düşük düzeni koruma

Oluşturulduktan **sonra** **minimum düzeninizi** korumak için doğrulama ve düzeltme komutlarını kullanın. **verify komutu** minimum düzende bozuk veya eksik paket olup olmadığını belirler. Verify komutunu çalıştırdıktan sonra **herhangi** bir sorunla karşılaşırsanız, **eksik** veya bozuk paketleri düzeltmek için düzeltme komutunu kullanın.

* Bir düzenin bozuk veya eksik paketleri olduğunu doğrulamak için aşağıdakiler kullanılır:

  ```shell
  MinimalLayout.exe Verify --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --languages en-US
  ```

* Bu düzeni şu şekilde düzeltebilirsiniz:

  ```shell
  MinimalLayout.exe fix --targetLocation C:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeRecommended --languages en-US
  ```

>[!NOTE]
> Bu düzen, bir uygulama yüklemesini onarmak Visual Studio kullanılamaz. Uygulamanın mevcut bir örneğini onarmak Visual Studio bkz. [Visual Studio.](repair-visual-studio.md)
>

### <a name="how-to-use-a-minimal-offline-layout-to-update-an-existing-installation-of-visual-studio"></a>Mevcut bir yüklemesini güncelleştirmek için en düşük çevrimdışı düzeni Visual Studio

En az düzen oluştursanız bile minimal düzen klasörünün tamamını bir istemci makinesine kopyaabilirsiniz. Bilgisayarın özgün konumdaki en düşük düzen klasörüne erişimi yoksa bu gereklidir.

klasörüne gidin ve önyükleyici uygulama adını tanımlama. Önyükleyici uygulamasının adı, minimum düzen oluşturma sırasında belirtilen ProductId değerine bağlıdır. Yaygın örnekler için aşağıdaki tabloya bakın.

| ProductId değeri                             | Uygulama adı    |
|---------------------------------------------|---------------------|
| Microsoft.VisualStudio.Product. Enterprise   | vs_enterprise.exe   |
| Microsoft.VisualStudio.Product. Professional | vs_professional.exe |
| Microsoft.VisualStudio.Product.BuildTools   | vs_buildtools.exe   |

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
