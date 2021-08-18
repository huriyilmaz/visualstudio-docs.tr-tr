---
title: Dosya iç içe yerleştirme kuralları Çözüm Gezgini
description: Dosya iç içe Çözüm Gezgini, ön ayarlar ve özelleştirme hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 05/25/2018
ms.topic: conceptual
helpviewer_keywords:
- file nesting
- Solution Explorer, file nesting
author: angelosp
ms.author: angelpe
manager: jmartens
ms.technology: vs-ide-general
ms.openlocfilehash: c1b91bf55dfe56737464bf5b333b365f6a5bb882
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122109311"
---
# <a name="file-nesting-in-solution-explorer"></a>Çözüm Gezgini’nde dosya iç içe yerleştirme

**Çözüm Gezgini,** düzenlemeye ve daha kolay bulunmasına yardımcı olmak için ilgili dosyaları iç içe yerleştirmenizi sağlar. Örneğin, bir projeye Windows Formlar formu eklersiniz, formun kod dosyası formun altına **Çözüm Gezgini.** Bu ASP.NET Core, dosya iç içe yerleştirme bir adım ileri atabilirsiniz. Dosya iç içe yerleştirme ön ayarları **Kapalı,** Varsayılan ve Web **arasında** seçim **seçebilirsiniz.** Ayrıca dosyaların iç [içe nasıl iç içe geçmiş olduğunu özelleştirilebilir veya](#customize-file-nesting) [çözüme özgü ve projeye özgü ayarlar oluşturabilirsiniz.](#create-project-specific-settings)

> [!NOTE]
> Özellik şu anda yalnızca projelerde ASP.NET Core desteklene sahiptir.

## <a name="file-nesting-options"></a>Dosya iç içe yerleştirme seçenekleri

![Dosya iç içe yerleştirmeyi açma/kapatma düğmesi](media/filenesting_onoff.png)

Özelleştirilmeyen dosya iç içe yerleştirme seçenekleri şunlardır:

* **Kapalı:** Bu seçenek, iç içe yerleştirmeye gerek kalmadan düz bir dosya listesi sağlar.

* **Varsayılan:** Bu seçenek, dosya iç içe yerleştirme davranışını varsayılan olarak **Çözüm Gezgini.** Bir proje türü için hiçbir ayar yoksa, proje içinde hiçbir dosya iç içe yerleştirmez. Örneğin, bir web projesi için ayarlar varsa iç içe yerleştirme uygulanır.

* **Web:** Bu **seçenek, Geçerli çözümde** yer alan tüm projelere Web dosyası iç içe yerleştirme davranışını uygular. Çok sayıda kuralı vardır ve bu kurala göz atarak bize ne düşünmekte olduğunu anlatmayı teşvik ederiz. Aşağıdaki ekran görüntüsünde, bu seçenekle elde eden dosya iç içe yerleştirme davranışına yalnızca birkaç örnek vurgulanır:

   ![Çözüm Gezgini’nde dosya iç içe yerleştirme](media/filenesting.png)

## <a name="customize-file-nesting"></a>Dosya iç içe yerleştirmeyi özelleştirme

Kutudan çıkararak elde etmek istediğiniz ayarların pek bir şey olmadığınız gibi, dosyaları nasıl iç içe yerleştirmeniz Çözüm Gezgini kendi **özel dosya iç içe** yerleştirme ayarlarınızı oluşturabilirsiniz. İstediğiniz sayıda özel dosya iç içe yerleştirme ayarı ekleyebilir ve aralarında istediğiniz şekilde geçiş yapabilirsiniz. Yeni bir özel ayar oluşturmak için boş bir dosyayla başlayabilir veya başlangıç noktanız **olarak Web** ayarlarını kullanabilirsiniz:

![Özel dosya iç içe yerleştirme kuralları ekleme](media/filenesting_addcustom.png)

Zaten çalışır durumda olan bir şey ile çalışmak daha kolay olduğundan başlangıç noktanız olarak **Web** ayarlarını kullanmanızı öneririz. Başlangıç noktanız **olarak Web** ayarlarını kullanırsanız,.filenesting.js *aşağıdaki* dosyaya benzer:

![Özel ayarlar için temel olarak mevcut dosya iç içe yerleştirme kurallarını kullanın](media/filenesting_editcustom.png)

Şimdi düğüm **bağımlıFileProviders ve alt** düğümlerine odaklanın. Her alt düğüm, dosyaları iç içe Visual Studio kullanabileceğiniz bir kural t t tür. Örneğin, **aynı dosya adı, ancak farklı bir uzantıya sahip olmak** bir kural t t'dır. Kullanılabilir kurallar:

* **extensionToExtension:** *File.ts* altında iç *içe* file.jsiçin bu tür bir kural kullanın

* **fileSuffixToExtension:** Bu tür bir kuralı kullanarak dosyafile-vsdoc.js *iç* içe *file.js*

* **addedExtension:** *l.css'i* file.html altında iç içefile.htm *kullanın*

* **pathSegment:** Bu tür bir kuralı kullanarakjquery.min.js *iç* içe *jquery.js*

* **allExtensions:** Dosyayı iç içe yerleştirmek için bu kural türünü *kullanın.* * altında *file.js*

* **fileToFile:** *.bowerrc* altındaki dosyaları iç *içebower.js* için bu tür bir kural kullanın

### <a name="the-extensiontoextension-provider"></a>extensionToExtension sağlayıcısı

Bu sağlayıcı, belirli dosya uzantılarını kullanarak dosya iç içe yerleştirme kuralları tanımlamanızı sağlar. Aşağıdaki örneği inceleyin:

![extentionToExtension örnek kuralları](media/filenesting_extensiontoextension.png) ![extentionToExtension örnek etkisi](media/filenesting_extensiontoextension_effect.png)

* *cart.js* ilk **extensionToExtension** kuralı nedeniyle *cart.ts* altında iç içe geçmiş

* *cart.js* **.tsx,** kurallarda **.tsx'den** önce geldiğinden ve yalnızca bir üst öğe olduğundan, bu öğe *cart.tsx* altında iç içe iç içe yerleştirmez

* ikinci **extensionToExtension** kuralı nedeniyle *light.css* *light.sass* altında iç içe geçmiş

* *home.html,* üçüncü **extensionToExtension** *kuralı home.md* altında iç içe geçmiş

### <a name="the-filesuffixtoextension-provider"></a>fileSuffixToExtension sağlayıcısı

Bu sağlayıcı **extensionToExtension** sağlayıcısı gibi çalışır ve tek fark, kuralın dosyanın yalnızca uzantı yerine son eke bakmış olmasıdır. Aşağıdaki örneği inceleyin:

![fileSuffixToExtension örnek kuralları](media/filenesting_filesuffixtoextension.png) ![fileSuffixToExtension örnek etkisi](media/filenesting_filesuffixtoextension_effect.png)

* *portal-vsdoc.js,* **fileSuffixToExtension** kuralı *nedeniyle* portal.jsaltında iç içe geçmiş

* kuralın diğer tüm yönleri **extensionToExtension ile aynı şekilde çalışır**

### <a name="the-addedextension-provider"></a>addedExtension sağlayıcısı

Bu sağlayıcı, ek uzantıya sahip dosyaları dosyanın altına ek uzantı olmadan iç içe yerleştirme. Ek uzantı yalnızca tam dosya adı sonunda görünebilir.

Aşağıdaki örneği inceleyin:

![addedExtension örnek kuralları](media/filenesting_addedextension.png) ![addedExtension örnek etkisi](media/filenesting_addedextension_effect.png)

* *file.html.css,* **addedExtension** *kuralıfile.html* altında iç içe geçmiştir

> [!NOTE]
> Kural için herhangi bir dosya uzantısı belirtmezsiniz; tüm `addedExtension` dosya uzantılarına otomatik olarak uygulanır. Diğer bir ifadeyle, başka bir dosyayla aynı adı ve uzantıyı ve sonunda ek bir uzantıyı olan tüm dosyalar diğer dosyanın altına iç içe geçmiş olur. Bu sağlayıcının etkisini yalnızca belirli dosya uzantılarıyla sınırlayaamazsiniz.

### <a name="the-pathsegment-provider"></a>pathSegment sağlayıcısı

Bu sağlayıcı, ek uzantılı dosyaları ek uzantı olmadan bir dosyanın altına iç içe yerleştirme. Ek uzantı yalnızca tam dosya adı ortasında görünebilir.

Aşağıdaki örneği inceleyin:

![pathSegment örnek kuralları](media/filenesting_pathsegment.png) ![pathSegment örnek etkisi](media/filenesting_pathsegment_effect.png)

* *jquery.min.js* **pathSegment** *kuralıjquery.js* iç içe geçmiş

> [!NOTE]
> - Kural için belirli bir dosya uzantısı `pathSegment` belirtmezseniz, bu tüm dosya uzantıları için geçerlidir. Başka bir ifadeyle, başka bir dosyayla aynı adı ve uzantıyı ve ortadaki ek bir uzantıyı olan tüm dosyalar diğer dosyanın altına iç içe geçmiştir.
> - Kuralın etkisini aşağıdaki `pathSegment` şekilde belirterek belirli dosya uzantılarıyla sınırabilirsiniz:
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

Bu sağlayıcı, aynı temel dosya adı olan herhangi bir uzantıya sahip dosyalar için dosya iç içe yerleştirme kuralları tanımlamanızı sağlar. Aşağıdaki örneği inceleyin:

![allExtensions örnek kuralları](media/filenesting_allextensions.png) ![allExtensions örnek etkisi](media/filenesting_allextensions_effect.png)

* *template.cs* *vetemplate.doc,* **allExtensions** *template.tt* altında iç içe geçmiştir.

### <a name="the-filetofile-provider"></a>fileToFile sağlayıcısı

Bu sağlayıcı, dosya adlarına göre dosya iç içe yerleştirme kuralları tanımlamanızı sağlar. Aşağıdaki örneği inceleyin:

![fileToFile örnek kuralları](media/filenesting_filetofile.png) ![fileToFile örnek etkisi](media/filenesting_filetofile_effect.png)

* **fileToFile** kuralı nedeniyle *.bowerrc* *bower.js* altında iç içe geçmiş

### <a name="rule-order"></a>Kural sırası

Sıralama, özel ayarlar dosyanın her bölümünde önemlidir. **DependentFileProvider** düğümünün içinde yukarı veya aşağı hareket ettirerek kuralların yürütülme sıralarını değiştirebilirsiniz. Örneğin, **file.js'i file.ts'nin** üst öğesi yapan bir kuralınız ve  **file.coffee'i** **file.ts'nin** üst öğesi yapan başka bir kuralınız varsa, üç dosyanın da mevcut olduğunda dosyada görünme sırası iç içe yerleştirme davranışını belirtir. **file.ts yalnızca** bir üst öğeye sahip olduğu için, ilk yürütülen kural kazanır.

Sıralama, yalnızca bir bölüm içindeki dosyalar için değil kural bölümleri için de önemlidir. Bir dosya çifti bir dosya iç içe yerleştirme kuralıyla eşleştiriliyorsa, dosyanın daha aşağılarında yer alan diğer kurallar yoksayılır ve sonraki dosya çifti işlenir.

### <a name="file-nesting-button"></a>Dosya iç içe yerleştirme düğmesi

Kendi özel ayarlarınız da dahil olmak üzere tüm ayarları, aynı düğmeyi kullanarak **Çözüm Gezgini:**

![Özel dosya iç içe yerleştirme kurallarını etkinleştirme](media/filenesting_activatecustom.png)

## <a name="create-project-specific-settings"></a>Projeye özgü ayarlar oluşturma

Her çözümün ve projenin sağ tıklama menüsü (bağlam menüsü) aracılığıyla çözüme özgü ve projeye özgü ayarlar oluşturabilirsiniz:

![Çözüm ve projeye özgü iç içe yerleştirme kuralları](media/filenesting_solutionprojectspecific.png)

Çözüme özgü ve projeye özgü ayarlar, etkin Visual Studio birlikte kullanılır. Örneğin, projeye özgü boş bir ayarlar dosyanız olabilir, ancak **Çözüm Gezgini** dosyaları iç içe geçirme işlemi devam etmektedir. iç içe geçme davranışı çözüme özgü ayarlardan veya Visual Studio ayarlarından geliyor. dosya iç içe geçme ayarlarını birleştirme önceliği: Visual Studio > çözüm > Project.

   >    >    >  **dosya iç içe** ASP.NET Core araç seçenekleri altındaki çözümü ve proje ayarlarını yoksay seçeneğini etkinleştirerek çözüme özgü ve projeye özgü ayarları yok saymaya Visual Studio söyleyebilirsiniz.

**kök** düğümü **true** olarak ayarlayarak *yalnızca* çözüme özgü veya projeye özgü ayarları kullanmak için Visual Studio tersini yapabilir ve bunu söyleyebilirsiniz. Visual Studio, dosyaları bu düzeyde birleştirmeyi durduruyor ve hiyerarşiyi daha üst düzeydeki dosyalarla birleştirmez.

Çözüme özgü ve projeye özgü ayarlar kaynak denetimine iade edilebilir ve kod temeli üzerinde çalışma yapan tüm takım bunları paylaşabilir.

## <a name="disable-file-nesting-rules-for-a-project"></a>Bir proje için dosya iç içe kurallarını devre dışı bırak

Belirli çözümler veya projeler için, **Ekle** yerine bir sağlayıcının **Kaldır** eylemini kullanarak mevcut genel dosya iç içe kurallarını devre dışı bırakabilirsiniz. Örneğin, bir projeye aşağıdaki ayar kodunu eklerseniz, bu belirli proje için genel olarak mevcut olabilecek tüm **PathSegment** kuralları devre dışı bırakılır:

```json
"dependentFileProviders": {
  "remove": {
    "pathSegment": {}
  }
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [IDE’yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md)
- [Visual Studio çözümler ve projeler](solutions-and-projects-in-visual-studio.md)
