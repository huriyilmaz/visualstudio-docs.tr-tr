---
title: Blend 'de XAML hatalarını ayıklama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 29a37182-2a2c-47e4-a4a9-2d5412738fed
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8e032f9f99087df26c82b4984c2267a35236bf6e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "81444641"
---
# <a name="debug-xaml-in-blend"></a>Blend'de XAML hatalarını ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[blend_first](../includes/blend-first-md.md)]UYGULAMANıZDAKI xaml hatalarını ayıklamak için içindeki araçları kullanabilirsiniz. Bir proje oluşturduğunuzda, tüm hatalar **sonuçlar** panelinde görüntülenir. Hatayla ilgili işaretlemeyi bulmak için bir hataya çift tıklayın. Çalışmak için daha fazla yer gerekiyorsa, F12 tuşuna basarak **sonuçlar** panelini gizleyebilirsiniz.  
  
## <a name="syntax-errors"></a>Sözdizimi hataları  
 XAML veya arka plan kod dosyaları dilin biçimlendirme kurallarını izleyememesi durumunda sözdizimi hataları oluşur. Hatanın açıklaması, nasıl düzeltileceğini anlamanıza yardımcı olabilir. Listede ayrıca dosyanın adı ve hatanın gerçekleştiği satır numarası da belirtilir. XAML hataları, **sonuçlar** panelinde **biçimlendirme** sekmesinde listelenir.  
  
> [!TIP]
> XAML, XML tabanlı bir biçimlendirme dilidir ve XML sözdizimi kurallarını izler.  
  
 XAML sözdizimi hatalarının bazı yaygın nedenleri şunlardır:  
  
- Bir anahtar sözcük yanlış yazılmıştır veya büyük harf ayrımı yanlıştır.  
  
- Özniteliklerin veya metin dizelerinin etrafında tırnak işaretleri eksik.  
  
- XAML öğesinde bir kapatma etiketi eksiktir.  
  
- XAML öğesi, izin verilmeyen bir konumda bulunmaktadır.  
  
  Ortak XAML sözdizimi hakkında daha fazla bilgi için bkz. [temel xaml sözdizimi Kılavuzu](https://msdn.microsoft.com/library/windows/apps/hh700351.aspx).  
  
  Ayrıca, içinde basit kod hataları, derleme hataları ve çalışma zamanı hataları tanımlayabilir ve bunları çözebilirsiniz [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] . Ancak, Visual Studio 'da kodun arkasındaki hataların tanımlanması ve çözümlenmesi daha kolay olabilir.  
  
### <a name="debugging-sample-xaml-code"></a>Örnek XAML kodunda hata ayıklama  
 Aşağıdaki örnek, içinde basit bir XAML hata ayıklama oturumunda size yol gösterecektir [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] .  
  
##### <a name="to-create-a-project"></a>Bir proje oluşturmak için  
  
1. İçinde [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] , **Dosya** menüsünü açın ve ardından **Yeni proje**' ye tıklayın.  
  
    **Yeni proje** iletişim kutusunda, sol tarafta proje türlerinin bir listesi görüntülenir. Bir proje türüne tıkladığınızda, onunla ilişkili proje şablonları sağ tarafta görüntülenir.  
  
2. Proje türleri listesinde **XAML (Windows Mağazası)** öğesine tıklayın.  
  
3. Proje şablonları listesinde **boş uygulama**' ya tıklayın.  
  
4. **Ad** metin kutusuna yazın `DebuggingSample` .  
  
5. **Konum** metin kutusunda projenin konumunu doğrulayın.  
  
6. **Dil** listesinde, **Visual C#**' yi tıklatın ve ardından projeyi oluşturmak için **Tamam** ' ı tıklatın.  
  
7. Tasarım yüzeyine sağ tıklayın ve ardından **bölünmüş** görünüme geçmek Için **kaynağı görüntüle** ' ye tıklayın.  
  
8. Kodun sağ üst köşesindeki **Kopyala** bağlantısına tıklayarak aşağıdaki kodu kopyalayın.  
  
   ```  
   <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>  
        <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>  
   </Grid>  
  
   ```  
  
9. Varsayılan **Kılavuzu**bulun ve açılış ve kapanış **kılavuz** etiketleri arasına kodu yapıştırın. İşiniz bittiğinde kodunuzun aşağıdaki gibi görünmesi gerekir:  
  
    ```  
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
  
10. Projeyi derlemek için Ctrl+Shift+B'ye basın.  
  
    Projenin derlenmeyeceğini ve hataları listelerken **sonuçlar** bölmesinin uygulamanın altında göründüğünü belirten bir hata iletisi görüntülenir.  
  
    ![Visual Studio için Blend'de XAML hatalarını ayıklama](../debugger/media/blend-debugxaml-xaml.png "blend_debugXAML_XAML")  
  
### <a name="resolving-xaml-errors"></a>XAML hatalarını çözme  
 XAML hataları algılandığında tasarım yüzeyi, projenizin geçersiz biçimlendirme içerdiğini belirten bir uyarı görüntüler. Hataları çözümlediğinizde, **sonuçlar** panelindeki hata listesi güncellenir. Tüm hataları çözdüyseniz tasarım yüzeyi etkinleştirilir ve uygulamanız tasarım yüzeyinde görüntülenir.  
  
##### <a name="to-resolve-the-xaml-errors"></a>XAML hatalarını çözümlemek için  
  
1. Listedeki ilk hataya çift tıklayın. Açıklama "< ' değeri özniteliğinde geçerli değildir." Hatayı çift tıklattığınızda, işaretçi kodda karşılık gelen konumu bulur. `<`Yukarıdaki, `Button` hata iletisinde önerildiği şekilde değil, geçerli bir öznitelik değil. Yukarıdaki kod satırına baktığınızda, öznitelik için kapanan tırnak işaretlerinin eksik olduğunu fark edeceksiniz `Top` . Kapanış tırnak işaretlerini yazın. **Sonuçlar** panelindeki hata listesinin değişikliklerinizi yansıtacak şekilde güncelleştiğine dikkat edin.  
  
2. "' 0" açıklamasına çift tıklayarak bir adın başlangıcında geçerli değildir. " `Margin="0,149,0,0"` iyi biçimlendirilmiş gibi görünüyor. Ancak, renk kodlamasının, `Margin` koddaki diğer örneklerle eşleşmediğinden emin olun `Margin` . Önceki ad/değer çiftindeki () kapanış tırnak işaretleri eksik olduğundan `VerticalAlignment="Top` , `Margin="` önceki özniteliğin değerinin bir parçası olarak salt okunurdur ve 0 bir ad/değer çiftinin başlangıcı olarak okunurdur. Kapanış tırnak işaretlerini yazın `Top` . **Sonuçlar** panelindeki hata listesi, yaptığınız değişiklikleri yansıtacak şekilde güncelleştirilir.  
  
3. Kalan hataya çift tıklayın, "kapanış XML etiketi ' Button ' eşleşmiyor." İşaretçi, **Grid** `</Grid>` hatanın nesnenin içinde olması için kapanış kılavuz etiketinde () bulunur `Grid` . İkinci `Button` nesnede kapanış etiketinin eksik olduğuna dikkat edin. Kapatmayı ekledikten sonra `/` **sonuçlar** paneli listesi güncellenir. Artık bu ilk hatalar çözümlendiğinden, iki ek hata belirlenmiştir.  
  
4. "Üye ' içerik ' tanınmıyor veya erişilebilir değil" seçeneğine çift tıklayın. `c`İçindeki, `content` büyük harf olmalıdır. "C" alt durumunu "c" büyük harfle değiştirin.  
  
5. "' MAME ' özelliği ad alanında yok ' a çift tıklayın `https://schemas.microsoft.com/winfx/2006/xaml` ." "Mame" içindeki "d", "N" olmalıdır. "D" değerini bir "N" ile değiştirin. Artık XAML ayrıştırılabilmesine göre, uygulama tasarım yüzeyinde görünür.  
  
    ![Visual Studio için Blend XAML hatalarını ayıklama](../debugger/media/blend-debugartboard-xaml.png "blend_debugArtboard_XAML")  
  
    Projenizi derlemek için CTRL + SHIFT + B tuşlarına basın ve kalan hata olmadığını onaylayın.  
  
## <a name="debugging-in-visual-studio"></a>Visual Studio'da Hata Ayıklama  
 [!INCLUDE[blend_subs](../includes/blend-subs-md.md)]Uygulamanızdaki kodda daha kolay hata ayıklama yapmak için projeleri Visual Studio 'da açabilirsiniz. [!INCLUDE[blend_subs](../includes/blend-subs-md.md)]Visual Studio 'da bir projeyi açmak Için **Projeler** panelinde projeye sağ tıklayın ve ardından **Visual Studio 'da Düzenle**' ye tıklayın. Visual Studio 'da hata ayıklama oturumunuzu tamamladıktan sonra, tüm değişikliklerinizi kaydetmek için CTRL + SHIFT + S tuşlarına basın ve ardından geri dönün [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] . Projeyi yeniden yüklemeniz istenecektir. Üzerinde çalışmaya devam etmek için **Tümüne Evet** ' e tıklayın [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] .  
  
 Uygulamanızda hata ayıklama hakkında daha fazla bilgi için bkz. [Visual Studio 'Da Windows Mağazası uygulamalarında hata ayıklama](https://msdn.microsoft.com/library/windows/apps/hh441472.aspx).  
  
## <a name="getting-help"></a>Yardım alma  
 Uygulamanızda hata ayıklama konusunda daha fazla yardıma ihtiyacınız varsa [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] , sorununuzla ilgili olarak [Windows Mağazası uygulaması topluluk forumlarında](https://social.msdn.microsoft.com/Forums/windowsapps/home?category=windowsapps) arama yapabilir veya soru gönderebilirsiniz.
