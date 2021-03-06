---
description: Visual Studio komutları için kısayollar tanımlayabilir, bu kısayolları özelleştirebilir ve başkalarının kullanması için dışarı aktarabilirsiniz.
title: Klavye kısayollarını tanımlama ve özelleştirme
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4686a6459f62fceeebe202cf52d7c30cf99f6fc3
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221255"
---
# <a name="identify-and-customize-keyboard-shortcuts-in-visual-studio"></a>Visual Studio 'da klavye kısayollarını tanımla ve Özelleştir

Visual Studio komutları için kısayollar tanımlayabilir, bu kısayolları özelleştirebilir ve başkalarının kullanması için dışarı aktarabilirsiniz. Birçok kısayol her zaman aynı komutları çağırır, ancak kısayolun davranışı aşağıdaki koşullara göre değişebilir:

- Visual Studio 'Yu ilk kez açtığınızda &mdash; , genel geliştirme veya Visual C# için hangi varsayılan ortam ayarları seçersiniz. (Ayarlarınızı değiştirme veya sıfırlama hakkında daha fazla bilgi için bkz. [ortam ayarları](environment-settings.md).)

- Kısayolun davranışını özelleştirip özelleştirmediğiniz.

- Kısayolu seçtiğiniz anda içinde bulunduğunuz bağlam. Örneğin,  `Edit.EditCell` **Ayarlar tasarımcısını** kullanıyorsanız F2 kısayolu komutu çağırır ve `File.Rename` **Takım Gezgini** kullanıyorsanız komutu çağırır.

Ayarlar, özelleştirme ve bağlamlarından bağımsız olarak, **Seçenekler** iletişim kutusunda her zaman bir klavye kısayolunu bulabilir ve değiştirebilirsiniz. Ayrıca [popüler klavye kısayollarında](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md)birkaç düzine komut için varsayılan klavye kısayollarına bakabilirsiniz. Tüm varsayılan kısayolların listesi için ( **genel geliştirme** ayarlarına bağlı olarak), [tüm klavye kısayollarına](../ide/default-keyboard-shortcuts-in-visual-studio.md)bakın.

Bir kısayol *genel* bağlamdaki bir komuta atanmışsa ve başka bağlam yoksa, bu kısayol her zaman bu komutu çağırır. Ancak bir kısayol, Genel bağlamda bir komuta ve özel bağlamda farklı bir komuta atanabilir. Böyle bir komutu özel bağlamda kullanırsanız, özel bağlama ilişkin komutu çağırır (Genel bağlama ilişkin komutu çağırmaz).

> [!NOTE]
> Ayarlarınıza ve Visual Studio sürümünüze göre, menü komutlarının adları ve konumları ve iletişim kutularında görünen seçenekler değişik olabilir. Bu sayfa, **genel geliştirme** ayarları profilini temel alır.

## <a name="identify-a-keyboard-shortcut"></a>Klavye kısayolunu tanımla

1. Menü çubuğunda **Araçlar**  >  **Seçenekler**' i seçin.

2. **Ortam**' ı genişletin ve ardından **klavye**' yi seçin.

   ![Seçenekler iletişim kutusunda klavye kısayollarını görüntüleme](../ide/media/optionskeyboard.png)

3. **İçerilen komutları göster** kutusunda, boşluk olmadan komutun adının tamamını veya bir kısmını girin.

   Örneğin, için komutları bulabilirsiniz `solutionexplorer` .

4. Listede doğru komutu seçin.

    Örneğin, seçeneğini belirleyebilirsiniz `View.SolutionExplorer` .

5. Komutun klavye kısayolu varsa, **Seçilen komut listesi Için kısayollar** görüntülenir.

   ![Belirtilen komut için bir kısayol görüntüle](../ide/media/viewshortcut.png)

## <a name="customize-a-keyboard-shortcut"></a>Klavye kısayolunu özelleştirme

1. Menü çubuğunda **Araçlar**  >  **Seçenekler**' i seçin.

2. **Ortam**' ı genişletin ve ardından **klavye**' yi seçin.

3. İsteğe bağlı: komutun adının tümünü veya bir kısmını, **içerilen komutları göster** kutusunu girerek komut listesini filtreleyin.

4. Listede, klavye kısayolu atamak istediğiniz komutu seçin.

   **Yeni Kısayol kullan** listesinde, kısayolu kullanmak istediğiniz özellik alanını seçin.

   Örneğin, kısayolun tüm bağlamlarda çalışmasını istiyorsanız **genel** ' i seçebilirsiniz. Başka bir düzenleyicide Genel olarak eşlenmemiş herhangi bir kısayolu kullanabilirsiniz. Aksi takdirde düzenleyici kısayolu geçersiz kılar.

   > [!NOTE]
   > Aşağıdaki anahtarları **küresel** bir klavye kısayolunun parçası olarak atayamazsınız:
   >
   > - ENTER, Tab, Caps Lock
   > - PRINT SCRN/SYS RQ, Scroll Lock, Duraklat/kes
   > - Ekle, giriş, son, sayfa yukarı, sayfa aşağı
   > - Windows logosu tuşu, uygulama anahtarı, herhangi bir ok tuşu
   > - Sayısal tuş takımında Lock, DELETE veya Clear NUM
   > - CTRL + ALT + DELETE tuş bileşimi

6. **Kısayol tuşlarını bas** kutusunda, kullanmak istediğiniz kısayolu girin.

    > [!NOTE]
    > Bir harfi **alt** tuşu, **CTRL** tuşu veya her ikisiyle birleştiren bir kısayol oluşturabilirsiniz. Ayrıca, **alt** tuşu, **CTRL** tuşu veya her ikisiyle de **SHIFT** tuşunu ve bir harfi birleştiren bir kısayol da oluşturabilirsiniz.

     Bir kısayol zaten başka bir komuta atanmışsa, bu, **Şu anda kullanıldığı kısayolda** görünür. Bu durumda, farklı bir tane denemeden önce bu kısayolu silmek için **geri al** tuşunu seçin.

    ![Komut için farklı bir kısayol belirtin](../ide/media/reassignshortcut.png)

7. **Ata** düğmesini seçin.

    > [!NOTE]
    > Bir komut için farklı bir kısayol belirtirseniz, **ata**' ya tıklayın ve ardından iletişim kutusunu kapatmak için **iptal** ' e tıklayın, atadığınız kısayol geri döndürülemez.

## <a name="share-custom-keyboard-shortcuts"></a>Özel klavye kısayollarını paylaşma

Özel klavye kısayollarınızı bir dosyaya dışarı aktararak ve verileri içeri aktarabilmeleri için bu dosyayı başkalarına vererek, klavye kısayollarınızı paylaşabilirsiniz.

### <a name="to-export-only-keyboard-shortcuts"></a>Yalnızca klavye kısayollarını dışarı aktarmak için

1. Menü çubuğunda **Araçlar**  >  **içeri aktar ve dışarı aktar ayarları**' nı seçin.

2. **Seçili ortam ayarlarını dışarı aktar**' ı seçin ve ardından **İleri**' yi seçin.

3. **Hangi ayarları dışarı aktarmak istiyorsunuz?** bölümünde, **Tüm ayarlar** onay kutusunun işaretini kaldırın, **Seçenekler**' i genişletin ve ardından **ortam**' ı genişletin.

4. **Klavye** onay kutusunu seçin ve ardından **İleri**' yi seçin.

   ![Yalnızca özelleştirilmiş klavye kısayollarını dışarı aktar](../ide/media/exportshortcuts.png)

5. **Ayarlar dosyanıza ne ad vermek** istiyorsunuz ve ayarlarımı **Bu dizin kutularında depola** ' da, varsayılan değerleri bırakın veya farklı değerler belirtip **son**' u seçin.

::: moniker range="vs-2017"

Varsayılan olarak, kısayollarınız *%userprofile%\, Studio 2017 \ Settings* klasöründeki bir dosyaya kaydedilir. Dosyanın adı, ayarları verdiğiniz tarihi yansıtır ve uzantı *. vssettings* olur.

::: moniker-end

::: moniker range=">=vs-2019"

Varsayılan olarak, kısayollarınız *%userprofile%\, Studio 2019 \ ayarlar* klasöründeki bir dosyaya kaydedilir. Dosyanın adı, ayarları verdiğiniz tarihi yansıtır ve uzantı *. vssettings* olur.

::: moniker-end

### <a name="to-import-only-keyboard-shortcuts"></a>Yalnızca klavye kısayollarını içeri aktarmak için

1. Menü çubuğunda **Araçlar**  >  **içeri aktar ve dışarı aktar ayarları**' nı seçin.

2. **Seçili ortam ayarlarını Içeri aktar** seçenek düğmesini seçin ve ardından **İleri**' yi seçin.

3. **Hayır, yeni ayarları içeri aktar, geçerli ayarlarım üzerine yaz** seçenek düğmesini seçin ve ardından **İleri**' yi seçin.

4. Ayarlarım **altında,** içeri aktarmak istediğiniz kısayolları içeren dosyayı seçin veya doğru dosyayı bulmak Için, **Gözden** geçirme düğmesini seçin.

5. **İleri**’yi seçin.

6. **Hangi ayarları içeri aktarmak istiyorsunuz?**, **Tüm ayarlar** onay kutusunun işaretini kaldırın, **Seçenekler**' i genişletin ve ardından **ortam**' ı genişletin.

7. **Klavye** onay kutusunu seçin ve ardından **son**' u seçin.

   ![Yalnızca özelleştirilmiş klavye kısayollarını içeri aktar](../ide/media/importshortcuts.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'nun erişilebilirlik özellikleri](../ide/reference/accessibility-features-of-visual-studio.md)
