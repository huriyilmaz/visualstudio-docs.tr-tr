---
title: Kod gezinti komutları
ms.date: 11/21/2019
ms.topic: conceptual
helpviewer_keywords:
- code editor, navigation
- code editor, go to
- code editor, go to definition
- code editor, go to line
- code editor, peek definition
- code editor, navigation bar
- go to definition
- peek definition
- go to line
- go to
author: TerryGLee
ms.author: tglee
manager: tglee
ms.workload:
- multiple
ms.openlocfilehash: 0216a71b675473d54aec9738ea7bdc85b7643841
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585827"
---
# <a name="navigate-code"></a>Kodda gezinme

Visual Studio, editörde kodda gezinmenin çeşitli yollarını sağlar. Bu konu, kodunuzda gezinmenin farklı yollarını özetler ve daha fazla ayrıntıya giren konulara bağlantılar sağlar.

## <a name="navigate-backward-and-navigate-forward-commands"></a>Geriye Doğru Git ve İleri'de Gezinme komutları

Ekleme noktasını önceki konumlara taşımak **Navigate Forward** veya önceki konumdan daha yeni bir konuma dönmek için araç çubuğundaki **İleri Git** (**Ctrl**+**Ctrl**+**-****Shift**+**-**) düğmelerini kullanabilirsiniz. Bu düğmeler ekleme noktasının son 20 noktasını korur. Bu komutlar, **Geriye Doğru Git** ve İleri **Git**altında **Görünüm** menüsünde de mevcuttur.

![İleri ve geri navigasyon düğmeleri](../ide/media/vs2017_nav_buttons.png)

## <a name="navigation-bar"></a>Gezinti çubuğu

Kod tabanındaki koda gitmek için **gezinme çubuğunu** (kod penceresinin üst kısmındaki açılır kutular) kullanabilirsiniz. Doğrudan gitmek için bir tür veya üye seçebilirsiniz. Visual Basic, C#veya C++ kod tabanında kodu edindiğinizde gezinti çubuğu görüntülenir. Kısmi bir sınıfta, geçerli kod dosyası dışında tanımlanan üyeler devre dışı tutulabilir (gri renkte görünürler).

![Kod gezinme çubuğu](../ide/media/vside_navigation_bar.png)

Açılan kutularda aşağıdaki gibi gezinebilirsiniz:

- Geçerli dosyanın ait olduğu başka bir projeye gitmek için, dosyayı sol açılır menüden seçin.

- Bir sınıfa veya türe gitmek için, orta açılır menüden seçin.

- Bir yordamveya sınıfın diğer üyesine doğrudan gitmek için, doğru açılır menüde seçin.

- Odak noktasını kod penceresinden gezinti çubuğuna kaydırmak için kısayol tuşu birleşimi **Ctrl**+**F2'ye**basın.

- Gezinme çubuğundaki kutudan kutuya odak kaydırmak için **Sekme** tuşuna basın.

- Odak noktası olan gezinti çubuğu öğesini seçmek ve kod penceresine dönmek için **Enter** tuşuna basın.

- Hiçbir şey seçmeden gezinti çubuğundan kodun odağına dönmek için **Esc** tuşuna basın.

Gezinti çubuğunu gizlemek için Metin **Düzenleyicisi Tüm Diller** ayarlarında **Gezinme çubuğu** seçeneğini **(Araçlar** > **Seçenekleri** > **Metin Düzenleyicisi** > **Tüm Diller)** değiştirin veya tek tek dillerin ayarlarını değiştirebilirsiniz.

## <a name="find-all-references"></a>Tüm referansları bulun

Çözümde seçili öğeye yapılan tüm başvuruları bulur. Bunu, büyük bir yeniden düzenlemenin olası yan etkilerini denetlemek veya "ölü" kodu doğrulamak için kullanabilirsiniz. Sonuçlar arasında atlamak için **F8** tuşuna basın. Daha fazla bilgi için [bkz.](finding-references.md)

Girdi | İşlev
------------ | ---
**Klavye** | Metin imlecinizi tür adının içinde bir yere yerleştirin ve **Shift**+**F12 tuşuna** basın
**Fare** | Sağ tıklama menüsünden **Tüm Referansları Bul'u** seçin

## <a name="reference-highlighting"></a>Referans vurgulama

Kaynak kodundaki bir simgeyi tıklattığınızda, bu sembolün tüm örnekleri belgede vurgulanır. Vurgulanan semboller, bildirimleri ve başvuruları ve **Tüm Başvuruları Bul'un** döneceği diğer birçok sembolü içerebilir. Bunlar sınıfların, nesnelerin, değişkenlerin, yöntemlerin ve özelliklerin adlarını içerir. Visual Basic kodunda, birçok denetim yapısı için anahtar kelimeler de vurgulanır. Bir sonraki veya önceki vurgulanan simgeye geçmek için Ctrl**Shift**+Down Arrow veya+ **Ctrl**+**Shift**+**Up****Arrow** tuşlarına basın. **Ctrl** **Araçlar** > **Seçenekleri** > **Ortamı** > **Yazı Tipleri ve Renkler** > **Vurgulanan Başvuru'da**vurgulama rengini değiştirebilirsiniz.

## <a name="go-to-commands"></a>Komutlara Git

Go To'da, **Git'** in altındaki **Edit** menüsünde bulunan aşağıdaki komutlar vardır:

- **Satıra Git** (**Ctrl**+**G**): Etkin belgede belirtilen satır numarasına geçin.

- **Tüme Git** (**Ctrl**+**T** veya **Ctrl**+**,**): Belirtilen satıra, yazıya, dosyaya, üyeye veya simgeye taşıyın.

- **Dosyaya Git** (**Ctrl**+**1**, **Ctrl**+**F**): Çözümde belirtilen dosyaya taşıyın.

- **Son Dosyaya Git** (**Ctrl**+**1**, **Ctrl**+**R**): Çözümde belirtilen, en son ziyaret edilen dosyaya taşıyın.

- **Git Türüne** (**Ctrl**+**1**, **Ctrl**+**T**): Çözeltide belirtilen türe geçin.

- **Üyeye Git** (**Ctrl**+**1**, **Ctrl**+**M**): Çözümde belirtilen üyeye taşıyın.

- **Sembole Git** (**Ctrl**+**1**, **Ctrl**+**S**): Çözümde belirtilen sembole taşıyın.

Visual Studio 2017 sürüm 15.8 ve sonraki sürümlerinde aşağıdaki **Go To** navigasyon komutları da mevcuttur:

- **Dosyada Sonraki Sayıya Git** (**Alt**+**PgDn**) ve **Dosyadaki Önceki Sayıya Git** (**Alt**+**PgUp**)

- **Son Edit Konumuna Git** (**Ctrl**+**Shift**+**Backspace**)

Go To komutları konusunu [kullanarak Bul kodundaki](../ide/go-to.md) bu komutlar hakkında daha fazla bilgi edinin.

## <a name="go-to-definition"></a>Tanıma Git

Go To Definition sizi seçili öğenin tanımına götürür. Daha fazla bilgi için Bkz. [Tanımı ve Peek Tanımı git.](../ide/go-to-and-peek-definition.md)

Girdi | İşlev
------------ | ---
**Klavye** | Metin imlecinizi tür adının içinde bir yere yerleştirin ve **F12 tuşuna** basın
**Fare** | Tür adına sağ tıklayın ve **Tanıma Git'i** seçin VEYA **Ctrl** tuşuna basın ve tür adına tıklayın

## <a name="peek-definition"></a>Tanıma Göz At

Peek Definition, kod düzenleyicisinde geçerli konumunuzdan uzaklaşmadan bir pencerede seçili öğenin tanımını görüntüler. Daha fazla bilgi [için bkz: Peek Definition ve](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md) Go To Definition ve Peek [Definition](../ide/go-to-and-peek-definition.md)kullanarak kodu görüntüleme ve düzenleme.

Girdi | İşlev
------------ | ---
**Klavye** | Metin imlecinizi tür adının içinde bir yere yerleştirin ve **Alt**+**F12 tuşuna** basın
**Fare** | Tür adına sağ tıklayın ve **Peek Definition** OR'u seçin **Ctrl** tuşuna basın ve tür adına tıklayın **(peek görünümü seçeneğinde Açık tanım** işaretliyse)

## <a name="go-to-implementation"></a>Uygulamaya Git

Uygulamaya Git'i kullanarak, taban sınıftan veya uygulamalarından uygulamalarına gidebilirsiniz. Birden çok uygulama varsa, bunları Simge Bulun **Sonuçları** penceresinde listelenirken görürsünüz:

Girdi | İşlev
------------ | ---
**Klavye** | Metin imlecinizi tür adının içinde bir yere yerleştirin ve **Ctrl**+**F12 tuşuna** basın
**Fare** | Tür adına sağ tıklayın ve **Uygulamaya Git'i** seçin

## <a name="go-to-base"></a>Temele Git

Base'e Git'i kullanarak, seçili öğenin devralma zincirinde gezinebilirsiniz. Birden çok sonuç varsa, bunları **Temele Git** penceresinde göreceksiniz:

Girdi | İşlev
------------ | ---
**Klavye** | Metin imlecinizi tür adının içinde bir yere yerleştirin ve **Alt**+**Ana Sayfa'ya** basın
**Fare** | Tür adına sağ tıklayın ve **Base'e Git'i** seçin

## <a name="call-hierarchy"></a>Çağrı Hiyerarşisi

[Çağrı Hiyerarşisi penceresinde](../ide/reference/call-hierarchy.md)bir yönteme yapılan aramaları görüntüleyebilirsiniz:

Girdi | İşlev
------------ | ---
**Klavye** | Metin imlecinizi tür adının içinde bir yere yerleştirin ve **Ctrl**+**K**, **Ctrl**+**T** tuşlarına basın
**Fare** | Üye adına sağ tıklayın ve **Çağrı Hiyerarşisini Görüntüle'yi** seçin

## <a name="next-method-and-previous-method-commands-visual-basic"></a>Sonraki Yöntem ve Önceki Yöntem komutları (Visual Basic)

Visual Basic kod dosyalarında, ekleme noktasını farklı yöntemlere taşımak için bu komutları kullanın. **Sonraki Yöntemi** **Edit'i** > seçin veya Önceki**Yöntemi** **Edin.** > 

## <a name="structure-visualizer"></a>Yapı Görselleştiricisi

Kod düzenleyicisindeki Yapı Görselleştiricisi özelliği, kod tabanınızdaki eşleşen kıvırcık ayraçları gösteren dikey kesik çizgiler - *yapı kılavuz çizgilerini* gösterir. Bu, mantıksal blokların nerede başlayıp nerede sona erdirini görmenizi kolaylaştırır.

![Yapı Görselleştiricisi](../ide/media/vside_structure_visualizer.png)

Yapı kılavuz çizgilerini devre dışı katmayı sağlamak için **Araçlar** > **Seçenekleri** > Metin**DüzenleyiciSi Genel'e** **Text Editor** > gidin ve **Yapı kılavuz çizgilerini göster** kutusunu temizleyin.

## <a name="enhanced-scroll-bar"></a>Gelişmiş kaydırma çubuğu

Kod pencerenizdeki gelişmiş kaydırma çubuğunu kullanarak kodunuzu kuş bakışı görebilirsiniz. Harita modunda, imleci kaydırma çubuğunda yukarı ve aşağı hareket ettirdiğinizde kodun önizlemelerini görebilirsiniz. Daha fazla bilgi için [bkz: Kaydırma çubuğunu özelleştirerek kodunuzu izleyin.](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)

## <a name="codelens-information"></a>CodeLens bilgileri

CodeLens'i kod düzenleyicisinde kullandığınızda değişiklikler ve bu değişiklikleri, başvuruları, hataları, iş öğelerini, kod incelemelerini ve birim test durumunu kimler yaptı gibi belirli kodlar hakkında bilgi bulabilirsiniz. CodeLens, Team Foundation Server ile Visual Studio Enterprise'ı kullandığınızda teke tek ekran gibi çalışır. Bkz. [Kod değişikliklerini ve diğer geçmişi bul.](../ide/find-code-changes-and-other-history-with-codelens.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod düzenleyicisinin özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)
- [Arama hiyerarşisi görüntüle](../ide/reference/call-hierarchy.md)
