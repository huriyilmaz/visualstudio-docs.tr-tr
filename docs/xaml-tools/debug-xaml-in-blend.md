---
title: Blend 'de XAML hatalarını ayıklama | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 29a37182-2a2c-47e4-a4a9-2d5412738fed
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.technology: vs-ide-debug
ms.workload:
- uwp
ms.openlocfilehash: 5d6f0e54c37c394fce464b07440daa99b4dd7d5e
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188900"
---
# <a name="debug-xaml-in-blend"></a>Blend'de XAML hatalarını ayıklama

Uygulamanızdaki XAML hatalarını ayıklamak için Visual Studio için Blend içindeki araçları kullanabilirsiniz. Bir proje oluşturduğunuzda, tüm hatalar **sonuçlar** panelinde görüntülenir. Hatayla ilgili işaretlemeyi bulmak için bir hataya çift tıklayın. Çalışmak için daha fazla yer gerekiyorsa, **F12**tuşuna basarak **sonuçlar** panelini gizleyebilirsiniz.

## <a name="syntax-errors"></a>Sözdizimi hataları

XAML veya arka plan kod dosyaları dilin biçimlendirme kurallarını izleyememesi durumunda sözdizimi hataları oluşur. Hatanın açıklaması, nasıl düzeltileceğini anlamanıza yardımcı olabilir. Listede ayrıca dosyanın adı ve hatanın gerçekleştiği satır numarası da belirtilir. XAML hataları, **sonuçlar** panelinde **biçimlendirme** sekmesinde listelenir.

> [!TIP]
> XAML, XML tabanlı bir biçimlendirme dilidir ve XML sözdizimi kurallarını izler.

XAML sözdizimi hatalarının bazı yaygın nedenleri şunlardır:

- Bir anahtar sözcük yanlış yazılmıştır veya büyük harf ayrımı yanlıştır.

- Özniteliklerin veya metin dizelerinin etrafında tırnak işaretleri eksik.

- XAML öğesinde bir kapatma etiketi eksiktir.

- XAML öğesi, izin verilmeyen bir konumda bulunmaktadır.

Ortak XAML sözdizimi hakkında daha fazla bilgi için bkz. [temel xaml sözdizimi Kılavuzu](/windows/uwp/xaml-platform/xaml-syntax-guide).

Ayrıca Blend 'de basit kod hataları, derleme hataları ve çalışma zamanı hataları tanımlayabilir ve bunları çözebilirsiniz. Ancak, Visual Studio 'da kodun arkasındaki hataların tanımlanması ve çözümlenmesi daha kolay olabilir.

### <a name="debugging-sample-xaml-code"></a>Örnek XAML kodunda hata ayıklama

Aşağıdaki örnek, Blend 'de basit bir XAML hata ayıklama oturumunda size yol gösterecektir.

#### <a name="to-create-a-project"></a>Bir proje oluşturmak için

1. Blend 'de **Dosya** menüsünü açın ve ardından **Yeni proje**' ye tıklayın.

    **Yeni proje** iletişim kutusunda, sol tarafta proje türlerinin bir listesi görüntülenir. Bir proje türüne tıkladığınızda, onunla ilişkili proje şablonları sağ tarafta görüntülenir.

2. Proje türleri listesinde **Windows Evrensel**' e tıklayın.

3. Proje şablonları listesinde **boş uygulama (Evrensel Windows)** seçeneğine tıklayın.

4. **Ad** metin kutusuna `DebuggingSample` yazın.

5. **Konum** metin kutusunda projenin konumunu doğrulayın.

6. **Dil** listesinde, **görsel C#** ' e tıklayın ve ardından projeyi oluşturmak için **Tamam** ' a tıklayın.

7. Tasarım yüzeyine sağ tıklayın ve ardından **bölünmüş** görünüme geçmek Için **kaynağı görüntüle** ' ye tıklayın.

8. Kodun sağ üst köşesindeki **Kopyala** bağlantısına tıklayarak aşağıdaki kodu kopyalayın.

   ```xml
   <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>
        <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>
   </Grid>
   ```

9. Varsayılan **Kılavuzu**bulun ve açılış ve kapanış **kılavuz** etiketleri arasına kodu yapıştırın. İşiniz bittiğinde kodunuzun aşağıdaki gibi görünmesi gerekir:

    ```xml
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
         <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>
              <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>
         </Grid>
    </Grid>
    ```

10. Projeyi derlemek için **Ctrl**+**SHIFT**+**B** tuşlarına basın.

    Projenin derlenmeyeceğini ve hataları listelerken **sonuçlar** bölmesinin uygulamanın altında göründüğünü belirten bir hata iletisi görüntülenir.

    ![Visual Studio için Blend'de XAML hatalarını ayıklama](../debugger/media/blend_debugxaml_xaml.png "blend_debugXAML_XAML")

### <a name="resolve-xaml-errors"></a>XAML hatalarını çözümleme

XAML hataları algılandığında tasarım yüzeyi, projenizin geçersiz biçimlendirme içerdiğini belirten bir uyarı görüntüler. Hataları çözümlediğinizde, **sonuçlar** panelindeki hata listesi güncellenir. Tüm hataları çözdüyseniz tasarım yüzeyi etkinleştirilir ve uygulamanız tasarım yüzeyinde görüntülenir.

#### <a name="to-resolve-the-xaml-errors"></a>XAML hatalarını çözümlemek için

1. Listedeki ilk hataya çift tıklayın. Açıklama "< ' değeri özniteliğinde geçerli değildir." Hatayı çift tıklattığınızda, işaretçi kodda karşılık gelen konumu bulur. Önceki `Button` `<`, hata iletisinde önerildiği şekilde bir öznitelik değil, geçerlidir. Yukarıdaki kod satırına baktığınızda, `Top` özniteliği için kapatma tırnak işaretlerinin eksik olduğunu fark edeceksiniz. Kapanış tırnak işaretlerini yazın. **Sonuçlar** panelindeki hata listesinin değişikliklerinizi yansıtacak şekilde güncelleştiğine dikkat edin.

2. "' 0" açıklamasına çift tıklayarak bir adın başlangıcında geçerli değildir. " `Margin="0,149,0,0"` düzgün biçimde düzenlenmiş görünüyor. Ancak, `Margin` ' ın renk kodlamasının koddaki `Margin` ' in diğer örnekleriyle eşleşmediğinden emin olun. Önceki ad/değer çiftinde (`VerticalAlignment="Top`) kapanış tırnak işaretleri eksik olduğundan, `Margin="` önceki özniteliğin değerinin bir parçası olarak okunurdur ve 0 bir ad/değer çiftinin başlangıcı olarak okunurdur. `Top`için kapanan tırnak işaretlerini yazın. **Sonuçlar** panelindeki hata listesi, yaptığınız değişiklikleri yansıtacak şekilde güncelleştirilir.

3. Kalan hataya çift tıklayın, "kapanış XML etiketi ' Button ' eşleşmiyor." İşaretçi, hatanın `Grid` nesnesinin içinde olması için kapanış **kılavuz** etiketinde (`</Grid>`) bulunur. İkinci `Button` nesnesinde kapanış etiketinin eksik olduğuna dikkat edin. Kapanış `/`ekledikten sonra **sonuçlar** paneli listesi güncellenir. Artık bu ilk hatalar çözümlendiğinden, iki ek hata belirlenmiştir.

4. "Üye ' içerik ' tanınmıyor veya erişilebilir değil" seçeneğine çift tıklayın. `content` `c` büyük harfle yazılmalıdır. "C" alt durumunu "c" büyük harfle değiştirin.

5. "'<http://schemas.microsoft.com/winfx/2006/xaml>' ad alanında" mame "özelliği yok." "Mame" içindeki "d", "N" olmalıdır. "D" değerini bir "N" ile değiştirin. Artık XAML ayrıştırılabilmesine göre, uygulama tasarım yüzeyinde görünür.

    ![Visual Studio için Blend XAML hatalarını ayıklama](../debugger/media/blend_debugartboard_xaml.png "blend_debugArtboard_XAML")

    Projenizi derlemek ve kalan hata olmadığını doğrulamak için **Ctrl**+**SHIFT**+**B** tuşlarına basın.

## <a name="debug-in-visual-studio"></a>Visual Studio’da hata ayıklama

Uygulamanızda kodda daha kolay hata ayıklaması yapmak için, Visual Studio 'da Blend projelerini açabilirsiniz. Visual Studio 'da bir Blend projesi açmak için **Projeler** panelinde projeye sağ tıklayın ve ardından **Visual Studio 'da Düzenle**' ye tıklayın. Visual Studio 'da hata ayıklama oturumunuzu tamamladıktan sonra, tüm değişikliklerinizi kaydetmek için CTRL + SHIFT + S tuşlarına basın ve ardından Blend 'e geri dönün. Projeyi yeniden yüklemeniz istenecektir. Blend 'de çalışmaya devam etmek için **Tümüne Evet** ' e tıklayın.

Uygulamanızda hata ayıklama hakkında daha fazla bilgi için bkz. [Visual Studio 'DA UWP uygulamalarında hata ayıklama](../debugger/debugging-windows-store-and-windows-universal-apps.md).

## <a name="get-help"></a>Yardım alın

Blend uygulamanızda hata ayıklama konusunda daha fazla yardıma ihtiyacınız varsa, sorun veya soru göndermek için [UWP uygulama topluluğu forumlarında](https://social.msdn.microsoft.com/Forums/windowsapps/home?category=windowsapps) arama yapabilirsiniz.
