---
title: "Nasıl yapılır: Özet tanımı 'Nı kullanarak kodu görüntüleme ve düzenleme (alt + F12) | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 45f3dd20-902a-4047-8cca-9f18216123f4
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40772919031200466999df2dfbf651fae3ee01e7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670563"
---
# <a name="how-to-view-and-edit-code-by-using-peek-definition-altf12"></a>Nasıl yapılır: Özet Tanımı'nı Kullanarak Kodu Görüntüleme ve Düzenleme (Alt+F12)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yazmakta olduğunuz koddan çıkmadan kodu görüntülemek ve düzenlemek için Özet **tanım** komutunu kullanabilirsiniz. **Tanıma göz atın** ve **Tanıma Git** aynı bilgileri gösterir, ancak **göz atma tanımı** bir açılır pencerede gösterir ve **Tanıma Git** kodu ayrı bir kod penceresinde gösterir. **Tanıma Git** , bağlamınızın (yani, etkin kod penceresi, geçerli satır ve imleç konumu) tanım kodu penceresine geçiş yapmasına neden olur. Özet **tanımı**'nı kullanarak tanımı görüntüleyip düzenleyebilir ve özgün kod dosyasında yerinizi tutarken tanım dosyası içinde gezinebilirsiniz.

 **Açıklama tanımını** C#, Visual Basic ve C++ kodu ile birlikte kullanabilirsiniz. Visual Basic, **Gözatma tanımı** , tanım meta verileri olmayan semboller için **nesne tarayıcısı** bir bağlantı gösterir (örneğin, içinde yerleşik .NET Framework türler).

> [!IMPORTANT]
> Visual Studio 2013'ün herhangi bir Express sürümünde bu komutu kullanamazsınız.

## <a name="working-with-peek-definition"></a>Özet Tanım ile Çalışma

#### <a name="to-open-a-peek-definition-window"></a>Bir Özet Tanım penceresi açmak için

1. Araştırmak istediğiniz bir yöntemin kısayol menüsünü açarak Özet **tanımını** bulabilirsiniz. (Klavye: Alt+F12)

     Bu çizimde adlı bir yöntem için Özet **tanım** penceresi gösterilmektedir `Print()` :

     ![Pencereye göz atma](../ide/media/peekwindow.png "PeekWindow")

     Tanım penceresi `printer.Print(“Hello World!”)` Orijinal dosyadaki satırın altında görünür. Pencerede, özgün dosyanızdaki kodlardan hiçbiri gizlenmez. Çağrıyı izleyen satırlar, `printer.Print(“Hello World!”)` Tanım penceresinin altında görünür.

2. İmleci, kod tanımı penceresinde farklı konumlara taşıyabilirsiniz. Özgün kod penceresinde tanım penceresinin altında veya üstünde gezinmeye devam edebilirsiniz.

3. Dizeyi tanım penceresinden kopyalayıp özgün koda yapıştırabilirsiniz. Dizeyi tanım penceresinden sürükleyip özgün koda da bırakabilirsiniz (tanım penceresinden silinmeden).

4. Tanım penceresi sekmesinden ESC tuşunu veya **Kapat** düğmesini seçerek tanım penceresini kapatabilirsiniz.

#### <a name="to-open-a-peek-definition-window-from-within-a-peek-definition-window"></a>Bir Özet Tanım penceresinin içinden Özet Tanım penceresi açmak için

- Zaten açık bir Özet **tanım** penceresi varsa, Bu penceredeki kodda **göz atma tanımını** yeniden çağırabilirsiniz. Başka bir tanım penceresi açılır. Tanım penceresi sekmesinin yanında, tanım pencereleri arasında gezinmek için kullanabileceğiniz bir dizi içerik haritası noktası görünür. Her bir noktadaki araç ipucu, noktanın temsil ettiği tanım dosyasının dosya adını ve yolunu gösterir.

     ![Bir göz atma penceresindeki pencereye göz atın](../ide/media/peekwithinpeek.png "PeekWithinPeek")

#### <a name="to-use-peek-definition-with-multiple-results"></a>Özet Tanım komutunu birden çok sonuçla kullanmak için

- Birden fazla tanıma sahip kodda (örneğin, kısmi sınıflar) Özet **tanım** ' ı kullanırsanız, kod tanımı görünümünün sağında bir sonuç listesi görünür. Listede istediğiniz sonucu seçerek tanımını görüntüleyebilirsiniz.

     ![Birden çok sonuçtan pencereye göz atın](../ide/media/peekmultiple.png "PeekMultiple")

#### <a name="to-edit-inside-the-peek-definition-window"></a>Özet Tanım penceresinin içinde düzenlemek için

- Bir Özet **tanım** penceresi içinde düzenlemeye başladığınızda, değiştirdiğiniz dosya otomatik olarak kod düzenleyicisinde ayrı bir sekme olarak açılır ve önceden yaptığınız değişiklikleri yansıtır. **Göz atma** penceresinde değişiklikler yapmaya, geri almaya ve kaydetmeye devam edebilirsiniz ve sekme bu değişiklikleri yansıtacak şekilde devam eder. Değişikliklerinizi kaydetmeden pencereyi kapatsanız bile, tam olarak pencerede kaldığınız yeri seçerek, kalan değişikliklerinizi bu sekmede yapabilir, geri alabilir ve kaydedebilirsiniz.

     ![Bir göz atma penceresinde Düzenle](../ide/media/peekedit.png "PeekEdit")

#### <a name="to-use-keyboard-shortcuts-for-peek-definition"></a>Özet Tanım klavye kısayollarını kullanmak için

- Bu klavye kısayollarını **göz atma** penceresiyle birlikte kullanabilirsiniz:

    |İşlev|Klavye kısayolu|
    |-------------------|-----------------------|
    |Tanım penceresini açma|Alt+F12|
    |Tanım penceresini kapatma|Esc|
    |Tanım penceresini bir normal belge sekmesine yükseltme|Shift+Alt+Home|
    |Tanım pencereleri arasında gezinme|Ctrl+Alt+- ve Ctrl+Alt+=|
    |Birden fazla sonuç arasında gezinme|F8ve Shift+F8|
    |Kod düzenleyicisi penceresi ile tanım penceresi arasında geçiş yapma|Shift+Esc|

    > [!NOTE]
    > Aynı klavye kısayollarını, Visual Studio 'da başka bir yerde kullandığınız şekilde bir Özet **tanım** penceresinde kod düzenlemek için de kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca Bkz.
 [Üretkenlik Ipuçları](../ide/productivity-tips-for-visual-studio.md)
