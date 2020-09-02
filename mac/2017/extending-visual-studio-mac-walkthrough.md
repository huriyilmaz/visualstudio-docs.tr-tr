---
title: Mac için Visual Studio Izlenecek yolu genişletme
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/14/2017
ms.technology: vs-ide-sdk
ms.assetid: 7D00512B-9688-4D8D-87A7-F04F207E3D02
ms.openlocfilehash: c5b3b759b32acfc86b4b584b3f3d52298c138a2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74985031"
---
# <a name="extending-visual-studio-for-mac-walkthrough"></a>Mac için Visual Studio Izlenecek yolu genişletme

Bu konu, [basit bir uzantı paketi](https://github.com/mjh4/AddIns/tree/master/DateInserter)oluşturma konusunda size rehberlik eder. Uzantı paketi Mac için Visual Studio düzenleme menüsünde, kullanıcının geçerli tarih ve saati açık metin belgesine eklemesini sağlayan yeni bir komut oluşturur.

Bu örnek, eklenti Oluşturucu 'yu kullanır. Eklenti Oluşturucu yeni bir proje şablonu oluşturur ve bunu özel uzantı paketimiz için gereken dosyalarla doldurur.

1. Zaten açık değilse Mac için Visual Studio başlatarak başlayın:

   ![Mac için Visual Studio ekran görüntüsü](media/extending-visual-studio-mac-addin3.png)

2. Uzantı Yöneticisi 'Ni kullanarak _eklenti Oluşturucu uzantı paketini_ yükler. Visual Studio menüsünden Uzantılar ' ı seçin **...**:

   ![Eklenti Yöneticisi sekmesi](media/extending-visual-studio-mac-addin4.png)

3. Galeri sekmesine gidin ve `Addin Maker` sağ üst arama çubuğuna yazın. Eklenti geliştirme kategorisinden AddIn Maker <kbd>' ı seçin ve ardından Ekle</kbd>' ye tıklayın. Hiçbir şey gösterilmezse Yenile ' ye basın ve yeniden arayın:

   ![Eklenti Yöneticisi](media/extending-visual-studio-mac-addin5.png)

4. Artık eklenti Oluşturucu yüklü olduğuna göre, bir uzantı paketi oluşturmaya başlayabilirsiniz. Yeni bir çözüm oluşturarak başlayın.

5. **Yeni çözüm iletişim kutusunda** **diğer > diğer > genel > Xamarin Studio eklenti > C#** şablonu ' nu seçin ve aşağıdaki ekranda yeni çözümü adlandırın `DateInserter` :

   ![Yeni çözüm oluşturma](media/extending-visual-studio-mac-addin7New.png)

6. Mac için Visual Studio yeni bir çözümü dolduracaktır:

   ![Doldurulmuş çözüm](media/extending-visual-studio-mac-addin8.png)

7. İçindeki şablon kodunu kaldırın `Manifest.addin.xml` ve aşağıdaki kodla değiştirin:

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

8. Şimdi metin düzenleyicisine tarih ve saat eklemeyi işleyecek dosyaları ayarlamanız gerekir. Proje düğümüne sağ tıklayın ve yeni bir dosya ekleyin. **Genel > boş sınıfı** ' nı seçin ve yeni dosya *ınsertdatehandler*olarak adlandırın:

   ![Tarih Işleyicisi Ekle](media/extending-visual-studio-mac-addin9.png)

9. Bundan sonra şablon kodunu kaldıralım `InsertDateHandler.cs` ve şu kodla değiştirin:

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

10. **Dateınserter** projesine sağ tıklayın ve **> yeni dosya Ekle**' yi seçin. **Genel > boş sabit listesi**' ni seçin ve ardından yeni dosya *Dateınsertercommands*olarak adlandırın:

    ![Dateınsertercommands](media/extending-visual-studio-mac-addin10.png)

11. `InsertDate`Komutu dosyasına yeni bir numaralandırma olarak ekleyin `DateInserterCommands.cs` :

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

12. Bu noktada, bir çalışma uzantısı paketiniz olmalıdır. İşinizi kaydederek ve uygulamayı çalıştırarak test edebilirsiniz. IDE yeni uzantı paketi yüklüyken Mac için Visual Studio yeni bir örneğini başlatır. **Düzenleme menüsüne**gittiğinizde, Mac için Visual Studio aşağıdaki ekran görüntüsünde gösterildiği gibi **ekleme tarihi**adlı yeni bir seçeneğe sahip olduğunu görürsünüz:

    ![Tarih Ekle komutu](media/extending-visual-studio-mac-addin11.png)

    Menüdeki ekleme tarihini seçme, geçerli uygulamanın yalnızca yer tutucu yöntemlerine sahip olduğu için hiçbir etkiye sahip olmadığını unutmayın.

13. Altyapı, Uzantı paketi için yerinde ve tarihi eklemenin temelini oluşturan kodun yazılması zaman. İlk olarak, **Tarih Ekle komutunun** yalnızca, `Update` içindeki yöntemi aşağıdaki kodla değiştirerek bir metin dosyası açıkken etkinleştirildiğinden emin olun `InsertDateHandler.cs` :

    ```cs
    protected override void Update(CommandInfo info)
    {
      info.Enabled = IdeApp.Workbench.ActiveDocument?.Editor != null;
    }
    ```

14. `Run`Aşağıdaki kodla tarih ve saat eklemek Için komut metodunu güncelleştirin:

    ``` cs
    protected override void Run () {
      var editor = IdeApp.Workbench.ActiveDocument.Editor;
      var date = DateTime.Now.ToString ();
      editor.InsertAtCaret (date);

    }
    ```

15. Son olarak, bu uzantıyı test etmek için uzantı paketimizi çalıştıralım. Yeni Mac için Visual Studio örneğinde **düzenle > Ekle Tarih**' i seçin. Şu anki tarih ve saat, aşağıdaki ekran görüntüsünde gösterildiği gibi giriş işaretimize eklenir:

    ![Tarih Ekle ekran görüntüsü](media/extending-visual-studio-mac-addin12.png)

## <a name="see-also"></a>Ayrıca bkz.

- [İlk uzantınızı oluşturma (Windows üzerinde Visual Studio)](/visualstudio/extensibility/extensibility-hello-world)