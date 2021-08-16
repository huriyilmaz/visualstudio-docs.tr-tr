---
title: Blend 'de XAML hatalarını ayıklama | Microsoft Docs
description: uygulamanızdaki XAML hatalarını algılamak, hatalarını ayıklamak ve çözümlemek için Visual Studio için Blend araçlarını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 29a37182-2a2c-47e4-a4a9-2d5412738fed
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xaml-tools
ms.workload:
- uwp
ms.openlocfilehash: 3764a71b63968c879e3347f0a5c130c2d95ba3d22e7dd8bd5cc8914ccfa50669
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121365697"
---
# <a name="debug-xaml-in-blend"></a>Blend'de XAML hatalarını ayıklama

uygulamanızdaki XAML hatalarını ayıklamak için Visual Studio için Blend içindeki araçları kullanabilirsiniz. Bir proje oluşturduğunuzda, tüm hatalar **sonuçlar** panelinde görüntülenir. Hatayla ilgili işaretlemeyi bulmak için bir hataya çift tıklayın. Çalışmak için daha fazla yer gerekiyorsa, **F12** tuşuna basarak **sonuçlar** panelini gizleyebilirsiniz.

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

Ayrıca Blend 'de basit kod hataları, derleme hataları ve çalışma zamanı hataları tanımlayabilir ve bunları çözebilirsiniz. Ancak, arka plan kod hataları Visual Studio içinde tanımlanması ve çözümlenmesi daha kolay olabilir.

### <a name="debugging-sample-xaml-code"></a>Örnek XAML kodunda hata ayıklama

Aşağıdaki örnek, Blend 'de basit bir XAML hata ayıklama oturumunda size yol gösterecektir.

#### <a name="to-create-a-project"></a>Bir proje oluşturmak için

1. Blend 'de **Dosya** menüsünü açın ve ardından **yeni Project**' ye tıklayın.

    **yeni Project** iletişim kutusunda, sol tarafta proje türlerinin bir listesi görüntülenir. Bir proje türüne tıkladığınızda, onunla ilişkili proje şablonları sağ tarafta görüntülenir.

2. proje türleri listesinde, **evrensel Windows**' ye tıklayın.

3. Proje şablonları listesinde **boş uygulama (evrensel Windows)** seçeneğine tıklayın.

4. **Ad** metin kutusuna yazın `DebuggingSample` .

5. **Konum** metin kutusunda projenin konumunu doğrulayın.

6. **Dil** listesinde, **Visual C#**' yi tıklatın ve ardından projeyi oluşturmak için **Tamam** ' ı tıklatın.

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

9. Varsayılan **Kılavuzu** bulun ve açılış ve kapanış **kılavuz** etiketleri arasına kodu yapıştırın. İşiniz bittiğinde kodunuzun aşağıdaki gibi görünmesi gerekir:

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

10.  +  + Projeyi derlemek için CTRL SHIFT **B** tuşlarına basın.

    Projenin derlenmeyeceğini ve hataları listelerken **sonuçlar** bölmesinin uygulamanın altında göründüğünü belirten bir hata iletisi görüntülenir.

    ![Visual Studio için Blend'de XAML hatalarını ayıklama](../debugger/media/blend_debugxaml_xaml.png "blend_debugXAML_XAML")

### <a name="resolve-xaml-errors"></a>XAML hatalarını çözümleme

XAML hataları algılandığında tasarım yüzeyi, projenizin geçersiz biçimlendirme içerdiğini belirten bir uyarı görüntüler. Hataları çözümlediğinizde, **sonuçlar** panelindeki hata listesi güncellenir. Tüm hataları çözdüyseniz tasarım yüzeyi etkinleştirilir ve uygulamanız tasarım yüzeyinde görüntülenir.

#### <a name="to-resolve-the-xaml-errors"></a>XAML hatalarını çözümlemek için

1. Listedeki ilk hataya çift tıklayın. Açıklama "< ' değeri özniteliğinde geçerli değildir." Hatayı çift tıklattığınızda, işaretçi kodda karşılık gelen konumu bulur. `<`Yukarıdaki, `Button` hata iletisinde önerildiği şekilde değil, geçerli bir öznitelik değil. Yukarıdaki kod satırına baktığınızda, öznitelik için kapanan tırnak işaretlerinin eksik olduğunu fark edeceksiniz `Top` . Kapanış tırnak işaretlerini yazın. **Sonuçlar** panelindeki hata listesinin değişikliklerinizi yansıtacak şekilde güncelleştiğine dikkat edin.

2. "' 0" açıklamasına çift tıklayarak bir adın başlangıcında geçerli değildir. " `Margin="0,149,0,0"` iyi biçimlendirilmiş gibi görünüyor. Ancak, renk kodlamasının, `Margin` koddaki diğer örneklerle eşleşmediğinden emin olun `Margin` . Önceki ad/değer çiftindeki () kapanış tırnak işaretleri eksik olduğundan `VerticalAlignment="Top` , `Margin="` önceki özniteliğin değerinin bir parçası olarak salt okunurdur ve 0 bir ad/değer çiftinin başlangıcı olarak okunurdur. Kapanış tırnak işaretlerini yazın `Top` . **Sonuçlar** panelindeki hata listesi, yaptığınız değişiklikleri yansıtacak şekilde güncelleştirilir.

3. Kalan hataya çift tıklayın, "kapanış XML etiketi ' Button ' eşleşmiyor." İşaretçi,  `</Grid>` hatanın nesnenin içinde olması için kapanış kılavuz etiketinde () bulunur `Grid` . İkinci `Button` nesnede kapanış etiketinin eksik olduğuna dikkat edin. Kapatmayı ekledikten sonra `/` **sonuçlar** paneli listesi güncellenir. Artık bu ilk hatalar çözümlendiğinden, iki ek hata belirlenmiştir.

4. "Üye ' içerik ' tanınmıyor veya erişilebilir değil" seçeneğine çift tıklayın. `c`İçindeki, `content` büyük harf olmalıdır. "C" alt durumunu "c" büyük harfle değiştirin.

5. "' MAME ' özelliği ad alanında yok ' a çift tıklayın `http://schemas.microsoft.com/winfx/2006/xaml` ." "Mame" içindeki "d", "N" olmalıdır. "D" değerini bir "N" ile değiştirin. Artık XAML ayrıştırılabilmesine göre, uygulama tasarım yüzeyinde görünür.

    ![Visual Studio için Blend XAML hatalarını ayıklama](../debugger/media/blend_debugartboard_xaml.png "blend_debugArtboard_XAML")

     +  + Projenizi derlemek için CTRL SHIFT **B** tuşlarına basın ve kalan hata olmadığını onaylayın.

## <a name="debug-in-visual-studio"></a>Visual Studio'da hata ayıklama

uygulamanızdaki kodda hata ayıklamanın daha kolay olması için Visual Studio Blend projelerini açabilirsiniz. Visual Studio bir Blend projesi açmak için **projeler** panelinde projeye sağ tıklayın ve ardından **Visual Studio düzenle**' ye tıklayın. Visual Studio hata ayıklama oturumunuzu tamamladıktan sonra, tüm değişikliklerinizi kaydetmek için Ctrl + shıft + S tuşlarına basın ve ardından Blend 'e geri dönün. Projeyi yeniden yüklemeniz istenecektir. Blend 'de çalışmaya devam etmek için **Tümüne Evet** ' e tıklayın.

Uygulamanızda hata ayıklama hakkında daha fazla bilgi için bkz. [VISUAL STUDIO UWP uygulamalarının hatalarını ayıklama](../debugger/debugging-windows-store-and-windows-universal-apps.md).

## <a name="get-help"></a>Yardım alın

Blend uygulamanızda hata ayıklama konusunda daha fazla yardıma ihtiyacınız varsa, sorun veya soru göndermek için [UWP uygulama topluluğu forumlarında](https://social.msdn.microsoft.com/Forums/windowsapps/home?category=windowsapps) arama yapabilirsiniz.
