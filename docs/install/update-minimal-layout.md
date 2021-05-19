---
title: En düşük düzeyde çevrimdışı düzen kullanarak Visual Studio'yu güncelleştirme
description: Minimum çevrimdışı düzen Visual Studio güncelleştirme hakkında bilgi alın.
ms.date: 05/18/2021
ms.custom: seodec18
ms.topic: how-to
ms.assetid: ''
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 9971007ed38a1f09aa28145ead468f6e5383eeae
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2021
ms.locfileid: "109973613"
---
# <a name="update-visual-studio-using-a-minimal-offline-layout"></a>En düşük düzeyde çevrimdışı düzen kullanarak Visual Studio'yu güncelleştirme

İnternet'e bağlı olan bilgisayarlar için en az düzen oluşturmak, çevrimdışı örneklerinizi güncelleştirmenin en kolay ve en Visual Studio yoludur.

En düşük düzen aracı, takımınıza özel olarak uyarlanmış bir düzen üretir. Kuruluş yöneticileri bu aracı kullanarak 2017 ve 2019'Visual Studio sürümleri için güncelleştirme düzenleri oluşturabilir. Tam bir Visual Studio aksine, minimum düzen yalnızca güncelleştirilmiş paketleri içerir, bu nedenle oluşturma ve dağıtma her zaman daha küçük ve daha hızlıdır. Yalnızca istenen dilleri, iş yüklerini ve bileşenleri belirterek güncelleştirme düzeninin boyutunu daha da küçültebilirsiniz.

## <a name="how-to-generate-a-minimal-layout"></a>Minimum düzen oluşturma

> [!IMPORTANT]
> Bu yönergelerde, daha önce düzen oluşturduğunuz ve bunları kullandığı varsayılanlar vardır. Bunun nasıl olduğu hakkında daha fazla bilgi için Ağ [tabanlı yüklemesini güncelleştirme Visual Studio](update-a-network-installation-of-visual-studio.md) bakın.
>
> Ürün yaşam döngüsü hakkında daha Visual Studio için Ürün Yaşam [Döngüsü Visual Studio Bakım sayfasına](/visualstudio/releases/2019/servicing) bakın.
>

Bu araç, Visual Studio 2017 (15.9) ve sonrası için güncelleştirme düzenleri oluşturur. Düzen, örneklerde güncelleştirme yapmak için ağ/çevrimdışı Visual Studio dağıtılabilir. Normal [düzen oluşturma sırasında,](update-a-network-installation-of-visual-studio.md)bu sürüme göre tüm paketler indirilir. Örneklerde normal düzen oluşturma işlemi onarım, kaldırma ve diğer standart Visual Studio gereklidir. En düşük düzen yalnızca güncelleştirilmiş paketleri indirdiği için çevrimdışı makinelere daha küçük ve daha kolay kopyalayabilirsiniz.

### <a name="installing-the-minimal-layout-tool"></a>En düşük düzen aracını yükleme

 1. İlk olarak, burada bulunan en düşük düzen aracını [indirin.](https://aka.ms/vs/installer/minimallayout) İstendiğinde **Kaydet'i ve** ardından Çalıştır'ı seçin.

     ![En az düzen aracını kaydetme](media/save-minimal-layout.png)

 2. Ardından, Evet'e tıklayarak Kullanıcı Hesabı Denetimi istemini kabul **et.**

     ![Kullanıcı hesabı denetimini kabul et](media/accept-user-account-control.png)

 3. En küçük düzen Aracı ' e yüklenir `C:\Program Files (x86)\Microsoft Visual Studio\MinimalLayout` .

### <a name="how-to-use-the-minimal-layout-tool"></a>En az düzen aracını kullanma

`MinimalLayout.exe` düzeni oluşturmak için aşağıdaki komutları ve seçenekleri kullanır. Aracı çalıştırmak için en az bir komut gereklidir. Aracı nasıl çalıştıracağınızı aşağıda bulabilirsiniz:

```MinimalLayout.exe [command] <options>...```

#### <a name="commands"></a>Komutlar
* **Önizleme**: kaç paketin indirileceği ve bu düzeni oluşturmak için kullanılan toplam alanın önizlemesi için bu komutu kullanın.
* **Oluştur**: Visual Studio 'yu güncelleştirmek için en az düzeni oluşturmak için bu komutu kullanın.
* Yeniden **Oluştur**: var olan en az düzen yanıt dosyasını kullanarak bir düzeni yeniden oluşturmak için bu komutu kullanın. En az Düzen `MinimalLayout.json` , özgün en az düzen giriş parametrelerini içeren bir yanıt dosyası üretir. En az düzeni yeniden oluşturmak için yeniden **Oluştur** komutunu ve bir `MinimalLayout.json` yanıt dosyasını kullanabilirsiniz. Bu, önceki minimum düzenin yanıt dosyasına dayanan yeni bir Visual Studio güncelleştirmesi için en az bir düzen oluşturmak istiyorsanız yararlıdır.

   Bu komut için, `MinimalLayout.json` önceden oluşturulmuş bir düzenden bir dosya yolu gereklidir.

    ```cmd
    MinimalLayout.exe regenerate --filePath C:\MinimalLayout\MinimalLayout.json
    ```

* **Doğrula**: düzen klasörünün bozuk olup olmadığını anlamak için bu komutu kullanın.
* **Çözüm**: eksik olan paketleri düzen klasöründen değiştirme dahil bozuk bir düzen klasörünü onarmak için bu komutu kullanın.

::: moniker range="vs-2019"

#### <a name="options"></a>Seçenekler

|Seçenekler    |Description    |Gerekli/İsteğe Bağlı |Örnek |
|:----------|:-----------|:------------|:--------------|
|--targetLocation &lt; dir&gt; |En az bir çevrimdışı düzen oluşturulacağı dizini belirtir.       |Gerekli        |--targetLocation c:\VSLayout\ |
|--baseVersion &lt; sürümü&gt;|Bu sürümle başlayarak en az çevrimdışı düzen oluşturulacaktır.   |Gerekli|--baseVersion 16.4.0 |
|--targetVersion &lt; sürümü&gt;|Bu sürüme kadar ve bu sürüm dahil olmak üzere en düşük çevrimdışı düzen oluşturulur.|Gerekli|--targetVersion 16.4.4|
|--languages    |En düşük çevrimdışı düzende yer alan dilleri belirtir. Boşluklarla ayırarak birden çok değer belirtilebilir.    |Gerekli    |--languages en-US fr-FR |
|--productIds &lt; bir veya daha fazla ürün kimlikleri&gt;    |Minimum çevrimdışı düzenin oluşturulacak ürün veya ürün kimlikleri virgülle ayrılmıştır. <br> <ul><li>Microsoft.VisualStudio.Product.Enterprise</li><li>Microsoft.VisualStudio.Product.Professional</li><li>Microsoft.VisualStudio.Product.BuildTools</li><li>Microsoft.VisualStudio.Product.TestAgent</li><li>Microsoft.VisualStudio.Product.TestController</li><li>Microsoft.VisualStudio.Product.TeamExplorer</li></ul>|Gerekli|--productIds Microsoft.VisualStudio.Product.Enterprise,Microsoft.VisualStudio.Product.Professional |
|--filePath    |Önceden oluşturulmuş bir MinimalLayout.jsdosyanın dosya yolu. Bu seçenek yalnızca Yeniden Oluştur komutuyla kullanılır.     |Yeniden oluştur komutu için gerekli    |--filePath C:\VSLayout\minimalLayout.json <br><br> **Yeniden oluştur komutunun yalnızca bir seçenek olarak--filePath aldığını unutmayın.** |
|-- &lt; bir veya daha fazla iş yükü veya Bileşen kimliği ekleyin&gt;    |Eklenecek bir veya daha fazla iş yükünü veya bileşen kimliğini belirtir. Ek bileşenler,--ıncludereyorumded ve/veya kullanılarak genel olarak eklenebilir <br> –-includeOptional. Birden çok iş yükü veya Bileşen kimliği, boşlukla ayrılmış olarak belirtilebilir.    |İsteğe Bağlı    |--Microsoft. VisualStudio. Workload. ManagedDesktop Microsoft. VisualStudio. Workload. NetWeb Component. GitHub. VisualStudio ekleyin |
|--ıncludereyorumded    |, Yüklü olan, ancak isteğe bağlı bileşenleri olmayan tüm iş yükleri için önerilen bileşenleri içerir.    |İsteğe Bağlı    |Belirli bir iş yükü için: <br> --Microsoft. VisualStudio. Workload ekleyin. ManagedDesktop; ıncludereyorum <br><br> Tüm iş yüklerine uygulamak için:--ıncludereyorumded |
|--IncludeOptional |, Önerilen bileşenler dahil olmak üzere yüklü olan tüm iş yükleri için isteğe bağlı bileşenleri içerir.    |İsteğe Bağlı    |Belirli bir iş yükü için: <br>--Microsoft. VisualStudio. Workload ekleyin. ManagedDesktop; IncludeOptional <br><br> Tüm iş yüklerini uygulamak için: --includeOptional |

::: moniker-end

::: moniker range="vs-2017"

#### <a name="options"></a>Seçenekler

|Seçenekler    |Description    |Gerekli/İsteğe Bağlı |Örnek |
|:----------|:-----------|:------------|:--------------|
|--targetLocation &lt; dir&gt; |En düşük çevrimdışı düzenin oluşturularak bir dizin belirtir.       |Gerekli        |--targetLocation c:\VSLayout\ |
|--baseVersion &lt; sürümü&gt;|Bu sürümden başlayarak en düşük çevrimdışı düzen oluşturulacak.   |Gerekli|--baseVersion 15.0.0 |
|--targetVersion &lt; sürümü&gt;|Bu sürüme kadar ve bu sürüm dahil olmak üzere en düşük çevrimdışı düzen oluşturulur.|Gerekli|--targetVersion 15.9.31|
|--languages    |En düşük çevrimdışı düzende yer alan dilleri belirtir. Boşluklarla ayırarak birden çok değer belirtilebilir.    |Gerekli    |--languages en-US fr-FR |
|--productIds &lt; bir veya daha fazla ürün kimlikleri&gt;    |Minimum çevrimdışı düzenin oluşturulacak ürün veya ürün kimlikleri virgülle ayrılmıştır. <br> <ul><li>Microsoft.VisualStudio.Product.Enterprise</li><li>Microsoft.VisualStudio.Product.Professional</li><li>Microsoft.VisualStudio.Product.BuildTools</li><li>Microsoft.VisualStudio.Product.TestAgent</li><li>Microsoft. VisualStudio. Product. TestController</li><li>Microsoft. VisualStudio. Product. TeamExplorer</li></ul>|Gerekli|--ProductIDs Microsoft. VisualStudio. Product. Enterprise, Microsoft. VisualStudio. Product. Professional |
|--filePath    |Zaten oluşturulmuş bir düzenden dosyanın MinimalLayout.jsdosya yolu. Bu seçenek yalnızca yeniden oluştur komutuyla kullanılır.     |Yeniden oluştur komutu için gerekli    |--filePath C:\VSLayout\minimalLayout.json <br><br> **Yeniden oluştur komutunun yalnızca bir seçenek olarak--filePath aldığını unutmayın.** |
|-- &lt; bir veya daha fazla iş yükü veya Bileşen kimliği ekleyin&gt;    |Eklenecek bir veya daha fazla iş yükünü veya bileşen kimliğini belirtir. Ek bileşenler,--ıncludereyorumded ve/veya kullanılarak genel olarak eklenebilir <br> –-includeOptional. Birden çok iş yükü veya Bileşen kimliği, boşlukla ayrılmış olarak belirtilebilir.    |İsteğe Bağlı    |--Microsoft. VisualStudio. Workload. ManagedDesktop Microsoft. VisualStudio. Workload. NetWeb Component. GitHub. VisualStudio ekleyin |
|--ıncludereyorumded    |, Yüklü olan, ancak isteğe bağlı bileşenleri olmayan tüm iş yükleri için önerilen bileşenleri içerir.    |İsteğe Bağlı    |Belirli bir iş yükü için: <br> --Microsoft. VisualStudio. Workload ekleyin. ManagedDesktop; ıncludereyorum <br><br> Tüm iş yüklerini uygulamak için: --includeRecommended |
|--includeOptional |Önerilen bileşenler de dahil olmak üzere yüklü tüm iş yükleri için isteğe bağlı bileşenleri içerir.    |İsteğe Bağlı    |Belirli bir iş yükü için: <br>--microsoft.VisualStudio.workload ekleyin. ManagedDesktop;includeOptional <br><br> Tüm iş yüklerini uygulamak için: --includeOptional |

::: moniker-end

### <a name="generating-a-minimal-layout"></a>Minimum düzen oluşturma

> [!IMPORTANT]
>  Bu yönergelerde, daha önce bir ağ yükleme düzeni oluşturduğunuz varsayılanlar vardır. Bunun nasıl olduğu hakkında daha fazla bilgi için Ağ [yüklemesi oluşturma Visual Studio](create-a-network-installation-of-visual-studio.md) bakın.

Belirtilen sürüm aralığınız için **oluştur komutunu** kullanarak minimal bir düzen oluşturun. Ayrıca productId, languages ve gerekli olan belirli iş yüklerini de biliyor oluruz. Bu en düşük düzen, Visual Studio ve hedef sürüm dahil olmak üzere temel sürümden tüm örnek örneklerini güncelleştirecek.

Düzeni oluşturmadan önce, önizleme komutunu kullanarak indirmenin toplam boyutunu ve paket sayısını **bulabilirsiniz.** Bu komut, oluşturma komutuyla **aynı** seçenekleri alır ve ayrıntılar konsola yazılır.

Şimdi minimum düzende önizleme, oluşturma ve yeniden oluşturma ile ilgili birkaç örnek üzerinde durelim:

::: moniker range="vs-2019"

- İlk olarak, yalnızca İngilizce için 16.4.0 Visual Studio Enterprise 16.4.4 sürümleri için bir düzenin önizlemesini nasıl önizleyebilirsiniz?

    ```cmd
    MinimalLayout.exe preview --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --languages en-US
    ```

- Aynı düzeni tek bir iş yüküyle nasıl oluşturabilirsiniz?

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US
    ```

- Ayrıca var olan bir yanıt dosyasını kullanarak en düşük düzeyde çevrimdışı düzenin nasıl yeniden üretln?

    ```cmd
    MinimalLayout.exe regenerate -filepath c:\VSLayout\MinimalLayout.json
    ```

komutunu kullanan diğer örneklerden **birkaçı:**

- Ek bir iş yükü ekleme ve yalnızca önerilen paketleri ekleme.

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Professional --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb;includeRecommended --languages en-US
    ```

- Son olarak, en az düzeninizde birden çok dili nasıl dahil edeceğiniz aşağıda bulabilirsiniz.

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US fr-FR
    ```

::: moniker-end

::: moniker range="vs-2017"

- İlk olarak, 'sının 15.0.0 sürümleri için bir düzenin yalnızca Ingilizce için nasıl önizlemesinin Visual Studio Enterprise bir örneği aşağıda verilmiştir.

    ```cmd
    MinimalLayout.exe preview --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --languages en-US
    ```

- Aynı düzeni bir iş yüküyle nasıl oluşturabileceğiniz aşağıda açıklanmaktadır.

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US
    ```

- İşte, var olan bir yanıt dosyasını kullanarak en az bir çevrimdışı düzeni yeniden üretme.

    ```cmd
    MinimalLayout.exe regenerate -filepath c:\VSLayout\MinimalLayout.json
    ```

**Generate** komutunu kullanarak diğer birkaç örnek:

- Ek bir iş yükü ekleme ve yalnızca önerilen paketleri ekleme.

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Professional --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb;includeRecommended --languages en-US
    ```

- Son olarak, en az düzeninizde birden çok dili nasıl dahil edeceğiniz aşağıda bulabilirsiniz.

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US fr-FR
    ```

::: moniker-end

### <a name="how-to-maintain-a-minimal-layout"></a>En az bir düzen koruma

Oluşturulduktan sonra en az düzeninizi sürdürmek için **doğrulama** ve **çözme** komutlarını kullanın. **Verify** komutu, en az düzende bozuk veya eksik paketler olup olmadığını belirler. **Verify** komutunu çalıştırdıktan sonra herhangi bir sorunla karşılaşırsanız, eksik veya bozuk paketleri düzeltmek için **Düzelt** komutunu kullanın.

- Bir düzenin bozuk veya eksik paketlere sahip olup olmadığını doğrulamak için şu adımları uygulayın:

    ```cmd
    MinimalLayout.exe Verify --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --languages en-US
    ```

- Bu düzenin nasıl düzeltileceğini aşağıda görebilirsiniz:

    ```cmd
    MinimalLayout.exe fix --targetLocation C:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeRecommended --languages en-US
    ```

>[!NOTE]
> Bu düzen, Visual Studio yüklemesini onarmak için kullanılamaz. Visual Studio 'nun mevcut bir örneğini onarmak için bkz. [Visual Studio 'Yu onarma](repair-visual-studio.md).
>

### <a name="how-to-use-a-minimal-offline-layout-to-update-an-existing-installation-of-visual-studio"></a>Var olan bir Visual Studio yüklemesini güncelleştirmek için en az bir çevrimdışı düzen kullanma

En az bir düzen oluşturduktan sonra, en küçük düzen klasörünün tamamını bir istemci makinesine kopyalayabilirsiniz. Bilgisayarın özgün konumunda en düşük düzen klasörüne erişimi yoksa bu gereklidir.

Klasöre gidin ve önyükleyici uygulama adını tespit edin. Önyükleyici uygulamasının adı, minimum düzen oluşturma sırasında belirtilen ProductId değerine bağlıdır. Yaygın örnekler için aşağıdaki tabloya bakın.

|ProductId değeri    |Uygulama adı|
|:-----------|:------------|
|Microsoft.VisualStudio.Product.Enterprise    |vs_enterprise.exe|
|Microsoft.VisualStudio.Product.Professional    |vs_professional.exe|
|Microsoft.VisualStudio.Product.BuildTools    |vs_buildtools.exe|

Güncelleştirme, iki adımda Visual Studio örnek için uygulanır. İlk olarak, Visual Studio Yükleyicisi güncelleştirin ve Visual Studio.

1. **Güncelleştirme Visual Studio Yükleyicisi**

    Gerekirse doğru önyükleyici uygulama `vs_enterprise.exe`  adıyla değiştirin ve aşağıdaki komutu çalıştırın.

    ```cmd
    vs_enterprise.exe --quiet --update --offline C:\VSLayout\vs_installer.opc
    ```

2. **Visual Studio güncelleştirme**

    Bu Visual Studio güncelleştirmek için, güncelleştirmek istediğiniz Visual Studio örneğinin installPath'ini belirtmeniz gerekir. Birden çok örnek Visual Studio, her birinin ayrı olarak güncelleştirilmiş olması gerekir. Minimum düzende olmayan `–noWeb` bileşenlerin yüklemesini önlemek için güncelleştirme komutuyla seçeneğini belirtmenizi kesinlikle öneririz. Bu, çalışmadan Visual Studio durumda bırakmasını sağlar.

    InstallPath komut satırı parametresini uygun şekilde değiştirarak aşağıdaki komutu çalıştırın. Doğru önyükleyici uygulama adını da kullanmaya emin olun.

    ```cmd
    vs_enterprise.exe update --noWeb --quiet --installpath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise"
    ```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yu yükleme](install-visual-studio.md)
* [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
* [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio örneklerini algılamaya ve yönetmeye yönelik araçlar](tools-for-managing-visual-studio-instances.md)
* [Yanıt dosyasında ayarları tanımlama](automated-installation-with-response-file.md)
* [Ağ tabanlı Visual Studio dağıtımlarında güncelleştirmeleri denetleme](controlling-updates-to-visual-studio-deployments.md)
* [Visual Studio ürün yaşam döngüsü ve bakım](/visualstudio/releases/2019/servicing/)
