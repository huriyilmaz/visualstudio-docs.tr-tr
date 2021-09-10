---
title: Kod Parçacıkları
description: Kod parçacıklarını kullanarak kod parçacıklarında verimli bir şekilde program Mac için Visual Studio
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/09/2020
ms.assetid: 0FE27C0C-A861-4133-A74E-8D0505CF5342
ms.openlocfilehash: a8fdf70b4d966c644719047eca4249e432561ace
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123964847"
---
# <a name="code-snippets"></a>Kod parçacıkları

Kod şablonları olarak da adlandırılan kod parçacıkları, önceden yazılmış kod bloklarının eklemesine ve düzenlenmesine olanak sağlayan verimli programlama için yararlıdır. Kod parçacıklarının kullanımı, yaygın desenleri hızla eklemek, hatta geliştirici olarak söz dizimi konusunda emin olmadığınız yeni desenler öğrenmek için kullanışlı olabilir. C#, F#, HTML, XML, Python ve Razor için sağlanan şablonlar vardır.

Bu bölümde kod parçacıkları oluşturma, ekleme ve kodda kullanma açık açıklamalarını içerir.

## <a name="inserting-a-snippet"></a>Kod parçacığı ekleme

Kod parçacıkları eklemenin bazı farklı yolları vardır ve bazıları aşağıda açıklanmıştır:

- **Sekme Genişletme** &ndash; Şablon adını yazmaya başlayın, listeden seçin ve Sekme **tuşuna** **basarak** ekleyin:

  ![Kodda Sekme Genişletme](media/source-editor-image13.png)

- **Araç Kutusu** &ndash; Tüm kod parçacıklarının listesini görüntülemek için Araç Kutusu Penceresi'ne tıklayın. Araç kutusundan herhangi bir şablonu kaynak kodunda doğru konuma sürükleyin:

  [![Araç Kutusunda kod parçacıkları](media/source-editor-image14-sml.png)](media/source-editor-image14.png#lightbox)

- **Şablon Ekle komutu** &ndash; Şu anda şablon eklemek için varsayılan anahtar bağlama kümesi yoktur. Bir tane oluşturmak için, Visual Studio > **Tercihleri'ne > ve** için arama `template` oluşturun. Bu, istenen anahtar bağlamayı Bağlamayı Düzenle alanına eklemeye ve ardından Uygula'ya tıklamaya **olanak sağlar:**

  ![Şablona Ekleme komutu](media/source-editor-image15.png)

## <a name="creating-a-new-template"></a>Yeni şablon oluşturma

Kullanabileceğiniz ve düzenleyemezsiniz çeşitli dillerde çok sayıda mevcut şablon vardır, ancak Visual Studio > Tercihler > Metin Düzenleyici'ye ve Kod Parçacıklarına giderek **> eklenebilir:**

![Yeni şablon oluşturma](media/source-editor-image12.png)

Kod parçacıkları **oluşturmak** veya **düzenlemek** için Ekle veya Düzenle düğmelerine basın.

## <a name="keywords-in-code-snippets"></a>Kod parçacıklarındaki anahtar sözcükler

Düzenleyiciye bir kod parçacığı eklendikten sonra, tanımlanan tüm anahtar sözcükler vurgulanır ve bunlar arasında sekmeyle düzenlenemez. Anahtar sözcükler kod parçacığında bir "değişken" gibi davranır ve anahtar sözcüğünün adının önünde ve sonrasında bir dolar işareti `$` yerleştirerek tanımlanır. 

Yerleşik **kod parçacığını** düzenleyerek şablonu düzenle penceresi aşağıda `prop` gösterilmiştir. Kod parçacığı iki anahtar sözcük içerir ve pencerenin sağ tarafında daha fazla özellik ayarlanmış olabilir (varsayılan değer &ndash; `$type$` ve araç ipucu `$name$` &ndash; gibi):

![Şablon düzenleme penceresi](media/source-editor-image12z.png)

Bir kod parçacığını tanımlamak için aşağıdaki alanlar kullanılır:

- **Kısayol** &ndash; Kullanıcının kod parçacığını eklemek için ekleyesi metin.
- **Grupla** &ndash; Kod parçacıkları, bu değer kullanılarak kod parçacığı içerik menüsünde birlikte gruplandı.
- **Açıklama** &ndash; Kod parçacığının amacının açıklaması.
- **Mime** &ndash; Kod parçacığının hangi dosya türlerinde kullanılabilir olduğunu kontrol eder.
- **Genişletilebilir şablon** &ndash; Kısayol yazarak kod parçacığının imleçe eklenece kadar bu öğenin işaretli olduğundan emin olun.
- **Şablonla çevreli** &ndash; Düzenleyicinin Surround **with...** içerik menüsünde bu kısayolu listele seçeneğini işaretleyin.
- **Şablon metni** &ndash; Düzenleyiciye eklenecek gerçek kod parçacığı. Anahtar sözcük yer tutucuları, dolar işaretleriyle bir belirteci çevrelerken tanımlanabilir. `$type$`.
- **Anahtar sözcük özellik paneli** &ndash; Pencerenin sağ tarafında, bir anahtar sözcük seçmek (örneğin) ve varsayılan değer ve araç ipucu gibi özellikleri düzenlemek için üst tarafındaki açılan `type` listeyi kullanın.

## <a name="using-keywords-in-the-editor"></a>Düzenleyicide anahtar sözcükleri kullanma

Yukarıda tanımlanan gibi anahtar sözcüklerle kod parçacığını kullanmak için kısayolu yazın ve **Sekme** tuşuna iki kez basın; kod parçacığı içeriği imlecin üzerine eklenir:

![Anahtar sözcükleri gösteren eklenen kod parçacığı](media/source-editor-image12a.png)

Sınıf için **kod** parçacığını özelleştirmek için `object` ve arasında geçiş yapmak için Sekme `MyProperty` tuşuna basın.

Anahtar sözcük, bu örnekte olduğu gibi bir kod parçacığında yinelendiğinde `for` anahtar sözcüğün `$i$` 3 kez göründüğüne dikkat ekleyebilirsiniz:

![Yinelenen anahtar sözcüklerle kod parçacığı şablonu](media/source-editor-image12b.png)

Düzenleyicide kullanılırken, **Sekme tuşu** ilk ve arasında `i` geçiş yapmak için `max` kullanılır. değerini farklı bir değişken `i` adıyla üzerine yazsanız üç örnek de güncelleştirilir:

![Birden çok anahtar sözcük gösteren eklenen kod parçacığı](media/source-editor-image12c.png)

### <a name="reserved-keywords"></a>Ayrılmış anahtar sözcükler

Bir kod parçacığında kullanabileceğiniz iki ayrılmış anahtar sözcük vardır:

- `$selected$`&ndash;Kod parçacığında **Is surround with template** işaretli ise, bu anahtar sözcük kod parçacığı seçilirken düzenleyicide vurgulanan metinle değiştirilir.
- `$end$`&ndash;Kullanıcı bir kod parçacığında anahtar sözcükleri düzenlemeyi bitirdikten sonra imleci anahtar sözcüğün konumunun üzerine `$end$` yerleştirilir.

Önceki `for` bölümde yer alan kod parçacığı, bu ayrılmış anahtar sözcüklerin her ikisine de bir örnektir.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod parçacıkları (Visual Studio Windows)](/visualstudio/ide/code-snippets)
