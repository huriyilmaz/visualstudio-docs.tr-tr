---
title: Peek tanımını kullanma
ms.date: 01/10/2018
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39d4d9dd4fb7364ddadd5e7568a2f34255c393ae
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656523"
---
# <a name="how-to-view-and-edit-code-by-using-peek-definition-altf12"></a>Nasıl yapılır: Özet tanımı 'nı kullanarak kodu görüntüleme ve düzenleme (alt + F12)

Yazmakta olduğunuz koddan çıkmadan kodu görüntülemek ve düzenlemek için Özet **tanım** komutunu kullanabilirsiniz. **Tanıma göz atın** ve **Tanıma Git** aynı bilgileri gösterir, ancak **göz atma tanımı** bir açılır pencerede gösterir ve **Tanıma Git** kodu ayrı bir kod penceresinde gösterir. **Tanıma Git** , bağlamınızın (yani, etkin kod penceresi, geçerli satır ve imleç konumu) tanım kodu penceresine geçiş yapmasına neden olur. Özet **tanımı**'nı kullanarak tanımı görüntüleyip düzenleyebilir ve özgün kod dosyasında yerinizi tutarken tanım dosyası içinde gezinebilirsiniz.

**Peek tanımını** , Visual Basic ve C++ kodla C#birlikte kullanabilirsiniz. Visual Basic, **Gözatma tanımı** , tanım meta verileri olmayan semboller için **nesne tarayıcısı** bağlantısını gösterir (örneğin, içinde yerleşik .net türleri).

## <a name="use-peek-definition"></a>Göz atma tanımını kullan

### <a name="open-a-peek-definition-window"></a>Bir Özet Tanım penceresi açın

1. İncelemek istediğiniz bir tür veya üyenin sağ tıklama menüsünden **Açıklama tanımı** ' nı seçerek bir tanımına göz atmayı sağlayabilirsiniz. Seçenek etkinleştirilirse, **CTRL** (veya başka bir değiştirici) tuşuna basarak ve üye adına tıklayarak bir tanımına da göz atmayı sağlayabilirsiniz. Ya da klavyeden **Alt** +**F12**tuşuna basın.

     Bu çizimde `Print()` adlı bir yöntem için Özet **tanım** penceresi gösterilmektedir:

     ![Pencereye göz atma](../ide/media/peekwindow.png)

     Tanım penceresi orijinal dosyadaki `printer.Print("Hello World!")` satırının altında görüntülenir. Pencerede, özgün dosyanızdaki kodlardan hiçbiri gizlenmez. @No__t_0 izleyen satırlar, tanım penceresinin altında görünür.

1. İmleci, gözatma tanımı penceresinde farklı konumlara taşıyabilirsiniz. Ayrıca özgün kod penceresinde de devam edebilirsiniz.

1. Dizeyi tanım penceresinden kopyalayıp özgün koda yapıştırabilirsiniz. Dizeyi tanım penceresinden sürükleyip özgün koda da bırakabilirsiniz (tanım penceresinden silinmeden).

1. Tanım penceresi sekmesinden **ESC** tuşunu veya **Kapat** düğmesini seçerek tanım penceresini kapatabilirsiniz.

### <a name="open-a-peek-definition-window-from-within-a-peek-definition-window"></a>Bir göz atma penceresi içinden bir Özet Tanım penceresi açın

Zaten açık bir Özet **tanım** penceresi varsa, Bu penceredeki kodda **göz atma tanımını** yeniden çağırabilirsiniz. Başka bir tanım penceresi açılır. Tanım penceresi sekmesinin yanında, tanım pencereleri arasında gezinmek için kullanabileceğiniz bir dizi içerik haritası noktası görünür. Her bir noktadaki araç ipucu, noktanın temsil ettiği tanım dosyasının dosya adını ve yolunu gösterir.

   ![Bir göz atma penceresindeki pencereye göz atın](../ide/media/peekwithinpeek.png)

### <a name="peek-definition-with-multiple-results"></a>Birden çok sonuç içeren tanıma göz atma

Birden fazla tanıma sahip kodda (örneğin, kısmi bir sınıf) Özet **tanım** ' ı kullanırsanız, kod tanımı görünümünün sağında bir sonuç listesi görünür. Listede istediğiniz sonucu seçerek tanımını görüntüleyebilirsiniz.

   ![Birden çok sonuçtan pencereye göz atın](../ide/media/peekmultiple.png)

### <a name="edit-inside-the-peek-definition-window"></a>Göz atma penceresinin içinde Düzenle

Bir Özet **tanım** penceresi içinde düzenlemeye başladığınızda, değiştirdiğiniz dosya otomatik olarak kod düzenleyicisinde ayrı bir sekme olarak açılır ve yaptığınız değişiklikleri yansıtır. **Göz atma** penceresinde değişiklikler yapmaya, geri almaya ve kaydetmeye devam edebilirsiniz ve sekme bu değişiklikleri yansıtacak şekilde devam eder. Değişikliklerinizi kaydetmeden **göz atma** penceresini kapatsanız bile, sekmede daha fazla değişiklik yapabilir, geri alabilir ve daha fazla değişiklik yapabilirsiniz. böylece, **göz atma** penceresinde, tam olarak kaldığınız yerden devam edebilirsiniz.

   ![Bir göz atma penceresinde Düzenle](../ide/media/peekedit.png)

### <a name="to-change-options-for-peek-definition"></a>Göz atma tanımı seçeneklerini değiştirmek için

1. **Araçlar**  > **Seçenekler**  > **metin Düzenleyicisi** **genel** >  ' e gidin.

1. **Göz atma görünümünde açık tanım**seçeneğini belirleyin.

1. **Seçenekler** iletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.

   ![Fare tıklaması tanım seçeneğini ayarlama](../ide/media/editor_options_peek_view.png)

### <a name="keyboard-shortcuts-for-peek-definition"></a>Göz atma tanımı için klavye kısayolları

Bu klavye kısayollarını **göz atma** penceresiyle birlikte kullanabilirsiniz:

|İşlevi|Klavye kısayolu|
|-------------------|:-----------------------:|
|Tanım penceresini açma|**Alt** +**F12**|
|Tanım penceresini kapatma|**Larına**|
|Tanım penceresini bir normal belge sekmesine yükseltme|**Shıft** +**alt** +**giriş**|
|Tanım pencereleri arasında gezinme|**Ctrl** +**alt** + **-** ve **CTRL** +**alt** + **1**|
|Birden fazla sonuç arasında gezinme|**F8** ve **SHIFT** +**F8**|
|Kod düzenleyicisi penceresi ile tanım penceresi arasında geçiş yapma|**Shıft** +**ESC**|

> [!NOTE]
> Aynı klavye kısayollarını, Visual Studio 'da başka bir yerde kullandığınız şekilde bir Özet **tanım** penceresinde kod düzenlemek için de kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Koda git](../ide/navigating-code.md)
- [Tanıma ve Özet Tanıma Gitme](../ide/go-to-and-peek-definition.md)
- [Visual Studio 'da üretkenlik özellikleri](../ide/productivity-features.md)