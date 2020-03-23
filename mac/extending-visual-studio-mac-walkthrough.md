---
title: Mac Walkthrough için Visual Studio genişletme
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/14/2017
ms.technology: vs-ide-sdk
ms.assetid: 7D00512B-9688-4D8D-87A7-F04F207E3D02
ms.openlocfilehash: c5b3b759b32acfc86b4b584b3f3d52298c138a2c
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "74983295"
---
# <a name="extending-visual-studio-for-mac-walkthrough"></a>Mac Walkthrough için Visual Studio genişletme

Bu [konu, basit bir uzantı paketi](https://github.com/mjh4/AddIns/tree/master/DateInserter)oluşturarak size yol gösteriyor. Uzantı paketi, Mac'in Edit menüsü için Visual Studio'da kullanıcının geçerli tarih ve saati açık bir metin belgesine eklemesine olanak tanıyan yeni bir Komut oluşturur.

Bu örnek, Eklenti Oluşturucu'yu kullanır. Eklenti Oluşturucu yeni bir Proje şablonu oluşturur ve özel uzantı paketimiz için gerekli dosyalarla doldurulur.

1. Zaten açık değilse Mac için Visual Studio başlatarak başlayın:

   ![Mac Ekran Görüntüsü için Visual Studio](media/extending-visual-studio-mac-addin3.png)

2. Eklenti _Yöneticisi'ni kullanarak Eklenti Oluşturucu uzantısı paketini_ yükleyin. Visual Studio menüsünden **Uzantılar'ı seçin...**:

   ![Addin Yöneticisi Sekmesi](media/extending-visual-studio-mac-addin4.png)

3. Galeri sekmesine gidin `Addin Maker` ve sağ üstteki arama çubuğuna yazın. Eklenti Geliştirme kategorisinden Addin Maker'ı seçin ve <kbd>Yükle'yi</kbd>tıklatın. Hiçbir şey yoksa, Yenile'ye vurun ve yeniden arayın:

   ![Addin Yöneticisi](media/extending-visual-studio-mac-addin5.png)

4. Addin Maker yüklü olduğuna göre, bir uzatma paketi oluşturmaya başlayabilirsiniz. Yeni bir çözüm oluşturarak başlayın.

5. Yeni **Çözüm iletişim kutusundan,** **Diğer > Çeşitli > Genel > Xamarin Studio Addin > C#** şablonu `DateInserter`ve aşağıdaki ekran adı yeni Çözüm seçin:

   ![Yeni Bir Çözüm Oluşturma](media/extending-visual-studio-mac-addin7New.png)

6. Mac için Visual Studio yeni bir Çözüm dolduracak:

   ![Doldurulan Çözüm](media/extending-visual-studio-mac-addin8.png)

7. Şablon kodunu çıkarın `Manifest.addin.xml` ve aşağıdakilerle değiştirin:

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

8. Şimdi, tarih ve saati metin düzenleyicisine eklemeyi işleyecek dosyaları ayarlamanız gerekir. Proje düğümüne sağ tıklayın ve yeni bir dosya ekleyin. **Genel > Boş Sınıf'ı** seçin ve yeni *dosyayı InsertDateHandler'ı*adlandırın:

   ![Tarih İdesi Ekle](media/extending-visual-studio-mac-addin9.png)

9. Şablon kodunu kaldıralım `InsertDateHandler.cs` ve aşağıdaki kodla değiştirelim:

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

   Bu iki yer tutucu yöntemini daha sonra genişleteceğiz.

10. **DateInserter** Projesi'ne sağ tıklayın ve **Yeni Dosya ekle >** seçin. **Genel > Boş Numaralandırma'yı**seçin ve ardından yeni dosyadateInserterKomutları'nı adlandırın: *DateInserterCommands*

    ![DateInserterKomutları](media/extending-visual-studio-mac-addin10.png)

11. `DateInserterCommands.cs` Komutu `InsertDate` dosyaya yeni bir numaralandırma olarak ekleyin:

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

12. Bu noktada, bir çalışma uzantısı paketi olmalıdır. Çalışmanızı kaydederek ve uygulamayı çalıştırarak test edebilirsiniz. IDE yeni uzantısı paketi yüklü mac için Visual Studio yeni bir örnek başlatacak. **Edit menüsüne**giderseniz, Mac için Visual Studio'nun aşağıdaki ekran görüntüsünde gösterildiği gibi **Tarihi Ekle**adlı yeni bir seçeneği olduğunu görürsünüz:

    ![Tarih Komutu Ekle](media/extending-visual-studio-mac-addin11.png)

    Geçerli uygulamayalnızca yer tutucu yöntemleri olduğundan, menüden Tarihi Ekle'yi seçmenin hiçbir etkisi olmadığını unutmayın.

13. Uzantı paketi için çerçeve hazırdır ve tarihi ekleme yetkisi veren kodu yazma nın zamanı geldi. İlk olarak, **Insert Date** Komutu'nun yalnızca kullanıcının bir metin dosyası `Update` açık `InsertDateHandler.cs` olduğunda, yöntemi aşağıdaki kodla değiştirerek etkinleştirildiğinden emin olun:

    ```cs
    protected override void Update(CommandInfo info)
    {
      info.Enabled = IdeApp.Workbench.ActiveDocument?.Editor != null;
    }
    ```

14. Tarih ve saati `Run` aşağıdaki kodla eklemek için Komutun yöntemini güncelleştirin:

    ``` cs
    protected override void Run () {
      var editor = IdeApp.Workbench.ActiveDocument.Editor;
      var date = DateTime.Now.ToString ();
      editor.InsertAtCaret (date);

    }
    ```

15. Son olarak, bunu test etmek için uzatma paketi çalıştıralım. Mac için Visual Studio'nun yeni örneğinde, **Tarihi > Ekle'yi >'yi**seçin. Geçerli tarih ve saat, aşağıdaki ekran görüntüsünde gösterildiği gibi, bizim caret eklenir:

    ![Tarih Ekran Ekle](media/extending-visual-studio-mac-addin12.png)

## <a name="see-also"></a>Ayrıca bkz.

- [İlk uzantınızı oluşturun (Windows'ta Visual Studio)](/visualstudio/extensibility/extensibility-hello-world)