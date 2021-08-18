---
title: Tanıma Göz At kullanma
description: Şu anda yazmakta olan koddan bağlam değiştirmek zorunda kalmadan kodunuzu görüntülemek ve düzenlemek için Tanıma Göz At komutunu kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/10/2018
ms.topic: how-to
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 925acb8a046647ec1ea64f2eb2f446e30fdb5d6d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122078290"
---
# <a name="how-to-view-and-edit-code-by-using-peek-definition-altf12"></a>Nasıllı: Tanıma Göz At (Alt+F12) kullanarak kodu görüntüleme ve düzenleme

Peek Definition **komutunu kullanarak,** yazmakta olduğu koddan uzaklaşarak kodu görüntüleyemez ve düzenleyebilirsiniz. **Tanıma Göz** **At** ve Tanıma Git  aynı bilgileri gösterir, ancak Tanıma Göz  At bir açılır pencerede, Tanıma Git ise kodu ayrı bir kod penceresinde gösterir. **Tanıma Git,** bağlamınızı (etkin kod penceresi, geçerli satır ve imleç konumu) tanım kod penceresine geçişe neden olur. Tanıma **Göz At'ı** kullanarak tanımı görüntüleyemez, düzenleyebilir ve özgün kod dosyasında yerlerinizi alırken tanım dosyasının içinde dolaşabilirsiniz.

Peek **Definition'i** C#, Visual Basic ve C++ koduyla kullanabilirsiniz. Bu **Visual Basic, Tanıma** Göz At,  tanım meta verileri olmayan simgeler (örneğin, yerleşik .NET türleri) için Nesne Tarayıcısı'nın bağlantısını gösterir.

## <a name="use-peek-definition"></a>Tanıma Göz At'i kullanma

### <a name="open-a-peek-definition-window"></a>Bir Tanıma Göz At penceresi açma

1. Keşfetmek istediğiniz bir tür veya **üyenin** sağ tıklama menüsünden Tanıma Göz At'ı seçerek bir tanıma göz atabilirsiniz. Seçenek etkinleştirildiyse, **Ctrl** tuşuna basarak (veya başka bir değiştirici) ve üye adına tıklayarak da bir tanıma göz atabilirsiniz. Alternatif olarak, klavyeden **Alt** + **F12 tuşuna basın.**

     Bu çizimde **adlı bir** yöntemin Peek Definition penceresi `Print()` gösterilir:

     ![Göz Atma Penceresi](../ide/media/peekwindow.png)

     Tanım penceresi özgün `printer.Print("Hello World!")` dosyada satırın altında görünür. Pencerede, özgün dosyanızdaki kodlardan hiçbiri gizlenmez. Aşağıdaki satırlar `printer.Print("Hello World!")` tanım penceresinin altında görünür.

1. İmleci, göz atma tanımı penceresinde farklı konumlara hareket ettirebilirsiniz. Özgün kod penceresinde de hareket ettirebilirsiniz.

1. Dizeyi tanım penceresinden kopyalayıp özgün koda yapıştırabilirsiniz. Dizeyi tanım penceresinden sürükleyip özgün koda da bırakabilirsiniz (tanım penceresinden silinmeden).

1. Tanım penceresi sekmesinde Esc tuşuna veya **Kapat** düğmesini **seçerek** tanım penceresini kapatabilirsiniz.

### <a name="open-a-peek-definition-window-from-within-a-peek-definition-window"></a>Bir Tanıma Göz At penceresinden Bir Tanıma Göz At penceresi açın

Zaten bir Tanıma Göz At **penceresi** açıksa, bu pencerenin kodunda **Peek Definition'ı** yeniden çağırabilirsiniz. Başka bir tanım penceresi açılır. Tanım penceresi sekmesinin yanında, tanım pencereleri arasında gezinmek için kullanabileceğiniz bir dizi içerik haritası noktası görünür. Her bir noktadaki araç ipucu, noktanın temsil ettiği tanım dosyasının dosya adını ve yolunu gösterir.

   ![Göz atma penceresindeki göz atma penceresi](../ide/media/peekwithinpeek.png)

### <a name="peek-definition-with-multiple-results"></a>Birden çok sonuçla Tanıma Göz Atma

Birden fazla tanımı **(örneğin,** kısmi bir sınıf) olan kodda Peek Definition kullanırsanız, kod tanımı görünümünün sağ yanında bir sonuç listesi görüntülenir. Listede istediğiniz sonucu seçerek tanımını görüntüleyebilirsiniz.

   ![Birden çok sonuçtan göz atma penceresi](../ide/media/peekmultiple.png)

### <a name="edit-inside-the-peek-definition-window"></a>Tanıma Göz At penceresinin içinde düzenleme

Bir Tanıma Göz At  penceresinde düzenlemeye başsanız, değiştir yaptığınız dosya otomatik olarak kod düzenleyicisinde ayrı bir sekme olarak açılır ve yaptığınız değişiklikleri gösterir. Tanıma Göz At penceresinde değişiklik yapmaya, geri alma ve kaydetmeye **devam** edersiniz ve sekme bu değişiklikleri yansıtmaya devam eder. Değişikliklerinizi kaydetmeden **Tanıma** Göz At penceresini kapatsanız bile, sekmede daha fazla değişiklik yapabilirsiniz, geri alabilir ve kaydedebilirsiniz. Bu değişiklikleri Tanıma Göz At penceresinde tam olarak nerede **bıraktığınızı** seçerek yapabilirsiniz.

   ![Göz Atma penceresinde düzenleme](../ide/media/peekedit.png)

### <a name="to-change-options-for-peek-definition"></a>Tanıma Göz At seçeneklerini değiştirmek için

1. Araçlar Seçenekler **Metin**  >  **Düzenleyici**  >  **Genel'e**  >  **gidin.**

1. Tanımı göz atma **görünümünde aç seçeneğini belirleyin.**

1. Seçenekler **iletişim** kutusunu kapatmak için **Tamam'a** tıklayın.

   ![Fareyle tıklamayla tanıma göz atma seçeneğini ayarlama](../ide/media/editor_options_peek_view.png)

### <a name="keyboard-shortcuts-for-peek-definition"></a>Tanıma Göz At için klavye kısayolları

Bu klavye kısayollarını Tanıma Göz At **penceresiyle kullanabilirsiniz:**

|İşlev|Klavye kısayolu|
|-------------------|:-----------------------:|
|Tanım penceresini açma|**Alt** + **F12**|
|Tanım penceresini kapatma|**Esc**|
|Tanım penceresini bir normal belge sekmesine yükseltme|**Ctrl tuşunu basılı tutarak** + **Alt** + **Giriş**|
|Tanım pencereleri arasında gezinme|**Ctrl tuşunu basılı tutarak** +  + Alt **-** ve **Ctrl** + **Alt**+**=**|
|Birden fazla sonuç arasında gezinme|**F8** ve **Shift** + **F8**|
|Kod düzenleyicisi penceresi ile tanım penceresi arasında geçiş yapma|**Shift ile kaydırma** + **Esc**|

> [!NOTE]
> Ayrıca aynı klavye kısayollarını kullanarak bir Tanıma Göz At penceresindeki kodu düzenlemenin **aynılarını,** diğer yerlerde kullandığınız Visual Studio.

## <a name="see-also"></a>Ayrıca bkz.

- [Kodda gezinme](../ide/navigating-code.md)
- [Tanıma ve Özet Tanıma Gitme](../ide/go-to-and-peek-definition.md)
- [Visual Studio'daki üretkenlik özellikleri](../ide/productivity-features.md)
