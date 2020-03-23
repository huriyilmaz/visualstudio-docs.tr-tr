---
title: Klavye kısayollarını tanımlama ve özelleştirme
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Environment.Keyboard
helpviewer_keywords:
- keyboard shortcuts [Visual Studio], customizing
- importing shortcut keys [Visual Studio]
- shortcut key combinations [Visual Studio]
- commands [Visual Studio], shortcut keys
- custom shortcut keys [Visual Studio]
- customizing keyboard shortcuts [Visual Studio]
- exporting shortcut keys [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce87385314ec84c7c0ed9d30c806a6287bb91d9e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591339"
---
# <a name="identify-and-customize-keyboard-shortcuts-in-visual-studio"></a>Visual Studio'da klavye kısayollarını tanımlama ve özelleştirme

Visual Studio komutları için kısayollar tanımlayabilir, bu kısayolları özelleştirebilir ve başkalarının kullanması için dışarı aktarabilirsiniz. Birçok kısayol her zaman aynı komutları çağırır, ancak kısayolun davranışı aşağıdaki koşullara göre değişebilir:

- Genel Geliştirme veya Visual C# gibi Visual&mdash;Studio'yu ilk kez açtığınızda hangi varsayılan ortam ayarlarını seçersiniz. (Ayarlarınızı değiştirme veya sıfırlama hakkında bilgi için [Ortam ayarlarına](environment-settings.md)bakın.)

- Kısayolun davranışını özelleştirip özelleştirmediğiniz.

- Kısayolu seçtiğiniz anda içinde bulunduğunuz bağlam. Örneğin, **Ayarlar Tasarımcısı'nı** kullanıyorsanız `Edit.EditCell` **F2** kısayolu komutu çağırır ve `File.Rename` Team **Explorer**kullanıyorsanız komutu çağırır.

Ayarlar, özelleştirme ve bağlam ne olursa olsun, **Seçenekler** iletişim kutusunda her zaman bir klavye kısayolu bulabilir ve değiştirebilirsiniz. Ayrıca Popüler klavye [kısayollarında](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md)birkaç düzine komut için varsayılan klavye kısayollarını da alabilirsiniz. Tüm varsayılan kısayolların tam listesi için **(Genel Geliştirme** ayarlarına göre), [tüm klavye kısayollarını](../ide/default-keyboard-shortcuts-in-visual-studio.md)görün.

*Genel* bağlamda bir komuta bir kısayol atanmışsa ve başka bağlamlar yoksa, bu kısayol her zaman bu komutu çağırır. Ancak bir kısayol, Genel bağlamda bir komuta ve özel bağlamda farklı bir komuta atanabilir. Böyle bir komutu özel bağlamda kullanırsanız, özel bağlama ilişkin komutu çağırır (Genel bağlama ilişkin komutu çağırmaz).

> [!NOTE]
> Ayarlarınıza ve Visual Studio sürümünüze göre, menü komutlarının adları ve konumları ve iletişim kutularında görünen seçenekler değişik olabilir. Bu sayfa Genel **Geliştirme** ayarları profilini temel alınr.

## <a name="identify-a-keyboard-shortcut"></a>Klavye kısayolu tanımlama

1. Menü çubuğunda **Araç** > **Seçenekleri'ni**seçin.

2. **Ortamı**Genişlet ve **ardından Klavye'yi**seçin.

   ![Seçenekler iletişim kutusunda klavye kısayollarını görüntüleme](../ide/media/optionskeyboard.png)

3. Kutu **içeren Göster komutlarına,** boşluk olmadan komutun adının tamamını veya bir kısmını girin.

   Örneğin, '' için `solutionexplorer`komutları bulabilirsiniz.

4. Listede doğru komutu seçin.

    Örneğin, seçebilirsiniz. `View.SolutionExplorer`

5. Komutun klavye kısayolu varsa, seçili komut listesi **için Kısayol(lar)'da** görünür.

   ![Belirli bir komut için kısayol görüntüleme](../ide/media/viewshortcut.png)

## <a name="customize-a-keyboard-shortcut"></a>Klavye kısayolu özelleştirme

1. Menü çubuğunda **Araç** > **Seçenekleri'ni**seçin.

2. **Ortamı**Genişlet ve **ardından Klavye'yi**seçin.

3. İsteğe bağlı: Boşluk olmadan komut adının tamamını veya bir kısmını girerek **komutlistesini kutuiçeren Göster komutlarına** filtre uygulayın.

4. Listede, klavye kısayolu atamak istediğiniz komutu seçin.

   Listedeki **yeni kısayolu Kullan'da,** kısayolu kullanmak istediğiniz özellik alanını seçin.

   Örneğin, kısayol'un tüm bağlamlarda çalışmasını istiyorsanız **Genel** Olarak'ı seçebilirsiniz. Başka bir düzenleyicide Genel olarak eşlenmemiş herhangi bir kısayolu kullanabilirsiniz. Aksi takdirde düzenleyici kısayolu geçersiz kılar.

   > [!NOTE]
   > Aşağıdaki tuşları **Global'de**bir klavye kısayolu olarak atayamazsınız:
   >
   > - Girin, Sekme, Büyük Harfler Kilidi
   > - Yazdırma Scrn/Sys Rq, Kaydırma Kilidi, Duraklatma/Kesme
   > - Ekle, Ana Sayfa, Bitiş, Sayfa Yukarı, Sayfa Aşağı
   > - Windows logo tuşu, Uygulama tuşu, Ok tuşlarından herhangi biri
   > - Sayısal tuş tuşu üzerinde Num Lock, Delete veya Clear
   > - Ctrl+Alt+Sil tuşu kombinasyonu

6. Basın **kısayol tuşu(lar)** kutusuna, kullanmak istediğiniz kısayolu girin.

    > [!NOTE]
    > Bir harfi **Alt** tuşu, **Ctrl** tuşu veya her ikisiyle birleştiren bir kısayol oluşturabilirsiniz. Shift **tuşunu** ve bir harfi **Alt** tuşu, **Ctrl** tuşu veya her ikisiyle birleştiren bir kısayol da oluşturabilirsiniz.

     Başka bir komuta zaten bir kısayol atanmışsa, şu anda kutu **tarafından kullanılan Kısayol'da** görünür. Bu durumda, farklı bir kısayol denemeden önce bu kısayolu silmek için **Backspace** tuşunu seçin.

    ![Komut için farklı bir kısayol belirtin](../ide/media/reassignshortcut.png)

7. **Atla** düğmesini seçin.

    > [!NOTE]
    > Bir komut için farklı bir kısayol belirtirseniz, **Ata'yı**tıklatın ve iletişim kutusunu kapatmak için **İptal'i** tıklatın, atadığınız kısayol geri döndürülmez.

## <a name="share-custom-keyboard-shortcuts"></a>Özel klavye kısayollarını paylaşın

Özel klavye kısayollarınızı bir dosyaya dışarı aktararak ve verileri içeri aktarabilmeleri için bu dosyayı başkalarına vererek, klavye kısayollarınızı paylaşabilirsiniz.

### <a name="to-export-only-keyboard-shortcuts"></a>Yalnızca klavye kısayollarını dışarı aktarmak için

1. Menü çubuğunda, **Araçlar** > **Alma ve Dışa Aktarma Ayarları'nı**seçin.

2. **Seçili ortam ayarlarını dışa**aktar'ı seçin ve sonra **İleri'yi**seçin.

3. **Hangi ayarlar altında dışa aktarmak istiyorsunuz?** **All Settings** **Options** **Environment**

4. **Klavye** onay kutusunu seçin ve sonra **İleri'yi**seçin.

   ![Yalnızca özelleştirilmiş klavye kısayollarını dışa aktarma](../ide/media/exportshortcuts.png)

5. Ayarlar **dosyanıza ne ad** vermek ve **ayarlar dosyamı bu dizin kutularında saklamak** istediğiniz, varsayılan değerleri bırakın veya farklı değerler belirtin ve sonra **Bitir'i**seçin.

::: moniker range="vs-2017"

Varsayılan olarak, kısayollarınız *%USERPROFILE%\Documents\Visual Studio 2017\Settings* klasöründeki bir dosyaya kaydedilir. Dosyanın adı, ayarları dışa aktardığınız tarihi yansıtır ve uzantı *.vssettings'tir.*

::: moniker-end

::: moniker range=">=vs-2019"

Varsayılan olarak, kısayollarınız *%USERPROFILE%\Documents\Visual Studio 2019\Settings* klasöründeki bir dosyaya kaydedilir. Dosyanın adı, ayarları dışa aktardığınız tarihi yansıtır ve uzantı *.vssettings'tir.*

::: moniker-end

### <a name="to-import-only-keyboard-shortcuts"></a>Yalnızca klavye kısayollarını içeri aktarmak için

1. Menü çubuğunda, **Araçlar** > **Alma ve Dışa Aktarma Ayarları'nı**seçin.

2. **Seçili ortam ayarlarını içe aktar** seçeneğini seçin ve sonra **İleri'yi**seçin.

3. **Hayır'ı seçin, yalnızca yeni ayarlar içe aktarın, geçerli ayarlar** seçeneğim düğmesini üzerine yazın ve sonra **İleri'yi**seçin.

4. **Ayarlarım'ın**altında, içe aktarmayapmak istediğiniz kısayolları içeren dosyayı seçin veya doğru dosyayı bulmak için **Gözat** düğmesini seçin.

5. **İleri**’yi seçin.

6. Hangi ayarları n için içe almak **All Settings** **istiyorsunuz?** **Options** **Environment**

7. **Klavye** onay kutusunu seçin ve ardından **Bitir'i**seçin.

   ![Yalnızca özelleştirilmiş klavye kısayollarını alma](../ide/media/importshortcuts.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'nun erişilebilirlik özellikleri](../ide/reference/accessibility-features-of-visual-studio.md)
