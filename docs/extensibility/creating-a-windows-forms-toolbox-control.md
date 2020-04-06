---
title: Windows Forms Araç Kutusu Denetimi Oluşturma | Microsoft Dokümanlar
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- winforms
- toolbox
- windows forms
ms.assetid: 0be6ffc1-8afd-4d02-9a5d-e27dde05fde6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d7e7749302252c5d56f21c58de9b6ac23f898572
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739586"
---
# <a name="create-a-windows-forms-toolbox-control"></a>Windows Forms Araç Kutusu Denetimi Oluşturma

Visual Studio Genişletilebilirlik Araçları'na (VS SDK) dahil olan Windows Forms Araç Kutusu Denetimi öğesi şablonu, uzantı yüklendiğinde otomatik olarak eklenen bir **Araç Kutusu** denetimi oluşturmanıza olanak tanır. Bu izlik, diğer kullanıcılara dağıtabileceğiniz basit bir sayaç denetimi oluşturmak için şablonun nasıl kullanılacağını gösterir.

## <a name="prerequisites"></a>Ön koşullar

Visual Studio 2015'ten itibaren Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak yer almaktadır. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için Visual [Studio SDK'yı yükleyin.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-the-toolbox-control"></a>Araç Kutusu Denetimini Oluşturma

Windows Forms Araç Kutusu Denetimi şablonu tanımlanmamış bir kullanıcı denetimi oluşturur ve denetimi **Araç Kutusu'na**eklemek için gereken tüm işlevselliği sağlar.

### <a name="create-an-extension-with-a-windows-forms-toolbox-control"></a>Windows Forms Araç Kutusu Denetimi ile uzantı oluşturma

1. Adlı `MyWinFormsControl`bir VSIX projesi oluşturun. "vsix" aramasını yaparak **VSIX** proje şablonunu Yeni Proje iletişim kutusunda bulabilirsiniz.

2. Proje açıldığında, windows **forms araç kutusu denetimi** `Counter`öğesi şablonu ekleyin. Çözüm **Gezgini'nde**proje düğümüne sağ tıklayın ve**Yeni Öğe** **Ekle'yi** > seçin. Yeni **Öğe Ekle** iletişim kutusunda **Visual C#** > **Genişletilebilirlik'e** gidin ve **Windows Forms Araç Kutusu Denetimi'ni** seçin

3. Bu bir kullanıcı denetimi `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> ekler, bir **Araç Kutusu'nda**kontrol yerleştirmek için, ve dağıtım için VSIX bildiriminde **bir Microsoft.VisualStudio.ToolboxControl** Varlık girişi.

### <a name="build-a-user-interface-for-the-control"></a>Denetim için bir kullanıcı arabirimi oluşturma

Denetim `Counter` iki alt denetim <xref:System.Windows.Forms.Label> gerektirir: a geçerli sayısı <xref:System.Windows.Forms.Button> görüntülemek için ve a 0 sayısı sıfırlamak için. Arayanlar karşı sayacı programlı olarak artıya atlayacaktır, çünkü başka alt denetimler gerekli değildir.

#### <a name="to-build-the-user-interface"></a>Kullanıcı arabirimini oluşturmak için

1. **Solution Explorer'da,** tasarımcıda açmak için *Counter.cs* çift tıklatın.

2. Buraya **Tıklayın** kaldırın ! Windows Forms Araç Kutusu Denetimi öğesi şablonu eklediğinizde varsayılan olarak dahil edilen düğme.

3. Araç **Kutusundan,** bir `Label` denetimi sürükleyin ve ardından altından tasarım yüzeyine bir `Button` denetim sürükleyin.

4. Genel kullanıcı denetimini 150, 50 piksele yeniden boyutlandırın ve düğme denetimini 50,20 piksele yeniden boyutlandırın.

5. **Özellikler** penceresinde, tasarım yüzeyindeki denetimler için aşağıdaki değerleri ayarlayın.

    |Denetim|Özellik|Değer|
    |-------------|--------------|-----------|
    |`Label1`|**Metin**|""|
    |`Button1`|**Adı**|btnReset|
    |`Button1`|**Metin**|Sıfırla|

### <a name="code-the-user-control"></a>Kullanıcı denetimini kodlama

Denetim, `Counter` sayacı, sayaç artırıldığında yükseltilecek bir olayı, bir **Sıfırlama** düğmesini ve geçerli sayıyı, ekran metnini depolamak için üç özelliği ve **Sıfırlama** düğmesini gösterip göstermemeyi veya gizlemeyeceğini gösteren bir yöntemi ortaya çıkarır. Öznitelik, `ProvideToolboxControl` **Denetimin** `Counter` Araç Kutusu'nda nerede görüneceğini belirler.

#### <a name="to-code-the-user-control"></a>Kullanıcı denetimini kodlamak için

1. Kod penceresinde yük olayı işleyicisini açmak için formu çift tıklatın.

2. Olay işleyicisi yönteminin üzerinde, denetim sınıfında sayaç değerini depolamak için bir tamsayı ve aşağıdaki örnekte gösterildiği gibi görüntü metnini depolamak için bir dize oluşturun.

    ```csharp
    int currentValue;
    string displayText;
    ```

3. Aşağıdaki kamu malı beyannamelerini oluşturun.

    ```csharp
    public int Value {
        get { return currentValue; }
    }

    public string Message {
        get { return displayText; }
        set { displayText = value; }
    }

    public bool ShowReset {
        get { return btnReset.Visible; }
        set { btnReset.Visible = value; }
    }

    ```

    Arayanlar, sayacın ekran metnini almak ve ayarlamak ve **Sıfırlama** düğmesini göstermek veya gizlemek için bu özelliklere erişebilir. Arayanlar salt `Value` okunur özelliğinin geçerli değerini elde edebilir, ancak değeri doğrudan ayarlayamazlar.

4. Denetim için `Load` olaya aşağıdaki kodu koyun.

    ```csharp
    private void Counter_Load(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = Message + Value;
    }

    ```

    <xref:System.Windows.Forms.UserControl.Load> Durumda **Etiket** metninin ayarlanması, hedef özelliklerin değerleri uygulanmadan önce yüklenmesini sağlar. **Etiket** metninin oluşturucuya ayarlanması boş bir **Etiketle**sonuçlanır.

5. Sayacı nismeiçin aşağıdaki ortak yöntemi oluşturun.

    ```csharp
    public void Increment()
    {
        currentValue++;
        label1.Text = displayText + Value;
        Incremented(this, EventArgs.Empty);
    }

    ```

6. `Incremented` Olay için denetim sınıfına bir bildirim ekleyin.

    ```csharp
    public event EventHandler Incremented;
    ```

    Arayanlar, sayacın değerindeki değişikliklere yanıt vermek için bu olaya işleyiciler ekleyebilir.

7. Tasarım görünümüne dönün ve olay işleyicisini `btnReset_Click` oluşturmak için **Sıfırla** düğmesini çift tıklatın ve ardından aşağıdaki örnekte gösterildiği gibi doldurun.

    ```csharp
    private void btnReset_Click(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = displayText + Value;
    }

    ```

8. Sınıf tanımının hemen üstünde, öznitelik bildiriminde, `ProvideToolboxControl` ilk parametrenin değerini ' den `"MyWinFormsControl.Counter"` ' e `"General"`değiştirin Bu, **Denetimi Araç Kutusu'nda**barındıracak öğe grubunun adını ayarlar.

    Aşağıdaki örnek, `ProvideToolboxControl` özniteliği ve ayarlanan sınıf tanımını gösterir.

    ```csharp
    [ProvideToolboxControl("General", false)]
    public partial class Counter : UserControl
    ```

### <a name="test-the-control"></a>Denetimi test edin

 **Bir Araç Kutusu** denetimini sınamak için önce geliştirme ortamında sınayın ve ardından derlenmiş bir uygulamada test edin.

#### <a name="to-test-the-control"></a>Denetimi test etmek için

1. **Hata Ayıklamaya Başlamak**için **F5** tuşuna basın.

    Bu komut projeyi oluşturur ve denetimi yüklü olan Visual Studio'nun ikinci bir Deneysel örneğini açar.

2. Visual Studio'nun Deneysel örneğinde bir **Windows Forms Application** projesi oluşturun.

3. **Çözüm Gezgini'nde,** zaten açık değilse tasarımcıda açmak için *Form1.cs* çift tıklayın.

4. Araç **Kutusunda,** `Counter` denetim **Genel** bölümde görüntülenmelidir.

5. Denetimi `Counter` forma sürükleyin ve sonra seçin. , `Value` `Message`ve `ShowReset` özellikleri **Özellikler** penceresinde, devralınan özellikleri ile birlikte <xref:System.Windows.Forms.UserControl>görüntülenir.

6. Özelliği `Message` ' `Count:`ye ayarlayın.

7. Denetimi <xref:System.Windows.Forms.Button> forma sürükleyin ve düğmenin ad ve metin özelliklerini `Test`.'e ayarlayın.

8. Kod görünümünde *Form1.cs* açmak ve bir tıklama işleyicisi oluşturmak için düğmeyi çift tıklatın.

9. Tıklama işleyicisinde, `counter1.Increment()`.

10. Oluşturucu işlevinde, çağrıdan `InitializeComponent`sonra `counter1``.``Incremented +=` , yazın ve sonra **Sekme'ye** iki kez basın.

    Visual Studio olay için bir form `counter1.Incremented` düzeyi işleyicisi oluşturur.

11. Olay `Throw` işleyicisi, yazın `mbox`ve sonra mbox kodu snippet bir ileti kutusu oluşturmak için **sekme** iki kez basın ifadesini vurgulayın.

12. Sonraki satırda, `if` / `else` **Sıfırla** düğmesinin görünürlüğünü ayarlamak için aşağıdaki bloğu ekleyin.

    ```csharp
    if (counter1.Value < 5) counter1.ShowReset = false;
    else counter1.ShowReset = true;
    ```

13. **F5 tuşuna**basın.

    Form açılır. Denetim `Counter` aşağıdaki metni görüntüler.

    **Sayı: 0**

14. **Test'i**tıklatın.

    Sayaç artışları ve Visual Studio bir ileti kutusu görüntüler.

15. İleti kutusunu kapatın.

    **Sıfırlama** düğmesi kaybolur.

16. Sayaç ileti kutularını her seferinde **kapatarak 5'e** ulaşana kadar **Test'i** tıklatın.

    **Sıfırlama** düğmesi yeniden görüntülenir.

17. **Sıfırla'yı**tıklatın.

    Sayaç **0'a**sıfırlanır.

## <a name="next-steps"></a>Sonraki adımlar

Bir Araç **Kutusu** denetimi oluşturduğunuzda, Visual Studio projenizin \bin\debug\ klasöründe *ProjectName.vsix* adlı bir dosya oluşturur. *.vsix* dosyasını bir ağa veya bir Web sitesine yükleyerek denetimi dağıtabilirsiniz. Bir kullanıcı *.vsix* dosyasını açtığında, denetim yüklenir ve kullanıcının bilgisayarındaki Visual Studio **Araç Kutusu'na** eklenir. Alternatif olarak, *.vsix* dosyasını [Visual Studio Marketplace'e](https://marketplace.visualstudio.com/) yükleyebilirsiniz, böylece kullanıcılar **Araçlar** > **Uzantıları ve Güncelleştirmeleri** iletişim kutusunda göz atarak dosyayı bulabilirler.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'nun diğer bölümlerini genişletin](../extensibility/extending-other-parts-of-visual-studio.md)
- [WPF Araç Kutusu Denetimi Oluşturma](../extensibility/creating-a-wpf-toolbox-control.md)
- [Visual Studio'nun diğer bölümlerini genişletin](../extensibility/extending-other-parts-of-visual-studio.md)
- [Windows Forms geliştirme temellerini denetler](/dotnet/framework/winforms/controls/windows-forms-control-development-basics)
