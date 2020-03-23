---
title: Peek Tanımını Kullanma
ms.date: 01/10/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9eac5c8c47c208f39f74f542fbbff89c8340a93f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591352"
---
# <a name="how-to-view-and-edit-code-by-using-peek-definition-altf12"></a>Nasıl yapılır: Peek Definition (Alt+F12) kullanarak kodu görüntüleme ve düzenleme

Yazmakta olduğunuz koddan uzaklaşmadan kodu görüntülemek ve değiştirmek için **Peek Tanımı** komutunu kullanabilirsiniz. **Peek Definition** ve **Go To Definition** aynı bilgileri gösterir, ancak Peek **Tanımı** açılır pencerede gösterir ve **Tanıma Git** kodu ayrı bir kod penceresinde gösterir. **Tanıma Git,** bağlamınızın (diğer bir süre önce etkin kod penceresi, geçerli satır ve imleç konumu) tanım kodu penceresine geçmesine neden olur. Peek **Definition'ı**kullanarak, özgün kod dosyasındaki yerinizi tutarken tanımı görüntüleyebilir ve düzenlemeyapabilir ve tanım dosyasının içinde dolaşabilirsiniz.

C#, Visual Basic ve C++ koduyla **Peek Definition'ı** kullanabilirsiniz. Visual Basic'te, **Peek Definition** tanım meta verileri olmayan semboller için **Nesne Tarayıcısı'na** bir bağlantı gösterir (örneğin, yerleşik .NET türleri).

## <a name="use-peek-definition"></a>Peek Tanımını Kullanma

### <a name="open-a-peek-definition-window"></a>Peek Tanımı penceresi açma

1. Keşfetmek istediğiniz bir tür veya üye için sağ tıklama menüsünden **Peek Tanımı'nı** seçerek bir tanıma göz atabilirsiniz. Seçenek etkinse, **Ctrl'ye** (veya başka bir değiştiriciye) basarak ve üye adını tıklatarak fareyi kullanarak bir tanımı da gözetleyebilirsiniz. Veya klavyeden **Alt**+**F12**tuşuna basın.

     Bu resimde, **Peek Definition** adlı `Print()`bir yöntem için Peek Tanımı penceresi gösterilmektedir:

     ![Peek Penceresi](../ide/media/peekwindow.png)

     Tanım penceresi özgün dosyadaki satırın `printer.Print("Hello World!")` altında görünür. Pencerede, özgün dosyanızdaki kodlardan hiçbiri gizlenmez. Ardından `printer.Print("Hello World!")` gelen satırlar tanım penceresinin altında görünür.

1. İmleci peek tanımı penceresinde farklı konumlara taşıyabilirsiniz. Orijinal kod penceresinde de hareket edebilirsiniz.

1. Dizeyi tanım penceresinden kopyalayıp özgün koda yapıştırabilirsiniz. Dizeyi tanım penceresinden sürükleyip özgün koda da bırakabilirsiniz (tanım penceresinden silinmeden).

1. Tanım penceresi sekmesinde **Esc** tuşunu veya **Kapat** düğmesini seçerek tanım penceresini kapatabilirsiniz.

### <a name="open-a-peek-definition-window-from-within-a-peek-definition-window"></a>Peek Tanımı penceresinden Peek Tanımı penceresi açma

Zaten açık bir **Peek Tanımı** pencereniz varsa, bu penceredeki kodda Peek **Definition'ı** yeniden arayabilirsiniz. Başka bir tanım penceresi açılır. Tanım penceresi sekmesinin yanında, tanım pencereleri arasında gezinmek için kullanabileceğiniz bir dizi içerik haritası noktası görünür. Her bir noktadaki araç ipucu, noktanın temsil ettiği tanım dosyasının dosya adını ve yolunu gösterir.

   ![Peek penceresi içindeki peek penceresi](../ide/media/peekwithinpeek.png)

### <a name="peek-definition-with-multiple-results"></a>Birden çok sonuçla Peek Tanımı

Birden fazla tanımı olan kodda (örneğin, kısmi bir sınıf) **Peek Tanımı** kullanırsanız, kod tanımı görünümünün sağında bir sonuç listesi görüntülenir. Listede istediğiniz sonucu seçerek tanımını görüntüleyebilirsiniz.

   ![Birden çok sonuçtan peek penceresi](../ide/media/peekmultiple.png)

### <a name="edit-inside-the-peek-definition-window"></a>Peek Tanımı penceresi içinde edin

**Bir Peek Tanımı** penceresinde editörlük yapmaya başladığınızda, değiştirdiğiniz dosya kod düzenleyicisinde otomatik olarak ayrı bir sekme olarak açılır ve yaptığınız değişiklikleri yansıtır. **Peek Tanımı** penceresinde değişiklik yapmaya, geri almaya ve kaydetmeye devam edebilirsiniz ve sekme bu değişiklikleri yansıtmaya devam edecektir. Değişikliklerinizi kaydetmeden **Peek Tanımı** penceresini kapatsanız bile, Sekmede daha fazla değişiklik yapabilir, geri alabilir ve kaydedebilirsiniz ve **Peek Tanımı** penceresinde tam olarak kaldığınız yerden devam edebilirsiniz.

   ![Peek penceresi içinde düzenleme](../ide/media/peekedit.png)

### <a name="to-change-options-for-peek-definition"></a>Peek Definition seçeneklerini değiştirmek için

1. **Tools** > **Options** > **Metin Genel Yayın** > **Yönetmeni'ne**gidin.

1. **Peek görünümünde tanımı aç**seçeneğini seçin.

1. **Seçenekler** iletişim kutusunu kapatmak için **Tamam'ı** tıklatın.

   ![Fare tıklaması peek tanımı seçeneğini ayarlama](../ide/media/editor_options_peek_view.png)

### <a name="keyboard-shortcuts-for-peek-definition"></a>Peek Definition için klavye kısayolları

Bu klavye kısayollarını Peek **Definition** penceresi ile kullanabilirsiniz:

|İşlev|Klavye kısayolu|
|-------------------|:-----------------------:|
|Tanım penceresini açma|**Alt**+**F12**|
|Tanım penceresini kapatma|**Esc**|
|Tanım penceresini bir normal belge sekmesine yükseltme|**Shift**+**Alt**+**Ana Sayfa**|
|Tanım pencereleri arasında gezinme|**Ctrl**+**Alt** + **-** ve **Ctrl**+**Alt**+**=**|
|Birden fazla sonuç arasında gezinme|**F8** ve **Shift**+**F8**|
|Kod düzenleyicisi penceresi ile tanım penceresi arasında geçiş yapma|**Vardiya**+**Esc**|

> [!NOTE]
> Visual Studio'nun başka bir yerinde kullandığınız gibi **Peek Definition** penceresinde kodu da aynı klavye kısayollarını kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Kodda gezinme](../ide/navigating-code.md)
- [Tanıma ve Özet Tanıma Gitme](../ide/go-to-and-peek-definition.md)
- [Visual Studio'da verimlilik özellikleri](../ide/productivity-features.md)
