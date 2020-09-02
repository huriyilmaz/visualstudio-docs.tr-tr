---
title: Klavye Kısayollarını Tanımlama ve Özelleştirme
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
ms.assetid: d2774be2-60a4-4d6f-95f1-79d0d9e55b56
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e63395838d7d91170d54edbb07c0b38db548ccdf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670485"
---
# <a name="identifying-and-customizing-keyboard-shortcuts-in-visual-studio"></a>Visual Studio'daki Klavye Kısayollarını Tanımlama ve Özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio komutları için kısayollar tanımlayabilir, bu kısayolları özelleştirebilir ve başkalarının kullanması için dışarı aktarabilirsiniz. Birçok kısayol her zaman aynı komutları çağırır, ancak kısayolun davranışı aşağıdaki koşullara göre değişebilir:

- Visual Studio'yu ilk kez çalıştırdığınızda seçtiğiniz varsayılan ortam ayarları (örneğin, Genel Geliştirme veya Visual C#).

- Kısayolun davranışını özelleştirip özelleştirmediğiniz.

- Kısayolu seçtiğiniz anda içinde bulunduğunuz bağlam. Örneğin F2 kısayolu, Ayarlar Tasarımcısı'nı kullanıyorsanız Edit.EditCell komutunu, Ekip Gezgini'ni kullanıyorsanız File.Rename komutunu çağırır.

  Ayarlar, özelleştirme ve bağlamlarından bağımsız olarak, **Seçenekler** iletişim kutusunda her zaman bir klavye kısayolunu bulabilir ve değiştirebilirsiniz. Ayrıca, [sık kullanılan komutlar için varsayılan klavye kısayollarında](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md)birkaç düzine komut için varsayılan klavye kısayollarına bakabilir ve varsayılan [klavye kısayollarında](../ide/default-keyboard-shortcuts-in-visual-studio.md)tüm varsayılan kısayolların (genel geliştirme ayarlarına bağlı olarak) tümüyle bir listesini bulabilirsiniz.

  **Bu konuda**

- [Klavye kısayolunu tanımlama](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md#bkmk_identify)

- [Klavye kısayolunu özelleştirme](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md#bkmk_assign)

- [Özel klavye kısayollarını paylaşma](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md#bkmk_transfer)

  Bir komuta Genel bağlamda kısayol atanmış ve diğer bağlamlarda atanmamışsa, ilgili kısayol her zaman bu komutu çağırır. Ancak bir kısayol, Genel bağlamda bir komuta ve özel bağlamda farklı bir komuta atanabilir. Böyle bir komutu özel bağlamda kullanırsanız, özel bağlama ilişkin komutu çağırır (Genel bağlama ilişkin komutu çağırmaz).

> [!NOTE]
> Ayarlarınıza ve Visual Studio sürümünüze göre, menü komutlarının adları ve konumları ve iletişim kutularında görünen seçenekler değişik olabilir. Bu konu, **genel geliştirme ayarlarına**dayalıdır.

## <a name="identifying-a-keyboard-shortcut"></a><a name="bkmk_identify"></a> Klavye kısayolunu tanımlama

1. Menü çubuğunda **Araçlar**, **Seçenekler**' i seçin.

2. **Ortam**' ı genişletin ve ardından **klavye**' yi seçin.

     ![Seçenekler iletişim kutusunda klavye kısayollarını görüntüleme](../ide/media/optionskeyboard.png "Seçenekseçenekleri klavyesi")

3. **İçerilen komutları göster** kutusunda, boşluk olmadan komutun adının tamamını veya bir kısmını girin.

     Örneğin, **SolutionExplorer**komutlarını bulabilirsiniz.

4. Listede doğru komutu seçin.

     Örneğin, **View. SolutionExplorer**' ı seçebilirsiniz.

5. Komutun klavye kısayolu varsa, **Seçilen komut listesi Için kısayollar** görüntülenir.

     ![Belirtilen komut için bir kısayol görüntüle](../ide/media/viewshortcut.png "ViewShortcut")

## <a name="customizing-a-keyboard-shortcut"></a><a name="bkmk_assign"></a> Klavye kısayolunu özelleştirme

1. Menü çubuğunda **Araçlar**, **Seçenekler**' i seçin.

2. **Ortam** klasörünü genişletin ve ardından **klavye**' yi seçin.

     ![Seçenekler iletişim kutusunda klavye kısayollarını görüntüleme](../ide/media/optionskeyboard.png "Seçenekseçenekleri klavyesi")

3. **İçerilen komutları göster** kutusunda, boşluk olmadan komutun adının tamamını veya bir kısmını girin.

     Örneğin, **SolutionExplorer**komutlarını bulabilirsiniz.

4. Listede, klavye kısayolu atamak istediğiniz komutu seçin.

5. **Yeni Kısayol kullan** listesinde, kısayolu kullanmak istediğiniz özellik alanını seçin.

     Örneğin, kısayolun tüm bağlamlarda çalışmasını istiyorsanız **genel** ' i seçebilirsiniz. Başka bir düzenleyicide Genel olarak eşlenmemiş herhangi bir kısayolu kullanabilirsiniz. Aksi takdirde düzenleyici kısayolu geçersiz kılar.

    > [!NOTE]
    > Aşağıdaki anahtarları **genel**: Print SCRN/SYS RQ, Scroll Lock, Duraklat/kes, Tab, Caps Lock, INSERT, Home, End, page up, Page Down, Windows logo tuşu, uygulama anahtarı, ok tuşlarından herhangi biri veya ENTER gibi bir klavye kısayolunun parçası olarak atayamazsınız. Sayısal tuş takımında Lock, DELETE veya Clear olarak say; ya da CTRL + ALT + DELETE.

6. **Kısayol tuşlarını bas** kutusunda, kullanmak istediğiniz kısayolu girin.

    > [!NOTE]
    > Bir harfi; Alt tuşu, Ctrl tuşu veya her ikisiyle birden birleştiren bir kısayol oluşturabilirsiniz. Ayrıca Shift tuşu ve bir harfi; Alt tuşu, Ctrl tuşu veya her ikisiyle birden birleştiren bir kısayol da oluşturabilirsiniz.

     Bir kısayol zaten başka bir komuta atanmışsa, bu, **Şu anda kullanıldığı kısayolda** görünür. Bu durumda, farklı birini denemden önce kısayolu silmek için Geri Al tuşunu seçin.

     ![Komut için farklı bir kısayol belirtin](../ide/media/reassignshortcut.png "ReassignShortcut")

7. **Ata** düğmesini seçin.

    > [!NOTE]
    > Bir komut için farklı bir kısayol belirtirseniz, **ata** düğmesini seçin ve ardından **iptal** düğmesini seçin, iletişim kutusu kapanır, ancak değişiklik geri döndürülemez.

## <a name="sharing-custom-keyboard-shortcuts"></a><a name="bkmk_transfer"></a> Özel klavye kısayollarını paylaşma
 Özel klavye kısayollarınızı bir dosyaya dışarı aktararak ve verileri içeri aktarabilmeleri için bu dosyayı başkalarına vererek, klavye kısayollarınızı paylaşabilirsiniz.

#### <a name="to-export-only-keyboard-shortcuts"></a>Yalnızca klavye kısayollarını dışarı aktarmak için

1. Menü çubuğunda **Araçlar**, **içeri ve dışarı aktarma ayarları**' nı seçin.

2. **Seçili ortam ayarlarını dışarı aktar**' ı seçin ve ardından **İleri** düğmesini seçin.

3. **Hangi ayarları dışarı aktarmak istiyorsunuz?** bölümünde, **Tüm ayarlar** onay kutusunun işaretini kaldırın, **Seçenekler**' i genişletin ve ardından **ortam**' ı genişletin.

4. **Klavye** onay kutusunu seçin ve ardından **İleri** düğmesini seçin.

     ![Yalnızca özelleştirilmiş klavye kısayollarını dışarı aktar](../ide/media/exportshortcuts.png "Exportkýsayollar")

5. **Ayarlar dosyanızı ne adlandırmak istiyorsunuz?** ve ayarlarımı **Bu dizin kutularında depola** ' da, varsayılan değerleri bırakın veya farklı değerler belirtin ve ardından **son** düğmesini seçin.

     Varsayılan olarak kısayollarınız %USERPROFILE%\Documents\Visual Studio 2013\Settings klasöründe bulunan bir dosyaya kaydedilir. Dosyanın adı ayarları dışarı aktardığınız tarihi yansıtır ve uzantısı .vssettings olur.

#### <a name="to-import-only-keyboard-shortcuts"></a>Yalnızca klavye kısayollarını içeri aktarmak için

1. Menü çubuğunda **Araçlar**, **içeri ve dışarı aktarma ayarları**' nı seçin.

2. **Seçili ortam ayarlarını Içeri aktar** seçenek düğmesini seçin ve sonra **İleri** düğmesini seçin.

3. **Hayır, yeni ayarları içeri aktar, geçerli ayarlarım üzerine yaz** seçenek düğmesini seçin ve ardından **İleri** düğmesini seçin.

4. Ayarlarım **altında,** içeri aktarmak istediğiniz kısayolları içeren dosyayı seçin veya doğru dosyayı bulmak Için, **Gözden** geçirme düğmesini seçin.

5. **İleri** düğmesini seçin.

6. **Hangi ayarları içeri aktarmak istiyorsunuz?**, **Tüm ayarlar** onay kutusunun işaretini kaldırın, **Seçenekler**' i genişletin ve ardından **ortam**' ı genişletin.

7. **Klavye** onay kutusunu seçin ve ardından **son** düğmesini seçin.

     ![Yalnızca özelleştirilmiş klavye kısayollarını içeri aktar](../ide/media/importshortcuts.png "Importkýsayollar")

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio'nun Erişilebilirlik Özellikleri](../ide/reference/accessibility-features-of-visual-studio.md)
