---
title: EditorConfig
description: Mac için Visual Studio'da tutarlı proje kodlama stillerini etkinleştirmek için editorconfig Mac için Visual Studio.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.technology: vs-ide-install
ms.assetid: 26A0DE31-2FBF-4E1B-99FB-083111AA1680
ms.openlocfilehash: be8f508a0055d4cd7cbacf1c728e6d73c8b281f7
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123962163"
---
# <a name="creating-and-editing-a-custom-editorconfig-file"></a>Özel EditorConfig dosyası oluşturma ve düzenleme

Bu Mac için Visual Studio, kod temeli içinde çalışan herkes için tutarlı kodlama stilleri uygulamak için projenize veya çözümünüze bir [EditorConfig](https://editorconfig.org/) dosyası ekebilirsiniz. EditorConfig dosyasında bildirilen ayarlar, genel metin düzenleyici ayarlarına Mac için Visual Studio önceliklidir. Projeniz veya kod tabanınız içinde editorConfig dosyası kullanmak projeniz için kodlama stilinizi, tercihlerinizi ve uyarılarınızı ayarlamanızı sağlar. Dosya kod tabanınıza bir parçası olduğundan, IDE veya kod düzenleyicisi ne olursa olsun tüm kullanıcıların projenin kodlama uygulamalarına uymasını kolaylaştırır.

[EditorConfig](https://editorconfig.org/) dosyaları, 2017'de olduğu gibi birçok IDE'de ve kod Visual Studio de desteklemektedir.

## <a name="supported-settings"></a>Desteklenen ayarlar

Mac için Visual Studio düzenleyicisi editorConfig özelliklerinin temel [kümelerini destekler:](https://editorconfig.org/#supported-properties)

- `indent_style`
- `indent_size`
- `tab_width`
- `end_of_line`
- `charset`
- `trim_trailing_whitespace`
- `insert_final_newline`
- `root`

EditorConfig ayrıca [C# ile kodlama](/visualstudio/ide/editorconfig-code-style-settings-reference) kuralları desteği de sağlar.

## <a name="add-an-editorconfig-file-to-a-project"></a>Projeye EditorConfig dosyası ekleme

### <a name="adding-a-new-editorconfig-file"></a>Yeni EditorConfig dosyası ekleme

1. Projenizi Mac için Visual Studio. EditorConfig dosyasını eklemek istediğiniz çözümü veya proje düğümünü seçin. Dosyayı çözüm dizinine eklemek çözümde tüm projelere .editorconfig ayarlarını uygular.

2. Düğüme sağ tıklayın ve Yeni Dosya **ekle'>'yi seçerek** Yeni Dosya **iletişim kutusunu** açın:

    ![İçerik menüsü öğeleri](media/editorconfig-image0.png)

3. Misc **> Boş Metin Dosyası'nın adını** **girin.** `.editorconfig` Dosyayı **oluşturmak** ve düzenleyicide açmak için Yeni'ye basın:

    ![Yeni dosya iletişim kutusu](media/editorconfig-image1.png)

    Öğeyi çözüm düzeyinde eklemek, öğeyi otomatik olarak oluşturur ve bir Çözüm Öğeleri **klasörüne iç içe** ekler:

    ![Çözüm paneli içinde görüntülenen çözüm öğesi](media/editorconfig-image1a.png)

4. Dosyayı düzenleyin. Örnek:

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

4. Dosyadan alınan ayarlar, yeni kodlar için geçerlidir, ancak yeni ayarlarla tutarlı olması için mevcut `.editorconfig` kodun yeniden biçimlendirilmemiş olması gerekebilir. Dosyadan mevcut bir kaynak dosyaya ayarları uygulamak için dosyayı açın ve menü `.editorconfig` **çubuğundan > Biçim > Belgeyi** Biçimlendir'i seçin:

    ![Belgeyi Biçimlendir menü öğesi](media/editorconfig-image2.png)

### <a name="adding-an-existing-editorconfig-file"></a>Mevcut EditorConfig dosyasını ekleme

Zaten bir dosya içeren bir proje veya çözümle `.editorconfig` çalışıyorsanız, ayarları uygulamak için hiçbir şey yapmak zorunda değildir. Yeni kod satırları EditorConfig ayarlarına göre biçimlendirildi.

Projeniz içinde mevcut bir dosyayı `.editorconfig` yeniden kullanmak istiyor olabilir. Mevcut bir dosyayı eklemek için şunları yapın:

1. Eklemek istediğiniz klasöre sağ tıklayın ve Dosya Ekle'yi **> seçin.**

2. Gerekli dosyanın dizinine gidin.

3. ile başlayan dosyalar `.` (örneğin, `.editorconfig` ) macOS'ta gizli dosyalardır, bu nedenle **Komut + Shift + tuşlarına basın.** dosyayı görünür `.editorconfig` yapmak için.

4. Dosyayı seçin `.editorconfig` ve Aç'a **tıklayın:**

    ![yeni dosya penceresi ekleme](media/editorconfig-image3b.png)

5. Aşağıdaki iletişim kutusuyla birlikte, Dosyayı dizine kopyala seçeneğini belirleyin ve **Tamam'ı** **seçin:**

    ![Klasöre dosya ekle iletişim kutusu seçenekleri](media/editorconfig-image3.png)

### <a name="reflecting-editorconfig-settings"></a>.editorconfig ayarlarını yansıtma

Kod tabanınıza editorConfig dosyası eklediniz mi, eklenen tüm yeni kodlar belirtilen ayarlara göre otomatik olarak biçimlendirilir. Mevcut kod, kod tabanını biçimlendirmedikçe ayarları otomatik olarak yansıtmaz.

Dosyadan ayarları yansıtmak için, çözüm düğümünü seçin ve menü `.editorconfig` **çubuğundan > Biçim > Belgeyi** Biçimlendir'i seçin:

![Menü çubuğundan belgeyi biçimlendirme](media/editorconfig-image3a.png)

## <a name="editing-an-editorconfig-file"></a>EditorConfig dosyasını düzenleme

EditorConfig dosyaları, ayarları belirtmek için basit bir dosya düzeni kullanır ve önceki bir örnek kullanılarak aşağıda açıklanmıştır:

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

ayarı, `root` `true` `.editorconfig` [EditorConfig'i](#override-editorconfig-settings) Geçersiz Kılma bölümünde anlatıldığı gibi, bu dosyayı kod tabanının en üst dosyası ve projede daha yüksek herhangi bir dosya olarak Ayarlar yok sayılır.

Her bölüm kare (**[ ]**) ayraçları ile ifade edildi ve aşağıdaki özelliklerin ilgili olması gereken dosya türleriyle ilgili bilgileri belirtir.

Yukarıdaki örnekte, bazı ayarlar proje üzerindeki tüm dosyalara uygulanır ve diğerleri yalnızca C# dosyalarına eklenir. Aşağıdaki ekran görüntüleri, ayarlar uygulanmadan önce `.editorconfig` ve uygulandıktan sonra gösterir:

**Önce:**

![editorconfig ayarları uygulanmadan önce](media/editorconfig-image4.png)

**Sonra:**

![editorconfig ayarları uygulandıktan sonra](media/editorconfig-image5.png)

Kullanılabilir EditorConfig ayarları hakkında daha fazla bilgi için resmi belgelerde [](https://editorconfig.org/#supported-properties) [EditorConfig için .NET](/visualstudio/ide/editorconfig-code-style-settings-reference) kodlama kuralı ayarları makalesine ve Desteklenen Özellikler bölümüne bakın.

## <a name="override-editorconfig-settings"></a>EditorConfig'i geçersiz Ayarlar

Her çözümde birden fazla `.editorconfig` dosya olabilir. Mac için Visual Studio dosyaları çözümde üstten aşağıya doğru okuyarak ayarları ekler ve geçersiz `.editorconfig` kılınır. Bu, düzenlemekte olduğunuz `.editorconfig` _dosyaya_ en yakın olan ayarların öncelikli olduğu anlamına gelir. Ayarlar dosyadan aynı klasörden (varsa), ardından üst klasördeki `.editorconfig` `.editorconfig` (varsa) vb. alınır. bulana `root=true` kadar.

Kod tabanının bu _parçasına_ herhangi bir üst düzey dosyadan hiçbir ayar uygulanmay olduğundan emin olmak için, özelliğini alt düzey `.editorconfig` `root=true` dosyanın en üstüne `.editorconfig` ekleyin:

```EditorConfig
# top-most EditorConfig file
root = true
```

## <a name="see-also"></a>Ayrıca bkz.

- [EditorConfig ile özel düzenleyici ayarları oluşturma (Visual Studio üzerinde Windows)](/visualstudio/ide/create-portable-custom-editor-options)