---
title: Kod Parçacıkları
description: Mac için Visual Studio ' de kod parçacıklarını verimli bir şekilde kullanma
author: heiligerdankgesang
ms.author: dominicn
ms.date: 02/07/2019
ms.assetid: 0FE27C0C-A861-4133-A74E-8D0505CF5342
ms.openlocfilehash: 96344b72dd27095f8b9060078112fb767b1338fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74984812"
---
# <a name="code-snippets"></a>Kod parçacıkları

Genellikle _kod şablonları_olarak anılan kod parçacıkları, önceden yazılmış kod bloklarının eklenmesine ve düzenlenmesine izin veren verimli programlama için yararlıdır. Kod parçacıklarını kullanmak, sık kullanılan desenleri kolayca eklemek veya geliştirici olarak sözdiziminin ne zaman öğreneceğinizden yeni desenler öğrenmek için kullanışlı olabilir. C#, F #, HTML, XML, Python ve Razor için sunulan şablonlar vardır.

Bu bölümde kod içinde kod parçacıklarının nasıl oluşturulacağı, ekleneceği ve kullanılacağı açıklanmaktadır.

## <a name="inserting-a-snippet"></a>Kod parçacığı ekleme

Kod parçacıkları eklemenin bazı farklı yolları vardır, bazıları aşağıda açıklanmıştır:

- **Sekme genişletme** &ndash; Şablon adını yazmaya başlayın, listeden seçin ve eklemek için **sekme** **tuşuna basın** :

  ![Kodda sekme genişletme](media/source-editor-image13.png)

- **Araç kutusu** &ndash; Tüm kod parçacıklarının listesini göstermek için araç kutusu panelini kullanın. Araç kutusundaki herhangi bir şablonu kaynak kodda doğru konuma sürükleyin:

  [![Araç kutusundaki kod parçacıkları](media/source-editor-image14-sml.png)](media/source-editor-image14.png#lightbox)

- **Şablon Ekle komutu** &ndash; Şu anda şablon eklemek için ayarlanmış varsayılan anahtar bağlama yok. Bir tane oluşturmak için **Visual Studio > tercihleri > anahtar bağlamaları** ' na gidin ve arama yapın `template` . Bu, istenen anahtar bağlamasının düzenleme bağlama alanına eklenmesini sağlar ve ardından **Uygula**' ya tıklayın:

  ![İç içe şablon komutu](media/source-editor-image15.png)

## <a name="creating-a-new-template"></a>Yeni şablon oluşturma

Kullanabileceğiniz ve düzenleyebileceğiniz çeşitli dillerde birçok mevcut şablon varsa, **Visual Studio > tercihleri > metin düzenleyicisi > kod parçacıkları**' na giderek yeni şablonlar da eklenebilir.

![Yeni şablonu iç içe](media/source-editor-image12.png)

Kod parçacıkları oluşturmak veya düzenlemek için **Ekle** veya **Düzenle** düğmelerine basın.

## <a name="keywords-in-code-snippets"></a>Kod parçacıkları içindeki anahtar sözcükler

Bir kod parçacığı düzenleyiciye eklendikten sonra, tanımlanan tüm anahtar sözcükler vurgulanır ve bunlar arasında sekme ile düzenlenebilir. Anahtar sözcükler, kod parçacığında bir "değişken" gibi davranır ve `$` anahtar sözcüğünün adından önce ve sonra bir dolar işareti girilerek tanımlanır. 

**Şablonu Düzenle** penceresi aşağıda gösterilmektedir ve yerleşik `prop` kod parçacığı düzenlenmelidir. Kod parçacığı, &ndash; `$type$` `$name$` &ndash; pencerenin sağ tarafında daha fazla özellik kümesine (varsayılan değer ve araç ipucu gibi) sahip olabilecek iki anahtar sözcük içerir.

![Şablon penceresini Düzenle](media/source-editor-image12z.png)

Aşağıdaki alanlar bir kod parçacığını tanımlamak için kullanılır:

- **Kısayol** &ndash; Parçacığı eklemek için Kullanıcı tarafından kullanılacak metin.
- **Grup** &ndash; Kod parçacıkları, bu değer kullanılarak kod parçacığı içeriği menüsünde birlikte gruplandırılır.
- **Açıklama** &ndash; Kod parçacığının amacının açıklaması.
- **MIME** &ndash; Kod parçacığının hangi dosya türlerini kullanılabilir olduğunu denetler.
- **Genişletilebilir şablon** &ndash; Bu, kod parçacığının, kısayolu yazarak imlecin imlece eklenebilmesini sağlamak için kontrol edin.
- **Şablonla** &ndash; çevredir Bu kısayolu düzenleyicideki **... içerik menüsüyle çevrelemek** için bu seçeneği işaretleyin.
- **Şablon metni** &ndash; Düzenleyiciye eklenecek olan gerçek kod parçacığı. Anahtar sözcük yer tutucuları, bir belirteci dolar işareti gibi çevreleyerek tanımlanabilir. `$type$`.
- **Anahtar sözcük özelliği paneli** &ndash; Pencerenin sağ tarafında en üstteki açılan listeyi kullanarak bir anahtar sözcük (örn `type` .) seçin ve varsayılan değer ve araç ipucu gibi özellikleri düzenleyin.

## <a name="using-keywords-in-the-editor"></a>Düzenleyicide anahtar sözcükleri kullanma

Yukarıda tanımlanan gibi anahtar sözcüklerle bir kod parçacığı kullanmak için, kısayolu yazın ve **Tab** tuşuna iki kez basın ve kod parçacığı içerikleri imlecin üzerine eklenir:

![Anahtar sözcükleri gösteren parçacık ekleniyor](media/source-editor-image12a.png)

**Tab** `object` `MyProperty` Sınıfınızın kod parçacığını özelleştirmek için Tab tuşuna basın.

Anahtar sözcüğü bir kod parçacığında yinelenebilir, `for` Örneğin bu örnek, `$i$` anahtar sözcüğünün 3 kez göründüğünü fark edebilirsiniz:

![Yinelenen anahtar sözcüklerle kod parçacığı şablonu](media/source-editor-image12b.png)

Düzenleyicide kullanıldığında **Tab** tuşu ilk ve arasında geçiş yapar `i` `max` . `i`Farklı bir değişken adıyla üzerine yaz yaparsanız, üç örnek de güncelleştirilir:

![Birden çok anahtar sözcük gösteren yerleştirilmiş kod parçacığı](media/source-editor-image12c.png)

### <a name="reserved-keywords"></a>Ayrılmış anahtar sözcükler

Bir kod parçacığında kullanabileceğiniz iki ayrılmış anahtar sözcük vardır:

- `$selected$`&ndash;Kod parçacığında **şablonla birlikte** yer alıyorsa, bu anahtar sözcük, kod parçacığı seçildiğinde düzenleyicide vurgulanan metinle birlikte değişir.
- `$end$`&ndash;Kullanıcı bir kod parçacığında anahtar sözcükleri düzenlemesini bitirdiğinde, imleç `$end$` anahtar sözcüğünün konumuna yerleştirilir.

`for`Önceki bölümde yer aldığı kod parçacığı, bu ayrılmış anahtar sözcüklerin her ikisine de bir örnektir.

Daha fazla bilgi için [Visual Studio kod parçacıkları başvurusuna](/visualstudio/ide/code-snippets-schema-reference#keywords) bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod parçacıkları (Windows üzerinde Visual Studio)](/visualstudio/ide/code-snippets)