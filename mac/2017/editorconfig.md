---
title: EditorConfig
description: Mac için Visual Studio içinde tutarlı proje kodlama stillerini etkinleştirmek için bir editorconfig dosyası kullanma.
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.technology: vs-ide-install
ms.assetid: 26A0DE31-2FBF-4E1B-99FB-083111AA1680
ms.openlocfilehash: 8132a7f92986b853ffc2b20b93d0db34f7ac1880
ms.sourcegitcommit: ba0fef4f5dca576104db9a5b702670a54a0fcced
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73715885"
---
# <a name="creating-and-editing-a-custom-editorconfig-file"></a>Özel bir EditorConfig dosyası oluşturma ve düzenleniyor

Mac için Visual Studio, kod tabanında çalıştırılan herkes için tutarlı kodlama stillerini zorlamak üzere projenize veya çözümünüze bir [Editorconfig](https://editorconfig.org/) dosyası ekleyebilirsiniz. EditorConfig dosyasında belirtilen ayarlar, genel Mac için Visual Studio metin Düzenleyicisi ayarlarından önceliklidir. Projenizde veya kod tabanınızda bir EditorConfig dosyası kullanmak, projeniz için kodlama tarzınızı, tercihlerinizi ve uyarılarını ayarlamanıza olanak sağlar. Dosya, kod tabanınızın bir parçası olduğundan, kullandıkları IDE veya kod düzenleyiciden bağımsız olarak tüm kullanıcıların bir projenin kodlama uygulamalarına bağlı olmasını kolaylaştırır.

[Editorconfig](https://editorconfig.org/) dosyaları, Visual Studio 2017 dahil olmak üzere birçok Ides ve kod düzenleyicilerinde desteklenir.

## <a name="supported-settings"></a>Desteklenen ayarlar

Mac için Visual Studio düzenleyici, [Editorconfig özelliklerinin](https://editorconfig.org/#supported-properties)çekirdek kümesini destekler:

- `indent_style`
- `indent_size`
- `tab_width`
- `end_of_line`
- `charset`
- `trim_trailing_whitespace`
- `insert_final_newline`
- `root`

EditorConfig, C#içindeki [kodlama kurallarını](/visualstudio/ide/editorconfig-code-style-settings-reference) da destekler.

## <a name="add-an-editorconfig-file-to-a-project"></a>Bir projeye EditorConfig dosyası ekleme

### <a name="adding-a-new-editorconfig-file"></a>Yeni bir EditorConfig dosyası ekleniyor

1. Projenizi Mac için Visual Studio açın. EditorConfig dosyasını eklemek istediğiniz çözüm ya da proje düğümünü seçin. Dosyayı çözüm dizinine eklemek,. editorconfig ayarlarını Çözümdeki tüm projelere uygular.

2. Düğüme sağ **tıklayıp yeni dosya iletişim kutusunu** açmak Için **> yeni dosya Ekle** ' yi seçin:

    ![İçerik menü öğeleri](media/editorconfig-image0.png)

3. **Çeşitli > boş metin dosyası** seçin ve `.editorconfig`**adı** verin. **Yeni** ' ye basarak dosyayı oluşturun ve düzenleyicide açın:

    ![Yeni dosya iletişim kutusu](media/editorconfig-image1.png)

    Öğeyi çözüm düzeyinde eklemek, bir **Çözüm öğeleri** klasörü içinde otomatik olarak oluşturur ve oluşturur:

    ![Çözüm panelinde görünen çözüm öğesi](media/editorconfig-image1a.png)

4. Dosyayı düzenleyin. Örneğin:

    ```EditorConfig
    # This file is the top-most EditorConfig file
    root = true

    # All Files
    [*]
    indent_style = space
    indent_size = 8
    insert_final_newline = false
    trim_trailing_whitespace = false

    [*.cs]
    csharp_new_line_before_open_brace = none
    ```

4. `.editorconfig` dosyadaki ayarlar yazdığınız tüm yeni kodlar için geçerli olacaktır, ancak mevcut kodun yeni ayarlarla tutarlı olacak şekilde yeniden biçimlendirilmesi gerekebilir. `.editorconfig` dosyasındaki ayarları var olan bir kaynak dosyasına uygulamak için, dosyayı açın ve menü çubuğundan **belgeyi biçimlendir > düzenle > Biçimlendir** ' i seçin::

    ![Belge menü öğesini Biçimlendir](media/editorconfig-image2.png)

### <a name="adding-an-existing-editorconfig-file"></a>Mevcut bir EditorConfig dosyası ekleniyor

Zaten bir `.editorconfig` dosyası içeren bir proje veya çözümle çalışıyorsanız, ayarları uygulamak için yapmanız gereken bir şey yoktur. Tüm yeni kod satırları EditorConfig ayarlarına göre biçimlendirilir.

Projenizde var olan bir `.editorconfig` dosyasını yeniden kullanmak isteyebilirsiniz. Var olan bir dosyayı eklemek için aşağıdakileri yapın:

1. Eklemek istediğiniz klasöre sağ tıklayın ve Ekle **> dosya Ekle**' yi seçin.

2. Gerekli dosyanın dizinine gidin.

3. `.` (`.editorconfig`gibi) başlayan dosyalar macOS 'taki gizli dosyalardır, bu nedenle **Command + SHIFT +** tuşlarına basın. `.editorconfig` dosyasını görünür hale getirmek için.

4. `.editorconfig` dosyasını seçin ve **Aç**' a tıklayın:

    ![Yeni dosya penceresi ekleme](media/editorconfig-image3b.png)

5. Aşağıdaki iletişim kutusunda, **dosyayı dizine Kopyala** seçeneğini belirleyin ve **Tamam**' ı seçin:

    ![Klasöre dosya Ekle iletişim kutusu seçenekleri](media/editorconfig-image3.png)

### <a name="reflecting-editorconfig-settings"></a>. Editorconfig ayarlarını yansıtma

Kod tabanınıza bir EditorConfig dosyası ekledikten sonra eklenen her yeni kod, belirtilen ayarlara göre otomatik olarak biçimlendirilir. Kod temeli biçimlendirmediğiniz takdirde mevcut kod otomatik olarak ayarları yansıtmaz.

`.editorconfig` dosyadaki ayarları yansıtmak için çözüm düğümünü seçin ve menü çubuğundan **> biçimlendir > Düzenle belge Biçimlendir** ' i seçin:

![Menü çubuğundan belge biçimlendirme](media/editorconfig-image3a.png)

## <a name="editing-an-editorconfig-file"></a>EditorConfig dosyasını Düzenle

EditorConfig dosyaları, daha önceki bir örnek kullanılarak aşağıda açıklanan ayarları belirtmek için basit bir dosya düzeni kullanır:

```EditorConfig
# This file is the top-most EditorConfig file
root = true

# All Files
[*]
indent_style = space
indent_size = 4
insert_final_newline = false
trim_trailing_whitespace = false

[*.cs]
csharp_new_line_before_open_brace = none
```

`root`, bu dosyanın en üst codebase dosyası olarak `true` bayrakları, bu dosya ise [EditorConfig ayarlarını geçersiz kıl](#override-editorconfig-settings) bölümünde açıklandığı gibi, projedeki tüm daha yüksek `.editorconfig` dosyaları yoksayılır.

Her bölüm kare ( **[]** ) ayraçları ile gösterilir ve aşağıdaki özelliklerin ait olduğu dosya türleri hakkında bilgi belirtir.

Yukarıdaki örnekte, bazı ayarlar projedeki tüm dosyalara uygulanır ve diğerleri yalnızca C# dosyalara eklenir. Aşağıdaki ekran görüntüleri `.editorconfig` ayarları uygulandıktan önce ve sonra gösterilmektedir:

**Önce**:

![Editorconfig ayarları uygulanmadan önce](media/editorconfig-image4.png)

**Sonra**:

![editorconfig ayarları uygulandıktan sonra](media/editorconfig-image5.png)

Kullanılabilir EditorConfig ayarları hakkında daha fazla bilgi için bkz. [editorconfig için .net kodlama kuralı ayarları](/visualstudio/ide/editorconfig-code-style-settings-reference) ve resmi belgelerindeki [desteklenen özellikler](https://editorconfig.org/#supported-properties) bölümü.

## <a name="override-editorconfig-settings"></a>EditorConfig ayarlarını geçersiz kıl

Her bir çözümde birden fazla `.editorconfig` dosyası olması mümkündür. Mac için Visual Studio, çözümdeki en yukarıdan aşağıya `.editorconfig` dosyaları okur, bu ayarları olduğu gibi ekleyip geçersiz kılar. Bu, düzenlemekte olduğunuz dosyaya _en yakın_ `.editorconfig` ayarların öncelikli olacağı anlamına gelir. Ayarlar `.editorconfig` dosyadan aynı klasöre (varsa), ardından üst klasördeki `.editorconfig` (varsa), vb. alınır. `root=true`bulana kadar.

Kod temelinin bu bölümüne daha yüksek düzeydeki `.editorconfig` dosyalarından _hiçbir ayar uygulanmadığından_ emin olmak istiyorsanız, `root=true` özelliğini alt düzey `.editorconfig` dosyasının en üstüne ekleyin:

```EditorConfig
# top-most EditorConfig file
root = true
```

## <a name="see-also"></a>Ayrıca bkz.

- [EditorConfig ile özel düzenleyici ayarları oluşturma (Windows üzerinde Visual Studio)](/visualstudio/ide/create-portable-custom-editor-options)