---
title: Kılavuz Mac için Visual Studio Genişletme
description: Düzenle menüsünde yeni bir Komut oluşturan Mac için Visual Studio için basit bir uzantı paketi derlemeyi öğrenin.
ms.custom: SEO-VS-2020
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/14/2017
ms.technology: vs-ide-sdk
ms.assetid: 7D00512B-9688-4D8D-87A7-F04F207E3D02
ms.openlocfilehash: 60f929d3012ecf67a263040177ca55a8f349413a7567dabd84c6c308f2242177
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121242411"
---
# <a name="extending-visual-studio-for-mac-walkthrough"></a>Kılavuz Mac için Visual Studio Genişletme

Bu konu, basit bir uzantı [paketi inşa etmek için size yol sağlar.](https://github.com/mjh4/AddIns/tree/master/DateInserter) Uzantı paketi, kullanıcının Mac için Visual Studio belgeye geçerli tarih ve saati eklemesine olanak sağlayan Düzenle menüsünde yeni bir Komut oluşturacak.

Bu örnekte Eklenti Oluşturucusu 2. Add-In Oluşturucu, yeni bir Project şablonu oluşturur ve özel uzantı paketimiz için gerekli dosyalarla bu şablonu oluşturur.

1. Açık Mac için Visual Studio başlatarak başlayalım:

   ![Mac için Visual Studio Ekran görüntüsü](media/extending-visual-studio-mac-addin3.png)

2. Uzantı _Yöneticisi'ni kullanarak Eklenti Oluşturucu_ uzantısı paketini yükleyin. Yeni Visual Studio **Uzantılar... öğesini seçin:**

   ![Addin Manager Sekmesi](media/extending-visual-studio-mac-addin4.png)

3. Galeri sekmesine gidin ve `Addin Maker` sağ üst arama çubuğuna yazın. Eklenti Geliştirme kategorisinden Addin Maker'ı seçin ve Yükle'ye <kbd>tıklayın.</kbd> Herhangi bir şey yoksa Yenile'ye tarak yeniden arama yapma:

   ![Addin Manager](media/extending-visual-studio-mac-addin5.png)

4. Addin Maker'ın yüklü olduğua göre artık bir uzantı paketi oluşturmaya başlayabilirsiniz. Yeni bir çözüm oluşturarak başlayabilirsiniz.

5. Yeni Çözüm **iletişim kutusunda** Diğer > > > Genel **> Xamarin Studio C#** > ekle'yi seçin ve aşağıdaki ekranda yeni Çözümü olarak ad `DateInserter` girin:

   ![Yeni Çözüm Oluşturma](media/extending-visual-studio-mac-addin7New.png)

6. Mac için Visual Studio çözümü yeni bir çözümle doldurmak için:

   ![Doldurulmuş Çözüm](media/extending-visual-studio-mac-addin8.png)

7. içinde şablon kodunu `Manifest.addin.xml` kaldırın ve aşağıdakilerle değiştirin:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
      <ExtensionModel>
          <Extension path = "/MonoDevelop/Ide/Commands/Edit">
              <Command id = "DateInserter.DateInserterCommands.InsertDate"
                  _label = "Insert Date"
                  defaultHandler = "DateInserter.InsertDateHandler" />
          </Extension>

          <Extension path = "/MonoDevelop/Ide/MainMenu/Edit">
              <CommandItem id="DateInserter.DateInserterCommands.InsertDate" />
          </Extension>
      </ExtensionModel>
   ```

8. Şimdi, tarih ve saati metin düzenleyicisine eklemeyi sonunda işleyecek dosyaları ayarlayabilirsiniz. Right-Click düğümüne tıklayın ve yeni bir dosya ekleyin. Genel **sınıf > Sınıf'ı** seçin ve yeni dosyayı *InsertDateHandler olarak ad girin:*

   ![Tarih İşleyici ekle](media/extending-visual-studio-mac-addin9.png)

9. Şablon kodunu 'dan kaldırarak `InsertDateHandler.cs` aşağıdaki kodla değiştirebilirsiniz:

   ```cs
   using MonoDevelop.Components.Commands;
   using MonoDevelop.Ide;
   using MonoDevelop.Ide.Gui;
   using System;

   namespace DateInserter
   {
      class InsertDateHandler : CommandHandler
      {
          protected override void Run()
          {

          }

          protected override void Update(CommandInfo info)
          {

          }
      }
   }
   ```

   Bu iki yer tutucu yöntemi daha sonra genişleteceğiz.

10. **DateInserter** dosyasına sağ tıklayın Project Yeni Dosya **ekle'> seçin.** Genel **> Boş Numaralandır'ı seçin** ve ardından yeni dosyayı *DateInserterCommands olarak adlandırın:*

    ![DateInserterCommands](media/extending-visual-studio-mac-addin10.png)

11. Komutu `InsertDate` dosyasına yeni bir numaralama olarak `DateInserterCommands.cs` ekleyin:

    ``` cs
    using System;

    namespace DateInserter
    {
      public enum DateInserterCommands
      {
          InsertDate,
      }
    }
    ```

12. Bu noktada, çalışan bir uzantı paketiniz olması gerekir. Çalışmanızı kaydederek ve uygulamayı çalıştırarak test etmek için bunu testebilirsiniz. IDE, yeni uzantı paketi yüklü Mac için Visual Studio yeni bir örnek başlatacak. Düzenle menüsüne **gidip** aşağıdaki ekran görüntüsünde Mac için Visual Studio ekle adlı yeni bir seçeneği olduğunu görebilirsiniz:

    ![Tarih Ekle Komutu](media/extending-visual-studio-mac-addin11.png)

    Geçerli uygulamanın yalnızca yer tutucu yöntemleri olduğu için menüden Tarih Ekle seçeneğinin etkili olmadığını unutmayın.

13. Uzantı paketi için çerçeve hazır ve tarihi eklemeye gücü olan kodu yazma zamanı geldi. İlk olarak, Tarih  Ekle Komutu'na yalnızca kullanıcının içinde yöntemini aşağıdaki kodla değiştirerek bir metin dosyası açık olduğunda `Update` `InsertDateHandler.cs` etkinleştirildiğinden emin olun:

    ```cs
    protected override void Update(CommandInfo info)
    {
      info.Enabled = IdeApp.Workbench.ActiveDocument?.Editor != null;
    }
    ```

14. Aşağıdaki kodla tarih `Run` ve saati eklemek için Komutun yöntemini güncelleştirin:

    ``` cs
    protected override void Run () {
      var editor = IdeApp.Workbench.ActiveDocument.Editor;
      var date = DateTime.Now.ToString ();
      editor.InsertAtCaret (date);

    }
    ```

15. Son olarak, bunu test etmek için uzantı paketimizi çalıştırabilirsiniz. Yeni veri örneği Mac için Visual Studio Ekle'yi **> seçin.** Geçerli tarih ve saat, aşağıdaki ekran görüntüsünde gösterildiği gibi, bizim caret'imize eklenir:

    ![Tarih Ekle Ekran Görüntüsü](media/extending-visual-studio-mac-addin12.png)

## <a name="see-also"></a>Ayrıca bkz.

- [İlk uzantınızı oluşturma (Visual Studio Windows)](/visualstudio/extensibility/extensibility-hello-world)