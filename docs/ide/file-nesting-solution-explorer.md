---
title: Çözüm Gezgini için dosya iç içe geçme kuralları
ms.date: 05/25/2018
ms.topic: conceptual
helpviewer_keywords:
- file nesting
- Solution Explorer, file nesting
author: angelosp
ms.author: angelpe
manager: jillfra
ms.openlocfilehash: a36ca2535785f72756ad66a69c2ebe4d7d5a373b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "67587023"
---
# <a name="file-nesting-in-solution-explorer"></a>Çözüm Gezgini’nde dosya iç içe yerleştirme

**Çözüm Gezgini,** ilgili dosyaları düzenlemeye yardımcı olmak ve bulmalarını kolaylaştırmak için yuvaları. Örneğin, bir projeye Windows Forms formu eklerseniz, formun kod dosyası **Çözüm Gezgini'ndeki**formun altına iç içe geçer. ASP.NET Core projelerinde, dosya iç içe geçme bir adım daha ileri alınabilir. Dosya iç içe geçme ön kümeleri **Kapalı**, **Varsayılan**ve **Web**arasında seçim yapabilirsiniz. Ayrıca, [dosyaların iç içe nasıl iç içe olduğunu özelleştirebilir](#customize-file-nesting) veya [çözüme özgü ve projeye özgü ayarlar oluşturabilirsiniz.](#create-project-specific-settings)

> [!NOTE]
> Özellik şu anda yalnızca ASP.NET Core projeleri için desteklenir.

## <a name="file-nesting-options"></a>Dosya iç içe geçme seçenekleri

![Dosya iç içe geçmeyi açma/kapatma düğmesi](media/filenesting_onoff.png)

Özelleştirilmemiş dosya iç içe geçme için kullanılabilir seçenekler şunlardır:

* **Kapalı**: Bu seçenek, herhangi bir iç içe geçmeden dosyaların düz bir listesini verir.

* **Varsayılan**: Bu **seçenek, Çözüm Gezgini'nde**varsayılan dosya iç içe geçme davranışını sağlar. Belirli bir proje türü için ayar yoksa, projedeki hiçbir dosya iç içe geçmez. Ayarlar varsa, örneğin bir web projesi için iç içe geçme uygulanır.

* **Web**: Bu seçenek, geçerli çözümdeki tüm projelere **Web** dosyası iç içe geçme davranışını uygular. Çok sayıda kuralı var ve bunu kontrol etmenizi ve ne düşündüğünüzü bize söylemenizi öneririz. Aşağıdaki ekran görüntüsü, bu seçenekle elde ettiğiniz dosya iç içe geçme davranışının yalnızca birkaç örneğini vurgular:

   ![Çözüm Gezgini’nde dosya iç içe yerleştirme](media/filenesting.png)

## <a name="customize-file-nesting"></a>Dosya iç içe geçmeyi özelleştirme

Kutudan çıkanları beğenmezseniz, **Solution Explorer'a** dosyaları nasıl iç içe geçirirseniz öğreten kendi özel dosya iç içe geçme ayarlarınızı oluşturabilirsiniz. İstediğiniz kadar özel dosya iç içe geçme ayarı ekleyebilirsiniz ve istediğiniz gibi aralarında geçiş yapabilirsiniz. Yeni bir özel ayar oluşturmak için boş bir dosyayla başlayabilir veya Başlangıç noktanız olarak **Web** ayarlarını kullanabilirsiniz:

![Özel dosya iç içe geçme kuralları ekleme](media/filenesting_addcustom.png)

Zaten çalışan bir şeyle çalışmak daha kolay **olduğundan, Web** ayarlarını başlangıç noktanız olarak kullanmanızı öneririz. **Web** ayarlarını başlangıç noktanız olarak kullanırsanız, *.filenesting.json* dosyası aşağıdaki dosyaya benzer görünür:

![Özel ayarlar için temel olarak varolan dosya iç içe geçme kurallarını kullanma](media/filenesting_editcustom.png)

Düğüm **bağımlısıFileProviders** ve alt düğümlerine odaklanalım. Her alt düğüm, Visual Studio'nun dosyaları yuvalamak için kullanabileceği bir kural türüdür. Örneğin, **aynı dosya adına sahip, ancak farklı bir uzantı** kural türüdür. Mevcut kurallar şunlardır:

* **extensionToExtension**: *file.js'yi* *file.ts* altında yuvalamak için bu kural türünü kullanın

* **fileSuffixToExtension**: *dosya-vsdoc.js* *dosya.js* altında yuva için kural bu tür kullanın

* **addedExtension**: *file.html.css* *dosya.html* altında yuva için kural bu tür kullanın

* **pathSegment**: *jquery.min.js altında jquery.min.js* yuva için kural bu tür kullanın *jquery.js*

* **allExtensions**: Dosyayı yuvalamak için bu tür bir kural *kullanın.* * *altında file.js*

* **fileToFile**: *.bowerrc* altında *bower.json* yuva için kural bu tür kullanın

### <a name="the-extensiontoextension-provider"></a>ExtensionToExtension sağlayıcısı

Bu sağlayıcı, belirli dosya uzantılarını kullanarak dosya iç içe geçme kurallarını tanımlamanızı sağlar. Aşağıdaki örneği inceleyin:

![extentionToExtension örnek kuralları](media/filenesting_extensiontoextension.png) ![extentionToExtension örnek etkisi](media/filenesting_extensiontoextension_effect.png)

* *cart.js* ilk **uzantısıToExtension** kuralı nedeniyle *cart.ts* altında iç içe

* *cart.js* *cart.tsx* altında iç içe değildir çünkü **.tss** kurallarda **.tsx'ten** önce gelir ve yalnızca bir ebeveyn olabilir

* *light.css* ikinci **uzantısıToExtension** kuralı nedeniyle *light.sass* altında iç içe

* *home.html* üçüncü **uzantısıToExtension** kuralı nedeniyle *home.md* altında iç içe

### <a name="the-filesuffixtoextension-provider"></a>DosyaSuffixToExtension sağlayıcısı

Bu sağlayıcı, yalnızca kural yalnızca uzantısı yerine dosyanın soneki bakar olmak, **uzantıToExtension** sağlayıcısı gibi çalışır. Aşağıdaki örneği inceleyin:

![dosyaSuffixToExtension örnek kuralları](media/filenesting_filesuffixtoextension.png) ![dosyaSuffixToExtension örnek etkisi](media/filenesting_filesuffixtoextension_effect.png)

* *portal-vsdoc.js* **dosyasuffixToExtension** kuralı nedeniyle *portal.js* altında iç içe

* kuralın her yönü **extensionToExtension** ile aynı şekilde çalışır

### <a name="the-addedextension-provider"></a>addedExtension sağlayıcısı

Bu sağlayıcı, ek bir uzantı olmadan dosyanın altında ek bir uzantı ile dosyaları yuvaları. Ek uzantı yalnızca tam dosya adının sonunda görünebilir.

Aşağıdaki örneği inceleyin:

![addedExtension örnek kuralları](media/filenesting_addedextension.png) ![addedExtension örnek efekti](media/filenesting_addedextension_effect.png)

* *file.html.css* **addedExtension** kuralı nedeniyle *dosya.html* altında iç içe

> [!NOTE]
> `addedExtension` Kural için herhangi bir dosya uzantısı belirtmezsiniz; tüm dosya uzantıları için otomatik olarak geçerlidir. Diğer bir deyişle, başka bir dosya yla aynı ad ve uzantıya sahip herhangi bir dosya artı uçtaki ek uzantı diğer dosyanın altına yer alar. Bu sağlayıcının etkisini sadece belirli dosya uzantılarıyla sınırlayamazsınız.

### <a name="the-pathsegment-provider"></a>PathSegment sağlayıcısı

Bu sağlayıcı, ek bir uzantısı olmayan bir dosyanın altında ek bir uzantı ile dosyaları yuvaları. Ek uzantı yalnızca tam dosya adının ortasında görünebilir.

Aşağıdaki örneği inceleyin:

![pathSegment örnek kuralları](media/filenesting_pathsegment.png) ![pathSegment örnek efekti](media/filenesting_pathsegment_effect.png)

* *jquery.min.js* **yol Segment** kuralı nedeniyle *jquery.js* altında iç içe

> [!NOTE]
> - `pathSegment` Kural için belirli bir dosya uzantısı belirtmezseniz, bu kural tüm dosya uzantıları için geçerlidir. Diğer bir deyişle, başka bir dosya yla aynı ada ve uzantıya sahip herhangi bir dosya artı ortada ek bir uzantı diğer dosyanın altına yer alar.
> - Kuralın `pathSegment` etkisini aşağıdaki şekilde belirterek belirli dosya uzantılarıyla sınırlandırabilirsiniz:
>
>    ```json
>    "pathSegment": {
>       "add": {
>         ".*": [
>           ".js",
>           ".css",
>           ".html",
>           ".htm"
>         ]
>       }
>    }
>    ```

### <a name="the-allextensions-provider"></a>allExtensions sağlayıcısı

Bu sağlayıcı, herhangi bir uzantı sıdamadan aynı temel dosya adı olan dosyalar için dosya iç içe geçme kurallarını tanımlamanıza olanak tanır. Aşağıdaki örneği inceleyin:

![allExtensions örnek kuralları](media/filenesting_allextensions.png) ![allExtensions örnek efekti](media/filenesting_allextensions_effect.png)

* *template.cs* ve *template.doc,* **tüm Uzantılar** kuralı nedeniyle *template.tt* altında iç içe dir.

### <a name="the-filetofile-provider"></a>fileToFile sağlayıcısı

Bu sağlayıcı, dosya tüm adlarını temel alan dosya iç içe geçme kurallarını tanımlamanızı sağlar. Aşağıdaki örneği inceleyin:

![fileToFile örnek kuralları](media/filenesting_filetofile.png) ![fileToFile örnek efekti](media/filenesting_filetofile_effect.png)

* *.bowerrc* **fileToFile** kuralı nedeniyle *bower.json* altında iç içe

### <a name="rule-order"></a>Kural sırası

Sipariş, özel ayarlar dosyanızın her bölümünde önemlidir. Kurallar, **bağlı FileProvider** düğümünün içinde yukarı veya aşağı hareket ettirerek kuralların yürütülme sırasını değiştirebilirsiniz. Örneğin, **file.js'yi** **file.ts'nin** üst öğesi yapan bir kuralınız ve **dosya.kahveyi** **file.ts'nin**üst öğesi yapan başka bir kuralınız varsa, dosyada göründükleri sıra, üç dosya da bulunduğunda iç içe geçme davranışını belirler. **File.ts** yalnızca bir ebeveyne sahip olabileceğinden, hangi kural ilk kazanır yürütürse.

Sıralama, kural bölümleri için de önemlidir, sadece bir bölümdeki dosyalar için değil. Bir dosya çifti bir dosya iç içe geçme kuralıyla eşleşir eşleşmez, dosyadaki diğer kurallar yoksayılır ve bir sonraki dosya çifti işlenir.

### <a name="file-nesting-button"></a>Dosya iç içe geçme düğmesi

Kendi özel ayarlarınız da dahil olmak üzere tüm ayarları **Çözüm Gezgini'ndeki**aynı düğmeyle yönetebilirsiniz:

![Özel dosya iç içe geçme kurallarını etkinleştirme](media/filenesting_activatecustom.png)

## <a name="create-project-specific-settings"></a>Projeye özel ayarlar oluşturma

Her çözüm ve projenin sağ tıklama menüsünden (bağlam menüsü) çözüme ve projeye özgü ayarlar oluşturabilirsiniz:

![Çözüm ve projeye özel iç içe geçme kuralları](media/filenesting_solutionprojectspecific.png)

Çözüme özel ve projeye özel ayarlar, etkin Visual Studio ayarlarıyla birleştirilir. Örneğin, projeye özgü boş bir ayarlar dosyanız olabilir, ancak **Solution Explorer** hala dosyaları iç içe alıyor. İç içe geçme davranışı çözüme özgü ayarlardan veya Visual Studio ayarlarından geliyor. Dosya iç içe geçme ayarlarını birleştirmenin önceliği şudur: Visual Studio > Solution > Project.

Visual Studio'ya, dosyalar diskte olsa bile çözüme özgü ve projeye özgü ayarları yoksaymasını, Temel**Dosya İçi Yerleştirme**ASP.NET **Araçlar** > **Seçenekleri** > **ASP.NET Core** > altında **çözüm ve proje ayarlarını yok sayma** seçeneğini etkinleştirerek söyleyebilirsiniz.

Tam tersini yapabilir ve Visual Studio'ya **kök** düğümünü **doğru**ayarlayarak *yalnızca* çözüme özgü veya projeye özgü ayarları kullanmasını söyleyebilirsiniz. Visual Studio dosyaları bu düzeyde birleştirmeyi durdurur ve hiyerarşinin yukarısı dosyalarla birleştirmez.

Çözüme özgü ve projeye özgü ayarlar kaynak denetiminde denetlenebilir ve kod tabanında çalışan tüm ekip bunları paylaşabilir.

## <a name="disable-file-nesting-rules-for-a-project"></a>Proje için dosya iç içe geçme kurallarını devre dışı bırakmayı

Belirli çözümler veya projeler için varolan genel dosya iç içe geçme **kurallarını, ekle**yerine sağlayıcı için **kaldırma** eylemini kullanarak devre dışı kullanabilirsiniz. Örneğin, bir projeye aşağıdaki ayarlar kodunu eklerseniz, bu belirli proje için genel olarak var olabilecek tüm **yolSegment** kuralları devre dışı bırakılır:

```json
"dependentFileProviders": {
  "remove": {
    "pathSegment": {}
  }
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [IDE'yi kişiselleştirin](../ide/personalizing-the-visual-studio-ide.md)
- [Visual Studio'da çözümler ve projeler](solutions-and-projects-in-visual-studio.md)
