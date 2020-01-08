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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591339"
---
# <a name="identify-and-customize-keyboard-shortcuts-in-visual-studio"></a>Tanımlamak ve Visual Studio'daki klavye kısayollarını özelleştirme

Visual Studio komutları için kısayollar tanımlayabilir, bu kısayolları özelleştirebilir ve başkalarının kullanması için dışarı aktarabilirsiniz. Birçok kısayol her zaman aynı komutları çağırır, ancak kısayolun davranışı aşağıdaki koşullara göre değişebilir:

- Visual Studio 'Yu ilk kez açtığınızda, genel geliştirme veya görsel C#&mdash;varsayılan ortam ayarlarını seçersiniz. (Ayarlarınızı değiştirme veya sıfırlama hakkında daha fazla bilgi için bkz. [ortam ayarları](environment-settings.md).)

- Kısayolun davranışını özelleştirip özelleştirmediğiniz.

- Kısayolu seçtiğiniz anda içinde bulunduğunuz bağlam. Örneğin, **F2** kısayolu, **ayarlar tasarımcısını** kullanıyorsanız `Edit.EditCell` komutunu çağırır ve **Takım Gezgini**kullanıyorsanız `File.Rename` komutunu çağırır.

Ayarları, özelleştirme ve bağlam bağımsız olarak her zaman bulabilir ve klavye kısayolu Değiştir **seçenekleri** iletişim kutusu. Ayrıca [popüler klavye kısayollarında](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md)birkaç düzine komut için varsayılan klavye kısayollarına bakabilirsiniz. Tüm varsayılan kısayolların listesi için ( **genel geliştirme** ayarlarına bağlı olarak), [tüm klavye kısayollarına](../ide/default-keyboard-shortcuts-in-visual-studio.md)bakın.

Bir kısayol *genel* bağlamdaki bir komuta atanmışsa ve başka bağlam yoksa, bu kısayol her zaman bu komutu çağırır. Ancak bir kısayol, Genel bağlamda bir komuta ve özel bağlamda farklı bir komuta atanabilir. Böyle bir komutu özel bağlamda kullanırsanız, özel bağlama ilişkin komutu çağırır (Genel bağlama ilişkin komutu çağırmaz).

> [!NOTE]
> Ayarlarınıza ve Visual Studio sürümünüze göre, menü komutlarının adları ve konumları ve iletişim kutularında görünen seçenekler değişik olabilir. Bu sayfa, **genel geliştirme** ayarları profilini temel alır.

## <a name="identify-a-keyboard-shortcut"></a>Klavye kısayolu tanımlama

1. Menü çubuğunda, **Araçları** > **seçenekleri**.

2. Genişletin **ortam**ve ardından **klavye**.

   ![Seçenekler iletişim kutusundaki görüntüleme klavye kısayolları](../ide/media/optionskeyboard.png)

3. İçinde **içeren komutları göster** kutusuna, boşluk olmadan komutun adını bir kısmını veya tamamını girin.

   Örneğin, için komutları bulabilirsiniz `solutionexplorer`.

4. Listede doğru komutu seçin.

    Örneğin, seçebileceğiniz `View.SolutionExplorer`.

5. Komutun bir klavye kısayolu varsa görünür **seçili komut için kısayollar** listesi.

   ![Belirtilen komut için bir kısayol görüntüleyin](../ide/media/viewshortcut.png)

## <a name="customize-a-keyboard-shortcut"></a>Klavye kısayolunu özelleştirme

1. Menü çubuğunda, **Araçları** > **seçenekleri**.

2. Genişletin **ortam**ve ardından **klavye**.

3. İsteğe bağlı: adı, boşluk olmadan komut bir kısmını veya tamamını girerek komutların listesini filtrelemek **içeren komutları göster** kutusu.

4. Listede, klavye kısayolu atamak istediğiniz komutu seçin.

   İçinde **kullanım yeni kısayolu şunun içinde** listesinde, kısayolu kullanmak istediğiniz özellik alanını seçin.

   Örneğin, seçebileceğiniz **genel** kısayolun her bağlamda çalışmasını istiyorsanız. Başka bir düzenleyicide Genel olarak eşlenmemiş herhangi bir kısayolu kullanabilirsiniz. Aksi takdirde düzenleyici kısayolu geçersiz kılar.

   > [!NOTE]
   > Aşağıdaki anahtarları **küresel**bir klavye kısayolunun parçası olarak atayamazsınız:
   >
   > - ENTER, Tab, Caps Lock
   > - PRINT SCRN/SYS RQ, Scroll Lock, Duraklat/kes
   > - Ekle, giriş, son, sayfa yukarı, sayfa aşağı
   > - Windows logosu tuşu, uygulama anahtarı, herhangi bir ok tuşu
   > - Sayısal tuş takımında Lock, DELETE veya Clear NUM
   > - CTRL + ALT + DELETE tuş bileşimi

6. İçinde **kısayol tuşlarına basın** kutusunda, kullanmak istediğiniz kısayolu girin.

    > [!NOTE]
    > Bir harf ile birleştiren bir kısayol oluşturabilirsiniz **Alt** anahtar **Ctrl** tuşu veya her ikisi de. Birleştiren bir kısayol da oluşturabilirsiniz **Shift** anahtarı ve bir harf ile **Alt** anahtar **Ctrl** tuşu veya her ikisi de.

     Bir kısayol zaten başka bir komuta atanmışsa görünür **şu anda kullandığı kısayolunu** kutusu. Bu durumda, seçin **geri** başka bir denemeden önce kısayolu silmek için anahtar.

    ![Bir komut için farklı bir kısayol belirtin](../ide/media/reassignshortcut.png)

7. Seçin **atama** düğmesi.

    > [!NOTE]
    > Bir komut için farklı bir kısayol belirtirseniz, **ata**' ya tıklayın ve ardından iletişim kutusunu kapatmak için **iptal** ' e tıklayın, atadığınız kısayol geri döndürülemez.

## <a name="share-custom-keyboard-shortcuts"></a>Özel klavye kısayollarını paylaşma

Özel klavye kısayollarınızı bir dosyaya dışarı aktararak ve verileri içeri aktarabilmeleri için bu dosyayı başkalarına vererek, klavye kısayollarınızı paylaşabilirsiniz.

### <a name="to-export-only-keyboard-shortcuts"></a>Yalnızca klavye kısayollarını dışarı aktarmak için

1. Menü çubuğunda, **Araçları** > **içeri ve dışarı aktarma ayarları**.

2. **Seçili ortam ayarlarını dışarı aktar**' ı seçin ve ardından **İleri**' yi seçin.

3. Altında **hangi ayarları dışarı aktarmak istiyor musunuz?** temizleyin **tüm ayarlar** onay kutusunu işaretleyin, genişletme **seçenekleri**ve ardından **ortam**.

4. **Klavye** onay kutusunu seçin ve ardından **İleri**' yi seçin.

   ![Yalnızca özel klavye kısayollarını dışarı aktarma](../ide/media/exportshortcuts.png)

5. **Ayarlar dosyanıza ne ad vermek** istiyorsunuz ve ayarlarımı **Bu dizin kutularında depola** ' da, varsayılan değerleri bırakın veya farklı değerler belirtip **son**' u seçin.

::: moniker range="vs-2017"

Varsayılan olarak, kısayollarınızı bir dosyaya kaydedilir *%USERPROFILE%\Documents\Visual Studio 2017\Settings* klasör. Dosyanın adı ayarları dışarı aktardığınız ve uzantı tarihi yansıtır *.vssettings*.

::: moniker-end

::: moniker range=">=vs-2019"

Varsayılan olarak, kısayollarınız *%userprofile%\, Studio 2019 \ ayarlar* klasöründeki bir dosyaya kaydedilir. Dosyanın adı ayarları dışarı aktardığınız ve uzantı tarihi yansıtır *.vssettings*.

::: moniker-end

### <a name="to-import-only-keyboard-shortcuts"></a>Yalnızca klavye kısayollarını içeri aktarmak için

1. Menü çubuğunda, **Araçları** > **içeri ve dışarı aktarma ayarları**.

2. **Seçili ortam ayarlarını Içeri aktar** seçenek düğmesini seçin ve ardından **İleri**' yi seçin.

3. **Hayır, yeni ayarları içeri aktar, geçerli ayarlarım üzerine yaz** seçenek düğmesini seçin ve ardından **İleri**' yi seçin.

4. Altında **ayarlarım**, içeri aktarma veya seçmek istediğiniz kısayolları içeren dosyayı seçin **Gözat** doğru dosyayı bulmak için düğme.

5. Seçin **sonraki**.

6. Altında **hangi ayarları içeri aktarmak istiyor musunuz?** temizleyin **tüm ayarlar** onay kutusunu işaretleyin, genişletme **seçenekleri**ve ardından **ortam**.

7. **Klavye** onay kutusunu seçin ve ardından **son**' u seçin.

   ![Yalnızca özel klavye kısayollarını içeri aktarma](../ide/media/importshortcuts.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'nun erişilebilirlik özellikleri](../ide/reference/accessibility-features-of-visual-studio.md)
