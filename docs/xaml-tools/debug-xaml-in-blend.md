---
title: Blend |'de XAML'de hata ayıklama Microsoft Docs
description: Uygulamanıza XAML hatalarını Visual Studio için Blend, hatalarını ayıklamak ve çözmek için Visual Studio için Blend'daki araçları kullanmayı öğrenin.
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
ms.openlocfilehash: 5cd32b2eab82cd148bec4f21fa7a6f5e1f95c5b9
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726058"
---
# <a name="debug-xaml-in-blend"></a>Blend'de XAML hatalarını ayıklama

Uygulamanıza XAML'Visual Studio için Blend ayıklamak için Visual Studio için Blend'daki araçları kullanabilirsiniz. Proje derleme sırasında hatalar Sonuçlar panelinde **görüntülenir.** Hatayla ilgili işaretlemeyi bulmak için bir hataya çift tıklayın. Daha fazla çalışmanız gerekirse F12 tuşuna **basarak** Sonuçlar panelini **gizleyebilirsiniz.**

## <a name="syntax-errors"></a>Sözdizimi hataları

XAML veya arkadeki kod dosyaları dilin biçimlendirme kurallarına uymazsa söz dizimi hataları oluşur. Hatanın açıklaması, nasıl düzeltileceğini anlamanıza yardımcı olabilir. Liste ayrıca dosyanın adını ve hatanın oluştuğu satır numarasını belirtir. XAML hataları Sonuçlar **panelindeki İşaretleme** **sekmesinde** listelenir.

> [!TIP]
> XAML, XML tabanlı bir işaretleme dilidir ve XML söz dizimi kurallarını izler.

XAML söz dizimi hatalarının bazı yaygın nedenleri:

- Bir anahtar sözcük yanlış yazılmıştır veya büyük harf ayrımı yanlıştır.

- Öznitelikler veya metin dizeleri için tırnak işaretleri eksik.

- XAML öğesinde bir kapatma etiketi eksiktir.

- XAML öğesi, izin verilmeyen bir konumda bulunmaktadır.

Yaygın XAML söz dizimi hakkında daha fazla bilgi için [bkz. Temel XAML söz dizimi kılavuzu.](/windows/uwp/xaml-platform/xaml-syntax-guide)

Ayrıca Blend'de basit arka kod arkası söz dizimi hatalarını, derleme hatalarını ve çalışma zamanı hatalarını tanımlayabilir ve çözebilirsiniz. Ancak, arka alınan kod hatalarının daha kolay belirlenmesi ve bu hataların Visual Studio.

### <a name="debugging-sample-xaml-code"></a>Örnek XAML kodunda hata ayıklama

Aşağıdaki örnek, Blend'de basit bir XAML hata ayıklama oturumunda size yol sağlar.

#### <a name="to-create-a-project"></a>Bir proje oluşturmak için

1. Blend'de Dosya menüsünü **açın ve** yeni dosya'ya **Project.**

    Yeni **Project** iletişim kutusunda, sol tarafta proje türlerinin listesi görüntülenir. Bir proje türüne tıklarsanız, projeyle ilişkili proje şablonları sağ tarafta görünür.

2. Proje türleri listesinde Evrensel'e **Windows tıklayın.**

3. Proje şablonları listesinde Boş Uygulama **(Evrensel Uygulama) Windows.**

4. Ad **metin** kutusuna `DebuggingSample` yazın.

5. Konum **metin** kutusunda projenin konumunu doğrulayın.

6. Dil **listesinde Visual** **C# 'ye tıklayın** ve ardından Projeyi oluşturmak **için Tamam'a** tıklayın.

7. Tasarım yüzeyine sağ tıklayın ve ardından Kaynağı **Görüntüle'ye** tıklar ve Bölme **görünümüne geçiş** yapmak için.

8. Kodun sağ üst **köşesindeki** Kopyala bağlantısına tıklayarak aşağıdaki kodu kopyalayın.

   ```xml
   <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>
        <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>
   </Grid>
   ```

9. Varsayılan **Kılavuz'a** tıklayın ve kodu açma ve kapatma Kılavuz etiketleri **arasına** yapıştırın. Bitirdikten sonra kodunuzun aşağıdaki gibi olması gerekir:

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

10. Projeyi **derlemek için Ctrl** +  + **Shift B** tuşlarına basın.

    Projenin yapılamay durumuyla ilgili sizi uyaran  bir hata iletisi görüntülenir ve hataları liste alan Sonuçlar paneli uygulamanın alt kısmında görünür.

    ![Visual Studio için Blend'de XAML hatalarını ayıklama](../debugger/media/blend_debugxaml_xaml.png "blend_debugXAML_XAML")

### <a name="resolve-xaml-errors"></a>XAML hatalarını düzeltme

XAML hataları algılandığında, tasarım yüzeyi projenizin geçersiz işaretleme içerdiğini gösteren bir uyarı görüntüler. Hataları çözümlediğinde Sonuçlar panelindeki hata **listesi** güncelleştirilir. Tüm hataları çözümledikten sonra tasarım yüzeyi etkinleştirilir ve uygulama tasarım yüzeyinde görüntülenir.

#### <a name="to-resolve-the-xaml-errors"></a>XAML hatalarını çözmek için

1. Listede ilk hataya çift tıklayın. Açıklama şu şekildedir: "'<' değeri öznitelikte geçerli değil." Hataya çift tıklarsanız, işaretçi kodda karşılık gelen konumu bulur. Yukarıdaki `<` `Button` geçerlidir ve hata iletisinde önerilen bir öznitelik değildir. Önceki kod satırına bakarsanız özniteliğin kapanış tırnak işaretlerinin eksik olduğunu `Top` farkedersiniz. Kapanış tırnak işaretlerini yazın. Sonuçlar panelindeki hata listesinin **değişikliklerinizi** yansıtacak şekilde değiştirilebilir.

2. "'0' adı başında geçerli değil" açıklamasına çift tıklayın. `Margin="0,149,0,0"` iyi oluşturulmuş gibi görünür. Ancak, renk kodlamanın `Margin` kodda diğer örnekleriyle `Margin` eşleşmez. Kapatma tırnak işaretleri önceki ad/değer çifti () içinde eksik olduğundan, önceki özniteliğin değerinin bir parçası olarak okunur ve 0 bir ad/değer çiftinin başlangıcı `VerticalAlignment="Top` `Margin="` olarak okunur. için kapanış tırnak işaretlerini `Top` yazın. Sonuçlar panelindeki hata **listesi değişikliklerinizi** yansıtacak şekilde uzer.

3. Kalan hataya çift tıklayın: "'Düğme' kapanış XML etiketi eşleşmedi." İşaretçi, hatanın **nesnenin içinde** olduğunu öneren kapanış Kılavuz etiketinde () `</Grid>` `Grid` bulunur. İkinci nesnede `Button` kapanış etiketinin eksik olduğunu fark edersiniz. Kapatmayı ekledikten `/` sonra **Sonuçlar** paneli listesi güncelleştirilir. Bu ilk hatalar çözüldü, şimdi iki ek hata belirlendi.

4. "'İçerik' üyesi tanınmıyor veya erişilebilir değil"e çift tıklayın. `c`içinde `content` büyük harfli olması gerekir. Küçük harfli "c"yi büyük harf "c" ile değiştirin.

5. "'Mame' özelliği ad alanı içinde yok"a çift `http://schemas.microsoft.com/winfx/2006/xaml` tıklayın. "Mame" içinde "M" bir "N" olması gerekir. "M"yi "N" ile değiştirin. XAML ayrıştırılana kadar uygulama tasarım yüzeyinde görünür.

    ![Visual Studio için Blend'de XAML'de hata ayıklama](../debugger/media/blend_debugartboard_xaml.png "blend_debugArtboard_XAML")

    Projenizi **derlemek** için Ctrl Shift B tuşlarına +  +  basın ve kalan hata olmadığını onaylayın.

## <a name="debug-in-visual-studio"></a>Visual Studio'da hata ayıklama

Uygulamanıza kodda daha kolay Visual Studio için Blend projelerini bir uygulamada açabilirsiniz. Bir Blend projesini Visual Studio için Projeler **panelinde** projeye sağ tıklayın ve ardından **Visual Studio.** Visual Studio'da hata ayıklama oturum Visual Studio tüm değişikliklerinizi kaydetmek için Ctrl+Shift+S tuşlarına basın ve blend'e geri dönebilirsiniz. Projeyi yeniden yüklemeniz istenir. **Blend'de çalışmaya devam etmek** için Tamam'a tıklayın.

Uygulamanıza hata ayıklama hakkında daha fazla bilgi için bkz. [Visual Studio'de UWP uygulamalarının Visual Studio.](../debugger/debugging-windows-store-and-windows-universal-apps.md)

## <a name="get-help"></a>Yardım alın

Blend uygulamanıza hata ayıklaması için daha fazla yardıma ihtiyacınız varsa, UWP uygulaması topluluk [forumlarında](https://social.msdn.microsoft.com/Forums/windowsapps/home?category=windowsapps) sorunla ilgili gönderiler arayabilir veya bir soru paylaşabilirsiniz.
