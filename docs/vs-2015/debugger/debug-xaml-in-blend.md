---
title: Karışımda Hata Ayıklama XAML | Microsoft Dokümanlar
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
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444641"
---
# <a name="debug-xaml-in-blend"></a>Blend'de XAML hatalarını ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uygulamanızdaki XAML [!INCLUDE[blend_first](../includes/blend-first-md.md)] hatasını ayıklamak için araçları kullanabilirsiniz. Bir proje oluşturduğunuzda, **sonuçlar** panelinde hatalar görüntülenir. Hatayla ilgili biçimlendirmeyi bulmak için bir hatayı çift tıklatın. Çalışmak için daha fazla yere ihtiyacınız varsa, F12 tuşuna basarak **Sonuçlar** panelini gizleyebilirsiniz.  
  
## <a name="syntax-errors"></a>Sözdizimi hataları  
 XAML veya kod arkasındaki dosyalar dilin biçimlendirme kurallarına uymuyorsa sözdizimi hataları oluşur. Hatanın açıklaması, nasıl düzeltileceğini anlamanıza yardımcı olabilir. Listede ayrıca dosyanın adı ve hatanın oluştuğu satır numarası da belirtilir. XAML hataları **Sonuçlar** panelindeki **Biçimlendirme** sekmesinde listelenir.  
  
> [!TIP]
> XAML, XML tabanlı biçimlendirme dilidir ve XML sözdizimi kurallarına uyar.  
  
 XAML sözdizimi hatalarının bazı yaygın nedenleri şunlardır:  
  
- Bir anahtar sözcük yanlış yazılmıştır veya büyük harf ayrımı yanlıştır.  
  
- Özniteliklerin veya metin dizelerin inetrafında tırnak işaretleri eksiktir.  
  
- XAML öğesinde bir kapatma etiketi eksiktir.  
  
- XAML öğesi, izin verilmeyen bir konumda bulunmaktadır.  
  
  Ortak XAML sözdizimi hakkında daha fazla bilgi için [Temel XAML sözdizimi kılavuzuna](https://msdn.microsoft.com/library/windows/apps/hh700351.aspx)bakın.  
  
  Ayrıca, [!INCLUDE[blend_subs](../includes/blend-subs-md.md)]'deki basit kod arkasındaki sözdizimi hatalarını, derleme hatalarını ve çalışma zamanı hatalarını tanımlayabilir ve çözümleyebilirsiniz. Ancak, Visual Studio'da kod arkası hatalarının tanımlanması ve çözülmesi daha kolay olabilir.  
  
### <a name="debugging-sample-xaml-code"></a>Örnek XAML kodunun hata ayıklanması  
 Aşağıdaki örnek, [!INCLUDE[blend_subs](../includes/blend-subs-md.md)]basit bir XAML hata ayıklama oturumunda size yol verecektir.  
  
##### <a name="to-create-a-project"></a>Bir proje oluşturmak için  
  
1. Dosya [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] **menüsünü** açın ve ardından **Yeni Proje'yi**tıklatın.  
  
    Yeni **Proje** iletişim kutusunda, sol tarafta proje türlerinin listesi görüntülenir. Proje türünü tıklattığınızda, projeyle ilişkili proje şablonları sağ tarafta görünür.  
  
2. Proje türleri listesinde **XAML (Windows Mağazası)** seçeneğini tıklatın.  
  
3. Proje şablonları listesinde Boş **Uygulama'yı**tıklatın.  
  
4. **Ad** metin kutusuna, `DebuggingSample`yazın.  
  
5. **Konum** metin kutusunda, projenin konumunu doğrulayın.  
  
6. **Dil** listesinde Visual **C#** seçeneğini tıklatın ve projeyi oluşturmak için **Tamam'ı** tıklatın.  
  
7. Tasarım yüzeyine sağ tıklayın ve ardından **Görünüm'e** geçmek için **Kaynağı Görüntüle'yi** tıklatın.  
  
8. Kodun sağ üst köşesindeki **Kopyala** bağlantısını tıklatarak aşağıdaki kodu kopyalayın.  
  
   ```  
   <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>  
        <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>  
   </Grid>  
  
   ```  
  
9. Varsayılan **Izgara'yı**bulun ve kodu açma ve kapatma **Kılavuz** etiketleri arasına yapıştırın. İşinizi bitirdiğinizde, kodunuz aşağıdaki gibi görünmelidir:  
  
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
  
    Projenin oluşturulamayacağı konusunda sizi uyaran bir hata iletisi görüntülenir ve hataları listeleyen **Sonuçlar** paneli uygulamanın alt kısmında görünür.  
  
    ![Visual Studio için Blend'de XAML hatalarını ayıklama](../debugger/media/blend-debugxaml-xaml.png "blend_debugXAML_XAML")  
  
### <a name="resolving-xaml-errors"></a>XAML hatalarını çözme  
 XAML hataları algılandığında, tasarım yüzeyi projenizin geçersiz biçimlendirme içerdiğini belirten bir uyarı görüntüler. Hataları giderirken, **Sonuçlar** panelindeki hata listesi güncelleştirilir. Tüm hataları giderdiğinizde, tasarım yüzeyi etkinleştirilir ve uygulamanız tasarım yüzeyinde görüntülenir.  
  
##### <a name="to-resolve-the-xaml-errors"></a>XAML hatalarını gidermek için  
  
1. Listedeki ilk hatayı çift tıklatın. Açıklama "'<' değeri öznitelik geçerli değildir." Hatayı çift tıklattığınızda, işaretçi kodda karşılık gelen konumu bulur. Önceki `<` geçerli `Button` ve hata iletisinde önerilen bir öznitelik değil. Önceki kod satırına bakarsanız, öznitelik `Top` için kapanış tırnak işaretlerinin eksik olduğunu fark esiniz. Kapanış tırnak işaretlerini yazın. **Sonuçlar** panelindeki hata listesinin değişikliklerinizi yansıtacak şekilde güncellere delanın.  
  
2. "'0' açıklamasını çift tıklatın bir adın başında geçerli değildir." `Margin="0,149,0,0"`iyi şekillenmiş gibi görünüyor. Ancak, renk kodlama kodundaki diğer örnekleri `Margin` `Margin` eşleşmiyor unutmayın. Kapanış tırnak işaretleri önceki ad/değer çiftinden eksik`VerticalAlignment="Top`olduğundan `Margin="` ( ), önceki özniteliğin değerinin bir parçası olarak okunur ve 0 bir ad/değer çiftinin başlangıcı olarak okunur. `Top`Kapanış tırnak işaretlerini yazın. **Değişikliklerinizi** yansıtmak için Sonuçlar panelindeki hata listesi güncellenir.  
  
3. Kalan hatayı çift tıklatın, "Kapanış XML etiketi 'Düğme' uyumsuz." İşaretçi, hatanın `Grid` nesnenin içinde`</Grid>`olduğunu düşündüren kapanış **Grid** etiketinde bulunur. İkinci `Button` nesnenin kapanış etiketini kaçırdığına dikkat edin. Kapanışı `/`ekledikten **sonra, Sonuçlar** paneli listesi güncelleştirilir. Bu ilk hatalar çözüldüğüne göre, iki ek hata tanımlandı.  
  
4. Çift tıklayın "Üye 'içerik' tanınmıyor veya erişilemez." In `c` `content` büyük harf olmalı. Küçük harf "c"yi büyük harf "c" ile değiştirin.  
  
5. Çift tıklayın "Özellik 'Mame' `https://schemas.microsoft.com/winfx/2006/xaml` ad alanında yok." "Mame"deki "M" "N" olmalı. "M" ile "N" değiştirin. Artık XAML ayrıştırılabildiği için uygulama tasarım yüzeyinde görünür.  
  
    ![Visual Studio için Karışım xaml hata ayıklama](../debugger/media/blend-debugartboard-xaml.png "blend_debugArtboard_XAML")  
  
    Projenizi oluşturmak ve kalan hata olmadığını doğrulamak için Ctrl+Shift+B tuşuna basın.  
  
## <a name="debugging-in-visual-studio"></a>Visual Studio'da Hata Ayıklama  
 Uygulamanızdaki [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] kodu daha kolay hata ayıklamak için Visual Studio'da projeler açabilirsiniz. Visual Studio'da proje [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] açmak için **Projeler** panelindeki projeyi sağ tıklatın ve ardından Visual **Studio'da Edit'i**tıklatın. Visual Studio'daki hata ayıklama oturumunuzu tamamladıktan sonra, tüm değişikliklerinizi kaydetmek için Ctrl+Shift+S tuşuna [!INCLUDE[blend_subs](../includes/blend-subs-md.md)]basın ve sonra tekrar . Projeyi yeniden yüklemeniz istenir. Çalışmaya devam etmek için [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] **Tümüne Evet'i** tıklatın.  
  
 Uygulamanızın hata ayıklama hakkında daha fazla bilgi için [Visual Studio'daki Hata Ayıklama Windows Mağazası uygulamalarına](https://msdn.microsoft.com/library/windows/apps/hh441472.aspx)bakın.  
  
## <a name="getting-help"></a>Yardım alma  
 Uygulamanızın [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] hata ayıklama konusunda daha fazla yardıma ihtiyacınız varsa, sorununuzun ilgili gönderileri için [Windows Mağazası uygulama topluluk forumlarında](https://social.msdn.microsoft.com/Forums/windowsapps/home?category=windowsapps) arama yapabilir veya bir soru gönderebilirsiniz.
