---
title: EditorConfig
description: Mac için Visual Studio'da tutarlı proje kodlama stilleri sağlamak için bir editorconfig dosyası kullanma.
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.technology: vs-ide-install
ms.assetid: 26A0DE31-2FBF-4E1B-99FB-083111AA1680
ms.openlocfilehash: 6f6241c114d636cc8cb01cf5c4bf9ba2b5106701
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "73716897"
---
# <a name="creating-and-editing-a-custom-editorconfig-file"></a>Özel bir EditorConfig dosyası oluşturma ve düzenleme

Mac için Visual Studio'da, kod tabanında çalışan herkes için tutarlı kodlama stilleri uygulamak için projenize veya çözümünüze bir [EditorConfig](https://editorconfig.org/) dosyası ekleyebilirsiniz. EditorConfig dosyasında bildirilen ayarlar, Mac metin düzenleyicisi ayarları için global Visual Studio'dan önce gelir. Projeniz veya codebase içinde bir EditorConfig dosyası kullanarak projeniz için kodlama stilinizi, tercihlerinizi ve uyarılarınızı ayarlamanızı sağlar. Dosya kod tabanınızın bir parçası olduğundan, tüm kullanıcıların kullandıkları IDE veya kod düzenleyicisi ne olursa olsun, bir projenin kodlama uygulamalarına uymalarını kolaylaştırır.

[EditorConfig](https://editorconfig.org/) dosyaları Visual Studio da dahil olmak üzere birçok IDE ve kod düzenleyicisi üzerinde desteklenir.

## <a name="supported-settings"></a>Desteklenen ayarlar

Visual Studio for Mac editörü [EditorConfig özellikleri](https://editorconfig.org/#supported-properties)çekirdek kümesini destekler:

- `indent_style`
- `indent_size`
- `tab_width`
- `end_of_line`
- `charset`
- `trim_trailing_whitespace`
- `insert_final_newline`
- `root`

EditorConfig ayrıca C#'daki [Kodlama kurallarını](/visualstudio/ide/editorconfig-code-style-settings-reference) da destekler.

## <a name="add-an-editorconfig-file-to-a-project"></a>Projeye EditorConfig dosyası ekleme

### <a name="adding-a-new-editorconfig-file"></a>Yeni bir EditorConfig dosyası ekleme

1. Mac için Visual Studio'da projenizi açın. EditorConfig dosyasını eklemek istediğiniz çözüm veya proje düğümünü seçin. Dosyayı çözüm dizinine eklemek, .editorconfig ayarlarını çözümdeki tüm projelere uygular.

2. Düğüme sağ tıklayın ve **Yeni Dosya** iletişim kutusunu açmak için Yeni Dosya **> Ekle'yi** seçin:

    ![İçerik menüsü öğeleri](media/editorconfig-image0.png)

3. **Boş Metin Dosyası > Misc'i** seçin ve ona **Adını** `.editorconfig`verin. Dosyayı oluşturmak ve düzenleyicide açmak için **Yeni'ye** basın:

    ![Yeni dosya iletişim kutusu](media/editorconfig-image1.png)

    Öğeyi çözüm düzeyinde ekleme otomatik olarak oluşturur ve **çözüm öğeleri** klasörüne yerleştirilir:

    ![Çözüm defterinde görüntülenen çözüm öğesi](media/editorconfig-image1a.png)

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

4. `.editorconfig` Dosyadaki ayarlar yazdığınız herhangi bir yeni kod için geçerli dir, ancak varolan kodun yeni ayarlarla tutarlı olması için yeniden biçimlendirilmesi gerekebilir. `.editorconfig` Dosyadaki ayarları varolan bir kaynak dosyaya uygulamak için dosyayı açın ve menü çubuğundan **Belge> biçimlendirme>'>** seçin:

    ![Belge menü öğeni biçimlendir](media/editorconfig-image2.png)

### <a name="adding-an-existing-editorconfig-file"></a>Varolan bir EditorConfig dosyası ekleme

Zaten bir dosya içeren bir `.editorconfig` proje veya çözümle çalışıyorsanız, ayarları uygulamak için yapmanız gereken hiçbir şey yoktur. Yeni kod satırları EditorConfig ayarlarına göre biçimlendirilir.

Projenizdeki varolan `.editorconfig` bir dosyayı yeniden kullanmak isteyebilirsiniz. Varolan bir dosya eklemek için aşağıdakileri yapın:

1. Eklemek istediğiniz klasöre sağ tıklayın ve **Dosya Ekle >'i**seçin.

2. Gerekli dosyanın dizinine göz atın.

3. (vb) `.` `.editorconfig`ile başlayan dosyalar macOS'ta gizli dosyalardır, bu nedenle Komut + Shift + tuşuna **basın.** dosyayı `.editorconfig` görünür hale getirmek için.

4. Dosyayı `.editorconfig` seçin ve **Aç'ı**tıklatın:

    ![yeni bir dosya penceresi ekleme](media/editorconfig-image3b.png)

5. Aşağıdaki iletişim kutusu yla birlikte size sunulduğunda, **dosyayı dizin seçeneğine** kopyala'yı seçin ve **Tamam'ı**seçin:

    ![Klasör iletişim kutusuna dosya ekleme seçenekleri](media/editorconfig-image3.png)

### <a name="reflecting-editorconfig-settings"></a>.editorconfig ayarlarını yansıtma

Codebase'inize bir EditorConfig dosyası eklediğinizde, eklenen yeni kodlar belirtilen ayarlara göre otomatik olarak biçimlendirilir. Varolan kod, kod tabanını biçimlendirmediğiniz sürece ayarları otomatik olarak yansıtmaz.

`.editorconfig` Dosyadaki ayarları yansıtmak için çözüm düğümünü seçin ve menü çubuğundan **Belgeyi biçimlendirme >> >** biçimlendir'i seçin:

![Menü çubuğundan belgeyi biçimlendirme](media/editorconfig-image3a.png)

## <a name="editing-an-editorconfig-file"></a>EditorConfig dosyayı düzenleme

EditorConfig dosyaları, önceki bir örnek kullanılarak aşağıda açıklanan ayarları belirtmek için basit bir dosya düzeni kullanır:

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

Bu `root` `true` dosyayı kod tabanının en üstteki dosyası olarak `.editorconfig` işaretlemek ve projedeki daha yüksek dosyalar, [Geçersiz Kılma DüzenleyicisiConfig Ayarları](#override-editorconfig-settings) bölümünde açıklandığı gibi yoksayılır.

Her bölüm kare (**[ ]**) parantezile gösterilir ve aşağıdaki özelliklerin ilgili olması gereken dosya türleri hakkındaki bilgileri belirtir.

Yukarıdaki örnekte, projedeki tüm dosyalara bazı ayarlar uygulanır ve diğerleri yalnızca C# dosyalarına eklenir. Aşağıdaki ekran görüntüleri, ayarlar `.editorconfig` uygulanmadan önce ve sonra gösterilmektedir:

**Önce**:

![Editorconfig ayarları uygulanmadan önce](media/editorconfig-image4.png)

**Sonra**:

![editorconfig ayarları uygulandıktan sonra](media/editorconfig-image5.png)

Kullanılabilir EditorConfig ayarları hakkında daha fazla bilgi [için, EditorConfig makalesi için .NET kodlama kuralı ayarlarına](/visualstudio/ide/editorconfig-code-style-settings-reference) ve resmi belgelerdeki [Desteklenen Özellikler](https://editorconfig.org/#supported-properties) bölümüne bakın.

## <a name="override-editorconfig-settings"></a>Geçersiz Kılma EditorConfig Ayarları

Her çözümde birden `.editorconfig` fazla dosya olması mümkündür. Mac için Visual `.editorconfig` Studio, çözümde dosyaları yukarıdan aşağıya doğru okur ve ayarlar ekler ve geçersiz kılınar. Bu, düzenlediğiniz dosyaya `.editorconfig` _en yakın_ ayarlardan öncelikli olacağı anlamına gelir. Ayarlar `.editorconfig` dosyadan aynı klasörden (varsa), ana `.editorconfig` klasördeki (varsa) vb. alınır. bulana `root=true`kadar.

Codebase'in bu _no_ bölümüne üst düzey `.editorconfig` dosyalardan hiçbir ayar uygulanmadığından emin `root=true` olmak istiyorsanız, özelliği alt `.editorconfig` düzey dosyanın en üstüne ekleyin:

```EditorConfig
# top-most EditorConfig file
root = true
```

## <a name="see-also"></a>Ayrıca bkz.

- [EditorConfig (Windows'ta Visual Studio) ile özel düzenleyici ayarları oluşturun](/visualstudio/ide/create-portable-custom-editor-options)