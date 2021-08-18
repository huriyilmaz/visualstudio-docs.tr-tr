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
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: e69c2f43d4fdd306c556632aad2c271072987a9a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122101732"
---
# <a name="identify-and-customize-keyboard-shortcuts-in-visual-studio"></a>Klavye kısayollarını tanımlama ve Visual Studio

Visual Studio komutları için kısayollar tanımlayabilir, bu kısayolları özelleştirebilir ve başkalarının kullanması için dışarı aktarabilirsiniz. Birçok kısayol her zaman aynı komutları çağırır, ancak kısayolun davranışı aşağıdaki koşullara göre değişebilir:

- Genel Geliştirme veya Visual C# gibi bir Visual Studio ilk kez açmak &mdash; için hangi varsayılan ortam ayarlarını seçersiniz? (Ayarlarınızı değiştirme veya sıfırlama hakkında bilgi için bkz. [Ortam ayarları.)](environment-settings.md)

- Kısayolun davranışını özelleştirip özelleştirmediğiniz.

- Kısayolu seçtiğiniz anda içinde bulunduğunuz bağlam. Örneğin, Ayarlar Designer kullanıyorsanız **F2** kısayolu komutu çağırır ve Takım Gezgini. `Edit.EditCell`  `File.Rename` 

Ayarlar, özelleştirme ve bağlam ne olursa olsun, Seçenekler iletişim kutusunda her zaman bir klavye kısayolunu bulabilir **ve** değiştirebilirsiniz. Ayrıca Popüler klavye kısayolları içinde birkaç düzine komut için varsayılan klavye [kısayollarını da aramanız gerekir.](../ide/default-keyboard-shortcuts-in-visual-studio.md#popular) Tüm varsayılan kısayolların tam listesi için (Genel Geliştirme **ayarlarına göre),** bkz. [Tüm klavye kısayolları.](../ide/default-keyboard-shortcuts-in-visual-studio.md)

Genel bağlamdaki bir komuta bir  kısayol atanırsa ve başka bağlam atanmazsa, bu kısayol her zaman bu komutu çağırır. Ancak bir kısayol, Genel bağlamda bir komuta ve özel bağlamda farklı bir komuta atanabilir. Böyle bir komutu özel bağlamda kullanırsanız, özel bağlama ilişkin komutu çağırır (Genel bağlama ilişkin komutu çağırmaz).

> [!NOTE]
> Ayarlarınıza ve Visual Studio sürümünüze göre, menü komutlarının adları ve konumları ve iletişim kutularında görünen seçenekler değişik olabilir. Bu sayfa Genel Geliştirme **ayarları profilini** temel alan bir sayfadır.

## <a name="identify-a-keyboard-shortcut"></a>Klavye kısayolunu tanımlama

1. Menü çubuğunda Araçlar **Seçenekleri'ne**  >  **tıklayın.**

2. **Ortam'ı** genişletin ve ardından Klavye'yi **seçin.**

   ![Seçenekler iletişim kutusunda klavye kısayollarını görüntüleme](../ide/media/optionskeyboard.png)

3. Komut **içeren komutları göster** kutusuna komutun adının hepsini veya bir kısmını boşluk olmadan girin.

   Örneğin, için komutları `solutionexplorer` bulabilirsiniz.

4. Listede doğru komutu seçin.

    Örneğin, `View.SolutionExplorer` seçebilirsiniz.

5. Komutun bir klavye kısayolu varsa, bu kısayol **seçili komut listesinin Kısayollar'larında** görünür.

   ![Belirtilen komut için kısayolu görüntüleme](../ide/media/viewshortcut.png)

## <a name="customize-a-keyboard-shortcut"></a>Klavye kısayolunu özelleştirme

1. Menü çubuğunda Araçlar **Seçenekleri'ne**  >  **tıklayın.**

2. **Ortam'ı** genişletin ve ardından Klavye'yi **seçin.**

3. İsteğe bağlı: Komut içeren komutları göster kutusuna komut adının bir kısmını veya hepsini boşluk olmadan girerek **komut listesini filtrele.**

4. Listede, klavye kısayolu atamak istediğiniz komutu seçin.

   Yeni **kısayolu kullan** listesinde, kısayolu kullanmak istediğiniz özellik alanı seçin.

   Örneğin, kısayolun **tüm bağlamlarda** çalışması için Genel'i seçebilirsiniz. Başka bir düzenleyicide Genel olarak eşlenmemiş herhangi bir kısayolu kullanabilirsiniz. Aksi takdirde düzenleyici kısayolu geçersiz kılar.

   > [!NOTE]
   > Genel'de bir klavye kısayolu parçası olarak aşağıdaki anahtarları **atayabilirsiniz:**
   >
   > - Enter, Sekme, Caps Lock
   > - Scrn/Sys Rq Yazdırma, Kaydırma Kilidi, Duraklatma/Kesme
   > - Ekle, Giriş, Bitiş, Sayfa Yukarı, Sayfa Aşağı
   > - Windows logo anahtarı, Uygulama anahtarı ve Ok anahtarlarının herhangi biri
   > - Sayısal tuş takımındaki Num Kilidi, Silme veya Temizleme
   > - Ctrl+Alt+Delete tuş bileşimi

6. Kısayol **tuşlarına basın kutusuna** kullanmak istediğiniz kısayolu girin.

    > [!NOTE]
    > Bir harfi **Alt** tuşuyla, **Ctrl** tuşuyla veya her ikisini birden birleştiren bir kısayol oluşturabilirsiniz. Shift tuşunu ve bir harfi **Alt** tuşuyla, **Ctrl** **tuşuyla** veya her ikisini birden birleştiren bir kısayol da oluşturabilirsiniz.

     Başka bir komuta zaten atanmış bir kısayol varsa, kısayol şu anda tarafından kullanılan **Kısayol kutusunda** görünür. Bu durumda, farklı bir **kısayol denemeden** önce bu kısayolu silmek için Geri Al tuşuna basın.

    ![Komut için farklı bir kısayol belirtme](../ide/media/reassignshortcut.png)

7. Ata **düğmesini** seçin.

    > [!NOTE]
    > Bir komut için farklı bir kısayol belirtirseniz,  **Ata'ya** ve ardından İptal'e tıklarsanız iletişim kutusunu kapatırsanız, atadığınız kısayol geri döndürülmez.

## <a name="share-custom-keyboard-shortcuts"></a>Özel klavye kısayollarını paylaşma

Özel klavye kısayollarınızı bir dosyaya dışarı aktararak ve verileri içeri aktarabilmeleri için bu dosyayı başkalarına vererek, klavye kısayollarınızı paylaşabilirsiniz.

### <a name="to-export-only-keyboard-shortcuts"></a>Yalnızca klavye kısayollarını dışarı aktarmak için

1. Menü çubuğunda Araçlar İçeri ve Dışarı  >  **Aktarma'Ayarlar.**

2. Seçili **ortam ayarlarını dışarı aktar'ı** ve ardından Sonraki'yi **seçin.**

3. Hangi **ayarları dışarı aktarmayı istiyorsunuz?** altında Tüm ayarlar **onay Ayarlar** kutusunun işaretini kaldırın, Seçenekler'i **genişletin** ve ardından Ortam'ı **genişletin.**

4. Klavye onay **kutusunu** ve ardından Sonraki'yi **seçin.**

   ![Yalnızca özelleştirilmiş klavye kısayollarını dışarı aktarma](../ide/media/exportshortcuts.png)

5. Ayarlar **dosyanıza Ne** ad ve Ayarlar dosyamı bu **dizinde** depola kutularında varsayılan değerleri bırakın veya farklı değerler belirtin ve ardından Son'a **tıklayın.**

::: moniker range="vs-2017"

Varsayılan olarak, kısayollarınız *%USERPROFILE%\Documents\Visual Studio 2017\Ayarlar klasörüne* kaydedilir. Dosyanın adı, ayarları dışarı aktardığı tarihi, uzantının *ise .vssettings olduğu tarihi belirtir.*

::: moniker-end

::: moniker range=">=vs-2019"

Varsayılan olarak, kısayollarınız *%USERPROFILE%\Documents\Visual Studio 2019\Ayarlar klasörüne* kaydedilir. Dosyanın adı, ayarları dışarı aktardığı tarihi, uzantının *ise .vssettings olduğu tarihi belirtir.*

::: moniker-end

### <a name="to-import-only-keyboard-shortcuts"></a>Yalnızca klavye kısayollarını içeri aktarmak için

1. Menü çubuğunda Araçlar İçeri ve Dışarı  >  **Aktarma'Ayarlar.**

2. Seçili ortam **ayarlarını içeri aktar seçeneğini** belirleyin ve ardından Sonraki'yi **seçin.**

3. Hayır, **yeni ayarları içeri aktar, geçerli ayarlarım** seçeneğinin üzerine yaz ve ardından Sonraki'yi **seçin.**

4. My **Ayarlar** altında, içeri aktarmasını istediğiniz kısayolları içeren dosyayı seçin veya doğru dosyayı **bulmak** için Gözat düğmesini seçin.

5. **İleri**’yi seçin.

6. Hangi **ayarları içeri aktarmayı istiyorsunuz?** altında Tüm ayarlar onay Ayarlar kutusunun işaretini **kaldırın,** Seçenekler'i **genişletin** ve ardından Ortam'ı **genişletin.**

7. Klavye onay **kutusunu** ve ardından Son'a **tıklayın.**

   ![Yalnızca özelleştirilmiş klavye kısayollarını içeri aktarma](../ide/media/importshortcuts.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'nin erişilebilirlik özellikleri](../ide/reference/accessibility-features-of-visual-studio.md)
