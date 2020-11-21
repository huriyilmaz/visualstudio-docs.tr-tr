---
title: Çözüm Gezgini için dosya iç içe kuralları
description: Çözüm Gezgini dosya iç içe kuralları, önayarları ve özelleştirme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 05/25/2018
ms.topic: conceptual
helpviewer_keywords:
- file nesting
- Solution Explorer, file nesting
author: angelosp
ms.author: angelpe
manager: jillfra
ms.openlocfilehash: 5425c255e85a2785383f1e8e718340fc2049e0c4
ms.sourcegitcommit: 66cda27b63c9b55782b1db223a6dbda9f8cabe13
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2020
ms.locfileid: "95006698"
---
# <a name="file-nesting-in-solution-explorer"></a>Çözüm Gezgini’nde dosya iç içe yerleştirme

Onları düzenlemeye ve bulmayı kolaylaştırmak için ilgili dosyaları **Çözüm Gezgini** . Örneğin, bir projeye Windows Forms form eklerseniz, formun kod dosyası, **Çözüm Gezgini** formun altına iç içe geçmiş olur. ASP.NET Core projelerinde, iç içe geçmiş bir adım daha alınabilir. Dosya iç içe **ön ayarları arasından**, **varsayılan** ve **Web** arasında seçim yapabilirsiniz. Ayrıca [dosyaların iç içe geçmiş olduğunu](#customize-file-nesting) [ve çözüme özel ve projeye özel ayarlar oluşturmayı](#create-project-specific-settings)özelleştirebilirsiniz.

> [!NOTE]
> Özelliği şu anda yalnızca ASP.NET Core projeleri için desteklenir.

## <a name="file-nesting-options"></a>Dosya iç içe seçenekleri

![Dosya iç içe geçirmeyi açmak için düğme](media/filenesting_onoff.png)

Özelleştirilmemiş dosya iç içe geçme için kullanılabilen seçenekler şunlardır:

* **Kapalı**: Bu seçenek, herhangi bir iç içe geçme olmadan dosyaların düz bir listesini sağlar.

* **Varsayılan**: Bu seçenek, **Çözüm Gezgini**' de varsayılan dosya iç içe geçme davranışını sağlar. Belirli bir proje türü için hiçbir ayar yoksa, projedeki hiçbir dosya iç içe değildir. Ayarlar varsa, örneğin, bir Web projesi için, iç içe geçme uygulanır.

* **Web**: Bu seçenek, **Web** dosyası iç içe davranışını geçerli Çözümdeki tüm projelere uygular. Bu, çok sayıda kurala sahiptir ve sizi göz önünde bulundurmanızı ve bize söylediklerinizi söyliyoruz. Aşağıdaki ekran görüntüsünde, bu seçenekle aldığınız dosya iç içe geçme davranışına ilişkin birkaç örnek vurgulanmıştır:

   ![Çözüm Gezgini’nde dosya iç içe yerleştirme](media/filenesting.png)

## <a name="customize-file-nesting"></a>Dosya iç içe geçirmeyi Özelleştir

Hazır olma durumunu beğenmezseniz, dosyaları iç içe aktarma **Çözüm Gezgini** söylemek için kendi özel dosya iç içe geçmiş ayarlarınızı oluşturabilirsiniz. İstediğiniz kadar çok sayıda özel dosya iç içe ayarı ekleyebilir ve bunları istediğiniz gibi değiştirebilirsiniz. Yeni bir özel ayar oluşturmak için boş bir dosyayla başlayabilir veya **Web** ayarlarını başlangıç noktası olarak kullanabilirsiniz:

![Özel dosya iç içe kuralları ekleme](media/filenesting_addcustom.png)

Zaten işlev gören bir şeyle çalışmak daha kolay olduğundan, başlangıç noktası olarak **Web** ayarlarını kullanmanızı öneririz. Başlangıç noktası olarak **Web** ayarlarını kullanıyorsanız, dosyadaki *.filenesting.js* aşağıdaki dosyaya benzer şekilde görünür:

![Özel ayarlar için temel olarak mevcut dosya iç içe kurallarını kullanın](media/filenesting_editcustom.png)

Şimdi düğüm **Dependentfileproviders** ve onun alt düğümlerine odaklanalım. Her alt düğüm, Visual Studio 'Nun dosyaları iç içe aktarmak için kullanabileceği bir kural türüdür. Örneğin, **aynı dosya adına sahip ancak farklı bir uzantı** tek bir kural türüdür. Kullanılabilir kurallar şunlardır:

* **Extensiontoextension**: *dosya. TS* altındaki *file.js* iç içe yerleştirmek için bu kural türünü kullanın

* **Filesonfixtoextension**: *file.js* altına *file-vsdoc.js* iç içe yerleştirmek için bu kural türünü kullanın

* **Addedexgeri**: *file.html* altına *file.html. css* iç içe yerleştirmek için bu kural türünü kullanın

* **PathSegment**: *jquery.js* altına *jquery.min.js* iç içe yerleştirmek için bu kural türünü kullanın

* **allExtensions**: dosyayı iç içe aktarmak için bu kural türünü kullanın *.* * *file.js* altında

* **Filetofile**: *. bowerrc* altında *bower.js* iç içe yerleştirmek için bu kural türünü kullanın

### <a name="the-extensiontoextension-provider"></a>ExtensionToExtension sağlayıcısı

Bu sağlayıcı belirli dosya uzantılarını kullanarak dosya iç içe kuralları tanımlamanıza olanak sağlar. Aşağıdaki örneği inceleyin:

![extentionToExtension örnek kuralları](media/filenesting_extensiontoextension.png) ![extentionToExtension örnek etkisi](media/filenesting_extensiontoextension_effect.png)

* *cart.js* Ilk **extensiontoextension** kuralı nedeniyle *sepet. TS* altında iç içe geçmiş

* *cart.js* *sepet. TSX* altında iç içe değildir, çünkü **. TS** kurallarda **. TSX** 'den önce gelir ve yalnızca bir üst öğe olabilir

* *Light. css* , Ikinci **extensiontoextension** kuralı nedeniyle *Light. Sass* altında iç içe yerleştirilmiş

* Üçüncü **Extensiontoextension** kuralı nedeniyle *home.html* *Home.MD* altında iç içe geçmiş

### <a name="the-filesuffixtoextension-provider"></a>Filesonfixtoextension sağlayıcısı

Bu sağlayıcı, yalnızca uzantı yerine kuralın dosyanın sonekine baktığı tek fark ile yalnızca **Extensiontoextension** sağlayıcısı gibi çalışmaktadır. Aşağıdaki örneği inceleyin:

![Filesonfixtoextension örnek kuralları](media/filenesting_filesuffixtoextension.png) ![Filesonfixtoextension örnek etkisi](media/filenesting_filesuffixtoextension_effect.png)

* *portal-vsdoc.js* **Filesonfixtoextension** kuralı nedeniyle *portal.js* iç içe geçmiş

* kuralın diğer her yönü, **Extensiontoextension** ile aynı şekilde çalışmaktadır

### <a name="the-addedextension-provider"></a>Addedexgeri sağlayıcısı

Bu sağlayıcı, dosyaları ek bir uzantı olmadan dosya altında ek bir uzantıya sahip olarak alır. Ek uzantı yalnızca tam dosya adının sonunda yer alabilir.

Aşağıdaki örneği inceleyin:

![Addedexgeri örnek kuralları](media/filenesting_addedextension.png) ![Addedexgerilim örnek etkisi](media/filenesting_addedextension_effect.png)

* *file.html. css* , **Addedexgerme** kuralı nedeniyle *file.html* altında iç içe yerleştirilmiş

> [!NOTE]
> Kural için herhangi bir dosya uzantısı belirtmezsiniz `addedExtension` ; otomatik olarak tüm dosya uzantıları için geçerlidir. Diğer bir deyişle, başka bir dosya ile aynı ada ve uzantıya sahip herhangi bir dosya ve uçtaki ek bir uzantı, diğer dosyanın altında iç içe geçmiş olur. Bu sağlayıcının etkisini yalnızca belirli dosya uzantılarına göre sınırlandıryükleyemezsiniz.

### <a name="the-pathsegment-provider"></a>PathSegment sağlayıcısı

Bu sağlayıcı, dosyaları ek bir uzantı olmadan bir dosya altında ek bir uzantıya sahip olarak alır. Ek uzantı yalnızca tam dosya adının ortasında yer alabilir.

Aşağıdaki örneği inceleyin:

![pathSegment örnek kuralları](media/filenesting_pathsegment.png) ![pathSegment örnek etkisi](media/filenesting_pathsegment_effect.png)

* **PathSegment** kuralı nedeniyle *jquery.js* *jquery.min.js* iç içe geçmiş

> [!NOTE]
> - Kural için belirli bir dosya uzantısı belirtmezseniz `pathSegment` , tüm dosya uzantıları için geçerlidir. Diğer bir deyişle, başka bir dosya ile aynı ada ve uzantıya sahip herhangi bir dosya ve ortadaki ek bir uzantı diğer dosyanın altında iç içe geçmiş olur.
> - `pathSegment`Kuralın etkisini aşağıdaki şekilde belirterek belirli dosya uzantılarına göre sınırlayabilirsiniz:
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

### <a name="the-allextensions-provider"></a>AllExtensions sağlayıcısı

Bu sağlayıcı, herhangi bir uzantıya sahip, ancak aynı temel dosya adına sahip dosyalar için dosya iç içe kuralları tanımlamanızı sağlar. Aşağıdaki örneği inceleyin:

![allExtensions örnek kuralları](media/filenesting_allextensions.png) ![allExtensions örnek etkisi](media/filenesting_allextensions_effect.png)

* *Template.cs* ve *template.doc* **allExtensions** kuralı nedeniyle *Template.tt* altında iç içe geçmiş.

### <a name="the-filetofile-provider"></a>FileToFile sağlayıcısı

Bu sağlayıcı, tüm dosya adlarını temel alarak dosya iç içe kuralları tanımlamanıza olanak sağlar. Aşağıdaki örneği inceleyin:

![fileToFile örnek kuralları](media/filenesting_filetofile.png) ![fileToFile örnek etkisi](media/filenesting_filetofile_effect.png)

* *. bowerrc* , **filetofile** kuralı nedeniyle *üzerindebower.js* iç içe yerleştirilmiş

### <a name="rule-order"></a>Kural sırası

Özel ayarlar dosyanızın her bölümünde sıralama önemlidir. Kuralları, **Dependentfileprovider** düğümünün içine yukarı veya aşağı taşıyarak kuralların yürütüldüğü sırayı değiştirebilirsiniz. Örneğin, dosya **. TS** 'nin üst öğesini ve **Dosya** yapan başka bir kuralı **file.js** yapan bir kuralınız varsa, dosya **. TS**'nin üst öğesi, dosyada göründükleri sıra, üç dosya olduğunda iç içe geçme davranışını belirler. **Dosya. TS** 'nin yalnızca bir üst öğesi olabilir, bu kural ilk WINS 'i yürütür.

Yalnızca bölüm içindeki dosyalar için değil, kural bölümlerinin kendileri için sıralama de önemlidir. Dosya çifti bir dosya iç içe kuralıyla eşleştirildiği anda, dosyada daha fazla olan diğer kurallar yok sayılır ve sonraki dosya çifti işlenir.

### <a name="file-nesting-button"></a>Dosya iç içe düğmesi

Kendi özel ayarlarınız dahil olmak üzere tüm ayarları, **Çözüm Gezgini** içindeki aynı düğme aracılığıyla yönetebilirsiniz:

![Özel dosya iç içe kuralları etkinleştir](media/filenesting_activatecustom.png)

## <a name="create-project-specific-settings"></a>Projeye özgü ayarlar oluştur

Her bir çözümün ve projenin sağ tıklama menüsünde (bağlam menüsü), çözüme özgü ve projeye özel ayarlar oluşturabilirsiniz:

![Çözüme ve projeye özel iç içe geçme kuralları](media/filenesting_solutionprojectspecific.png)

Çözüme özgü ve projeye özel ayarlar, etkin Visual Studio ayarlarıyla birleştirilir. Örneğin, projeye özgü boş bir ayarlar dosyanız olabilir, ancak **Çözüm Gezgini** dosyaları iç içe geçirme işlemi devam etmektedir. İç içe geçme davranışı çözüme özgü ayarlardan ya da Visual Studio ayarlarından geliyor. Dosya iç içe geçme ayarlarını birleştirme önceliği: Visual Studio > çözüm > projesi.

Visual Studio 'ya, **Tools** dosya iç içe ASP.NET Core Araçlar Seçenekler altında **çözümü ve proje ayarlarını yoksay** seçeneğini etkinleştirerek çözüme özgü ve projeye özgü ayarları yok saymasını söyleyebilirsiniz  >  **Options**  >  **ASP.NET Core**  >  **File Nesting**.

Bunun tersini yapabilir ve Visual Studio 'ya *yalnızca* çözüme özgü veya projeye özgü ayarları kullanarak **kök** düğümü **true** olarak ayarlayarak bunu söyleyebilirsiniz. Visual Studio, dosyaları bu düzeyde birleştirmeyi durduruyor ve hiyerarşiyi daha üst düzeydeki dosyalarla birleştirmez.

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
- [Visual Studio 'da çözümler ve projeler](solutions-and-projects-in-visual-studio.md)
