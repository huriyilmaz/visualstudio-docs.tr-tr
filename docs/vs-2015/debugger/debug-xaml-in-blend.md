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
ms.openlocfilehash: d90e495ba64018479758e4fa38de0035601a8f0d
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298326"
---
# <a name="debug-xaml-in-blend"></a>Blend'de XAML hatalarını ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uygulamanızdaki XAML hatalarını ayıklamak için [!INCLUDE[blend_first](../includes/blend-first-md.md)] içindeki araçları kullanabilirsiniz. Bir proje oluşturduğunuzda, tüm hatalar **sonuçlar** panelinde görüntülenir. Hatayla ilgili işaretlemeyi bulmak için bir hataya çift tıklayın. Çalışmak için daha fazla yer gerekiyorsa, F12 tuşuna basarak **sonuçlar** panelini gizleyebilirsiniz.  
  
## <a name="syntax-errors"></a>Sözdizimi hataları  
 XAML veya arka plan kod dosyaları dilin biçimlendirme kurallarını izleyememesi durumunda sözdizimi hataları oluşur. Hatanın açıklaması, nasıl düzeltileceğini anlamanıza yardımcı olabilir. Listede ayrıca dosyanın adı ve hatanın gerçekleştiği satır numarası da belirtilir. XAML hataları, **sonuçlar** panelinde **biçimlendirme** sekmesinde listelenir.  
  
> [!TIP]
> XAML, XML tabanlı bir biçimlendirme dilidir ve XML sözdizimi kurallarını izler.  
  
 XAML sözdizimi hatalarının bazı yaygın nedenleri şunlardır:  
  
- Bir anahtar sözcük yanlış yazılmıştır veya büyük harf ayrımı yanlıştır.  
  
- Özniteliklerin veya metin dizelerinin etrafında tırnak işaretleri eksik.  
  
- XAML öğesinde bir kapatma etiketi eksiktir.  
  
- XAML öğesi, izin verilmeyen bir konumda bulunmaktadır.  
  
  Ortak XAML sözdizimi hakkında daha fazla bilgi için bkz. [temel xaml sözdizimi Kılavuzu](https://go.microsoft.com/fwlink/?LinkId=329942).  
  
  Ayrıca, [!INCLUDE[blend_subs](../includes/blend-subs-md.md)]' de basit kod hataları, derleme hataları ve çalışma zamanı hataları tanımlayabilir ve bunları çözebilirsiniz. Ancak, Visual Studio 'da kodun arkasındaki hataların tanımlanması ve çözümlenmesi daha kolay olabilir.  
  
### <a name="debugging-sample-xaml-code"></a>Örnek XAML kodunda hata ayıklama  
 Aşağıdaki örnek, [!INCLUDE[blend_subs](../includes/blend-subs-md.md)]basit bir XAML hata ayıklama oturumunda size yol gösterecektir.  
  
##### <a name="to-create-a-project"></a>Bir proje oluşturmak için  
  
1. [!INCLUDE[blend_subs](../includes/blend-subs-md.md)], **Dosya** menüsünü açın ve ardından **Yeni proje**' ye tıklayın.  
  
    **Yeni proje** iletişim kutusunda, sol tarafta proje türlerinin bir listesi görüntülenir. Bir proje türüne tıkladığınızda, onunla ilişkili proje şablonları sağ tarafta görüntülenir.  
  
2. Proje türleri listesinde **XAML (Windows Mağazası)** öğesine tıklayın.  
  
3. Proje şablonları listesinde **boş uygulama**' ya tıklayın.  
  
4. **Ad** metin kutusuna `DebuggingSample`yazın.  
  
5. **Konum** metin kutusunda projenin konumunu doğrulayın.  
  
6. **Dil** listesinde, **görsel C#** ' e tıklayın ve ardından projeyi oluşturmak için **Tamam** ' a tıklayın.  
  
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
  
10. Projeyi derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
    Projenin derlenmeyeceğini ve hataları listelerken **sonuçlar** bölmesinin uygulamanın altında göründüğünü belirten bir hata iletisi görüntülenir.  
  
    ![Visual Studio için Blend'de XAML hatalarını ayıklama](../debugger/media/blend-debugxaml-xaml.png "blend_debugXAML_XAML")  
  
### <a name="resolving-xaml-errors"></a>XAML hatalarını çözme  
 XAML hataları algılandığında tasarım yüzeyi, projenizin geçersiz biçimlendirme içerdiğini belirten bir uyarı görüntüler. Hataları çözümlediğinizde, **sonuçlar** panelindeki hata listesi güncellenir. Tüm hataları çözdüyseniz tasarım yüzeyi etkinleştirilir ve uygulamanız tasarım yüzeyinde görüntülenir.  
  
##### <a name="to-resolve-the-xaml-errors"></a>XAML hatalarını çözümlemek için  
  
1. Listedeki ilk hataya çift tıklayın. Açıklama "< ' değeri özniteliğinde geçerli değildir." Hatayı çift tıklattığınızda, işaretçi kodda karşılık gelen konumu bulur. Önceki `Button` `<`, hata iletisinde önerildiği şekilde bir öznitelik değil, geçerlidir. Yukarıdaki kod satırına baktığınızda, `Top` özniteliği için kapatma tırnak işaretlerinin eksik olduğunu fark edeceksiniz. Kapanış tırnak işaretlerini yazın. **Sonuçlar** panelindeki hata listesinin değişikliklerinizi yansıtacak şekilde güncelleştiğine dikkat edin.  
  
2. "' 0" açıklamasına çift tıklayarak bir adın başlangıcında geçerli değildir. " `Margin="0,149,0,0"` iyi biçimlendirilmiş gibi görünüyor. Ancak, `Margin` renk kodlamasının koddaki `Margin` diğer örneklerle eşleşmediğinden emin olun. Kapanış tırnak işaretleri önceki ad/değer çiftinde (`VerticalAlignment="Top`) olmadığından, `Margin="` önceki özniteliğin değerinin bir parçası olarak okunurdur ve 0 bir ad/değer çiftinin başlangıcı olarak okunurdur. `Top`için kapanan tırnak işaretlerini yazın. **Sonuçlar** panelindeki hata listesi, yaptığınız değişiklikleri yansıtacak şekilde güncelleştirilir.  
  
3. Kalan hataya çift tıklayın, "kapanış XML etiketi ' Button ' eşleşmiyor." İşaretçi kapanış **kılavuz** etiketinde bulunur (`</Grid>`) ve hatanın `Grid` nesnesinin içinde olması önerilir. İkinci `Button` nesnesinde kapanış etiketi eksik olduğuna dikkat edin. Kapanış `/`ekledikten sonra **sonuçlar** paneli listesi güncellenir. Artık bu ilk hatalar çözümlendiğinden, iki ek hata belirlenmiştir.  
  
4. "Üye ' içerik ' tanınmıyor veya erişilebilir değil" seçeneğine çift tıklayın. `content` `c` büyük harfle yazılmalıdır. "C" alt durumunu "c" büyük harfle değiştirin.  
  
5. "'<https://schemas.microsoft.com/winfx/2006/xaml>' ad alanında" mame "özelliği yok." "Mame" içindeki "d", "N" olmalıdır. "D" değerini bir "N" ile değiştirin. Artık XAML ayrıştırılabilmesine göre, uygulama tasarım yüzeyinde görünür.  
  
    ![Visual Studio için Blend XAML hatalarını ayıklama](../debugger/media/blend-debugartboard-xaml.png "blend_debugArtboard_XAML")  
  
    Projenizi derlemek için CTRL + SHIFT + B tuşlarına basın ve kalan hata olmadığını onaylayın.  
  
## <a name="debugging-in-visual-studio"></a>Visual Studio'da Hata Ayıklama  
 Uygulamanızdaki kodda daha kolay hata ayıklamak için Visual Studio 'da [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] projeleri açabilirsiniz. Visual Studio 'da bir [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] projesi açmak için **Projeler** panelinde projeye sağ tıklayın ve ardından **Visual Studio 'da Düzenle**' ye tıklayın. Visual Studio 'da hata ayıklama oturumunuzu tamamladıktan sonra, tüm değişikliklerinizi kaydetmek için CTRL + SHIFT + S tuşlarına basın ve ardından [!INCLUDE[blend_subs](../includes/blend-subs-md.md)]geri dönün. Projeyi yeniden yüklemeniz istenecektir. [!INCLUDE[blend_subs](../includes/blend-subs-md.md)]çalışmaya devam etmek için **Tümüne Evet** ' e tıklayın.  
  
 Uygulamanızda hata ayıklama hakkında daha fazla bilgi için bkz. [Visual Studio 'Da Windows Mağazası uygulamalarında hata ayıklama](https://go.microsoft.com/fwlink/?LinkId=329944).  
  
## <a name="getting-help"></a>Yardım alma  
 [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] uygulamanızda hata ayıklama konusunda daha fazla yardıma ihtiyacınız varsa, sorununuzla ilgili olarak [Windows Mağazası uygulaması topluluk forumlarında](https://go.microsoft.com/fwlink/?LinkId=280308) arama yapabilir veya soru gönderebilirsiniz.
