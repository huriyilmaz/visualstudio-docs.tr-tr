---
title: Kod Parçacıkları
description: Kod parçacıklarını kullanarak kod parçacıklarında verimli bir şekilde program Mac için Visual Studio
author: jmatthiesen
ms.author: jomatthi
manager: dominicn
ms.date: 11/09/2020
ms.topic: reference
ms.assetid: 0FE27C0C-A861-4133-A74E-8D0505CF5342
ms.openlocfilehash: 413c5b0a637c2d3d4dfd9fe0f2c07a5d865153d3
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135803602"
---
# <a name="code-snippets"></a>Kod parçacıkları

Kod şablonları olarak da adlandırılan kod _parçacıkları,_ önceden yazılmış kod bloklarının eklemesine ve düzenlenmesine olanak sağlayan verimli programlama için yararlıdır. Kod parçacıklarının kullanımı, yaygın desenleri hızla eklemek, hatta geliştirici olarak söz dizimi konusunda emin olmadığınız yeni desenler öğrenmek için kullanışlı olabilir. C#, F#, HTML, XML, Python ve Razor için sağlanan şablonlar vardır.

Bu bölümde kod parçacıkları oluşturma, ekleme ve kodda kullanma açık açıklamalarını içerir.

## <a name="inserting-a-snippet"></a>Kod parçacığı ekleme

Kod parçacıkları eklemenin bazı farklı yolları vardır ve bazıları aşağıda açıklanmıştır:

- **Sekme Genişletme** &ndash; Şablon adını yazmaya başlayın, listeden seçin ve Sekme **tuşuna** **basarak** ekleyin:

  ![Kodda Sekme Genişletme](media/source-editor-image13.png)

- **Araç** &ndash; Tüm kod parçacıklarının listesini görüntülemek için Araç Kutusu Penceresi'ne tıklayın. Araç kutusundan herhangi bir şablonu kaynak kodunda doğru konuma sürükleyin:

  [![Araç Kutusunda kod parçacıkları](media/source-editor-image14-sml.png)](media/source-editor-image14.png#lightbox)

- **Şablon Ekle komutu** &ndash; Şu anda şablon eklemek için varsayılan anahtar bağlama kümesi yoktur. Bir tane oluşturmak için, Anahtar **Bağlamaları Visual Studio > Tercihler'e > ve** için arama `template` oluşturun. Bu, istenen anahtar bağlamayı Bağlamayı Düzenle alanına eklemeye ve ardından Uygula'ya tıklamaya **olanak sağlar:**

  ![Şablona Ekleme komutu](media/source-editor-image15.png)

## <a name="creating-a-new-template"></a>Yeni şablon oluşturma

Kullanabileceğiniz ve düzenleyemezsiniz çeşitli dillerde birçok mevcut şablon vardır, ancak Visual Studio > Tercihler > Metin Düzenleyici'ye ve Kod Parçacıklarına giderek **yeni şablonlar > eklenebilir:**

![Yeni şablon oluşturma](media/source-editor-image12.png)

Kod parçacıkları **oluşturmak** veya **düzenlemek** için Ekle veya Düzenle düğmelerine basın.

## <a name="keywords-in-code-snippets"></a>Kod parçacıklarındaki anahtar sözcükler

Düzenleyiciye bir kod parçacığı eklendikten sonra, tanımlanan tüm anahtar sözcükler vurgulanır ve bunlar arasında sekmeyle düzenlenemez. Anahtar sözcükler kod parçacığında bir "değişken" gibi davranır ve anahtar sözcüğünün adının önünde ve sonrasında bir dolar işareti `$` yerleştirerek tanımlanır. 

Yerleşik **kod parçacığını** düzenleyerek şablonu düzenle penceresi aşağıda `prop` gösterilmiştir. Kod parçacığı iki anahtar sözcük içerir ve pencerenin sağ tarafında daha fazla özellik kümesi (varsayılan değer ve araç &ndash; `$type$` `$name$` &ndash; ipucu gibi) olabilir:

![Şablon düzenleme penceresi](media/source-editor-image12z.png)

Bir kod parçacığını tanımlamak için aşağıdaki alanlar kullanılır:

- **Kısayol** &ndash; Kullanıcının kod parçacığını eklemek için ekleyesi metin.
- **Grup** &ndash; Kod parçacıkları, bu değer kullanılarak kod parçacığı içerik menüsünde birlikte gruplandı.
- **Açıklama** &ndash; Kod parçacığının amacının açıklaması.
- **Mıme** &ndash; Kod parçacığının hangi dosya türlerinde kullanılabilir olduğunu kontrol eder.
- **Genişletilebilir şablon** &ndash; Kısayol yazarak kod parçacığının imleç üzerine eklen ekleneci için bunun işaretli olduğundan emin olun.
- **Şablonla çevreli** &ndash; Düzenleyicinin Surround **with...** içerik menüsünde bu kısayolu listele seçeneğini işaretleyin.
- **Şablon metni** &ndash; Düzenleyiciye eklenecek gerçek kod parçacığı. Anahtar sözcük yer tutucuları, dolar işaretleriyle bir belirteci çevrelerken tanımlanabilir. `$type$`.
- **Anahtar sözcük özellik paneli** &ndash; Pencerenin sağ tarafında, bir anahtar sözcük seçmek (örneğin) ve varsayılan değer ve araç ipucu gibi özellikleri düzenlemek için en üstte yer alan açılan `type` listeyi kullanın.

## <a name="using-keywords-in-the-editor"></a>Düzenleyicide anahtar sözcükleri kullanma

Yukarıda tanımlanan gibi anahtar sözcüklerle kod parçacığını kullanmak için kısayolu yazın ve **Sekme** tuşuna iki kez basın; kod parçacığı içeriği imlecin üzerine eklenir:

![Anahtar sözcükleri gösteren eklenen kod parçacığı](media/source-editor-image12a.png)

Sınıf için **kod** parçacığını özelleştirmek için `object` ve arasında geçiş yapmak için Sekme `MyProperty` tuşuna basın.

Anahtar sözcük, bu örnekte olduğu gibi bir kod parçacığında `for` yinelendiğinde anahtar sözcüğün `$i$` 3 kez göründüğüne dikkat ekleyebilirsiniz:

![Yinelenen anahtar sözcüklerle kod parçacığı şablonu](media/source-editor-image12b.png)

Düzenleyicide kullanılırken, **Sekme tuşu** ilk ve arasında `i` geçiş yapmak için `max` kullanılır. değerini farklı bir değişken `i` adıyla üzerine yazsanız üç örnek de güncelleştirilir:

![Birden çok anahtar sözcük gösteren eklenen kod parçacığı](media/source-editor-image12c.png)

### <a name="reserved-keywords"></a>Ayrılmış anahtar sözcükler

Bir kod parçacığında kullanabileceğiniz iki ayrılmış anahtar sözcük vardır:

- `$selected$`&ndash;Kod parçacığında **Is surround with template** işaretli ise, bu anahtar sözcük kod parçacığı seçilirken düzenleyicide vurgulanan metinle değiştirilir.
- `$end$`&ndash;Kullanıcı bir kod parçacığında anahtar sözcükleri düzenlemeyi bitirdikten sonra imleci anahtar sözcüğün konumunun üzerine `$end$` yerleştirilir.

Önceki `for` bölümde yer alan kod parçacığı, bu ayrılmış anahtar sözcüklerin her ikisine de bir örnektir.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod parçacıkları (Visual Studio üzerinde Windows)](/visualstudio/ide/code-snippets)
