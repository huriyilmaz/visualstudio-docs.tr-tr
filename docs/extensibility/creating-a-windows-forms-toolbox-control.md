---
title: Windows Forms araç kutusu denetimi oluşturma | Microsoft Docs
description: Bu izlenecek yol, Visual Studio SDK kullanarak basit bir sayaç denetimi oluşturmak için Windows Forms araç kutusu denetim şablonunun nasıl kullanılacağını gösterir.
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- winforms
- toolbox
- windows forms
ms.assetid: 0be6ffc1-8afd-4d02-9a5d-e27dde05fde6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 42dcf30e7c31880357bb95e3858a2c70aa59f174
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089335"
---
# <a name="create-a-windows-forms-toolbox-control"></a>Windows Forms araç kutusu denetimi oluşturma

Visual Studio Genişletilebilirlik Araçları (VS SDK) eklenen Windows Forms araç kutusu denetim öğesi şablonu, uzantı yüklendiğinde otomatik olarak eklenen bir **araç kutusu** denetimi oluşturmanıza olanak sağlar. Bu izlenecek yolda, diğer kullanıcılara dağıtabileceğiniz basit bir sayaç denetimi oluşturmak için şablonunun nasıl kullanılacağı gösterilmektedir.

## <a name="prerequisites"></a>Önkoşullar

Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yüklemeyi](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-toolbox-control"></a>Araç kutusu denetimini oluşturma

Windows Forms araç kutusu denetim şablonu tanımsız bir kullanıcı denetimi oluşturur ve denetimi **araç kutusu**'na eklemek için gereken tüm işlevleri sağlar.

### <a name="create-an-extension-with-a-windows-forms-toolbox-control"></a>Windows Forms araç kutusu denetimiyle uzantı oluşturma

1. Adlı bir VSıX projesi oluşturun `MyWinFormsControl` . VSıX proje şablonunu **Yeni proje** iletişim kutusunda, "VSIX" araması yaparak bulabilirsiniz.

2. Proje açıldığında adlı bir **Windows Forms araç kutusu denetim** öğesi şablonu ekleyin `Counter` . **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve   >  **Yeni öğe** Ekle ' yi seçin. **Yeni öğe Ekle** iletişim kutusunda, **Visual C#**  >  **genişletilebilirliği** ' ne gidin ve **Windows Forms araç kutusu denetimi** ' ni seçin.

3. Bu, `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> denetimin **araç kutusuna** yerleştirileceği bir Kullanıcı denetımı ve dağıtım Için VSIX bildiriminde bir **Microsoft. VisualStudio. ToolboxControl** varlık girişi ekler.

### <a name="build-a-user-interface-for-the-control"></a>Denetim için bir kullanıcı arabirimi oluşturma

`Counter`Denetim iki alt denetim gerektirir: <xref:System.Windows.Forms.Label> geçerli sayıyı göstermek için a ve <xref:System.Windows.Forms.Button> sayıyı 0 olarak sıfırlamak için a. Çağıran sayacı programlamayla artdığı için başka alt denetimler gerekli değildir.

#### <a name="to-build-the-user-interface"></a>Kullanıcı arabirimini oluşturmak için

1. **Çözüm Gezgini**, tasarımcı 'da açmak için *Counter. cs* öğesine çift tıklayın.

2. **Buraya tıklayın!** Windows Forms araç kutusu denetim öğesi şablonunu eklediğinizde varsayılan olarak eklenen düğme.

3. **Araç kutusundan**, bir `Label` denetimi ve sonra da bir `Button` denetimi tasarım yüzeyine sürükleyin.

4. Genel Kullanıcı denetimini 150, 50 piksel olacak şekilde yeniden boyutlandırın ve düğme denetimini 50, 20 piksel olarak yeniden boyutlandırın.

5. **Özellikler** penceresinde, Tasarım yüzeyinde denetimler için aşağıdaki değerleri ayarlayın.

    |Denetim|Özellik|Değer|
    |-------------|--------------|-----------|
    |`Label1`|**Metin**|""|
    |`Button1`|**Ad**|btnReset|
    |`Button1`|**Metin**|Sıfırla|

### <a name="code-the-user-control"></a>Kullanıcı denetimini kodlayın

`Counter`Denetim, sayacı artırmak için bir yöntem, sayaç ne zaman artırılacağı bir olay, bir **sıfırlama** düğmesi ve geçerli sayıyı, görüntüleme metnini ve **sıfırlama** düğmesinin gösterilip gösterilmeyeceğini veya gizlenmesi için üç özelliği sunar. `ProvideToolboxControl`Öznitelik, denetimin **araç kutusunda** nerede görüneceğini belirler `Counter` .

#### <a name="to-code-the-user-control"></a>Kullanıcı denetimini kodlayın

1. Kod penceresinde yük olay işleyicisini açmak için forma çift tıklayın.

2. Olay işleyicisi yönteminin üzerinde, denetim sınıfındaki sayaç değerini depolamak için bir tamsayı ve aşağıdaki örnekte gösterildiği gibi görüntüleme metnini depolamak için bir dize oluşturun.

    ```csharp
    int currentValue;
    string displayText;
    ```

3. Aşağıdaki ortak özellik bildirimlerini oluşturun.

    ```csharp
    public int Value {
        get { return currentValue; }
    }

    public string Message {
        get { return displayText; }
        set { displayText = value; }
    }

    public bool ShowReset {
        get { return btnReset.Visible; }
        set { btnReset.Visible = value; }
    }

    ```

    Çağıranlar, sayacın görüntüleme metnini almak ve ayarlamak ve **sıfırlama** düğmesini göstermek ya da gizlemek için bu özelliklere erişebilir. Çağıranlar salt okunurdur özelliğinin geçerli değerini elde edebilir `Value` , ancak doğrudan değer ayarlayamazlar.

4. Denetim için olaya aşağıdaki kodu koyun `Load` .

    ```csharp
    private void Counter_Load(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = Message + Value;
    }

    ```

    Olaydaki **etiket** metninin ayarlanması, <xref:System.Windows.Forms.UserControl.Load> değerleri uygulanmadan önce hedef özelliklerin yüklenmesine olanak sağlar. Oluşturucuda **etiket** metninin ayarlanması boş bir **etikete** neden olur.

5. Sayacı artırmak için aşağıdaki ortak yöntemi oluşturun.

    ```csharp
    public void Increment()
    {
        currentValue++;
        label1.Text = displayText + Value;
        Incremented(this, EventArgs.Empty);
    }

    ```

6. Denetim sınıfına olay için bir bildirim ekleyin `Incremented` .

    ```csharp
    public event EventHandler Incremented;
    ```

    Çağıranlar, sayaç değerindeki değişikliklere yanıt vermek için bu olaya işleyiciler ekleyebilir.

7. Tasarım görünümüne dönüp olay işleyicisini oluşturmak için **Sıfırla** düğmesine çift tıklayın `btnReset_Click` . Ardından, aşağıdaki örnekte gösterildiği gibi doldurmanız gerekir.

    ```csharp
    private void btnReset_Click(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = displayText + Value;
    }

    ```

8. Sınıf tanımının hemen üzerinde, `ProvideToolboxControl` öznitelik bildiriminde, ilk parametresinin değerini `"MyWinFormsControl.Counter"` olarak değiştirin `"General"` . Bu, **araç kutusunda** denetimi barındıracak olan öğe grubunun adını ayarlar.

    Aşağıdaki örnek, `ProvideToolboxControl` özniteliğini ve ayarlanmış sınıf tanımını gösterir.

    ```csharp
    [ProvideToolboxControl("General", false)]
    public partial class Counter : UserControl
    ```

### <a name="test-the-control"></a>Denetimi test etme

 Bir **araç kutusu** denetimini test etmek için, önce geliştirme ortamında test edin ve ardından derlenmiş bir uygulamada test edin.

#### <a name="to-test-the-control"></a>Denetimi test etmek için

1. **Hata ayıklamayı başlatmak** için **F5** 'e basın.

    Bu komut projeyi oluşturur ve denetimin yüklü olduğu ikinci bir Visual Studio örneğini açar.

2. Visual Studio 'nun deneysel örneğinde bir **Windows Forms uygulama** projesi oluşturun.

3. **Çözüm Gezgini**, zaten açık değilse, tasarımcıda açmak için *Form1. cs* ' ye çift tıklayın.

4. **Araç kutusunda**, `Counter` denetimin **genel** bölümünde görüntülenmesi gerekir.

5. Formunuza bir `Counter` Denetim sürükleyin ve sonra bunu seçin. `Value`, `Message` Ve `ShowReset` özellikleri **Özellikler** penceresinde, öğesinden devralınan özelliklerle birlikte görüntülenir <xref:System.Windows.Forms.UserControl> .

6. `Message`Özelliğini olarak ayarlayın `Count:` .

7. Forma bir <xref:System.Windows.Forms.Button> Denetim sürükleyin ve sonra düğmenin adını ve metin özelliklerini olarak ayarlayın `Test` .

8. Kod görünümünde *Form1. cs* ' yi açmak için düğmeye çift tıklayın ve bir tıklama işleyicisi oluşturun.

9. Tıklama işleyicisinde öğesini çağırın `counter1.Increment()` .

10. Oluşturucu işlevinde, öğesine çağrısından sonra `InitializeComponent` yazın `counter1``.``Incremented +=` ve Iki kez **Tab** tuşuna basın.

    Visual Studio, olay için form düzeyinde bir işleyici oluşturur `counter1.Incremented` .

11. `Throw`Olay işleyicisinde ifadeyi vurgulayın, yazın `mbox` ve ardından mbox kod parçacığından bir ileti kutusu oluşturmak için Iki kez **Tab** tuşuna basın.

12. Sonraki satırda, `if` / `else` **sıfırlama** düğmesinin görünürlüğünü ayarlamak için aşağıdaki bloğu ekleyin.

    ```csharp
    if (counter1.Value < 5) counter1.ShowReset = false;
    else counter1.ShowReset = true;
    ```

13. **F5** tuşuna basın.

    Form açılır. `Counter`Denetimde aşağıdaki metin görüntülenir.

    **Sayı: 0**

14. **Test**'i seçin.

    Sayaç artışları ve Visual Studio bir ileti kutusu görüntüler.

15. İleti kutusunu kapatın.

    **Sıfırla** düğmesi kaybolur.

16. Sayaç her seferinde ileti **kutularını kapatmadan önce** **Test** ' i seçin.

    **Sıfırla** düğmesi yeniden görüntülenir.

17. **Sıfırla**’yı seçin.

    Sayaç **0**' a sıfırlanır.

## <a name="next-steps"></a>Sonraki adımlar

Bir **araç kutusu** denetimi oluştururken, Visual Studio projenizin \bin\debug\ klasöründe *ProjectName. vsix* adlı bir dosya oluşturur. *. Vsix* dosyasını bir ağa veya bir Web sitesine yükleyerek bu denetimi dağıtabilirsiniz. Bir Kullanıcı *. vsix* dosyasını açtığında, denetim yüklenir ve kullanıcının bilgisayarında Visual Studio **araç kutusu** 'na eklenir. Alternatif olarak, kullanıcıların **araçları** [](https://marketplace.visualstudio.com/)   >  **Uzantılar ve güncelleştirmeler** iletişim kutusunda bulabilmeleri için. vsix dosyasını Visual Studio Market yükleyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'nun diğer kısımlarını genişletme](../extensibility/extending-other-parts-of-visual-studio.md)
- [WPF araç kutusu denetimi oluşturma](../extensibility/creating-a-wpf-toolbox-control.md)
- [Visual Studio 'nun diğer kısımlarını genişletme](../extensibility/extending-other-parts-of-visual-studio.md)
- [Windows Forms denetimi geliştirme temelleri](/dotnet/framework/winforms/controls/windows-forms-control-development-basics)
