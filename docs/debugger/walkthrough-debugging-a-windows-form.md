---
title: Windows Form | Microsoft Docs
description: Ortak bir yönetilen uygulama olan Windows Form oluşturma ve hata ayıklama adımlarını izleyin. C#, Visual Basic, C++ veya F# kullanabilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], walkthroughs
- debugging managed code, Windows Forms
- debugging [Visual Studio], Windows Forms
- Attach to Process dialog box
- debugger, attaching to programs
- Attach to Process dialog box, walkthroughs
- Windows Forms, debugging
- debugging Windows Forms, walkthroughs
ms.assetid: 529db1e2-d9ea-482a-b6a0-7c543d17f114
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 6790cd24bb6b4f927029ab7749e35acd1d756c24
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122051800"
---
# <a name="walkthrough-debugging-a-windows-form"></a>İzlenecek yol: Windows Formunda hata ayıklama
Bir Windows formülü en yaygın yönetilen uygulamalardan biridir. Bir Windows formu, standart bir Windows uygulaması oluşturur. Bu adım adım işlemleri Visual Basic, C# ya da C++ kullanarak tamamlayabilirsiniz.

 İlk olarak, herhangi bir açık çözümü kapatmanız gerekir.

### <a name="to-prepare-for-this-walkthrough"></a>Bu adım adım izleme için hazırlanmak amacıyla

- Açık olan bir çözümünüz varsa, kapatın. (Dosya menüsünde **Çözümü** **Kapat'ı seçin.)**

## <a name="create-a-new-windows-form"></a>Yeni bir Windows Formu Oluşturun
 Ardından, yeni bir Windows Formu oluşturacaksınız.

#### <a name="to-create-the-windows-form-for-this-walkthrough"></a>Bu anlatım için Windows formunu oluşturmak amacıyla

1. Dosya menüsünde **Yeni'yi** seçin **ve Seç'e** **Project.**

     **Yeni Proje** iletişim kutusu görünür.

2. Project Türleri bölmesinde, **Visual Basic**, **Visual C#** veya **Visual C++** düğümünü açın, sonra

    1. Visual Visual Basic veya Visual C# için, Windows **Desktop**  >  **Windows Form Uygulaması'Windows seçin.**

    2. Daha Visual C++ Masaüstü **Uygulaması'Windows seçin.**

3. Ad **kutusunda** projeye benzersiz bir ad (örneğin, Walkthrough_SimpleDebug).

4. **Tamam**'a tıklayın.

     Visual Studio, yeni bir proje oluşturur ve Windows Forms Tasarımcısı'nda yeni bir form görüntüler. Daha fazla bilgi için [bkz. Windows Forms Tasarımcısı.](/previous-versions/visualstudio/visual-studio-2010/e06hs424\(v\=vs.100\))

5. Görünüm menüsünde **Araç** **Kutusu'nı seçin.**

     Araç Kutusu açılır. Daha fazla bilgi için [bkz. Araç Kutusu.](../ide/reference/toolbox.md)

6. Araç Kutusunda Düğme denetimine **tıklayın ve** denetimi Form tasarım yüzeyine sürükleyin. Düğmeyi form üzerine bırakın.

7. Araç Kutusunda **TextBox** denetimine tıklayın ve denetimi Form tasarım yüzeyine sürükleyin. **TextBox'i** forma bırakın.

8. Form tasarım yüzeyinde, düğmeyi çift tıklatın.

     Bu sizi kod sayfasına götürür. İşaretçi `button1_Click` içinde olmalıdır.

10. `button1_Click` işlevinde, aşağıdaki kodu ekleyin:

    ```vb
    textBox1.Text = "Button was clicked!"
    ```

    ```csharp
    textBox1.Text = "Button was clicked!";
    ```

    ```cpp
    textBox1->Text = "Button was clicked!";
    ```

11. Derleme menüsünde **Çözümü** **Derleme'yi seçin.**

     Projenin hatasız oluşturması gerekir.

## <a name="debug-your-form"></a>Formunuzda Hata Ayıklama Yapın
 Şimdi, hata ayıklamayı başlatmak için hazırsınız.

#### <a name="to-debug-the-windows-form-created-for-this-walkthrough"></a>Bu adım adım izleme için oluşturulmuş Windows Formu hata ayıklaması için

1. Kaynak penceresinde, eklediğiniz metin ile aynı satırda sol kenar boşluğunu tıklatın:

     ```vb
    textBox1.Text = "Button was clicked!"
    ```

    ```csharp
    textBox1.Text = "Button was clicked!";
    ```

    ```cpp
    textBox1->Text = "Button was clicked!";
    ```

     Kırmızı bir nokta belirir ve satırdaki metin kırmızıyla vurgulanır. Kırmızı nokta bir kesme noktası temsil eder. Daha fazla bilgi için [bkz. Kesme Noktaları.](/previous-versions/ktf38f66(v=vs.100)) Uygulamayı hata ayıklayıcısı altında çalıştırdığınızda, hata ayıklayıcısı koda ulaşıldığında, yürütmeyi o konumda keser. Ardından uygulamanızın durumunu görüntüleyebilir ve ona hata ayıklama yapabilirsiniz.

    > [!NOTE]
    > Ayrıca herhangi bir kod satırına sağ tıklar, Kesme  Noktası'nın üzerine gelin ve ardından Kesme Noktası Ekle'ye tıklar ve bu satıra bir kesme noktası eklersiniz.

2. Hata **Ayıkla menüsünde** Başlat'ı **seçin.**

     Windows Formu çalışmaya başlar.

3. Windows Formu'nda, eklediğiniz düğmeyi tıklatın.

     Visual Studio'da bu, sizi kod satırında kesme noktası eklediğiniz satıra götürür. Bu satır, sarı ile vurgulanmış olmalıdır. Şimdi, uygulamanızda değişkenleri görüntüleyebilir ve yürütülmesini denetleyebilirsiniz. Uygulamanız artık yürütmeyi durdurmuştur ve sizden bir eylem bekliyordur.

4. Hata **Ayıkla menüsünde** **Windows'ı** ve ardından **İzle'yi seçin** ve **İzle1'e tıklayın.**

5. **Watch1 penceresinde** boş bir satıra tıklayın. Ad **sütununa** yazın (Visual Basic veya `textBox1.Text` Visual C# kullanıyorsanız) `textBox1->Text` veya (C++kullanıyorsanız) ENTER tuşuna basın.

     **Watch1 penceresinde** bu değişkenin değeri tırnak içinde şu şekilde gösterilir:

    `""`

6. Hata **Ayıkla menüsünde** **Adımla'ya tıklayın.**

     Watch1 penceresinde textBox1.Text değeri **şu** şekilde değişir:

    `Button was clicked!`

7. Hata **Ayıkla menüsünde Devam'ı** **seçerek** programda hata ayıklamayı sürdürün.

8. Windows Formunda, düğmeyi yeniden tıklatın.

     Visual Studio, yürütmeyi yeniden keser.

9. Kesme noktasını temsil eden kırmızı noktayı tıklatın.

     Bu, kesme noktasını kodunuzdan kaldırır.

10. Hata Ayıklama **menüsünde Hata Ayıklamayı** **Durdur'u seçin.**

## <a name="attach-to-your-windows-form-application-for-debugging"></a>Hata Ayıklama için Windows Form Uygulamanıza Ekleme
 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] içinde, hata ayıklayıcısını çalışan bir işleme ekleyebilirsiniz. Express Edition kullanıyorsanız, bu özellik desteklenmez.

#### <a name="to-attach-to-the-windows-form-application-for-debugging"></a>Hata ayıklama için Windows Form Uygulamasına eklemek için

1. Yukarıda oluşturduğunuz projede, sol kenar boşluğunu tıklatarak, eklediğiniz satırda bir kez daha bir kesme noktası ayarlayın:

     ```vb
    textBox1.Text = "Button was clicked!"
    ```

    ```csharp
    textBox1.Text = "Button was clicked!";
    ```

    ```cpp
    textBox1->Text = "Button was clicked!";
    ```

2. Hata Ayıklama **menüsünde Hata** Ayıklama Olmadan **Başlat'ı seçin.**

     Çalıştırılabilir haline çift tıklatmışsınız gibi, Windows Formu, Windows altında çalışmaya başlar. Hata ayıklayıcısı iliştirilmemiş.

3. Hata Ayıklama **menüsünde İşleme** **Ekle'yi seçin.** (Bu komut Araçlar menüsünde de **kullanılabilir.)**

     İşleme **Ekle iletişim** kutusu görüntülenir.

4. Kullanılabilir **İşlemler bölmesinde** İşlem sütununda işlem adını (Walkthrough_SimpleDebug.exe) **bulun ve** tıklayın.

5. Ekle **düğmesine** tıklayın.

6. Windows Formunuzda, tek başına bir tane olan düğmeyi tıklatın.

     Hata ayıklayıcısı, kesme noktasında Windows Formunun yürütülmesini keser.

## <a name="see-also"></a>Ayrıca bkz.
- [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)
- [Hata Ayıklayıcı Güvenliği](../debugger/debugger-security.md)