---
title: En düşük düzeyde çevrimdışı düzen kullanarak Visual Studio'yu güncelleştirme
description: En düşük düzeyde çevrimdışı düzen kullanarak Visual Studio 'Yu güncelleştirmeyi öğrenin.
ms.date: 07/21/2020
ms.custom: seodec18
ms.topic: how-to
ms.assetid: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 2b9c86c17b89258145613e867ba6a91b2219fe0d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88168755"
---
# <a name="update-visual-studio-using-a-minimal-offline-layout"></a>En düşük düzeyde çevrimdışı düzen kullanarak Visual Studio'yu güncelleştirme

İnternet 'e bağlı olmayan bilgisayarlar için, en az bir düzen oluşturmak, çevrimdışı Visual Studio örneklerinizi güncelleştirmenin en kolay ve en hızlı yoludur.

En küçük düzen Aracı, takımınızın ihtiyaçlarına özel olarak uyarlanmış bir düzen oluşturur. Kurumsal Yöneticiler bu aracı, Visual Studio 2017 ve 2019 için çoğu sürüm için güncelleştirme düzenleri oluşturmak üzere kullanabilir. Tam Visual Studio düzeninin aksine, en az bir düzen yalnızca güncelleştirilmiş paketleri içerir, bu nedenle oluşturmak ve dağıtmak için her zaman daha küçük ve daha hızlıdır. Yalnızca istediğiniz dilleri, iş yüklerini ve bileşenleri belirterek güncelleştirme düzeninin boyutunu daha da en aza indirgeyin.

## <a name="how-to-generate-a-minimal-layout"></a>En az bir düzen oluşturma

> [!IMPORTANT]
> Bu yönergelerde, düzenleri daha önce oluşturduğunuz ve kullandığınız varsayılır. Bunun nasıl yapılacağı hakkında daha fazla bilgi için bkz. [Visual Studio 'nun ağ tabanlı yüklemesini güncelleştirme](update-a-network-installation-of-visual-studio.md) sayfası.
>
> Visual Studio yaşam döngüsünü daha iyi anlamak için bkz. [Visual Studio ürün yaşam döngüsü ve bakım](/visualstudio/releases/2019/servicing) sayfası.
>

Bu araç, Visual Studio 2017 (15,9) ve sonraki sürümler için güncelleştirme düzenleri oluşturur. Düzen, Visual Studio örneklerini güncelleştirmek için ağ/çevrimdışı makinelere dağıtılabilir. [Normal düzen oluşturma](update-a-network-installation-of-visual-studio.md)sırasında, söz konusu sürümün tüm paketleri indirilir. Visual Studio örneklerinde onarım, kaldırma ve diğer standart işlemler için normal düzen oluşturma gereklidir. En küçük düzen yalnızca güncelleştirilmiş paketleri indirir, bu nedenle çevrimdışı makinelere kopyalamak daha küçüktür ve daha kolay olur.

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
* **Oluştur**: Visual Studio 'yu güncelleştirmek için en az düzeni oluşturmak için bu komutu kullanın.
* Yeniden **Oluştur**: var olan en az düzen yanıt dosyasını kullanarak bir düzeni yeniden oluşturmak için bu komutu kullanın. En az Düzen `MinimalLayout.json` , özgün en az düzen giriş parametrelerini içeren bir yanıt dosyası üretir. En az düzeni yeniden oluşturmak için yeniden **Oluştur** komutunu ve bir `MinimalLayout.json` yanıt dosyasını kullanabilirsiniz. Bu, önceki minimum düzenin yanıt dosyasına dayanan yeni bir Visual Studio güncelleştirmesi için en az bir düzen oluşturmak istiyorsanız yararlıdır.

   Bu komut için, `MinimalLayout.json` önceden oluşturulmuş bir düzenden bir dosya yolu gereklidir. 

    ```cmd
    MinimalLayout.exe regenerate --filePath C:\MinimalLayout\MinimalLayout.json
    ```

* **Doğrula**: düzen klasörünün bozuk olup olmadığını anlamak için bu komutu kullanın.
* **Çözüm**: eksik olan paketleri düzen klasöründen değiştirme dahil bozuk bir düzen klasörünü onarmak için bu komutu kullanın.

#### <a name="options"></a>Seçenekler 

|Seçenekler    |Description    |Gerekli/İsteğe Bağlı |Örnek |
|:----------|:-----------|:------------|:--------------|
|--targetLocation &lt; dir&gt; |En az bir çevrimdışı düzen oluşturulacağı dizini belirtir.       |Gerekli        |--targetLocation c:\VSLayout\ |
|--baseVersion &lt; sürümü&gt;|Bu sürümle başlayarak en az çevrimdışı düzen oluşturulacaktır.   |Gerekli|--baseVersion 16.4.0 |
|--targetVersion &lt; sürümü&gt;|En az çevrimdışı düzen, bu sürüm dahil olmak üzere en çok ve dahil oluşturulacak.|Gerekli|--targetVersion 16.4.4|
|--Diller    |En az çevrimdışı düzene dahil edilecek dilleri belirtir. Boşluklarla ayırarak birden çok değer belirtilebilir.    |Gerekli    |--Diller en-US fr-FR |
|--ProductID &lt; kimliği&gt;    |En az çevrimdışı düzenin oluşturulacağı ürünün KIMLIĞI. <br> <ul><li>Microsoft. VisualStudio. Product. Enterprise</li><li>Microsoft. VisualStudio. Product. Professional</li><li>Microsoft. VisualStudio. Product. BuildTools</li><li>Microsoft. VisualStudio. Product. TestAgent</li><li>Microsoft. VisualStudio. Product. TestController</li><li>Microsoft. VisualStudio. Product. TeamExplorer</li></ul>|Gerekli|--ProductID Microsoft. VisualStudio. Product. Enterprise |
|--filePath    |Zaten oluşturulmuş bir düzenden dosyanın MinimalLayout.jsdosya yolu. Bu seçenek yalnızca yeniden oluştur komutuyla kullanılır.     |Yeniden oluştur komutu için gerekli    |--filePath C:\VSLayout\minimalLayout.json <br><br> **Yeniden oluştur komutunun yalnızca bir seçenek olarak--filePath aldığını unutmayın.** |
|-- &lt; bir veya daha fazla iş yükü veya Bileşen kimliği ekleyin&gt;    |Eklenecek bir veya daha fazla iş yükünü veya bileşen kimliğini belirtir. Ek bileşenler,--ıncludereyorumded ve/veya kullanılarak genel olarak eklenebilir <br> –-includeOptional. Birden çok iş yükü veya Bileşen kimliği, boşlukla ayrılmış olarak belirtilebilir.    |İsteğe Bağlı    |--Microsoft. VisualStudio. Workload. ManagedDesktop Microsoft. VisualStudio. Workload. NetWeb Component. GitHub. VisualStudio ekleyin |
|--ıncludereyorumded    |, Yüklü olan, ancak isteğe bağlı bileşenleri olmayan tüm iş yükleri için önerilen bileşenleri içerir.    |İsteğe Bağlı    |Belirli bir iş yükü için: <br> --Microsoft. VisualStudio. Workload ekleyin. ManagedDesktop; ıncludereyorum <br><br> Tüm iş yüklerine uygulamak için:--ıncludereyorumded |
|--IncludeOptional |, Önerilen bileşenler dahil olmak üzere yüklü olan tüm iş yükleri için isteğe bağlı bileşenleri içerir.    |İsteğe Bağlı    |Belirli bir iş yükü için: <br>--Microsoft. VisualStudio. Workload ekleyin. ManagedDesktop; IncludeOptional <br><br> Tüm iş yüklerine uygulamak için:--includeOptional |

### <a name="generating-a-minimal-layout"></a>En az düzen oluşturma

> [!IMPORTANT]
>  Bu yönergelerde, daha önce bir ağ yükleme düzeni oluşturmuş olduğunuz varsayılır. Bunun nasıl yapılacağı hakkında daha fazla bilgi için [Visual Studio 'nun ağ yüklemesi oluşturma](create-a-network-installation-of-visual-studio.md) sayfasına bakın.

Belirtilen sürüm aralığınızı oluşturmak için **Oluştur** komutunu kullanarak en az bir düzen oluşturun. Ayrıca ProductID, Languages ve gereken belirli iş yüklerini bilmeniz gerekir. Bu en az düzen, temel sürümden hedef sürüm dahil olmak üzere tüm Visual Studio örneklerini güncelleyecek.

Düzeni oluşturmadan önce, indirmenin toplam boyutunu ve **Önizleme** komutu kullanılarak dahil edilen paket sayısını bulabilirsiniz. Bu komut, **Oluştur** komutuyla aynı seçenekleri alır ve Ayrıntılar konsola yazılır.

En az bir düzeni önizleme, oluşturma ve yeniden oluşturma hakkında birkaç örnek adım adım inceleyelim:

- İlk olarak, 16.4.0 sürümleri için bir düzenin yalnızca Ingilizce için nasıl önizlemesinin Visual Studio Enterprise bir örneği aşağıda verilmiştir.

    ```cmd
    MinimalLayout.exe preview --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --languages en-US
    ```

- Aynı düzeni bir iş yüküyle nasıl oluşturabileceğiniz aşağıda açıklanmaktadır.

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US
    ```

- İşte, var olan bir yanıt dosyasını kullanarak en az bir çevrimdışı düzeni yeniden üretme. 

    ```cmd
    MinimalLayout.exe regenerate -filepath c:\VSLayout\MinimalLayout.json
    ```

**Generate** komutunu kullanarak diğer birkaç örnek:

- Ek bir iş yükü ekleme ve yalnızca önerilen paketleri ekleme. 

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Professional --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb;includeRecommended --languages en-US
    ```

- Son olarak, en az düzeninizde birden çok dili nasıl dahil edeceğiniz aşağıda bulabilirsiniz. 

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US fr-FR
    ```

### <a name="how-to-maintain-a-minimal-layout"></a>En az bir düzen koruma

Oluşturulduktan sonra en az düzeninizi sürdürmek için **doğrulama** ve **çözme** komutlarını kullanın. **Verify** komutu, en az düzende bozuk veya eksik paketler olup olmadığını belirler. **Verify** komutunu çalıştırdıktan sonra herhangi bir sorunla karşılaşırsanız, eksik veya bozuk paketleri düzeltmek için **Düzelt** komutunu kullanın.

- Bir düzenin bozuk veya eksik paketlere sahip olup olmadığını doğrulamak için şu adımları uygulayın: 

    ```cmd
    MinimalLayout.exe Verify --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --languages en-US
    ```

- Bu düzenin nasıl düzeltileceğini aşağıda görebilirsiniz:

    ```cmd
    MinimalLayout.exe fix --targetLocation C:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeRecommended --languages en-US
    ```

>[!NOTE] 
> Bu düzen, Visual Studio yüklemesini onarmak için kullanılamaz. Visual Studio 'nun mevcut bir örneğini onarmak için bkz. [Visual Studio 'Yu onarma](repair-visual-studio.md).
>

### <a name="how-to-use-a-minimal-offline-layout-to-update-an-existing-installation-of-visual-studio"></a>Var olan bir Visual Studio yüklemesini güncelleştirmek için en az bir çevrimdışı düzen kullanma

En az bir düzen oluşturduktan sonra, en küçük düzen klasörünün tamamını bir istemci makinesine kopyalayabilirsiniz. Bilgisayarın özgün konumunda en düşük düzen klasörüne erişimi yoksa bu gereklidir.

Klasöre gidin ve önyükleyici uygulama adını tespit edin. Önyükleyici uygulamasının adı, en az düzen oluşturulurken belirtilen ProductID değerine bağlıdır. Ortak örnekler için aşağıdaki tabloya bakın.

|ProductID değeri    |Uygulama adı|
|:-----------|:------------|
|Microsoft. VisualStudio. Product. Enterprise    |vs_enterprise.exe|
|Microsoft. VisualStudio. Product. Professional    |vs_professional.exe|
|Microsoft. VisualStudio. Product. BuildTools    |vs_buildtools.exe|

Güncelleştirme, Visual Studio örneğine iki adımda uygulanır. Visual Studio Yükleyicisi güncelleyerek başlatın ve ardından Visual Studio 'Yu güncelleştirin.

1. **Visual Studio Yükleyicisi güncelleştirin** 

    `vs_enterprise.exe`Gerekirse, doğru önyükleyici uygulama adıyla değiştirerek aşağıdaki komutu çalıştırın. 

    ```cmd
    vs_enterprise.exe --quiet --update --offline C:\VSLayout\vs_installer.opc
    ```

2. **Visual Studio uygulamasını güncelleştirme**

    Visual Studio 'Yu güncelleştirmek için, güncelleştirmek istediğiniz Visual Studio örneğinin InstallPath ' i belirtmeniz gerekir. Visual Studio 'nun birden çok örneği yüklüyse, her birinin ayrı olarak güncelleştirilmesi gerekir. `–noWeb`Minimum düzende olmayan bileşenlerin yüklenmesini engellemek için Update komutuyla birlikte seçeneğini belirtmenize kesinlikle tavsiye ederiz. Bu, Visual Studio 'Yu kullanılamaz durumda bırakmanızı önler.

    InstallPath komut satırı parametresini uygun şekilde değiştirerek aşağıdaki komutu çalıştırın. Doğru önyükleyici uygulama adını da kullandığınızdan emin olun.

    ```cmd
    vs_enterprise.exe update --noWeb --quiet --installpath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise"
    ```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yu yükleme](install-visual-studio.md)
* [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
* [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio örneklerini algılamaya ve yönetmeye yönelik araçlar](tools-for-managing-visual-studio-instances.md)
* [Yanıt dosyasındaki ayarları tanımlama](automated-installation-with-response-file.md)
* [Ağ tabanlı Visual Studio dağıtımlarında güncelleştirmeleri denetleme](controlling-updates-to-visual-studio-deployments.md)
* [Visual Studio ürün yaşam döngüsü ve bakım](/visualstudio/releases/2019/servicing/)
